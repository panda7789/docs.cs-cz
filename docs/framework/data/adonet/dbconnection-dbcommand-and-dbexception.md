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
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="72654-102">Připojení DbConnection, DbCommand a dbexception –</span><span class="sxs-lookup"><span data-stu-id="72654-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="72654-103">Po vytvoření <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection>, pak můžete pracovat s příkazy a čtečky dat. k načtení dat ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="72654-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="72654-104">Příklad načítání dat</span><span class="sxs-lookup"><span data-stu-id="72654-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="72654-105">Tento příklad zpracuje `DbConnection` objektu jako argument.</span><span class="sxs-lookup"><span data-stu-id="72654-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="72654-106">A <xref:System.Data.Common.DbCommand> se vytvoří pro výběr data z tabulky kategorie podle nastavení <xref:System.Data.Common.DbCommand.CommandText%2A> do příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="72654-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="72654-107">Kód předpokládá, že v tabulce kategorie existuje ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="72654-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="72654-108">Připojení je otevřít a data se načítají pomocí <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="72654-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="72654-109">Provádění příkazu příklad</span><span class="sxs-lookup"><span data-stu-id="72654-109">Executing a Command Example</span></span>  
 <span data-ttu-id="72654-110">Tento příklad zpracuje `DbConnection` objektu jako argument.</span><span class="sxs-lookup"><span data-stu-id="72654-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="72654-111">Pokud `DbConnection` je platný, je-li otevřít připojení a <xref:System.Data.Common.DbCommand> se vytvoří a provést.</span><span class="sxs-lookup"><span data-stu-id="72654-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="72654-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Je nastaven na příkazu INSERT jazyka SQL, který provádí typu vložení do kategorií tabulky v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="72654-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="72654-113">Kód předpokládá, že databáze Northwind existuje ve zdroji dat, a zda je platná pro zadaného zprostředkovatele syntaxe SQL použít v příkazu INSERT.</span><span class="sxs-lookup"><span data-stu-id="72654-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="72654-114">Chyby, ke kterým dochází ve zdroji dat jsou zpracovávány <xref:System.Data.Common.DbException> blok kódu a všechny ostatní výjimky jsou zpracovávány v <xref:System.Exception> bloku.</span><span class="sxs-lookup"><span data-stu-id="72654-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="72654-115">Zpracování chyb dat s dbexception –</span><span class="sxs-lookup"><span data-stu-id="72654-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="72654-116"><xref:System.Data.Common.DbException> Třída je základní třída pro všechny výjimky vydané jménem zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="72654-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="72654-117">Můžete ji použít ve vašem kódu pro zpracování výjimek pro zpracování výjimky vyvolané různé zprostředkovatele bez nutnosti referenční třídy konkrétní výjimek.</span><span class="sxs-lookup"><span data-stu-id="72654-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="72654-118">Následující fragment kódu ukazuje, jak používat <xref:System.Data.Common.DbException> zobrazíte informace o chybě vrácený zdroje dat pomocí <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, a <xref:System.Exception.Message%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="72654-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="72654-119">Výstup se zobrazí typ chyby, zdroj označující název zprostředkovatele, kód chyby a zpráva přidružená k chybě.</span><span class="sxs-lookup"><span data-stu-id="72654-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72654-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="72654-120">See Also</span></span>  
 [<span data-ttu-id="72654-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="72654-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="72654-122">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="72654-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="72654-123">Úprava dat s DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="72654-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="72654-124">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="72654-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
