---
title: Mapování datového typu v ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 9c0d19f724c1876f7dac86055bed2ef77ac76a77
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785599"
---
# <a name="data-type-mappings-in-adonet"></a>Mapování datového typu v ADO.NET
.NET Framework je založena na společném systému typů, který definuje, jakým způsobem jsou typy deklarovány, používány a spravovány v modulu runtime. Skládá se z obou typů hodnot a odkazů, které jsou odvozeny ze <xref:System.Object> základního typu. Při práci se zdrojem dat je datový typ odvozen od poskytovatele dat, pokud není explicitně zadán. Například <xref:System.Data.DataSet> objekt je nezávislý na konkrétním zdroji dat. Data v `DataSet` nástroji jsou načtena ze zdroje dat a změny jsou uchovány zpět do zdroje dat `DataAdapter`pomocí. To znamená, že pokud `DataAdapter` <xref:System.Data.DataTable> v `DataSet` případě, že naplní hodnoty ze zdroje dat, budou `DataTable` výsledné datové typy sloupců v .NET Framework typy, nikoli typy specifické pro .NET Frameworkho poskytovatele dat, který slouží k připojení ke zdroji dat.  
  
 Podobně pokud `DataReader` vrátí hodnotu ze zdroje dat, výsledná hodnota je uložena v místní proměnné, která má typ .NET Framework. `Fill` Pro operace `DataAdapter` a`Get` metod ,jetyp.NETFrameworkodvozenzhodnotyvrácenéposkytovatelemdat.NETFramework.`DataReader`  
  
 Namísto spoléhání na odvozený datový typ můžete použít metody `DataReader` přístupového objektu, když znáte konkrétní typ vracené hodnoty. Typové přístupové metody poskytují lepší výkon tím, že vrací hodnotu jako konkrétní typ .NET Framework, což eliminuje nutnost dalšího převodu typu.  
  
> [!NOTE]
> Hodnoty null pro .NET Framework datové typy zprostředkovatele dat jsou reprezentovány `DBNull.Value`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů SQL Serveru](sql-server-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.SqlClient>pro.  
  
 [Mapování datových typů OLE DB](ole-db-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.OleDb>pro.  
  
 [Mapování datových typů ODBC](odbc-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.Odbc>pro.  
  
 [Mapování datových typů Oracle](oracle-data-type-mappings.md)  
 Seznam odvozených mapování datových typů a metod přistupujících dat <xref:System.Data.OracleClient>pro.  
  
 [Čísla s plovoucí desetinnou čárkou](floating-point-numbers.md)  
 Popisuje problémy, se kterými se vývojáři často setkávají při práci s čísly s plovoucí desetinnou čárkou.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy SQL Serveru a ADO.NET](./sql/sql-server-data-types.md)
- [Konfigurace parametrů a datové typy parametrů](configuring-parameters-and-parameter-data-types.md)
- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Obecný systém typů](../../../standard/base-types/common-type-system.md)
- [Převádění typů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Přehled ADO.NET](ado-net-overview.md)
