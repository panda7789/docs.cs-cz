---
ms.openlocfilehash: 8790637c31d503455eb8ba722cca827c2a24b7c9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021444"
---
### <a name="openssl-versions-on-macos"></a>Verze OpenSSL v macOS

Rozhraní .NET Core 3.0 a novější runtimes v systému macOS nyní preferují verze OpenSSL 1.1.x <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>před <xref:System.Security.Cryptography.RSAOpenSsl>verzemi OpenSSL 1.0.x <xref:System.Security.Cryptography.SafeEvpPKeyHandle> pro typy <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, , , , .

Runtime .NET Core 2.1 nyní podporuje verze OpenSSL 1.1.x, ale stále preferuje verze OpenSSL 1.0.x.

#### <a name="change-description"></a>Popis změny

Dříve používal runtime .NET Core verze OpenSSL 1.0.x v systému macOS pro typy, které interagují s OpenSSL. Nejnovější verze OpenSSL 1.0.x, OpenSSL 1.0.2, je nyní mimo podporu. Chcete-li zachovat typy, které používají OpenSSL v podporovaných verzích OpenSSL, používají nyní moduly .NET Core 3.0 a novější moduly runtimes novější verze OpenSSL v systému macOS.

S touto změnou je chování pro běhové toruny jádra .NET v systému macOS následující:

- Za běhu .NET Core 3.0 a novější verze používají OpenSSL 1.1.x, pokud jsou k dispozici, a vrátí se zpět na OpenSSL 1.0.x pouze v případě, že není k dispozici verze 1.1.x.

  Pro volající, kteří používají OpenSSL interop typy s vlastní P/Invokes, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> poznámkách. Pokud hodnotu nezkontrolujete, <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> může dojít k chybě aplikace.

- Runtime .NET Core 2.1 používá OpenSSL 1.0.x, pokud je k dispozici, a přejde zpět na OpenSSL 1.1.x, pokud není k dispozici verze 1.0.x.

  Runtime 2.1 preferuje starší verzi OpenSSL, <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> protože vlastnost neexistuje v rozhraní .NET Core 2.1, takže verzi OpenSSL nelze spolehlivě určit za běhu.

#### <a name="version-introduced"></a>Zavedená verze

- .NET Jádro 2.1.16
- .NET Jádro 3.0.3
- .NET Jádro 3.1.2

#### <a name="recommended-action"></a>Doporučená akce

- Odinstalujte OpenSSL verze 1.0.2, pokud už není potřeba.

- <xref:System.Security.Cryptography.AesCcm>Pokud používáte typy , <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl>, , nebo <xref:System.Security.Cryptography.SafeEvpPKeyHandle> nainstalujete soubor OpenSSL 1.1.x.

- Pokud používáte OpenSSL interop typy s vlastní P/Invokes, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> poznámkách.

#### <a name="category"></a>Kategorie

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
