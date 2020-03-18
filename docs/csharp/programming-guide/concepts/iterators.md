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
# <a name="iterators-c"></a><span data-ttu-id="87296-102">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="87296-102">Iterators (C#)</span></span>

<span data-ttu-id="87296-103">*Iterátor* lze krokovat kolekce, jako jsou seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="87296-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="87296-104">Iterator metoda `get` nebo přistupující objekt provádí vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="87296-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="87296-105">Metoda iterátoru používá yield [return](../../language-reference/keywords/yield.md) příkaz vrátit každý prvek jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="87296-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="87296-106">Po `yield return` dosažení příkazu je zapamatováno aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="87296-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="87296-107">Spuštění je restartován z tohoto umístění při příštím volání funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="87296-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="87296-108">Spotřebováváte iterátor z klientského kódu pomocí [foreach](../../language-reference/keywords/foreach-in.md) příkaz nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="87296-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="87296-109">V následujícím příkladu první iterace `foreach` smyčky způsobí, `SomeNumbers` že spuštění pokračovat v `yield return` iterátoru metody, dokud je dosaženo prvního příkazu.</span><span class="sxs-lookup"><span data-stu-id="87296-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="87296-110">Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru je zachováno.</span><span class="sxs-lookup"><span data-stu-id="87296-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="87296-111">Na další iteraci smyčky provádění v iterátoru metoda pokračuje od místa, kde `yield return` přestal, opět zastavení, když dosáhne příkazu.</span><span class="sxs-lookup"><span data-stu-id="87296-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="87296-112">Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru je opět zachováno.</span><span class="sxs-lookup"><span data-stu-id="87296-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="87296-113">Smyčka se dokončí po dosažení konce metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="87296-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="87296-114">Návratový typ metody iterátoru `get` nebo přistupujícího objektu <xref:System.Collections.IEnumerable>může být <xref:System.Collections.Generic.IEnumerable%601>, , <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="87296-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="87296-115">K ukončení `yield break` iterace můžete použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="87296-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="87296-116">Pro všechny příklady v tomto tématu s výjimkou simple iterátor `System.Collections.Generic` příklad, patří [použití](../../language-reference/keywords/using-directive.md) direktivy pro `System.Collections` a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="87296-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="87296-117">Jednoduchý iterátor</span><span class="sxs-lookup"><span data-stu-id="87296-117">Simple Iterator</span></span>

