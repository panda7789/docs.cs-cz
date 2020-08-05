---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555904"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="fa928-101">Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="fa928-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="fa928-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>Konstanta je označena jako [ \[ zastaralá \] ](xref:System.ObsoleteAttribute) od .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="fa928-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa928-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="fa928-103">Version introduced</span></span>

<span data-ttu-id="fa928-104">3.0</span><span class="sxs-lookup"><span data-stu-id="fa928-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="fa928-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="fa928-105">Change description</span></span>

<span data-ttu-id="fa928-106">Počínaje rozhraním .NET Core 3,0 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstantu.</span><span class="sxs-lookup"><span data-stu-id="fa928-106">Starting with .NET Core 3.0, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="fa928-107">Použití konstanty generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="fa928-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="fa928-108">V .NET Framework a předchozích verzích rozhraní .NET Core nebyla označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="fa928-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="fa928-109">Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="fa928-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="fa928-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine>Konstanta je ekvivalentem `\r\n` , sekvence znaků nového řádku ve Windows.</span><span class="sxs-lookup"><span data-stu-id="fa928-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="fa928-111">V systémech UNIX je znak nového řádku `\n` .</span><span class="sxs-lookup"><span data-stu-id="fa928-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa928-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="fa928-112">Recommended action</span></span>

<span data-ttu-id="fa928-113">[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro <xref:Microsoft.VisualBasic.Constants.vbNewLine> zahrnuje následující doporučení:</span><span class="sxs-lookup"><span data-stu-id="fa928-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="fa928-114">Pro návrat na začátek řádku a pro posun řádku použijte <xref:Microsoft.VisualBasic.Constants.vbCrLf> .</span><span class="sxs-lookup"><span data-stu-id="fa928-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="fa928-115">Pro nový řádek aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa928-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="fa928-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="fa928-116">Category</span></span>

<span data-ttu-id="fa928-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa928-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa928-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fa928-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
