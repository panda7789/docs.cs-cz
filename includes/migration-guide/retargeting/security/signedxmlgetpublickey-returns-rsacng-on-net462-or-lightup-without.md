---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234892"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey vrátí RSACng net462 (nebo lightup) bez změny mění se cílení

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, konkrétní typ objektu vrácený <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> metodu změnit (bez datového toku zvuku nabízí) od implementace CryptoServiceProvider pro implementaci Cng. Důvodem je, že implementace změnit pomocí <code>certificate.PublicKey.Key</code> pomocí vnitřní <code>certificate.GetAnyPublicKey</code> který předá do <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Doporučení|Počínaje aplikací běžících na rozhraní .NET Framework 4.7.1, můžete použít CryptoServiceProvider implementace používá ve výchozím nastavení v rozhraní .NET Framework 4.6.1 a starší verze tak, že přidáte následující konfigurační přepnout na [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
