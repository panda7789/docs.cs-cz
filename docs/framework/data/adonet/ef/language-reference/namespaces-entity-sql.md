---
title: Obory názvů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7f05067c4bdb859f3661f775c2502852b6658522
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319564"
---
# <a name="namespaces-entity-sql"></a>Obory názvů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zavádí obory názvů, aby nedocházelo ke konfliktům názvů pro globální identifikátory, jako jsou názvy typů, sady entit, funkce a tak dále. Podpora oboru názvů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je podobná podpoře oboru názvů v .NET Framework.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje dva formuláře klauzule USING: kvalifikované obory názvů (kde je k dispozici kratší alias pro obor názvů) a nekvalifikované obory názvů, jak je znázorněno v následujícím příkladu:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Pravidla překladu názvů  
 Pokud identifikátor nelze přeložit v místních oborech, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí najít název v globálním oboru (obory názvů). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se nejprve pokusí porovnat identifikátor (předponu) s jedním z kvalifikovaných oborů názvů. Pokud existuje shoda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí přeložit zbytek identifikátoru v určeném oboru názvů. Pokud není nalezena žádná shoda, je vyvolána výjimka.  
  
 V dalším kroku se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat všechny nekvalifikované obory názvů (zadané v prologu) pro identifikátor. Pokud identifikátor může být umístěn v přesně jednom oboru názvů, toto umístění je vráceno. Pokud má více než jeden obor názvů shodu pro tento identifikátor, je vyvolána výjimka. Pokud není možné identifikovat obor názvů pro identifikátor, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předá název do dalšího vnějšího oboru (objekt <xref:System.Data.Common.DbCommand> nebo <xref:System.Data.Common.DbConnection>), jak je znázorněno v následujícím příkladu:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Rozdíly mezi .NET Framework  
 V .NET Framework můžete použít částečně kvalifikované obory názvů. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to nepovoluje.  
  
## <a name="adonet-usage"></a>Využití ADO.NET  
 Dotazy jsou vyjádřeny prostřednictvím objektů ADO.NET <xref:System.Data.Common.DbCommand>. objekty <xref:System.Data.Common.DbCommand> lze vytvořit pomocí objektů <xref:System.Data.Common.DbConnection>. Obory názvů lze také zadat jako součást <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbConnection> objektů. Pokud [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nemůže vyřešit identifikátor v rámci samotného dotazu, externí obory názvů se sondují (na základě podobných pravidel).  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
