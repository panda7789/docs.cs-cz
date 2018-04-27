### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nejsou ve profilery ve výčtu

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework v4.5.1, profilaci API <code>RootReferences2()</code> nesprávně nikdy vrací <code>COR_PRF_GC_ROOT_HANDLE</code> (jsou vrácena jako <code>COR_PRF_GC_ROOT_OTHER</code> místo). Tento problém vyřešen, počínaje rozhraní .NET Framework 4.6.|
|Návrh|Tento problém byl opraven v rozhraní .NET Framework 4.6 a může být kontaktována upgrade na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|

