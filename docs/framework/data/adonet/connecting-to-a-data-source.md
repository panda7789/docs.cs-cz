---
title: "Připojení ke zdroji dat v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0d21c571b659e9d7aef65893db18b034d614e2af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="28016-102">Připojení ke zdroji dat v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="28016-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="28016-103">V technologii ADO.NET použijete **připojení** objekt, který chcete připojit ke zdroji dat konkrétní zadáním informace nezbytné ověřování v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="28016-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="28016-104">**Připojení** objekt použijete, závisí na typu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="28016-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="28016-105">Má každý zprostředkovatel dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbConnection> objektu: zahrnuje zprostředkovatel dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbConnection> objektu, zahrnuje zprostředkovatel dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> objekt,. Zprostředkovatel dat NET Framework pro ODBC zahrnuje <xref:System.Data.Odbc.OdbcConnection> objekt a zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="28016-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28016-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="28016-106">In This Section</span></span>  
 [<span data-ttu-id="28016-107">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="28016-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="28016-108">Popisuje způsob použití **připojení** objekt, který chcete vytvořit připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="28016-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="28016-109">Připojení událostí</span><span class="sxs-lookup"><span data-stu-id="28016-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="28016-110">Popisuje, jak používat **InfoMessage** na načíst informační zprávy ze zdroje dat události.</span><span class="sxs-lookup"><span data-stu-id="28016-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28016-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="28016-111">See Also</span></span>  
 [<span data-ttu-id="28016-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="28016-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="28016-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="28016-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="28016-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="28016-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="28016-115">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="28016-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="28016-116">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="28016-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="28016-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="28016-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
