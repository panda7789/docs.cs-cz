---
title: Iterovat přes kolekce vC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626267"
---
# <a name="iterators-c"></a><span data-ttu-id="2eb95-102">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="2eb95-102">Iterators (C#)</span></span>

<span data-ttu-id="2eb95-103">*Iterátor* se dá použít ke krokování kolekcí, jako jsou seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="2eb95-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="2eb95-104">Metoda iterátoru nebo přistupující objekt `get` provádí vlastní iteraci v kolekci.</span><span class="sxs-lookup"><span data-stu-id="2eb95-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="2eb95-105">Metoda iterátoru používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého prvku v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="2eb95-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="2eb95-106">Když je dosaženo příkazu `yield return`, aktuální umístění v kódu je zapamatovatelné.</span><span class="sxs-lookup"><span data-stu-id="2eb95-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="2eb95-107">Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="2eb95-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="2eb95-108">Můžete využít iterátor z klientského kódu pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="2eb95-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="2eb95-109">V následujícím příkladu první iterace smyčky `foreach` způsobí, že spuštění pokračuje v metodě `SomeNumbers` iterátoru, dokud se nedosáhne prvního příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="2eb95-110">Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru se zachová.</span><span class="sxs-lookup"><span data-stu-id="2eb95-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="2eb95-111">Při další iteraci smyčky pokračuje spuštění v metodě iterátoru tam, kde skončila, a znovu se zastaví, jakmile dosáhne `yield return`ho příkazu.</span><span class="sxs-lookup"><span data-stu-id="2eb95-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="2eb95-112">Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru se znovu zachová.</span><span class="sxs-lookup"><span data-stu-id="2eb95-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="2eb95-113">Smyčka skončí po dosažení konce metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="2eb95-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="2eb95-114">Návratový typ metody iterátoru nebo přístupového objektu `get` může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="2eb95-115">K ukončení iterace můžete použít příkaz `yield break`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="2eb95-116">Pro všechny příklady v tomto tématu, s výjimkou příkladu jednoduchého iterátoru, zahrňte direktivy [using](../../language-reference/keywords/using-directive.md) pro obory názvů `System.Collections` a `System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="2eb95-117">Jednoduchý iterátor</span><span class="sxs-lookup"><span data-stu-id="2eb95-117">Simple Iterator</span></span>

<span data-ttu-id="2eb95-118">V následujícím příkladu je jeden příkaz `yield return`, který je uvnitř smyčky [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="2eb95-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="2eb95-119">V `Main`Každá iterace těla příkazu `foreach` vytvoří volání funkce iterátoru, které pokračuje k dalšímu příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="2eb95-120">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="2eb95-120">Creating a Collection Class</span></span>

<span data-ttu-id="2eb95-121">V následujícím příkladu třída `DaysOfTheWeek` implementuje rozhraní <xref:System.Collections.IEnumerable>, které vyžaduje metodu <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="2eb95-122">Kompilátor implicitně volá metodu `GetEnumerator`, která vrací <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="2eb95-123">Metoda `GetEnumerator` vrátí každý řetězec v jednom okamžiku pomocí příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="2eb95-124">Následující příklad vytvoří třídu `Zoo`, která obsahuje kolekci zvířat.</span><span class="sxs-lookup"><span data-stu-id="2eb95-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="2eb95-125">Příkaz `foreach`, který odkazuje na instanci třídy (`theZoo`), implicitně volá metodu `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="2eb95-126">Příkazy `foreach`, které odkazují na vlastnosti `Birds` a `Mammals`, používají `AnimalsForType` s názvem iterátor.</span><span class="sxs-lookup"><span data-stu-id="2eb95-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="2eb95-127">Používání iterátorů v obecných seznamech</span><span class="sxs-lookup"><span data-stu-id="2eb95-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="2eb95-128">V následujícím příkladu <xref:System.Collections.Generic.Stack%601> obecná třída implementuje obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="2eb95-129">Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> přiřadí hodnoty k poli typu `T`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="2eb95-130">Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> vrací hodnoty pole pomocí příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="2eb95-131">Kromě obecných <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda musí být také implementována neobecná <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2eb95-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="2eb95-132">Důvodem je to, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="2eb95-133">Neobecná implementace se odloží k obecné implementaci.</span><span class="sxs-lookup"><span data-stu-id="2eb95-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="2eb95-134">Tento příklad používá pojmenované iterátory k podpoře různých způsobů iterace v rámci stejné kolekce dat.</span><span class="sxs-lookup"><span data-stu-id="2eb95-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="2eb95-135">Tyto pojmenované iterátory jsou vlastnosti `TopToBottom` a `BottomToTop` a metoda `TopN`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="2eb95-136">Vlastnost `BottomToTop` používá iterátor v přístupovém objektu `get`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="2eb95-137">Informace o syntaxi</span><span class="sxs-lookup"><span data-stu-id="2eb95-137">Syntax Information</span></span>

