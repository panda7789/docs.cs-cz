---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721197"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3,0 upřednostňuje OpenSSL 1.1. x až OpenSSL 1.0. x

Rozhraní .NET Core pro Linux, které funguje v různých distribucích systému Linux, může podporovat OpenSSL 1.0. x i OpenSSL 1.1. x.  .NET Core 2,1 a .NET Core 2,2 hledejte nejprve 1,0. x a potom se vraťte na verzi 1.1. x; .NET Core 3,0 nejprve vyhledá 1.1. x. Tato změna byla provedena za účelem přidání podpory pro nové kryptografické standardy.

Tato změna může mít vliv na knihovny nebo aplikace, které podporují interoperabilitu platforem s typy spolupráce OpenSSL specifickými pro .NET Core.

#### <a name="change-description"></a>Popis změny

V .NET Core 2,2 a starších verzích modul runtime upřednostňuje načítání OpenSSL 1.0. x přes 1.1. x. To znamená, že <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> typy a pro interoperabilitu s OpenSSL se používají s libcrypto. so. 1.0.0/libcrypto. so. 1,0/libcrypto. so. 10 Podle preference.

Počínaje rozhraním .NET Core 3,0, modul runtime upřednostňuje načtení OpenSSL 1.1. x nad OpenSSL 1.0. x, takže <xref:System.IntPtr> typy a <xref:System.Runtime.InteropServices.SafeHandle> pro spolupráci s OpenSSL se používají s libcrypto. proto. 1.1/libcrypto. so. 11/libcrypto. so. 1.1.0/libcrypto. tak. 1.1.1 podle preference. V důsledku toho můžou knihovny a aplikace, které spolupracují s OpenSSL, mít při upgradu z .NET Core 2,1 nebo .NET Core 2,2 nekompatibilní ukazatele s hodnotami vystavenými .NET Core.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Knihovny a aplikace, které provádějí přímé operace s OpenSSL, musí být opatrní, aby používaly stejnou verzi OpenSSL jako modul runtime .NET Core.

Všechny knihovny nebo aplikace, které používají <xref:System.IntPtr> nebo <xref:System.Runtime.InteropServices.SafeHandle> hodnoty z kryptografických typů .NET Core přímo s OpenSSL, by měly porovnat verzi knihovny, kterou používá, s novou <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> vlastností, aby bylo zajištěno, že jsou ukazatele kompatibilní.

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
