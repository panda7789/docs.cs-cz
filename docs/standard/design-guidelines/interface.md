---
title: "Rozhraní návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d04011622321638e1f3b0c5f4d270f840c7070e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interface-design"></a><span data-ttu-id="671ef-102">Rozhraní návrhu</span><span class="sxs-lookup"><span data-stu-id="671ef-102">Interface Design</span></span>
<span data-ttu-id="671ef-103">I když většina rozhraní API jsou nejlépe modelovány pomocí třídy a struktury, existují případy, ve kterých jsou vhodnější rozhraní, nebo je jedinou možností.</span><span class="sxs-lookup"><span data-stu-id="671ef-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="671ef-104">Modul CLR nepodporuje vícenásobná dědičnost (tj, tříd CLR nemůže Zdědit z více než jeden základní třídy), ale neumožňuje typy implementovat jednu nebo více rozhraní kromě dědění ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="671ef-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="671ef-105">Rozhraní se proto často používají k dosažení účinku vícenásobná dědičnost.</span><span class="sxs-lookup"><span data-stu-id="671ef-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="671ef-106">Například <xref:System.IDisposable> je rozhraní, které umožňuje typy pro podporu disposability nezávislé na dalších hierarchie dědičnosti, ve které se chcete zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="671ef-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="671ef-107">Další situace při definování, které je vhodné rozhraní je při vytváření jednotné rozhraní, které může podporovat několik typů, včetně některých typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="671ef-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="671ef-108">Typy hodnot nemůže Zdědit z typy jiné než <xref:System.ValueType>, ale implementovaly rozhraní, tak přes rozhraní je jedinou možností Chcete-li poskytovat běžné základního typu.</span><span class="sxs-lookup"><span data-stu-id="671ef-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="671ef-109">**PROVEĎTE ✓** definovat rozhraní, pokud potřebujete některé společné rozhraní API jsou podporováni sada typy, které obsahuje typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="671ef-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="671ef-110">**✓ ZVAŽTE** definování rozhraní, pokud potřebujete podporu pro typy, které již dědí od jiný typ jeho funkcí.</span><span class="sxs-lookup"><span data-stu-id="671ef-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="671ef-111">**X nepoužívejte** pomocí rozhraní značky (rozhraní s žádní členové).</span><span class="sxs-lookup"><span data-stu-id="671ef-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="671ef-112">Pokud potřebujete označte třídu tak, že má zvláštní vlastností (značka), obecně platí, použijte vlastní atribut, nikoli rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="671ef-113">**PROVEĎTE ✓** zadejte alespoň jeden typ, který je implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="671ef-114">Díky této pomáhá ověření návrhu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="671ef-115">Například <xref:System.Collections.Generic.List%601> je implementací <xref:System.Collections.Generic.IList%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="671ef-116">**PROVEĎTE ✓** zadejte alespoň jeden rozhraní API, které zabírá jednotlivá rozhraní definujete (metoda, která bere rozhraní jako parametr nebo vlastnost zadán jako rozhraní).</span><span class="sxs-lookup"><span data-stu-id="671ef-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="671ef-117">Díky této pomáhá ověření návrhu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="671ef-118">Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> spotřebovává <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="671ef-119">**X nesmí** přidat členy do rozhraní, které se dříve dodaný.</span><span class="sxs-lookup"><span data-stu-id="671ef-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="671ef-120">Tím by došlo k přerušení implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="671ef-121">Aby se zabránilo problémům s verzemi, byste měli vytvořit nové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="671ef-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="671ef-122">S výjimkou případů popsaných v těchto pokynů měli byste, obecně vybrat třídy, nikoli rozhraní návrhu opakovaně použitelné knihovny spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="671ef-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="671ef-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="671ef-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="671ef-124">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="671ef-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671ef-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="671ef-125">See Also</span></span>  
 [<span data-ttu-id="671ef-126">Typ pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="671ef-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="671ef-127">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="671ef-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
