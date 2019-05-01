---
title: Systém typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0afeffd3ad180d6cc6175010140754e279988b38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034099"
---
# <a name="type-system-entity-sql"></a>Systém typů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje několik typů:  
  
- (Jednoduchý) primitivní typy, jako `Int32` a `String.`  
  
- Nominální typy, které jsou definovány ve schématu, jako například <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, a <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Anonymní typy, které nejsou explicitně definovány ve schématu: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, a <xref:System.Data.Metadata.Edm.RefType>.  
  
 Tato část popisuje anonymní typy, které nejsou explicitně definovány ve schématu však není podporovaná Entity SQL. Informace o typech primitivní a nominální najdete v tématu [koncepční Model typy (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Řádky  
 Struktura řádek závisí na pořadí zadaném a pojmenované členy, které se skládá z řádku. Typ řádku nemá žádná identita a nejde ji zdědit z. Instance stejného typu řádku jsou rovnocenné, pokud jsou v uvedeném pořadí ekvivalentních členy. Řádky mít žádné chování, mimo jejich ekvivalence strukturální a nemají žádný ekvivalent v modulu common language runtime. Struktury obsahující řádky nebo kolekce řádků může způsobit dotazů. Rozhraní API vazby mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy a jazyk hostitelského definuje, jak jsou realizované řádků v dotazu, který vytváří výsledek. Informace o tom, jak vytvořit instanci řádku najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekce  
 Typy kolekce představují nula nebo víc instancí jiné objekty. Informace o tom, jak vytvořit kolekci, najdete v části [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odkazy  
 Odkaz je logický ukazatel na konkrétní entitu v sadě konkrétní entity.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje následující operátory sestavit, dekonstruovat a procházejte odkazy:  
  
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 Odkaz můžete procházet pomocí operátoru přístupu (tečka) člena (`.`). Následující fragment kódu extrahuje Vlastnost Id (pořadí) tak, že přejdete prostřednictvím vlastnosti r (odkaz).  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Pokud je hodnota odkaz null nebo cílem odkazu ještě neexistuje, výsledek je null.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [Specifikace CSDL, SSDL a MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
