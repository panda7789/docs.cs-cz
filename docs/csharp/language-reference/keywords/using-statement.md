---
title: "using – příkaz (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="aaf6a-102">using – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aaf6a-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="aaf6a-103">Poskytuje pohodlné syntaxe, které zajišťuje správné použití <xref:System.IDisposable> objekty.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf6a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aaf6a-104">Example</span></span>  
 <span data-ttu-id="aaf6a-105">Následující příklad ukazuje způsob použití pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-105">The following example shows how to use the using statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="aaf6a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaf6a-106">Remarks</span></span>  
 <span data-ttu-id="aaf6a-107"><xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, která přistupují k nespravované prostředky (v této obslužné rutiny souborů případu a kontexty zařízení).</span><span class="sxs-lookup"><span data-stu-id="aaf6a-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="aaf6a-108">Existuje mnoho dalších druhů nespravované prostředky a typů knihovny tříd, které zapouzdřují je.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="aaf6a-109">Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="aaf6a-110">Po dobu životnosti `IDisposable` objektu je omezený na jednu metodu, musí deklarovat a vytvoří instanci v `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="aaf6a-111">`using` Příkaz volání <xref:System.IDisposable.Dispose%2A> metoda v objektu správným způsobem a (pokud ji používáte jako je uvedené výše) také způsobuje, že samotného se dostala mimo rozsah objektu co nejrychleji <xref:System.IDisposable.Dispose%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="aaf6a-112">V rámci `using` blok, objekt je jen pro čtení a nelze změnit ani znovu přiřazen.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="aaf6a-113">`using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> je volána, i když dojde k výjimce při volání metody pro objekt.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="aaf6a-114">Můžete dosáhnout stejný výsledek vložení objektu do bloku try a pak voláním <xref:System.IDisposable.Dispose%2A> v a nakonec blokovat; ve skutečnosti, jedná se jak `using` příkaz je přeložen kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-114">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="aaf6a-115">Příklad kódu se dříve zasahuje do následující kód v době kompilace (Všimněte si velmi složené závorky k vytvoření omezeným oborem pro objekt):</span><span class="sxs-lookup"><span data-stu-id="aaf6a-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 <span data-ttu-id="aaf6a-116">V může být deklarován více instancí typu `using` příkaz, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-116">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="aaf6a-117">Můžete vytvořit instanci objektu prostředků a pak předejte proměnnou `using` prohlášení, ale to není osvědčený postup.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-117">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="aaf6a-118">V takovém případě zůstane objekt v oboru řízení odešel `using` blokovat, i když je pravděpodobně nebude mít přístup k jeho nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-118">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="aaf6a-119">Jinými slovy ji budou už inicializována plně.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-119">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="aaf6a-120">Pokud se pokusíte použít objekt mimo `using` blok riziko způsobuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-120">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="aaf6a-121">Z tohoto důvodu je obecně lepší vytvořit instanci objektu v `using` příkaz a omezit její obor `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="aaf6a-121">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="aaf6a-122">Další informace o uvolnění `IDisposable` objekty, najdete v části [použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="aaf6a-122">For more information on disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aaf6a-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aaf6a-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf6a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="aaf6a-124">See Also</span></span>  
 [<span data-ttu-id="aaf6a-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aaf6a-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aaf6a-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="aaf6a-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aaf6a-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aaf6a-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="aaf6a-128">Using – direktiva</span><span class="sxs-lookup"><span data-stu-id="aaf6a-128">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="aaf6a-129">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="aaf6a-129">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="aaf6a-130">Použití objektů implementujících rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="aaf6a-130">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="aaf6a-131">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="aaf6a-131">IDisposable interface</span></span>](xref:System.IDisposable)
