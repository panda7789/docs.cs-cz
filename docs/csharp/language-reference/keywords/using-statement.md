---
title: using – reference jazyka C#
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 3c479faeeb66865b8c368edba881429a7cb956ec
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199674"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="96e01-102">using – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="96e01-102">using statement (C# Reference)</span></span>

<span data-ttu-id="96e01-103">Poskytuje pohodlný syntax, který zajišťuje správné použití <xref:System.IDisposable> objektů.</span><span class="sxs-lookup"><span data-stu-id="96e01-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="96e01-104">Počínaje jazykem C# 8,0 `using` příkaz zajišťuje správné použití <xref:System.IAsyncDisposable> objektů.</span><span class="sxs-lookup"><span data-stu-id="96e01-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="96e01-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="96e01-105">Example</span></span>

<span data-ttu-id="96e01-106">Následující příklad ukazuje, jak použít `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="96e01-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="96e01-107">Počínaje jazykem C# 8,0 můžete použít následující alternativní syntaxi pro `using` příkaz, který nevyžaduje složené závorky:</span><span class="sxs-lookup"><span data-stu-id="96e01-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="96e01-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96e01-108">Remarks</span></span>

<span data-ttu-id="96e01-109"><xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontexty zařízení).</span><span class="sxs-lookup"><span data-stu-id="96e01-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="96e01-110">Existuje mnoho dalších druhů nespravovaných prostředků a typů knihoven tříd, které je zapouzdřují.</span><span class="sxs-lookup"><span data-stu-id="96e01-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="96e01-111">Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní nebo <xref:System.IAsyncDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96e01-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="96e01-112">Pokud je životnost `IDisposable` objektu omezena na jedinou metodu, měli byste deklarovat a vytvořit jeho instanci v `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="96e01-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="96e01-113">`using` Příkaz volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (při použití, jak je uvedeno výše), také způsobí, že se objekt sám vrátí do rozsahu, jakmile <xref:System.IDisposable.Dispose%2A> je volán.</span><span class="sxs-lookup"><span data-stu-id="96e01-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="96e01-114">V rámci `using` bloku je objekt jen pro čtení a nedá se změnit ani znovu přiřadit.</span><span class="sxs-lookup"><span data-stu-id="96e01-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="96e01-115">Pokud objekt implementuje `IAsyncDisposable` místo `IDisposable`, `using` příkaz zavolá <xref:System.IAsyncDisposable.DisposeAsync%2A> a `awaits` vrátí. <xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="96e01-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.Task>.</span></span>

<span data-ttu-id="96e01-116">`using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> (nebo <xref:System.IAsyncDisposable.DisposeAsync%2A>) je volána i v případě, že v rámci `using` bloku dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="96e01-116">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="96e01-117">Stejný výsledek můžete dosáhnout vložením objektu `try` dovnitř bloku a následným voláním <xref:System.IDisposable.Dispose%2A> (nebo <xref:System.IAsyncDisposable.DisposeAsync%2A>) v `finally` bloku. ve skutečnosti se jedná o způsob překladu `using` příkazu kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="96e01-117">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="96e01-118">Výše uvedený příklad kódu se v době kompilace rozšíří na následující kód (Poznamenejte si nadbytečné složené závorky pro vytvoření omezeného oboru pro objekt):</span><span class="sxs-lookup"><span data-stu-id="96e01-118">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="96e01-119">Novější `using` syntaxe příkazu se překládá na podobný kód.</span><span class="sxs-lookup"><span data-stu-id="96e01-119">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="96e01-120">`try` Blok se otevře, kde je proměnná deklarována.</span><span class="sxs-lookup"><span data-stu-id="96e01-120">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="96e01-121">`finally` Blok se přidá na konec ohraničujícího bloku, obvykle na konci metody.</span><span class="sxs-lookup"><span data-stu-id="96e01-121">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="96e01-122">Další `try` - `finally` informace o příkazu naleznete v článku [try-finally](try-finally.md) .</span><span class="sxs-lookup"><span data-stu-id="96e01-122">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="96e01-123">V jednom `using` příkazu lze deklarovat více instancí typu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="96e01-123">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="96e01-124">Všimněte si, že nemůžete použít implicitní typové`var`proměnné (), pokud deklarujete více proměnných v jednom příkazu:</span><span class="sxs-lookup"><span data-stu-id="96e01-124">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="96e01-125">Můžete zkombinovat více deklarací stejného typu pomocí nové syntaxe představené v jazyce C# 8, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="96e01-125">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="96e01-126">Můžete vytvořit instanci objektu prostředku a pak předat proměnnou `using` příkazu, ale to není doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="96e01-126">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="96e01-127">V takovém případě, když ovládací prvek `using` opustí blok, objekt zůstane v oboru, ale pravděpodobně nemá přístup k nespravovaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="96e01-127">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="96e01-128">Jinými slovy, již není zcela inicializován.</span><span class="sxs-lookup"><span data-stu-id="96e01-128">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="96e01-129">Pokud se pokusíte použít objekt mimo `using` blok, riskujete, že bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="96e01-129">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="96e01-130">Z tohoto důvodu je lepší vytvořit instanci objektu v `using` příkazu a omezit svůj rozsah na `using` blok.</span><span class="sxs-lookup"><span data-stu-id="96e01-130">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="96e01-131">Další informace o odstraňování `IDisposable` objektů najdete v tématu [použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="96e01-131">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="96e01-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="96e01-132">C# language specification</span></span>

<span data-ttu-id="96e01-133">Další informace naleznete ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction)v [příkazu Using](~/_csharplang/spec/statements.md#the-using-statement) .</span><span class="sxs-lookup"><span data-stu-id="96e01-133">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="96e01-134">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="96e01-134">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="96e01-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="96e01-135">See also</span></span>

- [<span data-ttu-id="96e01-136">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="96e01-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="96e01-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="96e01-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="96e01-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="96e01-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="96e01-139">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="96e01-139">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="96e01-140">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="96e01-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="96e01-141">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="96e01-141">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="96e01-142">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="96e01-142">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="96e01-143">using – příkaz v C# 8,0</span><span class="sxs-lookup"><span data-stu-id="96e01-143">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
