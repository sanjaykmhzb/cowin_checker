
#Import required library
import requests
from datetime import datetime, timedelta
#import pandas as pd


# 14 Days Date
today = datetime.today()
list_format = [today + timedelta(days=i) for i in range(14)]
dates_wk = [i.strftime("%d-%m-%Y") for i in list_format]

dates='30-05-2021'

#Search For
pincode=110092

#URL
alldist_url = "https://cdn-api.co-vin.in/api/v2/admin/location/districts/9"
bydist_url = "https://cdn-api.co-vin.in/api/v2/appointment/sessions/public/calendarByDistrict?district_id=9&date=28-05-2021"

bypin_url = "https://cdn-api.co-vin.in/api/v2/appointment/sessions/public/calendarByPin?pincode={}&date={}".format(pincode, dates)

header = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:88.0) Gecko/20100101 Firefox/88.0'} 
result = requests.get(bypin_url, headers=header)



counter=0

if result.ok:
    response_json = result.json()
    if response_json["centers"]:       
        for center in response_json["centers"]:
            for session in center["sessions"]:
                if (session["available_capacity"] > -1 ) : 
                    print('Pincode: ', center["pincode"])
                    print('\t state_name:    ', center["state_name"])
                    print('\t district_name: ', center["district_name"])                 
                    print("\t Available on:", session["date"])
                    print("\t Age: ", session["min_age_limit"])
                    print("\t", center["name"])
                    print("\t", center["block_name"])
                    print("\t Price: ", center["fee_type"])
                    print("\t Availablity : ", session["available_capacity"])
                    print("\t Dose1 : ", session["available_capacity_dose1"], ", Dose2 : ", session["available_capacity_dose2"])
                  #  print("\t Dose2 : ", session["available_capacity_dose2"])
                    if(session["vaccine"] != ''):
                        print("\t Vaccine type: ", session["vaccine"])
                    print("\n")
                    counter = counter + 1
else:
     print("No Response!")
                

