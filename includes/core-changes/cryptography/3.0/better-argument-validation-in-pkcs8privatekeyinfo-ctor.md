---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449209"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepší ověření argumentu v konstruktoru Pkcs8PrivateKeyInfo

Počínaje rozhraním .NET Core 3.0 Preview `Pkcs8PrivateKeyInfo` 9 `algorithmParameters` konstruktor ověří parametr jako jednu hodnotu kódovku KÓDované ber.

#### <a name="change-description"></a>Popis změny

Před .NET Core 3.0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil `algorithmParameters` argument.  Pokud tento argument představuje neplatnou hodnotu, konstruktor by <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>uspěl, ale volání některé z metod <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, nebo <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> by vyvolalo buď <xref:System.ArgumentException> argument pro, který nepřijali (`preEncodedValue`) nebo . <xref:System.Security.Cryptography.CryptographicException>

Pokud spustit s .NET Core 3.0 před náhledem 9, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> následující kód vyvolá výjimku pouze při volání metody:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Počínaje .NET Core 3.0 Náhled 9 argument je ověřen v konstruktoru a neplatná <xref:System.Security.Cryptography.CryptographicException>hodnota má za následek metodu vyvolání . Tato změna přesune výjimku blíže ke zdroji chyby dat. Například:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Ujistěte se, že jsou k dispozici `algorithmParameters` `Pkcs8PrivateKeyInfo` pouze platné hodnoty, nebo že volání testu konstruktoru pro oba <xref:System.ArgumentException> a <xref:System.Security.Cryptography.CryptographicException> pokud je požadováno zpracování výjimek.

### <a name="category"></a>Kategorie

Kryptografie

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
