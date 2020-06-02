---
title: Příkazy a parametry
description: Naučte se používat objekty příkazů pro každého poskytovatele .NET Framework dat ke spouštění příkazů a vracení výsledků ze zdroje dat.
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: c0baec4d6c3984cb50178c3aa7f9ed3878055bb6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287139"
---
# <a name="commands-and-parameters"></a>Příkazy a parametry
Po navázání připojení ke zdroji dat můžete provádět příkazy a vracet výsledky ze zdroje dat pomocí <xref:System.Data.Common.DbCommand> objektu. Můžete vytvořit příkaz pomocí jednoho z konstruktorů příkazu pro poskytovatele .NET Framework dat, se kterým pracujete. Konstruktory mohou mít volitelné argumenty, jako je například příkaz jazyka SQL, který má být spuštěn ve zdroji dat, <xref:System.Data.Common.DbConnection> objektu nebo <xref:System.Data.Common.DbTransaction> objektu. Tyto objekty můžete také nakonfigurovat jako vlastnosti příkazu. Můžete také vytvořit příkaz pro konkrétní připojení pomocí <xref:System.Data.Common.DbConnection.CreateCommand%2A> metody `DbConnection` objektu. Příkazy jazyka SQL spouštěné příkazem lze konfigurovat pomocí <xref:System.Data.Common.DbCommand.CommandText%2A> Vlastnosti.  
  
 Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, obsahuje `Command` objekt. Zprostředkovatel dat .NET Framework pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbCommand> objekt, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlCommand> objekt, .NET Framework Zprostředkovatel dat pro rozhraní ODBC zahrnuje objekt a .NET Framework Zprostředkovatel dat <xref:System.Data.Odbc.OdbcCommand> pro Oracle obsahuje objekt <xref:System.Data.OracleClient.OracleCommand> .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spuštění příkazu](executing-a-command.md)  
 Popisuje objekt ADO.NET `Command` a jeho použití ke spouštění dotazů a příkazů pro zdroj dat.  
  
 [Konfigurace parametrů a datové typy parametrů](configuring-parameters-and-parameter-data-types.md)  
 Popisuje práci s `Command` parametry, včetně směrů, datových typů a syntaxe parametrů.  
  
 [Generování příkazů s CommandBuilders](generating-commands-with-commandbuilders.md)  
 Popisuje, jak používat sestavovatele příkazů k automatickému generování příkazů INSERT, UPDATE a DELETE pro objekt `DataAdapter` , který má příkaz pro výběr s jednou tabulkou.  
  
 [Získání jedné hodnoty z databáze](obtaining-a-single-value-from-a-database.md)  
 Popisuje způsob použití `ExecuteScalar` metody `Command` objektu pro vrácení jedné hodnoty z databázového dotazu.  
  
 [Použití příkazů pro změny dat](using-commands-to-modify-data.md)  
 Popisuje, jak použít poskytovatele dat ke spouštění uložených procedur nebo příkazů DDL (Data Definition Language).  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Přehled ADO.NET](ado-net-overview.md)
