---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557959"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="b39a7-101">MulticastOption. Group nepřijímá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b39a7-101">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="b39a7-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> již nepřijímá hodnotu `null` .</span><span class="sxs-lookup"><span data-stu-id="b39a7-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="b39a7-103">Pokud nastavíte vlastnost na hodnotu `null` , <xref:System.ArgumentNullException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="b39a7-103">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b39a7-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b39a7-104">Version introduced</span></span>

<span data-ttu-id="b39a7-105">5.0</span><span class="sxs-lookup"><span data-stu-id="b39a7-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b39a7-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b39a7-106">Change description</span></span>

<span data-ttu-id="b39a7-107">V předchozích verzích rozhraní .NET můžete nastavit <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> vlastnost na `null` .</span><span class="sxs-lookup"><span data-stu-id="b39a7-107">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="b39a7-108">Pokud <xref:System.Net.Sockets.MulticastOption> je později předán do <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , modul runtime vyvolá <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="b39a7-108">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="b39a7-109">V rozhraní .NET 5,0 a novějším <xref:System.ArgumentNullException> je vyvolána výjimka, pokud nastavíte vlastnost na hodnotu `null` .</span><span class="sxs-lookup"><span data-stu-id="b39a7-109">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b39a7-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="b39a7-110">Reason for change</span></span>

<span data-ttu-id="b39a7-111">Aby byly v souladu s pokyny návrhu rozhraní, byla vlastnost aktualizována, aby vyvolala, <xref:System.ArgumentNullException> Pokud je hodnota `null` .</span><span class="sxs-lookup"><span data-stu-id="b39a7-111">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b39a7-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b39a7-112">Recommended action</span></span>

<span data-ttu-id="b39a7-113">Ujistěte se, že nejste nastaveni <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> na `null` .</span><span class="sxs-lookup"><span data-stu-id="b39a7-113">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="b39a7-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b39a7-114">Category</span></span>

<span data-ttu-id="b39a7-115">Sítě</span><span class="sxs-lookup"><span data-stu-id="b39a7-115">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b39a7-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b39a7-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
