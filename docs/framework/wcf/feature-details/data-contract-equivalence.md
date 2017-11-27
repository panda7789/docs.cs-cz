---
title: "Ekvivalence kontraktů dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e3494c877db156ecc818c760bd0712f5e59ca0a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="data-contract-equivalence"></a><span data-ttu-id="cd6fd-102">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="cd6fd-102">Data Contract Equivalence</span></span>
<span data-ttu-id="cd6fd-103">Pro klienta k úspěšnému odeslání dat určitého typu služby nebo k službě úspěšně posílat data do klienta odeslané typ nemusí nutně existovat na koncové straně příjmu.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-103">For a client to successfully send data of a certain type to a service, or a service to successfully send data to a client, the sent type does not necessarily have to exist on the receiving end.</span></span> <span data-ttu-id="cd6fd-104">Jediným požadavkem je, že kontrakty dat obou typů být ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-104">The only requirement is that the data contracts of both types be equivalent.</span></span> <span data-ttu-id="cd6fd-105">(V některých případech striktní ekvivalenční se nevyžaduje, jak je popsáno v [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span><span class="sxs-lookup"><span data-stu-id="cd6fd-105">(Sometimes, strict equivalence is not required, as discussed in [Data Contract Versioning](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span></span>  
  
 <span data-ttu-id="cd6fd-106">Pro datové kontrakty jako ekvivalentní musí mít stejný obor názvů a název.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-106">For data contracts to be equivalent, they must have the same namespace and name.</span></span> <span data-ttu-id="cd6fd-107">Kromě toho musí mít každý člen data na jedné straně člena ekvivalentní datové na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-107">Additionally, each data member on one side must have an equivalent data member on the other side.</span></span>  
  
 <span data-ttu-id="cd6fd-108">Pro datové členy jako ekvivalentní musí mít stejný název.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-108">For data members to be equivalent, they must have the same name.</span></span> <span data-ttu-id="cd6fd-109">Kromě toho musí představovat stejný typ dat; To znamená musí být jejich kontrakty dat ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-109">Additionally, they must represent the same type of data; that is, their data contracts must be equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd6fd-110">Všimněte si, že kontraktů dat názvy a obory názvů, jakož i názvy datových členů malých a velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-110">Note that data contract names and namespaces, as well as data member names, are case-sensitive.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cd6fd-111">názvy kontraktu dat a obory názvů, jakož i názvy členů data, najdete v části [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fd-111"> data contract names and namespaces, as well as data member names, see [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span></span>  
  
 <span data-ttu-id="cd6fd-112">Pokud existují dva typy na jedné straně (odesílatel nebo příjemce) a jejich kontrakty dat nejsou ekvivalentní (například mají různé datové členy), by neměl jim poskytnout se stejným názvem a oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-112">If two types exist on the same side (sender or receiver) and their data contracts are not equivalent (for example, they have different data members), you should not give them the same name and namespace.</span></span> <span data-ttu-id="cd6fd-113">Díky tomu může způsobit vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-113">Doing so may cause exceptions to be thrown.</span></span>  
  
 <span data-ttu-id="cd6fd-114">Kontrakty dat pro následující typy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="cd6fd-114">The data contracts for the following types are equivalent:</span></span>  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a><span data-ttu-id="cd6fd-115">Ekvivalence pořadí datových členů a kontrakt dat</span><span class="sxs-lookup"><span data-stu-id="cd6fd-115">Data Member Order and Data Contract equivalence</span></span>  
 <span data-ttu-id="cd6fd-116">Pomocí <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> třída může mít vliv na ekvivalence kontraktů dat.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-116">Using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> class may affect data contract equivalence.</span></span> <span data-ttu-id="cd6fd-117">Kontrakty dat musí mít členy, které se zobrazují ve stejném pořadí jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-117">The data contracts must have members that appear in the same order to be equivalent.</span></span> <span data-ttu-id="cd6fd-118">Výchozí pořadí je abecední.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-118">The default order is alphabetical.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="cd6fd-119">[Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fd-119"> [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="cd6fd-120">Například následující kód výsledkem ekvivalentní datové kontrakty.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-120">For example, the following code results in equivalent data contracts.</span></span>  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 <span data-ttu-id="cd6fd-121">Ale následující nevede ekvivalentní datové kontrakt.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-121">However, the following does not result in an equivalent data contract.</span></span>  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a><span data-ttu-id="cd6fd-122">Dědičnost, rozhraní a ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="cd6fd-122">Inheritance, Interfaces, and Data Contract Equivalence</span></span>  
 <span data-ttu-id="cd6fd-123">Při určování ekvivalenční, považuje kontraktu dat, která dědí z jiné kontrakt dat, pokud je pouze jeden kontrakt dat, která zahrnuje všechny členy data ze základního typu.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-123">When determining equivalence, a data contract that inherits from another data contract is treated as if it is just one data contract that includes all of the data members from the base type.</span></span> <span data-ttu-id="cd6fd-124">Mějte na paměti, která se musí shodovat s pořadí datových členů a že předcházet členy základní typ odvozený typ členy v pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-124">Keep in mind that the order of the data members must match and that base type members precede derived type members in the order.</span></span> <span data-ttu-id="cd6fd-125">Navíc pokud dva data členů jako v následujícím příkladu kódu mají stejnou hodnotu pořadí, řazení pro členy těchto dat je abecední.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-125">Furthermore, if, as in the following code example, two data members have the same order value, the ordering for those data members is alphabetical.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="cd6fd-126">[Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fd-126"> [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="cd6fd-127">V následujícím příkladu kontraktu dat pro typ `Employee` je ekvivalentní kontrakt dat pro typ `Worker`.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-127">In the following example, the data contract for type `Employee` is equivalent to the data contract for the type `Worker`.</span></span>  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 <span data-ttu-id="cd6fd-128">Při předávání parametry a návratové hodnoty mezi klientem a služby, kontrakt dat z databáze třídu, nelze odeslat při příjmu koncový bod očekává kontraktu dat z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-128">When passing parameters and return values between a client and a service, a data contract from a base class cannot be sent when the receiving endpoint expects a data contract from a derived class.</span></span> <span data-ttu-id="cd6fd-129">Toto je v souladu s objektově orientované programování principů.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-129">This is in accordance with object-oriented programming tenets.</span></span> <span data-ttu-id="cd6fd-130">V předchozím příkladu, objekt typu `Person` nelze odeslat, kdy `Employee` se očekává.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-130">In the previous example, an object of type `Person` cannot be sent when an `Employee` is expected.</span></span>  
  
 <span data-ttu-id="cd6fd-131">Kontrakt dat z odvozené třídy lze odeslat při kontraktu dat z databáze třídu, očekává se, ale pouze v případě, že přijímající koncový bod "ví" odvozený typ použití <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-131">A data contract from a derived class can be sent when a data contract from a base class is expected, but only if the receiving endpoint "knows" of the derived type using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="cd6fd-132">[Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fd-132"> [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="cd6fd-133">V předchozím příkladu, objekt typu `Employee` lze odeslat při `Person` je očekávané, ale pouze v případě, že kód příjemce aktivuje <xref:System.Runtime.Serialization.KnownTypeAttribute> chcete zahrnout do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-133">In the previous example, an object of type `Employee` can be sent when a `Person` is expected, but only if the receiver code employs the <xref:System.Runtime.Serialization.KnownTypeAttribute> to include it in the list of known types.</span></span>  
  
 <span data-ttu-id="cd6fd-134">Při předávání parametry a návratové hodnoty mezi aplikacemi, pokud očekávaný typ je rozhraní, je ekvivalentní očekávaný typ je typ <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-134">When passing parameters and return values between applications, if the expected type is an interface, it is equivalent to the expected type being of type <xref:System.Object>.</span></span> <span data-ttu-id="cd6fd-135">Protože každý typ výsledku odvozen z <xref:System.Object>, každý kontrakt dat nakonec odvozuje od kontrakt dat pro <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-135">Because every type ultimately derives from <xref:System.Object>, every data contract ultimately derives from the data contract for <xref:System.Object>.</span></span> <span data-ttu-id="cd6fd-136">Proto může být libovolný typ kontraktu dat předán očekávaném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6fd-136">Thus, any data contract type can be passed when an interface is expected.</span></span> <span data-ttu-id="cd6fd-137">Další kroky jsou nutné k úspěšně práci s rozhraními; Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fd-137">Additional steps are required to successfully work with interfaces; for more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6fd-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd6fd-138">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="cd6fd-139">Pořadí datových členů</span><span class="sxs-lookup"><span data-stu-id="cd6fd-139">Data Member Order</span></span>](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [<span data-ttu-id="cd6fd-140">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="cd6fd-140">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="cd6fd-141">Názvy kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="cd6fd-141">Data Contract Names</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
