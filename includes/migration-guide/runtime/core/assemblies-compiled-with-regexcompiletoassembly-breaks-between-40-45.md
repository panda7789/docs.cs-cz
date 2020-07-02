---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619948"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Sestavení zkompilované pomocí Regex. CompileToAssembly break mezi 4,0 a 4,5

#### <a name="details"></a>Podrobnosti

Pokud je sestavení kompilovaných regulárních výrazů sestaveno s .NET Framework 4,5, ale cílí na .NET Framework 4, pokus o použití jednoho regulárního výrazu v tomto sestavení v systému, ve kterém je nainstalováno .NET Framework 4, vyvolá výjimku.

#### <a name="suggestion"></a>Návrh

Pokud chcete tento problém obejít, můžete udělat jednu z následujících akcí:<ul><li>Sestavte sestavení obsahující regulární výrazy s .NET Framework 4.</li><li>Použijte interpretovaný regulární výraz.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
