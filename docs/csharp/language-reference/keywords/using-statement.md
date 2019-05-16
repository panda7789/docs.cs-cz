---
title: pomocí příkazu - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: e1a1a960fa69be593ea01cab51be576b0055fd5e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632903"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="f2619-102">Using – příkaz (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="f2619-102">using statement (C# Reference)</span></span>

<span data-ttu-id="f2619-103">Poskytuje pohodlné syntaxe, který zajistí správné použití <xref:System.IDisposable> objekty.</span><span class="sxs-lookup"><span data-stu-id="f2619-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="f2619-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2619-104">Example</span></span>

<span data-ttu-id="f2619-105">Následující příklad ukazuje způsob použití `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f2619-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a><span data-ttu-id="f2619-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2619-106">Remarks</span></span>

<span data-ttu-id="f2619-107"><xref:System.IO.File> a <xref:System.Drawing.Font> jsou příkladem spravované typy, které přístup k nespravovaným prostředkům (v této obslužné rutiny souborů případu a kontexty zařízení).</span><span class="sxs-lookup"><span data-stu-id="f2619-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="f2619-108">Existuje mnoho dalších typů nespravované prostředky a typy v knihovně tříd, které provádí zapouzdření je.</span><span class="sxs-lookup"><span data-stu-id="f2619-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="f2619-109">Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f2619-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="f2619-110">Když životnosti `IDisposable` objektu je omezen na jedinou metodu, musí deklarovat a vytvoření instance v `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f2619-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="f2619-111">`using` Příkaz volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (pokud ji používáte jak je uvedeno výše) navíc způsobí, že objekt samotný dostaly mimo obor co nejdříve <xref:System.IDisposable.Dispose%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="f2619-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="f2619-112">V rámci `using` blok, objekt je jen pro čtení a nelze upravovat nebo znovu přiřazen.</span><span class="sxs-lookup"><span data-stu-id="f2619-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="f2619-113">`using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> se nazývá i v případě, že dojde k výjimce v rámci `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="f2619-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="f2619-114">Můžete stejného výsledku dosáhnout vložení objektu uvnitř `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> v `finally` blokovat; ve skutečnosti je to způsob, jak `using` příkaz je přeložen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="f2619-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="f2619-115">Příklad kódu se dříve rozbalí v následujícím kódu v době kompilace (Všimněte si velmi složené závorky do vytvořit omezený obor pro objekt):</span><span class="sxs-lookup"><span data-stu-id="f2619-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="f2619-116">Další informace o `try` - `finally` prohlášení, najdete v článku [try-finally](try-finally.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="f2619-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="f2619-117">Více instancí typu mohou být deklarovány v `using` příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f2619-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="f2619-118">Můžete vytvořit instanci objektu prostředků a pak předejte proměnnou `using` příkazu, ale to není nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="f2619-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="f2619-119">V takovém případě po ponechá ovládacího prvku `using` blokovat, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="f2619-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="f2619-120">Jinými slovy je inicializován není plně zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="f2619-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="f2619-121">Pokud se pokusíte použít objekt mimo `using` blokovat, riziko způsobuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="f2619-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="f2619-122">Z tohoto důvodu je obecně lepší pro vytvoření instance objektu na `using` příkazu a omezit její obor `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="f2619-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="f2619-123">Další informace o uvolnění `IDisposable` objekty, najdete [použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f2619-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2619-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2619-124">C# language specification</span></span>

<span data-ttu-id="f2619-125">Další informace najdete v tématu [příkaz using](~/_csharplang/spec/statements.md#the-using-statement) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2619-125">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="f2619-126">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f2619-126">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2619-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2619-127">See also</span></span>

- [<span data-ttu-id="f2619-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2619-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2619-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f2619-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2619-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2619-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f2619-131">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="f2619-131">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="f2619-132">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="f2619-132">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="f2619-133">Použití objektů implementujících rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="f2619-133">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="f2619-134">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="f2619-134">IDisposable interface</span></span>](xref:System.IDisposable)
