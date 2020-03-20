---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859305"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng nyní správně načte rsa klíče nestandardní velikosti klíče

|   |   |
|---|---|
|Podrobnosti|Ve verzích rozhraní .NET Framework před verzí 4.6.2 nemají zákazníci s nestandardními velikostmi <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> klíčů pro certifikáty RSA přístup k těmto klíčům prostřednictvím metod a extension.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> se &quot;zprávou Je vyvolána&quot; požadovaná velikost klíče. V rozhraní .NET Framework 4.6.2 byl tento problém opraven. Podobně a <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> nyní pracovat s nestandardní velikosti kláves <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>bez házení .|
|Návrh|Pokud existuje logika zpracování výjimek, která závisí <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> na předchozí chování, kde je vyvolána při použití nestandardní velikosti klíče, zvažte odebrání logiky.|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
