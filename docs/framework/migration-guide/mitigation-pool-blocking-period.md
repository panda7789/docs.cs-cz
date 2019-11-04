---
title: 'Zmírnění rizika: doba blokování fondu'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457843"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="b1635-102">Zmírnění rizika: doba blokování fondu</span><span class="sxs-lookup"><span data-stu-id="b1635-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="b1635-103">Bylo odebráno období blokování fondu připojení pro připojení k databázím Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="b1635-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="b1635-104">Další popis</span><span class="sxs-lookup"><span data-stu-id="b1635-104">Additional description</span></span>  
 <span data-ttu-id="b1635-105">Pokud se v .NET Framework 4.6.1 a starších verzích při připojování k databázi stala chyba přechodného připojení, pokus o připojení se nedá opakovat, protože fond připojení tuto chybu ukládá do mezipaměti a znovu ho vyvolá po dobu 5 sekund až 1. dlouhé. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="b1635-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="b1635-106">Toto chování je problematické pro připojení k databázím Azure SQL, což často selhává kvůli přechodným chybám, které se obvykle obnovují během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="b1635-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="b1635-107">Funkce blokování fondu připojení znamená, že se aplikace nemůže po rozsáhlé době připojit k databázi, a to i v případě, že je databáze k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1635-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="b1635-108">Toto chování je obzvláště problematické u webových aplikací, které se připojují k databázím SQL Azure a které je potřeba vykreslit během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="b1635-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="b1635-109">Počínaje .NET Framework 4.6.2, pro žádosti o otevření připojení ke známým databázím Azure SQL (\*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), připojení otevřené chyby nejsou ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b1635-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="b1635-110">U všech dalších pokusů o připojení se i nadále vynutilo období blokování fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="b1635-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b1635-111">Dopad</span><span class="sxs-lookup"><span data-stu-id="b1635-111">Impact</span></span>  
 <span data-ttu-id="b1635-112">Tato změna umožňuje okamžité opakování pokusu o připojení pro databáze SQL Azure, což zlepšuje výkon aplikací s podporou cloudu.</span><span class="sxs-lookup"><span data-stu-id="b1635-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b1635-113">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="b1635-113">Mitigation</span></span>  
 <span data-ttu-id="b1635-114">U aplikací, u kterých tato změna nepříznivě ovlivnila, je možné nastavit dobu blokování fondu připojení nastavením vlastnosti nová <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1635-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="b1635-115">Hodnota vlastnosti je členem výčtu <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType>, který může převzít jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="b1635-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="b1635-116">Předchozí chování lze obnovit nastavením vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> na hodnotu <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1635-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1635-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1635-117">See also</span></span>

- [<span data-ttu-id="b1635-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="b1635-118">Application compatibility</span></span>](application-compatibility.md)