<span data-ttu-id="87296-118">Následující příklad má `yield return` jeden příkaz, který je uvnitř [for](../../language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="87296-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="87296-119">V `Main`aplikaci každá `foreach` iterace těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="87296-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="87296-120">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="87296-120">Creating a Collection Class</span></span>

<span data-ttu-id="87296-121">V následujícím příkladu `DaysOfTheWeek` třída implementuje <xref:System.Collections.IEnumerable> rozhraní, <xref:System.Collections.IEnumerable.GetEnumerator%2A> které vyžaduje metodu.</span><span class="sxs-lookup"><span data-stu-id="87296-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="87296-122">Kompilátor implicitně `GetEnumerator` volá metodu, <xref:System.Collections.IEnumerator>která vrací .</span><span class="sxs-lookup"><span data-stu-id="87296-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="87296-123">Metoda `GetEnumerator` vrátí každý řetězec jeden po `yield return` druhém pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="87296-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="87296-124">Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.</span><span class="sxs-lookup"><span data-stu-id="87296-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="87296-125">Příkaz, `foreach` který odkazuje na instanci třídy (`theZoo`) implicitně volá metodu. `GetEnumerator`</span><span class="sxs-lookup"><span data-stu-id="87296-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="87296-126">`foreach` Příkazy, které `Birds` odkazují `Mammals` na `AnimalsForType` vlastnosti a používají metodu pojmenovaný iterátor.</span><span class="sxs-lookup"><span data-stu-id="87296-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="87296-127">Používání iterátorů v obecných seznamech</span><span class="sxs-lookup"><span data-stu-id="87296-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="87296-128">V následujícím příkladu <xref:System.Collections.Generic.Stack%601> obecná třída <xref:System.Collections.Generic.IEnumerable%601> implementuje obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87296-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="87296-129">Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> přiřazuje hodnoty `T`poli typu .</span><span class="sxs-lookup"><span data-stu-id="87296-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="87296-130">Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> vrátí hodnoty pole pomocí `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="87296-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="87296-131">Kromě obecné <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody musí být implementována i neobecná <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="87296-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="87296-132">Důvodem <xref:System.Collections.Generic.IEnumerable%601> je, <xref:System.Collections.IEnumerable>že dědí z .</span><span class="sxs-lookup"><span data-stu-id="87296-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="87296-133">Neobecná implementace se odkládá na obecnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="87296-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="87296-134">Příklad používá pojmenované iterátory pro podporu různých způsobů iterace prostřednictvím stejné kolekce dat.</span><span class="sxs-lookup"><span data-stu-id="87296-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="87296-135">Tyto pojmenované iterátory `TopToBottom` jsou `BottomToTop` vlastnosti `TopN` a a metoda.</span><span class="sxs-lookup"><span data-stu-id="87296-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="87296-136">Vlastnost `BottomToTop` používá iterátor v `get` přistupujícím objektu.</span><span class="sxs-lookup"><span data-stu-id="87296-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="87296-137">Informace o syntaxi</span><span class="sxs-lookup"><span data-stu-id="87296-137">Syntax Information</span></span>

<span data-ttu-id="87296-138">Iterátor může dojít jako metoda `get` nebo přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="87296-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="87296-139">Iterátor nemůže dojít v události, instance konstruktor, statický konstruktor nebo statický finalizační prostředek.</span><span class="sxs-lookup"><span data-stu-id="87296-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="87296-140">Implicitní převod musí existovat z `yield return` typu výrazu v `IEnumerable<T>` příkazu na argument typu pro vrácený iterátorem.</span><span class="sxs-lookup"><span data-stu-id="87296-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="87296-141">V c#, iterátor metoda nemůže `in` `ref`mít `out` žádné , , nebo parametry.</span><span class="sxs-lookup"><span data-stu-id="87296-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="87296-142">V C# `yield` není vyhrazené slovo a má zvláštní význam pouze `return` `break` v případě, že se používá před nebo klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="87296-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="87296-143">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="87296-143">Technical Implementation</span></span>

<span data-ttu-id="87296-144">I když píšete iterátor jako metodu, kompilátor překládá do vnořené třídy, která je ve skutečnosti stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="87296-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="87296-145">Tato třída udržuje informace o pozici iterátoru `foreach` tak dlouho, dokud bude smyčka v kódu klienta pokračovat.</span><span class="sxs-lookup"><span data-stu-id="87296-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="87296-146">Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm.exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="87296-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="87296-147">Při vytváření iterátoru pro [třídu](../../language-reference/keywords/class.md) nebo [strukturu](../../language-reference/builtin-types/struct.md), není nutné <xref:System.Collections.IEnumerator> implementovat celé rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87296-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="87296-148">Když kompilátor detekuje iterátor, automaticky generuje `Current`, `MoveNext`a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87296-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="87296-149">Na každé následné `foreach` iteraci smyčky (nebo přímé volání `IEnumerator.MoveNext`na ), další iterátor kód tělo pokračuje po předchozí `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="87296-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="87296-150">Potom pokračuje k `yield return` dalšímu příkazu, dokud není dosaženo konce těla `yield break` iterátoru nebo dokud není zjištěn příkaz.</span><span class="sxs-lookup"><span data-stu-id="87296-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="87296-151">Iterátory nepodporují metodu. <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="87296-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="87296-152">Chcete-li zopakovat od začátku, musíte získat nový iterátor.</span><span class="sxs-lookup"><span data-stu-id="87296-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="87296-153">Volání <xref:System.Collections.IEnumerator.Reset%2A> na iterátoru vrácené metodou iterátoru <xref:System.NotSupportedException>vyvolá .</span><span class="sxs-lookup"><span data-stu-id="87296-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="87296-154">Další informace naleznete v jazykové [specifikaci jazyka C#](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="87296-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="87296-155">Používání iterátorů</span><span class="sxs-lookup"><span data-stu-id="87296-155">Use of Iterators</span></span>

<span data-ttu-id="87296-156">Iterátory umožňují zachovat jednoduchost smyčky, `foreach` když potřebujete použít složitý kód k naplnění pořadí seznamu.</span><span class="sxs-lookup"><span data-stu-id="87296-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="87296-157">To může být užitečné, pokud chcete provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="87296-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="87296-158">Po první `foreach` iteraci smyčky upravte pořadí seznamu.</span><span class="sxs-lookup"><span data-stu-id="87296-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="87296-159">Vyhněte se úplnému načtení `foreach` velkého seznamu před první iterací smyčky.</span><span class="sxs-lookup"><span data-stu-id="87296-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="87296-160">Příkladem je stránkované načtení pro načtení dávky řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="87296-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="87296-161">Dalším příkladem <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> je metoda, která implementuje iterátory v rámci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87296-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="87296-162">Zapouzdření vytváření seznamu v iterátoru.</span><span class="sxs-lookup"><span data-stu-id="87296-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="87296-163">V metodě iterátoru můžete sestavit seznam a potom výtěžnost každý výsledek ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="87296-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="87296-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="87296-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="87296-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="87296-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="87296-166">yield</span><span class="sxs-lookup"><span data-stu-id="87296-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="87296-167">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="87296-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="87296-168">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="87296-168">Generics</span></span>](../generics/index.md)
