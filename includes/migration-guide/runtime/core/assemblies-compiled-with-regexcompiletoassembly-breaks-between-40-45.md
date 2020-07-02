---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619948"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="2f528-101">Sestavení zkompilované pomocí Regex. CompileToAssembly break mezi 4,0 a 4,5</span><span class="sxs-lookup"><span data-stu-id="2f528-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="2f528-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2f528-102">Details</span></span>

<span data-ttu-id="2f528-103">Pokud je sestavení kompilovaných regulárních výrazů sestaveno s .NET Framework 4,5, ale cílí na .NET Framework 4, pokus o použití jednoho regulárního výrazu v tomto sestavení v systému, ve kterém je nainstalováno .NET Framework 4, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="2f528-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2f528-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="2f528-104">Suggestion</span></span>

<span data-ttu-id="2f528-105">Pokud chcete tento problém obejít, můžete udělat jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="2f528-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="2f528-106">Sestavte sestavení obsahující regulární výrazy s .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2f528-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="2f528-107">Použijte interpretovaný regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="2f528-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="2f528-108">Name</span><span class="sxs-lookup"><span data-stu-id="2f528-108">Name</span></span>    | <span data-ttu-id="2f528-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2f528-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2f528-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2f528-110">Scope</span></span>   |<span data-ttu-id="2f528-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="2f528-111">Minor</span></span>|
|<span data-ttu-id="2f528-112">Verze</span><span class="sxs-lookup"><span data-stu-id="2f528-112">Version</span></span>|<span data-ttu-id="2f528-113">4.5</span><span class="sxs-lookup"><span data-stu-id="2f528-113">4.5</span></span>|
|<span data-ttu-id="2f528-114">Typ</span><span class="sxs-lookup"><span data-stu-id="2f528-114">Type</span></span>|<span data-ttu-id="2f528-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2f528-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2f528-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2f528-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
