---
title: Výjimky a výkon
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026429"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="8edf5-102">Výjimky a výkon</span><span class="sxs-lookup"><span data-stu-id="8edf5-102">Exceptions and Performance</span></span>
<span data-ttu-id="8edf5-103">Jeden společný problém související s výjimkami je, že pokud se výjimky použijí pro kód, který pravidelně selže, výkon implementace nepřijatelná.</span><span class="sxs-lookup"><span data-stu-id="8edf5-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="8edf5-104">Toto je platný žádný problém.</span><span class="sxs-lookup"><span data-stu-id="8edf5-104">This is a valid concern.</span></span> <span data-ttu-id="8edf5-105">Pokud člen vyvolá výjimku, jeho výkon a může být řádů pomalejší.</span><span class="sxs-lookup"><span data-stu-id="8edf5-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="8edf5-106">Je však možné dosáhnout dobrý výkon při výhradně týkajícími se výjimka pokyny, které zakáže použití se kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="8edf5-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="8edf5-107">Dva způsoby, které jsou popsané v této části navrhujeme způsoby, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="8edf5-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="8edf5-108">**X DO NOT** z důvodu obavy, že výjimky může ovlivnit výkon negativně používat kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="8edf5-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="8edf5-109">Ke zlepšení výkonu, je možné použít vzor Tester Doer nebo zkuste analýzy vzor, je popsáno v následujících dvou částech.</span><span class="sxs-lookup"><span data-stu-id="8edf5-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="8edf5-110">Vzor Tester Doer</span><span class="sxs-lookup"><span data-stu-id="8edf5-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="8edf5-111">Výkon člena vyvolání výjimek v některých případech lze zvýšit tím, že rozkládají člena na dva.</span><span class="sxs-lookup"><span data-stu-id="8edf5-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="8edf5-112">Podívejme se <xref:System.Collections.Generic.ICollection%601.Add%2A> metodu <xref:System.Collections.Generic.ICollection%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8edf5-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="8edf5-113">Metoda `Add` vyvolá výjimku, pokud je kolekce určena jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="8edf5-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="8edf5-114">To může být problém s výkonem ve scénářích, kde je očekávána volání metody, které k selhání často.</span><span class="sxs-lookup"><span data-stu-id="8edf5-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="8edf5-115">Jedním ze způsobů pro zmírnění těchto potíží je k ověření, zda kolekce je zapisovatelný, než se pokusíte přidat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8edf5-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="8edf5-116">Člen použily k testování podmínku, která je v našem příkladu vlastnost `IsReadOnly`, se označuje jako tester.</span><span class="sxs-lookup"><span data-stu-id="8edf5-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="8edf5-117">Člen použil k potenciálně aktivační operaci `Add` metoda v našem příkladu se označuje jako doer.</span><span class="sxs-lookup"><span data-stu-id="8edf5-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="8edf5-118">**✓ CONSIDER** Tester Doer vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.</span><span class="sxs-lookup"><span data-stu-id="8edf5-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="8edf5-119">Try-Parse vzor</span><span class="sxs-lookup"><span data-stu-id="8edf5-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="8edf5-120">Pro velmi citlivé na výkon rozhraní API je třeba použít ještě rychlejší vzor než Tester Doer vzor je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8edf5-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="8edf5-121">Vzor se volá pro úpravu názvu členu a proveďte jasně definované testovací malá a velká část sémantiku člena.</span><span class="sxs-lookup"><span data-stu-id="8edf5-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="8edf5-122">Například <xref:System.DateTime> definuje <xref:System.DateTime.Parse%2A> metodu, která vyvolá výjimku, pokud analýza řetězce selže.</span><span class="sxs-lookup"><span data-stu-id="8edf5-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="8edf5-123">Definuje také odpovídající <xref:System.DateTime.TryParse%2A> metodu, která se pokusí analyzovat, ale vrátí false, pokud analýza neúspěšná a vrátí výsledek úspěšné analýzy pomocí `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="8edf5-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
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
  
 <span data-ttu-id="8edf5-124">Při použití tohoto modelu, je potřeba definovat funkci zkuste v striktní podmínky.</span><span class="sxs-lookup"><span data-stu-id="8edf5-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="8edf5-125">Pokud člen selže z nějakého důvodu než je dobře definovaný try, musí člen stále vyvolat odpovídající výjimky.</span><span class="sxs-lookup"><span data-stu-id="8edf5-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="8edf5-126">**✓ CONSIDER** zkuste analýzy vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.</span><span class="sxs-lookup"><span data-stu-id="8edf5-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="8edf5-127">**✓ DO** použijte předponu "Zkuste" a logickou hodnotu návratový typ pro metody implementace tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="8edf5-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="8edf5-128">**✓ DO** zadejte člena vyvolávání výjimek pro každého člena pomocí vzoru zkuste analýzy.</span><span class="sxs-lookup"><span data-stu-id="8edf5-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="8edf5-129">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="8edf5-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8edf5-130">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="8edf5-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8edf5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8edf5-131">See also</span></span>

- [<span data-ttu-id="8edf5-132">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="8edf5-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8edf5-133">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="8edf5-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
