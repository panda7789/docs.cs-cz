---
title: DbConnection, DbCommand a DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 09526f111adeecb817ce4c4e587ca3713e0d8cde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785198"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand a DbException
Po vytvoření <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection>a a pak můžete pracovat s příkazy a čtenáři dat a načíst data ze zdroje dat.  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Tento příklad přijímá `DbConnection` objekt jako argument. Vytvoří <xref:System.Data.Common.DbCommand> se, pokud chcete vybrat data z tabulky Categories <xref:System.Data.Common.DbCommand.CommandText%2A> nastavením příkazu na příkaz SQL SELECT. Kód předpokládá, že tabulka Categories existuje ve zdroji dat. Připojení je otevřeno a data jsou načtena pomocí <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Spuštění příkladu příkazu  
 Tento příklad přijímá `DbConnection` objekt jako argument. Pokud je platný, připojení se otevře <xref:System.Data.Common.DbCommand> a vytvoří se a spustí se. `DbConnection` <xref:System.Data.Common.DbCommand.CommandText%2A> Je nastaven na příkaz SQL INSERT, který provede vložení do tabulky Categories v databázi Northwind. Kód předpokládá, že databáze Northwind existuje ve zdroji dat a že syntaxe SQL použitá v příkazu INSERT je platná pro zadaného zprostředkovatele. Chyby, ke kterým došlo na zdroji dat, jsou zpracovávány <xref:System.Data.Common.DbException> blokem kódu a všechny ostatní výjimky jsou zpracovávány <xref:System.Exception> v bloku.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Zpracování chyb dat pomocí DbException  
 <xref:System.Data.Common.DbException> Třída je základní třída pro všechny výjimky vyvolané jménem zdroje dat. Můžete ji použít v kódu zpracování výjimek pro zpracování výjimek vyvolaných různými zprostředkovateli bez nutnosti odkazování na konkrétní třídu výjimky. Následující fragment kódu ukazuje, <xref:System.Data.Common.DbException> jak použít k zobrazení informací o chybách vrácených zdrojem dat pomocí <xref:System.Exception.GetType%2A>vlastností, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>a <xref:System.Exception.Message%2A> . Ve výstupu se zobrazí typ chyby, zdroj označující název zprostředkovatele, kód chyby a zprávu spojenou s chybou.  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [DbProviderFactories](dbproviderfactories.md)
- [Získání DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [Úpravy dat přes DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Přehled ADO.NET](ado-net-overview.md)