<span data-ttu-id="2eb95-138">Iterátor se může vyskytnout jako metoda nebo přistupující objekt `get`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="2eb95-139">Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statické finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="2eb95-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="2eb95-140">Implicitní převod musí existovat v typu výrazu v příkazu `yield return` do argumentu typu pro `IEnumerable<T>` vracené iterátorem.</span><span class="sxs-lookup"><span data-stu-id="2eb95-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="2eb95-141">V C#nástroji iterátor nemůže mít žádné parametry `in`, `ref`nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="2eb95-142">V C#`yield` není rezervované slovo a má zvláštní význam pouze v případě, že je použit před klíčovým slovem `return` nebo `break`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="2eb95-143">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="2eb95-143">Technical Implementation</span></span>

<span data-ttu-id="2eb95-144">I když zapisujete iterátor jako metodu, kompilátor je převede na vnořenou třídu, která je v podstatě Stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="2eb95-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="2eb95-145">Tato třída uchovává informace o poloze iterátoru, pokud bude `foreach` smyčka v kódu klienta pokračovat.</span><span class="sxs-lookup"><span data-stu-id="2eb95-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="2eb95-146">Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm. exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="2eb95-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="2eb95-147">Při vytváření iterátoru pro [třídu](../../language-reference/keywords/class.md) nebo [strukturu](../../language-reference/builtin-types/struct.md)není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2eb95-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="2eb95-148">Když kompilátor detekuje iterátor, automaticky generuje `Current`, `MoveNext`a `Dispose` metody rozhraní <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="2eb95-149">U každého následného opakování smyčky `foreach` (nebo přímého volání `IEnumerator.MoveNext`) pokračuje další tělo kódu iterátoru po předchozím příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="2eb95-150">Pak pokračuje dalším příkazem `yield return` až do chvíle, kdy se dosáhne konce textu iterátoru, nebo dokud se nezjistí příkaz `yield break`.</span><span class="sxs-lookup"><span data-stu-id="2eb95-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="2eb95-151">Iterátory nepodporují metodu <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2eb95-152">K opakování iterace od začátku musíte získat nový iterátor.</span><span class="sxs-lookup"><span data-stu-id="2eb95-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="2eb95-153">Volání <xref:System.Collections.IEnumerator.Reset%2A> na iterátoru vrácené metodou iterátoru vyvolá <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="2eb95-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="2eb95-154">Další informace najdete v [ C# tématu Specifikace jazyka](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="2eb95-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="2eb95-155">Používání iterátorů</span><span class="sxs-lookup"><span data-stu-id="2eb95-155">Use of Iterators</span></span>

<span data-ttu-id="2eb95-156">Iterátory umožňují udržovat jednoduchost smyčky `foreach`, když potřebujete použít složitý kód k naplnění pořadí seznamu.</span><span class="sxs-lookup"><span data-stu-id="2eb95-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="2eb95-157">To může být užitečné v případě, že chcete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="2eb95-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="2eb95-158">Upravte pořadí seznamu po první iteraci `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="2eb95-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="2eb95-159">Vyhněte se úplnému načítání velkého seznamu před první iterací `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="2eb95-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="2eb95-160">Příkladem stránkovaného načtení je načtení dávky řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="2eb95-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="2eb95-161">Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rámci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2eb95-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="2eb95-162">Zapouzdřit sestavení seznamu v iterátoru.</span><span class="sxs-lookup"><span data-stu-id="2eb95-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="2eb95-163">V metodě iterátoru můžete sestavit seznam a pak každý výsledek vracet ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="2eb95-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="2eb95-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="2eb95-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="2eb95-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="2eb95-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="2eb95-166">yield</span><span class="sxs-lookup"><span data-stu-id="2eb95-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="2eb95-167">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="2eb95-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="2eb95-168">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="2eb95-168">Generics</span></span>](../generics/index.md)
