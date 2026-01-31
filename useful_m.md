# Useful M Code Expressions

# Clean Column Names Function
```sql
let
  FormatColumnNames = (tbl as table) => 
  let 
    #"Replace Underscores" = Table.TransformColumnNames(tbl, each Text.Replace(_, "_", " ")),
    #"Capitalize Column Names" = Table.TransformColumnNames(#"Replace Underscores", Text.Proper),
    #"Clean Column Names" = Table.TransformColumnNames(#"Capitalize Column Names", Text.Clean),
    #"Trim Column Names" = Table.TransformColumnNames(#"Clean Column Names", Text.Trim)
  in
    #"Trim Column Names"
in
  FormatColumnNames
```