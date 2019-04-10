---
ms.openlocfilehash: 69b25db88c7580787bbb47fb0902b6bb072f8dde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235373"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Sestavení zkompilovaná Regex.CompileToAssembly zalomení mezi 4.0 a 4.5

|   |   |
|---|---|
|Podrobnosti|Pokud je sestavení zkompilované regulární výrazy vytvořené pomocí rozhraní .NET Framework 4.5, ale cílí na .NET Framework 4, pokus o použití jedné regulárních výrazů v tom, že sestavení v systému pomocí rozhraní .NET Framework 4 nainstalováno vyvolá výjimku.|
|Doporučení|Chcete-li tento problém vyřešit, můžete provést jeden z následujících akcí:<ul><li>Sestavení, který obsahuje regulární výrazy pomocí rozhraní .NET Framework 4.</li><li>Použijte interpretované regulární výraz.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
