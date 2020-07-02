---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620110"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException – nyní nastavuje pozice řádků správně

#### <a name="details"></a>Podrobnosti

Pokud <xref:System.Xml.Linq.LoadOptions.SetLineInfo> je hodnota předána metodě Load a dojde k chybě ověření, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> vlastnosti a nyní obsahují informace o řádku.

#### <a name="suggestion"></a>Návrh

Kód pro zpracování výjimek, který předpokládá <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nebude nastaven, by měl být aktualizován, protože tyto vlastnosti budou nyní nastaveny správně, pokud se při načítání XML používá SetLineInfo.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
