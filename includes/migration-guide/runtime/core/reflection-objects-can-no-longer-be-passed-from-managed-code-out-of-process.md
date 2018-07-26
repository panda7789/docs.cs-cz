### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Objekty reflexe lze předat už ze spravovaného kódu DCOM klientům mimo proces

|   |   |
|---|---|
|Podrobnosti|Objekty reflexe je už předat ze spravovaného kódu DCOM klientům mimo proces. Jsou ovlivněny následující typy:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (a jeho odvozeným typům, včetně <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, a <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Volání <code>IMarshal</code> pro vrácení objektu <code>E_NOINTERFACE</code>.|
|Návrh|Aktualizace kódu zařazování pro práci s objekty bez reflexe|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|

