---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449209"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="e945d-101">Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="e945d-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="e945d-102">Počínaje rozhraním .NET Core 3,0 Preview 9 konstruktor `Pkcs8PrivateKeyInfo` ověřuje parametr `algorithmParameters` jako jednu hodnotu kódovanou jako BER.</span><span class="sxs-lookup"><span data-stu-id="e945d-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e945d-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="e945d-103">Change description</span></span>

<span data-ttu-id="e945d-104">Před rozhraním .NET Core 3,0 Preview 9 [konstruktor`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil argument `algorithmParameters`.</span><span class="sxs-lookup"><span data-stu-id="e945d-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="e945d-105">Pokud tento argument představoval neplatnou hodnotu, konstruktor by byl úspěšný, ale volání jakékoli <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>nebo metody <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> by vyvolalo buď <xref:System.ArgumentException> pro argument, který nepřijal (`preEncodedValue`) nebo <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="e945d-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="e945d-106">Pokud spustíte s .NET Core 3,0 před verzí Preview 9, následující kód vyvolá výjimku pouze v případě, že je volána metoda <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>:</span><span class="sxs-lookup"><span data-stu-id="e945d-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="e945d-107">Počínaje rozhraním .NET Core 3,0 Preview 9 se v konstruktoru ověří argument a neplatná hodnota způsobí, že metoda vyvolává <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="e945d-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="e945d-108">Tato změna přesune výjimku blíže ke zdroji chyby dat.</span><span class="sxs-lookup"><span data-stu-id="e945d-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="e945d-109">Například:</span><span class="sxs-lookup"><span data-stu-id="e945d-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="e945d-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e945d-110">Version introduced</span></span>

<span data-ttu-id="e945d-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="e945d-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e945d-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e945d-112">Recommended action</span></span>

<span data-ttu-id="e945d-113">Zajistěte, aby byly zadány pouze platné hodnoty `algorithmParameters` nebo zda volání `Pkcs8PrivateKeyInfo` konstruktoru konstruktoru pro <xref:System.ArgumentException> a <xref:System.Security.Cryptography.CryptographicException>, pokud je požadováno zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="e945d-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="e945d-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e945d-114">Category</span></span>

<span data-ttu-id="e945d-115">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="e945d-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="e945d-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e945d-116">Affected APIs</span></span>

- <span data-ttu-id="e945d-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="e945d-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
