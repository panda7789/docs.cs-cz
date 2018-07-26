### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Sestavení zkompilovaná Regex.CompileToAssembly zalomení mezi 4.0 a 4.5

|   |   |
|---|---|
|Podrobnosti|Pokud je sestavení zkompilované regulární výrazy vytvořené pomocí rozhraní .NET Framework 4.5, ale cílí na .NET Framework 4, pokus o použití jedné regulárních výrazů v tom, že sestavení v systému pomocí rozhraní .NET Framework 4 nainstalováno vyvolá výjimku.|
|Návrh|Chcete-li tento problém vyřešit, můžete provést jeden z následujících akcí:<ul><li>Sestavení, který obsahuje regulární výrazy pomocí rozhraní .NET Framework 4.</li><li>Použijte interpretované regulární výraz.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|

