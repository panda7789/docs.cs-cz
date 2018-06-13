---
title: Sdružování připojení
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: 47143e1d08f6a910b82b435303c164729b6ad3a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755523"
---
# <a name="connection-pooling"></a><span data-ttu-id="f2bc8-102">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="f2bc8-102">Connection Pooling</span></span>
<span data-ttu-id="f2bc8-103">Připojení ke zdroji dat může být časově náročná.</span><span class="sxs-lookup"><span data-stu-id="f2bc8-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="f2bc8-104">Chcete-li minimalizovat náklady na otevření připojení, ADO.NET používá volat metodu optimalizace *sdružování připojení*, což minimalizuje náklady na opakovaně otvírání a zavírání připojení.</span><span class="sxs-lookup"><span data-stu-id="f2bc8-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="f2bc8-105">Sdružování připojení se proto liší pro zprostředkovatele dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2bc8-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2bc8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f2bc8-106">In This Section</span></span>  
 [<span data-ttu-id="f2bc8-107">Sdružování připojení SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f2bc8-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="f2bc8-108">Obsahuje základní informace o sdružování připojení a popisuje, jak sdružování připojení funguje v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f2bc8-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="f2bc8-109">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="f2bc8-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="f2bc8-110">Popisuje zprostředkovatele dat .NET Framework pro OLE DB, zprostředkovatel dat .NET Framework pro ODBC a zprostředkovatel dat .NET Framework pro Oracle sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="f2bc8-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2bc8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2bc8-111">See Also</span></span>  
 [<span data-ttu-id="f2bc8-112">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2bc8-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="f2bc8-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f2bc8-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
