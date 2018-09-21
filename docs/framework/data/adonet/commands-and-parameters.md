---
title: Příkazy a parametry
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 8e476d68b60272d944eecfe585fd77d8a7a8f08c
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46527987"
---
# <a name="commands-and-parameters"></a>Příkazy a parametry
Po navázání připojení ke zdroji dat, můžete spouštět příkazy a vracení výsledků z zdroje dat pomocí <xref:System.Data.Common.DbCommand> objektu. Můžete vytvořit příkaz pomocí jednoho z konstruktorů příkaz pro zprostředkovatele dat .NET Framework, kterou pracujete. Konstruktory může trvat volitelné argumenty, jako je například příkazu SQL ke spuštění ve zdroji dat <xref:System.Data.Common.DbConnection> objektu, nebo <xref:System.Data.Common.DbTransaction> objektu. Tyto objekty lze také nakonfigurovat jako vlastnosti příkazu. Můžete také vytvořit příkaz pro konkrétní připojení pomocí <xref:System.Data.Common.DbConnection.CreateCommand%2A> metodu `DbConnection` objektu. Příkaz jazyka SQL prováděný pomocí příkazu lze konfigurovat pomocí <xref:System.Data.Common.DbCommand.CommandText%2A> vlastnost.  
  
 Má každý zprostředkovatele dat .NET Framework je součástí rozhraní .NET Framework `Command` objektu. Obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlCommand> objektu zprostředkovatele dat .NET Framework pro ODBC zahrnuje <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)  
 Popisuje ADO.NET `Command` objekt a jak ho použít ke spuštění dotazů a příkazů proti zdroji dat.  
  
 [Konfigurace parametrů a datové typy parametrů](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 Popisuje práci s `Command` parametry, včetně směr, datových typů a syntaxe parametru.  
  
 [Generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 Popisuje, jak můžete automaticky generovat příkazy INSERT, UPDATE a DELETE pro příkaz tvůrci `DataAdapter` , který má příkazu SELECT jedné tabulky.  
  
 [Získání jedné hodnoty z databáze](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 Popisuje způsob použití `ExecuteScalar` metodu `Command` objektu, který chcete vrátit jednu hodnotu z databázového dotazu.  
  
 [Použití příkazů pro změny dat](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 Popisuje, jak zprostředkovatel dat slouží ke spuštění uložené procedury nebo data (příkazy DDL definition language).  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
