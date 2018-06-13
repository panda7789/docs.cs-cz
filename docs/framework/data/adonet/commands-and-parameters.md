---
title: Příkazy a parametry
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 3634ce97ba162d59e39d273418b9a13217b9ddff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757148"
---
# <a name="commands-and-parameters"></a>Příkazy a parametry
Po navázání připojení ke zdroji dat, můžete provést příkazy a vrácení výsledků z zdroje dat pomocí <xref:System.Data.Common.DbCommand> objektu. Můžete vytvořit příkaz pomocí některé z konstruktorů příkaz zprostředkovatel dat .NET Framework, které pracujete. Konstruktory může trvat volitelné argumenty, jako je například příkazu SQL k provedení ve zdroji dat <xref:System.Data.Common.DbConnection> objekt, nebo <xref:System.Data.Common.DbTransaction> objektu. Tyto objekty můžete také nakonfigurovat jako vlastnosti příkazu. Můžete také vytvořit příkaz pro konkrétní připojení pomocí <xref:System.Data.Common.DbConnection.CreateCommand%2A> metodu `DbConnection` objektu. Příkaz jazyka SQL, který je vykonáván příkaz můžete nakonfigurovat pomocí <xref:System.Data.Common.DbCommand.CommandText%2A> vlastnost.  
  
 Má každý zprostředkovatel dat .NET Framework je součástí rozhraní .NET Framework `Command` objektu. Zahrnuje zprostředkovatel dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro ODBC <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)  
 Popisuje technologie ADO.NET `Command` objekt a způsobu jeho použití k provedení dotazy a příkazy pro datový zdroj.  
  
 [Konfigurace parametrů a datové typy parametrů](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 Popisuje práci s `Command` parametry, včetně směr, datové typy a syntaxe parametru.  
  
 [Generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 Popisuje, jak používat příkaz počítačů k automatickému generování příkazy INSERT, UPDATE a DELETE pro `DataAdapter` má vyberte příkaz jedné tabulky.  
  
 [Získání jedné hodnoty z databáze](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 Popisuje postup použití `ExecuteScalar` metodu `Command` objekt, který chcete vrátit jednu hodnotu z dotazu databáze.  
  
 [Použití příkazů pro změny dat](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 Popisuje postup použití zprostředkovatele dat pro spuštění uložené procedury nebo data (příkazy DDL definition language).  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
