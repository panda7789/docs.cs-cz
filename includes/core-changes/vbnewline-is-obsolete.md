---
ms.openlocfilehash: 82017569128937d344838df850445cf55aa9ea4c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930031"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="295ed-101">Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="295ed-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="295ed-102">Konstanta je označena jako [zastaralá](xref:System.ObsoleteAttribute) v .NET Framework, ale v knihovně .NET Core 3,0 se předtím chyběl atribut. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="295ed-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) in .NET Framework, but the attribute was missing previously in the .NET Core 3.0 library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="295ed-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="295ed-103">Version introduced</span></span>

<span data-ttu-id="295ed-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="295ed-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="295ed-105">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="295ed-105">Details</span></span>

<span data-ttu-id="295ed-106">Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> `vbNewLine` konstantu, aby odpovídal v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="295ed-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant to conform to `vbNewLine` in the .NET Framework.</span></span> <span data-ttu-id="295ed-107">`vbNewLine` Použití konstanty generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="295ed-107">Use of the `vbNewLine` constant produces a compiler warning.</span></span> 

<span data-ttu-id="295ed-108">V předchozích verzích .NET Core `vbNewLine` nevzniklo upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="295ed-108">In previous versions of .NET Core, `vbNewLine` did not produce a compiler warning.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="295ed-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="295ed-109">Recommended action</span></span>

<span data-ttu-id="295ed-110">[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu `vbNewLine` pro zahrnuje následující doporučení:</span><span class="sxs-lookup"><span data-stu-id="295ed-110">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="295ed-111">Pro návrat na začátek řádku a pro posun řádku použijte [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="295ed-111">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="295ed-112">Pro nový řádek aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="295ed-112">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="295ed-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="295ed-113">Category</span></span>
<span data-ttu-id="295ed-114">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="295ed-114">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="295ed-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="295ed-115">Affected APIs</span></span>
- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

