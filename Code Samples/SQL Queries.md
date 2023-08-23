#### Get the Id back after insert
```
INSERT INTO (table) (col1, col2, col3...)
VALUES (val1, val2, val3,...);
SELECT CAST(SCOPE_IDENTITY() AS int) AS 'Identity';
```

This return the Id value of an auto incrememnted identity from a SQL Server table. Can execute the quest in the following ways:
_C#_
```
SqlCommand cmd = new SqlCommand(query, conn);
using(conn)
using(cmd)
{
	conn.Open();
	int id = (int)cmd.ExecuteScaler();
}
```

______
