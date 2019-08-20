---
title: Iterovat přes kolekce vC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: d47dcf6e7748f85978b1b0bcf739b5d1280263f3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594961"
---
# <a name="iterators-c"></a>Iterátory (C#)

*Iterátor* se dá použít ke krokování kolekcí, jako jsou seznamy a pole.

Metoda iterátoru nebo `get` přistupující objekt provádí vlastní iteraci v kolekci. Metoda iterátoru používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého prvku v jednom okamžiku. Při dosažení `yield return` příkazu je aktuální umístění v kódu zapamatovatelné. Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.

Můžete využít iterátor z klientského kódu pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) nebo pomocí dotazu LINQ.

V následujícím příkladu první iterace `foreach` smyčky způsobí, že provádění pokračuje `SomeNumbers` v metodě iterátoru, dokud není dosaženo prvního `yield return` příkazu. Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru se zachová. Při další iteraci smyčky pokračuje spuštění v metodě iterátoru z místa, kde skončilo, a opětovné zastavení při dosažení `yield return` příkazu. Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru se znovu zachová. Smyčka skončí po dosažení konce metody iterátoru.

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

`get` Návratový typ metody iterátoru nebo přístupového objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.

K ukončení iterace `yield break` můžete použít příkaz.

> [!NOTE]
> Pro všechny příklady v tomto tématu s výjimkou příkladu jednoduchého iterátoru přidejte direktivy `System.Collections` using pro obory názvů a. [](../../language-reference/keywords/using-directive.md) `System.Collections.Generic`

## <a name="simple-iterator"></a>Jednoduchý iterátor

Následující příklad obsahuje jediný `yield return` příkaz, který je uvnitř smyčky [for](../../language-reference/keywords/for.md) . V `Main`, Každá iterace `foreach` těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `yield return` příkazu.

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

V následujícím příkladu `DaysOfTheWeek` třída <xref:System.Collections.IEnumerable> implementuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> rozhraní, které vyžaduje metodu. Kompilátor implicitně volá `GetEnumerator` metodu, která <xref:System.Collections.IEnumerator>vrací.

Metoda vrátí každý řetězec po jednom v čase `yield return` pomocí příkazu. `GetEnumerator`

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

Příkaz, který odkazuje na instanci třídy (`theZoo` `GetEnumerator` ) implicitně volá metodu. `foreach` Příkazy, které odkazují `Birds` na vlastnosti a `Mammals` používají `AnimalsForType` metodu s názvem iterátor. `foreach`

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

V následujícím příkladu <xref:System.Collections.Generic.Stack%601> obecná třída <xref:System.Collections.Generic.IEnumerable%601> implementuje obecné rozhraní. Metoda přiřadí hodnoty k poli typu `T`. <xref:System.Collections.Generic.Stack%601.Push%2A> Metoda vrací hodnoty pole `yield return` pomocí příkazu. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>

Kromě obecné <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody musí být také implementována neobecná <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. Důvodem je, <xref:System.Collections.Generic.IEnumerable%601> že dědí <xref:System.Collections.IEnumerable>z. Neobecná implementace se odloží k obecné implementaci.

Tento příklad používá pojmenované iterátory k podpoře různých způsobů iterace v rámci stejné kolekce dat. Tyto pojmenované iterátory jsou `TopToBottom` vlastnosti a `BottomToTop` a `TopN` metoda.

Vlastnost používá iterátor `get` v přístupovém objektu. `BottomToTop`

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

Iterátor se může vyskytnout jako metoda nebo `get` přistupující objekt. Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statické finalizační metody.

Implicitní převod musí existovat v typu výrazu v `yield return` příkazu na argument typu pro typ IEnumerable\<T > vrácený iterátorem.

V C#nástroji iterátor nemůže mít žádné `in`parametry, `ref`nebo `out` .

V C#znamená, že "yield" není rezervované slovo a má zvláštní význam pouze v `return` případě, že je použit před klíčovým slovem or. `break`

## <a name="technical-implementation"></a>Technická implementace

I když zapisujete iterátor jako metodu, kompilátor je převede na vnořenou třídu, která je v podstatě Stavový počítač. Tato třída uchovává informace o poloze iterátoru, dokud `foreach` smyčka v kódu klienta pokračuje.

Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm. exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.

Při vytváření iterátoru pro [třídu](../../language-reference/keywords/class.md) nebo [strukturu](../../language-reference/keywords/struct.md)není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní. Když kompilátor detekuje iterátor, automaticky `Current`generuje metody <xref:System.Collections.IEnumerator> , `MoveNext`a `Dispose` rozhraní nebo <xref:System.Collections.Generic.IEnumerator%601> .

U každé následné iterace `foreach` smyčky (nebo přímého `IEnumerator.MoveNext`volání) pokračuje další tělo kódu iterátoru za předchozím `yield return` příkazem. Pak pokračuje k dalšímu `yield return` příkazu až do konce textu iterátoru nebo `yield break` do doby, než se dorazí na příkaz.

Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metodu. K opakování iterace od začátku musíte získat nový iterátor. Volání <xref:System.Collections.IEnumerator.Reset%2A> iterátoru vráceného metodou iterátoru <xref:System.NotSupportedException>vyvolá.

Další informace najdete v [ C# tématu Specifikace jazyka](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Používání iterátorů

Iterátory umožňují udržovat jednoduchost `foreach` smyčky, pokud potřebujete použít složitý kód k naplnění pořadí seznamu. To může být užitečné v případě, že chcete provést následující akce:

- Změňte pořadí seznamu po iteraci první `foreach` smyčky.

- Vyhněte se úplnému načítání velkého seznamu před první iterací `foreach` smyčky. Příkladem stránkovaného načtení je načtení dávky řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rámci .NET Framework.

- Zapouzdřit sestavení seznamu v iterátoru. V metodě iterátoru můžete sestavit seznam a pak každý výsledek vracet ve smyčce.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Použití příkazu foreach s poli](../arrays/using-foreach-with-arrays.md)
- [Obecné typy](../generics/index.md)
