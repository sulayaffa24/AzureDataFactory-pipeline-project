# AzureDataFactory-pipeline-project
>Created a simple data pipeline using Azure Data Factory

## Project Overview
I will need to create a couple of Azure data services in a resource group. Which will include:
* **Storage account** -> where we will initially store our data 
* **Azure Data Factory** -> Azure's pipeline service where we will move data from our storage account to our database
* **Azure SQL** -> Where our data will be finally stored and to be queried

### Getting the data
___
I was able to download the .csv file from [DATA.GOV](https://data.wa.gov/Transportation/Electric-Vehicle-Population-Data/f6w7-q2d2) and later upload it in my Azure storage account. Here's a preview of the data on the website:

![image](https://user-images.githubusercontent.com/30465635/214925032-fbf24a4b-a8ba-4911-9011-c54ad61b4a51.png)

*This dataset shows the Battery Electric Vehicles (BEVs) and Plug-in Hybrid Electric Vehicles (PHEVs) that are currently registered through Washington State Department of Licensing (DOL)*


### Step 1 Create the resources needed in a resource group
___

![image](https://user-images.githubusercontent.com/30465635/214947663-1f49a140-aeb6-4501-84ed-a684906b78f6.png)

### Step 2 Upload the dataset in a Blob Container
___
Created an Azure Storage Account and a Blob Storage Container where I uploaded the dataset

![image](https://user-images.githubusercontent.com/30465635/214944051-a628f07d-c043-4325-9c4b-9a70ebba5062.png)

### Step 3 Create the schema for the database that matches the csv file downloaded
___

```sql
CREATE TABLE Electric_Vehicles (
  VIN VARCHAR(50),
  County VARCHAR(50),
  City VARCHAR(50),
  State VARCHAR(50),
  ...
)
```

### Step 4 Go to the Azure Data Factory service that you just created and launch the service
___
![image](https://user-images.githubusercontent.com/30465635/214948158-51aad8f0-66db-497a-bcd1-c27d89c787bc.png)

### Step 5 Create a pipeline to connect your file in your blob container to your SQL Database
___
![image](https://user-images.githubusercontent.com/30465635/214950382-6b66c810-bc4a-44de-9e52-177ec68688b1.png)

**It is important to debug the pipeline to check for errors before publishing it. If it is successful you can check the database to view the data. I like to use the Azure Data Studio tool. Here's a preview of the data in the database:**

![image](https://user-images.githubusercontent.com/30465635/214953772-db7c3828-cefa-45c1-88cf-8211dcd510d4.png)

Here are the columns in the database table:

![image](https://user-images.githubusercontent.com/30465635/214954011-ffcf9613-715a-49de-9605-c1b2dc064f6a.png)

