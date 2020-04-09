---
title: using statement - C# Reference using statement - C# Reference using statement - C# Reference using statement
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989178"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="b965d-102">using příkaz (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="b965d-102">using statement (C# Reference)</span></span>

<span data-ttu-id="b965d-103">Poskytuje pohodlnou syntaxi, která <xref:System.IDisposable> zajišťuje správné použití objektů.</span><span class="sxs-lookup"><span data-stu-id="b965d-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="b965d-104">Počínaje C# `using` 8.0, příkaz zajišťuje správné <xref:System.IAsyncDisposable> použití objektů.</span><span class="sxs-lookup"><span data-stu-id="b965d-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="b965d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b965d-105">Example</span></span>

<span data-ttu-id="b965d-106">Následující příklad ukazuje, jak `using` použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="b965d-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="b965d-107">Počínaje C# 8.0, můžete použít následující alternativní `using` syntaxe pro příkaz, který nevyžaduje závorky:</span><span class="sxs-lookup"><span data-stu-id="b965d-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="b965d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b965d-108">Remarks</span></span>

<span data-ttu-id="b965d-109"><xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontexty zařízení).</span><span class="sxs-lookup"><span data-stu-id="b965d-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="b965d-110">Existuje mnoho dalších druhů nespravovaných prostředků a typů knihovny tříd, které je zapouzdřují.</span><span class="sxs-lookup"><span data-stu-id="b965d-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="b965d-111">Všechny tyto typy <xref:System.IDisposable> musí implementovat <xref:System.IAsyncDisposable> rozhraní nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b965d-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="b965d-112">Pokud je životnost `IDisposable` objektu omezena na jednu metodu, měli byste `using` deklarovat a konkretizovat v příkazu.</span><span class="sxs-lookup"><span data-stu-id="b965d-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="b965d-113">Příkaz `using` volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (při použití, jak je uvedeno výše) také způsobí, <xref:System.IDisposable.Dispose%2A> že samotný objekt přejít mimo rozsah, jakmile je volána.</span><span class="sxs-lookup"><span data-stu-id="b965d-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="b965d-114">V `using` rámci bloku je objekt jen pro čtení a nelze jej změnit ani znovu přiřadit.</span><span class="sxs-lookup"><span data-stu-id="b965d-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="b965d-115">`IAsyncDisposable` Pokud objekt implementuje `IDisposable`místo `using` , <xref:System.IAsyncDisposable.DisposeAsync%2A> příkaz `awaits` volá <xref:System.Threading.Tasks.Task>a vrácené .</span><span class="sxs-lookup"><span data-stu-id="b965d-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.Task>.</span></span>

<span data-ttu-id="b965d-116">Příkaz `using` zajišťuje, <xref:System.IDisposable.Dispose%2A> že <xref:System.IAsyncDisposable.DisposeAsync%2A>(nebo ) je volána i `using` v případě, že dojde k výjimce v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="b965d-116">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="b965d-117">Můžete dosáhnout stejného výsledku vložením `try` objektu <xref:System.IDisposable.Dispose%2A> do <xref:System.IAsyncDisposable.DisposeAsync%2A> bloku `finally` a pak volání (nebo `using` v bloku; ve skutečnosti je to, jak je příkaz přeložen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="b965d-117">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="b965d-118">Příklad kódu dříve rozbalí na následující kód v době kompilace (všimněte si extra složené závorky k vytvoření omezeného oboru pro objekt):</span><span class="sxs-lookup"><span data-stu-id="b965d-118">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="b965d-119">Syntaxe `using` novějšího příkazu se překládá na podobný kód.</span><span class="sxs-lookup"><span data-stu-id="b965d-119">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="b965d-120">Blok `try` se otevře tam, kde je proměnná deklarována.</span><span class="sxs-lookup"><span data-stu-id="b965d-120">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="b965d-121">Blok `finally` je přidán na konci ohraničující blok, obvykle na konci metody.</span><span class="sxs-lookup"><span data-stu-id="b965d-121">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="b965d-122">Další informace o `try` - `finally` příkazu naleznete v článku [try-finally.](try-finally.md)</span><span class="sxs-lookup"><span data-stu-id="b965d-122">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="b965d-123">Více instancí typu lze deklarovat v jednom `using` příkazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b965d-123">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="b965d-124">Všimněte si, že nelze použít implicitně`var`zadané proměnné ( ) při deklarování více proměnných v jednom příkazu:</span><span class="sxs-lookup"><span data-stu-id="b965d-124">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="b965d-125">Můžete kombinovat více deklarací stejného typu pomocí nové syntaxe zavedené s C# 8 také, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b965d-125">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="b965d-126">Můžete vytvořit instanci objektu prostředku a pak `using` předat proměnnou příkazu, ale to není osvědčený postup.</span><span class="sxs-lookup"><span data-stu-id="b965d-126">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="b965d-127">V tomto případě po `using` ovládací prvek opustí blok, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="b965d-127">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="b965d-128">Jinými slovy, už to není úplně inicializováno.</span><span class="sxs-lookup"><span data-stu-id="b965d-128">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="b965d-129">Pokud se pokusíte použít `using` objekt mimo blok, riskujete, že dojde k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="b965d-129">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="b965d-130">Z tohoto důvodu je lepší vytvořit instanci objektu v příkazu `using` `using` a omezit jeho rozsah na blok.</span><span class="sxs-lookup"><span data-stu-id="b965d-130">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="b965d-131">Další informace o likvidaci `IDisposable` objektů naleznete v tématu [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b965d-131">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b965d-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b965d-132">C# language specification</span></span>

<span data-ttu-id="b965d-133">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b965d-133">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b965d-134">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="b965d-134">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="b965d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="b965d-135">See also</span></span>

- [<span data-ttu-id="b965d-136">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b965d-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b965d-137">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b965d-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b965d-138">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b965d-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b965d-139">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="b965d-139">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="b965d-140">Uvolněné</span><span class="sxs-lookup"><span data-stu-id="b965d-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b965d-141">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="b965d-141">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="b965d-142">IJednorázové rozhraní</span><span class="sxs-lookup"><span data-stu-id="b965d-142">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="b965d-143">using statement in C# 8.0</span><span class="sxs-lookup"><span data-stu-id="b965d-143">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
