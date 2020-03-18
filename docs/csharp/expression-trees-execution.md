---
title: Provádění stromů výrazů
description: Informace o provádění stromů výrazů jejich převedením do spustitelných pokynů pro středně dobíjecí jazyk (IL).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146018"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="5ce49-103">Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="5ce49-103">Executing Expression Trees</span></span>

[<span data-ttu-id="5ce49-104">Předchozí -- Typy architektury podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="5ce49-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="5ce49-105">*Strom výrazů* je datová struktura, která představuje určitý kód.</span><span class="sxs-lookup"><span data-stu-id="5ce49-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="5ce49-106">Není kompilován a spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="5ce49-106">It is not compiled and executable code.</span></span> <span data-ttu-id="5ce49-107">Pokud chcete spustit kód .NET, který je reprezentován stromem výrazů, musíte jej převést na spustitelné il instrukce.</span><span class="sxs-lookup"><span data-stu-id="5ce49-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="5ce49-108">Lambda výrazy na funkce</span><span class="sxs-lookup"><span data-stu-id="5ce49-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="5ce49-109">Můžete převést libovolný LambdaExpression nebo libovolný typ odvozený z LambdaExpression do spustitelné IL.</span><span class="sxs-lookup"><span data-stu-id="5ce49-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="5ce49-110">Jiné typy výrazů nelze přímo převést na kód.</span><span class="sxs-lookup"><span data-stu-id="5ce49-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="5ce49-111">Toto omezení má v praxi jen malý účinek.</span><span class="sxs-lookup"><span data-stu-id="5ce49-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="5ce49-112">Lambda výrazy jsou pouze typy výrazů, které byste chtěli spustit převodem na spustitelný zprostředkující jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="5ce49-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="5ce49-113">(Přemýšlejte o tom, co `ConstantExpression`by to znamenalo přímo spustit .</span><span class="sxs-lookup"><span data-stu-id="5ce49-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="5ce49-114">Znamenalo by to něco užitečného?) Libovolný strom výrazů, `LambdaExpression`který je , `LambdaExpression` nebo typ odvozený z lze převést na IL.</span><span class="sxs-lookup"><span data-stu-id="5ce49-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="5ce49-115">Typ `Expression<TDelegate>` výrazu je jediným konkrétním příkladem v knihovnách .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ce49-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="5ce49-116">Používá se k reprezentaci výraz, který se mapuje na libovolný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="5ce49-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="5ce49-117">Vzhledem k tomu, že tento typ mapuje na typ delegáta, .NET můžete zkontrolovat výraz a generovat IL pro příslušného delegáta, který odpovídá podpisu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="5ce49-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span>

<span data-ttu-id="5ce49-118">Ve většině případů se tím vytvoří jednoduché mapování mezi výrazem a jeho odpovídajícím delegátem.</span><span class="sxs-lookup"><span data-stu-id="5ce49-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="5ce49-119">Například strom výraz, který `Expression<Func<int>>` je reprezentován by být převedeny na delegáta typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="5ce49-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="5ce49-120">Pro výraz lambda s libovolným návratovým typem a seznamem argumentů existuje typ delegáta, který je cílovým typem pro spustitelný kód reprezentovaný tímto výrazem lambda.</span><span class="sxs-lookup"><span data-stu-id="5ce49-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="5ce49-121">Typ `LambdaExpression` obsahuje `Compile` `CompileToMethod` a členy, které byste použili k převodu stromu výrazů na spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="5ce49-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="5ce49-122">Metoda `Compile` vytvoří delegáta.</span><span class="sxs-lookup"><span data-stu-id="5ce49-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="5ce49-123">Metoda `CompileToMethod` aktualizuje `MethodBuilder` objekt s IL, který představuje zkompilovaný výstup stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="5ce49-124">Všimněte `CompileToMethod` si, že je k dispozici pouze v rámci plochy, nikoli v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ce49-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="5ce49-125">Volitelně můžete také poskytnout, `DebugInfoGenerator` který obdrží informace o ladění symbolu pro generovaný objekt delegáta.</span><span class="sxs-lookup"><span data-stu-id="5ce49-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="5ce49-126">To umožňuje převést strom výrazů na objekt delegáta a mít úplné ladicí informace o generovaném delegátovi.</span><span class="sxs-lookup"><span data-stu-id="5ce49-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="5ce49-127">Výraz byste převedli na delegáta pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5ce49-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="5ce49-128">Všimněte si, že typ delegáta je založen na typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="5ce49-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="5ce49-129">Pokud chcete objekt delegáta použít silným způsobem, musíte znát návratový typ a seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="5ce49-130">Metoda `LambdaExpression.Compile()` vrátí `Delegate` typ.</span><span class="sxs-lookup"><span data-stu-id="5ce49-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="5ce49-131">Budete muset přetypovat na správný typ delegáta, aby všechny nástroje v době kompilace zkontrolovaly seznam argumentů nebo návratový typ.</span><span class="sxs-lookup"><span data-stu-id="5ce49-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="5ce49-132">Provedení a životnost</span><span class="sxs-lookup"><span data-stu-id="5ce49-132">Execution and Lifetimes</span></span>

<span data-ttu-id="5ce49-133">Kód spustíte vyvoláním delegáta vytvořeného při `LambdaExpression.Compile()`volání .</span><span class="sxs-lookup"><span data-stu-id="5ce49-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="5ce49-134">Můžete vidět výše, `add.Compile()` kde vrátí delegáta.</span><span class="sxs-lookup"><span data-stu-id="5ce49-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="5ce49-135">Vyvolání tohoto delegáta voláním `func()` provede kód.</span><span class="sxs-lookup"><span data-stu-id="5ce49-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="5ce49-136">Tento delegát představuje kód ve stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="5ce49-137">Popisovač můžete zachovat na delegáta a vyvolat později.</span><span class="sxs-lookup"><span data-stu-id="5ce49-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="5ce49-138">Není nutné zkompilovat strom výrazu pokaždé, když chcete spustit kód, který představuje.</span><span class="sxs-lookup"><span data-stu-id="5ce49-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="5ce49-139">(Nezapomeňte, že stromy výrazů jsou neměnné a kompilace stejného stromu výrazů později vytvoří delegáta, který provede stejný kód.)</span><span class="sxs-lookup"><span data-stu-id="5ce49-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="5ce49-140">Varuji vás před pokusem o vytvoření sofistikovanějších mechanismů ukládání do mezipaměti pro zvýšení výkonu tím, že se vyhnete zbytečným voláním kompilace.</span><span class="sxs-lookup"><span data-stu-id="5ce49-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="5ce49-141">Porovnání dvou libovolných stromů výrazů k určení, zda představují stejný algoritmus, bude také časově náročné spuštění.</span><span class="sxs-lookup"><span data-stu-id="5ce49-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="5ce49-142">Pravděpodobně zjistíte, že výpočetní čas, který ušetříte, aby se zabránilo dalším voláním, `LambdaExpression.Compile()` bude více než spotřebován časem provádění kódu, který určuje dva různé stromy výrazů, což vede ke stejnému spustitelnému kódu.</span><span class="sxs-lookup"><span data-stu-id="5ce49-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="5ce49-143">Upozornění</span><span class="sxs-lookup"><span data-stu-id="5ce49-143">Caveats</span></span>

<span data-ttu-id="5ce49-144">Kompilace výrazu lambda delegátovi a vyvolání tohoto delegáta je jednou z nejjednodušších operací, které lze provést se stromem výrazů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="5ce49-145">Nicméně, i s touto jednoduchou operací, tam jsou upozornění, musíte být vědomi.</span><span class="sxs-lookup"><span data-stu-id="5ce49-145">However, even with this simple operation, there are caveats you must be aware of.</span></span>

<span data-ttu-id="5ce49-146">Lambda výrazy vytvořit uzavření přes všechny místní proměnné, které jsou odkazovány ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="5ce49-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="5ce49-147">Musíte zaručit, že všechny proměnné, které by byly součástí delegáta, `Compile`jsou použitelné v umístění, kde voláte , a při spuštění výsledného delegáta.</span><span class="sxs-lookup"><span data-stu-id="5ce49-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="5ce49-148">Obecně kompilátor zajistí, že je to pravda.</span><span class="sxs-lookup"><span data-stu-id="5ce49-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="5ce49-149">Pokud však výraz přistupuje `IDisposable`k proměnné, která implementuje , je možné, že váš kód může nakládat s objektem, zatímco je stále držen stromem výrazů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="5ce49-150">Například tento kód funguje `int` dobře, `IDisposable`protože neimplementuje :</span><span class="sxs-lookup"><span data-stu-id="5ce49-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="5ce49-151">Delegát zachytil odkaz na místní proměnnou `constant`.</span><span class="sxs-lookup"><span data-stu-id="5ce49-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="5ce49-152">Tato proměnná je přístupná kdykoli později, `CreateBoundFunc` když funkce vrácená provede.</span><span class="sxs-lookup"><span data-stu-id="5ce49-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="5ce49-153">Zvažte však tuto (spíše vykonstruovanou) třídu, která implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="5ce49-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="5ce49-154">Pokud jej použijete ve výrazu, jak je `ObjectDisposedException` znázorněno níže, získáte `Resource.Argument` při spuštění kódu, na který odkazuje vlastnost:</span><span class="sxs-lookup"><span data-stu-id="5ce49-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="5ce49-155">Delegát vrácené z této metody `constant` byl uzavřen přes objekt, který byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="5ce49-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="5ce49-156">(Byl vyřazen, protože byl deklarován v příkazu.) `using`</span><span class="sxs-lookup"><span data-stu-id="5ce49-156">(It's been disposed, because it was declared in a `using` statement.)</span></span>

<span data-ttu-id="5ce49-157">Nyní při spuštění delegáta vrácena z této metody, budete mít `ObjectDisposedException` vyvolána v místě spuštění.</span><span class="sxs-lookup"><span data-stu-id="5ce49-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="5ce49-158">Zdá se divné mít chybu za běhu představující konstrukci v době kompilace, ale to je svět, do kterého vstupujeme při práci se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="5ce49-159">Existuje mnoho permutací tohoto problému, takže je těžké nabídnout obecné pokyny, aby se mu zabránilo.</span><span class="sxs-lookup"><span data-stu-id="5ce49-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="5ce49-160">Při definování výrazů buďte opatrní při přístupu k místním proměnným a buďte opatrní `this`při přístupu ke stavu v aktuálním objektu (reprezentovaném) při vytváření stromu výrazů, který může být vrácen veřejným rozhraním API.</span><span class="sxs-lookup"><span data-stu-id="5ce49-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="5ce49-161">Kód ve výrazu může odkazovat na metody nebo vlastnosti v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="5ce49-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="5ce49-162">Toto sestavení musí být přístupné, když je definován výraz a když je kompilován a když je vyvolán výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="5ce49-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="5ce49-163">Setkáte se s `ReferencedAssemblyNotFoundException` ním v případech, kdy není přítomen.</span><span class="sxs-lookup"><span data-stu-id="5ce49-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="5ce49-164">Souhrn</span><span class="sxs-lookup"><span data-stu-id="5ce49-164">Summary</span></span>

<span data-ttu-id="5ce49-165">Stromy výrazů, které představují výrazy lambda, mohou být zkompilovány a vytvořit delegáta, kterého můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="5ce49-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="5ce49-166">To poskytuje jeden mechanismus pro spuštění kódu reprezentovaného stromem výrazu.</span><span class="sxs-lookup"><span data-stu-id="5ce49-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="5ce49-167">Strom výrazů představuje kód, který by se spouštěl pro danou konstrukci, kterou vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="5ce49-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="5ce49-168">Tak dlouho, dokud prostředí, kde zkompilujete a spustíte kód odpovídá prostředí, kde vytvoříte výraz, vše funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="5ce49-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="5ce49-169">Pokud k tomu nedojde, chyby jsou velmi předvídatelné a budou zachyceny v prvních testech libovolného kódu pomocí stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="5ce49-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="5ce49-170">Další -- Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="5ce49-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
