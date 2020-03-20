---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858977"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey vrátí funkce RSACng na net462 (nebo lightup) bez změny retargetingu.

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6.2, konkrétní typ <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> objektu vrácené metodou změněn (bez vtípek) z implementace CryptoServiceProvider na implementaci CNG. Důvodem je, že <code>certificate.PublicKey.Key</code> implementace se <code>certificate.GetAnyPublicKey</code> změnila z <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>použití pomocí vnitřní, která předává do .|
|Návrh|Počínaje aplikacemi spuštěnými v rozhraní .NET Framework 4.7.1 můžete použít implementaci CryptoServiceProvider používanou ve výchozím nastavení v rozhraní .NET Framework 4.6.1 a starších verzích přidáním následujícího konfiguračního přepínače do sekce [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
