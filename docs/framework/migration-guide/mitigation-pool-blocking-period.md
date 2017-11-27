---
title: "Omezení rizik: Fond Blocking období"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8749e2d7b91e611ee153c6f36708fa34a44ecccd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="a86da-102">Omezení rizik: Fond Blocking období</span><span class="sxs-lookup"><span data-stu-id="a86da-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="a86da-103">Odebrali jsme blokování období fondu připojení pro připojení k databázím Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="a86da-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="a86da-104">Další popis</span><span class="sxs-lookup"><span data-stu-id="a86da-104">Additional description</span></span>  
 <span data-ttu-id="a86da-105">V [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší verze, když aplikace zaznamená přechodné chybě při připojování k databázi, pokus o připojení nejde opakovat rychle, protože fond připojení ukládá do mezipaměti chyby a znovu vyvolá po dobu 5 sekund do 1 min. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="a86da-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="a86da-106">Toto chování je problematické pro připojení k databázím Azure SQL, které často dojde k chybě přechodné chyby, které jsou obvykle obnovit z během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="a86da-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="a86da-107">Funkce připojení k fondu blokování znamená, že aplikace nemůže připojit k databázi pro rozsáhlé období, i když je databáze dostupná.</span><span class="sxs-lookup"><span data-stu-id="a86da-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="a86da-108">Toto chování je obzvláště problematické pro webové aplikace, která připojení k databázím Azure SQL a které jsou nutné k vykreslení během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="a86da-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="a86da-109">Od verze [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], připojení otevřené žádosti o známé databází Azure SQL (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Otevřete chyb připojení se neukládají do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a86da-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="a86da-110">Pro všechny ostatní pokusy o připojení i nadále vynucovat blokování období fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="a86da-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a86da-111">Dopad</span><span class="sxs-lookup"><span data-stu-id="a86da-111">Impact</span></span>  
 <span data-ttu-id="a86da-112">Tato změna umožňuje otevřete pokus o připojení k okamžitě opakovat u databází Azure SQL, a tím zvýšení výkonu aplikací povolenou podporu cloudu.</span><span class="sxs-lookup"><span data-stu-id="a86da-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a86da-113">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="a86da-113">Mitigation</span></span>  
 <span data-ttu-id="a86da-114">Aplikace, které jsou negativně ovlivněn touto změnou, blokování období fondu připojení se dá nakonfigurovat pomocí nastavení nové <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a86da-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property.</span></span>  <span data-ttu-id="a86da-115">Hodnota vlastnosti je členem skupiny <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> výčet, který může mít jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="a86da-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 <span data-ttu-id="a86da-116">Předchozí chování může být obnovena nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnost `PoolBlockingPeriod.AlwaysBlock`.</span><span class="sxs-lookup"><span data-stu-id="a86da-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to `PoolBlockingPeriod.AlwaysBlock`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86da-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a86da-117">See Also</span></span>  
 [<span data-ttu-id="a86da-118">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a86da-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
