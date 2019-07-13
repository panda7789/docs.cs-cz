---
ms.openlocfilehash: 9605352c66f85b6942ba24942cb07c88bdd81f2a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857595"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Odebrat fond připojení blokování období pro Azure SQL Database

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, pro připojení k otevření žádosti o známých databází Azure SQL (*. database.windows.net, *. database.chinacloudapi.cn, *. database.usgovcloudapi.net, *. database.cloudapi.de), fond připojení je blokování období odebrat, a otevřete chyb připojení nejsou uložené v mezipaměti. Pokusy o opakování otevřené žádosti o připojení dojde k téměř okamžitě po připojení přechodné chyby. Tato změna umožňuje otevřít pokus o připojení k opakovat okamžitě pro Azure SQL Database, následné vylepšení výkonu aplikací pro cloud-povoleno. Pro všechny ostatní pokusy o připojení pokračuje v období blokování fondu připojení vynucení.<p/>V rozhraní .NET Framework 4.6.1 a starší verze pokud aplikace zjistí chyba přechodného připojení při připojování k databázi, pokus o připojení se nedá opakovat, rychle, protože fond připojení ukládá do mezipaměti, chyby a znovu vyvolá po dobu 5 sekund do 1 minuty. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, které často dojde k přechodným chybám, které jsou obvykle obnovila během několika sekund. Blokuje funkce fondu připojení znamená, že aplikace nemůže připojit k databázi rozsáhlé dobu, i když je k dispozici databáze a aplikace je potřeba vykreslit během několika sekund.|
|Doporučení|Pokud toto chování nežádoucí, v období blokování fondu připojení lze nastavit tak, že nastavíte <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> vlastnost zavedena v rozhraní .NET Framework 4.6.2. Hodnota vlastnosti je členem skupiny <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> výčet, který může mít jednu ze tří hodnot:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Předchozí chování můžete obnovit nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> vlastnost <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

