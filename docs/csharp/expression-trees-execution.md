---
title: Provádění stromů výrazů
description: Informace o provádění stromů výrazů jejich převedením na spustitelný soubor pokyny Intermediate Language (IL).
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: fb9ec5f023587b4e5c74ab71acbd6a886e085e4a
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207388"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="3cf48-103">Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="3cf48-103">Executing Expression Trees</span></span>

[<span data-ttu-id="3cf48-104">Předchozí – Typy Framework podpůrné stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="3cf48-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="3cf48-105">*Strom výrazu* je datová struktura, která představuje nějaký kód.</span><span class="sxs-lookup"><span data-stu-id="3cf48-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="3cf48-106">Není kompilované a spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-106">It is not compiled and executable code.</span></span> <span data-ttu-id="3cf48-107">Pokud chcete provést kód .NET, která je reprezentována strom výrazu, je nutné je převést na spustitelný soubor IL pokyny.</span><span class="sxs-lookup"><span data-stu-id="3cf48-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="3cf48-108">Lambda – výrazy to – funkce</span><span class="sxs-lookup"><span data-stu-id="3cf48-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="3cf48-109">Můžete převést všechny LambdaExpression nebo kterýkoli typ odvozený od LambdaExpression do spustitelného souboru IL.</span><span class="sxs-lookup"><span data-stu-id="3cf48-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="3cf48-110">Ostatní typy výrazů nelze převést přímo do kódu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="3cf48-111">Toto omezení se v praxi malý vliv.</span><span class="sxs-lookup"><span data-stu-id="3cf48-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="3cf48-112">Lambda – výrazy jsou pouze typy výrazů, které byste chtěli spusťte tak, že převádění do převodního jazyka spustitelný soubor (IL).</span><span class="sxs-lookup"><span data-stu-id="3cf48-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="3cf48-113">(Vezměte v úvahu, o co znamená přímo provést `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="3cf48-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="3cf48-114">By to znamená nic užitečného?) Všechny strom výrazu, který je `LambdaExpression`, nebo z odvozený typ. `LambdaExpression` lze převést na IL.</span><span class="sxs-lookup"><span data-stu-id="3cf48-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="3cf48-115">Typ výrazu `Expression<TDelegate>` se pouze konkrétní příklad v rozhraní .NET Core libraries.</span><span class="sxs-lookup"><span data-stu-id="3cf48-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="3cf48-116">Slouží k reprezentaci výraz, který se mapuje na jakýkoli typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="3cf48-117">Protože tento typ se mapuje na typ delegáta, rozhraní .NET můžete zkontrolujte výraz a generovat IL pro příslušné delegáta, který odpovídá podpis výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="3cf48-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="3cf48-118">Ve většině případů tím se vytvoří jednoduchý mapování mezi výrazu a jeho odpovídající delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="3cf48-119">Například strom výrazu, která je reprezentována `Expression<Func<int>>` bude převedena na delegáta typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="3cf48-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="3cf48-120">Výraz lambda veškeré návratový typ a seznam argumentů existuje typ delegáta, který je cílový typ pro spustitelný kód reprezentována tohoto výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="3cf48-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="3cf48-121">`LambdaExpression` Typ obsahuje `Compile` a `CompileToMethod` členy, které byste použili převést strom výrazu spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="3cf48-122">`Compile` Metoda vytvoří delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="3cf48-123">`CompileToMethod` Metoda aktualizace `MethodBuilder` objekt s IL představující kompilované výstup strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="3cf48-124">Všimněte si, že `CompileToMethod` je k dispozici v rámci celé ploše, není v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3cf48-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="3cf48-125">Volitelně můžete zadat taky `DebugInfoGenerator` , se zobrazí symbol ladicí informace pro objekt generovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="3cf48-126">To umožňuje převést strom výrazu do objektu delegáta a mít úplné ladicí informace o generovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="3cf48-127">Výraz by převod delegáta pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="3cf48-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="3cf48-128">Všimněte si, že typ delegáta je založen na typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="3cf48-129">Pokud chcete použít objekt delegáta způsobem silného typu, je nutné znát návratový typ a seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="3cf48-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="3cf48-130">`LambdaExpression.Compile()` Metoda vrátí `Delegate` typu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="3cf48-131">Budete mít přetypovat na typ správné delegáta mít žádné nástroje kompilaci zkontrolujte seznam argumentů nebo návratový typ.</span><span class="sxs-lookup"><span data-stu-id="3cf48-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="3cf48-132">Spuštění a životnosti</span><span class="sxs-lookup"><span data-stu-id="3cf48-132">Execution and Lifetimes</span></span>

<span data-ttu-id="3cf48-133">Spouštění kódu vyvoláním delegát vytvoří, když jste volali metodu `LambdaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="3cf48-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="3cf48-134">Můžete to vidět výše kde `add.Compile()` vrátí delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="3cf48-135">Vyvolání delegáta, voláním `func()` spustí kód.</span><span class="sxs-lookup"><span data-stu-id="3cf48-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="3cf48-136">Tento delegát představuje kód na strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="3cf48-137">Můžete zachovat popisovač přidělíte a později ji použít.</span><span class="sxs-lookup"><span data-stu-id="3cf48-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="3cf48-138">Nemusíte kompilovat pokaždé, když chcete spustit kód, který představuje strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="3cf48-139">(Nezapomeňte, že jsou neměnné stromů výrazů a později kompilování stejném stromu pro výraz vytvoří delegáta, který provádí stejný kód.)</span><span class="sxs-lookup"><span data-stu-id="3cf48-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="3cf48-140">I bude upozornění proti pokusu o vytvoření všechny sofistikovanější ukládání do mezipaměti mechanismy pro zvýšení výkonu zabráněním nepotřebné kompilace volání.</span><span class="sxs-lookup"><span data-stu-id="3cf48-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="3cf48-141">Porovnání dvou stromy libovolný výrazů k určení, zda představují stejnou algoritmus bude také časově náročné provést.</span><span class="sxs-lookup"><span data-stu-id="3cf48-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="3cf48-142">Pravděpodobně zjistíte, dobu výpočtů uložit zabraňující jakékoli další volání `LambdaExpression.Compile()` více než využijí na době, provádění kód, který určuje ze dvou různých stromů výrazů mít za následek stejný spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="3cf48-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="3cf48-143">Upozornění</span><span class="sxs-lookup"><span data-stu-id="3cf48-143">Caveats</span></span>

<span data-ttu-id="3cf48-144">Kompilování výrazu lambda s delegátem a vyvolání tento delegát je jedním z nejjednodušší operace, které můžete provádět s strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3cf48-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="3cf48-145">Nicméně i přes tato jednoduchá operace existují upozornění, které musí mít přehled o.</span><span class="sxs-lookup"><span data-stu-id="3cf48-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="3cf48-146">Lambda – výrazy vytvoří uzavření žádné místní proměnné, které jsou odkazované ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="3cf48-147">Musí zaručit, že jsou všechny proměnné, které by byly součástí delegát použitelné tam, kde volání `Compile`, a po spuštění výsledného delegáta.</span><span class="sxs-lookup"><span data-stu-id="3cf48-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="3cf48-148">Obecně platí kompilátor zajistí, že se jedná o hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="3cf48-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="3cf48-149">Ale pokud výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že kódu může dispose objektu, zatímco je stále držené strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cf48-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="3cf48-150">Například tento kód funguje bez problémů, protože `int` neimplementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="3cf48-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="3cf48-151">Delegát má zaznamenat odkaz na proměnnou místní `constant`.</span><span class="sxs-lookup"><span data-stu-id="3cf48-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="3cf48-152">Tuto proměnnou přistupuje kdykoli později, když funkce vrácený `CreateBoundFunc` provede.</span><span class="sxs-lookup"><span data-stu-id="3cf48-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="3cf48-153">Zvažte však tato třída (místo contrived), který implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="3cf48-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="3cf48-154">Pokud můžete použít ve výrazu, jak je uvedeno níže, získáte `ObjectDisposedException` při spuštění kód odkazuje `Resource.Argument` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="3cf48-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="3cf48-155">Tato metoda vrátí delegáta zavřel přes `constant` objekt, který byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="3cf48-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="3cf48-156">(Je byl zrušen, protože byla deklarována v `using` příkaz.)</span><span class="sxs-lookup"><span data-stu-id="3cf48-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="3cf48-157">Teď, když spustíte delegáta, tato metoda vrátí, budete mít `ObjecctDisposedException` vyvolána v okamžiku spuštění.</span><span class="sxs-lookup"><span data-stu-id="3cf48-157">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="3cf48-158">Pravděpodobně tak, aby měl představující kompilaci konstrukce běhová chyba neobvyklé, ale který je na světě, které jsme zadat, když budeme pracovat s stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3cf48-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="3cf48-159">Proto je obtížné nabízejí obecné pokyny k tomu zamezit je celá řada permutací tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="3cf48-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="3cf48-160">Buďte opatrní při definování výrazy přístup k místní proměnné a buďte opatrní o přístup ke stavu v aktuálním objektu (reprezentována `this`) při vytváření strom výrazu, který může být vrácen pouze veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3cf48-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="3cf48-161">Kód do výrazu odkazy na metody nebo vlastnosti v ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="3cf48-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="3cf48-162">Toto sestavení musí být dostupný, když je definována výraz a když je zkompilovat a při vyvolání Výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="3cf48-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="3cf48-163">Budete splnit s `ReferencedAssemblyNotFoundException` v případech, kde není přítomen.</span><span class="sxs-lookup"><span data-stu-id="3cf48-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="3cf48-164">Souhrn</span><span class="sxs-lookup"><span data-stu-id="3cf48-164">Summary</span></span>

<span data-ttu-id="3cf48-165">Stromy výrazů, které představují výrazy lambda mohou být zkompilovány vytvořit delegáta, který můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="3cf48-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="3cf48-166">To představuje jeden mechanismus ke spouštění kódu vytvořeného reprezentována strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3cf48-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="3cf48-167">Strom výrazu představují kód, který by provést pro jakékoli dané konstrukce, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="3cf48-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="3cf48-168">Tak dlouho, dokud prostředí, kde zkompilování a spuštění kód odpovídá prostředí, kde můžete vytvořit výraz, všechno funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="3cf48-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="3cf48-169">Když, nedojde, chyby jsou velmi předvídatelný a jejich bude zachycena v první testy kódu pomocí stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3cf48-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="3cf48-170">Další – Interpretace výrazy</span><span class="sxs-lookup"><span data-stu-id="3cf48-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
