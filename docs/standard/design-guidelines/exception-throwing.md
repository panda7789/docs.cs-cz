---
title: "Vyvolání výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b1aa0eaccc26e1bd7cc6b78953dc0a782b2f952e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exception-throwing"></a><span data-ttu-id="4ccd9-102">Vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="4ccd9-102">Exception Throwing</span></span>
<span data-ttu-id="4ccd9-103">Pokyny pro vyvolávání výjimek popsaných v této části vyžadují dobrý definice význam selhání spuštění.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="4ccd9-104">Dojde k chybě provádění, vždy, když se člen nemůžete udělat, co byla navržená tak, aby se (co člena již název napovídá).</span><span class="sxs-lookup"><span data-stu-id="4ccd9-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="4ccd9-105">Například pokud `OpenFile` metoda nemůže vrátit popisovač otevřený soubor volajícímu, může být považovaná Chyba při spuštění.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="4ccd9-106">Většina vývojářů se tedy se použití výjimek pro využití chyby jako např. dělení nulou či odkazy s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="4ccd9-107">V rozhraní Framework výjimky se používají pro všechny chybové stavy, včetně chyby spuštění.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="4ccd9-108">**X nesmí** návratové kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="4ccd9-109">Výjimky jsou primární způsob zasílání zpráv o chybách v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="4ccd9-110">**PROVEĎTE ✓** sestavy selhání spuštění ve vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="4ccd9-111">**✓ ZVAŽTE** proces se ukončuje voláním `System.Environment.FailFast` (funkce rozhraní .NET Framework 2.0) namísto došlo k výjimce, pokud váš kód zjistí situaci, kde nezabezpečený pro další zpracování.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="4ccd9-112">**X nesmí** používat výjimky pro normálního toku řízení, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="4ccd9-113">S výjimkou chyby systému a operace s potenciální konflikty časování měli framework Designer navrhnout rozhraní API, uživatelé můžete napsat kód, který nevyvolá výjimku výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="4ccd9-114">Můžete například zadat způsob, jak zkontrolovat předběžné podmínky před voláním členem, takže uživatelé můžete napsat kód, který nevyvolá výjimku výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="4ccd9-115">Člen použita ke kontrole předběžné podmínky jiného člena se často označuje jako testování a člena, který skutečně funguje se nazývá doer.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="4ccd9-116">Pokud vzor Tester Doer může mít nepřijatelné zatížení existují případy.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="4ccd9-117">V takových případech vzoru takzvané zkuste analýzy považovat (viz [výjimky a výkonu](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Další informace).</span><span class="sxs-lookup"><span data-stu-id="4ccd9-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="4ccd9-118">**✓ ZVAŽTE** vliv na výkon u vyvolávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="4ccd9-119">Throw sazby vyšší než 100 za sekundu se pravděpodobně výrazně ovlivnit výkon většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="4ccd9-120">**PROVEĎTE ✓** dokumentu všechny výjimky vyvolané veřejně s členy z důvodu narušení člena smlouvy (místo selhání systému) a je považovat za část vaše smlouvy.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="4ccd9-121">Výjimky, které jsou součástí smlouvy nesmí změnit z jedné verze na další (tj, nesmí změnit typ výjimky a by neměly být přidávány nové výjimky).</span><span class="sxs-lookup"><span data-stu-id="4ccd9-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="4ccd9-122">**X nesmí** veřejné členy, které můžete buď throw nebo není na některé možnost základě.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="4ccd9-123">**X nesmí** mají veřejné členy, které vracejí výjimky jako návratová hodnota nebo `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="4ccd9-124">Vrácení výjimky z veřejné rozhraní API místo vyvolání je účinně chrání před řadu výhod zasílání zpráv o chybách na základě výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="4ccd9-125">**✓ ZVAŽTE** pomocí metody tvůrce výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="4ccd9-126">Je běžné vyvolat stejnou výjimku z různých místech.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="4ccd9-127">Předejdete tomu kódu použitím pomocné metody, které vytvořit výjimky a jejich vlastnosti inicializace.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="4ccd9-128">Také nejsou členy, kteří throw výjimky získávání vložená.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="4ccd9-129">Přesunutí příkaz throw do Tvůrce, mohou povolovat člen být vložená.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="4ccd9-130">**X nesmí** vyvolat výjimky z bloky filtru výjimek.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="4ccd9-131">Pokud filtr výjimek vyvolá výjimku, je výjimka zachycena CLR a filtr, vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="4ccd9-132">Toto chování je lišit od filtr provádění a vrácení hodnoty false explicitně a je proto velmi obtížné ladění.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="4ccd9-133">**X nepoužívejte** explicitně vyvolání výjimky z finally – bloky.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="4ccd9-134">Výsledkem volání metody, které vyvolají implicitně vyvolané výjimky jsou přijatelné.</span><span class="sxs-lookup"><span data-stu-id="4ccd9-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="4ccd9-135">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4ccd9-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4ccd9-136">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4ccd9-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ccd9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ccd9-137">See Also</span></span>  
 [<span data-ttu-id="4ccd9-138">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="4ccd9-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="4ccd9-139">Pokyny pro návrh pro výjimky</span><span class="sxs-lookup"><span data-stu-id="4ccd9-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
