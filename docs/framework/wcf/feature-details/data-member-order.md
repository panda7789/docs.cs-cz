---
title: Pořadí datových členů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 717d7014f4c4a56249ead0c839cf05f4f83a6f5f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593461"
---
# <a name="data-member-order"></a>Pořadí datových členů
V některých aplikacích je užitečné znát pořadí, ve kterém jsou odesílána data z různých datových členů, nebo se očekává, že budou přijata (například pořadí, ve kterém se data zobrazují v serializovaném kódu XML). V některých případech může být nutné změnit toto pořadí. Toto téma vysvětluje pravidla řazení.  
  
## <a name="basic-rules"></a>Základní pravidla  
 Základní pravidla pro řazení dat zahrnují:  
  
- Pokud je typ kontraktu dat součástí hierarchie dědičnosti, datové členy svých základních typů jsou vždy první v pořadí.  
  
- Další v pořadí jsou datové členy aktuálního typu, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> sady atributů v abecedním pořadí.  
  
- Další jsou všechny datové členy, které mají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> sady atributů. Ty jsou seřazené podle hodnoty `Order` vlastnosti nejdříve a pak abecedně, pokud je více než jeden člen určité `Order` hodnoty. Hodnoty pořadí se můžou přeskočit.  
  
 Abecední pořadí je stanoveno voláním <xref:System.String.CompareOrdinal%2A> metody.  
  
## <a name="examples"></a>Příklady  
 Vezměte v úvahu následující kód.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Vyprodukovaný kód XML je podobný následujícímu.  
  
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
- [Ekvivalence kontraktů dat](data-contract-equivalence.md)
- [Použití kontraktů dat](using-data-contracts.md)
