---
ms.openlocfilehash: fa09831ac47a59535ff73c8c8680c2642c3248c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981532"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>Používá SqlBulkCopy. cílový sloupec kódování pro řetězce

|   |   |
|---|---|
|Podrobnosti|Při vkládání dat do sloupce <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> používá kódování cílového sloupce namísto výchozího kódování pro <code>VARCHAR</code> a <code>CHAR</code> typy. Tato změna eliminuje možnost poškození dat při použití výchozího kódování, pokud cílový sloupec nepoužívá výchozí kódování. Ve výjimečných případech může existující aplikace vyvolat SqlException – výjimka, pokud změna kódování vytvoří data, která se nevejdou do cílového sloupce.|
|Doporučení|Očekávat, že <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> se už poškodit data kvůli kódování rozdíly. Pokud se blíží limitu velikosti cílový sloupec řetězce se kopírují, může být potřeba buď předem kódování dat (které se mají zkopírovat ke kontrole, že se data vejdou do cílového sloupce) nebo zachytit <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|
