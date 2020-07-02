---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619999"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy používá pro řetězce kódování cílového sloupce.

#### <a name="details"></a>Podrobnosti

Při vkládání dat do sloupce <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> používá místo výchozího kódování pro a typy kódování cílového sloupce <code>VARCHAR</code> <code>CHAR</code> . Tato změna eliminuje možnost poškození dat při použití výchozího kódování, pokud cílový sloupec nepoužívá výchozí kódování. Ve výjimečných případech může existující aplikace vyvolat výjimku SqlException, pokud změna kódování vytvoří data, která jsou příliš velká, aby se vešla do cílového sloupce.

#### <a name="suggestion"></a>Návrh

V <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> důsledku rozdílů v kódování se očekává, že už nebudou poškozená data. Pokud se zkopírují řetězce v blízkosti limitu velikosti cílového sloupce, může být nutné buď předem kódovat data (aby bylo možné ověřit, že se data vejdou do cílového sloupce), nebo zachytit <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> s.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
