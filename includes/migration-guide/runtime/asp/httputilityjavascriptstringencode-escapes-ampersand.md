---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619924"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>Ampersand – HttpUtility. JavaScriptStringEncode – řídicí znaky

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> řídí znak ampersand ( &amp; ).

#### <a name="suggestion"></a>Návrh

Pokud vaše aplikace závisí na předchozím chování této metody, můžete přidat nastavení ASPNET: JavaScriptDoNotEncodeAmpersand do [elementu ASP.NET appSettings](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) v konfiguračním souboru.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
