# SyntacticSugarInCSharp
## **References**

- [Expression-bodied function members](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members)
- [Automatic property initializers](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-6#auto-property-initializers)
- [C# ternary operator](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator)
- [Switch Expression](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression)

## **Instructions**

1. Copy the code below into your `Program.cs`, inside the namespace, but outside of the `Program` class.  Then convert all of the class methods to an expression-bodied function member.
2. Create some instances of your class in the `Main` method and invoke their methods.

```csharp
public class Bug
{
    /*
        You can declare a typed public property, make it read-only,
        and initialize it with a default value all on the same
        line of code in C#. Readonly properties can be set in the
        class' constructors, but not by external code.
    */
    public string Name { get; } = "";
    public string Species { get; } = "";
    public List<string> Predators { get; } = new List<string>();
    public List<string> Prey { get; } = new List<string>();

    // Convert this readonly property to an expression member
    public string FormalName
    {
        get
        {
            return $"{this.Name} the {this.Species}";
        }
    }

    // Class constructor
    public Bug(string name, string species, List<string> predators, List<string> prey)
    {
        this.Name = name;
        this.Species = species;
        this.Predators = predators;
        this.Prey = prey;
    }

    // Convert this method to an expression member
    public string PreyList()
    {
        var commaDelimitedPrey = string.Join(",", this.Prey);
        return commaDelimitedPrey;
    }

    // Convert this method to an expression member
    public string PredatorList()
    {
        var commaDelimitedPredators = string.Join(",", this.Predators);
        return commaDelimitedPredators;
    }

    // Convert this to expression method
    public string Eat(string food)
    {
        if (this.Prey.Contains(food))
        {
            return $"{this.Name} ate the {food}.";
        } else {
            return $"{this.Name} is still hungry.";
        }
    }
}
```
