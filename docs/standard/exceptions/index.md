---
title: "Zpracování a generování výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b064dc39f5807b154a1529eebe17493ae84981cf
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="339c8-102">Zpracování a generování výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="339c8-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="339c8-103">Aplikace musí být schopen zpracovávat chyby, ke kterým došlo během provádění konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="339c8-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="339c8-104">Rozhraní .NET poskytuje model pro oznamování chyb aplikace jednotného: operace .NET označují selhání vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="339c8-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="339c8-105">Výjimky</span><span class="sxs-lookup"><span data-stu-id="339c8-105">Exceptions</span></span>

<span data-ttu-id="339c8-106">Výjimkou je libovolná chyba nebo neočekávanému chování, které se vyskytne provádění programu.</span><span class="sxs-lookup"><span data-stu-id="339c8-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="339c8-107">Výjimky může být vyvolána z důvodu selhání ve vašem kódu nebo kód, který volání (například sdílené knihovny), prostředky operačního systému není k dispozici, neočekávané podmínky, které modul runtime, zaznamená (například kód, který nemůže být ověřen) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="339c8-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that cannot be verified), and so on.</span></span> <span data-ttu-id="339c8-108">Aplikace lze obnovit z některé z těchto podmínek, ale ne od ostatních.</span><span class="sxs-lookup"><span data-stu-id="339c8-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="339c8-109">I když můžete obnovit z většina výjimky aplikací, nelze obnovit z většina výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="339c8-109">Although you can recover from most application exceptions, you cannot recover from most runtime exceptions.</span></span>

<span data-ttu-id="339c8-110">V rozhraní .NET, je objekt, který dědí z výjimka <xref:System.Exception?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="339c8-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="339c8-111">Z oblasti kódu, kde došlo k potížím, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="339c8-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="339c8-112">Výjimka je přidána na zásobník dokud ji zpracovává aplikaci nebo program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="339c8-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="339c8-113">Výjimky oproti tradiční metody zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="339c8-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="339c8-114">Obvyklým model zpracování chyb jazyk spoléhali na jazyka jedinečný způsob zjišťování chyb a vyhledání obslužné rutiny pro ně nebo na mechanizmus zpracování chyb v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="339c8-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="339c8-115">Způsob zpracování výjimek implementuje rozhraní .NET poskytuje následující výhody:</span><span class="sxs-lookup"><span data-stu-id="339c8-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="339c8-116">Výjimka vyvolání a zpracování funguje stejně programovacích jazyků .NET.</span><span class="sxs-lookup"><span data-stu-id="339c8-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="339c8-117">Nevyžaduje žádné konkrétní jazykové syntaxe pro zpracování výjimek, ale umožňuje definovat vlastní syntaxe jednotlivé jazyky.</span><span class="sxs-lookup"><span data-stu-id="339c8-117">Does not require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="339c8-118">Výjimky může být vyvolána napříč proces a i počítač hranice.</span><span class="sxs-lookup"><span data-stu-id="339c8-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="339c8-119">Zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.</span><span class="sxs-lookup"><span data-stu-id="339c8-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="339c8-120">Výjimky nabízejí výhod oproti jiným metodám oznámení o chybě, jako je například návratové kódy.</span><span class="sxs-lookup"><span data-stu-id="339c8-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="339c8-121">Selhání nedojde vzhledem k tomu, že pokud je vyvolána výjimka, a nemusíte je zpracovávat, modul runtime ukončí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="339c8-121">Failures do not go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="339c8-122">Neplatné hodnoty nepokračujte rozšíří v rámci systému v důsledku kód, který se nepodaří vyhledat návratový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="339c8-122">Invalid values do not continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span> 

## <a name="common-exceptions"></a><span data-ttu-id="339c8-123">Běžné výjimky</span><span class="sxs-lookup"><span data-stu-id="339c8-123">Common Exceptions</span></span>

<span data-ttu-id="339c8-124">Následující tabulka uvádí některé běžné výjimky s příklady, co může způsobit.</span><span class="sxs-lookup"><span data-stu-id="339c8-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="339c8-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="339c8-125">Exception type</span></span> | <span data-ttu-id="339c8-126">Základní typ</span><span class="sxs-lookup"><span data-stu-id="339c8-126">Base type</span></span> | <span data-ttu-id="339c8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="339c8-127">Description</span></span> | <span data-ttu-id="339c8-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="339c8-128">Example</span></span> |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | <span data-ttu-id="339c8-129">Základní třída pro všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="339c8-129">Base class for all exceptions.</span></span> | <span data-ttu-id="339c8-130">Žádný (použijte třídu odvozenou této výjimky).</span><span class="sxs-lookup"><span data-stu-id="339c8-130">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="339c8-131">Vyvolána modulem runtime pouze v případě, že pole je indexovaný nesprávně.</span><span class="sxs-lookup"><span data-stu-id="339c8-131">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="339c8-132">Indexování pole mimo platný rozsah:`arr[arr.Length+1]`</span><span class="sxs-lookup"><span data-stu-id="339c8-132">Indexing an array outside its valid range: `arr[arr.Length+1]`</span></span> |
| <xref:System.NullReferenceException> | <xref:System.Exception> | <span data-ttu-id="339c8-133">Vyvolána modulem runtime pouze v případě, že se odkazuje objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="339c8-133">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | <span data-ttu-id="339c8-134">Vyvolána metodami, když je v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="339c8-134">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="339c8-135">Volání metody `Enumerator.GetNext()` po odebrání položky ze zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="339c8-135">Calling `Enumerator.GetNext()` after removing an Item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <xref:System.Exception> | <span data-ttu-id="339c8-136">Základní třída pro všechny výjimky argumentu.</span><span class="sxs-lookup"><span data-stu-id="339c8-136">Base class for all argument exceptions.</span></span> | <span data-ttu-id="339c8-137">Žádný (použijte třídu odvozenou této výjimky).</span><span class="sxs-lookup"><span data-stu-id="339c8-137">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | <span data-ttu-id="339c8-138">Vyvolané metody, které neumožňují argumentu mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="339c8-138">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="339c8-139">Vyvolané metody, které ověřte, zda jsou argumenty v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="339c8-139">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="339c8-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="339c8-140">See Also</span></span>

* [<span data-ttu-id="339c8-141">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="339c8-141">Exception Class and Properties</span></span>](exception-class-and-properties.md)
* [<span data-ttu-id="339c8-142">Postupy: zachycení výjimky pomocí bloku Try-Catch</span><span class="sxs-lookup"><span data-stu-id="339c8-142">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [<span data-ttu-id="339c8-143">Postupy: používání specifických výjimek v bloku Catch</span><span class="sxs-lookup"><span data-stu-id="339c8-143">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
* [<span data-ttu-id="339c8-144">Postupy: explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="339c8-144">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
* [<span data-ttu-id="339c8-145">Postupy: vytváření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="339c8-145">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
* [<span data-ttu-id="339c8-146">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="339c8-146">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
* [<span data-ttu-id="339c8-147">Postupy: používání bloků Finally</span><span class="sxs-lookup"><span data-stu-id="339c8-147">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
* [<span data-ttu-id="339c8-148">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="339c8-148">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
* [<span data-ttu-id="339c8-149">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="339c8-149">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)

<span data-ttu-id="339c8-150">Další informace o fungování výjimek v rozhraní .NET najdete v tématu [každých Dev co potřebujete vědět o výjimky v modulu Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="339c8-150">To learn more about how exceptions work in .NET, see [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
