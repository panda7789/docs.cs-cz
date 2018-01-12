---
title: "Provádění stromů výrazů"
description: "Informace o provádění stromů výrazů jejich převedením na spustitelný soubor pokyny Intermediate Language (IL)."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: db481c18a79f55b079ec2558b884ce288e2a9933
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="executing-expression-trees"></a><span data-ttu-id="3fff5-104">Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="3fff5-104">Executing Expression Trees</span></span>

[<span data-ttu-id="3fff5-105">Předchozí – Typy Framework podpůrné stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="3fff5-105">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="3fff5-106">*Strom výrazu* je datová struktura, která představuje nějaký kód.</span><span class="sxs-lookup"><span data-stu-id="3fff5-106">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="3fff5-107">Není kompilované a spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-107">It is not compiled and executable code.</span></span> <span data-ttu-id="3fff5-108">Pokud chcete provést kód .NET, která je reprezentována strom výrazu, je nutné je převést na spustitelný soubor IL pokyny.</span><span class="sxs-lookup"><span data-stu-id="3fff5-108">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="3fff5-109">Lambda – výrazy to – funkce</span><span class="sxs-lookup"><span data-stu-id="3fff5-109">Lambda Expressions to Functions</span></span>
<span data-ttu-id="3fff5-110">Můžete převést všechny LambdaExpression nebo kterýkoli typ odvozený od LambdaExpression do spustitelného souboru IL.</span><span class="sxs-lookup"><span data-stu-id="3fff5-110">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="3fff5-111">Ostatní typy výrazů nelze převést přímo do kódu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-111">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="3fff5-112">Toto omezení se v praxi malý vliv.</span><span class="sxs-lookup"><span data-stu-id="3fff5-112">This restriction has little effect in practice.</span></span> <span data-ttu-id="3fff5-113">Lambda – výrazy jsou pouze typy výrazů, které byste chtěli spusťte tak, že převádění do převodního jazyka spustitelný soubor (IL).</span><span class="sxs-lookup"><span data-stu-id="3fff5-113">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="3fff5-114">(Vezměte v úvahu, o co znamená přímo provést `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="3fff5-114">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="3fff5-115">By to znamená nic užitečného?) Všechny strom výrazu, který je `LamdbaExpression`, nebo z odvozený typ. `LambdaExpression` lze převést na IL.</span><span class="sxs-lookup"><span data-stu-id="3fff5-115">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="3fff5-116">Typ výrazu `Expression<TDelegate>` se pouze konkrétní příklad v rozhraní .NET Core libraries.</span><span class="sxs-lookup"><span data-stu-id="3fff5-116">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="3fff5-117">Slouží k reprezentaci výraz, který se mapuje na jakýkoli typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-117">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="3fff5-118">Protože tento typ se mapuje na typ delegáta, rozhraní .NET můžete zkontrolujte výraz a generovat IL pro příslušné delegáta, který odpovídá podpis výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="3fff5-118">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="3fff5-119">Ve většině případů tím se vytvoří jednoduchý mapování mezi výrazu a jeho odpovídající delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-119">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="3fff5-120">Například strom výrazu, která je reprezentována `Expression<Func<int>>` bude převedena na delegáta typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="3fff5-120">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="3fff5-121">Výraz lambda veškeré návratový typ a seznam argumentů existuje typ delegáta, který je typ cíle pro spustitelný kód reprezentována této lamdba výrazem.</span><span class="sxs-lookup"><span data-stu-id="3fff5-121">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="3fff5-122">`LamdbaExpression` Typ obsahuje `Compile` a `CompileToMethod` členy, které byste použili převést strom výrazu spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-122">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="3fff5-123">`Compile` Metoda vytvoří delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-123">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="3fff5-124">`CompileToMethod` Metoda aktualizace `MethodBuilder` objekt s IL představující kompilované výstup strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-124">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="3fff5-125">Všimněte si, že `CompileToMethod` dostupný jen na úplné desktopového rozhraní, nikoli na rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fff5-125">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="3fff5-126">Volitelně můžete zadat taky `DebugInfoGenerator` , se zobrazí symbol ladicí informace pro objekt generovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-126">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="3fff5-127">To umožňuje převést strom výrazu do objektu delegáta a mít úplné ladicí informace o generovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-127">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="3fff5-128">Výraz by převod delegáta pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="3fff5-128">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="3fff5-129">Všimněte si, že typ delegáta je založen na typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-129">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="3fff5-130">Pokud chcete použít objekt delegáta způsobem silného typu, je nutné znát návratový typ a seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="3fff5-130">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="3fff5-131">`LambdaExpression.Compile()` Metoda vrátí `Delegate` typu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-131">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="3fff5-132">Budete muset převést na typ správné delegáta, který má mít žádné nástroje kompilaci zkontrolujte seznam argumentů návratový typ.</span><span class="sxs-lookup"><span data-stu-id="3fff5-132">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="3fff5-133">Spuštění a životnosti</span><span class="sxs-lookup"><span data-stu-id="3fff5-133">Execution and Lifetimes</span></span>

<span data-ttu-id="3fff5-134">Spouštění kódu vyvoláním delegát vytvoří, když jste volali metodu `LamdbaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="3fff5-134">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="3fff5-135">Můžete to vidět výše kde `add.Compile()` vrátí delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-135">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="3fff5-136">Vyvolání delegáta, voláním `func()` spustí kód.</span><span class="sxs-lookup"><span data-stu-id="3fff5-136">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="3fff5-137">Tento delegát představuje kód na strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-137">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="3fff5-138">Můžete zachovat popisovač přidělíte a později ji použít.</span><span class="sxs-lookup"><span data-stu-id="3fff5-138">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="3fff5-139">Nemusíte kompilovat pokaždé, když chcete spustit kód, který představuje strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-139">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="3fff5-140">(Nezapomeňte, že jsou neměnné stromů výrazů a později kompilování stejném stromu pro výraz vytvoří delegáta, který provádí stejný kód.)</span><span class="sxs-lookup"><span data-stu-id="3fff5-140">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="3fff5-141">I bude upozornění proti pokusu o vytvoření všechny sofistikovanější ukládání do mezipaměti mechanismy pro zvýšení výkonu zabráněním nepotřebné kompilace volání.</span><span class="sxs-lookup"><span data-stu-id="3fff5-141">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="3fff5-142">Porovnání dvou stromy libovolný výrazů k určení, zda představují stejnou algoritmus bude také časově náročné provést.</span><span class="sxs-lookup"><span data-stu-id="3fff5-142">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="3fff5-143">Pravděpodobně zjistíte, dobu výpočtů uložit zabraňující jakékoli další volání `LambdaExpression.Compile()` více než využijí na době, provádění kód, který určuje ze dvou různých stromů výrazů mít za následek stejný spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="3fff5-143">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="3fff5-144">Upozornění</span><span class="sxs-lookup"><span data-stu-id="3fff5-144">Caveats</span></span>

<span data-ttu-id="3fff5-145">Kompilování výrazu lambda s delegátem a vyvolání tento delegát je jedním z nejjednodušší operace, které můžete provádět s strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3fff5-145">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="3fff5-146">Nicméně i přes tato jednoduchá operace existují upozornění, které musí mít přehled o.</span><span class="sxs-lookup"><span data-stu-id="3fff5-146">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="3fff5-147">Lambda – výrazy vytvoří uzavření žádné místní proměnné, které jsou odkazované ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-147">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="3fff5-148">Musí zaručit, že jsou všechny proměnné, které by byly součástí delegát použitelné tam, kde volání `Compile`, a po spuštění výsledného delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fff5-148">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="3fff5-149">Obecně platí kompilátor zajistí, že se jedná o hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="3fff5-149">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="3fff5-150">Ale pokud výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že kódu může dispose objektu, zatímco je stále držené strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3fff5-150">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="3fff5-151">Například tento kód funguje bez problémů, protože `int` neimplementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="3fff5-151">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="3fff5-152">Delegát má zaznamenat odkaz na proměnnou místní `constant`.</span><span class="sxs-lookup"><span data-stu-id="3fff5-152">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="3fff5-153">Tuto proměnnou přistupuje kdykoli později, když funkce vrácený `CreateBoundFunc` provede.</span><span class="sxs-lookup"><span data-stu-id="3fff5-153">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="3fff5-154">Zvažte však tato třída (místo contrived), který implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="3fff5-154">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="3fff5-155">Pokud můžete použít ve výrazu, jak je uvedeno níže, získáte `ObjectDisposedException` při spuštění kód odkazuje `Resource.Argument` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="3fff5-155">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="3fff5-156">Tato metoda vrátí delegáta zavřel přes `constant` objekt, který byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="3fff5-156">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="3fff5-157">(Je byl zrušen, protože byla deklarována v `using` příkaz.)</span><span class="sxs-lookup"><span data-stu-id="3fff5-157">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="3fff5-158">Teď, když spustíte delegáta, tato metoda vrátí, budete mít `ObjecctDisposedException` vyvolána v okamžiku spuštění.</span><span class="sxs-lookup"><span data-stu-id="3fff5-158">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="3fff5-159">Pravděpodobně tak, aby měl představující kompilaci konstrukce běhová chyba neobvyklé, ale který je na světě, které jsme zadat, když budeme pracovat s stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3fff5-159">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="3fff5-160">Proto je obtížné nabízejí obecné pokyny k tomu zamezit je celá řada permutací tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="3fff5-160">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="3fff5-161">Buďte opatrní při definování výrazy přístup k místní proměnné a buďte opatrní o přístup ke stavu v aktuálním objektu (reprezentována `this`) při vytváření strom výrazu, který může být vrácen pouze veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3fff5-161">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="3fff5-162">Kód do výrazu odkazy na metody nebo vlastnosti v ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="3fff5-162">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="3fff5-163">Toto sestavení musí být dostupný, když je definována výraz a když je zkompilovat a při vyvolání Výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="3fff5-163">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="3fff5-164">Budete splnit s `ReferencedAssemblyNotFoundException` v případech, kde není přítomen.</span><span class="sxs-lookup"><span data-stu-id="3fff5-164">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="3fff5-165">Souhrn</span><span class="sxs-lookup"><span data-stu-id="3fff5-165">Summary</span></span>

<span data-ttu-id="3fff5-166">Stromy výrazů, které představují výrazy lambda mohou být zkompilovány vytvořit delegáta, který můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="3fff5-166">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="3fff5-167">To představuje jeden mechanismus ke spouštění kódu vytvořeného reprezentována strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3fff5-167">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="3fff5-168">Strom výrazu představují kód, který by provést pro jakékoli dané konstrukce, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="3fff5-168">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="3fff5-169">Tak dlouho, dokud prostředí, kde zkompilování a spuštění kód odpovídá prostředí, kde můžete vytvořit výraz, všechno funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="3fff5-169">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="3fff5-170">Když, nedojde, chyby jsou velmi předvídatelný a jejich bude zachycena v první testy kódu pomocí stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3fff5-170">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="3fff5-171">Další – Interpretace výrazy</span><span class="sxs-lookup"><span data-stu-id="3fff5-171">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
