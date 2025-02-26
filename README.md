[# Splunk-Command](https://docs.splunk.com/Documentation/SplunkCloud/9.3.2408/SearchTutorial/GetthetutorialdataintoSplunk

---Launch Splunk
C:\Program Files\Splunk\bin\splunk.exe
	or
http://127.0.0.1:8000/en-US/app/launcher/home)

Upload data to splunk -> setting-> add data-> upload data

index="price_demo" source="prices.csv" | eval discount = round ((price - sale_price), 2) | table productId, product_name, price, sale_price, discount, code

index="price_demo" source="prices.csv" | stats count as "Total Product" by product_name

index="price_demo" source="prices.csv" | where price=sale_price | table productId 

index="price_demo" source="prices.csv" | sort by price | table productId, product_name , price, sale_price, code

index="price_demo" source="prices.csv" | stats max(price) as Max_Price , min(price) as Min_Price

index="price_demo" source="prices.csv" | sort price | table productId, code, price, product_name,

index="price_demo" source="prices.csv" | eval discount_Percentage= round((price- sale_price) * 100 / price, 2) | sort -discount_percentage | table productId, code, product_name, price,sale_price, discount_Percentage

index="price_demo" source="prices.csv" | eval discount = round ((price - sale_price)*100/price,2) |  stats count by discount

index="price_demo" source="prices.csv" | eval discount = round ((price - sale_price)*100/price,2) |sort discount| table productId, product_name, price, sale_price, discount, code
