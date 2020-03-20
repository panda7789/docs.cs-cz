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
# <a name="mitigation-pool-blocking-period"></a>Zmírnění rizik: Období blokování fondu
Období blokování fondu připojení bylo odebráno pro připojení k databázím Azure SQL.  
  
## <a name="additional-description"></a>Další popis  
 V rozhraní .NET Framework 4.6.1 a starších verzích, když aplikace narazí na selhání přechodného připojení při připojení k databázi, nelze pokus o připojení zopakovat rychle, protože fond připojení ukládá chybu do mezipaměti a znovu ji vyvolá na 5 sekund až 1 min. Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, které často selžou s přechodnými chybami, které se obvykle obnovují během několika sekund. Funkce blokování fondu připojení znamená, že aplikace nemůže připojit k databázi po delší dobu, i když databáze je k dispozici. Toto chování je obzvláště problematické pro webové aplikace, které se připojují k databázím Azure SQL a které je potřeba vykreslit během několika sekund.  
  
 Počínaje rozhraním .NET Framework 4.6.2 pro připojení otevřené požadavky na známé \*databáze Azure \*SQL \*(*.database.windows.net, .database.chinacloudapi.cn, .database.usgovcloudapi.net, .database.cloudapi.de), chyby otevření připojení nejsou uloženy do mezipaměti. Pro všechny ostatní pokusy o připojení období blokování fondu připojení je nadále vynuceno.  
  
## <a name="impact"></a>Dopad  
 Tato změna umožňuje pokus o otevření připojení, který se okamžitě zopakovává pro databáze Azure SQL, čímž se zlepší výkon aplikací s podporou cloudu.  
  
## <a name="mitigation"></a>Omezení rizik  
 U aplikací, které jsou touto změnou nepříznivě ovlivněny, lze <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> nakonfigurovat období blokování fondu připojení nastavením nové vlastnosti.  Hodnota vlastnosti je členem výčtu, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> který může trvat jednu ze tří hodnot:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Předchozí chování lze obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnosti na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
