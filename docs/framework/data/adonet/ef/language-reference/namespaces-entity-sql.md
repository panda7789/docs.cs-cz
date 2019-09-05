---
title: Obory názvů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 395ffb23859be27b4897dfc352f6e44d52286b26
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249985"
---
# <a name="namespaces-entity-sql"></a>Obory názvů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zavádí obory názvů, aby se zabránilo konfliktům názvů u globálních identifikátorů, jako jsou názvy typů, sady entit, funkce a tak dále. Podpora oboru názvů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroji je podobná podpoře oboru názvů v .NET Framework.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje dva formy klauzule USING: kvalifikované obory názvů (kde je k dispozici kratší alias pro obor názvů) a nekvalifikované obory názvů, jak je znázorněno v následujícím příkladu:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Pravidla překladu názvů  
 Pokud identifikátor nelze přeložit v místních oborech, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroj se pokusí najít název v globálním oboru (obory názvů). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Nejprve se pokusí porovnat identifikátor (předponu) s jedním z kvalifikovaných oborů názvů. Pokud existuje shoda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí se přeložit zbytek identifikátoru v zadaném oboru názvů. Pokud není nalezena žádná shoda, je vyvolána výjimka.  
  
 V dalším kroku se pokusívyhledatvšechnynekvalifikovanéoborynázvů(zadanévprologu)proidentifikátor.[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Pokud identifikátor může být umístěn v přesně jednom oboru názvů, toto umístění je vráceno. Pokud má více než jeden obor názvů shodu pro tento identifikátor, je vyvolána výjimka. Pokud pro identifikátor není možné identifikovat obor názvů, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předává název do dalšího vnějšího oboru <xref:System.Data.Common.DbCommand> (objekt nebo <xref:System.Data.Common.DbConnection> ), jak je znázorněno v následujícím příkladu:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Rozdíly mezi .NET Framework  
 V .NET Framework můžete použít částečně kvalifikované obory názvů. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]to nepovoluje.  
  
## <a name="adonet-usage"></a>Využití ADO.NET  
 Dotazy jsou vyjádřeny prostřednictvím <xref:System.Data.Common.DbCommand> objektů ADO.NET. <xref:System.Data.Common.DbCommand>objekty mohou být sestaveny <xref:System.Data.Common.DbConnection> objekty. Obory názvů lze také zadat jako součást <xref:System.Data.Common.DbCommand> objektů a. <xref:System.Data.Common.DbConnection> Pokud [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nelze vyřešit identifikátor v rámci samotného dotazu, externí obory názvů jsou zjišťovány (na základě podobných pravidel).  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
