---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720922"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="85969-101">Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="85969-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="85969-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>Konstanta je označena jako [ \[ \] zastaralá](xref:System.ObsoleteAttribute) od verze .NET Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="85969-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="85969-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="85969-103">Version introduced</span></span>

<span data-ttu-id="85969-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="85969-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="85969-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="85969-105">Change description</span></span>

<span data-ttu-id="85969-106">Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstantu.</span><span class="sxs-lookup"><span data-stu-id="85969-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="85969-107">Použití konstanty generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="85969-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="85969-108">V .NET Framework a předchozích verzích rozhraní .NET Core nebyla označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="85969-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="85969-109">Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="85969-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="85969-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine>Konstanta je ekvivalentem `\r\n` , sekvence znaků nového řádku ve Windows.</span><span class="sxs-lookup"><span data-stu-id="85969-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="85969-111">V systémech UNIX je znak nového řádku `\n` .</span><span class="sxs-lookup"><span data-stu-id="85969-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="85969-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="85969-112">Recommended action</span></span>

<span data-ttu-id="85969-113">[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro <xref:Microsoft.VisualBasic.Constants.vbNewLine> zahrnuje následující doporučení:</span><span class="sxs-lookup"><span data-stu-id="85969-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="85969-114">Pro návrat na začátek řádku a pro posun řádku použijte <xref:Microsoft.VisualBasic.Constants.vbCrLf> .</span><span class="sxs-lookup"><span data-stu-id="85969-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="85969-115">Pro nový řádek aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85969-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="85969-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="85969-116">Category</span></span>

<span data-ttu-id="85969-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85969-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="85969-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="85969-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
