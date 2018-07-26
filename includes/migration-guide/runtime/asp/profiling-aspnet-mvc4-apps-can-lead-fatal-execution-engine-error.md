### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilace aplikací ASP.Net MVC4 může vést k závažné chybě

|   |   |
|---|---|
|Podrobnosti|Profilovací programy pomocí sestavení NGEN/Profile dojít k chybě profilovaných aplikací technologie ASP.NET MVC4 při spuštění s "závažnou spuštění modulu výjimku.|
|Návrh|Tento problém je vyřešen v rozhraní .NET Framework 4.5.2. Alternativně může profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masky události.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

