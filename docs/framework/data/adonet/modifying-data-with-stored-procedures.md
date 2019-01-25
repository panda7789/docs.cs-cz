---
title: Úpravy dat pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 2093554eb59746d6b52c2895ec3ded5d9088fa3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658270"
---
# <a name="modifying-data-with-stored-procedures"></a>Úpravy dat pomocí uložených procedur
Uložené procedury může přijmout data jako vstupní parametry a vrací data jako výstupní parametry, sad výsledků dotazu nebo návratové hodnoty. Následující ukázka znázorňuje, jak ADO.NET odesílá a přijímá vstupní parametry, výstupních parametrů a návratové hodnoty. V příkladu vloží nového záznamu do tabulky, kde sloupec primárního klíče je sloupec identity v databázi serveru SQL Server.  
  
> [!NOTE]
>  Pokud chcete upravit nebo odstranit data s využitím používáte uložených procedur SQL serveru <xref:System.Data.SqlClient.SqlDataAdapter>, ujistěte se, že SET NOCOUNT na nepoužívejte v definici uloženou proceduru. To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako ke konfliktu souběžnosti. V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.  
  
## <a name="example"></a>Příklad  
 Ukázka používá následující uložené procedury pro vložení do nové kategorie **Northwind** **kategorie** tabulky. Uložené procedury přijímá hodnotu **CategoryName** sloupce jako vstupní parametr a použije SCOPE_IDENTITY() funkce k načtení nové hodnoty pole identity **CategoryID**a vrácení výstupní parametr. Příkaz RETURN používá @@ROWCOUNT funkce vrací počet řádků vložit.  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Následující příklad kódu používá `InsertCategory` uloženou proceduru jako zdroj pro uvedené výše <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Výstupní parametr, se projeví ve <xref:System.Data.DataSet> po záznamu byla vložena do databáze při `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter> je volána. Kód také použije vrácenou hodnotu.  
  
> [!NOTE]
>  Při použití <xref:System.Data.OleDb.OleDbDataAdapter>, je nutné zadat parametry <xref:System.Data.ParameterDirection> z **ReturnValue** před jinými parametry.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
