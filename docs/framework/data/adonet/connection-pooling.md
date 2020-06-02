---
title: Sdružování připojení
description: Přečtěte si o sdružování připojení, technice optimalizace, kterou ADO.NET používá k minimalizaci nákladů na otevírání připojení ke zdrojům dat.
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: b8f89dfda7edbde14dbb5945f10f2284ac43c3d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287087"
---
# <a name="connection-pooling"></a><span data-ttu-id="f5006-103">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="f5006-103">Connection Pooling</span></span>
<span data-ttu-id="f5006-104">Připojení ke zdroji dat může být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="f5006-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="f5006-105">Pro minimalizaci nákladů na otevírání připojení používá ADO.NET techniku optimalizace nazývanou *sdružování připojení*, která minimalizuje náklady na opakované otevírání a uzavírání připojení.</span><span class="sxs-lookup"><span data-stu-id="f5006-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="f5006-106">Sdružování připojení se pro poskytovatele .NET Frameworkch dat zpracovává jinak.</span><span class="sxs-lookup"><span data-stu-id="f5006-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5006-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f5006-107">In This Section</span></span>  
 [<span data-ttu-id="f5006-108">Sdružování připojení SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f5006-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="f5006-109">Poskytuje přehled sdružování připojení a popisuje, jak sdružování připojení funguje v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5006-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="f5006-110">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="f5006-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="f5006-111">Popisuje sdružování připojení pro .NET Framework Zprostředkovatel dat pro OLE DB, .NET Framework Zprostředkovatel dat pro rozhraní ODBC a .NET Framework Zprostředkovatel dat pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="f5006-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5006-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5006-112">See also</span></span>

- [<span data-ttu-id="f5006-113">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5006-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="f5006-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5006-114">ADO.NET Overview</span></span>](ado-net-overview.md)
