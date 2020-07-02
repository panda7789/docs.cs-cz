---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614437"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>Algoritmem RSACng nyní správně načítá klíče RSA nestandardní velikosti klíče.

#### <a name="details"></a>Podrobnosti

V .NET Framework verzích starších než 4.6.2 zákazníci, kteří mají nestandardní velikosti klíčů pro certifikáty RSA, nemůžou získat přístup k těmto klíčům prostřednictvím <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> rozšiřujících metod a.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> se zprávou &quot; , že požadovaná velikost klíče není podporována, &quot; je vyvolána. V .NET Framework 4.6.2 Tento problém byl vyřešen. Podobně <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> a <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> teď můžete pracovat s nestandardními velikostmi klíčů bez vyvolání <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> .

#### <a name="suggestion"></a>Návrh

Pokud je k dispozici logika zpracování výjimek, která spoléhá na předchozí chování, kde <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> je vyvolána při použití nestandardních velikostí klíčů, zvažte odebrání logiky.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
