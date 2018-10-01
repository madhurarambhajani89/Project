# Capstone-Project
Business challenge/requirementFor this capstone project we will be analyzing 911 call data from Kaggle.
This data is from Montgomery County in  Pennsylvania State of USA. 911 is most important social security feature of USA.
It is the no. which citizens can call in case of any emergencies such as crime, medical, traffic, fire etc.
As a data analyst you have to analyze and visualize the data  and answer the question in section Approach to Solve
Key issues
Data should be analyzed accurately
considerations
NONE
data volume & Description
-Approx 260K 
records –file 911.csv
Fields in Data are:
•lat : String variable, 
Latitude•lng: String variable,
Longitude•desc: String variable, 
Description of the Emergency Call•zip: String variable,
Zipcode•title: String variable, 
Title•timeStamp: String variable,
YYYY-MM-DD HH:MM:SS•twp: String variable, 
Township•addr: String variable,
Address•e: String variable,
additional information-NA
business benefits
Better utilization of resources based on the density of 911 calls.
Approach to Solve
You have to use fundamentals covered till Module 8 and answer following 8 questions
Compute  --What are the top 10 Zipcodes for 911  & Question 1: Are Zipcodes 19446 and 19090 present ?•
Compute --What are the top 4 townships (twp) for 911 calls  Question 2: Which  of the following township are  not present? --LOWER POTTSGROVE, NORRISTOWN, HORSHAM, ABINGTON
•Compute --Create new features  & Question 3: What is the most common Reason for a 911 call based on Reason Column? Which comes second
•Compute --Plot barchart using matplot  for 911 calls by Reason  & Question 4: How can you plot the bars horizontally ?
•Do data manipulation & Question 5: Which day got maximum calls for EMS and how many?
•Compute --Create a countplot of the Day of Week column with the hue based of the Reason column & Question 6: On which day traffic calls were lowest ?
•Compute --Create a countplot month wise  --Question 7: Which month saw highest calls for fire?
•Compute --Create Web Map for Traffic Calls  & Question 8: Why some areas seem tohave lower or almost zero traffic calls? Hint: Zoom the map

import pandas as pd
import numpy as np
import csv
import folium as fm
import matplotlib.pyplot as plt
import seaborn as sns
#Q.1Compute  --What are the top 10 Zipcodes for 911  & Question 1: Are Zipcodes 19446 and 19090 present ?
df=pd.read_csv('911.csv')
df=df.dropna()
#print(df)
df1=df['zip'].value_counts()
df1=df1.head(10)
df1.to_csv('1.csv')
with open('1.csv',newline='') as f:
    r = csv.reader(f)
    data = [line for line in r]
with open('1.csv','w',newline='') as f:
    w = csv.writer(f)
    w.writerow(['zip','frequency'])
    w.writerows(data)
df2=pd.read_csv('1.csv')
print(df2)

a1=list(df2['zip'])
a2=list(df2['frequency'])
x=19090
y=19446
#print(df2.isin([19090,19446]))
if (x in a1) & (y in a1):
    print("Zipcodes are present in top 10")
else:
    print("Zipcodes are not found")

#Q.2Compute --What are the top 4 townships (twp) for 911 calls
# & Question 2: Which  of the following township are  not present? --LOWER POTTSGROVE, NORRISTOWN, HORSHAM, ABINGTON
df3=df['twp'].value_counts()
df3=df3.head(4)
#print(df3)
df3.to_csv('2.csv')
with open('2.csv',newline='') as f1:
    r1 = csv.reader(f1)
    data1 = [line1 for line1 in r1]
with open('2.csv','w',newline='') as f1:
    w1 = csv.writer(f1)
    w1.writerow(['Town','frequency'])
    w1.writerows(data1)
df4=pd.read_csv('2.csv')
print(df4)

b1=list(df4['Town'])
b2=list(df4['frequency'])
x1="LOWER POTTSGROVE"
x2="NORRISTOWN"
x3="HORSHAM"
x4="ABINGTON"
if(x1 in b1):
    print(x1,"is in top four towns")
else:
    print(x1,"is not in top four towns")
if(x2 in b1):
    print(x2,"in in top four towns")
else:
    print(x2,"is not in top four towns")
if(x3 in b1):
    print(x3,"is in top four towns")
