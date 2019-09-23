---
ms.openlocfilehash: 5ef785f476b795a9c53e511d51b2683b99e6da05
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181980"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="9982a-101">Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9982a-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="9982a-102">Konstanta je označena jako [zastaralá](xref:System.ObsoleteAttribute) od verze .NET Core 3,0 Preview 8. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9982a-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9982a-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9982a-103">Version introduced</span></span>

<span data-ttu-id="9982a-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9982a-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="9982a-105">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9982a-105">Details</span></span>

<span data-ttu-id="9982a-106">Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstantu.</span><span class="sxs-lookup"><span data-stu-id="9982a-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="9982a-107">Použití konstanty generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9982a-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="9982a-108">V předchozích verzích rozhraní .NET Core a .NET Framework nebyla označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9982a-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="9982a-109">Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="9982a-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="9982a-110">Konstanta je `\r\n`ekvivalentem, sekvence znaků nového řádku ve Windows. `vbNewLine`</span><span class="sxs-lookup"><span data-stu-id="9982a-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="9982a-111">V systémech UNIX je `\n`znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="9982a-111">On Unix-based systems, the newline character is `\n`.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="9982a-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9982a-112">Recommended action</span></span>

<span data-ttu-id="9982a-113">[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu `vbNewLine` pro zahrnuje následující doporučení:</span><span class="sxs-lookup"><span data-stu-id="9982a-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="9982a-114">Pro návrat na začátek řádku a pro posun řádku použijte [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="9982a-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="9982a-115">Pro nový řádek aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9982a-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="9982a-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9982a-116">Category</span></span>

<span data-ttu-id="9982a-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9982a-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9982a-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9982a-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

