---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568136"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="c9d22-101">Operace analýzy s plovoucí desetinnou táhou již neselžou nebo nevyvolá vyzvučují výjimku Přetečení</span><span class="sxs-lookup"><span data-stu-id="c9d22-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="c9d22-102">Metody analýzy s plovoucí desetinnou <xref:System.OverflowException> desetinnou tázkou již nevyvolávají nebo vracejí, `false` když analyzují řetězec, jehož číselná hodnota je mimo rozsah typu <xref:System.Single> nebo <xref:System.Double> typu s plovoucí desetinnou tálkou.</span><span class="sxs-lookup"><span data-stu-id="c9d22-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c9d22-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="c9d22-103">Change description</span></span>

<span data-ttu-id="c9d22-104">V .NET Core 2.2 a <xref:System.Double.Parse%2A?displayProperty=nameWithType> starší <xref:System.Single.Parse%2A?displayProperty=nameWithType> verze <xref:System.OverflowException> a metody throw pro hodnoty, které mimo rozsah jejich příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="c9d22-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="c9d22-105">Metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> a `false` vrátí pro řetězcové reprezentace číselných hodnot mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="c9d22-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="c9d22-106">Počínaje rozhraním .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType>3.0 již neseselá <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>metoda , a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody při analýzě číselných řetězců mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="c9d22-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="c9d22-107">Místo toho <xref:System.Double> metody analýzy <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> vrátí hodnoty, které <xref:System.Double.MaxValue?displayProperty=nameWithType> <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> překračují , a <xref:System.Double.MinValue?displayProperty=nameWithType>vrátí pro hodnoty, které jsou menší než .</span><span class="sxs-lookup"><span data-stu-id="c9d22-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c9d22-108">Podobně <xref:System.Single> metody analýzy vrátí <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> hodnoty, které <xref:System.Single.MaxValue?displayProperty=nameWithType>překračují , <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> a vracejí hodnoty, které jsou menší než <xref:System.Single.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9d22-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c9d22-109">Tato změna byla provedena pro lepší dodržování předpisů IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="c9d22-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c9d22-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="c9d22-110">Version introduced</span></span>

<span data-ttu-id="c9d22-111">3.0</span><span class="sxs-lookup"><span data-stu-id="c9d22-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c9d22-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c9d22-112">Recommended action</span></span>

<span data-ttu-id="c9d22-113">Tato změna může ovlivnit váš kód jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="c9d22-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="c9d22-114">Váš kód závisí na <xref:System.OverflowException> obslužné rutiny pro spuštění při přetečení dojde.</span><span class="sxs-lookup"><span data-stu-id="c9d22-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="c9d22-115">V takovém případě byste `catch` měli příkaz odebrat a `If` umístit potřebný <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> kód `true`do příkazu, který testuje, zda je nebo je .</span><span class="sxs-lookup"><span data-stu-id="c9d22-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="c9d22-116">Váš kód předpokládá, že hodnoty `Infinity`s plovoucí desetinnou čárkou nejsou .</span><span class="sxs-lookup"><span data-stu-id="c9d22-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="c9d22-117">V takovém případě byste měli přidat kód potřebný ke `PositiveInfinity` kontrole `NegativeInfinity`hodnot s plovoucí desetinnou čárky a .</span><span class="sxs-lookup"><span data-stu-id="c9d22-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="c9d22-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c9d22-118">Category</span></span>

<span data-ttu-id="c9d22-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c9d22-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c9d22-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c9d22-120">Affected APIs</span></span>

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
