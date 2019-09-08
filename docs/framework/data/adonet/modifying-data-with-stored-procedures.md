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
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="d1bd9-102">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="d1bd9-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="d1bd9-103">Uložené procedury mohou přijímat data jako vstupní parametry a mohou vracet data jako výstupní parametry, sady výsledků nebo návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="d1bd9-104">Následující ukázka ukazuje, jak ADO.NET odesílá a přijímá vstupní parametry, výstupní parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="d1bd9-105">Příklad vloží nový záznam do tabulky, kde sloupec primárního klíče je sloupec identity v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1bd9-106">Pokud používáte SQL Server uložené procedury k úpravám nebo odstraňování dat pomocí <xref:System.Data.SqlClient.SqlDataAdapter>, ujistěte se, že v definici uložené procedury nepoužijete nastavení počet.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="d1bd9-107">To způsobí, že počet ovlivněných řádků vrátil hodnotu nula, což `DataAdapter` interpretuje jako konflikt souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="d1bd9-108">V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bd9-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1bd9-109">Example</span></span>  
 <span data-ttu-id="d1bd9-110">Ukázka používá následující uloženou proceduru k vložení nové kategorie do tabulky kategorií **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="d1bd9-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="d1bd9-111">Uložená procedura převezme hodnotu ve sloupci **CategoryName** jako vstupní parametr a pomocí funkce SCOPE_IDENTITY () načte novou hodnotu pole identity, **KódKategorie**a vrátí ji do výstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="d1bd9-112">Příkaz return pomocí funkce @@ROWCOUNT vrátí počet vložených řádků.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="d1bd9-113">Následující příklad kódu používá `InsertCategory` uloženou proceduru uvedenou výše jako zdroj <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> pro <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="d1bd9-114">Výstupní parametr se projeví <xref:System.Data.DataSet> v poté, co byl záznam vložen `Update` do databáze <xref:System.Data.SqlClient.SqlDataAdapter> při volání metody. `@Identity`</span><span class="sxs-lookup"><span data-stu-id="d1bd9-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="d1bd9-115">Kód také načte vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1bd9-116">Při použití <xref:System.Data.OleDb.OleDbDataAdapter>, je nutné zadat parametry <xref:System.Data.ParameterDirection> s parametrem **ReturnValue** před jinými parametry.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d1bd9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1bd9-117">See also</span></span>

- [<span data-ttu-id="d1bd9-118">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1bd9-118">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="d1bd9-119">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="d1bd9-119">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d1bd9-120">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="d1bd9-120">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="d1bd9-121">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1bd9-121">ADO.NET Overview</span></span>](ado-net-overview.md)
