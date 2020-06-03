---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720880"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo

Počínaje rozhraním .NET Core 3,0 Preview 9 `Pkcs8PrivateKeyInfo` konstruktor ověří `algorithmParameters` parametr jako jedinou hodnotu zakódovanou v ber.

#### <a name="change-description"></a>Popis změny

Před rozhraním .NET Core 3,0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil `algorithmParameters` argument.  Pokud tento argument představoval neplatnou hodnotu, konstruktor by byl úspěšný, ale volání jakékoli <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> metody,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> , nebo <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> by vyvolalo buď <xref:System.ArgumentException> pro argument, který nepřijal ( `preEncodedValue` ) nebo <xref:System.Security.Cryptography.CryptographicException> .

Pokud spustíte s .NET Core 3,0 před verzí Preview 9, následující kód vyvolá výjimku pouze v případě, že <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> je metoda volána:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Počínaje rozhraním .NET Core 3,0 Preview 9 je argument v konstruktoru ověřován a neplatná hodnota má za následek vyvolání metody <xref:System.Security.Cryptography.CryptographicException> . Tato změna přesune výjimku blíže ke zdroji chyby dat. Příklad:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Zajistěte, aby `algorithmParameters` byly zadány pouze platné hodnoty, nebo že volání `Pkcs8PrivateKeyInfo` testu konstruktoru pro obojí i v případě, že <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> je požadováno zpracování výjimek.

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
