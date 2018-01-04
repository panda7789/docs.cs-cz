---
title: "Výjimky a výkonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9a876a818086e0d54251f53a1e8f83cc74a574ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="5e33f-102">Výjimky a výkonu</span><span class="sxs-lookup"><span data-stu-id="5e33f-102">Exceptions and Performance</span></span>
<span data-ttu-id="5e33f-103">Jeden běžný problém související s výjimkami je, že pokud se výjimky použijí pro kód, který pravidelně selže, výkon implementace nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="5e33f-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="5e33f-104">Jde o platný problém.</span><span class="sxs-lookup"><span data-stu-id="5e33f-104">This is a valid concern.</span></span> <span data-ttu-id="5e33f-105">Pokud člen, vyvolá výjimku, může být jeho výkon pořadí podle velikosti pomalejší.</span><span class="sxs-lookup"><span data-stu-id="5e33f-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="5e33f-106">Je však možné, abyste dosáhli dobrého výkonu při zachování výhradně výjimka pokyny, které zakáže použití kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="5e33f-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="5e33f-107">Dva vzory popsaných v této části zjistíte, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="5e33f-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="5e33f-108">**X nesmí** z důvodu obavy, že výjimky může ovlivnit výkon negativně používat kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="5e33f-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="5e33f-109">Pokud chcete zvýšit výkon, je možné použít vzor Tester Doer nebo vzoru zkuste analýzy popsané v následujících dvou částech.</span><span class="sxs-lookup"><span data-stu-id="5e33f-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="5e33f-110">Vzor Tester Doer</span><span class="sxs-lookup"><span data-stu-id="5e33f-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="5e33f-111">V některých případech je možné zlepšit výkon člena vyvolávání výjimek porušením člena do dvou.</span><span class="sxs-lookup"><span data-stu-id="5e33f-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="5e33f-112">Podívejme se na <xref:System.Collections.Generic.ICollection%601.Add%2A> metodu <xref:System.Collections.Generic.ICollection%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e33f-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="5e33f-113">Metoda `Add` způsobí výjimku, pokud kolekce je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="5e33f-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="5e33f-114">Může se jednat o problém s výkonem ve scénářích, kde je očekávána volání metody, které k selhání často.</span><span class="sxs-lookup"><span data-stu-id="5e33f-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="5e33f-115">Jedním ze způsobů zmírnit problém je k ověření, zda kolekce lze zapisovat, než se pokusíte přidat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5e33f-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="5e33f-116">Člen používá k testování podmínku, která v našem příkladu je vlastnost `IsReadOnly`, se označuje jako zkušební zařízení.</span><span class="sxs-lookup"><span data-stu-id="5e33f-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="5e33f-117">Člen používá k provádění potenciálně aktivační operace, `Add` metoda v našem příkladu se označuje jako doer.</span><span class="sxs-lookup"><span data-stu-id="5e33f-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="5e33f-118">**✓ ZVAŽTE** Tester Doer vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.</span><span class="sxs-lookup"><span data-stu-id="5e33f-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="5e33f-119">Try analýzy vzor</span><span class="sxs-lookup"><span data-stu-id="5e33f-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="5e33f-120">Pro rozhraní API velmi náročné na výkon je třeba použít vzor ještě rychlejší než vzoru Tester Doer popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5e33f-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="5e33f-121">Vzor volání pro přizpůsobení název člena, aby dobře definované testovací případ součástí sémantiku člen.</span><span class="sxs-lookup"><span data-stu-id="5e33f-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="5e33f-122">Například <xref:System.DateTime> definuje <xref:System.DateTime.Parse%2A> metoda, která vyvolá výjimku, pokud analýza řetězce nezdaří.</span><span class="sxs-lookup"><span data-stu-id="5e33f-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="5e33f-123">Také definuje odpovídající <xref:System.DateTime.TryParse%2A> metoda, která se pokusí analyzovat, ale vrací hodnotu false Pokud analýza neúspěšná a vrátí výsledek úspěšné analýzy pomocí `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="5e33f-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="5e33f-124">Pokud používáte tento vzor, je důležité určit, zkuste funkce v striktní podmínky.</span><span class="sxs-lookup"><span data-stu-id="5e33f-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="5e33f-125">Pokud z nějakého důvodu než dobře definovaný zkuste selže člen, musí člen stále odpovídající výjimku vyvolat.</span><span class="sxs-lookup"><span data-stu-id="5e33f-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="5e33f-126">**✓ ZVAŽTE** zkuste analýzy vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.</span><span class="sxs-lookup"><span data-stu-id="5e33f-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="5e33f-127">**PROVEĎTE ✓** použijte předponu "Zkuste" a logickou hodnotu návratový typ pro metody implementace tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="5e33f-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="5e33f-128">**PROVEĎTE ✓** zadejte člena vyvolávání výjimek pro každého člena pomocí vzoru zkuste analýzy.</span><span class="sxs-lookup"><span data-stu-id="5e33f-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="5e33f-129">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="5e33f-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5e33f-130">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5e33f-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e33f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e33f-131">See Also</span></span>  
 [<span data-ttu-id="5e33f-132">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="5e33f-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="5e33f-133">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="5e33f-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
