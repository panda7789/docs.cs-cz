---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 255ef115e6851b5f1d93744b54ec88990746d9cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543537"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
<xref:System.Data.Common> Obor názvů obsahuje třídy pro vytváření <xref:System.Data.Common.DbProviderFactory> instance pro práci s konkrétní zdroje. Když vytvoříte <xref:System.Data.Common.DbProviderFactory> instance a předávat informace o poskytovateli dat `DbProviderFactory` můžete určit objekt správný, silného typu připojení se vraťte na základě informací byl poskytnut.  
  
 Počínaje .NET Framework verze 4, zprostředkovatele dat, jako <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, a <xref:System.Data.OracleClient> jsou už není uvedený v souboru machine.config, ale vlastní zprostředkovatelé bude dál zobrazovat existuje.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu objektu pro vytváření](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 Poskytuje přehled vzoru návrhu objekt pro vytváření a programovací rozhraní.  
  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 Ukazuje, jak se seznam nainstalovaných dat a vytvářet <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.  
  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 Ukazuje, jak vytvořit <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbDataReader>a způsob zpracování chyb dat pomocí <xref:System.Data.Common.DbException>.  
  
 [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 Ukazuje, jak používat <xref:System.Data.Common.DbCommandBuilder> s <xref:System.Data.Common.DbDataAdapter> načtení a upravovat data.  
  
## <a name="see-also"></a>Viz také:
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
