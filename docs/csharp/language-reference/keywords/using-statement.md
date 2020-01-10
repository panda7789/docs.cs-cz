---
title: použití odkazu na C# příkaz
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712959"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="f144e-102">using – příkazC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="f144e-102">using statement (C# Reference)</span></span>

<span data-ttu-id="f144e-103">Poskytuje pohodlný syntax, který zajišťuje správné použití <xref:System.IDisposable> objektů.</span><span class="sxs-lookup"><span data-stu-id="f144e-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="f144e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f144e-104">Example</span></span>

<span data-ttu-id="f144e-105">Následující příklad ukazuje, jak použít příkaz `using`.</span><span class="sxs-lookup"><span data-stu-id="f144e-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="f144e-106">Počínaje C# 8,0 můžete použít následující alternativní syntaxi pro příkaz `using`, který nevyžaduje složené závorky:</span><span class="sxs-lookup"><span data-stu-id="f144e-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="f144e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f144e-107">Remarks</span></span>

<span data-ttu-id="f144e-108">Příklady spravovaných typů, které přistupují k nespravovaným prostředkům (v tomto případě popisovače souborů a kontextech zařízení), jsou <xref:System.IO.File> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="f144e-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="f144e-109">Existuje mnoho dalších druhů nespravovaných prostředků a typů knihoven tříd, které je zapouzdřují.</span><span class="sxs-lookup"><span data-stu-id="f144e-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="f144e-110">Všechny tyto typy musí implementovat rozhraní <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="f144e-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="f144e-111">Pokud je životnost objektu `IDisposable` omezená na jedinou metodu, měli byste deklarovat a vytvořit jeho instanci v příkazu `using`.</span><span class="sxs-lookup"><span data-stu-id="f144e-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="f144e-112">Příkaz `using` volá metodu <xref:System.IDisposable.Dispose%2A> objektu správným způsobem a (pokud ji použijete, jak je uvedeno výše), také způsobí, že se objekt sám dostanou mimo rozsah, jakmile se zavolá <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="f144e-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="f144e-113">V rámci `using` bloku je objekt určen jen pro čtení a nelze jej změnit ani znovu přiřadit.</span><span class="sxs-lookup"><span data-stu-id="f144e-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="f144e-114">Příkaz `using` zajišťuje, že <xref:System.IDisposable.Dispose%2A> je volána i v případě, že dojde k výjimce v rámci bloku `using`.</span><span class="sxs-lookup"><span data-stu-id="f144e-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="f144e-115">Stejný výsledek můžete dosáhnout vložením objektu do `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> v bloku `finally`; ve skutečnosti je to způsob, jak je příkaz `using` přeložen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="f144e-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="f144e-116">Výše uvedený příklad kódu se v době kompilace rozšíří na následující kód (Poznamenejte si nadbytečné složené závorky pro vytvoření omezeného oboru pro objekt):</span><span class="sxs-lookup"><span data-stu-id="f144e-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="f144e-117">Novější syntaxe příkazu `using` se překládá na velmi podobný kód.</span><span class="sxs-lookup"><span data-stu-id="f144e-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="f144e-118">Blok `try` se otevře, kde je proměnná deklarována.</span><span class="sxs-lookup"><span data-stu-id="f144e-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="f144e-119">Blok `finally` se přidá na konec ohraničujícího bloku, obvykle na konci metody.</span><span class="sxs-lookup"><span data-stu-id="f144e-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="f144e-120">Další informace o příkazu `try`-`finally` naleznete v tématu [try-finally](try-finally.md) .</span><span class="sxs-lookup"><span data-stu-id="f144e-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="f144e-121">V příkazu `using` lze deklarovat více instancí typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f144e-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="f144e-122">Můžete zkombinovat více deklarací stejného typu pomocí nové syntaxe, kterou přináší i C# 8.</span><span class="sxs-lookup"><span data-stu-id="f144e-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="f144e-123">To je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f144e-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="f144e-124">Můžete vytvořit instanci objektu prostředku a pak předat proměnnou do příkazu `using`, ale to není doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="f144e-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="f144e-125">V takovém případě, když ovládací prvek opustí blok `using`, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravovaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="f144e-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="f144e-126">Jinými slovy, již není zcela inicializován.</span><span class="sxs-lookup"><span data-stu-id="f144e-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="f144e-127">Pokud se pokusíte použít objekt mimo blok `using`, riskujete, že bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f144e-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="f144e-128">Z tohoto důvodu je obecně lepší vytvořit instanci objektu v příkazu `using` a omezit svůj rozsah na blok `using`.</span><span class="sxs-lookup"><span data-stu-id="f144e-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="f144e-129">Další informace o odstraňování `IDisposable` objektů naleznete v tématu [using Objects Implements IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f144e-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f144e-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f144e-130">C# language specification</span></span>

<span data-ttu-id="f144e-131">Další informace naleznete ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction)v [příkazu Using](~/_csharplang/spec/statements.md#the-using-statement) .</span><span class="sxs-lookup"><span data-stu-id="f144e-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f144e-132">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f144e-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="f144e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f144e-133">See also</span></span>

- [<span data-ttu-id="f144e-134">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="f144e-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f144e-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f144e-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f144e-136">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f144e-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f144e-137">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="f144e-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="f144e-138">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="f144e-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="f144e-139">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="f144e-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="f144e-140">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="f144e-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="f144e-141">using – příkaz C# v 8,0</span><span class="sxs-lookup"><span data-stu-id="f144e-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
