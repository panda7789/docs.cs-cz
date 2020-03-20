---
title: Pořadí datových členů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 2a5d7430953bdc31644e92b9207cd2865209cce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185202"
---
# <a name="data-member-order"></a><span data-ttu-id="1b2d7-102">Pořadí datových členů</span><span class="sxs-lookup"><span data-stu-id="1b2d7-102">Data Member Order</span></span>
<span data-ttu-id="1b2d7-103">V některých aplikacích je užitečné znát pořadí, ve kterém jsou odesílána nebo očekáváse, že budou přijata data z různých datových členů (například pořadí, ve kterém se data zobrazí v serializovaném xml).</span><span class="sxs-lookup"><span data-stu-id="1b2d7-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="1b2d7-104">Někdy může být nutné toto pořadí změnit.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="1b2d7-105">Toto téma vysvětluje pravidla řazení.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="1b2d7-106">Základní pravidla</span><span class="sxs-lookup"><span data-stu-id="1b2d7-106">Basic Rules</span></span>  
 <span data-ttu-id="1b2d7-107">Mezi základní pravidla pro objednávání dat patří:</span><span class="sxs-lookup"><span data-stu-id="1b2d7-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="1b2d7-108">Pokud typ kontraktu dat je součástí hierarchie dědičnosti, datové členy jeho základní typy jsou vždy první v pořadí.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="1b2d7-109">Další v pořadí jsou datové členy aktuálního typu, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost sady <xref:System.Runtime.Serialization.DataMemberAttribute> atributů v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="1b2d7-110">Dále jsou všechny datové <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> členy, <xref:System.Runtime.Serialization.DataMemberAttribute> které mají vlastnost atribut ustanovené.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="1b2d7-111">Ty jsou seřazeny podle hodnoty `Order` vlastnosti první a pak abecedně, pokud je více než jeden člen určité `Order` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="1b2d7-112">Hodnoty objednávky mohou být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="1b2d7-113">Abecední pořadí je <xref:System.String.CompareOrdinal%2A> stanovena voláním metody.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1b2d7-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="1b2d7-114">Examples</span></span>  
 <span data-ttu-id="1b2d7-115">Zvažte následující kód.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="1b2d7-116">Vytvořený kód XML je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="1b2d7-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b2d7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b2d7-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="1b2d7-118">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1b2d7-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="1b2d7-119">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1b2d7-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
