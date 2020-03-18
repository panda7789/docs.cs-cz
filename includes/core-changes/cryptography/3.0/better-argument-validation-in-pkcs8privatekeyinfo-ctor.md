---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449209"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="97779-101">Lepší ověření argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="97779-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="97779-102">Počínaje rozhraním .NET Core 3.0 Preview `Pkcs8PrivateKeyInfo` 9 `algorithmParameters` konstruktor ověří parametr jako jednu hodnotu kódovku KÓDované ber.</span><span class="sxs-lookup"><span data-stu-id="97779-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="97779-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="97779-103">Change description</span></span>

<span data-ttu-id="97779-104">Před .NET Core 3.0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil `algorithmParameters` argument.</span><span class="sxs-lookup"><span data-stu-id="97779-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="97779-105">Pokud tento argument představuje neplatnou hodnotu, konstruktor by <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>uspěl, ale volání některé z metod <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, nebo <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> by vyvolalo buď <xref:System.ArgumentException> argument pro, který nepřijali (`preEncodedValue`) nebo . <xref:System.Security.Cryptography.CryptographicException></span><span class="sxs-lookup"><span data-stu-id="97779-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="97779-106">Pokud spustit s .NET Core 3.0 před náhledem 9, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> následující kód vyvolá výjimku pouze při volání metody:</span><span class="sxs-lookup"><span data-stu-id="97779-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="97779-107">Počínaje .NET Core 3.0 Náhled 9 argument je ověřen v konstruktoru a neplatná <xref:System.Security.Cryptography.CryptographicException>hodnota má za následek metodu vyvolání .</span><span class="sxs-lookup"><span data-stu-id="97779-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="97779-108">Tato změna přesune výjimku blíže ke zdroji chyby dat.</span><span class="sxs-lookup"><span data-stu-id="97779-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="97779-109">Například:</span><span class="sxs-lookup"><span data-stu-id="97779-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="97779-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="97779-110">Version introduced</span></span>

<span data-ttu-id="97779-111">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="97779-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="97779-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="97779-112">Recommended action</span></span>

<span data-ttu-id="97779-113">Ujistěte se, že jsou k dispozici `algorithmParameters` `Pkcs8PrivateKeyInfo` pouze platné hodnoty, nebo že volání testu konstruktoru pro oba <xref:System.ArgumentException> a <xref:System.Security.Cryptography.CryptographicException> pokud je požadováno zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="97779-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="97779-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="97779-114">Category</span></span>

<span data-ttu-id="97779-115">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="97779-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="97779-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="97779-116">Affected APIs</span></span>

- <span data-ttu-id="97779-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="97779-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
