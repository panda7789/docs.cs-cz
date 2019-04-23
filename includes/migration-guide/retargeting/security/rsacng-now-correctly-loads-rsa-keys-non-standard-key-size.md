---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803722"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng nyní správně načte klíče nestandardní velikost klíče RSA

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework verze starší než 4.6.2, jsou zákazníky s nestandardního velikostí klíče RSA certifikáty nelze získat přístup k tyto klíče účtů prostřednictvím <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> a <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> metody rozšíření.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zprávou &quot;požadovaná velikost klíče nepodporuje&quot; je vyvolána výjimka. V rozhraní .NET Framework 4.6.2 Tento problém vyřešen. Obdobně <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> a <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> teď pracovat s nestandardního velikostí klíče bez vyvolání <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Doporučení|Při zpracování logiky, která závisí na předchozím chování všech výjimek kde <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> je vyvolána při použití jsou nestandardní velikostí, zvažte odebrání logiku.|
|Rozsah|Edge|
|Version|4.6.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