else:
    print(x3,"is not in top four towns")
if(x4 in b1):
    print(x4,"is in top four towns")
else:
    print(x4,"is not in top four towns")

#Q.3Compute --Create new features  & Question 3: What is the most common Reason for a 911 call based on Reason Column? Which comes second

df[['Reason', 'Title']] = df.title.str.split(': ', expand = True)
df.to_csv('3.csv',index=False)
#print(df)
df5=df['Reason'].value_counts()
print('The 2 most common reasons for calling 911 are',df5.head(2))
df5.to_csv('4.csv')
with open('4.csv',newline='') as f2:
    r2 = csv.reader(f2)
    data2 = [line2 for line2 in r2]
with open('4.csv','w',newline='') as f2:
    w2 = csv.writer(f2)
    w2.writerow(['Reason','frequency'])
    w2.writerows(data2)

df6=pd.read_csv('4.csv',index_col=False)
print(df6)


#Compute --Plot barchart using matplot  for 911 calls by Reason  & Question 4: How can you plot the bars horizontally ?


objects=tuple(df6['Reason'])
y_pos = np.arange(len(objects))
frequency1=list(df6['frequency'])

plt.bar(y_pos, frequency1, align='center')
plt.barh(y_pos,frequency1,align='center')
plt.xticks(y_pos, objects)
plt.ylabel('FRequency')
plt.title('Statistics')
plt.show()

#Do data manipulation & Question 5: Which day got maximum calls for EMS and how many?
df['timeStamp']=pd.to_datetime(df['timeStamp'])
#df.to_csv('5.csv')
#df7=pd.read_csv('5.csv')
#df[['Date', 'Time']] = df.timeStamp.str.split(' ', expand = True)
df['day_of_week'] = df['timeStamp'].dt.day_name()
df.to_csv('5.csv')
df7=df['day_of_week'].value_counts()
print("the maximum call for ems was on",df7.head(1))

#Compute --Create a countplot of the Day of Week column with the hue based of the Reason column & Question 6: On which day traffic calls were lowest ?
sns.set(style="darkgrid")
sns.countplot(x='day_of_week', hue='Reason', data=df)
plt.legend(bbox_to_anchor=(1,1))
plt.show()

#Compute --Create a countplot month wise  --Question 7: Which month saw highest calls for fire?

df['Month'] = df['timeStamp'].apply(lambda time:time.month)
sns.countplot(x='Month', hue='Reason', data=df)
plt.legend(bbox_to_anchor=(1,1))
plt.show()

#Compute --Create Web Map for Traffic Calls  & Question 8: Why some areas seem tohave lower or almost zero traffic calls? Hint: Zoom the map
SF_COORDINATES = (40.2978759,-75.5812935)
mdata = pd.read_csv('911.csv')
map = fm.Map(location=SF_COORDINATES, zoom_start=12,tiles="OpenStreetMap")
fg = fm.FeatureGroup(name="Locations")
for data in mdata.iterrows():
    fg.add_child(fm.Marker(location=[data[1]['lng'], data[1]['lat'] ],icon=fm.Icon(color="red")))
map.add_child(fg)
map.save("BasicWebMap.html")
print(map)


import pandas as pd
import numpy as np
import csv
import folium as fm
import matplotlib.pyplot as plt
import seaborn as sns
#Q.1Compute  --What are the top 10 Zipcodes for 911  & Question 1: Are Zipcodes 19446 and 19090 present ?
df=pd.read_csv('911.csv')
df=df.dropna()
#print(df)
df1=df['zip'].value_counts()
df1=df1.head(10)
df1.to_csv('1.csv')
with open('1.csv',newline='') as f:
    r = csv.reader(f)
    data = [line for line in r]
with open('1.csv','w',newline='') as f:
    w = csv.writer(f)
    w.writerow(['zip','frequency'])
    w.writerows(data)
df2=pd.read_csv('1.csv')
print(df2)

a1=list(df2['zip'])
a2=list(df2['frequency'])
x=19090
y=19446
#print(df2.isin([19090,19446]))
if (x in a1) & (y in a1):
    print("Zipcodes are present in top 10")
else:
    print("Zipcodes are not found")

