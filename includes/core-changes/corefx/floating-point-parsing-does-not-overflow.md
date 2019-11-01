---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198396"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="1b1b4-101">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="1b1b4-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="1b1b4-102">Metody analýzy s plovoucí desetinnou čárkou již nevyvolávají <xref:System.OverflowException> nebo vracet `false` při analýze řetězce, jehož číselná hodnota je mimo rozsah typu s plovoucí desetinnou čárkou <xref:System.Single> nebo <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1b1b4-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="1b1b4-103">Change description</span></span>

<span data-ttu-id="1b1b4-104">V .NET Core 2,2 a starších verzích metody <xref:System.Double.Parse%2A?displayProperty=nameWithType> a <xref:System.Single.Parse%2A?displayProperty=nameWithType> vyvolávají <xref:System.OverflowException> pro hodnoty, které přesahují rozsah jejich příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="1b1b4-105">Metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType> a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> vracejí `false` pro řetězcové reprezentace číselných hodnot mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="1b1b4-106">Počínaje rozhraním .NET Core 3,0 se metody <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nebudou při analýze číselných řetězců mimo rozsah zdařit.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="1b1b4-107">Místo toho metody analýzy <xref:System.Double> vrátí <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> pro hodnoty větší než <xref:System.Double.MaxValue?displayProperty=nameWithType> a vrátí <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> pro hodnoty, které jsou menší než <xref:System.Double.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1b1b4-108">Podobně metody analýzy <xref:System.Single> vrátí <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pro hodnoty, které překračují <xref:System.Single.MaxValue?displayProperty=nameWithType>, a vrátí <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> pro hodnoty, které jsou menší než <xref:System.Single.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1b1b4-109">Tato změna byla provedena pro zlepšení dodržování standardů IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b1b4-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="1b1b4-110">Version introduced</span></span>

<span data-ttu-id="1b1b4-111">3.0</span><span class="sxs-lookup"><span data-stu-id="1b1b4-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b1b4-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1b1b4-112">Recommended action</span></span>

<span data-ttu-id="1b1b4-113">Tato změna může mít vliv na váš kód některým ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="1b1b4-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="1b1b4-114">Váš kód závisí na obslužné rutině <xref:System.OverflowException>, která se má provést, když dojde k přetečení.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="1b1b4-115">V takovém případě byste měli odebrat příkaz `catch` a umístit jakýkoliv potřebný kód do příkazu `If`, který testuje, zda je `true`<xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> nebo <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="1b1b4-116">Váš kód předpokládá, že hodnoty s plovoucí desetinnou čárkou nejsou `Infinity`.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="1b1b4-117">V takovém případě byste měli přidat potřebný kód pro kontrolu hodnot s plovoucí desetinnou čárkou `PositiveInfinity` a `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="1b1b4-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="1b1b4-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1b1b4-118">Category</span></span>

<span data-ttu-id="1b1b4-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="1b1b4-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b1b4-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1b1b4-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
