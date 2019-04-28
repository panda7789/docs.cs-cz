---
title: DbConnection, DbCommand a DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 759b2f36f9d38cdac0cfe4ff8e451b38012493e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607242"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand a DbException
Jakmile vytvoříte <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection>, pak můžete pracovat s příkazy a čtečky dat. k načtení dat z datového zdroje.  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Tento příklad používá `DbConnection` objektu jako argument. A <xref:System.Data.Common.DbCommand> se vytvoří vyberte data z tabulky Kategorie nastavením <xref:System.Data.Common.DbCommand.CommandText%2A> na příkazu SQL SELECT. Kód předpokládá, že existuje kategorie tabulky ve zdroji dat. Otevření připojení a data jsou načítány s použitím <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Provedení příkazu příklad  
 Tento příklad používá `DbConnection` objektu jako argument. Pokud `DbConnection` je platný, je otevřeno připojení a <xref:System.Data.Common.DbCommand> je vytvořen a spuštěn. <xref:System.Data.Common.DbCommand.CommandText%2A> Je nastavena na příkazu INSERT jazyka SQL, který provádí vložení do kategorií tabulky v databázi Northwind. Kód předpokládá, že databáze Northwind existuje ve zdroji dat a syntaxe SQL v příkazu INSERT je platný pro zadaného zprostředkovatele. Zpracovává chyby, ke kterým dochází ve zdroji dat <xref:System.Data.Common.DbException> blok kódu a všechny ostatní výjimky jsou zpracovány v <xref:System.Exception> bloku.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Zpracování chyb Data s DbException  
 <xref:System.Data.Common.DbException> Třída je základní třída pro všechny výjimky vyvolané jménem zdroji dat. Vám pomůže ho v váš kód zpracování výjimek zpracování výjimek vyvolaných různí poskytovatelé, aniž byste museli reference – třída výjimky. Následující fragment kódu ukazuje, jak používat <xref:System.Data.Common.DbException> zobrazíte informace o chybách vrácených ve zdroji dat pomocí <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, a <xref:System.Exception.Message%2A> vlastnosti. Ve výstupu se zobrazí typ chyby, zdrojový označující název zprostředkovatele, kód chyby a zprávy související s chybou.  
  
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

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
