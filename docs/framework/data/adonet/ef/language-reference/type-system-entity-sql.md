---
title: "Systém typů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b68bce0e3f1139b48446200decca5beb0a1a1a71
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="type-system-entity-sql"></a>Systém typů (entita SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje několik typů:  
  
-   (Jednoduchý) primitivní typy, jako `Int32` a`String.`  
  
-   Nominální typy, které jsou definované ve schématu, jako například <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, a <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
-   Anonymní typy, které nejsou výslovně definované ve schématu: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, a <xref:System.Data.Metadata.Edm.RefType>.  
  
 Tato část popisuje anonymní typy, které nejsou výslovně definované ve schématu, ale podporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Informace o typech primitivní a nominální najdete v tématu [konceptuálního modelu typy (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).  
  
## <a name="rows"></a>Řádky  
 Struktura řádku závisí na pořadí typu a s názvem členů, které se skládá z řádku. Typ řádku má žádná identita a nemůže být zděděno z. Instance stejného typu řádek jsou ekvivalentní, pokud jsou členy v uvedeném pořadí ekvivalentní. Řádky žádné chovají nad rámec jejich strukturální ekvivalenční a nemají žádný ekvivalent v modulu CLR. Dotazy může mít za následek struktury, které obsahují řádky nebo kolekce řádků. Rozhraní API vazbu mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy a hostitelského jazyka definuje, jak jsou realizovány řádků v dotazu, který vytváří výsledek. Informace o tom, jak vytvořit instanci řádek najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekce  
 Typy kolekcí představují nula nebo více instancí jiné objekty. Informace o tom, jak vytvořit kolekci najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odkazy  
 Odkaz je logické ukazatel na konkrétní entity v sadě konkrétní entity.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje následující operátory k vytváření, deconstruct a procházení odkazy:  
  
-   [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 Odkaz můžete procházet pomocí operátor přístupu (tečka) členů (`.`). Následující fragment kódu extrahuje Vlastnost Id (pořadí) tak, že přejdete pomocí vlastnosti r (referenční dokumentace).  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Pokud hodnota odkaz má hodnotu null, nebo pokud cíl odkazu neexistuje, výsledkem je null.  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 [Specifikace CSDL, SSDL a MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
