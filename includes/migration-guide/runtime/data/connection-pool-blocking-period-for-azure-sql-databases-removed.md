---
ms.openlocfilehash: d7a18a0b457c2a38f40c1da3b2f0bfc578259475
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621067"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Doba blokování fondu připojení pro databáze SQL Azure je odebraná.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.6.2 platí, že pro žádosti o otevření připojení ke známým databázím Azure SQL ( \* . Database.Windows.NET,. \* Database.chinacloudapi.cn, \* . database.usgovcloudapi.net, \* . Database.cloudapi.de) se odeberou dobu blokování fondu připojení a chyby otevření připojení se neukládají do mezipaměti. Pokusí se znovu spustit žádosti o připojení, ke kterým dojde téměř hned po přechodných chybách připojení. Tato změna umožňuje okamžité opakování pokusu o připojení pro databáze SQL Azure, což zlepšuje výkon aplikací s podporou cloudu. U všech dalších pokusů o připojení se i nadále vynutilo období blokování fondu připojení.<p/>Pokud se v .NET Framework 4.6.1 a starších verzích při připojování k databázi vyskytne přechodný výpadek připojení, pokus o připojení se nedá znovu zkusit znovu, protože fond připojení ukládá chybu do mezipaměti a znovu ji vyvolá po dobu 5 sekund až 1 minuty. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, což často selhává kvůli přechodným chybám, které se obvykle obnovují během několika sekund. Funkce blokování fondu připojení znamená, že se aplikace nemůže po rozsáhlé době připojit k databázi, a to i v případě, že je databáze k dispozici a aplikace musí vykreslovat během několika sekund.

#### <a name="suggestion"></a>Návrh

Je-li toto chování nežádoucí, lze nastavit dobu blokování fondu připojení nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> vlastnosti zavedené ve .NET Framework 4.6.2. Hodnota vlastnosti je členem <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> výčtu, který může převzít jednu ze tří hodnot:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Předchozí chování lze obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> vlastnosti na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
