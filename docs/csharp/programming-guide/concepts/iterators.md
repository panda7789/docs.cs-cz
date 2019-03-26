---
title: Iterovat kolekcí v jazyce C#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 2b0e1d509cf80e13d2cee3cf0ddf2021d6c84c5b
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464317"
---
# <a name="iterators-c"></a>Iterátory (C#)

*Iterátoru* slouží k procházení kolekcí, jako je seznamy a pole.

Metodu iterátoru nebo `get` přistupující objekt provádí vlastní iterace nad kolekcí. Využívá metoda iterace [yield return](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit vždy jeden prvek v čase. Když `yield return` je dosažen příkaz, se uloží aktuální umístění v kódu. Provádění je restartováno z tohoto umístění při příštím je zavolána funkce iterátoru.

Využívat iterátor z klientského kódu pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz nebo pomocí dotazu LINQ.

V následujícím příkladu první iterace `foreach` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` metody iterátoru až do první `yield return` je dosažen příkaz. Tuto iteraci, vrátí hodnotu 3 a je zachováno aktuální umístění v metodě iterátoru. Na další iteraci smyčky v metodě iterátoru pokračuje odkud zastaví se opět tehdy, když se dosáhne `yield return` příkazu. Tuto iteraci, vrátí hodnotu 5 a znovu se uchovávají aktuální umístění v metodě iterátoru. Smyčky dokončí, když je dosaženo konce metody iterátoru.

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

Návratový typ metody iterátoru nebo `get` přistupující objekt může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.

Můžete použít `yield break` příkaz do konce iterace.

> [!NOTE]
> Všechny příklady v tomto tématu, s výjimkou příklad jednoduchý iterátor zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections` a `System.Collections.Generic` obory názvů.

## <a name="simple-iterator"></a>Jednoduchý iterátor

V následujícím příkladu má jeden `yield return` , který se nachází uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky. V `Main`, každá iterace `foreach` tělo s příkazy vytvoří volání funkce iterátoru, který pokračuje k dalšímu `yield return` příkazu.

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

V následujícím příkladu `DaysOfTheWeek` implementuje třída <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.

`GetEnumerator` Metoda vrátí jednotlivých řetězců, jeden po druhém pomocí `yield return` příkazu.

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

Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířata.

`foreach` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metody. `foreach` Příkazů, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem metody iterátoru.

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

V následujícím příkladu <xref:System.Collections.Generic.Stack%601> obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecného rozhraní. <xref:System.Collections.Generic.Stack%601.Push%2A> Metoda přiřadí hodnoty do pole typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot s použitím `yield return` příkazu.

Kromě obecného <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody, který není obecný <xref:System.Collections.IEnumerable.GetEnumerator%2A> musí také být implementována metoda. Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>. Implementace neobecnou odloží na obecnou implementaci.

Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory. Tyto iterátory s názvem jsou `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.

`BottomToTop` Vlastnost používá iterátor v `get` přistupujícího objektu.

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

Iterátor může dojít, jako metodu nebo `get` přistupujícího objektu. V události, konstruktor instance, statický konstruktor nebo statická finalizační metoda nemůže dojít k iterátoru.

Musí existovat implicitní převod z typu výrazu v `yield return` příkaz na argument typu pro IEnumerable\<T > vrátí iterátor.

V jazyce C#, nemůže obsahovat metodu iterátoru ani `in`, `ref`, nebo `out` parametry.

V jazyce C#, "yield" není vyhrazené slovo a má zvláštní význam pouze v případě, že je použitá před `return` nebo `break` – klíčové slovo.

## <a name="technical-implementation"></a>Technická implementace

I když píšete iterátoru jako metodu, kompilátor přeloží ho do vnořené třídy, který je, v důsledku toho stavového stroje. Tato třída uchovává informace o pozice iterátoru jako dlouho `foreach` pokračuje smyčka v kódu klienta.

Pokud chcete zobrazit, co dělá kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který je generován pro metodu iterátoru.

Při vytváření iterátor pro [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní. Když kompilátor zjistí iterátoru, automaticky generuje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.

Na každou následnou iterací z `foreach` smyčky (nebo přímého volání `IEnumerator.MoveNext`), další kód tělo iterátoru pokračuje po předchozí `yield return` příkazu. Bude pokračovat na další `yield return` příkaz, dokud je dosaženo konce tělo iterátoru, nebo dokud `yield break` příkaz dochází.

Nepodporují iterátory <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Zdůrazňujeme od začátku, musíte získat nový iterátoru. Volání <xref:System.Collections.IEnumerator.Reset%2A> na iterátor vrácené z metody iterátoru vyvolá <xref:System.NotSupportedException>.

Další informace najdete v tématu [specifikace jazyka C#](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Používání iterátorů

Iterátory umožňují udržovat jednoduchost `foreach` smyčky, když budete chtít použít k naplnění seznamu pořadí složitého kódu. To může být užitečné, pokud chcete provést následující kroky:

- Pořadí seznamu změnit po prvním `foreach` iterace smyčky.

- Vyhněte se plně načítání velkých seznamu před první iteraci `foreach` smyčky. Příkladem je stránkovaného načtení načíst dávku řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodu, která implementuje iterátorů v rámci rozhraní .NET Framework.

- Zapouzdření vytváření seznamu v iterátoru. V metodě iterátoru můžete vytvořit seznam a potom yield každého výsledku ve smyčce.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)
- [yield](../../../csharp/language-reference/keywords/yield.md)
- [Použití příkazu foreach s poli](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)