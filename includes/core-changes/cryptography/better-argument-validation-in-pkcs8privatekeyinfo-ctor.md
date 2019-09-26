---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263317"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo

Počínaje rozhraním .NET Core 3,0 Preview 9 `Pkcs8PrivateKeyInfo` konstruktor ověří `algorithmParameters` parametr jako jedinou hodnotu zakódovanou v ber.

#### <a name="change-description"></a>Změnit popis

Před rozhraním .NET Core 3,0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil `algorithmParameters` argument.  Pokud tento argument představoval neplatnou hodnotu, konstruktor by byl úspěšný, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>ale volání kterékoli z metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, nebo <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> vyvolá buď <xref:System.ArgumentException> pro argument, který nepřijal (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>nebo.

Pokud spustíte s .NET Core 3,0 před verzí Preview 9, následující kód vyvolá výjimku pouze v případě, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> že je metoda volána:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Počínaje rozhraním .NET Core 3,0 Preview 9 je argument v konstruktoru ověřován a neplatná hodnota má za následek vyvolání <xref:System.Security.Cryptography.CryptographicException>metody. Tato změna přesune výjimku blíže ke zdroji chyby dat. Příklad:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Zajistěte, `algorithmParameters` aby byly zadány pouze platné hodnoty, nebo `Pkcs8PrivateKeyInfo` že volání testu konstruktoru <xref:System.ArgumentException> pro <xref:System.Security.Cryptography.CryptographicException> obojí i v případě, že je požadováno zpracování výjimek.

### <a name="category"></a>Kategorie

Kryptografick

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
