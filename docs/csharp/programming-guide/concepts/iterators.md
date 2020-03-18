---
title: 'Iterate prostřednictvím sbírek v C #'
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626267"
---
# <a name="iterators-c"></a>Iterátory (C#)

*Iterátor* lze krokovat kolekce, jako jsou seznamy a pole.

Iterator metoda `get` nebo přistupující objekt provádí vlastní iteraci přes kolekci. Metoda iterátoru používá yield [return](../../language-reference/keywords/yield.md) příkaz vrátit každý prvek jeden po druhém. Po `yield return` dosažení příkazu je zapamatováno aktuální umístění v kódu. Spuštění je restartován z tohoto umístění při příštím volání funkce iterátoru.

Spotřebováváte iterátor z klientského kódu pomocí [foreach](../../language-reference/keywords/foreach-in.md) příkaz nebo pomocí dotazu LINQ.

V následujícím příkladu první iterace `foreach` smyčky způsobí, `SomeNumbers` že spuštění pokračovat v `yield return` iterátoru metody, dokud je dosaženo prvního příkazu. Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru je zachováno. Na další iteraci smyčky provádění v iterátoru metoda pokračuje od místa, kde `yield return` přestal, opět zastavení, když dosáhne příkazu. Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru je opět zachováno. Smyčka se dokončí po dosažení konce metody iterátoru.

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

Návratový typ metody iterátoru `get` nebo přistupujícího objektu <xref:System.Collections.IEnumerable>může být <xref:System.Collections.Generic.IEnumerable%601>, , <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.

K ukončení `yield break` iterace můžete použít příkaz.

> [!NOTE]
> Pro všechny příklady v tomto tématu s výjimkou simple iterátor `System.Collections.Generic` příklad, patří [použití](../../language-reference/keywords/using-directive.md) direktivy pro `System.Collections` a obory názvů.

## <a name="simple-iterator"></a>Jednoduchý iterátor

Následující příklad má `yield return` jeden příkaz, který je uvnitř [for](../../language-reference/keywords/for.md) smyčky. V `Main`aplikaci každá `foreach` iterace těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `yield return` příkazu.

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a>Vytvoření třídy kolekce

V následujícím příkladu `DaysOfTheWeek` třída implementuje <xref:System.Collections.IEnumerable> rozhraní, <xref:System.Collections.IEnumerable.GetEnumerator%2A> které vyžaduje metodu. Kompilátor implicitně `GetEnumerator` volá metodu, <xref:System.Collections.IEnumerator>která vrací .

Metoda `GetEnumerator` vrátí každý řetězec jeden po `yield return` druhém pomocí příkazu.

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.

Příkaz, `foreach` který odkazuje na instanci třídy (`theZoo`) implicitně volá metodu. `GetEnumerator` `foreach` Příkazy, které `Birds` odkazují `Mammals` na `AnimalsForType` vlastnosti a používají metodu pojmenovaný iterátor.

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a>Používání iterátorů v obecných seznamech

V následujícím příkladu <xref:System.Collections.Generic.Stack%601> obecná třída <xref:System.Collections.Generic.IEnumerable%601> implementuje obecné rozhraní. Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> přiřazuje hodnoty `T`poli typu . Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> vrátí hodnoty pole pomocí `yield return` příkazu.

Kromě obecné <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody musí být implementována i neobecná <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. Důvodem <xref:System.Collections.Generic.IEnumerable%601> je, <xref:System.Collections.IEnumerable>že dědí z . Neobecná implementace se odkládá na obecnou implementaci.

Příklad používá pojmenované iterátory pro podporu různých způsobů iterace prostřednictvím stejné kolekce dat. Tyto pojmenované iterátory `TopToBottom` jsou `BottomToTop` vlastnosti `TopN` a a metoda.

Vlastnost `BottomToTop` používá iterátor v `get` přistupujícím objektu.

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a>Informace o syntaxi

Iterátor může dojít jako metoda `get` nebo přistupující objekt. Iterátor nemůže dojít v události, instance konstruktor, statický konstruktor nebo statický finalizační prostředek.

Implicitní převod musí existovat z `yield return` typu výrazu v `IEnumerable<T>` příkazu na argument typu pro vrácený iterátorem.

V c#, iterátor metoda nemůže `in` `ref`mít `out` žádné , , nebo parametry.

V C# `yield` není vyhrazené slovo a má zvláštní význam pouze `return` `break` v případě, že se používá před nebo klíčové slovo.

## <a name="technical-implementation"></a>Technická implementace

I když píšete iterátor jako metodu, kompilátor překládá do vnořené třídy, která je ve skutečnosti stavový počítač. Tato třída udržuje informace o pozici iterátoru `foreach` tak dlouho, dokud bude smyčka v kódu klienta pokračovat.

Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm.exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.

Při vytváření iterátoru pro [třídu](../../language-reference/keywords/class.md) nebo [strukturu](../../language-reference/builtin-types/struct.md), není nutné <xref:System.Collections.IEnumerator> implementovat celé rozhraní. Když kompilátor detekuje iterátor, automaticky generuje `Current`, `MoveNext`a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.

Na každé následné `foreach` iteraci smyčky (nebo přímé volání `IEnumerator.MoveNext`na ), další iterátor kód tělo pokračuje po předchozí `yield return` příkaz. Potom pokračuje k `yield return` dalšímu příkazu, dokud není dosaženo konce těla `yield break` iterátoru nebo dokud není zjištěn příkaz.

Iterátory nepodporují metodu. <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> Chcete-li zopakovat od začátku, musíte získat nový iterátor. Volání <xref:System.Collections.IEnumerator.Reset%2A> na iterátoru vrácené metodou iterátoru <xref:System.NotSupportedException>vyvolá .

Další informace naleznete v jazykové [specifikaci jazyka C#](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Používání iterátorů

Iterátory umožňují zachovat jednoduchost smyčky, `foreach` když potřebujete použít složitý kód k naplnění pořadí seznamu. To může být užitečné, pokud chcete provést následující kroky:

- Po první `foreach` iteraci smyčky upravte pořadí seznamu.

- Vyhněte se úplnému načtení `foreach` velkého seznamu před první iterací smyčky. Příkladem je stránkované načtení pro načtení dávky řádků tabulky. Dalším příkladem <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> je metoda, která implementuje iterátory v rámci rozhraní .NET Framework.

- Zapouzdření vytváření seznamu v iterátoru. V metodě iterátoru můžete sestavit seznam a potom výtěžnost každý výsledek ve smyčce.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Použití příkazu foreach s poli](../arrays/using-foreach-with-arrays.md)
- [Obecné typy](../generics/index.md)
