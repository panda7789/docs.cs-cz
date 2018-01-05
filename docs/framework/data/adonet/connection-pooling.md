---
title: "Sdružování připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5082adda3c03bfbc40eafb174513a39fe17a3da8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="connection-pooling"></a><span data-ttu-id="24572-102">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="24572-102">Connection Pooling</span></span>
<span data-ttu-id="24572-103">Připojení ke zdroji dat může být časově náročná.</span><span class="sxs-lookup"><span data-stu-id="24572-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="24572-104">Chcete-li minimalizovat náklady na otevření připojení, ADO.NET používá volat metodu optimalizace *sdružování připojení*, což minimalizuje náklady na opakovaně otvírání a zavírání připojení.</span><span class="sxs-lookup"><span data-stu-id="24572-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="24572-105">Sdružování připojení se proto liší pro zprostředkovatele dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24572-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24572-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="24572-106">In This Section</span></span>  
 [<span data-ttu-id="24572-107">Sdružování připojení SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="24572-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="24572-108">Obsahuje základní informace o sdružování připojení a popisuje, jak sdružování připojení funguje [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24572-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="24572-109">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="24572-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="24572-110">Popisuje zprostředkovatele dat .NET Framework pro OLE DB, zprostředkovatel dat .NET Framework pro ODBC a zprostředkovatel dat .NET Framework pro Oracle sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="24572-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24572-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="24572-111">See Also</span></span>  
 [<span data-ttu-id="24572-112">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="24572-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="24572-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="24572-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
