---
title: pomocí příkazu - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: df116a200795fd20405381fd71e82d1d6fe662bc
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614386"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="719c5-102">Using – příkaz (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="719c5-102">using statement (C# Reference)</span></span>

<span data-ttu-id="719c5-103">Poskytuje pohodlné syntaxe, který zajistí správné použití <xref:System.IDisposable> objekty.</span><span class="sxs-lookup"><span data-stu-id="719c5-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="719c5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="719c5-104">Example</span></span>

<span data-ttu-id="719c5-105">Následující příklad ukazuje způsob použití `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="719c5-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a><span data-ttu-id="719c5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="719c5-106">Remarks</span></span>

<span data-ttu-id="719c5-107"><xref:System.IO.File> a <xref:System.Drawing.Font> jsou příkladem spravované typy, které přístup k nespravovaným prostředkům (v této obslužné rutiny souborů případu a kontexty zařízení).</span><span class="sxs-lookup"><span data-stu-id="719c5-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="719c5-108">Existuje mnoho dalších typů nespravované prostředky a typy v knihovně tříd, které provádí zapouzdření je.</span><span class="sxs-lookup"><span data-stu-id="719c5-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="719c5-109">Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="719c5-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="719c5-110">Když životnosti `IDisposable` objektu je omezen na jedinou metodu, musí deklarovat a vytvoření instance v `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="719c5-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="719c5-111">`using` Příkaz volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (pokud ji používáte jak je uvedeno výše) navíc způsobí, že objekt samotný dostaly mimo obor co nejdříve <xref:System.IDisposable.Dispose%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="719c5-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="719c5-112">V rámci `using` blok, objekt je jen pro čtení a nelze upravovat nebo znovu přiřazen.</span><span class="sxs-lookup"><span data-stu-id="719c5-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="719c5-113">`using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> se nazývá i v případě, že dojde k výjimce v rámci `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="719c5-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="719c5-114">Můžete stejného výsledku dosáhnout vložení objektu uvnitř `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> v `finally` blokovat; ve skutečnosti je to způsob, jak `using` příkaz je přeložen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="719c5-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="719c5-115">Příklad kódu se dříve rozbalí v následujícím kódu v době kompilace (Všimněte si velmi složené závorky do vytvořit omezený obor pro objekt):</span><span class="sxs-lookup"><span data-stu-id="719c5-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="719c5-116">Další informace o `try` - `finally` prohlášení, najdete v článku [try-finally](try-finally.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="719c5-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="719c5-117">Více instancí typu mohou být deklarovány v `using` příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="719c5-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="719c5-118">Můžete vytvořit instanci objektu prostředků a pak předejte proměnnou `using` příkazu, ale to není nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="719c5-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="719c5-119">V takovém případě po ponechá ovládacího prvku `using` blokovat, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="719c5-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="719c5-120">Jinými slovy je inicializován není plně zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="719c5-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="719c5-121">Pokud se pokusíte použít objekt mimo `using` blokovat, riziko způsobuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="719c5-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="719c5-122">Z tohoto důvodu je obecně lepší pro vytvoření instance objektu na `using` příkazu a omezit její obor `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="719c5-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="719c5-123">Další informace o uvolnění `IDisposable` objekty, najdete [použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="719c5-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="719c5-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="719c5-124">C# language specification</span></span>

<span data-ttu-id="719c5-125">Další informace najdete v tématu [příkaz using](~/_csharplang/spec/statements.md#the-using-statement) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="719c5-125">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="719c5-126">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="719c5-126">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="719c5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="719c5-127">See also</span></span>

- [<span data-ttu-id="719c5-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="719c5-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="719c5-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="719c5-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="719c5-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="719c5-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="719c5-131">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="719c5-131">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="719c5-132">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="719c5-132">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="719c5-133">Použití objektů implementujících rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="719c5-133">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="719c5-134">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="719c5-134">IDisposable interface</span></span>](xref:System.IDisposable)