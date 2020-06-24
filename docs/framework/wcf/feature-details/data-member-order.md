---
title: Pořadí datových členů
description: Přečtěte si o pořadí datových členů ve službě WCF. Aplikace může potřebovat znát nebo změnit pořadí, ve kterém jsou datové členy odesílány nebo očekávány.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 5c192d3bda65a7364345df4310dccd96cbe04056
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247361"
---
# <a name="data-member-order"></a><span data-ttu-id="3a6c7-104">Pořadí datových členů</span><span class="sxs-lookup"><span data-stu-id="3a6c7-104">Data Member Order</span></span>
<span data-ttu-id="3a6c7-105">V některých aplikacích je užitečné znát pořadí, ve kterém jsou odesílána data z různých datových členů, nebo se očekává, že budou přijata (například pořadí, ve kterém se data zobrazují v serializovaném kódu XML).</span><span class="sxs-lookup"><span data-stu-id="3a6c7-105">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="3a6c7-106">V některých případech může být nutné změnit toto pořadí.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-106">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="3a6c7-107">Toto téma vysvětluje pravidla řazení.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-107">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="3a6c7-108">Základní pravidla</span><span class="sxs-lookup"><span data-stu-id="3a6c7-108">Basic Rules</span></span>  
 <span data-ttu-id="3a6c7-109">Základní pravidla pro řazení dat zahrnují:</span><span class="sxs-lookup"><span data-stu-id="3a6c7-109">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="3a6c7-110">Pokud je typ kontraktu dat součástí hierarchie dědičnosti, datové členy svých základních typů jsou vždy první v pořadí.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-110">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="3a6c7-111">Další v pořadí jsou datové členy aktuálního typu, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> sady atributů v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-111">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="3a6c7-112">Další jsou všechny datové členy, které mají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> sady atributů.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-112">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="3a6c7-113">Ty jsou seřazené podle hodnoty `Order` vlastnosti nejdříve a pak abecedně, pokud je více než jeden člen určité `Order` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-113">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="3a6c7-114">Hodnoty pořadí se můžou přeskočit.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-114">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="3a6c7-115">Abecední pořadí je stanoveno voláním <xref:System.String.CompareOrdinal%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-115">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3a6c7-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="3a6c7-116">Examples</span></span>  
 <span data-ttu-id="3a6c7-117">Vezměte v úvahu následující kód.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-117">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="3a6c7-118">Vyprodukovaný kód XML je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="3a6c7-118">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a6c7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a6c7-119">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="3a6c7-120">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="3a6c7-120">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="3a6c7-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="3a6c7-121">Using Data Contracts</span></span>](using-data-contracts.md)
