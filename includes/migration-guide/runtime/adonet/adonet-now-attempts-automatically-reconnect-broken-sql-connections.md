---
ms.openlocfilehash: 4c65cd62b2d84ef2b852d10a04e5f6ce0cc82d3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648989"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET teď pokusí automaticky znovu připojila, přerušení připojení SQL

|   |   |
|---|---|
|Podrobnosti|Od rozhraní .NET Framework 4.5.1, rozhraní .NET Framework se pokusí automaticky znovu připojila, přerušení připojení SQL. I když to budou obvykle vytvořit obdobné aplikace spolehlivější, existují hraniční případy, kdy aplikace potřebuje vědět, že se ztratí připojení, tak, aby se provedlo určitou akci při opětovné připojení.|
|Doporučení|Pokud tato funkce nežádoucí z důvodu kompatibility, je možné ho zakázat nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> vlastnost připojovacího řetězce (nebo <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) na hodnotu 0.|
|Rozsah|Edge|
|Version|4.5.1|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|
