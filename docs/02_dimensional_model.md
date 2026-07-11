Fact table: FactStockPrice

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
<img width="997" height="572" alt="data modelling" src="https://github.com/user-attachments/assets/c413cc45-6e82-4653-a4ad-db350e42bd2e" />

