---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619945"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET se teď pokusí automaticky znovu připojit k přerušeným připojením SQL.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.5.1 se .NET Framework pokusí automaticky znovu připojit přerušená připojení SQL. I když se tím obvykle aplikace spolehlivější, existují hraniční případy, ve kterých aplikace potřebuje znát, že připojení bylo ztraceno, aby mohlo při opětovném připojení provést nějakou akci.

#### <a name="suggestion"></a>Návrh

Pokud je tato funkce nežádoucí kvůli problémům s kompatibilitou, může být zakázána nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> vlastnosti připojovacího řetězce (nebo <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> ) na hodnotu 0.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
