---
title: Vyvolání výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: KrzysztofCwalina
ms.openlocfilehash: 74eee418a3c87b335cdf96557c4e17b95aff7b58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562879"
---
# <a name="exception-throwing"></a><span data-ttu-id="937f2-102">Vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="937f2-102">Exception Throwing</span></span>
<span data-ttu-id="937f2-103">Vyvolání výjimek pokynů popsaných v této části vyžadují správné definice význam selhání spuštění.</span><span class="sxs-lookup"><span data-stu-id="937f2-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="937f2-104">Chyba při spuštění vyvolá se při každém člena nelze provést, který byl navržený tak, aby se (co člen již název napovídá).</span><span class="sxs-lookup"><span data-stu-id="937f2-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="937f2-105">Například pokud `OpenFile` metoda popisovač otevřený soubor nemůže vracet volajícímu, může být považován Chyba při spuštění.</span><span class="sxs-lookup"><span data-stu-id="937f2-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="937f2-106">Většina vývojářů se staly umíte pracovat se použití výjimek pro využití chyby jako např. dělení nulou či odkazy s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="937f2-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="937f2-107">V rámci výjimky se používají pro všechny chybové stavy, včetně zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="937f2-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="937f2-108">**X DO NOT** návratové kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="937f2-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="937f2-109">Výjimky jsou primární prostředky zpráv o chybách v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="937f2-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="937f2-110">**✓ DO** sestavy selhání spuštění ve vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="937f2-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="937f2-111">**✓ CONSIDER** proces se ukončuje voláním `System.Environment.FailFast` (funkce rozhraní .NET Framework 2.0) namísto došlo k výjimce, pokud váš kód zjistí situaci, kde nezabezpečený pro další zpracování.</span><span class="sxs-lookup"><span data-stu-id="937f2-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="937f2-112">**X DO NOT** používat výjimky pro normálního toku řízení, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="937f2-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="937f2-113">S výjimkou chyby systému a operace s potenciální konflikty časování by měl framework návrháři navrhovat rozhraní API, tak uživatelům můžete napsat kód, který nevrací výjimky.</span><span class="sxs-lookup"><span data-stu-id="937f2-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="937f2-114">Můžete například poskytnout způsob, jak zkontrolovat předpoklady před voláním člen tak uživatelům můžete napsat kód, který nevrací výjimky.</span><span class="sxs-lookup"><span data-stu-id="937f2-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="937f2-115">Člen sloužící ke kontrole předběžné podmínky jiného člena se často označuje jako tester a člena, který ve skutečnosti funguje se volá doer.</span><span class="sxs-lookup"><span data-stu-id="937f2-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="937f2-116">Existují případy, kdy vzor Tester Doer může mít nároky na výkon nepřijatelný.</span><span class="sxs-lookup"><span data-stu-id="937f2-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="937f2-117">V takových případech takzvané vzor analýzy zkuste by měl být (viz [výjimek a výkonu](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Další informace).</span><span class="sxs-lookup"><span data-stu-id="937f2-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="937f2-118">**✓ CONSIDER** vliv na výkon u vyvolávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="937f2-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="937f2-119">Sazby za throw nad 100 za sekundu se pravděpodobně výrazně ovlivnit výkon většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="937f2-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="937f2-120">**✓ DO** dokumentu všechny výjimky vyvolané veřejně s členy z důvodu narušení člena smlouvy (místo selhání systému) a je považovat za část vaše smlouvy.</span><span class="sxs-lookup"><span data-stu-id="937f2-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="937f2-121">Výjimky, které jsou součástí smlouvy nesmí změnit z jedné verze na další (tj, by neměly měnit typ výjimky a neměl by se přidávat nové výjimky).</span><span class="sxs-lookup"><span data-stu-id="937f2-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="937f2-122">**X DO NOT** veřejné členy, které můžete buď throw nebo není na některé možnost základě.</span><span class="sxs-lookup"><span data-stu-id="937f2-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="937f2-123">**X DO NOT** mají veřejné členy, které vracejí výjimky jako návratová hodnota nebo `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="937f2-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="937f2-124">Vrácení výjimky z veřejných rozhraní API namísto vyvolání jejich poráží mnohé z výhod hlášení chyb na základě výjimky.</span><span class="sxs-lookup"><span data-stu-id="937f2-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="937f2-125">**✓ CONSIDER** pomocí metody tvůrce výjimky.</span><span class="sxs-lookup"><span data-stu-id="937f2-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="937f2-126">Je běžné vyvolat stejnou výjimku z různých míst.</span><span class="sxs-lookup"><span data-stu-id="937f2-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="937f2-127">Aby se zabránilo jejímu narůstání kódu, použijte pomocné metody vytvoření výjimky a inicializaci jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="937f2-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="937f2-128">Navíc nejsou členy, které vyvolají výjimky získávání vložená.</span><span class="sxs-lookup"><span data-stu-id="937f2-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="937f2-129">Přesunutí příkaz throw do Tvůrce může umožnit člen se nedá vložit.</span><span class="sxs-lookup"><span data-stu-id="937f2-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="937f2-130">**X DO NOT** vyvolat výjimky z bloky filtru výjimek.</span><span class="sxs-lookup"><span data-stu-id="937f2-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="937f2-131">Když filtru výjimky vyvolá výjimku, výjimka se zachycuje prostřednictvím modulu CLR a filtr vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="937f2-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="937f2-132">Toto chování je nerozeznatelná od tohoto filtru, provádění a vrácení hodnoty false explicitně a proto je velmi obtížné ladit.</span><span class="sxs-lookup"><span data-stu-id="937f2-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="937f2-133">**X AVOID** explicitně vyvolání výjimky z finally – bloky.</span><span class="sxs-lookup"><span data-stu-id="937f2-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="937f2-134">Implicitně vyvolané výjimky vyplývající z volání metod, které vyvolají jsou přijatelné.</span><span class="sxs-lookup"><span data-stu-id="937f2-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="937f2-135">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="937f2-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="937f2-136">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="937f2-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937f2-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="937f2-137">See also</span></span>

- [<span data-ttu-id="937f2-138">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="937f2-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="937f2-139">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="937f2-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
