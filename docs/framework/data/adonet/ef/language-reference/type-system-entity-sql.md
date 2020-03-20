---
title: Typový systém (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149828"
---
# <a name="type-system-entity-sql"></a>Typový systém (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje řadu typů:  
  
- Primitivní (jednoduché) typy, jako `Int32` jsou`String.`  
  
- Nominální typy, které jsou definovány ve <xref:System.Data.Metadata.Edm.EntityType>schématu, například , <xref:System.Data.Metadata.Edm.ComplexType>a <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Anonymní typy, které nejsou definovány ve <xref:System.Data.Metadata.Edm.CollectionType>schématu explicitně: , <xref:System.Data.Metadata.Edm.RowType>a <xref:System.Data.Metadata.Edm.RefType>.  
  
 Tato část popisuje anonymní typy, které nejsou definovány ve schématu explicitně, ale jsou podporovány entity SQL. Informace o primitivních a nominálních typech naleznete v [tématu Conceptual Model Types (CSDL).](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)  
  
## <a name="rows"></a>Řádky  
 Struktura řádku závisí na pořadí zadali a pojmenované členy, které řádek se skládá z. Typ řádku nemá žádnou identitu a nelze z ní zdědit. Instance stejného typu řádku jsou ekvivalentní, pokud jsou členy ekvivalentní. Řádky nemají žádné chování mimo jejich strukturální ekvivalence a nemají žádný ekvivalent v běžném jazyku runtime. Dotazy může mít za následek struktury, které obsahují řádky nebo kolekce řádků. Vazba rozhraní [!INCLUDE[esql](../../../../../../includes/esql-md.md)] API mezi dotazy a jazyk hostitele definuje, jak jsou řádky realizovány v dotazu, který vytvořil výsledek. Informace o tom, jak vytvořit instanci řádku, naleznete v [tématu Vytváření typů](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekce  
 Kolekce typy představují nula nebo více instancí jiných objektů. Informace o tom, jak vytvořit kolekci, naleznete [v tématu Vytváření typů](constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odkazy  
 Odkaz je logický ukazatel na určitou entitu v určité sadě entit.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje následující operátory k vytvoření, dekonstrukci a procházení odkazů:  
  
- [Ref](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [Klíč](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Můžete procházet odkaz pomocí operátoru přístup u člena`.`(tečka) ( ). Následující úryvek extrahuje Id vlastnost (Order) procházením r (reference) vlastnost.  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 Pokud je hodnota odkazu null nebo pokud cíl odkazu neexistuje, výsledek je null.  
  
## <a name="see-also"></a>Viz také

- [Přehled Entity SQL](entity-sql-overview.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [Specifikace CSDL, SSDL a MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
