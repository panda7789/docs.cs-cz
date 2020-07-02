---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616044"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml. GetPublicKey vrátí algoritmem RSACng na net462 (nebo Lightup) bez změny cílení.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.6.2 se konkrétní typ objektu vráceného <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> metodou změnil (bez Quirk) z implementace CryptoServiceProvider pro implementaci CNG. Důvodem je to, že implementace se změnila z použití `certificate.PublicKey.Key` na použití interního, `certificate.GetAnyPublicKey` které je předáno <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> .

#### <a name="suggestion"></a>Návrh

Počínaje aplikacemi, které běží na .NET Framework 4.7.1, můžete použít implementaci CryptoServiceProvider použitou ve výchozím nastavení v .NET Framework 4.6.1 a starších verzích přidáním následujícího konfiguračního přepínače do oddílu [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
