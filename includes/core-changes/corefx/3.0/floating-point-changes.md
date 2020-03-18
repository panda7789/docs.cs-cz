---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568208"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="870dc-101">Změněno formátování a analýza s plovoucí desetinnou tázkem.</span><span class="sxs-lookup"><span data-stu-id="870dc-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="870dc-102">Chování analýzy a formátování s plovoucí <xref:System.Double> desetinnou tázkem (podle <xref:System.Single> a typů) je nyní kompatibilní s IEEE.</span><span class="sxs-lookup"><span data-stu-id="870dc-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="870dc-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="870dc-103">Change description</span></span>

<span data-ttu-id="870dc-104">V rozhraní .NET Core 2.2 a starších <xref:System.Single.ToString%2A?displayProperty=nameWithType>verzích formátování <xref:System.Double.Parse%2A?displayProperty=nameWithType>s <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> , a analýza s , , a nejsou kompatibilní s IEEE.</span><span class="sxs-lookup"><span data-stu-id="870dc-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="870dc-105">V důsledku toho není možné zaručit, že hodnota bude roundtrip s všechny podporované standardní nebo vlastní formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="870dc-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="870dc-106">U některých vstupů může pokus o analýzu formátované hodnoty selhat a u jiných se analyzovaná hodnota nerovná původní hodnotě.</span><span class="sxs-lookup"><span data-stu-id="870dc-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="870dc-107">Počínaje rozhraním .NET Core 3.0 jsou operace analýzy a formátování kompatibilní s rozhraním IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="870dc-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="870dc-108">Tím je zajištěno, že chování typů s plovoucí desetinnou desetinnou tácek v rozhraní .NET odpovídá chování jazyků kompatibilních s IEEE, jako je například C#.</span><span class="sxs-lookup"><span data-stu-id="870dc-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="870dc-109">Další informace naleznete v [vylepšení analýzy a formátování s plovoucí desetinnou tácející](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) v příspěvku blogu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="870dc-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="870dc-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="870dc-110">Version introduced</span></span>

<span data-ttu-id="870dc-111">3.0</span><span class="sxs-lookup"><span data-stu-id="870dc-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="870dc-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="870dc-112">Recommended action</span></span>

<span data-ttu-id="870dc-113">Část "Potenciální dopad na existující kód" vylepšení [analýzy a formátování s plovoucí desetinnou čárkou v](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) příspěvku blogu .NET Core 3.0 navrhuje změny kódu, pokud zaznamenáte změnu chování ve srovnání s aplikacemi .NET Core 2.2 Obecně to zahrnuje použití jiného standardního nebo vlastního formátovacího řetězce k vynucení požadovaného chování.</span><span class="sxs-lookup"><span data-stu-id="870dc-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="870dc-114">Některé výsledky nemusí mít řešení, pokud byly dříve nesprávné.</span><span class="sxs-lookup"><span data-stu-id="870dc-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="870dc-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="870dc-115">Category</span></span>

<span data-ttu-id="870dc-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="870dc-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="870dc-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="870dc-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
