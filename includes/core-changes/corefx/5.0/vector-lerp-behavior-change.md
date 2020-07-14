---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281294"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="67457-101">Změna chování pro Vector2. lerp a Vector4. lerp</span><span class="sxs-lookup"><span data-stu-id="67457-101">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="67457-102">Implementace <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> a <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> Změna správného účtu pro chybu zaokrouhlení s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="67457-102">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

#### <a name="change-description"></a><span data-ttu-id="67457-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="67457-103">Change description</span></span>

<span data-ttu-id="67457-104">Dříve <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> a <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> byly implementovány jako `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="67457-104">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="67457-105">Z důvodu chyby zaokrouhlení plovoucí desetinné čárky však tento algoritmus vždy nevrátí, `value2` Pokud `amount` je `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="67457-105">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="67457-106">V rozhraní .NET 5,0 a novější implementace používá stejný algoritmus jako <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> , což je `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="67457-106">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="67457-107">Tento algoritmus správně účty pro chybu zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="67457-107">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="67457-108">Teď, když `amount` je `1.0f` , výsledek je přesně `value2` .</span><span class="sxs-lookup"><span data-stu-id="67457-108">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="67457-109">Aktualizovaný algoritmus také umožňuje, aby byl algoritmus volně optimalizovaný pomocí, <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> když je dostupný.</span><span class="sxs-lookup"><span data-stu-id="67457-109">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="67457-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="67457-110">Version introduced</span></span>

<span data-ttu-id="67457-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="67457-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="67457-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="67457-112">Recommended action</span></span>

<span data-ttu-id="67457-113">Není nutná žádná akce.</span><span class="sxs-lookup"><span data-stu-id="67457-113">No action is necessary.</span></span> <span data-ttu-id="67457-114">Pokud však chcete zachovat staré chování, můžete implementovat vlastní `Lerp` funkci, která používá předchozí algoritmus `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="67457-114">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

#### <a name="category"></a><span data-ttu-id="67457-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="67457-115">Category</span></span>

<span data-ttu-id="67457-116">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="67457-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="67457-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="67457-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
