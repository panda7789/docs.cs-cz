---
title: Mapování datového typu
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 610cdc1a679b0c51125075076120e12db97da421
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980194"
---
# <a name="data-type-mappings-in-adonet"></a>Mapování datového typu v ADO.NET
.NET Framework je založena na společném systému typů, který definuje, jakým způsobem jsou typy deklarovány, používány a spravovány v modulu runtime. Skládá se z obou typů hodnot a odkazů, které jsou odvozeny od základního typu <xref:System.Object>. Při práci se zdrojem dat je datový typ odvozen od poskytovatele dat, pokud není explicitně zadán. Například objekt <xref:System.Data.DataSet> je nezávislý na konkrétním zdroji dat. Data ve `DataSet` jsou načtena ze zdroje dat a změny jsou uchovány zpět do zdroje dat pomocí `DataAdapter`. To znamená, že když `DataAdapter` vyplní <xref:System.Data.DataTable> v `DataSet` s hodnotami ze zdroje dat, výsledné datové typy sloupců v `DataTable` jsou .NET Framework typy namísto typů specifických pro poskytovatele .NET Framework dat, který se používá pro připojení ke zdroji dat.  
  
 Podobně pokud `DataReader` vrátí hodnotu ze zdroje dat, výsledná hodnota je uložena v místní proměnné, která má typ .NET Framework. Pro `Fill` operace `DataAdapter` a `Get` metody `DataReader`je typ .NET Framework odvozen z hodnoty vrácené poskytovatelem dat .NET Framework.  
  
 Místo spoléhání na odvozený datový typ můžete použít metody přístupového objektu `DataReader`, když znáte konkrétní typ vracené hodnoty. Typové přístupové metody poskytují lepší výkon tím, že vrací hodnotu jako konkrétní typ .NET Framework, což eliminuje nutnost dalšího převodu typu.  
  
> [!NOTE]
> Hodnoty null pro .NET Framework datové typy zprostředkovatele dat jsou reprezentovány `DBNull.Value`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů SQL Serveru](sql-server-data-type-mappings.md)  
 Vypíše mapování odvozených datových typů a metody přístup k datům pro <xref:System.Data.SqlClient>.  
  
 [Mapování datových typů OLE DB](ole-db-data-type-mappings.md)  
 Vypíše mapování odvozených datových typů a metody přístup k datům pro <xref:System.Data.OleDb>.  
  
 [Mapování datových typů ODBC](odbc-data-type-mappings.md)  
 Vypíše mapování odvozených datových typů a metody přístup k datům pro <xref:System.Data.Odbc>.  
  
 [Mapování datových typů Oracle](oracle-data-type-mappings.md)  
 Vypíše mapování odvozených datových typů a metody přístup k datům pro <xref:System.Data.OracleClient>.  
  
 [Čísla s plovoucí desetinnou čárkou](floating-point-numbers.md)  
 Popisuje problémy, se kterými se vývojáři často setkávají při práci s čísly s plovoucí desetinnou čárkou.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy SQL Serveru a ADO.NET](./sql/sql-server-data-types.md)
- [Konfigurace parametrů a datové typy parametrů](configuring-parameters-and-parameter-data-types.md)
- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Obecný systém typů](../../../standard/base-types/common-type-system.md)
- [Převádění typů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Přehled ADO.NET](ado-net-overview.md)
