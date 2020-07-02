---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614538"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Výchozí algoritmy SignedXML a SignedXMS se změnily na SHA256

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,7 a starších verzích SignedXML a SignedCMS jako výchozí SHA1 pro některé operace. Počínaje .NET Framework 4.7.1 je SHA256 ve výchozím nastavení povolen pro tyto operace. Tato změna je nezbytná, protože SHA1 již není považována za zabezpečenou.

#### <a name="suggestion"></a>Návrh

Existují dvě nové hodnoty přepnutí kontextu, které určují, jestli se ve výchozím nastavení používá SHA1 (nezabezpečené) nebo SHA256:

- Switch.System.Security.Cryptography.Xml. UseInsecureHashAlgorithms
- Switch.System. Security. Cryptography. PKCS. UseInsecureHashAlgorithms pro aplikace cílené na .NET Framework 4.7.1 a novějších verzích, pokud je použití SHA256 nežádoucí, můžete obnovit výchozí hodnotu SHA1 přidáním následujícího konfiguračního přepínače do oddílu [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

Pro aplikace, které cílí na .NET Framework 4,7 a starší verze, se můžete přihlásit k této změně přidáním následujícího konfiguračního přepínače do oddílu [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
