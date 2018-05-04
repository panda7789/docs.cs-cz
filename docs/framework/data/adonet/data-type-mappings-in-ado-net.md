---
title: Mapování datového typu v technologii ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 1064f3be7f2548337b5dd6653c76b70a04fad980
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-mappings-in-adonet"></a>Mapování datového typu v technologii ADO.NET
Rozhraní .NET Framework je založena na obecný systém typů, který definuje, jak jsou typy deklarovat, používat a spravovat v modulu runtime. Obsahuje typy hodnot a odkazové typy, které jsou odvozeny od <xref:System.Object> základní typ. Při práci se zdrojem dat, je datový typ odvodit z poskytovatele dat, pokud není explicitně zadané. Například <xref:System.Data.DataSet> je nezávislý na libovolný zdroj dat pro konkrétní objekt. Data v `DataSet` se načítají ze zdroje dat a zachováním změn zpět do zdroje dat pomocí `DataAdapter`. To znamená, že pokud `DataAdapter` doplní <xref:System.Data.DataTable> v `DataSet` s hodnotami ze zdroje dat, výsledné datové typy sloupce v `DataTable` jsou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy místo typy, které jsou specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat Zprostředkovatel, který se používá k připojení ke zdroji dat.  
  
 Podobně když `DataReader` vrátí hodnotu ze zdroje dat, výsledná hodnota je uložen v místní proměnné, která má [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Pro oba `Fill` operace `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen z hodnota vrácená z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat.  
  
 Aniž byste museli spoléhat na odvozené datový typ, můžete použít metody typu přístupového objektu `DataReader` Pokud znáte konkrétní typ hodnoty nebyl vrácen. Typové přístupových metod získáte lepší výkon a vrátila hodnotu jako konkrétní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu, který eliminuje potřebu další typ převodu.  
  
> [!NOTE]
>  Hodnoty Null [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele datové typy jsou reprezentované pomocí `DBNull.Value`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů SQL Serveru](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.SqlClient>.  
  
 [Mapování datových typů OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.OleDb>.  
  
 [Mapování datových typů ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.Odbc>.  
  
 [Mapování datových typů Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.OracleClient>.  
  
 [Čísla s plovoucí desetinnou čárkou](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Popisuje problémy, které vývojáři často nastat při práci s plovoucí desetinnou čárkou.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy SQL Serveru a ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Konfigurace parametrů a datové typy parametrů](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Obecný systém typů](../../../../docs/standard/base-types/common-type-system.md)  
 [Převádění typů](http://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
