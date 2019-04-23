---
ms.openlocfilehash: fcaee245e98dfe71beb4042a2664a14b64cf2398
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803684"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>Připojení SqlConnection můžete už připojení k SQL Server 1997 nebo databáze pomocí adaptéru VIA

|   |   |
|---|---|
|Podrobnosti|Připojení k databázím SQL Server pomocí [virtuální rozhraní VIA (adaptér) protokol](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229%28v=sql.105%29) již nejsou podporovány. Protokol použitý pro připojení k databázi serveru SQL Server je viditelný v připojovacím řetězci. Bude obsahovat VIA připojení přes:&lt;servername&gt;. Pokud tato aplikace se připojuje k SQL přes protokol než VIA (tcp: nebo np: například), pak se setkáte žádné rozbíjející změny. Také připojení k SQL serveru 7 (1997) již nejsou podporovány.|
|Doporučení|Protokolu VIA je zastaralý, tak alternativní protokol se má použít pro připojení k databázím SQL. Nejběžnější protokol použitý je protokol TCP/IP. Další informace o připojení prostřednictvím protokolu TCP/IP naleznete v tématu [protokol TCP/IP pro instanci databáze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Pokud databázi přistupuje pouze z v rámci sítě intranet, protokol sdíleného kanálů může poskytovat lepší výkon, pokud je pomalé síti.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|
