---
title: using statement - C# Reference using statement - C# Reference using statement - C# Reference using statement
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712959"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="8e846-102">using příkaz (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="8e846-102">using statement (C# Reference)</span></span>

<span data-ttu-id="8e846-103">Poskytuje pohodlnou syntaxi, která <xref:System.IDisposable> zajišťuje správné použití objektů.</span><span class="sxs-lookup"><span data-stu-id="8e846-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="8e846-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e846-104">Example</span></span>

<span data-ttu-id="8e846-105">Následující příklad ukazuje, jak `using` použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e846-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="8e846-106">Počínaje C# 8.0, můžete použít následující alternativní `using` syntaxe pro příkaz, který nevyžaduje závorky:</span><span class="sxs-lookup"><span data-stu-id="8e846-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="8e846-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e846-107">Remarks</span></span>

<span data-ttu-id="8e846-108"><xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontexty zařízení).</span><span class="sxs-lookup"><span data-stu-id="8e846-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="8e846-109">Existuje mnoho dalších druhů nespravovaných prostředků a typů knihovny tříd, které je zapouzdřují.</span><span class="sxs-lookup"><span data-stu-id="8e846-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="8e846-110">Všechny tyto typy <xref:System.IDisposable> musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e846-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="8e846-111">Pokud je životnost `IDisposable` objektu omezena na jednu metodu, měli byste `using` deklarovat a konkretizovat v příkazu.</span><span class="sxs-lookup"><span data-stu-id="8e846-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="8e846-112">Příkaz `using` volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (při použití, jak je uvedeno výše) také způsobí, <xref:System.IDisposable.Dispose%2A> že samotný objekt přejít mimo rozsah, jakmile je volána.</span><span class="sxs-lookup"><span data-stu-id="8e846-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="8e846-113">V `using` rámci bloku je objekt jen pro čtení a nelze jej změnit ani znovu přiřadit.</span><span class="sxs-lookup"><span data-stu-id="8e846-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="8e846-114">Příkaz `using` zajišťuje, <xref:System.IDisposable.Dispose%2A> že je volána i v `using` případě, že dojde k výjimce v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="8e846-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="8e846-115">Můžete dosáhnout stejného výsledku vložením `try` objektu <xref:System.IDisposable.Dispose%2A> do `finally` bloku a následným voláním bloku; ve skutečnosti je to, jak je `using` příkaz přeložen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="8e846-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="8e846-116">Příklad kódu dříve rozbalí na následující kód v době kompilace (všimněte si extra složené závorky k vytvoření omezeného oboru pro objekt):</span><span class="sxs-lookup"><span data-stu-id="8e846-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="8e846-117">Syntaxe `using` novějšího příkazu se překládá na velmi podobný kód.</span><span class="sxs-lookup"><span data-stu-id="8e846-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="8e846-118">Blok `try` se otevře tam, kde je proměnná deklarována.</span><span class="sxs-lookup"><span data-stu-id="8e846-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="8e846-119">Blok `finally` je přidán na konci ohraničující blok, obvykle na konci metody.</span><span class="sxs-lookup"><span data-stu-id="8e846-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="8e846-120">Další informace o `try` - `finally` příkazu naleznete v tématu [try-finally.](try-finally.md)</span><span class="sxs-lookup"><span data-stu-id="8e846-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="8e846-121">Více instancí typu lze deklarovat v příkazu, `using` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e846-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="8e846-122">Můžete kombinovat více deklarací stejného typu pomocí nové syntaxe zavedené s C# 8 také.</span><span class="sxs-lookup"><span data-stu-id="8e846-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="8e846-123">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e846-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="8e846-124">Můžete vytvořit instanci objektu prostředku a potom `using` předat proměnnou příkazu, ale to není osvědčený postup.</span><span class="sxs-lookup"><span data-stu-id="8e846-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="8e846-125">V tomto případě po `using` ovládací prvek opustí blok, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="8e846-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="8e846-126">Jinými slovy, už to není úplně inicializováno.</span><span class="sxs-lookup"><span data-stu-id="8e846-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="8e846-127">Pokud se pokusíte použít `using` objekt mimo blok, riskujete, že dojde k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="8e846-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="8e846-128">Z tohoto důvodu je obecně lepší vytvořit instanci `using` objektu v příkazu `using` a omezit jeho rozsah na blok.</span><span class="sxs-lookup"><span data-stu-id="8e846-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="8e846-129">Další informace o likvidaci `IDisposable` objektů naleznete v tématu [Použití objektů, které implementují IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="8e846-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8e846-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e846-130">C# language specification</span></span>

<span data-ttu-id="8e846-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="8e846-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8e846-132">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8e846-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e846-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e846-133">See also</span></span>

- [<span data-ttu-id="8e846-134">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e846-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8e846-135">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e846-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8e846-136">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8e846-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8e846-137">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="8e846-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="8e846-138">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="8e846-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="8e846-139">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="8e846-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="8e846-140">IJednorázové rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e846-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="8e846-141">using statement in C# 8.0</span><span class="sxs-lookup"><span data-stu-id="8e846-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
