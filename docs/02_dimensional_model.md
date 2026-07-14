Fact table: FactStockPrice

One row represents one stock's trading activity for one trading day
ex: 
<img width="672" height="47" alt="image" src="https://github.com/user-attachments/assets/1cb8ca92-c7f0-4b2b-b529-54f53dca97da" />



    Columns: 
      StockKey
      DateKey
      OpenPrice
      HighPrice
      LowPrice
      ClosePrice
      Volume
      DailyReturn

Dimension Tables:
  1.  DimStock

    Columns:
      StockKey	
      Symbol	
      Company	
      Sector

  2.   DimDate

    Columns: 
      DateKey	
      Date	
      Year	
      Month	
      Quarter

  3.   DimSector

    Columns: 
      SectorKey	
      Sector	

StockKey, DateKey, SectorKey are surrogate keys.

Surrogate keys are generated internally and used for dimension joins instead of natural keys.

<img width="997" height="572" alt="data modelling" src="https://github.com/user-attachments/assets/c413cc45-6e82-4653-a4ad-db350e42bd2e" />

