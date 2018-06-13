---
title: Iterátory (C#)
ms.date: 07/20/2015
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 08fe529f46ccaae7b2e17367a47346265aa0e8b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338868"
---
# <a name="iterators-c"></a>Iterátory (C#)
*Iterator* slouží k krok prostřednictvím kolekcí, jako například seznamy a maticových.  
  
 Metodu iterator nebo `get` přistupujícího objektu provede vlastní iteraci přes kolekci. Používá metodu iterator [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit každý element, jeden v čase. Když `yield return` příkaz je dosaženo, uloží je aktuální umístění v kódu. Provádění restartování z tohoto umístění při příštím iterator funkce je volána.  
  
 Využívat iterovat z klientského kódu pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz nebo pomocí dotazu LINQ.  
  
 V následujícím příkladu, první iterace `foreach` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` iterator – metoda dokud první `yield return` je dosaženo příkaz. Tato iterace vrací hodnotu 3 a aktuální umístění v metodě iterator zůstane. Na další iteraci smyčky, pokračuje spuštění v metodě iterator odkud bylo přerušeno, znovu zastavit při dosažení `yield return` příkaz. Tento iterace vrací hodnotu 5 a opakujte aktuální umístění v metodě iterator zůstane. Když je dosaženo konce iterator metody dokončení smyčky.  
  
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
  
 Návratový typ metody iterator nebo `get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Můžete použít `yield break` příkaz k ukončení iterace.  
  
 Iterátory byly zavedeny v jazyce C# v sadě Visual Studio 2005.  
  
 **V tomto tématu**  
  
-   [Jednoduché iterátorů](#BKMK_SimpleIterator)  
  
-   [Vytvoření třídy kolekce](#BKMK_CollectionClass)  
  
-   [Pomocí seznamu obecné iterátory](#BKMK_GenericList)  
  
-   [Informace ze syntaxe](#BKMK_SyntaxInformation)  
  
-   [Technická implementace](#BKMK_Technical)  
  
-   [Použití iterátory](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Všechny příklady v tomto tématu, s výjimkou Iterator jednoduchý příklad, zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections` a `System.Collections.Generic` obory názvů.  
  
##  <a name="BKMK_SimpleIterator"></a> Jednoduché iterátorů  
 V následujícím příkladu má jeden `yield return` příkaz, který je uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky. V `Main`, každé iteraci `foreach` těla příkazu vytvoří volání funkce iterator, který bude pokračovat na další `yield return` příkaz.  
  
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
  
##  <a name="BKMK_CollectionClass"></a> Vytvoření třídy kolekce  
 V následujícím příkladu `DaysOfTheWeek` třída implementuje <xref:System.Collections.IEnumerable> rozhraní, což vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Metoda vrátí každý řetězec jeden současně pomocí `yield return` příkaz.  
  
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
  
 `foreach` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metoda. `foreach` Příkazy, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem iterator – metoda.  
  
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
  
##  <a name="BKMK_GenericList"></a> Pomocí seznamu obecné iterátory  
 V následujícím příkladu `Stack(Of T)` – obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní. `Push` Metoda přiřadí hodnoty do pole typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot pomocí `yield return` příkaz.  
  
 Kromě obecná <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, neobecnou <xref:System.Collections.IEnumerable.GetEnumerator%2A> také musí být implementována metoda. Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>. Implementace neobecnou odkládat údaje pro obecnou implementaci.  
  
 Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory. Jsou to s názvem iterátory `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.  
  
 `BottomToTop` Vlastnost používá iterace v `get` přistupujícího objektu.  
  
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
    // foreach is allowed because theStack implements  
    // IEnumerable<int>.  
    foreach (int number in theStack)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    // foreach is allowed, because theStack.TopToBottom  
    // returns IEnumerable(Of Integer).  
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
  
##  <a name="BKMK_SyntaxInformation"></a> Informace ze syntaxe  
 Může dojít iterator jako metodu nebo `get` přistupujícího objektu. Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické finalizační metodu.  
  
 Musí existovat implicitní převod z typu výrazu v `yield return` příkaz, který má návratový typ iteraci.  
  
 V jazyce C#, nemůže obsahovat metodu iterator ani `in`, `ref`, nebo `out` parametry.  
  
 V jazyce C#, "výnos" není vyhrazené slovo a má zvláštní význam jenom v případě, že se používá před `return` nebo `break` – klíčové slovo.  
  
##  <a name="BKMK_Technical"></a> Technická implementace  
 I když napíšete iterovat jako metodu, kompilátor převede jej do vnořené třídy ve výsledku, který je stav počítače. Tato třída uchovává informace o umístění iterator jako dlouho `foreach` pokračuje smyčky v kódu klienta.  
  
 Pokud chcete zobrazit, jaké kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který se vygeneruje pro metodu iterator.  
  
 Při vytváření iterace pro [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), nemáte k implementaci celek <xref:System.Collections.IEnumerator> rozhraní. Zjistí-li kompilátor iteraci, automaticky vygeneruje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.  
  
 Při každém opakování následných `foreach` smyčky (nebo přímé volání `IEnumerator.MoveNext`), těle další kód iterator obnoví po předchozí `yield return` příkaz. Bude pokračovat na další `yield return` prohlášení, dokud je dosaženo konce iterator text, nebo dokud `yield break` příkaz je zjistil.  
  
 Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metoda. Chcete-li procházení znovu od začátku, je nutné získat nové iterator.  
  
 Další informace najdete v tématu [specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).  
  
##  <a name="BKMK_UseOfIterators"></a> Použití iterátory  
 Iterátory umožňují zachovat jednoduchost `foreach` cykly, když potřebujete použít složitý kód pro naplnění seznamu pořadí. To může být užitečné, pokud chcete provést následující akce:  
  
-   Změňte pořadí seznamu po první `foreach` cykly iterací.  
  
-   Vyhněte se plně načítání velkých seznamu před první iterace `foreach` smyčky. Příkladem je stránkové fetch načíst dávku řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rozhraní .NET Framework.  
  
-   Zapouzdření vytváření seznamu v iteraci. V metodě iterator můžete sestavit v seznamu a pak yield každý výsledek ve smyčce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [yield](../../../csharp/language-reference/keywords/yield.md)  
 [Použití příkazu foreach s poli](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)
