---
title: Úprava dat pomocí uložené procedury
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: d9dcda6b93fbc036818ad2ad43da4bfac95f6833
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758153"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="5416e-102">Úprava dat pomocí uložené procedury</span><span class="sxs-lookup"><span data-stu-id="5416e-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="5416e-103">Uložené procedury lze přijímat data jako vstupní parametry a vrací data jako výstupní parametry, sad výsledků dotazu nebo návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5416e-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="5416e-104">Následující ukázka ukazuje, jak ADO.NET odesílá a přijímá vstupní parametry, výstupní parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5416e-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="5416e-105">V příkladu vloží nového záznamu do tabulky, kde sloupec primárního klíče je sloupec identity v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5416e-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5416e-106">Pokud chcete upravit nebo odstranit data pomocí používáte uložené procedury SQL serveru <xref:System.Data.SqlClient.SqlDataAdapter>, ujistěte se, nepoužívejte SET NOCOUNT ON v definici uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="5416e-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="5416e-107">To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako konflikt souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="5416e-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="5416e-108">V takovém případě <xref:System.Data.DBConcurrencyException> bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5416e-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5416e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5416e-109">Example</span></span>  
 <span data-ttu-id="5416e-110">Ukázka používá následující uložené procedury vložit novou kategorii do **Northwind** **kategorie** tabulky.</span><span class="sxs-lookup"><span data-stu-id="5416e-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="5416e-111">Uložená procedura přebírá hodnotu **CategoryName** sloupec jako vstupní parametr a používá SCOPE_IDENTITY() funkci, aby se nová hodnota pole identity načíst **CategoryID**a obnoví v něm výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="5416e-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="5416e-112">Příkaz RETURN používá @@ROWCOUNT funkce, která se vrátí počet vložené řádky.</span><span class="sxs-lookup"><span data-stu-id="5416e-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="5416e-113">Následující příklad kódu používá `InsertCategory` uložené procedury výše uvedeném jako zdroj pro <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="5416e-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="5416e-114">`@Identity` Výstupní parametr, se projeví ve <xref:System.Data.DataSet> po záznamu byla vložena do databáze při `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter> je volána.</span><span class="sxs-lookup"><span data-stu-id="5416e-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="5416e-115">Kód také načte návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5416e-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5416e-116">Při použití <xref:System.Data.OleDb.OleDbDataAdapter>, je nutné zadat parametry s <xref:System.Data.ParameterDirection> z **ReturnValue** před jinými parametry.</span><span class="sxs-lookup"><span data-stu-id="5416e-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5416e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5416e-117">See Also</span></span>  
 [<span data-ttu-id="5416e-118">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5416e-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="5416e-119">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="5416e-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="5416e-120">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="5416e-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="5416e-121">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="5416e-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
