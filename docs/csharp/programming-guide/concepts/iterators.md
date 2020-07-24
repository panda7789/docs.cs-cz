---
title: 'Iterovat přes kolekce v jazyce C #'
description: Naučte se používat iterátor ke krokování mezi kolekcemi, jako jsou seznamy a pole. Iterátory jsou spotřebovány z klientského kódu pomocí příkazu foreach nebo dotazu LINQ.
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 310fff68a242812620357517c212ddd5f053775c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104255"
---
# <a name="iterators-c"></a><span data-ttu-id="7a1fd-104">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="7a1fd-104">Iterators (C#)</span></span>

<span data-ttu-id="7a1fd-105">*Iterátor* se dá použít ke krokování kolekcí, jako jsou seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-105">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="7a1fd-106">Metoda iterátoru nebo `get` přistupující objekt provádí vlastní iteraci v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-106">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="7a1fd-107">Metoda iterátoru používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého prvku v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-107">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="7a1fd-108">Při `yield return` dosažení příkazu je aktuální umístění v kódu zapamatovatelné.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-108">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="7a1fd-109">Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-109">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="7a1fd-110">Můžete využít iterátor z klientského kódu pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-110">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="7a1fd-111">V následujícím příkladu první iterace smyčky způsobí, že `foreach` provádění pokračuje v `SomeNumbers` metodě iterátoru, dokud `yield return` není dosaženo prvního příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-111">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="7a1fd-112">Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru se zachová.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-112">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="7a1fd-113">Při další iteraci smyčky pokračuje spuštění v metodě iterátoru z místa, kde skončilo, a opětovné zastavení při dosažení `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-113">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="7a1fd-114">Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru se znovu zachová.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-114">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="7a1fd-115">Smyčka skončí po dosažení konce metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-115">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="7a1fd-116">Návratový typ metody iterátoru nebo `get` přístupového objektu může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-116">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="7a1fd-117">`yield break`K ukončení iterace můžete použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-117">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="7a1fd-118">Pro všechny příklady v tomto tématu s výjimkou příkladu jednoduchého iterátoru přidejte direktivy [using](../../language-reference/keywords/using-directive.md) pro `System.Collections` `System.Collections.Generic` obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-118">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="7a1fd-119">Jednoduchý iterátor</span><span class="sxs-lookup"><span data-stu-id="7a1fd-119">Simple Iterator</span></span>

<span data-ttu-id="7a1fd-120">Následující příklad obsahuje jediný `yield return` příkaz, který je uvnitř smyčky [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-120">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="7a1fd-121">V `Main` , Každá iterace `foreach` těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-121">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="7a1fd-122">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="7a1fd-122">Creating a Collection Class</span></span>

<span data-ttu-id="7a1fd-123">V následujícím příkladu `DaysOfTheWeek` Třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-123">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="7a1fd-124">Kompilátor implicitně volá `GetEnumerator` metodu, která vrací <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-124">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="7a1fd-125">`GetEnumerator`Metoda vrátí každý řetězec po jednom v čase pomocí `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-125">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="7a1fd-126">Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-126">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="7a1fd-127">`foreach`Příkaz, který odkazuje na instanci třídy ( `theZoo` ) implicitně volá `GetEnumerator` metodu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-127">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="7a1fd-128">`foreach`Příkazy, které odkazují na `Birds` vlastnosti a `Mammals` používají `AnimalsForType` metodu s názvem iterátor.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-128">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="7a1fd-129">Používání iterátorů v obecných seznamech</span><span class="sxs-lookup"><span data-stu-id="7a1fd-129">Using Iterators with a Generic List</span></span>

