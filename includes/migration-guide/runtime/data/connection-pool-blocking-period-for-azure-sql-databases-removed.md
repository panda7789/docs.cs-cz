---
ms.openlocfilehash: 33c262ebe131aade2b32d824395721f098640cf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857595"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Období blokování fondu připojení pro databáze Azure SQL se odebere

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6.2 pro otevřené požadavky připojení ke známým databázím Azure SQL (*.database.windows.net, *.database.chinacloudapi.cn, *.database.usgovcloudapi.net, *.database.cloudapi.de) je období blokování fondu připojení a chyby otevření připojení nejsou ukládány do mezipaměti. Pokusy o opakování otevřených požadavků připojení dojde téměř okamžitě po přechodných chyb připojení. Tato změna umožňuje pokus o otevření připojení se zopakovat okamžitě pro azure SQL databází, čímž se zlepší výkon aplikací s podporou cloudu. Pro všechny ostatní pokusy o připojení období blokování fondu připojení je nadále vynuceno.<p/>V rozhraní .NET Framework 4.6.1 a starších verzích, když aplikace narazí na selhání přechodného připojení při připojení k databázi, nelze pokus o připojení zopakovat rychle, protože fond připojení ukládá chybu do mezipaměti a znovu ji vyvolá na 5 sekund až 1 Minutu. Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, které často selžou s přechodnými chybami, které se obvykle obnovují během několika sekund. Funkce blokování fondu připojení znamená, že aplikace nemůže připojit k databázi po dlouhou dobu, i když databáze je k dispozici a aplikace potřebuje vykreslit během několika sekund.|
|Návrh|Pokud je toto chování nežádoucí, může být doba <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> blokování fondu připojení nakonfigurována nastavením vlastnosti zavedené v rozhraní .NET Framework 4.6.2. Hodnota vlastnosti je členem výčtu, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> který může trvat jednu ze tří hodnot:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Předchozí chování lze obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> vlastnosti na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
