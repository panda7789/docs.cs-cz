---
title: Připojení ke zdroji dat
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 84dc15c0965b7ac8209bd9115d611162e57d6dda
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980246"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="fd1c9-102">Připojení ke zdroji dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd1c9-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="fd1c9-103">V ADO.NET použijete objekt **připojení** pro připojení ke konkrétnímu zdroji dat zadáním potřebných ověřovacích informací v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="fd1c9-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="fd1c9-104">Použitý objekt **připojení** závisí na typu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fd1c9-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="fd1c9-105">Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, má <xref:System.Data.Common.DbConnection> objekt: .NET Framework Zprostředkovatel dat pro OLE DB obsahuje objekt <xref:System.Data.OleDb.OleDbConnection>, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje objekt <xref:System.Data.SqlClient.SqlConnection>, .NET Framework Zprostředkovatel dat pro rozhraní ODBC zahrnuje <xref:System.Data.Odbc.OdbcConnection> objekt a .NET Framework Zprostředkovatel dat pro Oracle zahrnuje objekt <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="fd1c9-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd1c9-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fd1c9-106">In This Section</span></span>  
 [<span data-ttu-id="fd1c9-107">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="fd1c9-107">Establishing the Connection</span></span>](establishing-the-connection.md)  
 <span data-ttu-id="fd1c9-108">Popisuje způsob použití objektu **připojení** k navázání připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="fd1c9-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="fd1c9-109">Události připojení</span><span class="sxs-lookup"><span data-stu-id="fd1c9-109">Connection Events</span></span>](connection-events.md)  
 <span data-ttu-id="fd1c9-110">Popisuje, jak používat událost **InfoMessage** k načtení informativních zpráv ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fd1c9-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1c9-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd1c9-111">See also</span></span>

- [<span data-ttu-id="fd1c9-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="fd1c9-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="fd1c9-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="fd1c9-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="fd1c9-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="fd1c9-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="fd1c9-115">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="fd1c9-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="fd1c9-116">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="fd1c9-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="fd1c9-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd1c9-117">ADO.NET Overview</span></span>](ado-net-overview.md)
