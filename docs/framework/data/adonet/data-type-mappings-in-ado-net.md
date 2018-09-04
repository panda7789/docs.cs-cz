---
title: Mapování datového typu v ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: aba1eb4fdaaf43d66337ca764fe01b7d3f4624bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516924"
---
# <a name="data-type-mappings-in-adonet"></a>Mapování datového typu v ADO.NET
Rozhraní .NET Framework podle systému společných typů, která definuje, jak jsou typy deklarovány, použití a spravovány v modulu runtime. Skládá se z hodnotové typy a typy odkazů, které jsou odvozeny z <xref:System.Object> základní typ. Při práci se zdrojem dat, datový typ je odvozen od poskytovatele dat. Pokud nebyl explicitně zadán. Například <xref:System.Data.DataSet> je nezávislý na libovolný zdroj dat pro konkrétní objekt. Data v `DataSet` načíst ze zdroje dat, a změny jsou trvalé zpět do zdroje dat s využitím `DataAdapter`. To znamená, že `DataAdapter` vyplní <xref:System.Data.DataTable> v `DataSet` s hodnotami ze zdroje dat, výsledné datové typy sloupců v `DataTable` jsou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typů, aniž specifické pro typy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat Zprostředkovatel, který se používá k připojení ke zdroji dat.  
  
 Podobně, když `DataReader` vrátí hodnotu ze zdroje dat, výsledná hodnota uložená v místní proměnné, která má [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Pro obě `Fill` operace `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen od hodnoty vrácené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb.  
  
 Aniž byste museli spoléhat na odvozené datový typ, můžete použít zadaný přístupové metody `DataReader` Pokud znáte konkrétní typ vracené hodnoty. Zadaný přístupové metody získáte lepší výkon tak, že vrací hodnotu jako konkrétní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ, který eliminuje potřebu dalších převodů.  
  
> [!NOTE]
>  Hodnoty pro Null [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data zprostředkovatele datové typy jsou reprezentovány `DBNull.Value`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů SQL Serveru](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Seznamy odvodit mapování datových typů a data přístupové metody pro <xref:System.Data.SqlClient>.  
  
 [Mapování datových typů OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Seznamy odvodit mapování datových typů a data přístupové metody pro <xref:System.Data.OleDb>.  
  
 [Mapování datových typů ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Seznamy odvodit mapování datových typů a data přístupové metody pro <xref:System.Data.Odbc>.  
  
 [Mapování datových typů Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Seznamy odvodit mapování datových typů a data přístupové metody pro <xref:System.Data.OracleClient>.  
  
 [Čísla s plovoucí desetinnou čárkou](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Popisuje problémy, které vývojáři často narazit při práci s čísly s plovoucí desetinnou čárkou.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy SQL Serveru a ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Konfigurace parametrů a datové typy parametrů](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Obecný systém typů](../../../../docs/standard/base-types/common-type-system.md)  
 [Převádění typů](https://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
