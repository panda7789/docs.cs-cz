---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721448"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="a7c02-101">Změnilo se formátování a chování při analýze s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="a7c02-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="a7c02-102">Chování při analýze a formátování plovoucí desetinné čárky (podle <xref:System.Double> <xref:System.Single> typu a) nyní dodržuje standard IEEE.</span><span class="sxs-lookup"><span data-stu-id="a7c02-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a7c02-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a7c02-103">Change description</span></span>

<span data-ttu-id="a7c02-104">V rozhraní .NET Core 2,2 a starších verzích, formátování pomocí <xref:System.Double.ToString%2A?displayProperty=nameWithType> a a <xref:System.Single.ToString%2A?displayProperty=nameWithType> analýzy pomocí,, a <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nejsou kompatibilní se standardem IEEE.</span><span class="sxs-lookup"><span data-stu-id="a7c02-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="a7c02-105">V důsledku toho není možné zaručit, že hodnota převedená s jakýmkoli podporovaným standardním nebo vlastním formátovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="a7c02-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="a7c02-106">U některých vstupů může být pokus o analýzu formátované hodnoty neúspěšný a pro ostatní se analyzovaná hodnota nerovná původní hodnotě.</span><span class="sxs-lookup"><span data-stu-id="a7c02-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="a7c02-107">Počínaje .NET Core 3,0 jsou operace analýzy a formátování kompatibilní se standardem IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="a7c02-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="a7c02-108">Tím je zajištěno, že chování typů s plovoucí desetinnou čárkou v rozhraní .NET odpovídá jazyku standardu IEEE, jako je C#.</span><span class="sxs-lookup"><span data-stu-id="a7c02-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="a7c02-109">Další informace najdete v příspěvku na blogu k [analýze a formátování s plovoucí desetinnou čárkou v .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="a7c02-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a7c02-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a7c02-110">Version introduced</span></span>

<span data-ttu-id="a7c02-111">3.0</span><span class="sxs-lookup"><span data-stu-id="a7c02-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a7c02-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a7c02-112">Recommended action</span></span>

<span data-ttu-id="a7c02-113">Část "potenciální dopad na stávající kód" v rámci analýzy s plovoucí desetinnou čárkou [a vylepšení formátování na blogu .NET core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) navrhuje změny kódu, pokud v porovnání s aplikacemi .net Core 2,2 nastáváte se změnou chování, pokud se obvykle projeví při použití jiného standardního nebo vlastního formátovacího řetězce, který vynutil požadované chování.</span><span class="sxs-lookup"><span data-stu-id="a7c02-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="a7c02-114">Některé výsledky nemusí mít alternativní řešení, pokud byly dříve nesprávné.</span><span class="sxs-lookup"><span data-stu-id="a7c02-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="a7c02-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a7c02-115">Category</span></span>

<span data-ttu-id="a7c02-116">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="a7c02-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7c02-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a7c02-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
