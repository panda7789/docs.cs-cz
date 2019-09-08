---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784099"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
Obor názvů poskytuje třídy pro vytváření <xref:System.Data.Common.DbProviderFactory> instancí pro práci s konkrétními zdroji dat. <xref:System.Data.Common> Když vytvoříte <xref:System.Data.Common.DbProviderFactory> instanci a předáte informace o poskytovateli dat `DbProviderFactory` , může určit správný objekt připojení silného typu, který se bude vracet na základě informací, které byly poskytnuty.  
  
 Od .NET Framework verze 4 nejsou <xref:System.Data.Odbc>poskytovatelé dat <xref:System.Data.SqlClient>, jako jsou, <xref:System.Data.OleDb>, a <xref:System.Data.OracleClient> , již v souboru Machine. config uvedeny, ale vlastní zprostředkovatelé budou dále uvedeni v seznamu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu objektu pro vytváření](factory-model-overview.md)  
 Poskytuje přehled vzoru návrhu a programovacího rozhraní pro vytváření.  
  
 [Získání DbProviderFactory](obtaining-a-dbproviderfactory.md)  
 Ukazuje, jak zobrazit seznam nainstalovaných zprostředkovatelů dat a <xref:System.Data.Common.DbConnection> vytvořit `DbProviderFactory`z.  
  
 [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)  
 Ukazuje, jak vytvořit <xref:System.Data.Common.DbCommand> a a <xref:System.Data.Common.DbDataReader>jak zpracovávat chyby dat pomocí. <xref:System.Data.Common.DbException>  
  
 [Úpravy dat přes DbDataAdapter](modifying-data-with-a-dbdataadapter.md)  
 Ukazuje, jak použít <xref:System.Data.Common.DbCommandBuilder> <xref:System.Data.Common.DbDataAdapter> s a k načtení a úpravě dat.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
