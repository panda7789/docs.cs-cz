---
title: Připojení ke zdroji dat
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287074"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="f6b30-102">Připojení ke zdroji dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f6b30-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="f6b30-103">V ADO.NET použijete objekt **připojení** pro připojení ke konkrétnímu zdroji dat zadáním potřebných ověřovacích informací v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="f6b30-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="f6b30-104">Použitý objekt **připojení** závisí na typu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="f6b30-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="f6b30-105">Každý .NET Framework poskytovatel dat, který je součástí .NET Framework <xref:System.Data.Common.DbConnection> , má objekt: .NET Framework Zprostředkovatel dat pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbConnection> objekt, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje objekt, .NET Framework Zprostředkovatel dat <xref:System.Data.SqlClient.SqlConnection> pro rozhraní ODBC obsahuje objekt a .NET Framework Zprostředkovatel dat <xref:System.Data.Odbc.OdbcConnection> pro Oracle <xref:System.Data.OracleClient.OracleConnection> obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="f6b30-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6b30-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f6b30-106">In This Section</span></span>  
 <span data-ttu-id="f6b30-107">[Navazování připojení](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="f6b30-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="f6b30-108">Popisuje způsob použití objektu **připojení** k navázání připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="f6b30-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="f6b30-109">[Události připojení](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="f6b30-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="f6b30-110">Popisuje, jak používat událost **InfoMessage** k načtení informativních zpráv ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="f6b30-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b30-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6b30-111">See also</span></span>

- [<span data-ttu-id="f6b30-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="f6b30-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="f6b30-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="f6b30-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="f6b30-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="f6b30-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="f6b30-115">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="f6b30-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="f6b30-116">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="f6b30-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="f6b30-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f6b30-117">ADO.NET Overview</span></span>](ado-net-overview.md)
