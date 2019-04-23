---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803678"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>Vlastnost HttpRequest.ContentEncoding zakazuje UTF7

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, kódování UTF-7 je zakázáno v <xref:System.Web.HttpRequest?displayProperty=name>s "subjekty. Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.|
|Doporučení|V ideálním případě by měl používat v kódování UTF-7 aktualizují aplikace <xref:System.Web.HttpRequest?displayProperty=name>s. Alternativně lze obnovit starší chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atribut [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
