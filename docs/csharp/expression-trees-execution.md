---
title: Provádění stromů výrazů
description: Další informace o provádění stromů výrazů jejich převedením na spustitelný soubor pokynů Intermediate Language (IL).
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: f6dca5a3965924e8eb6e1c04fe7ffc3c78c7df93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664555"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="4e4e4-103">Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="4e4e4-103">Executing Expression Trees</span></span>

[<span data-ttu-id="4e4e4-104">Předchozí – Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="4e4e4-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="4e4e4-105">*Stromu výrazů* je datová struktura, která představuje nějaký kód.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="4e4e4-106">Není zkompilovaných a spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-106">It is not compiled and executable code.</span></span> <span data-ttu-id="4e4e4-107">Pokud chcete spustit kód v .NET, která je reprezentována strom výrazů, je nutné ji převést do spustitelného souboru instrukcí IL.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="4e4e4-108">Výrazy lambda na funkce</span><span class="sxs-lookup"><span data-stu-id="4e4e4-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="4e4e4-109">Můžete převést všechny LambdaExpression nebo libovolného typu odvozeného z LambdaExpression do spustitelného souboru IL.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="4e4e4-110">Jiné typy výrazů nelze převést přímo do kódu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="4e4e4-111">Toto omezení má malý vliv v praxi.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="4e4e4-112">Výrazy lambda jsou pouze typy výrazů, které byste měli provést převedením na spustitelný soubor (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="4e4e4-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="4e4e4-113">(Představit, co to znamenalo přímé spuštění `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="4e4e4-114">By to znamenat nic užitečného?) Žádné strom výrazu, který je `LambdaExpression`, nebo typ odvozený od `LambdaExpression` lze převést na IL.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="4e4e4-115">Typ výrazu `Expression<TDelegate>` je pouze konkrétní příklad v .NET Core knihovny.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="4e4e4-116">Používá se k reprezentaci výrazu, který se mapuje na typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="4e4e4-117">Protože tento typ se mapuje na typ delegáta, .NET můžete prozkoumat výraz a generovat IL pro příslušné delegát, který odpovídá signatuře výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="4e4e4-118">Ve většině případů tím se vytvoří jednoduchý mapování mezi výrazem a jeho odpovídající delegáta.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="4e4e4-119">Například strom výrazu, která je reprezentována `Expression<Func<int>>` bude převeden na delegáta typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="4e4e4-120">Pro výraz lambda s jakékoli návratový typ a seznam argumentů existuje typ delegáta, který je cílový typ pro spustitelný kód reprezentována tento výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="4e4e4-121">`LambdaExpression` Typ obsahuje `Compile` a `CompileToMethod` členy, které můžete použít k převedení strom výrazu na spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="4e4e4-122">`Compile` Metoda vytvoří delegát.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="4e4e4-123">`CompileToMethod` Metodu aktualizace `MethodBuilder` objekt s IL, který představuje kompilovaném výstupu stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="4e4e4-124">Všimněte si, že `CompileToMethod` dostupná jenom v rámci plně, ne na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="4e4e4-125">Volitelně můžete zadat taky `DebugInfoGenerator` , který se zobrazí symbol ladicí informace pro objekt generované delegáta.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="4e4e4-126">To umožňuje převést na strom výrazu objektu delegáta a mít úplné ladicí informace o vygenerovaný delegáta.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="4e4e4-127">Výraz by převést na delegáta, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4e4e4-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="4e4e4-128">Všimněte si, že typ delegáta je založen na typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="4e4e4-129">Pokud chcete používat objekt delegáta silného typu způsobem, musíte znát návratový typ a seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="4e4e4-130">`LambdaExpression.Compile()` Vrátí metoda `Delegate` typu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="4e4e4-131">Je nutné přetypovat na typ správného delegáta mít žádné nástroje kompilace zkontrolujte seznam argumentů nebo návratového typu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="4e4e4-132">Spuštění a životnosti</span><span class="sxs-lookup"><span data-stu-id="4e4e4-132">Execution and Lifetimes</span></span>

<span data-ttu-id="4e4e4-133">Při spuštění kódu tak, že vyvolá delegáta vytvoří, když jste volali `LambdaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="4e4e4-134">Tohle je vidět výše where `add.Compile()` vrátí delegáta.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="4e4e4-135">Vyvolání tohoto delegáta voláním `func()` spustí kód.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="4e4e4-136">Tento delegát představuje kód ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="4e4e4-137">Můžete zachovat popisovač delegátu a později ho vyvolat.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="4e4e4-138">Není nutné ke kompilaci pokaždé, když chcete spustit kód, který představuje strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="4e4e4-139">(Mějte na paměti, že stromů výrazů jsou neměnné a později kompilaci stejném stromu pro výraz vytvoří delegát, který spouští stejný kód.)</span><span class="sxs-lookup"><span data-stu-id="4e4e4-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="4e4e4-140">Můžu se průkaz pokusu o vytvoření jakékoli sofistikovanější ukládání do mezipaměti mechanismy pro zvýšení výkonu zabráněním volání zbytečných kompilace.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="4e4e4-141">Porovnání dvou stromů výrazů libovolného k určení, zda představují stejný algoritmus bude taky časově náročné ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="4e4e4-142">Pravděpodobně zjistíte, že výpočetní čas uložíte vyhnout jakékoli další volání `LambdaExpression.Compile()` bude používat více než v době provádění kódu, který určuje dvě různé stromů výrazů za následek stejný spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="4e4e4-143">Upozornění</span><span class="sxs-lookup"><span data-stu-id="4e4e4-143">Caveats</span></span>

<span data-ttu-id="4e4e4-144">Probíhá kompilace výrazu lambda delegátovi a vyvolání tohoto delegáta je jedním z nejjednodušší operace, které můžete provádět pomocí strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="4e4e4-145">Ale i v této jednoduché operaci existují upozornění, které musí mít přehled o.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="4e4e4-146">Výrazy lambda vytvoření uzávěry přes místní proměnné, které se odkazuje ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="4e4e4-147">Je nutné zaručit, že jsou všechny proměnné, které by byly součástí delegáta použitelné na místě, kde volání `Compile`, a při spuštění Výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="4e4e4-148">Kompilátor bude obecně platí, ujistěte se, že je hodnota true.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="4e4e4-149">Nicméně pokud výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že váš kód může uvolnění objektu, zatímco se stále nachází ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="4e4e4-150">Například tento kód funguje, protože `int` neimplementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="4e4e4-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="4e4e4-151">Delegát má zachytit odkazem na místní proměnnou `constant`.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="4e4e4-152">Tuto proměnnou přistupuje kdykoli později, pokud funkce vrátí `CreateBoundFunc` spustí.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="4e4e4-153">Zvažte však, zda tato (místo toho contrived) třída, která implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="4e4e4-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="4e4e4-154">Pokud používáte ho ve výrazu, jak je znázorněno níže, získáte `ObjectDisposedException` při spuštění kód odkazuje `Resource.Argument` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="4e4e4-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="4e4e4-155">Delegát, tato metoda vrátí byl uzavřen za `constant` objektu, který byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="4e4e4-156">(Je byla vyřazena, protože byl deklarován v `using` příkazu.)</span><span class="sxs-lookup"><span data-stu-id="4e4e4-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="4e4e4-157">Teď, když provedete delegáta, tato metoda vrátí, máte k dispozici `ObjectDisposedException` vyvolána v době vykonání.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="4e4e4-158">Zdát neobvyklé obsahuje chybu modulu runtime představující konstrukci za kompilace, ale to je svět, ve kterém jsme zadejte při spolupracujeme s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="4e4e4-159">Existuje velké množství permutací tento problém tak, aby byl těžko poskytují obecné pokyny, jak jí předcházet.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="4e4e4-160">Buďte opatrní při přístupu k místní proměnné při definování výrazy a buďte opatrní při přístupu k stavu v aktuálním objektu (představované `this`) při vytváření stromu výrazů, který může být vrácen veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="4e4e4-161">Kód ve výrazu může odkazovat na metody nebo vlastnosti v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="4e4e4-162">Toto sestavení musí být přístupné, když je definována výrazem a při kompilaci a kdy je výsledný delegát vyvolán.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="4e4e4-163">Budete splnit pomocí `ReferencedAssemblyNotFoundException` v případech, kdy není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="4e4e4-164">Souhrn</span><span class="sxs-lookup"><span data-stu-id="4e4e4-164">Summary</span></span>

<span data-ttu-id="4e4e4-165">Stromy výrazů, které představují výrazy lambda mohou být zkompilovány k vytvoření delegáta, který můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="4e4e4-166">To poskytuje jeden mechanismus ke spouštění kódu vytvořeného reprezentována strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="4e4e4-167">Strom výrazu představuje kód, který bude spuštěn pro jakékoli dané konstrukce, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="4e4e4-168">Za předpokladu, prostředí, ve kterém zkompilovat a spustit kód odpovídá prostředí, ve kterém vytvoříte výrazu, všechno funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="4e4e4-169">Když, který nestane, chyby jsou velmi předvídatelné a, bude zachycena v první testy z jakéhokoli kódu pomocí stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="4e4e4-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="4e4e4-170">Další--Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="4e4e4-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
