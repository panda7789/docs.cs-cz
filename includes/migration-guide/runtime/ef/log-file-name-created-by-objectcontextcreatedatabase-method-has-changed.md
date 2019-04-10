---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235391"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Změnil se název souboru protokolu vytvořené metodou ObjectContext.CreateDatabase tak, aby odpovídaly specifikace serveru SQL Server

|   |   |
|---|---|
|Podrobnosti|Když <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda je volána buď přímo nebo pomocí Code First se zprostředkovatelem SqlClient a je hodnota AttachDBFilename připojovacího řetězce, vytvoří soubor protokolu s názvem filename_log.ldf místo filename.ldf (kde název_souboru je název soubor určený hodnotou AttachDBFilename). Tato změna zlepšuje ladění poskytnutím souboru protokolu s názvem podle specifikace serveru SQL Server.|
|Doporučení|Pokud název souboru protokolu je důležité pro aplikace, aplikace se musí aktualizovat můžete očekávat formát názvu souboru standardní _log.ldf.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
