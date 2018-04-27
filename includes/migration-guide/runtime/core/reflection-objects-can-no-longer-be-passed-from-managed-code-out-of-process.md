### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Reflexe lze už předat objekty ze spravovaného kódu DCOM klientům mimo proces

|   |   |
|---|---|
|Podrobnosti|Reflexe lze už předat objekty ze spravovaného kódu DCOM klientům mimo proces. Následující typy jsou ovlivněné:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (a jeho odvozených typů, včetně <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, a <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Volání <code>IMarshal</code> pro objekt návratový <code>E_NOINTERFACE</code>.|
|Návrh|Aktualizujte zařazování kód pro práci s objekty bez reflexe|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|

