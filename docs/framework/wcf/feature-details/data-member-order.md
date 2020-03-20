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
# <a name="data-member-order"></a>Pořadí datových členů
V některých aplikacích je užitečné znát pořadí, ve kterém jsou odesílána nebo očekáváse, že budou přijata data z různých datových členů (například pořadí, ve kterém se data zobrazí v serializovaném xml). Někdy může být nutné toto pořadí změnit. Toto téma vysvětluje pravidla řazení.  
  
## <a name="basic-rules"></a>Základní pravidla  
 Mezi základní pravidla pro objednávání dat patří:  
  
- Pokud typ kontraktu dat je součástí hierarchie dědičnosti, datové členy jeho základní typy jsou vždy první v pořadí.  
  
- Další v pořadí jsou datové členy aktuálního typu, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost sady <xref:System.Runtime.Serialization.DataMemberAttribute> atributů v abecedním pořadí.  
  
- Dále jsou všechny datové <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> členy, <xref:System.Runtime.Serialization.DataMemberAttribute> které mají vlastnost atribut ustanovené. Ty jsou seřazeny podle hodnoty `Order` vlastnosti první a pak abecedně, pokud je více než jeden člen určité `Order` hodnoty. Hodnoty objednávky mohou být přeskočeny.  
  
 Abecední pořadí je <xref:System.String.CompareOrdinal%2A> stanovena voláním metody.  
  
## <a name="examples"></a>Příklady  
 Zvažte následující kód.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Vytvořený kód XML je podobný následujícímu.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
