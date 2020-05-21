---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720897"
---
### <a name="openssl-versions-on-macos"></a>Verze OpenSSL v macOS

Moduly runtime .NET Core 3,0 a novější v MacOS nyní upřednostňují OpenSSL verze 1.1. x pro OpenSSL 1.0. x pro <xref:System.Security.Cryptography.AesCcm> typy,,, <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> , <xref:System.Security.Cryptography.ECDsaOpenSsl> , <xref:System.Security.Cryptography.RSAOpenSsl> a <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .

Modul runtime .NET Core 2,1 teď podporuje verze OpenSSL 1.1. x, ale přesto upřednostňuje verze OpenSSL 1.0. x.

#### <a name="change-description"></a>Popis změny

V minulosti používal modul runtime .NET Core OpenSSL verze 1.0. x v macOS pro typy, které komunikují s OpenSSL. Nejnovější verze OpenSSL 1.0. x, OpenSSL 1.0.2, teď není podporovaná. Chcete-li zachovat typy, které používají OpenSSL na podporovaných verzích OpenSSL, rozhraní .NET Core 3,0 a novější modul runtime nyní používají novější verze OpenSSL v macOS.

Tato změna znamená, že chování pro modul runtime .NET Core v macOS je následující:

- Modul runtime .NET Core 3,0 a novější verze používá OpenSSL 1.1. x, pokud je k dispozici, a vraťte se do OpenSSL 1.0. x, pouze pokud není k dispozici žádná verze 1.1. x.

  Pro volající, kteří používají typy spolupráce OpenSSL s vlastními P/Invoke, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> komentářích. Vaše aplikace může selhat, pokud hodnotu nekontrolujete <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> .

- Modul runtime .NET Core 2,1 používá OpenSSL 1.0. x, pokud je k dispozici, a vrátí se k OpenSSL 1.1. x, pokud není k dispozici žádná verze 1.0. x.

  Modul runtime 2,1 preferuje starší verzi OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> , protože vlastnost v rozhraní .NET Core 2,1 neexistuje, takže verzi OpenSSL nelze spolehlivě určit v době běhu.

#### <a name="version-introduced"></a>Představená verze

- .NET Core 2.1.16
- .NET Core 3.0.3
- .NET Core 3.1.2

#### <a name="recommended-action"></a>Doporučená akce

- Odinstalujte OpenSSL verze 1.0.2, pokud ji už nepotřebujete.

- Pokud používáte <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> typy,, <xref:System.Security.Cryptography.DSAOpenSsl> ,, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> , <xref:System.Security.Cryptography.RSAOpenSsl> nebo <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , nainstalujte OpenSSL 1.1. x.

- Pokud používáte typy spolupráce OpenSSL s vlastními P/Invoke, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> komentářích.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
