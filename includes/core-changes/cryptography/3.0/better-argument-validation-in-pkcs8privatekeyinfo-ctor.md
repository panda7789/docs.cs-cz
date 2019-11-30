---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568002"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo

Počínaje rozhraním .NET Core 3,0 Preview 9 konstruktor `Pkcs8PrivateKeyInfo` ověřuje parametr `algorithmParameters` jako jednu hodnotu kódovanou jako BER.

#### <a name="change-description"></a>Změnit popis

Před rozhraním .NET Core 3,0 Preview 9 [konstruktor`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil argument `algorithmParameters`.  Pokud tento argument představoval neplatnou hodnotu, konstruktor by byl úspěšný, ale volání jakékoli <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>nebo metody <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> by vyvolalo buď <xref:System.ArgumentException> pro argument, který nepřijal (`preEncodedValue`) nebo <xref:System.Security.Cryptography.CryptographicException>.

Pokud spustíte s .NET Core 3,0 před verzí Preview 9, následující kód vyvolá výjimku pouze v případě, že je volána metoda <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Počínaje rozhraním .NET Core 3,0 Preview 9 se v konstruktoru ověří argument a neplatná hodnota způsobí, že metoda vyvolává <xref:System.Security.Cryptography.CryptographicException>. Tato změna přesune výjimku blíže ke zdroji chyby dat. Příklad:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Zajistěte, aby byly zadány pouze platné hodnoty `algorithmParameters` nebo zda volání `Pkcs8PrivateKeyInfo` konstruktoru konstruktoru pro <xref:System.ArgumentException> a <xref:System.Security.Cryptography.CryptographicException>, pokud je požadováno zpracování výjimek.

### <a name="category"></a>Kategorie

Kryptografie

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
