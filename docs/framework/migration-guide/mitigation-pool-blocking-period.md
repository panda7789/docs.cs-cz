---
title: 'Zmírnění rizika: doba blokování fondu'
description: Naučte se, jak zmírnit problémy způsobené tím, že dojde k odebrání období blokování pro připojení k databázím Azure SQL.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: be60fe87952697d964571176743a4e6f839c4894
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475408"
---
# <a name="mitigation-pool-blocking-period"></a>Zmírnění rizika: doba blokování fondu
Bylo odebráno období blokování fondu připojení pro připojení k databázím Azure SQL.  
  
## <a name="additional-description"></a>Další popis  
 Pokud se v .NET Framework 4.6.1 a starších verzích při připojování k databázi stala chyba přechodného připojení, pokus o připojení se nedá opakovat, protože fond připojení tuto chybu ukládá do mezipaměti a znovu ho vyvolá po dobu 5 sekund až 1 min. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, což často selhává kvůli přechodným chybám, které se obvykle obnovují během několika sekund. Funkce blokování fondu připojení znamená, že se aplikace nemůže po rozsáhlé době připojit k databázi, a to i v případě, že je databáze k dispozici. Toto chování je obzvláště problematické u webových aplikací, které se připojují k databázím SQL Azure a které je potřeba vykreslit během několika sekund.  
  
 Počínaje .NET Framework 4.6.2 se pro žádosti o otevření připojení ke známým databázím SQL Azure (*. database.windows.net, \* . Database.chinacloudapi.cn, \* . Database.usgovcloudapi.NET, \* . Database.cloudapi.de) neukládají do mezipaměti otevřené připojení. U všech dalších pokusů o připojení se i nadále vynutilo období blokování fondu připojení.  
  
## <a name="impact"></a>Dopad  
 Tato změna umožňuje okamžité opakování pokusu o připojení pro databáze SQL Azure, což zlepšuje výkon aplikací s podporou cloudu.  
  
## <a name="mitigation"></a>Omezení rizik  
 U aplikací, u kterých tato změna nepříznivě ovlivnila, je možné nastavit dobu blokování fondu připojení nastavením nové <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> Vlastnosti.  Hodnota vlastnosti je členem <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> výčtu, který může převzít jednu ze tří hodnot:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Předchozí chování lze obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnosti na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
