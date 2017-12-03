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
# <a name="data-member-order"></a>Pořadí datových členů
V některých aplikacích je dobré vědět, pořadí, ve kterém se odesílají data z různých datových členů, nebo musí být přijata (například pořadí, ve kterém se data zobrazí v serializovaných XML). V některých případech může být potřeba změnit toto pořadí. Toto téma popisuje pravidla řazení.  
  
## <a name="basic-rules"></a>Základních pravidel  
 Základní pravidla pro řazení dat patří:  
  
-   Pokud typ kontraktu dat je součástí hierarchie dědičnosti, jsou vždy první v pořadí datových členů z jeho základních typů.  
  
-   Další v pořadí jsou členy aktuální typ dat, které nemají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> nastaven v abecedním pořadí atribut.  
  
-   Dále jsou všechny datové členy, které mají <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> nastaven atribut. Tyto jsou seřazené podle hodnoty `Order` vlastnost první a potom abecedně, pokud je více než jednoho člena určité `Order` hodnotu. Může být přeskočeny hodnoty pořadí.  
  
 Abecedním pořadí založená na volání <xref:System.String.CompareOrdinal%2A> metoda.  
  
## <a name="examples"></a>Příklady  
 Vezměte v úvahu následující kód.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 XML vytvořeného je podobný následujícímu.  
  
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
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
