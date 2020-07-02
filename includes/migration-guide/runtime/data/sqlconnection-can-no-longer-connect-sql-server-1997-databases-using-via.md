---
ms.openlocfilehash: 241184d61d718fedfea396260e739d2dbc05c305
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620002"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection se už nemůže připojit k SQL Server 1997 nebo databázím pomocí adaptéru VIA.

#### <a name="details"></a>Podrobnosti

Připojení k databázím SQL Server s využitím [protokolu s adaptérem virtuálního rozhraní (Via)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) už nejsou podporovaná. Protokol používaný pro připojení k databázi SQL Server je viditelný v připojovacím řetězci. PŘES připojení bude obsahovat prostřednictvím: &lt; servername &gt; . Pokud se tato aplikace připojuje k SQL prostřednictvím jiného protokolu než přes (TCP: nebo NP:), neobjeví se žádná neprůlomová změna. Připojení k SQL Server 7 (1997) už navíc nejsou podporovaná.

#### <a name="suggestion"></a>Návrh

Protokol VIA je zastaralý, proto by se měl použít alternativní protokol pro připojení k databázím SQL. Nejčastěji používaný protokol je TCP/IP. Další informace o připojení přes protokol TCP/IP najdete v tématu [Povolení protokolu TCP/IP pro instanci databáze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Pokud je databáze k databázi dostupná pouze v intranetu, protokol sdílených kanálů může poskytovat lepší výkon, pokud je síť pomalá.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)></li></ul>|
