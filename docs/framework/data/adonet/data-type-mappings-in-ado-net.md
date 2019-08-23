---
title: Mapování datového typu v ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: ddb3c1c5551336ace66bab53af3beb83b6cd2d34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950402"
---
# <a name="data-type-mappings-in-adonet"></a>Mapování datového typu v ADO.NET
.NET Framework je založena na společném systému typů, který definuje, jakým způsobem jsou typy deklarovány, používány a spravovány v modulu runtime. Skládá se z obou typů hodnot a odkazů, které jsou odvozeny ze <xref:System.Object> základního typu. Při práci se zdrojem dat je datový typ odvozen od poskytovatele dat, pokud není explicitně zadán. Například <xref:System.Data.DataSet> objekt je nezávislý na konkrétním zdroji dat. Data v `DataSet` nástroji jsou načtena ze zdroje dat a změny jsou uchovány zpět do zdroje dat `DataAdapter`pomocí. To znamená, že pokud `DataAdapter` <xref:System.Data.DataTable> v `DataSet` případě, že naplní hodnoty ze zdroje dat, budou `DataTable` výsledné datové typy sloupců v .NET Framework typy, nikoli typy specifické pro .NET Frameworkho poskytovatele dat, který slouží k připojení ke zdroji dat.  
  
 Podobně pokud `DataReader` vrátí hodnotu ze zdroje dat, výsledná hodnota je uložena v místní proměnné, která má typ .NET Framework. `Fill` Pro operace `DataAdapter` a`Get` metod ,jetyp.NETFrameworkodvozenzhodnotyvrácenéposkytovatelemdat.NETFramework.`DataReader`  
  
 Namísto spoléhání na odvozený datový typ můžete použít metody `DataReader` přístupového objektu, když znáte konkrétní typ vracené hodnoty. Typové přístupové metody poskytují lepší výkon tím, že vrací hodnotu jako konkrétní typ .NET Framework, což eliminuje nutnost dalšího převodu typu.  
  
> [!NOTE]
> Hodnoty null pro .NET Framework datové typy zprostředkovatele dat jsou reprezentovány `DBNull.Value`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů SQL Serveru](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.SqlClient>pro.  
  
 [Mapování datových typů OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.OleDb>pro.  
  
 [Mapování datových typů ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.Odbc>pro.  
  
 [Mapování datových typů Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.OracleClient>pro.  
  
 [Čísla s plovoucí desetinnou čárkou](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Popisuje problémy, se kterými se vývojáři často setkávají při práci s čísly s plovoucí desetinnou čárkou.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy SQL Serveru a ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Konfigurace parametrů a datové typy parametrů](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [Obecný systém typů](../../../standard/base-types/common-type-system.md)
- [Převádění typů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
