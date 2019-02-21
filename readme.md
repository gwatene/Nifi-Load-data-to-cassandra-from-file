NiFi Example: Load CSV file into Cassandra Table using the traditional way and the new way using Record
Example Data
Ingested to the example flows by GenerateFlowFile:

ID, CITY_NAME, ZIP_CD, STATE_CD
001, CITY_A, 1111, AA
002, CITY_B, 2222, BB
003, CITY_C, 3333, CC
004, CITY_D, 4444, DD
Destination Table

create table cities (
  id text,
  city_name text,
  zip_cd text,
  state_cd text,
  primary key (id)
);
Traditional way
Upto Apache NiFi ver 1.2.0, I'd use ConvertCSVToAvro, then Avro to JSON, finally JSON to SQL. There maybe other solutions to load a CSV file with different processors, but you need to use multiple processors together.



With Record
Since Apache NiFi ver 1.3.0, new Record concept has been introduced. With Record, you can read/write different data format such as CSV/Avro/JSON ... etc. As shown in this example, several processors were also added to process Records, e.g. PutDatabaseRecord or ConvertRecord.

With Record aware processors, you don't have to convert data format as we had to do before. You can construct simpler and more efficient data flows.




