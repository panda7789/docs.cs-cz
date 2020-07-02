---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620020"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Název souboru protokolu vytvořený metodou ObjectContext. CreateDatabase se změnil tak, aby odpovídal SQL Server specifikacím.

#### <a name="details"></a>Podrobnosti

Pokud <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> je metoda volána přímo nebo pomocí Code First se zprostředkovatelem SqlClient a hodnotou AttachDBFilename v připojovacím řetězci, vytvoří soubor protokolu s názvem filename_log. ldf namísto filename. ldf (kde filename je název souboru určeného hodnotou AttachDBFilename). Tato změna zlepšuje ladění poskytnutím souboru protokolu s názvem podle specifikace serveru SQL Server.

#### <a name="suggestion"></a>Návrh

Pokud je název souboru protokolu pro aplikaci důležitý, měla by být aplikace aktualizována tak, aby byla očekávána standardní _log formát názvu souboru. ldf.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
