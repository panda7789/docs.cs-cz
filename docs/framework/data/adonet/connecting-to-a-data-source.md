---
title: Připojení ke zdroji dat v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44706395"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="cb722-102">Připojení ke zdroji dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb722-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="cb722-103">V ADO.NET pomocí **připojení** objektu, který chcete připojit ke konkrétnímu zdroji dat zadáním potřebné ověřovací údaje v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="cb722-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="cb722-104">**Připojení** objektu použijete, závisí na typu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="cb722-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="cb722-105">Má každý zprostředkovatele dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbConnection> objektu: obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbConnection> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlConnection> objektu,. Zahrnuje NET Framework Data Provider pro rozhraní ODBC <xref:System.Data.Odbc.OdbcConnection> objektu a zprostředkovatele dat .NET Framework pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="cb722-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb722-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cb722-106">In This Section</span></span>  
 [<span data-ttu-id="cb722-107">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="cb722-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="cb722-108">Popisuje způsob použití **připojení** k navázání připojení ke zdroji dat objektu.</span><span class="sxs-lookup"><span data-stu-id="cb722-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="cb722-109">Události připojení</span><span class="sxs-lookup"><span data-stu-id="cb722-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="cb722-110">Popisuje způsob použití **InfoMessage** na načtení informační zprávy ze zdroje dat události.</span><span class="sxs-lookup"><span data-stu-id="cb722-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb722-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb722-111">See Also</span></span>  
 [<span data-ttu-id="cb722-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="cb722-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="cb722-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="cb722-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="cb722-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="cb722-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="cb722-115">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="cb722-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="cb722-116">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="cb722-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="cb722-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="cb722-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
