# R library for MS SQL

```
DB <- MSSQL()

DB$schema   <- 'dbo'
DB$database <- 'datascience'

if(!DB$use.in('temptable')) {
  glue('
         CREATE TABLE dbo.[WSPR_VERSION_CONTROL] (
          ID nvarchar(35) NOT NULL,
          DATET DATE NOT NULL,
          DEPS nvarchar(MAX) NULL,
        CONSTRAINT ID_UQ UNIQUE(ID) 
     )'
  ) %>% 
 DB$sql()
}
```
