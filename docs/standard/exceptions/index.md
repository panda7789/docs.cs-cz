---
title: Zpracování a generování výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b71ffd9bfcfcb048f148ac1a3a418c03b9834ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575450"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="809e7-102">Zpracování a generování výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="809e7-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="809e7-103">Aplikace musí být schopen zpracovávat chyby, ke kterým došlo během provádění konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="809e7-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="809e7-104">Rozhraní .NET poskytuje model pro oznamování chyb aplikace jednotného: operace .NET označují selhání vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="809e7-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="809e7-105">Výjimky</span><span class="sxs-lookup"><span data-stu-id="809e7-105">Exceptions</span></span>

<span data-ttu-id="809e7-106">Výjimkou je libovolná chyba nebo neočekávanému chování, které se vyskytne provádění programu.</span><span class="sxs-lookup"><span data-stu-id="809e7-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="809e7-107">Výjimky může být vyvolána z důvodu selhání ve vašem kódu nebo kód, který volání (například sdílené knihovny), prostředky operačního systému není k dispozici, neočekávané podmínky, které modul runtime, zaznamená (například kód, který nemůže být ověřen) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="809e7-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that cannot be verified), and so on.</span></span> <span data-ttu-id="809e7-108">Aplikace lze obnovit z některé z těchto podmínek, ale ne od ostatních.</span><span class="sxs-lookup"><span data-stu-id="809e7-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="809e7-109">I když můžete obnovit z většina výjimky aplikací, nelze obnovit z většina výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="809e7-109">Although you can recover from most application exceptions, you cannot recover from most runtime exceptions.</span></span>

<span data-ttu-id="809e7-110">V rozhraní .NET, je objekt, který dědí z výjimka <xref:System.Exception?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="809e7-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="809e7-111">Z oblasti kódu, kde došlo k potížím, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="809e7-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="809e7-112">Výjimka je přidána na zásobník dokud ji zpracovává aplikaci nebo program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="809e7-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="809e7-113">Výjimky oproti tradiční metody zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="809e7-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="809e7-114">Obvyklým model zpracování chyb jazyk spoléhali na jazyka jedinečný způsob zjišťování chyb a vyhledání obslužné rutiny pro ně nebo na mechanizmus zpracování chyb v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="809e7-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="809e7-115">Způsob zpracování výjimek implementuje rozhraní .NET poskytuje následující výhody:</span><span class="sxs-lookup"><span data-stu-id="809e7-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="809e7-116">Výjimka vyvolání a zpracování funguje stejně programovacích jazyků .NET.</span><span class="sxs-lookup"><span data-stu-id="809e7-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="809e7-117">Nevyžaduje žádné konkrétní jazykové syntaxe pro zpracování výjimek, ale umožňuje definovat vlastní syntaxe jednotlivé jazyky.</span><span class="sxs-lookup"><span data-stu-id="809e7-117">Does not require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="809e7-118">Výjimky může být vyvolána napříč proces a i počítač hranice.</span><span class="sxs-lookup"><span data-stu-id="809e7-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="809e7-119">Zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.</span><span class="sxs-lookup"><span data-stu-id="809e7-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="809e7-120">Výjimky nabízejí výhod oproti jiným metodám oznámení o chybě, jako je například návratové kódy.</span><span class="sxs-lookup"><span data-stu-id="809e7-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="809e7-121">Selhání nedojde vzhledem k tomu, že pokud je vyvolána výjimka, a nemusíte je zpracovávat, modul runtime ukončí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="809e7-121">Failures do not go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="809e7-122">Neplatné hodnoty nepokračujte rozšíří v rámci systému v důsledku kód, který se nepodaří vyhledat návratový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="809e7-122">Invalid values do not continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span> 

## <a name="common-exceptions"></a><span data-ttu-id="809e7-123">Běžné výjimky</span><span class="sxs-lookup"><span data-stu-id="809e7-123">Common Exceptions</span></span>

<span data-ttu-id="809e7-124">Následující tabulka uvádí některé běžné výjimky s příklady, co může způsobit.</span><span class="sxs-lookup"><span data-stu-id="809e7-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="809e7-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="809e7-125">Exception type</span></span> | <span data-ttu-id="809e7-126">Základní typ</span><span class="sxs-lookup"><span data-stu-id="809e7-126">Base type</span></span> | <span data-ttu-id="809e7-127">Popis</span><span class="sxs-lookup"><span data-stu-id="809e7-127">Description</span></span> | <span data-ttu-id="809e7-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="809e7-128">Example</span></span> |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | <span data-ttu-id="809e7-129">Základní třída pro všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="809e7-129">Base class for all exceptions.</span></span> | <span data-ttu-id="809e7-130">Žádný (použijte třídu odvozenou této výjimky).</span><span class="sxs-lookup"><span data-stu-id="809e7-130">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="809e7-131">Vyvolána modulem runtime pouze v případě, že pole je indexovaný nesprávně.</span><span class="sxs-lookup"><span data-stu-id="809e7-131">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="809e7-132">Indexování pole mimo platný rozsah: `arr[arr.Length+1]`</span><span class="sxs-lookup"><span data-stu-id="809e7-132">Indexing an array outside its valid range: `arr[arr.Length+1]`</span></span> |
| <xref:System.NullReferenceException> | <xref:System.Exception> | <span data-ttu-id="809e7-133">Vyvolána modulem runtime pouze v případě, že se odkazuje objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="809e7-133">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | <span data-ttu-id="809e7-134">Vyvolána metodami, když je v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="809e7-134">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="809e7-135">Volání metody `Enumerator.GetNext()` po odebrání položky ze zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="809e7-135">Calling `Enumerator.GetNext()` after removing an Item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <xref:System.Exception> | <span data-ttu-id="809e7-136">Základní třída pro všechny výjimky argumentu.</span><span class="sxs-lookup"><span data-stu-id="809e7-136">Base class for all argument exceptions.</span></span> | <span data-ttu-id="809e7-137">Žádný (použijte třídu odvozenou této výjimky).</span><span class="sxs-lookup"><span data-stu-id="809e7-137">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | <span data-ttu-id="809e7-138">Vyvolané metody, které neumožňují argumentu mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="809e7-138">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="809e7-139">Vyvolané metody, které ověřte, zda jsou argumenty v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="809e7-139">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="809e7-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="809e7-140">See Also</span></span>

* [<span data-ttu-id="809e7-141">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="809e7-141">Exception Class and Properties</span></span>](exception-class-and-properties.md)
* [<span data-ttu-id="809e7-142">Postupy: Používání bloku Try/Catch k zachycování výjimek</span><span class="sxs-lookup"><span data-stu-id="809e7-142">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [<span data-ttu-id="809e7-143">Postupy: Používání specifických výjimek v bloku Catch</span><span class="sxs-lookup"><span data-stu-id="809e7-143">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
* [<span data-ttu-id="809e7-144">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="809e7-144">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
* [<span data-ttu-id="809e7-145">Postupy: Vytváření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="809e7-145">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
* [<span data-ttu-id="809e7-146">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="809e7-146">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
* [<span data-ttu-id="809e7-147">Postupy: Používání bloků Finally</span><span class="sxs-lookup"><span data-stu-id="809e7-147">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
* [<span data-ttu-id="809e7-148">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="809e7-148">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
* [<span data-ttu-id="809e7-149">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="809e7-149">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)

<span data-ttu-id="809e7-150">Další informace o fungování výjimek v rozhraní .NET najdete v tématu [každých Dev co potřebujete vědět o výjimky v modulu Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="809e7-150">To learn more about how exceptions work in .NET, see [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
