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

c('c_3', '~date', 'prev') %>%
 DB$insert()
 
 DB$f('Persons') %>%                              # from 
  DB$s('name, SUM(salary)') %>%                   # select 
  DB$w('name IN ({1})', c('RU', 'UA', 'BY')) %>%  # where 
  DB$g('name') %>%                                # group by   
  DB$o('salary') %>%                              # order by 
  DB$l(100) %>%                                   # limit   
  DB$h('[2] > 100') # means: SUM(salary) > 100    # having 
  DB$d('[1]') # means distinct name               # distinct                                    
 
```
