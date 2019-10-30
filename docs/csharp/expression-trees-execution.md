---
title: Spouštění stromů výrazů
description: Přečtěte si informace o spouštění stromů výrazů jejich převodem na instrukce ke spustitelnému jazyku IL (executable Intermediate Language).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037117"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="07e5f-103">Spouštění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="07e5f-103">Executing Expression Trees</span></span>

[<span data-ttu-id="07e5f-104">Předchozí typy architektury podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="07e5f-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="07e5f-105">*Strom výrazů* je datová struktura, která představuje nějaký kód.</span><span class="sxs-lookup"><span data-stu-id="07e5f-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="07e5f-106">Není zkompilován a spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="07e5f-106">It is not compiled and executable code.</span></span> <span data-ttu-id="07e5f-107">Pokud chcete spustit kód .NET, který je reprezentován stromem výrazu, je nutné jej převést na spustitelné instrukce IL.</span><span class="sxs-lookup"><span data-stu-id="07e5f-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="07e5f-108">Výrazy lambda pro funkce</span><span class="sxs-lookup"><span data-stu-id="07e5f-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="07e5f-109">Můžete převést libovolný LambdaExpression nebo jakýkoli typ odvozený z LambdaExpression do spustitelného IL.</span><span class="sxs-lookup"><span data-stu-id="07e5f-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="07e5f-110">Jiné typy výrazů nelze přímo převést na kód.</span><span class="sxs-lookup"><span data-stu-id="07e5f-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="07e5f-111">Toto omezení má malý účinek v praxi.</span><span class="sxs-lookup"><span data-stu-id="07e5f-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="07e5f-112">Výrazy lambda jsou jediné typy výrazů, které byste chtěli provést převodem do spustitelného zprostředkujícího jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="07e5f-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="07e5f-113">(Zamyslete se nad tím, co by to znamenalo k přímému spuštění `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="07e5f-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="07e5f-114">To znamená cokoli užitečné?) Libovolný strom výrazů, který je `LambdaExpression`nebo typ odvozený od `LambdaExpression`, lze převést na IL.</span><span class="sxs-lookup"><span data-stu-id="07e5f-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="07e5f-115">Typ výrazu `Expression<TDelegate>` je jediný konkrétní příklad v knihovnách .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07e5f-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="07e5f-116">Slouží k reprezentaci výrazu, který se mapuje na libovolný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="07e5f-117">Vzhledem k tomu, že tento typ je namapován na typ delegáta, může rozhraní .NET prověřit výraz a vygenerovat IL pro příslušný delegáta, který odpovídá signatuře výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="07e5f-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="07e5f-118">Ve většině případů to vytvoří jednoduché mapování mezi výrazem a jeho odpovídajícím delegátem.</span><span class="sxs-lookup"><span data-stu-id="07e5f-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="07e5f-119">Například strom výrazu, který je reprezentován `Expression<Func<int>>`, by byl převeden na delegáta typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="07e5f-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="07e5f-120">Pro výraz lambda s jakýmkoli návratovým typem a seznamem argumentů existuje typ delegáta, který je cílovým typem pro spustitelný kód reprezentovaný tímto výrazem lambda.</span><span class="sxs-lookup"><span data-stu-id="07e5f-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="07e5f-121">Typ `LambdaExpression` obsahuje členy `Compile` a `CompileToMethod`, které byste použili k převodu stromu výrazu na spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="07e5f-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="07e5f-122">Metoda `Compile` vytvoří delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="07e5f-123">Metoda `CompileToMethod` aktualizuje objekt `MethodBuilder` pomocí IL, který představuje zkompilovaný výstup stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="07e5f-124">Všimněte si, že `CompileToMethod` je k dispozici pouze v rozhraních kompletní plocha, nikoli v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07e5f-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="07e5f-125">Volitelně můžete také zadat `DebugInfoGenerator`, které obdrží informace o ladění symbolů pro generovaný objekt delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="07e5f-126">To umožňuje převést strom výrazu na objekt delegáta a získat úplné informace o ladění vygenerovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="07e5f-127">Výraz byste převedli na delegáta pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="07e5f-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="07e5f-128">Všimněte si, že typ delegáta je založen na typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="07e5f-129">Je nutné znát návratový typ a seznam argumentů, pokud chcete použít objekt delegáta ve silném typu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="07e5f-130">Metoda `LambdaExpression.Compile()` vrací typ `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="07e5f-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="07e5f-131">Budete je muset přetypovat na správný typ delegáta, aby se všechny nástroje v čase kompilace zkontrolovaly v seznamu argumentů nebo v návratovém typu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="07e5f-132">Spuštění a životnost</span><span class="sxs-lookup"><span data-stu-id="07e5f-132">Execution and Lifetimes</span></span>

<span data-ttu-id="07e5f-133">Spusťte kód vyvoláním delegáta vytvořeného při volání `LambdaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="07e5f-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="07e5f-134">Vidíte to výše, kde `add.Compile()` vrací delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="07e5f-135">Volání tohoto delegáta voláním `func()` spustí kód.</span><span class="sxs-lookup"><span data-stu-id="07e5f-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="07e5f-136">Tento delegát představuje kód ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="07e5f-137">Můžete zachovat popisovač pro daného delegáta a vyvolat ho později.</span><span class="sxs-lookup"><span data-stu-id="07e5f-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="07e5f-138">Strom výrazů není nutné kompilovat pokaždé, když chcete spustit kód, který představuje.</span><span class="sxs-lookup"><span data-stu-id="07e5f-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="07e5f-139">(Nezapomeňte, že stromy výrazů jsou neměnné a kompilace stejného stromu výrazů později vytvoří delegáta, který spustí stejný kód.)</span><span class="sxs-lookup"><span data-stu-id="07e5f-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="07e5f-140">Při pokusu o vytvoření jakýchkoli propracovaných mechanismů pro ukládání do mezipaměti se mi bude snažit zvýšit výkon tím, že se vyhnete zbytečným voláním kompilace.</span><span class="sxs-lookup"><span data-stu-id="07e5f-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="07e5f-141">Porovnání dvou libovolných stromů výrazů k určení, jestli představují stejný algoritmus, bude také časově náročné na provedení.</span><span class="sxs-lookup"><span data-stu-id="07e5f-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="07e5f-142">Pravděpodobně zjistíte, že úsporný čas, který byste ušetřili, aby nedošlo k žádnému nadbytečnému volání `LambdaExpression.Compile()` bude více než spotřebované při provádění kódu, který určuje, že se dvě různé stromy výrazů vrátí do stejného spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="07e5f-143">Upozornění</span><span class="sxs-lookup"><span data-stu-id="07e5f-143">Caveats</span></span>

<span data-ttu-id="07e5f-144">Kompilování výrazu lambda do delegáta a vyvolání tohoto delegáta je jedním z nejjednodušších operací, které můžete provádět se stromem výrazů.</span><span class="sxs-lookup"><span data-stu-id="07e5f-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="07e5f-145">I když je však tato jednoduchá operace k dispozici, je nutné mít na paměti informace o aspektech.</span><span class="sxs-lookup"><span data-stu-id="07e5f-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="07e5f-146">Výrazy lambda vytvoří uzávěry pro všechny místní proměnné, na které se odkazuje ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="07e5f-147">Musíte zaručit, aby všechny proměnné, které by byly součástí delegáta, byly použitelné v umístění, kde zavoláte `Compile`, a při spuštění výsledného delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="07e5f-148">Obecně kompilátor zajistí, že se jedná o true.</span><span class="sxs-lookup"><span data-stu-id="07e5f-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="07e5f-149">Nicméně pokud váš výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že váš kód může vyřadit objekt, když je stále ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="07e5f-150">Tento kód například funguje správně, protože `int` neimplementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="07e5f-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="07e5f-151">Delegát zachytil odkaz na místní proměnnou `constant`.</span><span class="sxs-lookup"><span data-stu-id="07e5f-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="07e5f-152">K této proměnné lze kdykoli později přejít, když se funkce vrátí `CreateBoundFunc` spustí.</span><span class="sxs-lookup"><span data-stu-id="07e5f-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="07e5f-153">Zvažte však tuto třídu (spíše contrived), která implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="07e5f-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="07e5f-154">Pokud ho použijete ve výrazu, jak je vidět níže, dostanete `ObjectDisposedException`, když spustíte kód, na který odkazuje vlastnost `Resource.Argument`:</span><span class="sxs-lookup"><span data-stu-id="07e5f-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="07e5f-155">Delegát vrácený touto metodou byl uzavřen nad objektem `constant`, který byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="07e5f-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="07e5f-156">(Bylo zrušeno, protože bylo deklarováno v příkazu `using`.)</span><span class="sxs-lookup"><span data-stu-id="07e5f-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="07e5f-157">Když nyní spustíte delegáta, který je vrácen z této metody, budete mít `ObjectDisposedException` vyvolána v okamžiku spuštění.</span><span class="sxs-lookup"><span data-stu-id="07e5f-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="07e5f-158">Zdá se, že došlo k chybě za běhu představující konstrukci v čase kompilace, ale to je World, který zadáte při práci s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="07e5f-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="07e5f-159">Tento problém je hodně permutací, takže je těžké nabídnout obecné pokyny, abyste se k tomu předešli.</span><span class="sxs-lookup"><span data-stu-id="07e5f-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="07e5f-160">Při vytváření stromu výrazů, který může být vrácen veřejným rozhraním API, buďte opatrní při přístupu k místním proměnným při definování výrazů a buďte opatrní při přístupu ke stavu v aktuálním objektu (reprezentovaný `this`).</span><span class="sxs-lookup"><span data-stu-id="07e5f-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="07e5f-161">Kód ve výrazu může odkazovat na metody nebo vlastnosti v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="07e5f-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="07e5f-162">Toto sestavení musí být přístupné při definování výrazu a při jeho kompilaci a při vyvolání výsledného delegáta.</span><span class="sxs-lookup"><span data-stu-id="07e5f-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="07e5f-163">V případech, kdy není k dispozici, se zobrazí `ReferencedAssemblyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="07e5f-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="07e5f-164">Souhrn</span><span class="sxs-lookup"><span data-stu-id="07e5f-164">Summary</span></span>

<span data-ttu-id="07e5f-165">Stromy výrazů, které reprezentují výrazy lambda, mohou být zkompilovány k vytvoření delegáta, který lze spustit.</span><span class="sxs-lookup"><span data-stu-id="07e5f-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="07e5f-166">To poskytuje jeden mechanismus pro spuštění kódu reprezentovaného stromem výrazu.</span><span class="sxs-lookup"><span data-stu-id="07e5f-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="07e5f-167">Strom výrazu představuje kód, který by byl proveden pro libovolnou vytvořenou konstrukci.</span><span class="sxs-lookup"><span data-stu-id="07e5f-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="07e5f-168">Dokud prostředí, kde kompilujete a spouštíte kód, odpovídá prostředí, ve kterém vytvoříte výraz, vše funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="07e5f-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="07e5f-169">Pokud k tomu nedojde, chyby jsou velmi předvídatelné a budou zachyceny v prvních testech libovolného kódu pomocí stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="07e5f-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="07e5f-170">Další – interpretují se výrazy.</span><span class="sxs-lookup"><span data-stu-id="07e5f-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
