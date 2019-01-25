---
title: Pořadí datových členů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 93ec81d94d8133fc5a6d71d7f1b57b2e9a6aad21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659628"
---
# <a name="data-member-order"></a>Pořadí datových členů
V některých aplikacích je užitečné vědět, pořadí, ve kterém se odešle data z různých datových členů, nebo má být přijata (jako například pořadí, ve kterém se zobrazí data v serializovaném kódu XML). V některých případech může být potřeba toto pořadí změnit. Toto téma popisuje pravidla řazení.  
  
## <a name="basic-rules"></a>Základní pravidla  
 Základní pravidla pro řazení dat patří:  
  
-   Pokud typ kontraktu dat je součástí hierarchie dědičnosti, jsou vždy první v pořadí datových členů z jeho základních typů.  
  
-   Dále v pořadí jsou aktuální typ datové členy, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atribut sady, v abecedním pořadí.  
  
-   Dále jsou všechny datové členy, které mají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> sadu atributů. Tyto jsou řazeny podle hodnoty `Order` vlastnost první a pak podle abecedy, pokud existuje více než jednoho člena sady určitým `Order` hodnotu. Hodnoty pořadí se může přeskočit.  
  
 Abecedním pořadí pokládáme stav, voláním <xref:System.String.CompareOrdinal%2A> metody.  
  
## <a name="examples"></a>Příklady  
 Uvažujme následující kód.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
