---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720880"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="a545c-101">Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="a545c-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="a545c-102">Počínaje rozhraním .NET Core 3,0 Preview 9 `Pkcs8PrivateKeyInfo` konstruktor ověří `algorithmParameters` parametr jako jedinou hodnotu zakódovanou v ber.</span><span class="sxs-lookup"><span data-stu-id="a545c-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a545c-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a545c-103">Change description</span></span>

<span data-ttu-id="a545c-104">Před rozhraním .NET Core 3,0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil `algorithmParameters` argument.</span><span class="sxs-lookup"><span data-stu-id="a545c-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="a545c-105">Pokud tento argument představoval neplatnou hodnotu, konstruktor by byl úspěšný, ale volání jakékoli <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> metody,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> , nebo <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> by vyvolalo buď <xref:System.ArgumentException> pro argument, který nepřijal ( `preEncodedValue` ) nebo <xref:System.Security.Cryptography.CryptographicException> .</span><span class="sxs-lookup"><span data-stu-id="a545c-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="a545c-106">Pokud spustíte s .NET Core 3,0 před verzí Preview 9, následující kód vyvolá výjimku pouze v případě, že <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> je metoda volána:</span><span class="sxs-lookup"><span data-stu-id="a545c-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="a545c-107">Počínaje rozhraním .NET Core 3,0 Preview 9 je argument v konstruktoru ověřován a neplatná hodnota má za následek vyvolání metody <xref:System.Security.Cryptography.CryptographicException> .</span><span class="sxs-lookup"><span data-stu-id="a545c-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="a545c-108">Tato změna přesune výjimku blíže ke zdroji chyby dat.</span><span class="sxs-lookup"><span data-stu-id="a545c-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="a545c-109">Například:</span><span class="sxs-lookup"><span data-stu-id="a545c-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="a545c-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a545c-110">Version introduced</span></span>

<span data-ttu-id="a545c-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a545c-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a545c-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a545c-112">Recommended action</span></span>

<span data-ttu-id="a545c-113">Zajistěte, aby `algorithmParameters` byly zadány pouze platné hodnoty, nebo že volání `Pkcs8PrivateKeyInfo` testu konstruktoru pro obojí i v případě, že <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> je požadováno zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="a545c-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

#### <a name="category"></a><span data-ttu-id="a545c-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a545c-114">Category</span></span>

<span data-ttu-id="a545c-115">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="a545c-115">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a545c-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a545c-116">Affected APIs</span></span>

- <span data-ttu-id="a545c-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="a545c-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
