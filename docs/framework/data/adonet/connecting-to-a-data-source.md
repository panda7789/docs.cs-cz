---
title: Připojení ke zdroji dat v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786760"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="d2620-102">Připojení ke zdroji dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d2620-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="d2620-103">V ADO.NET použijete objekt **připojení** pro připojení ke konkrétnímu zdroji dat zadáním potřebných ověřovacích informací v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="d2620-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="d2620-104">Použitý objekt **připojení** závisí na typu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d2620-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="d2620-105">Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, <xref:System.Data.Common.DbConnection> má objekt: .NET Framework Zprostředkovatel dat pro OLE DB <xref:System.Data.OleDb.OleDbConnection> obsahuje objekt, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlConnection> objekt,. Rozhraní .NET Framework Zprostředkovatel dat pro rozhraní ODBC <xref:System.Data.Odbc.OdbcConnection> zahrnuje objekt a .NET Framework Zprostředkovatel dat pro Oracle <xref:System.Data.OracleClient.OracleConnection> obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="d2620-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2620-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d2620-106">In This Section</span></span>  
 [<span data-ttu-id="d2620-107">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="d2620-107">Establishing the Connection</span></span>](establishing-the-connection.md)  
 <span data-ttu-id="d2620-108">Popisuje způsob použití objektu **připojení** k navázání připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d2620-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="d2620-109">Události připojení</span><span class="sxs-lookup"><span data-stu-id="d2620-109">Connection Events</span></span>](connection-events.md)  
 <span data-ttu-id="d2620-110">Popisuje, jak používat událost **InfoMessage** k načtení informativních zpráv ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d2620-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2620-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2620-111">See also</span></span>

- [<span data-ttu-id="d2620-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="d2620-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="d2620-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="d2620-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="d2620-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="d2620-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="d2620-115">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="d2620-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d2620-116">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="d2620-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="d2620-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d2620-117">ADO.NET Overview</span></span>](ado-net-overview.md)
