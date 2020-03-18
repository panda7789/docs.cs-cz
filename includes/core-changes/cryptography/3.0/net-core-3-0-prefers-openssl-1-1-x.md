---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568001"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 preferuje OpenSSL 1.1.x na OpenSSL 1.0.x

.NET Core pro Linux, který funguje napříč několika linuxovými distribucemi, může podporovat jak OpenSSL 1.0.x, tak OpenSSL 1.1.x.  .NET Core 2.1 a .NET Core 2.2 nejprve hledají 1.0.x, pak se vrátí na 1.1.x; .NET Core 3.0 hledá nejprve 1.1.x. Tato změna byla provedena přidat podporu pro nové kryptografické standardy.

Tato změna může mít vliv na knihovny nebo aplikace, které interop platformy s typy interop specifické pro OpenSSL v .NET Core.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2.2 a starších verzích preferuje runtime načítání OpenSSL 1.0.x před 1.1.x. To znamená, <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> že typy a pro interop s OpenSSL se používají s libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 podle preference.

Počínaje .NET Core 3.0, runtime preferuje načítání OpenSSL 1.1.x přes OpenSSL <xref:System.IntPtr> 1.0.x, takže typy a <xref:System.Runtime.InteropServices.SafeHandle> pro interop s OpenSSL se používají s libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1. V důsledku toho mohou mít knihovny a aplikace, které přímo spolupracují s OpenSSL, nekompatibilní ukazatele s hodnotami vystavenými jádrem .NET při upgradu z rozhraní .NET Core 2.1 nebo .NET Core 2.2.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Knihovny a aplikace, které provádějí přímé operace s OpenSSL, musí být pečlivě nutné zajistit, aby používaly stejnou verzi OpenSSL jako zaběhu .NET Core.

Všechny knihovny nebo <xref:System.IntPtr> aplikace, které používají nebo <xref:System.Runtime.InteropServices.SafeHandle> hodnoty z kryptografických typů .NET Core přímo <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> s OpenSSL by měl porovnat verzi knihovny, které používají s novou vlastnost, aby bylo zajištěno, že ukazatele jsou kompatibilní.

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

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
