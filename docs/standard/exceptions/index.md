---
title: Zpracování a vyvolání výjimek v rozhraní .NET
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
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741352"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="936d8-102">Zpracování a vyvolání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="936d8-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="936d8-103">Aplikace musí být schopné zpracovávat chyby, ke kterým dochází během provádění konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="936d8-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="936d8-104">.NET poskytuje model pro oznamování chyb aplikacím jednotným způsobem: operace .NET indikují selhání vyvoláním výjimek.</span><span class="sxs-lookup"><span data-stu-id="936d8-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="936d8-105">Výjimky</span><span class="sxs-lookup"><span data-stu-id="936d8-105">Exceptions</span></span>

<span data-ttu-id="936d8-106">Výjimka je jakýkoli chybový stav nebo neočekávané chování, které se zjistilo spuštěným programem.</span><span class="sxs-lookup"><span data-stu-id="936d8-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="936d8-107">Výjimky mohou být vyvolány z důvodu chyby ve vašem kódu nebo v kódu, který zavoláte (například sdílená knihovna), nedostupných prostředků operačního systému, neočekávaných podmínek, které modul runtime narazí (například kódu, který nelze ověřit) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="936d8-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="936d8-108">Vaše aplikace se může zotavit z některých těchto podmínek, ale ne od ostatních.</span><span class="sxs-lookup"><span data-stu-id="936d8-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="936d8-109">I když můžete zotavit z většiny výjimek aplikace, nemůžete obnovit z většiny běhových výjimek.</span><span class="sxs-lookup"><span data-stu-id="936d8-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="936d8-110">V rozhraní .NET je výjimka objektem, který dědí z třídy <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="936d8-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="936d8-111">Výjimka je vyvolána z oblasti kódu, kde došlo k problému.</span><span class="sxs-lookup"><span data-stu-id="936d8-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="936d8-112">Výjimka předává zásobníku, dokud ji aplikace nezpracuje nebo ukončí program.</span><span class="sxs-lookup"><span data-stu-id="936d8-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="936d8-113">Výjimky vs. tradiční metody zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="936d8-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="936d8-114">Tradičně se model zpracování chyb jazyka spoléhal buď na jedinečný způsob zjišťování chyb a hledání obslužných rutin pro tyto účely, nebo na mechanismu zpracování chyb poskytovaný operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="936d8-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="936d8-115">Způsob, jakým rozhraní .NET implementuje zpracování výjimek, poskytuje následující výhody:</span><span class="sxs-lookup"><span data-stu-id="936d8-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="936d8-116">Vyvolání a zpracování výjimky funguje stejně pro programovací jazyky .NET.</span><span class="sxs-lookup"><span data-stu-id="936d8-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="936d8-117">Nevyžaduje žádnou konkrétní jazykovou syntaxi pro zpracování výjimek, ale umožňuje každému jazyku definovat vlastní syntaxi.</span><span class="sxs-lookup"><span data-stu-id="936d8-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="936d8-118">Výjimky mohou být vyvolány napříč procesem a dokonce i na hranicích počítačů.</span><span class="sxs-lookup"><span data-stu-id="936d8-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="936d8-119">Kód pro zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.</span><span class="sxs-lookup"><span data-stu-id="936d8-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="936d8-120">Výjimky nabízí výhody proti jiným způsobům chybového oznámení, jako jsou například návratové kódy.</span><span class="sxs-lookup"><span data-stu-id="936d8-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="936d8-121">Selhání nejdou nepatrné, protože pokud je vyvolána výjimka a nezpracováváte ji, modul runtime ukončí vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="936d8-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="936d8-122">Neplatné hodnoty nejsou dále šířeny v systému jako výsledek kódu, který nedokáže vyhledat návratový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="936d8-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="936d8-123">Běžné výjimky</span><span class="sxs-lookup"><span data-stu-id="936d8-123">Common exceptions</span></span>

<span data-ttu-id="936d8-124">V následující tabulce jsou uvedeny některé běžné výjimky s příklady toho, co můžou způsobit.</span><span class="sxs-lookup"><span data-stu-id="936d8-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="936d8-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="936d8-125">Exception type</span></span> | <span data-ttu-id="936d8-126">Popis</span><span class="sxs-lookup"><span data-stu-id="936d8-126">Description</span></span> | <span data-ttu-id="936d8-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="936d8-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="936d8-128">Základní třída pro všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="936d8-128">Base class for all exceptions.</span></span> | <span data-ttu-id="936d8-129">Žádný (použijte odvozenou třídu této výjimky).</span><span class="sxs-lookup"><span data-stu-id="936d8-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="936d8-130">Vyvolána modulem runtime pouze v případě, že je nesprávně indexováno pole</span><span class="sxs-lookup"><span data-stu-id="936d8-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="936d8-131">Indexování pole mimo platný rozsah:</span><span class="sxs-lookup"><span data-stu-id="936d8-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="936d8-132">Vyvolána modulem runtime pouze v případě, že je odkazováno na objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="936d8-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="936d8-133">Vyvoláno metodami, pokud je v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="936d8-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="936d8-134">Volání `Enumerator.MoveNext()` po odebrání položky z podkladové kolekce.</span><span class="sxs-lookup"><span data-stu-id="936d8-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="936d8-135">Základní třída pro všechny výjimky argumentů</span><span class="sxs-lookup"><span data-stu-id="936d8-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="936d8-136">Žádný (použijte odvozenou třídu této výjimky).</span><span class="sxs-lookup"><span data-stu-id="936d8-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="936d8-137">Vyvoláno metodami, které neumožňují, aby argument byl null.</span><span class="sxs-lookup"><span data-stu-id="936d8-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="936d8-138">Vyvoláno metodami, které ověřují, zda jsou argumenty v daném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="936d8-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="936d8-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="936d8-139">See also</span></span>

- [<span data-ttu-id="936d8-140">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="936d8-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="936d8-141">Postupy: Používání bloku Try/Catch k zachycování výjimek</span><span class="sxs-lookup"><span data-stu-id="936d8-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="936d8-142">Postupy: Používání specifických výjimek v bloku Catch</span><span class="sxs-lookup"><span data-stu-id="936d8-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="936d8-143">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="936d8-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="936d8-144">Postupy: Vytváření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="936d8-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="936d8-145">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="936d8-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="936d8-146">Postupy: Používání bloků Finally</span><span class="sxs-lookup"><span data-stu-id="936d8-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="936d8-147">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="936d8-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="936d8-148">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="936d8-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="936d8-149">Co každá z vývoje potřebuje znát o výjimkách v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="936d8-149">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
