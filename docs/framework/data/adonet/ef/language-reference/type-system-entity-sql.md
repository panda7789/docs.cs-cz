---
title: Systém typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0f7dae9e57132929737d752c67694cd369b79d9e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319236"
---
# <a name="type-system-entity-sql"></a>Systém typů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje několik typů:  
  
- Primitivní (jednoduché) typy jako `Int32` a `String.`  
  
- Nominální typy, které jsou definovány ve schématu, například <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> a <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Anonymní typy, které nejsou definovány ve schématu explicitně: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> a <xref:System.Data.Metadata.Edm.RefType>.  
  
 Tato část popisuje anonymní typy, které nejsou explicitně definovány ve schématu, ale jsou podporovány Entity SQL. Informace o primitivních a nominálních typech naleznete v tématu [typy konceptuálních modelů (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>tabulky  
 Struktura řádku závisí na sekvenci typovaného a pojmenovaného člena, ze kterého se řádek skládá. Typ řádku nemá žádnou identitu a nedá se dědit z. Instance stejného typu řádku jsou ekvivalentní, pokud jsou členy ekvivalentní. Řádky nemají žádné chování nad jejich strukturální rovnocennost a nemají ekvivalent v modulu CLR (Common Language Runtime). Dotazy mohou mít za následek struktury, které obsahují řádky nebo kolekce řádků. Vazba rozhraní API mezi dotazy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a jazykem hostitele definuje způsob, jakým jsou řádky realizovány v dotazu, který vytvořil výsledek. Informace o tom, jak vytvořit instanci řádku, naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekce  
 Typy kolekce reprezentují nula nebo více instancí jiných objektů. Informace o tom, jak sestavit kolekci, naleznete v tématu [konstrukce typů](constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odkazy  
 Odkaz je logický ukazatel na konkrétní entitu v konkrétní sadě entit.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje následující operátory pro konstrukci, dekonstrukci a navigaci prostřednictvím odkazů:  
  
- [REF](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [KEY](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Můžete procházet odkazem pomocí operátoru přístupu ke členu (tečka) (`.`). Následující fragment kódu extrahuje vlastnost ID (z pořadí) přechodem na vlastnost r (Reference).  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Pokud má referenční hodnota hodnotu null nebo pokud cíl odkazu neexistuje, výsledek je null.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [Specifikace CSDL, SSDL a MSL](csdl-ssdl-and-msl-specifications.md)
