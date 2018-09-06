---
title: Návrh rozhraní
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c687d7622e82ee206b2201760818827398f8543b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863719"
---
# <a name="interface-design"></a><span data-ttu-id="002a3-102">Návrh rozhraní</span><span class="sxs-lookup"><span data-stu-id="002a3-102">Interface Design</span></span>
<span data-ttu-id="002a3-103">I když většina rozhraní API jsou nejlepším modelovány pomocí třídy a struktury, existují případy, ve kterých jsou vhodnější rozhraní, nebo je jedinou možností.</span><span class="sxs-lookup"><span data-stu-id="002a3-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="002a3-104">Modul CLR nepodporuje vícenásobnou dědičnost (například tříd CLR nemůže dědit z více než jedné základní třídy), ale umožní typy implementovat jedno nebo více rozhraní kromě dědí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="002a3-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="002a3-105">Rozhraní se proto často používají k dosažení efekt vícenásobná dědičnost.</span><span class="sxs-lookup"><span data-stu-id="002a3-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="002a3-106">Například <xref:System.IDisposable> je rozhraní, která umožňuje typy pro podporu disposability nezávisle na jiných hierarchii dědičnosti, ve kterém se mají zapojit.</span><span class="sxs-lookup"><span data-stu-id="002a3-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="002a3-107">Další situace, při definování, které je vhodné rozhraní je při vytváření jednotné rozhraní, které může podporovat několik typů, včetně některých typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="002a3-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="002a3-108">Typy hodnot nemůže dědit z typů jiných než <xref:System.ValueType>, ale mohou implementovat rozhraní, pomocí rozhraní je jedinou možností negace běžné základního typu.</span><span class="sxs-lookup"><span data-stu-id="002a3-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="002a3-109">**✓ DO** definovat rozhraní, pokud potřebujete některé společné rozhraní API jsou podporováni sada typy, které obsahuje typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="002a3-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="002a3-110">**✓ CONSIDER** definování rozhraní, pokud potřebujete podporu pro typy, které již dědí od jiný typ jeho funkcí.</span><span class="sxs-lookup"><span data-stu-id="002a3-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="002a3-111">**X AVOID** pomocí rozhraní značky (rozhraní s žádní členové).</span><span class="sxs-lookup"><span data-stu-id="002a3-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="002a3-112">Pokud budete muset označit třídu jako mají konkrétní charakteristiku (značky), obecně platí, použijte vlastní atribut, nikoli rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="002a3-113">**✓ DO** zadejte alespoň jeden typ, který je implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="002a3-114">Provádí se to pomáhá k ověření návrhu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="002a3-115">Například <xref:System.Collections.Generic.List%601> je implementace <xref:System.Collections.Generic.IList%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="002a3-116">**✓ DO** zadejte alespoň jeden rozhraní API, které zabírá jednotlivá rozhraní definujete (metoda, která bere rozhraní jako parametr nebo vlastnost zadán jako rozhraní).</span><span class="sxs-lookup"><span data-stu-id="002a3-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="002a3-117">Provádí se to pomáhá k ověření návrhu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="002a3-118">Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> využívá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="002a3-119">**X DO NOT** přidat členy do rozhraní, které se dříve dodaný.</span><span class="sxs-lookup"><span data-stu-id="002a3-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="002a3-120">Mohlo by narušil implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="002a3-121">Pokud se chcete vyhnout problémy se správou verzí byste měli vytvořit nové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="002a3-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="002a3-122">S výjimkou případů popsaných v těchto pokynů by měly obecně platí, zvolte třídy, nikoli rozhraní při navrhování opakovaně použitelné knihovny spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="002a3-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="002a3-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="002a3-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="002a3-124">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="002a3-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002a3-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="002a3-125">See also</span></span>

- [<span data-ttu-id="002a3-126">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="002a3-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="002a3-127">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="002a3-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
