---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619933"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode už nekóduje neplatné vstupní sekvence.

#### <a name="details"></a>Podrobnosti

Ve výchozím nastavení metody dekódování již neprovádějí dekódování neplatné vstupní sekvence do neplatného řetězce UTF-16. Namísto toho vracejí původní vstup.

#### <a name="suggestion"></a>Návrh

Změna dekodéru výstupu by měla mít vliv, pouze pokud do řetězců ukládáte binární data namísto dat UTF-16. Chcete-li toto chování explicitně řídit, nastavte <code>aspnet:AllowRelaxedUnicodeDecoding</code> atribut elementu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) na <code>true</code> , aby bylo možné povolit starší chování nebo <code>false</code> Povolit aktuální chování.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
