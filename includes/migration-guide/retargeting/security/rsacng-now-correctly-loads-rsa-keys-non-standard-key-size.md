---
ms.openlocfilehash: 6d9f4b630e95d9a63393da3ae0ecd83c2b994712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859305"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng nyní správně načte klíče nestandardní velikost klíče RSA

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework verze starší než 4.6.2, jsou zákazníky s nestandardního velikostí klíče RSA certifikáty nelze získat přístup k tyto klíče účtů prostřednictvím <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> a <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> metody rozšíření.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zprávou &quot;požadovaná velikost klíče nepodporuje&quot; je vyvolána výjimka. V rozhraní .NET Framework 4.6.2 Tento problém vyřešen. Obdobně <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> a <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> teď pracovat s nestandardního velikostí klíče bez vyvolání <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Doporučení|Při zpracování logiky, která závisí na předchozím chování všech výjimek kde <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> je vyvolána při použití jsou nestandardní velikostí, zvažte odebrání logiku.|
|Scope|Edge|
|Version|4.6.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|

