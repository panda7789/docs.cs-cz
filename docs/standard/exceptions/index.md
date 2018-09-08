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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263e6394a57ec3e7ef00eb79671d9b8ac47e724f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177232"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="5fcfd-102">Zpracování a vyvolání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="5fcfd-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="5fcfd-103">Aplikace musí být schopna zpracovávat chyby, ke kterým dochází při provádění konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="5fcfd-104">.NET poskytuje model pro oznamování chyb aplikace jednotným způsobem: operace .NET označení selhání vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="5fcfd-105">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5fcfd-105">Exceptions</span></span>

<span data-ttu-id="5fcfd-106">Výjimka je libovolný chybový stav nebo neočekávané chování, na kterou narazí prováděnému programu.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="5fcfd-107">Výjimky mohou být vyvolány z důvodu chyby v kódu nebo v kódu, který voláte (jako jsou sdílené knihovny), prostředky operačního systému není k dispozici, neočekávané podmínky, které modul runtime, zaznamená (například kód, který nelze ověřit) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="5fcfd-108">Aplikaci můžete obnovit z některé z těchto podmínek, ale ne od ostatních.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="5fcfd-109">I když můžete obnovit z většina výjimek aplikace, nebude možné obnovit z většiny výjimky modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="5fcfd-110">V .NET, je výjimka, která dědí z objektu <xref:System.Exception?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5fcfd-111">Výjimka je vyvolána z oblasti kódu, kde došlo k problému.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="5fcfd-112">Výjimka je předána na vrcholu zásobníku, dokud aplikace zvládne nebo program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="5fcfd-113">Výjimky vs. tradiční metody zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="5fcfd-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="5fcfd-114">Tradičně spoléhal jazykový model zpracování chyb jazyka jedinečný způsob zjišťování chyb a vyhledání obslužné rutiny pro ně nebo mechanismus zpracování chyb v operačním systému k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="5fcfd-115">Způsob zpracování výjimek implementuje .NET nabízí následující výhody:</span><span class="sxs-lookup"><span data-stu-id="5fcfd-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="5fcfd-116">Vyvolávání a zpracování výjimek funguje stejně v případě programovacích jazycích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="5fcfd-117">Nevyžaduje žádnou konkrétní jazykovou syntaxi pro zpracování výjimek, ale umožňuje definovat svou vlastní syntaxi jednotlivé jazyky.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="5fcfd-118">Výjimky mohou být vyvolány v procesu a dokonce i počítač hranice.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="5fcfd-119">Kód zpracování výjimek lze přidat do aplikace pro zvýšení spolehlivosti programu.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="5fcfd-120">Výjimky nabízí výhody oproti jiným metodám oznamování chyb, jako je například návratové kódy.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="5fcfd-121">Selhání není povšimnutí, protože pokud dojde k výjimce a nechcete ji zpracovat, modul runtime ukončí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="5fcfd-122">Neplatné hodnoty není nadále šířit prostřednictvím systému jako výsledek kódu, které se nedaří vyhledat návratový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="5fcfd-123">Běžné výjimky</span><span class="sxs-lookup"><span data-stu-id="5fcfd-123">Common exceptions</span></span>

<span data-ttu-id="5fcfd-124">Následující tabulka uvádí některé běžné výjimky s příklady, co může způsobit.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="5fcfd-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="5fcfd-125">Exception type</span></span> | <span data-ttu-id="5fcfd-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5fcfd-126">Description</span></span> | <span data-ttu-id="5fcfd-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fcfd-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="5fcfd-128">Základní třída pro všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-128">Base class for all exceptions.</span></span> | <span data-ttu-id="5fcfd-129">Žádný (použijte odvozené třídy této výjimky).</span><span class="sxs-lookup"><span data-stu-id="5fcfd-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="5fcfd-130">Vyvolané modulem runtime jenom v případě, že pole jsou indexována, nesprávně.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="5fcfd-131">Došlo k indexování pole mimo platný rozsah:</span><span class="sxs-lookup"><span data-stu-id="5fcfd-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="5fcfd-132">Vyvolané modulem runtime pouze v případě, že se odkazuje objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="5fcfd-133">Vyvolání metody v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="5fcfd-134">Volání `Enumerator.MoveNext()` po odebrání položky ze zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="5fcfd-135">Základní třída pro všechny výjimky argumentu.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="5fcfd-136">Žádný (použijte odvozené třídy této výjimky).</span><span class="sxs-lookup"><span data-stu-id="5fcfd-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="5fcfd-137">Vyvolání metody, které nepovolují argument mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="5fcfd-138">Vyvolání metody, které ověřují, že argumenty jsou v dané oblasti.</span><span class="sxs-lookup"><span data-stu-id="5fcfd-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="5fcfd-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fcfd-139">See also</span></span>

- [<span data-ttu-id="5fcfd-140">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="5fcfd-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)  
- [<span data-ttu-id="5fcfd-141">Postupy: Používání bloku Try/Catch k zachycování výjimek</span><span class="sxs-lookup"><span data-stu-id="5fcfd-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
- [<span data-ttu-id="5fcfd-142">Postupy: Používání specifických výjimek v bloku Catch</span><span class="sxs-lookup"><span data-stu-id="5fcfd-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)  
- [<span data-ttu-id="5fcfd-143">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="5fcfd-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)  
- [<span data-ttu-id="5fcfd-144">Postupy: Vytváření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="5fcfd-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)  
- [<span data-ttu-id="5fcfd-145">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="5fcfd-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)  
- [<span data-ttu-id="5fcfd-146">Postupy: Používání bloků Finally</span><span class="sxs-lookup"><span data-stu-id="5fcfd-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)  
- [<span data-ttu-id="5fcfd-147">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="5fcfd-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)  
- [<span data-ttu-id="5fcfd-148">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="5fcfd-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)  
- <span data-ttu-id="5fcfd-149">[Co každých vývoj je potřeba vědět o výjimky v modulu Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="5fcfd-149">[What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
