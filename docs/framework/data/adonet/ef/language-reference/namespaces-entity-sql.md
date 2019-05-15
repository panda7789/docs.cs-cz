---
title: Obory názvů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7bcd7a72df8afbd598a15ccd9a259ed11b5b9ef7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583822"
---
# <a name="namespaces-entity-sql"></a>Obory názvů (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zavádí obory názvů, aby nedocházelo ke konfliktům název pro globální identifikátory, jako jsou názvy typů, sad entit, funkce a tak dále. Podpora oboru názvů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je podobný podpora oboru názvů v rozhraní .NET Framework.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje dvě formy klauzuli USING: kvalifikovaný obory názvů (kdy kratší alias je zadáno pro obor názvů) a nekvalifikované obory názvů, jak je znázorněno v následujícím příkladu:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Název pravidla překladu  
 Pokud v místní obory, nelze přeložit identifikátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí se najít název v globální obory (obory názvů). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Nejprve se pokusí shodovat s identifikátorem (předpona) s jedním kvalifikovaný oborů názvů. Pokud není nalezena shoda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí přeložit zbývající části identifikátoru v určeném oboru názvů. Pokud není nalezena žádná shoda, je vyvolána výjimka.  
  
 Dále [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat všechny nekvalifikované obory názvů (zadané v prologu) pro identifikátor. Pokud identifikátor lze umístit do přesně jeden obor názvů, je vrácena tohoto umístění. Pokud je nalezena shoda s tímto identifikátorem více než jeden obor názvů, je vyvolána výjimka. Pokud pro identifikátor, lze identifikovat žádný obor názvů [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předá do další pasivního oboru názvu ( <xref:System.Data.Common.DbCommand> nebo <xref:System.Data.Common.DbConnection> objektu), jak je znázorněno v následujícím příkladu:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Rozdíly v rozhraní .NET Framework  
 V rozhraní .NET Framework můžete použít částečně kvalifikované obory názvů. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] neumožňuje to.  
  
## <a name="adonet-usage"></a>Používání ADO.NET  
 Dotazy jsou vyjádřeny pomocí ADO.NET <xref:System.Data.Common.DbCommand> objekty. <xref:System.Data.Common.DbCommand> objekty mohou být vytvořeny prostřednictvím <xref:System.Data.Common.DbConnection> objekty. Obory názvů lze také zadat jako součást <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbConnection> objekty. Pokud [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nelze přeložit identifikátor v samotném dotazu jsou vystavovány externí oborů názvů (v závislosti na podobné pravidla).  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
