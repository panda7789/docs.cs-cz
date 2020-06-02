---
title: Vyvolání výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 6bbc6e8fa11759afbd3a1fb2d785f476a6c178ad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289808"
---
# <a name="exception-throwing"></a><span data-ttu-id="1fdd4-102">Vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="1fdd4-102">Exception Throwing</span></span>
<span data-ttu-id="1fdd4-103">Výjimky – pokyny pro vyvolání výjimky popsané v této části vyžadují dobrou definici významu selhání spuštění.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="1fdd4-104">K selhání spuštění dojde pokaždé, když člen nemůže dělat, co byl navržený tak, aby to provedl (co název členu implikuje).</span><span class="sxs-lookup"><span data-stu-id="1fdd4-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="1fdd4-105">Například pokud `OpenFile` Metoda nemůže vrátit otevřený popisovač souboru volajícímu, bude považována za chybu spuštění.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="1fdd4-106">Většina vývojářů se seznámila s používáním výjimek pro chyby použití, jako je dělení nulou nebo odkazy s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="1fdd4-107">V rozhraní se výjimky používají pro všechny chybové stavy, včetně chyb spuštění.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="1fdd4-108">❌Nevracet chybové kódy.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="1fdd4-109">Výjimky jsou primárními prostředky pro hlášení chyb v rozhraních.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="1fdd4-110">✔️ provádění sestav při selhání při vyvolávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="1fdd4-111">✔️ Zvažte ukončení procesu voláním `System.Environment.FailFast` funkce (.NET Framework 2,0) namísto vyvolání výjimky, pokud váš kód narazí na situaci, kde je nebezpečný pro další spuštění.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="1fdd4-112">❌Nepoužívejte výjimky pro normální tok řízení, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="1fdd4-113">S výjimkou selhání systému a operací s potenciálními konflikty časování by měli návrháři architektury navrhovat rozhraní API, aby mohli uživatelé napsat kód, který nevyvolá výjimky.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="1fdd4-114">Například můžete zadat způsob, jak kontrolovat předběžné podmínky před voláním členu, aby mohli uživatelé napsat kód, který nevyvolá výjimky.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="1fdd4-115">Člen, který se používá ke kontrole předběžných podmínek jiného člena, se často označuje jako Tester a člen, který práci skutečně provede, se nazývá Doer.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="1fdd4-116">Existují případy, kdy test a Doer vzor může mít nepřijatelný výkon.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="1fdd4-117">V takových případech by se měl vzít v úvahu vzor typu try-Parse (viz [výjimky a výkon](exceptions-and-performance.md) pro další informace).</span><span class="sxs-lookup"><span data-stu-id="1fdd4-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="1fdd4-118">✔️ VZÍT v úvahu dopady na výkon při vyvolávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="1fdd4-119">Míry volání přesahující výše 100 za sekundu budou pravděpodobně výrazně ovlivňovat výkon většiny aplikací.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="1fdd4-120">✔️ zdokumentovat všechny výjimky vyvolané veřejně vyvolanými členy z důvodu porušení členské smlouvy (spíše než selhání systému) a zacházet s nimi jako součást vaší smlouvy.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="1fdd4-121">Výjimky, které jsou součástí kontraktu, by neměly být změněny z jedné verze na další (tj. typ výjimky by se neměly měnit a nové výjimky by neměly být přidány).</span><span class="sxs-lookup"><span data-stu-id="1fdd4-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="1fdd4-122">❌Nemají veřejné členy, které mohou na základě některé možnosti vyvolat nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="1fdd4-123">❌Nemají veřejné členy, kteří vracejí výjimky jako návratovou hodnotu nebo `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="1fdd4-124">Vrácení výjimek z veřejných rozhraní API namísto vyvolání přináší mnoho výhod zasílání zpráv o chybách na základě výjimek.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="1fdd4-125">✔️ Zvažte použití metod Tvůrce výjimek.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="1fdd4-126">Je běžné vyvolat stejnou výjimku z různých míst.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="1fdd4-127">Chcete-li se vyhnout dispozici determinističtější kódu, použijte pomocné metody, které vytvářejí výjimky a inicializujte jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="1fdd4-128">Také členy, kteří vyvolávají výjimky, nejsou vloženy.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="1fdd4-129">Přesunutí příkazu throw uvnitř tvůrce může umožňovat, aby byl člen vložen.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="1fdd4-130">❌Nevyvolávat výjimky z bloků filtru výjimky.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="1fdd4-131">Pokud filtr výjimek vyvolá výjimku, je výjimka zachycena modulem CLR a filtr vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="1fdd4-132">Toto chování je neodlišitelné od vykonání filtru a vrací hodnotu false explicitně a je proto velmi obtížné ho ladit.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="1fdd4-133">❌Vyhněte se explicitnímu vyvolávání výjimek z bloků finally.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="1fdd4-134">Implicitně vyvolané výjimky, které jsou výsledkem volání metod, které vyvolává vyvolání, jsou přijatelné.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="1fdd4-135">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="1fdd4-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1fdd4-136">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="1fdd4-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1fdd4-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fdd4-137">See also</span></span>

- [<span data-ttu-id="1fdd4-138">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="1fdd4-138">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1fdd4-139">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="1fdd4-139">Design Guidelines for Exceptions</span></span>](exceptions.md)
