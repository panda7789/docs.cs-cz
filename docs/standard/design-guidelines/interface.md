---
title: Rozhraní návrhu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dea5877f952869d5c84d6019617fcdc52d8ee0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573036"
---
# <a name="interface-design"></a><span data-ttu-id="fab01-102">Rozhraní návrhu</span><span class="sxs-lookup"><span data-stu-id="fab01-102">Interface Design</span></span>
<span data-ttu-id="fab01-103">I když většina rozhraní API jsou nejlépe modelovány pomocí třídy a struktury, existují případy, ve kterých jsou vhodnější rozhraní, nebo je jedinou možností.</span><span class="sxs-lookup"><span data-stu-id="fab01-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="fab01-104">Modul CLR nepodporuje vícenásobná dědičnost (tj, tříd CLR nemůže Zdědit z více než jeden základní třídy), ale neumožňuje typy implementovat jednu nebo více rozhraní kromě dědění ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fab01-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="fab01-105">Rozhraní se proto často používají k dosažení účinku vícenásobná dědičnost.</span><span class="sxs-lookup"><span data-stu-id="fab01-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="fab01-106">Například <xref:System.IDisposable> je rozhraní, které umožňuje typy pro podporu disposability nezávislé na dalších hierarchie dědičnosti, ve které se chcete zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="fab01-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="fab01-107">Další situace při definování, které je vhodné rozhraní je při vytváření jednotné rozhraní, které může podporovat několik typů, včetně některých typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="fab01-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="fab01-108">Typy hodnot nemůže Zdědit z typy jiné než <xref:System.ValueType>, ale implementovaly rozhraní, tak přes rozhraní je jedinou možností Chcete-li poskytovat běžné základního typu.</span><span class="sxs-lookup"><span data-stu-id="fab01-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="fab01-109">**✓ DO** definovat rozhraní, pokud potřebujete některé společné rozhraní API jsou podporováni sada typy, které obsahuje typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="fab01-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="fab01-110">**✓ CONSIDER** definování rozhraní, pokud potřebujete podporu pro typy, které již dědí od jiný typ jeho funkcí.</span><span class="sxs-lookup"><span data-stu-id="fab01-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="fab01-111">**X AVOID** pomocí rozhraní značky (rozhraní s žádní členové).</span><span class="sxs-lookup"><span data-stu-id="fab01-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="fab01-112">Pokud potřebujete označte třídu tak, že má zvláštní vlastností (značka), obecně platí, použijte vlastní atribut, nikoli rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="fab01-113">**✓ DO** zadejte alespoň jeden typ, který je implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="fab01-114">Díky této pomáhá ověření návrhu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="fab01-115">Například <xref:System.Collections.Generic.List%601> je implementací <xref:System.Collections.Generic.IList%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="fab01-116">**✓ DO** zadejte alespoň jeden rozhraní API, které zabírá jednotlivá rozhraní definujete (metoda, která bere rozhraní jako parametr nebo vlastnost zadán jako rozhraní).</span><span class="sxs-lookup"><span data-stu-id="fab01-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="fab01-117">Díky této pomáhá ověření návrhu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="fab01-118">Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> spotřebovává <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="fab01-119">**X DO NOT** přidat členy do rozhraní, které se dříve dodaný.</span><span class="sxs-lookup"><span data-stu-id="fab01-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="fab01-120">Tím by došlo k přerušení implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="fab01-121">Aby se zabránilo problémům s verzemi, byste měli vytvořit nové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab01-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="fab01-122">S výjimkou případů popsaných v těchto pokynů měli byste, obecně vybrat třídy, nikoli rozhraní návrhu opakovaně použitelné knihovny spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fab01-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="fab01-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="fab01-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fab01-124">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fab01-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab01-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="fab01-125">See Also</span></span>  
 [<span data-ttu-id="fab01-126">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="fab01-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="fab01-127">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="fab01-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
