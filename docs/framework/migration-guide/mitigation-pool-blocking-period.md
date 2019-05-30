---
title: 'Omezení rizik: Období blokování fondu'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01bd548bbafda34202705dda3dda148aae941e2b
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251103"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="9ce84-102">Omezení rizik: Období blokování fondu</span><span class="sxs-lookup"><span data-stu-id="9ce84-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="9ce84-103">Odebrali jsme blokování období fondu připojení pro připojení k databázím Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="9ce84-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="9ce84-104">Další popis</span><span class="sxs-lookup"><span data-stu-id="9ce84-104">Additional description</span></span>  
 <span data-ttu-id="9ce84-105">V rozhraní .NET Framework 4.6.1 a starší verze pokud aplikace zjistí chyba přechodného připojení při připojování k databázi, pokus o připojení se nedá opakovat, rychle, protože fond připojení ukládá do mezipaměti, chyby a znovu vyvolá po dobu 5 sekund do 1 min. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="9ce84-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="9ce84-106">Toto chování je problematické pro připojení k databázím Azure SQL, které často dojde k přechodným chybám, které jsou obvykle obnovila během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="9ce84-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="9ce84-107">Funkce připojení k fondu blokování znamená, že aplikace nemůže připojit k databázi rozsáhlé dobu, i v případě, že databáze je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9ce84-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="9ce84-108">Toto chování je zvláště problematický pro webové aplikace, které se připojovat k databázím Azure SQL a, které je potřeba vykreslit během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="9ce84-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="9ce84-109">Od verze rozhraní .NET Framework 4.6.2, pro připojení k otevření žádosti o známých databází Azure SQL (\*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de ), otevřete chyb připojení nejsou uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9ce84-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="9ce84-110">Pro všechny ostatní pokusy o připojení pokračuje v období blokování fondu připojení vynucení.</span><span class="sxs-lookup"><span data-stu-id="9ce84-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9ce84-111">Dopad</span><span class="sxs-lookup"><span data-stu-id="9ce84-111">Impact</span></span>  
 <span data-ttu-id="9ce84-112">Tato změna umožňuje otevřít pokus o připojení k opakovat okamžitě pro Azure SQL Database, následné vylepšení výkonu aplikací povolenou podporu cloudu.</span><span class="sxs-lookup"><span data-stu-id="9ce84-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9ce84-113">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="9ce84-113">Mitigation</span></span>  
 <span data-ttu-id="9ce84-114">U aplikací, které jsou této změně nepříznivě ovlivněny doby blokování fond připojení se dá nakonfigurovat nastavení nové <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9ce84-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="9ce84-115">Hodnota vlastnosti je členem skupiny <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> výčet, který může mít jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="9ce84-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="9ce84-116">Předchozí chování můžete obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnost <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ce84-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce84-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ce84-117">See also</span></span>

- [<span data-ttu-id="9ce84-118">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9ce84-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
