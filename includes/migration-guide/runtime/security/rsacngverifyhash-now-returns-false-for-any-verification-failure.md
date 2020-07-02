---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621082"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="baa0f-101">Algoritmem RSACng. VerifyHash teď pro jakékoli selhání ověřování vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="baa0f-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="baa0f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="baa0f-102">Details</span></span>

<span data-ttu-id="baa0f-103">Počínaje .NET Framework 4.6.2 vrátí tato metoda **hodnotu false** , pokud samotný podpis není správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="baa0f-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="baa0f-104">Nyní vrátí hodnotu false pro jakékoli selhání ověřování. V .NET Framework 4,6 a 4.6.1 metoda vyvolá výjimku, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> Pokud samotný podpis není správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="baa0f-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="baa0f-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="baa0f-105">Suggestion</span></span>

<span data-ttu-id="baa0f-106">Jakýkoli kód, jehož provádění závisí na zpracování, je <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> třeba provést, pokud se ověření nepovede a metoda vrátí **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="baa0f-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="baa0f-107">Name</span><span class="sxs-lookup"><span data-stu-id="baa0f-107">Name</span></span>    | <span data-ttu-id="baa0f-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="baa0f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="baa0f-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="baa0f-109">Scope</span></span>   |<span data-ttu-id="baa0f-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="baa0f-110">Minor</span></span>|
|<span data-ttu-id="baa0f-111">Verze</span><span class="sxs-lookup"><span data-stu-id="baa0f-111">Version</span></span>|<span data-ttu-id="baa0f-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="baa0f-112">4.6.2</span></span>|
|<span data-ttu-id="baa0f-113">Typ</span><span class="sxs-lookup"><span data-stu-id="baa0f-113">Type</span></span>|<span data-ttu-id="baa0f-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="baa0f-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="baa0f-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="baa0f-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
