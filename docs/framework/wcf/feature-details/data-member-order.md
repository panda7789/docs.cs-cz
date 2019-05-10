---
title: Pořadí datových členů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: d717673139ba810c1593e5c60e488537426f1f64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754407"
---
# <a name="data-member-order"></a><span data-ttu-id="dc618-102">Pořadí datových členů</span><span class="sxs-lookup"><span data-stu-id="dc618-102">Data Member Order</span></span>
<span data-ttu-id="dc618-103">V některých aplikacích je užitečné vědět, pořadí, ve kterém se odešle data z různých datových členů, nebo má být přijata (jako například pořadí, ve kterém se zobrazí data v serializovaném kódu XML).</span><span class="sxs-lookup"><span data-stu-id="dc618-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="dc618-104">V některých případech může být potřeba toto pořadí změnit.</span><span class="sxs-lookup"><span data-stu-id="dc618-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="dc618-105">Toto téma popisuje pravidla řazení.</span><span class="sxs-lookup"><span data-stu-id="dc618-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="dc618-106">Základní pravidla</span><span class="sxs-lookup"><span data-stu-id="dc618-106">Basic Rules</span></span>  
 <span data-ttu-id="dc618-107">Základní pravidla pro řazení dat patří:</span><span class="sxs-lookup"><span data-stu-id="dc618-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="dc618-108">Pokud typ kontraktu dat je součástí hierarchie dědičnosti, jsou vždy první v pořadí datových členů z jeho základních typů.</span><span class="sxs-lookup"><span data-stu-id="dc618-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="dc618-109">Dále v pořadí jsou aktuální typ datové členy, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atribut sady, v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="dc618-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="dc618-110">Dále jsou všechny datové členy, které mají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> sadu atributů.</span><span class="sxs-lookup"><span data-stu-id="dc618-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="dc618-111">Tyto jsou řazeny podle hodnoty `Order` vlastnost první a pak podle abecedy, pokud existuje více než jednoho člena sady určitým `Order` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dc618-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="dc618-112">Hodnoty pořadí se může přeskočit.</span><span class="sxs-lookup"><span data-stu-id="dc618-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="dc618-113">Abecedním pořadí pokládáme stav, voláním <xref:System.String.CompareOrdinal%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dc618-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dc618-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="dc618-114">Examples</span></span>  
 <span data-ttu-id="dc618-115">Uvažujme následující kód.</span><span class="sxs-lookup"><span data-stu-id="dc618-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="dc618-116">Vytvořený kód XML je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="dc618-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc618-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc618-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="dc618-118">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="dc618-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="dc618-119">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="dc618-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
