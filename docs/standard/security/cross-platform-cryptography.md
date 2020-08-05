---
title: Kryptografie pro různé platformy v .NET Core a .NET 5
description: Seznamte se s možnostmi kryptografie na platformách, které podporuje .NET.
ms.date: 06/19/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography, cross-platform
- encryption, cross-platform
ms.openlocfilehash: 61fd49e53761deac278b770003eb97241b6c2be9
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557148"
---
# <a name="cross-platform-cryptography-in-net-core-and-net-5"></a>Kryptografie pro různé platformy v .NET Core a .NET 5

Kryptografické operace v .NET Core a .NET 5 provádí knihovny operačního systému (OS). Tato závislost má výhody:

* Aplikace .NET využívají spolehlivost operačního systému. Udržování kryptografických knihoven zabezpečených proti chybám zabezpečení je pro dodavatele operačního systému vysoká priorita. K tomu poskytují aktualizace, které by měli použít správci systému.
* Pokud jsou knihovny operačního systému ověřovány standardem FIPS, aplikace .NET mají přístup k algoritmům ověřovaným standardem FIPS.

Závislost na knihovnách operačního systému také znamená, že aplikace .NET můžou používat jenom kryptografické funkce podporované operačním systémem. I když všechny platformy podporují určité základní funkce, některé funkce, které rozhraní .NET podporuje, se na některých platformách nedají použít. Tento článek popisuje funkce, které jsou podporovány na jednotlivých platformách.

V tomto článku se předpokládá, že máte obeznámenou funkční technologii s kryptografií v .NET. Další informace najdete v tématu [model kryptografie .NET](cryptography-model.md) a [kryptografické služby .NET](cryptographic-services.md).

## <a name="hash-algorithms"></a>Algoritmy hash

Všechny třídy algoritmu hash a třídy HMAC (hash-based Message Authentication), včetně `*Managed` tříd, se odloží do knihoven operačního systému. I když se různé knihovny operačního systému liší v výkonu, měly by být kompatibilní.

## <a name="symmetric-encryption"></a>Symetrické šifrování

Základní šifry a řetězení provádí systémové knihovny a všechny jsou podporovány všemi platformami.

| Cipher + – režim | Windows | Linux | macOS |
|---------------|---------|-------|-------|
| AES – CBC       | ✔️     | ✔️    | ✔️   |
| AES – ECB       | ✔️     | ✔️    | ✔️   |
| 3DES – CBC      | ✔️     | ✔️    | ✔️   |
| 3DES – ECB      | ✔️     | ✔️    | ✔️   |
| DES – CBC       | ✔️     | ✔️    | ✔️   |
| DES – ECB       | ✔️     | ✔️    | ✔️   |

## <a name="authenticated-encryption"></a>Ověřené šifrování

Pro AES-CCM a AES-GCM prostřednictvím tříd a se poskytuje podpora ověřeného šifrování (AE) <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName> <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName> .

V systémech Windows a Linux jsou implementace AES-CCM a AES-GCM poskytovány knihovnami operačních systémů.

### <a name="aes-ccm-and-aes-gcm-on-macos"></a>AES-CCM a AES-GCM v macOS

V macOS systémové knihovny nepodporují AES-CCM nebo AES-GCM pro kód třetí strany, takže <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> třídy a používají OpenSSL pro podporu. Uživatelé na macOS musí získat odpovídající kopii OpenSSL (libcrypto), aby tyto typy fungovaly, a musí být v cestě, kterou by systém načetl do knihovny ve výchozím nastavení. Doporučujeme nainstalovat OpenSSL ze Správce balíčků, jako je homebrew.

`libcrypto.0.9.7.dylib`Knihovny a `libcrypto.0.9.8.dylib` zahrnuté v MacOS jsou z dřívějších verzí OpenSSL a nebudou použity. `libcrypto.35.dylib`Knihovny, `libcrypto.41.dylib` a `libcrypto.42.dylib` jsou z LibreSSL a nebudou použity.

### <a name="aes-ccm-keys-nonces-and-tags"></a>Klíče AES-CCM, hodnoty nonce a značky

* Velikosti klíčů

  AES-CCM funguje s 128, 192 a 256 bitovými klíči.

