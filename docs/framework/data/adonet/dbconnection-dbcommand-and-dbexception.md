---
title: "Připojení DbConnection, DbCommand a dbexception –"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6fb5783ad8d0863ffcce0665795081c6f2041d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>Připojení DbConnection, DbCommand a dbexception –
Po vytvoření <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection>, pak můžete pracovat s příkazy a čtečky dat. k načtení dat ze zdroje dat.  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Tento příklad zpracuje `DbConnection` objektu jako argument. A <xref:System.Data.Common.DbCommand> se vytvoří pro výběr data z tabulky kategorie podle nastavení <xref:System.Data.Common.DbCommand.CommandText%2A> do příkazu SQL SELECT. Kód předpokládá, že v tabulce kategorie existuje ve zdroji dat. Připojení je otevřít a data se načítají pomocí <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Provádění příkazu příklad  
 Tento příklad zpracuje `DbConnection` objektu jako argument. Pokud `DbConnection` je platný, je-li otevřít připojení a <xref:System.Data.Common.DbCommand> se vytvoří a provést. <xref:System.Data.Common.DbCommand.CommandText%2A> Je nastaven na příkazu INSERT jazyka SQL, který provádí typu vložení do kategorií tabulky v databázi Northwind. Kód předpokládá, že databáze Northwind existuje ve zdroji dat, a zda je platná pro zadaného zprostředkovatele syntaxe SQL použít v příkazu INSERT. Chyby, ke kterým dochází ve zdroji dat jsou zpracovávány <xref:System.Data.Common.DbException> blok kódu a všechny ostatní výjimky jsou zpracovávány v <xref:System.Exception> bloku.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Zpracování chyb dat s dbexception –  
 <xref:System.Data.Common.DbException> Třída je základní třída pro všechny výjimky vydané jménem zdroj dat. Můžete ji použít ve vašem kódu pro zpracování výjimek pro zpracování výjimky vyvolané různé zprostředkovatele bez nutnosti referenční třídy konkrétní výjimek. Následující fragment kódu ukazuje, jak používat <xref:System.Data.Common.DbException> zobrazíte informace o chybě vrácený zdroje dat pomocí <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, a <xref:System.Exception.Message%2A> vlastnosti. Výstup se zobrazí typ chyby, zdroj označující název zprostředkovatele, kód chyby a zpráva přidružená k chybě.  
  
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
  
## <a name="see-also"></a>Viz také  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [Úprava dat s DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
