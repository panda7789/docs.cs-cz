---
title: 'Zmírnění rizik: Období blokování fondu'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457843"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="e6d21-102">Zmírnění rizik: Období blokování fondu</span><span class="sxs-lookup"><span data-stu-id="e6d21-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="e6d21-103">Období blokování fondu připojení bylo odebráno pro připojení k databázím Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="e6d21-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="e6d21-104">Další popis</span><span class="sxs-lookup"><span data-stu-id="e6d21-104">Additional description</span></span>  
 <span data-ttu-id="e6d21-105">V rozhraní .NET Framework 4.6.1 a starších verzích, když aplikace narazí na selhání přechodného připojení při připojení k databázi, nelze pokus o připojení zopakovat rychle, protože fond připojení ukládá chybu do mezipaměti a znovu ji vyvolá na 5 sekund až 1 min. Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="e6d21-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="e6d21-106">Toto chování je problematické pro připojení k databázím Azure SQL, které často selžou s přechodnými chybami, které se obvykle obnovují během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="e6d21-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="e6d21-107">Funkce blokování fondu připojení znamená, že aplikace nemůže připojit k databázi po delší dobu, i když databáze je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e6d21-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="e6d21-108">Toto chování je obzvláště problematické pro webové aplikace, které se připojují k databázím Azure SQL a které je potřeba vykreslit během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="e6d21-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="e6d21-109">Počínaje rozhraním .NET Framework 4.6.2 pro připojení otevřené požadavky na známé \*databáze Azure \*SQL \*(\*.database.windows.net, .database.chinacloudapi.cn, .database.usgovcloudapi.net, .database.cloudapi.de), chyby otevření připojení nejsou uloženy do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e6d21-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="e6d21-110">Pro všechny ostatní pokusy o připojení období blokování fondu připojení je nadále vynuceno.</span><span class="sxs-lookup"><span data-stu-id="e6d21-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e6d21-111">Dopad</span><span class="sxs-lookup"><span data-stu-id="e6d21-111">Impact</span></span>  
 <span data-ttu-id="e6d21-112">Tato změna umožňuje pokus o otevření připojení, který se okamžitě zopakovává pro databáze Azure SQL, čímž se zlepší výkon aplikací s podporou cloudu.</span><span class="sxs-lookup"><span data-stu-id="e6d21-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e6d21-113">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="e6d21-113">Mitigation</span></span>  
 <span data-ttu-id="e6d21-114">U aplikací, které jsou touto změnou nepříznivě ovlivněny, lze <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> nakonfigurovat období blokování fondu připojení nastavením nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e6d21-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="e6d21-115">Hodnota vlastnosti je členem výčtu, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> který může trvat jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="e6d21-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="e6d21-116">Předchozí chování lze obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnosti na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6d21-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d21-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6d21-117">See also</span></span>

- [<span data-ttu-id="e6d21-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="e6d21-118">Application compatibility</span></span>](application-compatibility.md)
