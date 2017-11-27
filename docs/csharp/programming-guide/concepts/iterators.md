---
title: "Iterátory (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d4994ea57d9fd0df8dfca7ffa40c280499caee6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iterators-c"></a><span data-ttu-id="5e4fd-102">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="5e4fd-102">Iterators (C#)</span></span>
<span data-ttu-id="5e4fd-103">*Iterator* slouží k krok prostřednictvím kolekcí, jako například seznamy a maticových.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="5e4fd-104">Metodu iterator nebo `get` přistupujícího objektu provede vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="5e4fd-105">Používá metodu iterator [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit každý element, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-105">An iterator method uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="5e4fd-106">Když `yield return` příkaz je dosaženo, uloží je aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="5e4fd-107">Provádění restartování z tohoto umístění při příštím iterator funkce je volána.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="5e4fd-108">Využívat iterovat z klientského kódu pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-108">You consume an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="5e4fd-109">V následujícím příkladu, první iterace `foreach` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` iterator – metoda dokud první `yield return` je dosaženo příkaz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="5e4fd-110">Tato iterace vrací hodnotu 3 a aktuální umístění v metodě iterator zůstane.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="5e4fd-111">Na další iteraci smyčky, pokračuje spuštění v metodě iterator odkud bylo přerušeno, znovu zastavit při dosažení `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="5e4fd-112">Tento iterace vrací hodnotu 5 a opakujte aktuální umístění v metodě iterator zůstane.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="5e4fd-113">Když je dosaženo konce iterator metody dokončení smyčky.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
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
  
 <span data-ttu-id="5e4fd-114">Návratový typ metody iterator nebo `get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="5e4fd-115">Můžete použít `yield break` příkaz k ukončení iterace.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-115">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="5e4fd-116">Iterátory byly zavedeny v jazyce C# v sadě Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-116">Iterators were introduced in C# in Visual Studio 2005.</span></span>  
  
 <span data-ttu-id="5e4fd-117">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="5e4fd-117">**In this topic**</span></span>  
  
-   [<span data-ttu-id="5e4fd-118">Jednoduché iterátorů</span><span class="sxs-lookup"><span data-stu-id="5e4fd-118">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="5e4fd-119">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="5e4fd-119">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="5e4fd-120">Pomocí seznamu obecné iterátory</span><span class="sxs-lookup"><span data-stu-id="5e4fd-120">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="5e4fd-121">Informace ze syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e4fd-121">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="5e4fd-122">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="5e4fd-122">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="5e4fd-123">Použití iterátory</span><span class="sxs-lookup"><span data-stu-id="5e4fd-123">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="5e4fd-124">Všechny příklady v tomto tématu, s výjimkou Iterator jednoduchý příklad, zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections` a `System.Collections.Generic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-124">For all examples in this topic except the Simple Iterator example, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <span data-ttu-id="5e4fd-125"><a name="BKMK_SimpleIterator"></a>Jednoduché iterátorů</span><span class="sxs-lookup"><span data-stu-id="5e4fd-125"><a name="BKMK_SimpleIterator"></a> Simple Iterator</span></span>  
 <span data-ttu-id="5e4fd-126">V následujícím příkladu má jeden `yield return` příkaz, který je uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-126">The following example has a single `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="5e4fd-127">V `Main`, každé iteraci `foreach` těla příkazu vytvoří volání funkce iterator, který bude pokračovat na další `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-127">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>  
  
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
  
##  <span data-ttu-id="5e4fd-128"><a name="BKMK_CollectionClass"></a>Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="5e4fd-128"><a name="BKMK_CollectionClass"></a> Creating a Collection Class</span></span>  
 <span data-ttu-id="5e4fd-129">V následujícím příkladu `DaysOfTheWeek` třída implementuje <xref:System.Collections.IEnumerable> rozhraní, což vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-129">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="5e4fd-130">Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-130">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="5e4fd-131">`GetEnumerator` Metoda vrátí každý řetězec jeden současně pomocí `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-131">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>  
  
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
  
 <span data-ttu-id="5e4fd-132">Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-132">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="5e4fd-133">`foreach` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metoda.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-133">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="5e4fd-134">`foreach` Příkazy, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem iterator – metoda.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-134">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
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
  
##  <span data-ttu-id="5e4fd-135"><a name="BKMK_GenericList"></a>Pomocí seznamu obecné iterátory</span><span class="sxs-lookup"><span data-stu-id="5e4fd-135"><a name="BKMK_GenericList"></a> Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="5e4fd-136">V následujícím příkladu `Stack(Of T)` – obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-136">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="5e4fd-137">`Push` Metoda přiřadí hodnoty do pole typu `T`.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-137">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="5e4fd-138"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot pomocí `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-138">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>  
  
 <span data-ttu-id="5e4fd-139">Kromě obecná <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, neobecnou <xref:System.Collections.IEnumerable.GetEnumerator%2A> také musí být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-139">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="5e4fd-140">Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-140">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="5e4fd-141">Implementace neobecnou odkládat údaje pro obecnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-141">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="5e4fd-142">Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-142">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="5e4fd-143">Jsou to s názvem iterátory `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-143">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="5e4fd-144">`BottomToTop` Vlastnost používá iterace v `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-144">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>  
  
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
  
##  <span data-ttu-id="5e4fd-145"><a name="BKMK_SyntaxInformation"></a>Informace ze syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e4fd-145"><a name="BKMK_SyntaxInformation"></a> Syntax Information</span></span>  
 <span data-ttu-id="5e4fd-146">Může dojít iterator jako metodu nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-146">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="5e4fd-147">Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-147">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>  
  
 <span data-ttu-id="5e4fd-148">Musí existovat implicitní převod z typu výrazu v `yield return` příkaz, který má návratový typ iteraci.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-148">An implicit conversion must exist from the expression type in the `yield return` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="5e4fd-149">V jazyce C#, nemůže obsahovat metodu iterator ani `ref` nebo `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-149">In C#, an iterator method cannot have any `ref` or `out` parameters.</span></span>  
  
 <span data-ttu-id="5e4fd-150">V jazyce C#, "výnos" není vyhrazené slovo a má zvláštní význam jenom v případě, že se používá před `return` nebo `break` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-150">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>  
  
##  <span data-ttu-id="5e4fd-151"><a name="BKMK_Technical"></a>Technická implementace</span><span class="sxs-lookup"><span data-stu-id="5e4fd-151"><a name="BKMK_Technical"></a> Technical Implementation</span></span>  
 <span data-ttu-id="5e4fd-152">I když napíšete iterovat jako metodu, kompilátor převede jej do vnořené třídy ve výsledku, který je stav počítače.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-152">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="5e4fd-153">Tato třída uchovává informace o umístění iterator jako dlouho `foreach` pokračuje smyčky v kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-153">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="5e4fd-154">Pokud chcete zobrazit, jaké kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který se vygeneruje pro metodu iterator.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-154">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="5e4fd-155">Při vytváření iterace pro [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), nemáte k implementaci celek <xref:System.Collections.IEnumerator> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-155">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="5e4fd-156">Zjistí-li kompilátor iteraci, automaticky vygeneruje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-156">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="5e4fd-157">Při každém opakování následných `foreach` smyčky (nebo přímé volání `IEnumerator.MoveNext`), těle další kód iterator obnoví po předchozí `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-157">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="5e4fd-158">Bude pokračovat na další `yield return` prohlášení, dokud je dosaženo konce iterator text, nebo dokud `yield break` příkaz je zjistil.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-158">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>  
  
 <span data-ttu-id="5e4fd-159">Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-159">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e4fd-160">Chcete-li procházení znovu od začátku, je nutné získat nové iterator.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-160">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="5e4fd-161">Další informace najdete v tématu [specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e4fd-161">For additional information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
##  <span data-ttu-id="5e4fd-162"><a name="BKMK_UseOfIterators"></a>Použití iterátory</span><span class="sxs-lookup"><span data-stu-id="5e4fd-162"><a name="BKMK_UseOfIterators"></a> Use of Iterators</span></span>  
 <span data-ttu-id="5e4fd-163">Iterátory umožňují zachovat jednoduchost `foreach` cykly, když potřebujete použít složitý kód pro naplnění seznamu pořadí.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-163">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="5e4fd-164">To může být užitečné, pokud chcete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="5e4fd-164">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="5e4fd-165">Změňte pořadí seznamu po první `foreach` cykly iterací.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-165">Modify the list sequence after the first `foreach` loop iteration.</span></span>  
  
-   <span data-ttu-id="5e4fd-166">Vyhněte se plně načítání velkých seznamu před první iterace `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-166">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="5e4fd-167">Příkladem je stránkové fetch načíst dávku řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-167">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="5e4fd-168">Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-168">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="5e4fd-169">Zapouzdření vytváření seznamu v iteraci.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-169">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="5e4fd-170">V metodě iterator můžete sestavit v seznamu a pak yield každý výsledek ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-170">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4fd-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e4fd-171">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="5e4fd-172">foreach v</span><span class="sxs-lookup"><span data-stu-id="5e4fd-172">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="5e4fd-173">YIELD –</span><span class="sxs-lookup"><span data-stu-id="5e4fd-173">yield</span></span>](../../../csharp/language-reference/keywords/yield.md)  
 [<span data-ttu-id="5e4fd-174">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="5e4fd-174">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
 [<span data-ttu-id="5e4fd-175">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="5e4fd-175">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
