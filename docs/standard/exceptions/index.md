---
title: Zpracování a vyvolávání výjimek v rozhraní .NET
description: Naučte se zpracovávat a vyvolávat výjimky v rozhraní .NET. Výjimky jsou způsob, jakým operace rozhraní .NET indikují selhání aplikacím.
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
ms.openlocfilehash: 89d88e3128917125d1a09466ed4e230604d6978c
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662768"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="407c2-104">Zpracování a vyvolávání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="407c2-104">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="407c2-105">Aplikace musí být schopné zpracovávat chyby, ke kterým dochází během provádění konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="407c2-105">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="407c2-106">.NET poskytuje model pro oznamování chyb aplikacím jednotným způsobem: operace .NET indikují selhání vyvoláním výjimek.</span><span class="sxs-lookup"><span data-stu-id="407c2-106">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="407c2-107">Výjimky</span><span class="sxs-lookup"><span data-stu-id="407c2-107">Exceptions</span></span>

<span data-ttu-id="407c2-108">Výjimka je jakýkoli chybový stav nebo neočekávané chování, které se zjistilo spuštěným programem.</span><span class="sxs-lookup"><span data-stu-id="407c2-108">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="407c2-109">Výjimky mohou být vyvolány z důvodu chyby ve vašem kódu nebo v kódu, který zavoláte (například sdílená knihovna), nedostupných prostředků operačního systému, neočekávaných podmínek, které modul runtime narazí (například kódu, který nelze ověřit) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="407c2-109">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="407c2-110">Vaše aplikace se může zotavit z některých těchto podmínek, ale ne od ostatních.</span><span class="sxs-lookup"><span data-stu-id="407c2-110">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="407c2-111">I když můžete zotavit z většiny výjimek aplikace, nemůžete obnovit z většiny běhových výjimek.</span><span class="sxs-lookup"><span data-stu-id="407c2-111">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="407c2-112">V rozhraní .NET je výjimka objektem, který dědí z <xref:System.Exception?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="407c2-112">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="407c2-113">Výjimka je vyvolána z oblasti kódu, kde došlo k problému.</span><span class="sxs-lookup"><span data-stu-id="407c2-113">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="407c2-114">Výjimka předává zásobníku, dokud ji aplikace nezpracuje nebo ukončí program.</span><span class="sxs-lookup"><span data-stu-id="407c2-114">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="407c2-115">Výjimky vs. tradiční metody zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="407c2-115">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="407c2-116">Tradičně se model zpracování chyb jazyka spoléhal buď na jedinečný způsob zjišťování chyb a hledání obslužných rutin pro tyto účely, nebo na mechanismu zpracování chyb poskytovaný operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="407c2-116">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="407c2-117">Způsob, jakým rozhraní .NET implementuje zpracování výjimek, poskytuje následující výhody:</span><span class="sxs-lookup"><span data-stu-id="407c2-117">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="407c2-118">Vyvolání a zpracování výjimky funguje stejně pro programovací jazyky .NET.</span><span class="sxs-lookup"><span data-stu-id="407c2-118">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="407c2-119">Nevyžaduje žádnou konkrétní jazykovou syntaxi pro zpracování výjimek, ale umožňuje každému jazyku definovat vlastní syntaxi.</span><span class="sxs-lookup"><span data-stu-id="407c2-119">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="407c2-120">Výjimky mohou být vyvolány napříč procesem a dokonce i na hranicích počítačů.</span><span class="sxs-lookup"><span data-stu-id="407c2-120">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="407c2-121">Kód pro zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.</span><span class="sxs-lookup"><span data-stu-id="407c2-121">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="407c2-122">Výjimky nabízí výhody proti jiným způsobům chybového oznámení, jako jsou například návratové kódy.</span><span class="sxs-lookup"><span data-stu-id="407c2-122">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="407c2-123">Selhání nejdou nepatrné, protože pokud je vyvolána výjimka a nezpracováváte ji, modul runtime ukončí vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="407c2-123">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="407c2-124">Neplatné hodnoty nejsou dále šířeny v systému jako výsledek kódu, který nedokáže vyhledat návratový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="407c2-124">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="407c2-125">Běžné výjimky</span><span class="sxs-lookup"><span data-stu-id="407c2-125">Common exceptions</span></span>

<span data-ttu-id="407c2-126">V následující tabulce jsou uvedeny některé běžné výjimky s příklady toho, co můžou způsobit.</span><span class="sxs-lookup"><span data-stu-id="407c2-126">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="407c2-127">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="407c2-127">Exception type</span></span> | <span data-ttu-id="407c2-128">Popis</span><span class="sxs-lookup"><span data-stu-id="407c2-128">Description</span></span> | <span data-ttu-id="407c2-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="407c2-129">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="407c2-130">Základní třída pro všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="407c2-130">Base class for all exceptions.</span></span> | <span data-ttu-id="407c2-131">Žádný (použijte odvozenou třídu této výjimky).</span><span class="sxs-lookup"><span data-stu-id="407c2-131">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="407c2-132">Vyvolána modulem runtime pouze v případě, že je nesprávně indexováno pole</span><span class="sxs-lookup"><span data-stu-id="407c2-132">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="407c2-133">Indexování pole mimo platný rozsah:</span><span class="sxs-lookup"><span data-stu-id="407c2-133">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="407c2-134">Vyvolána modulem runtime pouze v případě, že je odkazováno na objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="407c2-134">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="407c2-135">Vyvoláno metodami, pokud je v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="407c2-135">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="407c2-136">Volání `Enumerator.MoveNext()` po odebrání položky z podkladové kolekce.</span><span class="sxs-lookup"><span data-stu-id="407c2-136">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="407c2-137">Základní třída pro všechny výjimky argumentů</span><span class="sxs-lookup"><span data-stu-id="407c2-137">Base class for all argument exceptions.</span></span> | <span data-ttu-id="407c2-138">Žádný (použijte odvozenou třídu této výjimky).</span><span class="sxs-lookup"><span data-stu-id="407c2-138">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="407c2-139">Vyvoláno metodami, které neumožňují, aby argument byl null.</span><span class="sxs-lookup"><span data-stu-id="407c2-139">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="407c2-140">Vyvoláno metodami, které ověřují, zda jsou argumenty v daném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="407c2-140">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="407c2-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="407c2-141">See also</span></span>

- [<span data-ttu-id="407c2-142">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="407c2-142">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="407c2-143">Postupy: Používání bloku Try/Catch k zachycování výjimek</span><span class="sxs-lookup"><span data-stu-id="407c2-143">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="407c2-144">Postupy: Používání specifických výjimek v bloku Catch</span><span class="sxs-lookup"><span data-stu-id="407c2-144">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="407c2-145">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="407c2-145">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="407c2-146">Postupy: Vytváření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="407c2-146">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="407c2-147">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="407c2-147">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="407c2-148">Postupy: Používání bloků Finally</span><span class="sxs-lookup"><span data-stu-id="407c2-148">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="407c2-149">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="407c2-149">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="407c2-150">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="407c2-150">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="407c2-151">Co každá z vývoje potřebuje znát o výjimkách v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="407c2-151">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
