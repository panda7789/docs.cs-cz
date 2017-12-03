---
title: "Pořadí datových členů"
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
helpviewer_keywords: data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8a838b2dd2367bed3fb3ffa3248e67c23f7917d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="data-member-order"></a><span data-ttu-id="98386-102">Pořadí datových členů</span><span class="sxs-lookup"><span data-stu-id="98386-102">Data Member Order</span></span>
<span data-ttu-id="98386-103">V některých aplikacích je dobré vědět, pořadí, ve kterém se odesílají data z různých datových členů, nebo musí být přijata (například pořadí, ve kterém se data zobrazí v serializovaných XML).</span><span class="sxs-lookup"><span data-stu-id="98386-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="98386-104">V některých případech může být potřeba změnit toto pořadí.</span><span class="sxs-lookup"><span data-stu-id="98386-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="98386-105">Toto téma popisuje pravidla řazení.</span><span class="sxs-lookup"><span data-stu-id="98386-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="98386-106">Základních pravidel</span><span class="sxs-lookup"><span data-stu-id="98386-106">Basic Rules</span></span>  
 <span data-ttu-id="98386-107">Základní pravidla pro řazení dat patří:</span><span class="sxs-lookup"><span data-stu-id="98386-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="98386-108">Pokud typ kontraktu dat je součástí hierarchie dědičnosti, jsou vždy první v pořadí datových členů z jeho základních typů.</span><span class="sxs-lookup"><span data-stu-id="98386-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="98386-109">Další v pořadí jsou členy aktuální typ dat, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> nastaven v abecedním pořadí atribut.</span><span class="sxs-lookup"><span data-stu-id="98386-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="98386-110">Dále jsou všechny datové členy, které mají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> nastaven atribut.</span><span class="sxs-lookup"><span data-stu-id="98386-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="98386-111">Tyto jsou seřazené podle hodnoty `Order` vlastnost první a potom abecedně, pokud je více než jednoho člena určité `Order` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="98386-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="98386-112">Může být přeskočeny hodnoty pořadí.</span><span class="sxs-lookup"><span data-stu-id="98386-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="98386-113">Abecedním pořadí založená na volání <xref:System.String.CompareOrdinal%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="98386-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="98386-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="98386-114">Examples</span></span>  
 <span data-ttu-id="98386-115">Vezměte v úvahu následující kód.</span><span class="sxs-lookup"><span data-stu-id="98386-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="98386-116">XML vytvořeného je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="98386-116">The XML produced is similar to the following.</span></span>  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98386-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="98386-117">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [<span data-ttu-id="98386-118">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="98386-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="98386-119">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="98386-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
