---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567404"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="0fcde-101">Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0fcde-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="0fcde-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>ová konstanta je označena jako [zastaralá](xref:System.ObsoleteAttribute) od verze .net Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="0fcde-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0fcde-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="0fcde-103">Version introduced</span></span>

<span data-ttu-id="0fcde-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0fcde-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="0fcde-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="0fcde-105">Change description</span></span>

<span data-ttu-id="0fcde-106">Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstanta.</span><span class="sxs-lookup"><span data-stu-id="0fcde-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="0fcde-107">Použití konstanty generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0fcde-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="0fcde-108">V předchozích verzích rozhraní .NET Core a .NET Framework nebyla označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0fcde-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="0fcde-109">Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="0fcde-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="0fcde-110">`vbNewLine` konstanta je ekvivalentem `\r\n`, sekvence znaků nového řádku ve Windows.</span><span class="sxs-lookup"><span data-stu-id="0fcde-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="0fcde-111">V systémech UNIX je znak nového řádku `\n`.</span><span class="sxs-lookup"><span data-stu-id="0fcde-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0fcde-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0fcde-112">Recommended action</span></span>

<span data-ttu-id="0fcde-113">[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro `vbNewLine` obsahuje následující doporučení:</span><span class="sxs-lookup"><span data-stu-id="0fcde-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="0fcde-114">Pro návrat na začátek řádku a pro posun řádku použijte [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="0fcde-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="0fcde-115">V případě nového řádku aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fcde-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="0fcde-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0fcde-116">Category</span></span>

<span data-ttu-id="0fcde-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fcde-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0fcde-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0fcde-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
