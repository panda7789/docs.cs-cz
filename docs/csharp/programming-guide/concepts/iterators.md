---
title: Iterovat kolekcí v jazyce C#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: d8a39569df517dffa8ff4b2f638f089f420e44c7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46569261"
---
# <a name="iterators-c"></a><span data-ttu-id="a8382-102">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="a8382-102">Iterators (C#)</span></span>

<span data-ttu-id="a8382-103">*Iterátoru* slouží k procházení kolekcí, jako je seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="a8382-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="a8382-104">Metodu iterátoru nebo `get` přistupující objekt provádí vlastní iterace nad kolekcí.</span><span class="sxs-lookup"><span data-stu-id="a8382-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="a8382-105">Využívá metoda iterace [yield return](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit vždy jeden prvek v čase.</span><span class="sxs-lookup"><span data-stu-id="a8382-105">An iterator method uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="a8382-106">Když `yield return` je dosažen příkaz, se uloží aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="a8382-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="a8382-107">Provádění je restartováno z tohoto umístění při příštím je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="a8382-108">Využívat iterátor z klientského kódu pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="a8382-108">You consume an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="a8382-109">V následujícím příkladu první iterace `foreach` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` metody iterátoru až do první `yield return` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="a8382-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="a8382-110">Tuto iteraci, vrátí hodnotu 3 a je zachováno aktuální umístění v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="a8382-111">Na další iteraci smyčky v metodě iterátoru pokračuje odkud zastaví se opět tehdy, když se dosáhne `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a8382-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="a8382-112">Tuto iteraci, vrátí hodnotu 5 a znovu se uchovávají aktuální umístění v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="a8382-113">Smyčky dokončí, když je dosaženo konce metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="a8382-114">Návratový typ metody iterátoru nebo `get` přistupující objekt může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="a8382-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="a8382-115">Můžete použít `yield break` příkaz do konce iterace.</span><span class="sxs-lookup"><span data-stu-id="a8382-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="a8382-116">Všechny příklady v tomto tématu, s výjimkou příklad jednoduchý iterátor zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections` a `System.Collections.Generic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a8382-116">For all examples in this topic except the Simple Iterator example, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="a8382-117">Jednoduchý iterátor</span><span class="sxs-lookup"><span data-stu-id="a8382-117">Simple Iterator</span></span>

<span data-ttu-id="a8382-118">V následujícím příkladu má jeden `yield return` , který se nachází uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="a8382-118">The following example has a single `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="a8382-119">V `Main`, každá iterace `foreach` tělo s příkazy vytvoří volání funkce iterátoru, který pokračuje k dalšímu `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a8382-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="a8382-120">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="a8382-120">Creating a Collection Class</span></span>

<span data-ttu-id="a8382-121">V následujícím příkladu `DaysOfTheWeek` implementuje třída <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a8382-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="a8382-122">Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="a8382-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="a8382-123">`GetEnumerator` Metoda vrátí jednotlivých řetězců, jeden po druhém pomocí `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a8382-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="a8382-124">Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířata.</span><span class="sxs-lookup"><span data-stu-id="a8382-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="a8382-125">`foreach` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metody.</span><span class="sxs-lookup"><span data-stu-id="a8382-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="a8382-126">`foreach` Příkazů, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="a8382-127">Používání iterátorů v obecných seznamech</span><span class="sxs-lookup"><span data-stu-id="a8382-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="a8382-128">V následujícím příkladu <xref:System.Collections.Generic.Stack%601> obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a8382-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="a8382-129"><xref:System.Collections.Generic.Stack%601.Push%2A> Metoda přiřadí hodnoty do pole typu `T`.</span><span class="sxs-lookup"><span data-stu-id="a8382-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="a8382-130"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot s použitím `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a8382-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="a8382-131">Kromě obecného <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody, který není obecný <xref:System.Collections.IEnumerable.GetEnumerator%2A> musí také být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="a8382-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="a8382-132">Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="a8382-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="a8382-133">Implementace neobecnou odloží na obecnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="a8382-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="a8382-134">Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory.</span><span class="sxs-lookup"><span data-stu-id="a8382-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="a8382-135">Tyto iterátory s názvem jsou `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.</span><span class="sxs-lookup"><span data-stu-id="a8382-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="a8382-136">`BottomToTop` Vlastnost používá iterátor v `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="a8382-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="a8382-137">Informace o syntaxi</span><span class="sxs-lookup"><span data-stu-id="a8382-137">Syntax Information</span></span>

<span data-ttu-id="a8382-138">Iterátor může dojít, jako metodu nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="a8382-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="a8382-139">V události, konstruktor instance, statický konstruktor nebo statická finalizační metoda nemůže dojít k iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="a8382-140">Musí existovat implicitní převod z typu výrazu v `yield return` příkaz na argument typu pro IEnumerable<T> vrácený iterátor.</span><span class="sxs-lookup"><span data-stu-id="a8382-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the IEnumerable<T> returned by the iterator.</span></span>

<span data-ttu-id="a8382-141">V jazyce C#, nemůže obsahovat metodu iterátoru ani `in`, `ref`, nebo `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="a8382-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="a8382-142">V jazyce C#, "yield" není vyhrazené slovo a má zvláštní význam pouze v případě, že je použitá před `return` nebo `break` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a8382-142">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="a8382-143">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="a8382-143">Technical Implementation</span></span>

<span data-ttu-id="a8382-144">I když píšete iterátoru jako metodu, kompilátor přeloží ho do vnořené třídy, který je, v důsledku toho stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="a8382-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="a8382-145">Tato třída uchovává informace o pozice iterátoru jako dlouho `foreach` pokračuje smyčka v kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="a8382-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="a8382-146">Pokud chcete zobrazit, co dělá kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který je generován pro metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="a8382-147">Při vytváření iterátor pro [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a8382-147">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="a8382-148">Když kompilátor zjistí iterátoru, automaticky generuje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a8382-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="a8382-149">Na každou následnou iterací z `foreach` smyčky (nebo přímého volání `IEnumerator.MoveNext`), další kód tělo iterátoru pokračuje po předchozí `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a8382-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="a8382-150">Bude pokračovat na další `yield return` příkaz, dokud je dosaženo konce tělo iterátoru, nebo dokud `yield break` příkaz dochází.</span><span class="sxs-lookup"><span data-stu-id="a8382-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="a8382-151">Nepodporují iterátory <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a8382-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a8382-152">Zdůrazňujeme od začátku, musíte získat nový iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="a8382-153">Volání <xref:System.Collections.IEnumerator.Reset%2A> na iterátor vrácené z metody iterátoru vyvolá <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="a8382-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="a8382-154">Další informace najdete v tématu [specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8382-154">For additional information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="a8382-155">Používání iterátorů</span><span class="sxs-lookup"><span data-stu-id="a8382-155">Use of Iterators</span></span>

<span data-ttu-id="a8382-156">Iterátory umožňují udržovat jednoduchost `foreach` smyčky, když budete chtít použít k naplnění seznamu pořadí složitého kódu.</span><span class="sxs-lookup"><span data-stu-id="a8382-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="a8382-157">To může být užitečné, pokud chcete provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="a8382-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="a8382-158">Pořadí seznamu změnit po prvním `foreach` iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="a8382-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="a8382-159">Vyhněte se plně načítání velkých seznamu před první iteraci `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="a8382-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="a8382-160">Příkladem je stránkovaného načtení načíst dávku řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="a8382-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="a8382-161">Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodu, která implementuje iterátorů v rámci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8382-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="a8382-162">Zapouzdření vytváření seznamu v iterátoru.</span><span class="sxs-lookup"><span data-stu-id="a8382-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="a8382-163">V metodě iterátoru můžete vytvořit seznam a potom yield každého výsledku ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="a8382-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8382-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8382-164">See Also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="a8382-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="a8382-165">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="a8382-166">yield</span><span class="sxs-lookup"><span data-stu-id="a8382-166">yield</span></span>](../../../csharp/language-reference/keywords/yield.md)
- [<span data-ttu-id="a8382-167">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="a8382-167">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="a8382-168">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="a8382-168">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)