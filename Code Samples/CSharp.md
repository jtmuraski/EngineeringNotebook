### Parse a One to Many sql query result to an object
This is an example of a a way to parse a 1 to many SQL query into an object
```
// ---Sample objects---
public class Person
{
	public int Id;
	private string First Name;
	private string LastName;
	private int Age;
	public List<Address> PlacesLived = new List<Address>();
}

public class Address
{
	public int Id;
	public int PersonId;
	public string Street;
	public string Town;
	public string State;
	public string ZipCode; 
}

// Sql Query returns a single Person and a list of all the addresses that they have had
// Assuming the query and sql command have already been created

using(SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
{
	List<Person> persons = new List<Person>();
	while(reader.Read())
	{
		var personId = reader.GetInt32(reader.GetOrdinal("Id"))
		var person = persons.SingleOrDefault(p => p.Id == personId);
		if(person == null)
		{
			person.FirstName = //first name
			person.LastName = //last name
			person.Age = // age
			person.PlacesLived.Add(new Address)
			{
				Id = //id
				PersonId = persons.Id,
				Street = //street
				Town = //town
				State = //state
				ZipCode = //zipcode
			});
			persons.Add(person);			
	     }
		else
		{
			Address place = new Address)
			{
				Id = //id
				PersonId = persons.Id,
				Street = //street
				Town = //town
				State = //state
				ZipCode = //zipcode
			});
			if(!persons.PlacesLived.Contains(place))
				persons.PlacesLived.Add(place);
		}
	}
}
```

### Check if a number is a Power of 2
In order to find if a number is a Power of 2, take the Log base 2 of the number. if the result is an integer, it is a power of 2.
```
using System;

public static class Kata
{
  public static bool PowerOfTwo(int n)
  {
    if(n == 0)
      return false;
    else if(n== 1)
      return true;
    else if(n % 2 == 1)
      return false;
    
    return Math.Log2(n) % 1 == 0;
  }
}
```