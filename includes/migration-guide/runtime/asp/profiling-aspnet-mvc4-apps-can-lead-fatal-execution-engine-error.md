### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilace aplikací ASP.Net MVC4 může vést k závažné chybě

|   |   |
|---|---|
|Podrobnosti|Profilery pomocí/Profile NGEN sestavení může dojít k chybě PROFILOVANÉHO aplikace ASP.NET MVC4 při spuštění s 'závažné provádění modul výjimce.|
|Návrh|Tento problém vyřešen v rozhraní .NET Framework 4.5.2. Případně může zabránit tento problém zadáním profileru <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v maska událostí.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

