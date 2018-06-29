### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Sestavení kompilovat s Regex.CompileToAssembly zalomení mezi 4.0 a 4.5

|   |   |
|---|---|
|Podrobnosti|Pokud se rozhraní .NET Framework 4.5, ale cíle rozhraní .NET Framework 4 je integrovaný sestavení kompilované regulárních výrazů, pokouší použít jeden z regulárních výrazů v tomto sestavení v systému, rozhraní .NET Framework 4 nainstalováno vyvolá výjimku.|
|Návrh|Chcete-li tento problém obejít, můžete provést jeden z následujících akcí:<ul><li>Vytvořte sestavení, který obsahuje regulární výrazy k rozhraní .NET Framework 4.</li><li>Použijte na interpretované regulární výraz.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|

