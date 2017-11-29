---
title: "Obory názvů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ea5292d20aebdb27da726b0076179fb64631e5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-entity-sql"></a>Obory názvů (entita SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]představuje obory názvů, aby nedocházelo ke konfliktům název pro globální identifikátory například názvy typů, sady entit, funkce a tak dále. Podpora oboru názvů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je podobná podpora oboru názvů v [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje dvě formy v klauzuli USING: kvalifikovaný obory názvů (kde alias kratší je zadáno pro obor názvů) a nekvalifikované obory názvů, jak je znázorněno v následujícím příkladu:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Název pravidla překladu  
 Pokud v místní obory, nelze přeložit identifikátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat název v globálních oborech (obory názvů). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poprvé pokusí o shodovat s identifikátorem (předpona) s jedním z kvalifikovaný obory názvů. Pokud není nalezena shoda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zkusí vyřešit zbytek identifikátoru v určeném oboru názvů. Pokud není nalezena žádná shoda, je vyvolána výjimka.  
  
 Dále [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat všechny neúplné obory názvů (zadané v prologu) pro identifikátor. Pokud identifikátor může být umístěno v přesně jeden obor názvů, je vrácena tohoto umístění. Pokud má více než jeden obor názvů shody pro tento identifikátor, je vyvolána výjimka. Pokud žádný obor názvů může identifikovat pro identifikátor, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předává název na další pasivním rozsahu ( <xref:System.Data.Common.DbCommand> nebo <xref:System.Data.Common.DbConnection> objektu), jak je popsáno v následujícím příkladu:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Rozdíl oproti rozhraní .NET Framework  
 V [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], můžete použít částečně kvalifikovaný obory názvů. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]neumožňuje to.  
  
## <a name="adonet-usage"></a>Použití technologie ADO.NET  
 Dotazy jsou vyjádřit pomocí ADO.NET <xref:System.Data.Common.DbCommand> objekty. <xref:System.Data.Common.DbCommand>objekty se dají vytvářet přes <xref:System.Data.Common.DbConnection> objekty. Obory názvů, můžete také zadat jako součást <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbConnection> objekty. Pokud [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nelze přeložit identifikátor v samotném dotazu jsou zjištěný externí obory názvů (podle pravidla podobné).  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
