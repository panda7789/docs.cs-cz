---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619918"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>Vlastnost HttpRequest. ContentEncoding zakazuje UTF7.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5 je kódování UTF-7 v <xref:System.Web.HttpRequest?displayProperty=fullName> útvarech s zakázáno. Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.

#### <a name="suggestion"></a>Návrh

V ideálním případě by se měly aplikace aktualizovat tak, aby nepoužívaly kódování UTF-7 v <xref:System.Web.HttpRequest?displayProperty=fullName> s. Alternativně je možné obnovit starší chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atributu elementu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
