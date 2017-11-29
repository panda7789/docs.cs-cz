---
title: "Úprava dat pomocí uložené procedury"
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
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f8f0c37e5ac84d878f1d443d2bcc1e8ded099a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-data-with-stored-procedures"></a>Úprava dat pomocí uložené procedury
Uložené procedury lze přijímat data jako vstupní parametry a vrací data jako výstupní parametry, sad výsledků dotazu nebo návratové hodnoty. Následující ukázka ukazuje, jak ADO.NET odesílá a přijímá vstupní parametry, výstupní parametry a návratové hodnoty. V příkladu vloží nového záznamu do tabulky, kde sloupec primárního klíče je sloupec identity v databázi systému SQL Server.  
  
> [!NOTE]
>  Pokud chcete upravit nebo odstranit data pomocí používáte uložené procedury SQL serveru <xref:System.Data.SqlClient.SqlDataAdapter>, ujistěte se, nepoužívejte SET NOCOUNT ON v definici uložené procedury. To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako konflikt souběžnosti. V takovém případě <xref:System.Data.DBConcurrencyException> bude vyvolána.  
  
## <a name="example"></a>Příklad  
 Ukázka používá následující uložené procedury vložit novou kategorii do **Northwind** **kategorie** tabulky. Uložená procedura přebírá hodnotu **CategoryName** sloupec jako vstupní parametr a používá SCOPE_IDENTITY() funkci, aby se nová hodnota pole identity načíst **CategoryID**a obnoví v něm výstupní parametr. Příkaz RETURN používá @@ROWCOUNT funkce, která se vrátí počet vložené řádky.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Následující příklad kódu používá `InsertCategory` uložené procedury výše uvedeném jako zdroj pro <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Výstupní parametr, se projeví ve <xref:System.Data.DataSet> po záznamu byla vložena do databáze při `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter> je volána. Kód také načte návratovou hodnotu.  
  
> [!NOTE]
>  Při použití <xref:System.Data.OleDb.OleDbDataAdapter>, je nutné zadat parametry s <xref:System.Data.ParameterDirection> z **ReturnValue** před jinými parametry.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [DataAdapters a DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Spouštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