#Q.2Compute --What are the top 4 townships (twp) for 911 calls
# & Question 2: Which  of the following township are  not present? --LOWER POTTSGROVE, NORRISTOWN, HORSHAM, ABINGTON
df3=df['twp'].value_counts()
df3=df3.head(4)
#print(df3)
df3.to_csv('2.csv')
with open('2.csv',newline='') as f1:
    r1 = csv.reader(f1)
    data1 = [line1 for line1 in r1]
with open('2.csv','w',newline='') as f1:
    w1 = csv.writer(f1)
    w1.writerow(['Town','frequency'])
    w1.writerows(data1)
df4=pd.read_csv('2.csv')
print(df4)

b1=list(df4['Town'])
b2=list(df4['frequency'])
x1="LOWER POTTSGROVE"
x2="NORRISTOWN"
x3="HORSHAM"
x4="ABINGTON"
if(x1 in b1):
    print(x1,"is in top four towns")
else:
    print(x1,"is not in top four towns")
if(x2 in b1):
    print(x2,"in in top four towns")
else:
    print(x2,"is not in top four towns")
if(x3 in b1):
    print(x3,"is in top four towns")
else:
    print(x3,"is not in top four towns")
if(x4 in b1):
    print(x4,"is in top four towns")
else:
    print(x4,"is not in top four towns")

#Q.3Compute --Create new features  & Question 3: What is the most common Reason for a 911 call based on Reason Column? Which comes second

df[['Reason', 'Title']] = df.title.str.split(': ', expand = True)
df.to_csv('3.csv',index=False)
#print(df)
df5=df['Reason'].value_counts()
print('The 2 most common reasons for calling 911 are',df5.head(2))
df5.to_csv('4.csv')
with open('4.csv',newline='') as f2:
    r2 = csv.reader(f2)
    data2 = [line2 for line2 in r2]
with open('4.csv','w',newline='') as f2:
    w2 = csv.writer(f2)
    w2.writerow(['Reason','frequency'])
    w2.writerows(data2)

df6=pd.read_csv('4.csv',index_col=False)
print(df6)


#Compute --Plot barchart using matplot  for 911 calls by Reason  & Question 4: How can you plot the bars horizontally ?


objects=tuple(df6['Reason'])
y_pos = np.arange(len(objects))
frequency1=list(df6['frequency'])

plt.bar(y_pos, frequency1, align='center')
plt.barh(y_pos,frequency1,align='center')
plt.xticks(y_pos, objects)
plt.ylabel('FRequency')
plt.title('Statistics')
plt.show()

#Do data manipulation & Question 5: Which day got maximum calls for EMS and how many?
df['timeStamp']=pd.to_datetime(df['timeStamp'])
#df.to_csv('5.csv')
#df7=pd.read_csv('5.csv')
#df[['Date', 'Time']] = df.timeStamp.str.split(' ', expand = True)
df['day_of_week'] = df['timeStamp'].dt.day_name()
df.to_csv('5.csv')
df7=df['day_of_week'].value_counts()
print("the maximum call for ems was on",df7.head(1))

#Compute --Create a countplot of the Day of Week column with the hue based of the Reason column & Question 6: On which day traffic calls were lowest ?
sns.set(style="darkgrid")
sns.countplot(x='day_of_week', hue='Reason', data=df)
plt.legend(bbox_to_anchor=(1,1))
plt.show()

#Compute --Create a countplot month wise  --Question 7: Which month saw highest calls for fire?

df['Month'] = df['timeStamp'].apply(lambda time:time.month)
sns.countplot(x='Month', hue='Reason', data=df)
plt.legend(bbox_to_anchor=(1,1))
plt.show()

#Compute --Create Web Map for Traffic Calls  & Question 8: Why some areas seem tohave lower or almost zero traffic calls? Hint: Zoom the map
SF_COORDINATES = (40.2978759,-75.5812935)
mdata = pd.read_csv('911.csv')
map = fm.Map(location=SF_COORDINATES, zoom_start=12,tiles="OpenStreetMap")
fg = fm.FeatureGroup(name="Locations")
for data in mdata.iterrows():
    fg.add_child(fm.Marker(location=[data[1]['lng'], data[1]['lat'] ],icon=fm.Icon(color="red")))
map.add_child(fg)
map.save("BasicWebMap.html")
print(map)

