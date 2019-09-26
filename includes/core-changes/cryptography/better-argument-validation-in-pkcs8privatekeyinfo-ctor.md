---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263317"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="3a881-101">Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="3a881-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="3a881-102">Počínaje rozhraním .NET Core 3,0 Preview 9 `Pkcs8PrivateKeyInfo` konstruktor ověří `algorithmParameters` parametr jako jedinou hodnotu zakódovanou v ber.</span><span class="sxs-lookup"><span data-stu-id="3a881-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a881-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="3a881-103">Change description</span></span>

<span data-ttu-id="3a881-104">Před rozhraním .NET Core 3,0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) neověřil `algorithmParameters` argument.</span><span class="sxs-lookup"><span data-stu-id="3a881-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="3a881-105">Pokud tento argument představoval neplatnou hodnotu, konstruktor by byl úspěšný, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>ale volání kterékoli z metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, nebo <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> vyvolá buď <xref:System.ArgumentException> pro argument, který nepřijal (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>nebo.</span><span class="sxs-lookup"><span data-stu-id="3a881-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="3a881-106">Pokud spustíte s .NET Core 3,0 před verzí Preview 9, následující kód vyvolá výjimku pouze v případě, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> že je metoda volána:</span><span class="sxs-lookup"><span data-stu-id="3a881-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="3a881-107">Počínaje rozhraním .NET Core 3,0 Preview 9 je argument v konstruktoru ověřován a neplatná hodnota má za následek vyvolání <xref:System.Security.Cryptography.CryptographicException>metody.</span><span class="sxs-lookup"><span data-stu-id="3a881-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="3a881-108">Tato změna přesune výjimku blíže ke zdroji chyby dat.</span><span class="sxs-lookup"><span data-stu-id="3a881-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="3a881-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3a881-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="3a881-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="3a881-110">Version introduced</span></span>

<span data-ttu-id="3a881-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="3a881-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a881-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3a881-112">Recommended action</span></span>

<span data-ttu-id="3a881-113">Zajistěte, `algorithmParameters` aby byly zadány pouze platné hodnoty, nebo `Pkcs8PrivateKeyInfo` že volání testu konstruktoru <xref:System.ArgumentException> pro <xref:System.Security.Cryptography.CryptographicException> obojí i v případě, že je požadováno zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="3a881-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="3a881-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3a881-114">Category</span></span>

<span data-ttu-id="3a881-115">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="3a881-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="3a881-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3a881-116">Affected APIs</span></span>

- <span data-ttu-id="3a881-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="3a881-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
