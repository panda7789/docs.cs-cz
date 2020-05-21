---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721108"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="6567a-101">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="6567a-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="6567a-102">Metody analýzy s plovoucí desetinnou čárkou již nejsou <xref:System.OverflowException> `false` při analýze řetězce, jehož číselná hodnota je mimo rozsah <xref:System.Single> nebo typ s plovoucí desetinnou čárkou, vyhozeny nebo vraceny <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="6567a-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6567a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="6567a-103">Change description</span></span>

<span data-ttu-id="6567a-104">V .NET Core 2,2 a starších verzích <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> metody a vyvolávají výjimku <xref:System.OverflowException> pro hodnoty, které jsou mimo rozsah jejich příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="6567a-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="6567a-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType>Metody a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> vrátí `false` pro řetězcové reprezentace číselných hodnot mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="6567a-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="6567a-106">Počínaje rozhraním .NET Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType> metody,, a se <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> již nedaří při analýze číselných řetězců mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="6567a-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="6567a-107">Místo toho <xref:System.Double> metody analýzy vrátí <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> pro hodnoty, které překračují <xref:System.Double.MaxValue?displayProperty=nameWithType> , a vrátí <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> hodnotu, která je menší než <xref:System.Double.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6567a-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6567a-108">Podobně <xref:System.Single> metody analýzy vrátí <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pro hodnoty, které překračují <xref:System.Single.MaxValue?displayProperty=nameWithType> , a vrátí <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> pro hodnoty, které jsou menší než <xref:System.Single.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6567a-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6567a-109">Tato změna byla provedena pro zlepšení dodržování standardů IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="6567a-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6567a-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6567a-110">Version introduced</span></span>

<span data-ttu-id="6567a-111">3.0</span><span class="sxs-lookup"><span data-stu-id="6567a-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6567a-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6567a-112">Recommended action</span></span>

<span data-ttu-id="6567a-113">Tato změna může mít vliv na váš kód některým ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="6567a-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="6567a-114">Váš kód závisí na obslužné rutině, <xref:System.OverflowException> která se má provést, když dojde k přetečení.</span><span class="sxs-lookup"><span data-stu-id="6567a-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="6567a-115">V takovém případě byste měli příkaz odebrat `catch` a umístit jakýkoli potřebný kód do `If` příkazu, který testuje, zda <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> nebo <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> je `true` .</span><span class="sxs-lookup"><span data-stu-id="6567a-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="6567a-116">Váš kód předpokládá, že hodnoty s plovoucí desetinnou čárkou nejsou `Infinity` .</span><span class="sxs-lookup"><span data-stu-id="6567a-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="6567a-117">V takovém případě byste měli přidat potřebný kód pro kontrolu hodnot s plovoucí desetinnou čárkou `PositiveInfinity` a `NegativeInfinity` .</span><span class="sxs-lookup"><span data-stu-id="6567a-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="6567a-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6567a-118">Category</span></span>

<span data-ttu-id="6567a-119">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="6567a-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6567a-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6567a-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