* Velikosti nonce

  <xref:System.Security.Cryptography.AesCcm>Třída podporuje hodnoty nonce 56, 64, 72, 80, 88, 96 a 104 (7, 8, 9, 10, 11, 12 a 13 bajtů).

* Velikosti značek

  <xref:System.Security.Cryptography.AesCcm>Třída podporuje vytváření a zpracování značek 32, 48, 64, 80, 96, 112 a 128 (4, 8, 10, 12, 14 a 16 bajtů).

### <a name="aes-gcm-keys-nonces-and-tags"></a>AES-GCM klíče, hodnoty nonce a značky

* Velikosti klíčů

  AES-GCM funguje s 128, 192em a 256 bitovými klíči.

* Velikosti nonce

  <xref:System.Security.Cryptography.AesGcm>Třída podporuje pouze 96 (12 bajtů) náhodně.

* Velikosti značek

  <xref:System.Security.Cryptography.AesGcm>Třída podporuje vytváření a zpracování značek 96, 104, 112, 120 a 128 (12, 13, 14, 15 a 16 bajtů).

## <a name="asymmetric-cryptography"></a>Asymetrické šifrování

Tato část obsahuje následující pododdíly:

* [RSA](#rsa)
* [ECDSA](#ecdsa)
* [ECDH](#ecdh)
* [DSA](#dsa)

### <a name="rsa"></a>RSA

Generování klíče RSA (Rivest – Shamir – Adleman) provádí knihovny operačního systému a podléhá omezením velikosti a charakteristikám výkonu.

Klíčové operace RSA provádí knihovny operačního systému a typy klíčů, které se dají načíst, podléhají požadavkům na operační systém.

Rozhraní .NET nezveřejňuje "raw" (nedoplněno) operace RSA.

Knihovny operačního systému se používají k šifrování a dekódování dešifrování. Ne všechny platformy podporují stejné možnosti odsazení:

| Režim odsazení                          | Windows (CNG) | Linux (OpenSSL) | macOS | Windows (CAPI) |
|---------------------------------------|---------------|-----------------|-------|----------------|
| Šifrování výplně PKCS1                      | ✔️           | ✔️              | ✔️   | ✔️             |
| VÝPLNĚ OAEP-SHA-1                          | ✔️           | ✔️              | ✔️   | ✔️             |
| VÝPLNĚ OAEP-SHA-2 (SHA256, SHA384, SHA512) | ✔️           | ✔️              | ✔️   | ❌             |
| Signatura výplně PKCS1 (MD5, SHA-1)          | ✔️           | ✔️              | ✔️   | ✔️             |
| Podpis výplně PKCS1 (SHA-2)               | ✔️           | ✔️              | ✔️   | ⚠️\*           |
| POMOC                                   | ✔️           | ✔️              | ✔️   | ❌             |

\*Rozhraní Windows CryptoAPI (CAPI) je schopné výplně PKCS1 signatury pomocí algoritmu SHA-2. Ale jednotlivý objekt RSA může být načtený ve zprostředkovateli kryptografických služeb (CSP), který ho nepodporuje.

#### <a name="rsa-on-windows"></a>RSA ve Windows

* Rozhraní Windows CryptoAPI (CAPI) se používá vždy [`new RSACryptoServiceProvider()`](xref:System.Security.Cryptography.RSACryptoServiceProvider) , když se používá.
* Rozhraní Windows Cryptography API Next Generation (CNG) se používá [`new RSACng()`](xref:System.Security.Cryptography.RSACng) , když se použije.
* Objekt vrácený funkcí <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> je interně poháněný Windows CNG. Toto použití kryptografické služby Windows CNG je detailní detailem implementace a může se změnit.
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A>Metoda rozšíření pro <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> vrací <xref:System.Security.Cryptography.RSACng> instanci. Toto použití <xref:System.Security.Cryptography.RSACng> je podrobností implementace a může se změnit.
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A>Metoda rozšíření pro <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> aktuálně upřednostňuje <xref:System.Security.Cryptography.RSACng> instanci, ale <xref:System.Security.Cryptography.RSACng> v případě, že se klíč nemůže otevřít, <xref:System.Security.Cryptography.RSACryptoServiceProvider> bude proveden pokus. Upřednostňovaným poskytovatelem je podrobný popis implementace a může se změnit.

#### <a name="rsa-native-interop"></a>Nativní interoperabilita RSA

Rozhraní .NET zpřístupňuje typy, které umožní programům spolupracovat s knihovnami operačních systémů, které používá kryptografický kód .NET. Související typy se nepřevádí mezi platformami a měly by být v případě potřeby přímo použity.

| Typ                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.RSACryptoServiceProvider> | ✔️     | ⚠️<sup>první</sup>| ⚠️<sup>první</sup> |
| <xref:System.Security.Cryptography.RSACng>                   | ✔️     | ❌            | ❌            |
| <xref:System.Security.Cryptography.RSAOpenSsl>               | ❌     | ✔️            | ⚠️<sup>odst</sup> |

<sup>1</sup> v MacOS a Linux se <xref:System.Security.Cryptography.RSACryptoServiceProvider> dá použít k zajištění kompatibility s existujícími programy. V takovém případě jakákoli metoda, která vyžaduje interoperabilitu operačního systému, jako je například otevření pojmenovaného klíče, vyvolá <xref:System.PlatformNotSupportedException> .

<sup>2</sup> v MacOS <xref:System.Security.Cryptography.RSAOpenSsl> funguje, pokud je nainstalován OpenSSL a odpovídající libcrypto DYLIB lze najít prostřednictvím dynamického načítání knihovny. Pokud nelze nalézt odpovídající knihovnu, budou vyvolány výjimky.

### <a name="ecdsa"></a>ECDSA

ECDSA (algoritmus digitálního podpisu s eliptickou křivkou) provádí knihovny operačního systému a podléhá omezením velikosti a charakteristikám výkonu.

ECDSAé klíčové křivky jsou definovány knihovnami operačních systémů a podléhají jejich omezením.

| Eliptická křivka                     | Windows 10    | Windows 7 – 8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| Brainpool křivky (jako pojmenované křivky) | ✔️           | ❌              | ⚠️<sup>první</sup>| ❌           |
| Další pojmenované křivky                 | ⚠️<sup>odst</sup>| ❌             | ⚠️<sup>první</sup>| ❌           |
| Explicitní křivky                    | ✔️           | ❌              | ✔️           | ❌            |
| Exportovat nebo importovat jako explicitní       | ✔️           | ❌<sup>1</sup>  | ✔️           | ❌<sup>1</sup>|

<sup>1</sup> distribuce systému Linux nemají podporu pro stejné pojmenované křivky.

<sup>2</sup> k Windows CNG ve Windows 10 se přidala podpora pro pojmenované křivky. Další informace najdete v tématu [CNG s názvem eliptické křivky](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx). Pojmenované křivky nejsou k dispozici v dřívějších verzích Windows, s výjimkou tří křivek ve Windows 7.

<sup>3</sup> export s explicitními parametry křivky vyžaduje podporu knihovny operačního systému, která není k dispozici v MacOS nebo starších verzích Windows.

#### <a name="ecdsa-native-interop"></a>Nativní spolupráce ECDSA

Rozhraní .NET zpřístupňuje typy, které umožní programům spolupracovat s knihovnami operačních systémů, které používá kryptografický kód .NET. Typy, které se nevztahují mezi platformami a měly by být v případě potřeby přímo použity.

| Typ                                             | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDsaCng>     | ✔️     | ❌    | ❌    |
| <xref:System.Security.Cryptography.ECDsaOpenSsl> | ❌     | ✔️    | ⚠️\*  |

\*V macOS <xref:System.Security.Cryptography.ECDsaOpenSsl> funguje, pokud je v systému nainstalováno OpenSSL, a odpovídající libcrypto DYLIB lze najít prostřednictvím dynamického načítání knihovny. Pokud nelze nalézt odpovídající knihovnu, budou vyvolány výjimky.

### <a name="ecdh"></a>ECDH

Generování klíče ECDH (eliptická křivka Diffie-Hellman) provádí knihovny operačního systému a podléhá omezením velikosti a charakteristikám výkonu.

<xref:System.Security.Cryptography.ECDiffieHellman>Třída nevrátí hodnotu "raw" výpočtu ECDH. Všechna vracená data jsou z podmínek odvození klíčových funkcí:

* HASH (Z)
* HASH (komentář | | Z | | příloh
* HMAC (klíč, Z)
* HMAC (klíč, komentář | | Z | | příloh
* HMAC (Z, Z)
* HMAC (Z, předřadit | | Z | | příloh
* Tls11Prf (popisek, osazení)

Základní křivky ECDH jsou definované knihovnami operačních systémů a podléhají jejich omezením.

| Eliptická křivka                     | Windows 10    | Windows 7 – 8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| brainpool křivky (jako pojmenované křivky) | ✔️           | ❌              | ⚠️<sup>první</sup>| ❌           |
| Další pojmenované křivky                 | ⚠️<sup>odst</sup>| ❌             | ⚠️<sup>první</sup>| ❌           |
| explicitní křivky                    | ✔️           | ❌              | ✔️           | ❌            |
| Exportovat nebo importovat jako explicitní       | ✔️           | ❌<sup>1</sup>  | ✔️           | ❌<sup>1</sup>|

<sup>1</sup> distribuce systému Linux nemají podporu pro stejné pojmenované křivky.

<sup>2</sup> k Windows CNG ve Windows 10 se přidala podpora pro pojmenované křivky. Další informace najdete v tématu [CNG s názvem eliptické křivky](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx). Pojmenované křivky nejsou k dispozici v dřívějších verzích Windows, s výjimkou tří křivek ve Windows 7.

<sup>3</sup> export s explicitními parametry křivky vyžaduje podporu knihovny operačního systému, která není k dispozici v MacOS nebo starších verzích Windows.

#### <a name="ecdh-native-interop"></a>Nativní interoperabilita ECDH

Rozhraní .NET zpřístupňuje typy, které umožní programům spolupracovat s knihovnami operačních systémů, které používá rozhraní .NET. Typy, které se nevztahují mezi platformami a měly by být v případě potřeby přímo použity.

| Typ                                                       | Windows | Linux | macOS |
|------------------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDiffieHellmanCng>     | ✔️     | ❌    | ❌   |
| <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> | ❌     | ✔️    | ⚠️\* |

\*V macOS <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> funguje, pokud je nainstalován OpenSSL a odpovídající libcrypto DYLIB lze najít prostřednictvím dynamického načítání knihovny. Pokud nelze nalézt odpovídající knihovnu, budou vyvolány výjimky.

### <a name="dsa"></a>DSA

Generování klíče DSA (Digital Signature Algorithm) provádí systémové knihovny a podléhá omezením velikosti a charakteristikám výkonu.

| Funkce                      | CNG Windows | Linux | macOS         | Rozhraní Windows CAPI |
|-------------------------------|-------------|-------|---------------|--------------|
| Vytvoření klíče (<= 1024 bitů)   | ✔️         | ✔️    | ❌            | ✔️           |
| Vytváření klíčů (> 1024 bitů)    | ✔️         | ✔️    | ❌            | ❌            |
| Načítání klíčů (<= 1024 bitů)   | ✔️         | ✔️    | ✔️            | ✔️           |
| Načítání klíčů (> 1024 bitů)    | ✔️         | ✔️    | ⚠️\*          | ❌            |
| FIPS 186-2                    | ✔️         | ✔️    | ✔️            | ✔️           |
| FIPS 186-3 (signatury SHA-2) | ✔️         | ✔️    | ❌            | ❌            |

\*macOS načítá klíče DSA větší než 1024 bitů, ale chování těchto klíčů není definováno. Nechovají se podle standardu FIPS 186-3.

#### <a name="dsa-on-windows"></a>DSA ve Windows

* Rozhraní Windows CryptoAPI (CAPI) se používá vždy [`new DSACryptoServiceProvider()`](xref:System.Security.Cryptography.DSACryptoServiceProvider) , když se používá.
* Rozhraní Windows Cryptography API Next Generation (CNG) se používá [`new DSACng()`](xref:System.Security.Cryptography.DSACng) , když se použije.
* Objekt vrácený funkcí <xref:System.Security.Cryptography.DSA.Create%2A?displayProperty=nameWithType> je interně poháněný Windows CNG. Toto použití kryptografické služby Windows CNG je detailní detailem implementace a může se změnit.
* <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A>Metoda rozšíření pro <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> vrací <xref:System.Security.Cryptography.DSACng> instanci. Toto použití <xref:System.Security.Cryptography.DSACng> je podrobností implementace a může se změnit.
* <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A>Metoda rozšíření pro <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> preferovanou <xref:System.Security.Cryptography.DSACng> instanci, ale <xref:System.Security.Cryptography.DSACng> v případě, že se klíč nemůže otevřít, se <xref:System.Security.Cryptography.DSACryptoServiceProvider> pokusí.  Upřednostňovaným poskytovatelem je podrobný popis implementace a může se změnit.

#### <a name="dsa-native-interop"></a>Nativní interoperabilita DSA

Rozhraní .NET zpřístupňuje typy, které umožní programům spolupracovat s knihovnami operačních systémů, které používá kryptografický kód .NET. Typy, které se nevztahují mezi platformami a měly by být v případě potřeby přímo použity.

| Typ                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.DSACryptoServiceProvider> | ✔️     | ⚠️<sup>první</sup> | ⚠️<sup>první</sup> |
| <xref:System.Security.Cryptography.DSACng>                   | ✔️     | ❌             | ❌            |
| <xref:System.Security.Cryptography.DSAOpenSsl>               | ❌      | ✔️            | ⚠️<sup>odst</sup> |

<sup>1</sup> v MacOS a Linux se <xref:System.Security.Cryptography.DSACryptoServiceProvider> dá použít k zajištění kompatibility s existujícími programy. V takovém případě jakákoliv metoda, která vyžaduje interoperabilitu systému, jako je například otevření pojmenovaného klíče, vyvolá <xref:System.PlatformNotSupportedException> .

<sup>2</sup> v MacOS <xref:System.Security.Cryptography.DSAOpenSsl> funguje, pokud je nainstalován OpenSSL a odpovídající libcrypto DYLIB lze najít prostřednictvím dynamického načítání knihovny. Pokud nelze nalézt odpovídající knihovnu, budou vyvolány výjimky.

## <a name="x509-certificates"></a>Certifikáty X. 509

Většina podpory pro certifikáty X. 509 v .NET přichází z knihoven operačních systémů. Chcete-li načíst certifikát do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.X509Certificates.X509Certificate> instance nebo v rozhraní .NET, je nutné certifikát načíst pomocí základní knihovny operačního systému.

### <a name="read-a-pkcs12pfx"></a>Přečíst PKCS12/PFX

| Scénář                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Obsahovat                                        | ✔️     | ✔️    | ✔️   |
| Jeden certifikát, žádný privátní klíč              | ✔️     | ✔️    | ✔️   |
| Jeden certifikát s privátním klíčem            | ✔️     | ✔️    | ✔️   |
| Více certifikátů, žádné soukromé klíče       | ✔️     | ✔️    | ✔️   |
| Více certifikátů, jeden privátní klíč       | ✔️     | ✔️    | ✔️   |
| Více certifikátů, více privátních klíčů | ✔️     | ⚠️\*  | ✔️   |

\*K dispozici v verzích .NET 5 Preview.

### <a name="write-a-pkcs12pfx"></a>Zápis PKCS12/PFX

| Scénář                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Obsahovat                                        | ✔️     | ✔️    | ⚠️\* |
| Jeden certifikát, žádný privátní klíč              | ✔️     | ✔️    | ⚠️\* |
| Jeden certifikát s privátním klíčem            | ✔️     | ✔️    | ✔️   |
| Více certifikátů, žádné soukromé klíče       | ✔️     | ✔️    | ⚠️\* |
| Více certifikátů, jeden privátní klíč       | ✔️     | ✔️    | ✔️   |
| Více certifikátů, více privátních klíčů | ✔️     | ⚠️\*  | ✔️   |
| Dočasné načítání                            | ✔️     | ✔️    | ⚠️\* |

\*K dispozici v verzích .NET 5 Preview.

macOS nemůže načíst soukromé klíče certifikátu bez objektu řetězce klíčů, který vyžaduje zápis na disk. Pro načítání PFX se vytvoří automatické řetězy klíčů, které se odstraní, když se už nepoužívají. Vzhledem k <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> tomu, že tato možnost znamená, že by se soukromý klíč neměl zapsat na disk, vytvrzením tohoto příznaku na MacOS dojde k <xref:System.PlatformNotSupportedException> .

### <a name="write-a-pkcs7-certificate-collection"></a>Zápis kolekce certifikátů PKCS7

Windows a Linux nagenerují objekty BLOB v systému PKCS7 kódované pomocí DER. macOS emituje neurčité objekty blob zakódované pomocí CER s neomezenou délkou.

### <a name="x509store"></a>X509Store

Ve Windows <xref:System.Security.Cryptography.X509Certificates.X509Store> je třída reprezentace rozhraní API úložiště certifikátů systému Windows. Tato rozhraní API fungují v rozhraní .NET Core a .NET 5 stejně jako v .NET Framework.

V <xref:System.Security.Cryptography.X509Certificates.X509Store> systému Linux je třída projekcí rozhodnutí o důvěryhodnosti systému (jen pro čtení), rozhodnutí o důvěryhodnosti uživatele (čtení i zápis) a úložiště klíčů uživatele (pro čtení i zápis).

V macOS <xref:System.Security.Cryptography.X509Certificates.X509Store> je třída projekcí rozhodnutí o důvěryhodnosti systému (jen pro čtení), rozhodnutí o důvěryhodnosti uživatele (jen pro čtení) a uživatelského úložiště klíčů (pro čtení i zápis).

V následujících tabulkách jsou uvedeny scénáře, které jsou podporovány v každé platformě. V případě nepodporovaných scénářů ( ❌ v tabulkách) <xref:System.Security.Cryptography.CryptographicException> je vyvolána výjimka.

#### <a name="the-my-store"></a>Moje úložiště

| Scénář                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Otevřít do currentuser\my (jen pro čtení)                   | ✔️     | ✔️    | ✔️   |
| Otevřít do currentuser\my (pro čtení)                  | ✔️     | ✔️    | ✔️   |
| Otevřít do currentuser\my (ExistingOnly)               | ✔️     | ⚠️    | ✔️   |
| Otevřít úložišti LocalMachine\MY                             | ✔️     | ❌    | ✔️   |

V systému Linux se obchody vytvoří při prvním zápisu a ve výchozím nastavení neexistují žádní uživatelská úložiště, takže otevírání `CurrentUser\My` pomocí se `ExistingOnly` nemusí zdařit.

V macOS `CurrentUser\My` je úložiště výchozí řetězec klíčů uživatele, který je `login.keychain` ve výchozím nastavení. `LocalMachine\My`Úložiště je `System.keychain` .

#### <a name="the-root-store"></a>Kořenové úložiště

| Scénář                              | Windows | Linux | macOS           |
|---------------------------------------|---------|-------|-----------------|
| Otevřít CurrentUser\Root (jen pro čtení)      | ✔️     | ✔️    | ✔️             |
| Otevřít CurrentUser\Root (pro čtení)     | ✔️     | ✔️    | ❌              |
| Otevřít CurrentUser\Root (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (pokud jen pro čtení) |
| Otevřít LocalMachine\Root (jen pro čtení)     | ✔️     | ✔️    | ✔️             |
| Otevřít LocalMachine\Root (pro čtení)    | ✔️     | ❌    | ❌              |
| Otevřít LocalMachine\Root (ExistingOnly) | ✔️     | ⚠️    | ✔️ (pokud jen pro čtení) |

V systému Linux `LocalMachine\Root` je úložiště výkladem sady certifikačních autorit ve výchozí cestě pro OpenSSL.

V macOS `CurrentUser\Root` je úložiště interpretací `SecTrustSettings` výsledků pro doménu důvěryhodnosti uživatele. `LocalMachine\Root`Úložiště je interpretací `SecTrustSettings` výsledků domén pro důvěryhodnost správců a systémů.

#### <a name="the-intermediate-store"></a>Zprostředkující úložiště

| Scénář                                      | Windows | Linux | macOS           |
|-----------------------------------------------|---------|-------|-----------------|
| Otevřít CurrentUser\Intermediate (jen pro čtení)      | ✔️     | ✔️    | ✔️             |
| Otevřít CurrentUser\Intermediate (pro čtení)     | ✔️     | ✔️    | ❌              |
| Otevřít CurrentUser\Intermediate (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (pokud jen pro čtení) |
| Otevřít LocalMachine\Intermediate (jen pro čtení)     | ✔️     | ✔️    | ✔️             |
| Otevřít LocalMachine\Intermediate (pro čtení)    | ✔️     | ❌    | ❌              |
| Otevřít LocalMachine\Intermediate (ExistingOnly) | ✔️     | ⚠️    | ✔️ (pokud jen pro čtení) |

V systému Linux se `CurrentUser\Intermediate` úložiště používá jako mezipaměť při stahování zprostředkujících certifikačních autorit podle svých záznamů o přístupu k informacím autority na úspěšných X509Chain sestaveních. `LocalMachine\Intermediate`Úložiště je interpretací sady prostředků certifikační autority ve výchozí cestě pro OpenSSL.

#### <a name="the-disallowed-store"></a>Nepovolený obchod

| Scénář                                    | Windows | Linux | macOS           |
|---------------------------------------------|---------|-------|-----------------|
| Otevřít CurrentUser\Disallowed (jen pro čtení)      | ✔️     | ⚠️    | ✔️             |
| Otevřít CurrentUser\Disallowed (pro čtení)     | ✔️     | ⚠️    | ❌              |
| Otevřít CurrentUser\Disallowed (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (pokud jen pro čtení) |
| Otevřít LocalMachine\Disallowed (jen pro čtení)     | ✔️     | ❌    | ✔️             |
| Otevřít LocalMachine\Disallowed (pro čtení)    | ✔️     | ❌    | ❌              |
| Otevřít LocalMachine\Disallowed (ExistingOnly) | ✔️     | ❌    | ✔️ (pokud jen pro čtení) |

V systému Linux se `Disallowed` úložiště nepoužívá v sestavování řetězu a při pokusu o přidání obsahu do něj dojde k <xref:System.Security.Cryptography.CryptographicException> . <xref:System.Security.Cryptography.CryptographicException>Vyvolaná výjimka při otevření `Disallowed` obchodu, pokud již získala obsah.

V macOS úložiště CurrentUser\Disallowed a LocalMachine\Disallowed jsou interpretace příslušných výsledků SecTrustSettings pro certifikáty, jejichž důvěryhodnost je nastavená na `Always Deny` .

#### <a name="nonexistent-store"></a>Neexistující úložiště

| Scénář                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Otevřít neexistující úložiště (ExistingOnly)           | ❌     | ❌     | ❌    |
| Otevřít neexistující úložiště CurrentUser  | ✔️     | ✔️     | ⚠️   |
| Otevřít neexistující úložiště LocalMachine | ✔️     | ❌     | ❌    |

V macOS se vlastní vytváření úložiště s rozhraním API X509Store podporuje jenom pro `CurrentUser` umístění. Vytvoří nový řetězec klíčů bez hesla v adresáři řetězce klíčů uživatele (*~/Library/Keychains*). Chcete-li vytvořit řetězec klíčů s heslem, lze použít volání nespravovaného řetězce `SecKeychainCreate` . Podobně lze `SecKeychainOpen` použít k otevření řetězců klíčů v různých umístěních. Výsledek `IntPtr` může být předán pro [`new X509Store(IntPtr)`](xref:System.Security.Cryptography.X509Certificates.X509Store.%23ctor(System.IntPtr)) získání úložiště s možností čtení/zápisu v závislosti na oprávněních aktuálního uživatele.

### <a name="x509chain"></a>X509Chain

macOS nepodporuje použití offline seznamů CRL, takže `X509RevocationMode.Offline` se považuje za `X509RevocationMode.Online` .

macOS nepodporuje stahování iniciované uživatelem u seznamu CRL (seznam odvolaných certifikátů)/protokolu OCSP (Online Certificate Status Protocol)/AIA (přístup k informacím autority), takže `X509ChainPolicy.UrlRetrievalTimeout` se ignoruje.

## <a name="additional-resources"></a>Další zdroje informací

* [Kryptografický model .NET](cryptography-model.md)
* [Kryptografické služby .NET](cryptographic-services.md)
* [Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC](vulnerabilities-cbc-mode.md)
* [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
