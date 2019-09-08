---
title: Úpravy dat pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 46c92301b717e285c4c18241f84d0069069c7bdc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783523"
---
# <a name="modifying-data-with-stored-procedures"></a>Úpravy dat pomocí uložených procedur
Uložené procedury mohou přijímat data jako vstupní parametry a mohou vracet data jako výstupní parametry, sady výsledků nebo návratové hodnoty. Následující ukázka ukazuje, jak ADO.NET odesílá a přijímá vstupní parametry, výstupní parametry a návratové hodnoty. Příklad vloží nový záznam do tabulky, kde sloupec primárního klíče je sloupec identity v databázi SQL Server.  
  
> [!NOTE]
> Pokud používáte SQL Server uložené procedury k úpravám nebo odstraňování dat pomocí <xref:System.Data.SqlClient.SqlDataAdapter>, ujistěte se, že v definici uložené procedury nepoužijete nastavení počet. To způsobí, že počet ovlivněných řádků vrátil hodnotu nula, což `DataAdapter` interpretuje jako konflikt souběžnosti. V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.  
  
## <a name="example"></a>Příklad  
 Ukázka používá následující uloženou proceduru k vložení nové kategorie do tabulky kategorií **Northwind** . Uložená procedura převezme hodnotu ve sloupci **CategoryName** jako vstupní parametr a pomocí funkce SCOPE_IDENTITY () načte novou hodnotu pole identity, **KódKategorie**a vrátí ji do výstupního parametru. Příkaz return pomocí funkce @@ROWCOUNT vrátí počet vložených řádků.  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Následující příklad kódu používá `InsertCategory` uloženou proceduru uvedenou výše jako zdroj <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> pro <xref:System.Data.SqlClient.SqlDataAdapter>. Výstupní parametr se projeví <xref:System.Data.DataSet> v poté, co byl záznam vložen `Update` do databáze <xref:System.Data.SqlClient.SqlDataAdapter> při volání metody. `@Identity` Kód také načte vrácenou hodnotu.  
  
> [!NOTE]
> Při použití <xref:System.Data.OleDb.OleDbDataAdapter>, je nutné zadat parametry <xref:System.Data.ParameterDirection> s parametrem **ReturnValue** před jinými parametry.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Spuštění příkazu](executing-a-command.md)
- [Přehled ADO.NET](ado-net-overview.md)
