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
ms.openlocfilehash: a558547f0e6770e7e76ca31f760d6e2f55c712db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289782"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="564ed-102">Výjimky a výkon</span><span class="sxs-lookup"><span data-stu-id="564ed-102">Exceptions and Performance</span></span>
<span data-ttu-id="564ed-103">Jedním z běžných obav souvisejících s výjimkou je, že pokud jsou výjimky používány pro kód, který rutinně selže, výkon implementace nebude možné přijmout.</span><span class="sxs-lookup"><span data-stu-id="564ed-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="564ed-104">Toto je platný problém.</span><span class="sxs-lookup"><span data-stu-id="564ed-104">This is a valid concern.</span></span> <span data-ttu-id="564ed-105">Když člen vyvolá výjimku, může jeho výkon pomalejit pořadí.</span><span class="sxs-lookup"><span data-stu-id="564ed-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="564ed-106">Je však možné dosáhnout dobrého výkonu v rámci striktního dodržování pokynů pro výjimky, které zakazují použití kódů chyb.</span><span class="sxs-lookup"><span data-stu-id="564ed-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="564ed-107">Tento postup popisují dva vzory popsané v této části.</span><span class="sxs-lookup"><span data-stu-id="564ed-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="564ed-108">❌Nepoužívejte kódy chyb z důvodu obav, že výjimky mohou negativně ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="564ed-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="564ed-109">Chcete-li zvýšit výkon, je možné použít buď vzorek test-Doer, nebo vzor try-Parse, který je popsán v následujících dvou částech.</span><span class="sxs-lookup"><span data-stu-id="564ed-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="564ed-110">Tester – vzor Doer</span><span class="sxs-lookup"><span data-stu-id="564ed-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="564ed-111">V některých případech je možné zvýšit výkon člena s aktivačními výjimkami, a to rozdělením členu na dva.</span><span class="sxs-lookup"><span data-stu-id="564ed-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="564ed-112">Pojďme se podívat na <xref:System.Collections.Generic.ICollection%601.Add%2A> metodu <xref:System.Collections.Generic.ICollection%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="564ed-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="564ed-113">Metoda `Add` vyvolá, je-li kolekce určena pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="564ed-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="564ed-114">Může se jednat o problém s výkonem ve scénářích, kdy se očekává, že volání metody bude často neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="564ed-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="564ed-115">Jedním ze způsobů, jak zmírnit problém, je otestovat, jestli je kolekce zapisovatelná, než se pokusíte přidat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="564ed-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="564ed-116">Člen použitý k otestování podmínky, která v našem příkladu je vlastnost `IsReadOnly` , je označována jako tester.</span><span class="sxs-lookup"><span data-stu-id="564ed-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="564ed-117">Člen, který se používá k provedení potenciálně vyvolání operace, `Add` metoda v našem příkladu je označována jako Doer.</span><span class="sxs-lookup"><span data-stu-id="564ed-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="564ed-118">✔️ Představte si vzor Tester-Doer pro členy, které mohou vyvolat výjimky v běžných scénářích, aby nedocházelo k problémům s výkonem souvisejícím s výjimkami.</span><span class="sxs-lookup"><span data-stu-id="564ed-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="564ed-119">Vzor try-Parse</span><span class="sxs-lookup"><span data-stu-id="564ed-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="564ed-120">Pro vysoce výkonná rozhraní API je vhodné použít ještě rychlejší model, než je vzor testovacího Doeru popsaný v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="564ed-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="564ed-121">Vzor volá pro úpravu názvu člena k vytvoření dobře definovaného testovacího případu, který je součástí sémantiky členů.</span><span class="sxs-lookup"><span data-stu-id="564ed-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="564ed-122">Například <xref:System.DateTime> definuje <xref:System.DateTime.Parse%2A> metodu, která vyvolá výjimku, pokud se analýza řetězce nezdařila.</span><span class="sxs-lookup"><span data-stu-id="564ed-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="564ed-123">Definuje také odpovídající <xref:System.DateTime.TryParse%2A> metodu, která se pokusí analyzovat, ale vrátí hodnotu false, pokud je analýza neúspěšná a vrátí výsledek úspěšné analýzy pomocí `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="564ed-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="564ed-124">Při použití tohoto modelu je důležité definovat funkci try na základě striktních podmínek.</span><span class="sxs-lookup"><span data-stu-id="564ed-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="564ed-125">Pokud se člen z jiného důvodu než jasně definovaného try nedaří, člen musí stále vyvolat odpovídající výjimku.</span><span class="sxs-lookup"><span data-stu-id="564ed-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="564ed-126">✔️ Představte vzor try-Parse pro členy, kteří mohou vyvolat výjimky v běžných scénářích, aby se předešlo problémům s výkonem souvisejícím s výjimkami.</span><span class="sxs-lookup"><span data-stu-id="564ed-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="564ed-127">pro metody, které implementují tento model, ✔️ použít předponu try a logický návratový typ.</span><span class="sxs-lookup"><span data-stu-id="564ed-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="564ed-128">pro každého člena pomocí vzoru try-Parse ✔️ poskytněte člena vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="564ed-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="564ed-129">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="564ed-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="564ed-130">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="564ed-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="564ed-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="564ed-131">See also</span></span>

- [<span data-ttu-id="564ed-132">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="564ed-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="564ed-133">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="564ed-133">Design Guidelines for Exceptions</span></span>](exceptions.md)
