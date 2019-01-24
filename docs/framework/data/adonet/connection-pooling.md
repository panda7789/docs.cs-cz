---
title: Sdružování připojení
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: cba3311a15c8bc1c657b7a19e475047cafe9110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627282"
---
# <a name="connection-pooling"></a><span data-ttu-id="6a0d7-102">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="6a0d7-102">Connection Pooling</span></span>
<span data-ttu-id="6a0d7-103">Připojení ke zdroji dat může být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="6a0d7-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="6a0d7-104">Chcete-li minimalizovat náklady na otevření připojení ADO.NET používá optimalizaci techniky označované jako *sdružování připojení*, což minimalizuje náklady na opakovaného otevírání a zavírání připojení.</span><span class="sxs-lookup"><span data-stu-id="6a0d7-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="6a0d7-105">Sdružování připojení je zpracována jinak pro zprostředkovatele dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a0d7-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a0d7-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6a0d7-106">In This Section</span></span>  
 [<span data-ttu-id="6a0d7-107">Sdružování připojení SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="6a0d7-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="6a0d7-108">Obsahuje základní informace o sdružování připojení a popisuje, jak sdružování připojení funguje v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a0d7-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="6a0d7-109">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="6a0d7-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="6a0d7-110">Popisuje sdružování připojení zprostředkovatele dat .NET Framework pro OLE DB, zprostředkovatele dat .NET Framework pro ODBC a zprostředkovatele dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="6a0d7-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0d7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a0d7-111">See also</span></span>
- [<span data-ttu-id="6a0d7-112">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a0d7-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="6a0d7-113">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="6a0d7-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
