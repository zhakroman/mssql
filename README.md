# R library for MS SQL

```R
DB <- MSSQL()

DB$schema   <- 'dbo'
DB$database <- 'datascience'

if(!DB$use.in('VERSION_CONTROL')) {
  glue('
         CREATE TABLE [VERSION_CONTROL] (
          ID nvarchar(35) NOT NULL,
          DATET DATE NOT NULL,
          DEPS nvarchar(MAX) NULL,
        CONSTRAINT ID_UQ UNIQUE(ID) 
     )'
  ) %>% 
 DB$sql()
}

DB$use.table('VERSION_CONTROL')

c('c_3', '~date', 'NULL') %>%
 DB$insert()
 
```
