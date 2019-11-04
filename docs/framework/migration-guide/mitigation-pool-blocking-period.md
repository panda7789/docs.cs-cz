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
# <a name="mitigation-pool-blocking-period"></a>Zmírnění rizika: doba blokování fondu
Bylo odebráno období blokování fondu připojení pro připojení k databázím Azure SQL.  
  
## <a name="additional-description"></a>Další popis  
 Pokud se v .NET Framework 4.6.1 a starších verzích při připojování k databázi stala chyba přechodného připojení, pokus o připojení se nedá opakovat, protože fond připojení tuto chybu ukládá do mezipaměti a znovu ho vyvolá po dobu 5 sekund až 1. dlouhé. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, což často selhává kvůli přechodným chybám, které se obvykle obnovují během několika sekund. Funkce blokování fondu připojení znamená, že se aplikace nemůže po rozsáhlé době připojit k databázi, a to i v případě, že je databáze k dispozici. Toto chování je obzvláště problematické u webových aplikací, které se připojují k databázím SQL Azure a které je potřeba vykreslit během několika sekund.  
  
 Počínaje .NET Framework 4.6.2, pro žádosti o otevření připojení ke známým databázím Azure SQL (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), připojení otevřené chyby nejsou ukládány do mezipaměti. U všech dalších pokusů o připojení se i nadále vynutilo období blokování fondu připojení.  
  
## <a name="impact"></a>Dopad  
 Tato změna umožňuje okamžité opakování pokusu o připojení pro databáze SQL Azure, což zlepšuje výkon aplikací s podporou cloudu.  
  
## <a name="mitigation"></a>Zmírnění  
 U aplikací, u kterých tato změna nepříznivě ovlivnila, je možné nastavit dobu blokování fondu připojení nastavením vlastnosti nová <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.  Hodnota vlastnosti je členem výčtu <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType>, který může převzít jednu ze tří hodnot:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Předchozí chování lze obnovit nastavením vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> na hodnotu <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
