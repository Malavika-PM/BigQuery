1. Find the first and last dates from the data.

   ```SQL
   SELECT MIN(date) AS first_date, Max(date) AS last_date
   FROM 'bigquery-public-data.covid19_italy.national_trends';
   ```
   ![Result 1](https://github.com/Malavika-PM/BigQuery/assets/156827573/e7cfa53c-18ae-4561-9d73-2d082e459f23)

2. Calculate the total number of confirmed cases reported in italy.

   ```SQL
   SELECT SUM(total_confirmed_cases) AS total_confirmed_cases
   FROM 'bigquery-public-data.covid19_italy.national_trends';
   ```
   ![Result 2](https://github.com/Malavika-PM/BigQuery/assets/156827573/70b22a02-9aca-4883-a956-493a8074c91a)

3. Find the number the daily trend of active cases over time.

   ```SQL
   SELECT SUM(new_total_confirmed_cases) AS total_active_cases
   FROM 'bigquery-public-data.covid19_italy.national_trends';
   ```
   ![Result 3](https://github.com/Malavika-PM/BigQuery/assets/156827573/9e442251-adda-47ab-b53e-8ee69a35bd83)

4. Find the total number of deaths in italy for a specific time period.

    ```SQL
   SELECT SUM(deaths) AS total_deaths
   FROM 'bigquery-public-data.covid19_italy.national_trends'
   WHERE date BETWEEN '2020-01-01' AND '2024-02-03';
   ```
   ![Result 4](https://github.com/Malavika-PM/BigQuery/assets/156827573/957e2473-7470-436f-970c-9b5594bd636b)

5.  Identify the 5 dates with the highest number of deaths.

     ```SQL
     SELECT date, deaths
     FROM 'bigquery-public-data.covid19_italy.national_trends'
     ORDER BY deaths DESC
     LIMIT 5;
    ```
     ![Result 5](https://github.com/Malavika-PM/BigQuery/assets/156827573/6497d7e3-13a5-40d1-b31d-235559202622)

 6.   Find the 5 dates with the highest number of recoveries.

        ```SQL
       SELECT date, recovered
       FROM 'bigquery-public-data.covid19_italy.national_trends'
       ORDER BY recovered DESC
       LIMIT 5;
       ```
       ![Result  6](https://github.com/Malavika-PM/BigQuery/assets/156827573/4b8fd54e-7588-4503-bb1c-216a49859c73)

 7.  Find the total number of recoveries.

       ```SQL
          SELECT SUM(recovered) AS total_recoveries
          FROM 'bigquery-public-data.covid19_italy.national_trends';
        ```
       ![Result 7](https://github.com/Malavika-PM/BigQuery/assets/156827573/4efbfbc0-42ea-428f-b2ea-996ccb25ea62)

8.  Find the date with the highest number of hospitalized patients 

       ```SQL
          SELECT date, total_hospitalized_patients
          FROM 'bigquery-public-data.covid19_italy.national_trends'
          ORDER BY total_hospitalized_patients DESC
          LIMIT 5;
       ```
       ![Result 8](https://github.com/Malavika-PM/BigQuery/assets/156827573/e4d00acb-8987-4522-9bed-5b09d1f1b829)

 9.  How do the total confirmed cases in Lombardy and Tuscany compare to the national trend over the first 5 days?.
       ```SQL
     SELECT nt.date,
     nt.total_confirmed_cases AS national_cases,
     r.region_name,
     r.total_confirmed_cases AS regional_cases
     FROM `bigquery-public-data.covid19_italy.national_trends` AS nt
     INNER JOIN `bigquery-public-data.covid19_italy.data_by_region` AS r
     ON nt.date = r.date
     WHERE r.region_name IN ('Lombardia', 'Toscana')
     ORDER BY nt.date, r.region_name
     LIMIT 5;
     ```
       ![Result 9](https://github.com/Malavika-PM/BigQuery/assets/156827573/441e3c86-c079-44c5-ba0e-77a3f7ab88b6)

 10.  Find the trend of hospitalized cases nationally and regionally where regional hospitalized patients is greater than 50
         ```SQL
         SELECT nt.date,
         nt.total_hospitalized_patients AS national_hospitalized,
         r.region_name,
          r.total_hospitalized_patients AS regional_hospitalized,
         FROM `bigquery-public-data.covid19_italy.national_trends` AS nt
         INNER JOIN `bigquery-public-data.covid19_italy.data_by_region` AS r
         ON nt.date = r.date
         WHERE r.total_hospitalized_patients > 50
         ORDER BY nt.date, r.region_name
         limit 5;
         ```
         ![Result 10](https://github.com/Malavika-PM/BigQuery/assets/156827573/fe8187ab-9d22-463b-a9ac-5c56213883eb)

         


  
          
 
         

          

       

   
