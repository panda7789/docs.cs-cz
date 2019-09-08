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
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="e1867-102">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="e1867-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="e1867-103">Po vytvoření <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection>a a pak můžete pracovat s příkazy a čtenáři dat a načíst data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e1867-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="e1867-104">Příklad načítání dat</span><span class="sxs-lookup"><span data-stu-id="e1867-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="e1867-105">Tento příklad přijímá `DbConnection` objekt jako argument.</span><span class="sxs-lookup"><span data-stu-id="e1867-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="e1867-106">Vytvoří <xref:System.Data.Common.DbCommand> se, pokud chcete vybrat data z tabulky Categories <xref:System.Data.Common.DbCommand.CommandText%2A> nastavením příkazu na příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="e1867-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="e1867-107">Kód předpokládá, že tabulka Categories existuje ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e1867-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="e1867-108">Připojení je otevřeno a data jsou načtena pomocí <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="e1867-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="e1867-109">Spuštění příkladu příkazu</span><span class="sxs-lookup"><span data-stu-id="e1867-109">Executing a Command Example</span></span>  
 <span data-ttu-id="e1867-110">Tento příklad přijímá `DbConnection` objekt jako argument.</span><span class="sxs-lookup"><span data-stu-id="e1867-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="e1867-111">Pokud je platný, připojení se otevře <xref:System.Data.Common.DbCommand> a vytvoří se a spustí se. `DbConnection`</span><span class="sxs-lookup"><span data-stu-id="e1867-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="e1867-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Je nastaven na příkaz SQL INSERT, který provede vložení do tabulky Categories v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="e1867-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="e1867-113">Kód předpokládá, že databáze Northwind existuje ve zdroji dat a že syntaxe SQL použitá v příkazu INSERT je platná pro zadaného zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e1867-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="e1867-114">Chyby, ke kterým došlo na zdroji dat, jsou zpracovávány <xref:System.Data.Common.DbException> blokem kódu a všechny ostatní výjimky jsou zpracovávány <xref:System.Exception> v bloku.</span><span class="sxs-lookup"><span data-stu-id="e1867-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="e1867-115">Zpracování chyb dat pomocí DbException</span><span class="sxs-lookup"><span data-stu-id="e1867-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="e1867-116"><xref:System.Data.Common.DbException> Třída je základní třída pro všechny výjimky vyvolané jménem zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e1867-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="e1867-117">Můžete ji použít v kódu zpracování výjimek pro zpracování výjimek vyvolaných různými zprostředkovateli bez nutnosti odkazování na konkrétní třídu výjimky.</span><span class="sxs-lookup"><span data-stu-id="e1867-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="e1867-118">Následující fragment kódu ukazuje, <xref:System.Data.Common.DbException> jak použít k zobrazení informací o chybách vrácených zdrojem dat pomocí <xref:System.Exception.GetType%2A>vlastností, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>a <xref:System.Exception.Message%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1867-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="e1867-119">Ve výstupu se zobrazí typ chyby, zdroj označující název zprostředkovatele, kód chyby a zprávu spojenou s chybou.</span><span class="sxs-lookup"><span data-stu-id="e1867-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1867-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1867-120">See also</span></span>

- [<span data-ttu-id="e1867-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="e1867-121">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="e1867-122">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="e1867-122">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="e1867-123">Úpravy dat přes DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="e1867-123">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="e1867-124">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e1867-124">ADO.NET Overview</span></span>](ado-net-overview.md)