<span data-ttu-id="7a1fd-130">V následujícím příkladu <xref:System.Collections.Generic.Stack%601> Obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> Obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-130">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="7a1fd-131"><xref:System.Collections.Generic.Stack%601.Push%2A>Metoda přiřadí hodnoty k poli typu `T` .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-131">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="7a1fd-132"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Metoda vrací hodnoty pole pomocí `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-132">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="7a1fd-133">Kromě obecné <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody <xref:System.Collections.IEnumerable.GetEnumerator%2A> musí být také implementována neobecná metoda.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-133">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="7a1fd-134">Důvodem je <xref:System.Collections.Generic.IEnumerable%601> , že dědí z <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-134">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="7a1fd-135">Neobecná implementace se odloží k obecné implementaci.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-135">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="7a1fd-136">Tento příklad používá pojmenované iterátory k podpoře různých způsobů iterace v rámci stejné kolekce dat.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-136">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="7a1fd-137">Tyto pojmenované iterátory jsou `TopToBottom` vlastnosti a `BottomToTop` a `TopN` metoda.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-137">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="7a1fd-138">`BottomToTop`Vlastnost používá iterátor v `get` přístupovém objektu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-138">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="7a1fd-139">Informace o syntaxi</span><span class="sxs-lookup"><span data-stu-id="7a1fd-139">Syntax Information</span></span>

<span data-ttu-id="7a1fd-140">Iterátor se může vyskytnout jako metoda nebo `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-140">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="7a1fd-141">Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statické finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-141">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="7a1fd-142">Implicitní převod musí existovat v typu výrazu v `yield return` příkazu na argument typu pro `IEnumerable<T>` vrácenou iterátorem.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-142">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="7a1fd-143">V jazyce C# nemůže metoda iterátoru mít žádné `in` `ref` parametry, nebo `out` .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-143">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="7a1fd-144">V jazyce C# není `yield` rezervované slovo a má zvláštní význam pouze v případě, že je použit před `return` `break` klíčovým slovem or.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-144">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="7a1fd-145">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="7a1fd-145">Technical Implementation</span></span>

<span data-ttu-id="7a1fd-146">I když zapisujete iterátor jako metodu, kompilátor je převede na vnořenou třídu, která je v podstatě Stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-146">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="7a1fd-147">Tato třída uchovává informace o poloze iterátoru, dokud `foreach` smyčka v kódu klienta pokračuje.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-147">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="7a1fd-148">Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm.exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-148">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="7a1fd-149">Při vytváření iterátoru pro [třídu](../../language-reference/keywords/class.md) nebo [strukturu](../../language-reference/builtin-types/struct.md)není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-149">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="7a1fd-150">Když kompilátor detekuje iterátor, automaticky generuje `Current` `MoveNext` metody, a `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-150">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="7a1fd-151">U každé následné iterace `foreach` smyčky (nebo přímého volání `IEnumerator.MoveNext` ) pokračuje další tělo kódu iterátoru za předchozím `yield return` příkazem.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-151">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="7a1fd-152">Pak pokračuje k dalšímu `yield return` příkazu až do konce textu iterátoru nebo do doby, než `yield break` se dorazí na příkaz.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-152">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="7a1fd-153">Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-153">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a1fd-154">K opakování iterace od začátku musíte získat nový iterátor.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-154">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="7a1fd-155">Volání <xref:System.Collections.IEnumerator.Reset%2A> iterátoru vráceného metodou iterátoru vyvolá <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="7a1fd-155">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="7a1fd-156">Další informace najdete v tématu [specifikace jazyka C#](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="7a1fd-156">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="7a1fd-157">Používání iterátorů</span><span class="sxs-lookup"><span data-stu-id="7a1fd-157">Use of Iterators</span></span>

<span data-ttu-id="7a1fd-158">Iterátory umožňují udržovat jednoduchost `foreach` smyčky, pokud potřebujete použít složitý kód k naplnění pořadí seznamu.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-158">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="7a1fd-159">To může být užitečné v případě, že chcete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="7a1fd-159">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="7a1fd-160">Změňte pořadí seznamu po `foreach` iteraci první smyčky.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-160">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="7a1fd-161">Vyhněte se úplnému načítání velkého seznamu před první iterací `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-161">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="7a1fd-162">Příkladem stránkovaného načtení je načtení dávky řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-162">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="7a1fd-163">Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-163">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators in .NET.</span></span>

- <span data-ttu-id="7a1fd-164">Zapouzdřit sestavení seznamu v iterátoru.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-164">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="7a1fd-165">V metodě iterátoru můžete sestavit seznam a pak každý výsledek vracet ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="7a1fd-165">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a1fd-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a1fd-166">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="7a1fd-167">foreach, in</span><span class="sxs-lookup"><span data-stu-id="7a1fd-167">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="7a1fd-168">yield</span><span class="sxs-lookup"><span data-stu-id="7a1fd-168">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="7a1fd-169">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="7a1fd-169">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="7a1fd-170">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="7a1fd-170">Generics</span></span>](../generics/index.md)
