---
title: DbConnection, DbCommand a DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 759b2f36f9d38cdac0cfe4ff8e451b38012493e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143829"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="ea52a-102">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="ea52a-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="ea52a-103">Jakmile vytvoříte <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection>, pak můžete pracovat s příkazy a čtečky dat. k načtení dat z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="ea52a-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="ea52a-104">Příklad načítání dat</span><span class="sxs-lookup"><span data-stu-id="ea52a-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="ea52a-105">Tento příklad používá `DbConnection` objektu jako argument.</span><span class="sxs-lookup"><span data-stu-id="ea52a-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="ea52a-106">A <xref:System.Data.Common.DbCommand> se vytvoří vyberte data z tabulky Kategorie nastavením <xref:System.Data.Common.DbCommand.CommandText%2A> na příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="ea52a-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="ea52a-107">Kód předpokládá, že existuje kategorie tabulky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ea52a-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="ea52a-108">Otevření připojení a data jsou načítány s použitím <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ea52a-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="ea52a-109">Provedení příkazu příklad</span><span class="sxs-lookup"><span data-stu-id="ea52a-109">Executing a Command Example</span></span>  
 <span data-ttu-id="ea52a-110">Tento příklad používá `DbConnection` objektu jako argument.</span><span class="sxs-lookup"><span data-stu-id="ea52a-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="ea52a-111">Pokud `DbConnection` je platný, je otevřeno připojení a <xref:System.Data.Common.DbCommand> je vytvořen a spuštěn.</span><span class="sxs-lookup"><span data-stu-id="ea52a-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="ea52a-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Je nastavena na příkazu INSERT jazyka SQL, který provádí vložení do kategorií tabulky v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="ea52a-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="ea52a-113">Kód předpokládá, že databáze Northwind existuje ve zdroji dat a syntaxe SQL v příkazu INSERT je platný pro zadaného zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="ea52a-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="ea52a-114">Zpracovává chyby, ke kterým dochází ve zdroji dat <xref:System.Data.Common.DbException> blok kódu a všechny ostatní výjimky jsou zpracovány v <xref:System.Exception> bloku.</span><span class="sxs-lookup"><span data-stu-id="ea52a-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="ea52a-115">Zpracování chyb Data s DbException</span><span class="sxs-lookup"><span data-stu-id="ea52a-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="ea52a-116"><xref:System.Data.Common.DbException> Třída je základní třída pro všechny výjimky vyvolané jménem zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ea52a-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="ea52a-117">Vám pomůže ho v váš kód zpracování výjimek zpracování výjimek vyvolaných různí poskytovatelé, aniž byste museli reference – třída výjimky.</span><span class="sxs-lookup"><span data-stu-id="ea52a-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="ea52a-118">Následující fragment kódu ukazuje, jak používat <xref:System.Data.Common.DbException> zobrazíte informace o chybách vrácených ve zdroji dat pomocí <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, a <xref:System.Exception.Message%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea52a-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="ea52a-119">Ve výstupu se zobrazí typ chyby, zdrojový označující název zprostředkovatele, kód chyby a zprávy související s chybou.</span><span class="sxs-lookup"><span data-stu-id="ea52a-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea52a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea52a-120">See also</span></span>

- [<span data-ttu-id="ea52a-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="ea52a-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="ea52a-122">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="ea52a-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="ea52a-123">Úpravy dat přes DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="ea52a-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="ea52a-124">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ea52a-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
