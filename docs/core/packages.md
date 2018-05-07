---
title: Balíčky, metapackages a architektury
description: Přečtěte si terminologie pro balíčky, metapackages a architektur.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 915ccadbb4d2cca50fd1caa53d90aa05d83d9378
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="packages-metapackages-and-frameworks"></a>Balíčky, metapackages a architektury

.NET core je platforma, které se skládají z balíčků NuGet. Některé produktu vyskytne benefit z podrobných definice balíčků, zatímco jiní jej z hrubý. Abychom vyhověli této duality, je produktu distribuovaných jako podrobných sadu balíčků a pak popsaných v hrubší bloky dat s typem balíček neformálně názvem "metapackage".

Každý z balíčků .NET Core podporují, se spouští více implementace rozhraní .NET, vyjádřené architektury. Některé z těchto rozhraní jsou tradiční rozhraní, jako je třeba `net46`, představující rozhraní .NET Framework. Jiná sada je nové rozhraní, které si lze představit jako "na základě balíčku rozhraní", které vytvořit nový model pro definování rozhraní. Tyto architektury na základě balíčku jsou zcela vytvořen a definované jako balíčky, které tvoří silný vztah mezi balíčky a rozhraní.

## <a name="packages"></a>Balíčky

.NET core je rozdělená do sady balíčků, které poskytují primitiv, vyšší úrovně datové typy, typy složení aplikace a běžné nástroje. Každý z těchto balíčků představují jednoho sestavení se stejným názvem. Například [System.Runtime](https://www.nuget.org/packages/System.Runtime) obsahuje System.Runtime.dll. 

Existují výhody definování balíčků podrobných způsobem:

- Jemně odstupňovaných balíčky se dají dodávat svého vlastního plánu s relativně omezené testování další balíčky.
- Jemně odstupňovaných balíčky můžete poskytovat různé podporu operačního systému a procesoru.
- Jemně odstupňovaných balíčky může obsahovat závislosti konkrétní jenom jedna knihovna.
- Aplikace jsou menší, protože neregistrované balíčky nejsou stane součástí distribuce aplikací.

Některé z těchto výhod používají jenom za určitých okolností. Například základní NET obvykle dodávat na stejný plán s podporou stejnou platformu. V případě údržby, může distribuovat opravy a nainstalovat jako malé jeden balíček aktualizace. Z důvodu omezený rozsah změn je omezený na co je potřeba pro jednu knihovnu ověřování a čas, aby k dispozici oprava.

Následuje seznam klíčů balíčky NuGet pro .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) -nejzákladnější balíčku .NET Core, včetně <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>, a <xref:System.Collections.Generic.IList%601>.
- [System.Collections –](https://www.nuget.org/packages/System.Collections) -sadu (hlavně) obecné kolekce, včetně <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) -A sadu typů pro komunikaci pomocí protokolu HTTP sítě, včetně <xref:System.Net.Http.HttpClient> a <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -sadu typů pro čtení a zápis do místní nebo síťová diskové úložiště, včetně <xref:System.IO.File> a <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) -sadu typů pro dotazování objektů, včetně `Enumerable` a <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) -sadu typů pro načítání, kontroly a aktivace typů, včetně <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> a <xref:System.Reflection.MethodInfo>.

Místo včetně balíčků ve vašich projektů na základě balíčku balíček, je obvykle mnohem jednodušší zahrnout *metapackage*, což je sada balíčků, které se často používají společně. (Další informace o metapackages, najdete v následující části.) Ale pokud budete potřebovat jeden balíček, můžete zahrnout ho jako v příkladu níže, který odkazuje [System.Runtime](https://www.nuget.org/packages/System.Runtime/) balíčku. 

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Metapackages

Metapackages jsou konvence balíčku NuGet pro popisující sadu balíčky, které dohromady dávat smysl. Tato sada balíčky představují tím, že je závislosti. Rozhraní pro tuto sadu balíčků se Volitelně můžete vytvořit tak, že zadáte rozhraní. 

Předchozí verze nástrojů .NET Core (project.json a na základě csproj nástroje) ve výchozím nastavení zadat rozhraní a metapackage. V současné době však metapackage implicitně odkazuje cílové rozhraní, tak, aby každý metapackage je vázaný na cílové rozhraní. Například `netstandard1.6` framework odkazuje metapackage verze 1.6.0 NetStandard.Library. Podobně `netcoreapp1.1` framework odkazuje metapackage Microsoft.NETCore.App verze 1.1.0. Další informace najdete v tématu [metapackage implicitní odkaz na balíček v rozhraní .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Cílení na rozhraní a implicitně odkazující metapackage znamená, že platí přidáte odkaz na každý z jeho závislých balíčků jako gesto jeden. Který zpřístupňuje všech knihoven v těchto balíčcích pro IntelliSense (nebo podobné prostředí) a pro publikování aplikace.  

Existují výhody použití metapackages:

- Zajišťuje vhodné uživatelské prostředí tak, aby odkazovaly velké sady podrobných balíčky. 
- Definuje sadu balíčky (včetně konkrétních verzí), které jsou testovány a dobře fungují.

.NET Standard metapackage je:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) -popisuje knihovny, které jsou součástí na "Standard .NET". Platí pro všechny implementace rozhraní .NET (například rozhraní .NET Framework, .NET Core a Mono), které podporují .NET Standard. Vytvoří rozhraní 'monikerů netstandard'.

Klíče metapackages .NET Core jsou:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) -popisuje knihovny, které jsou součástí distribuční .NET Core. Vytvoří [ `.NETCoreApp` framework](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Závisí na menší `NETStandard.Library`.
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) -zahrnuje všechny podporované balíčky z interní a třetích stran závislosti používané ASP.NET Core a Entity Framework Core, Entity Framework Core a ASP.NET Core. V tématu [Microsoft.AspNetCore.All metapackage pro ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage) Další informace.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) -sadu průčelí kompatibility, které umožňují na základě mscorlib přenosné knihovny tříd (PCLs) ke spuštění na .NET Core.

## <a name="frameworks"></a>rozhraní

.NET core balíčky podporovat sadu rozhraní modulu runtime. Rozhraní popisují dostupné sadu rozhraní API (a případně také další vlastnosti), se můžete spolehnout na k identifikaci dané rozhraní. Verzí jsou při přidávání nových rozhraní API.

Například [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) podporuje následující rozhraní:

- . NETFramework, verze = 4.6
- . Monikerů NETStandard, verze = 1,3
- 6 Xamarin platformy (například xamarinios10)

Je užitečné kontrastu první dva z těchto rozhraní, protože jsou příklady dvěma různými způsoby, že jsou definovány architektury.

`.NETFramework,Version=4.6` Framework představuje dostupných rozhraní API v rozhraní .NET Framework 4.6. Můžete vytvořit knihovny kompilovat s referenční sestavení rozhraní .NET Framework 4.6 a pak distribuovat tyto knihovny v balíčky NuGet ve složce lib net46. Použije se pro aplikace, která cílí na rozhraní .NET Framework 4.6 nebo které jsou kompatibilní s ním. Jedná se jak počátku pracovaly všech rozhraní.

`.NETStandard,Version=1.3` Framework je rozhraní, na základě balíčku. Přitom spoléhá na balíčcích zacílených rozhraní k definování a zveřejňují rozhraní API z hlediska rozhraní.

## <a name="package-based-frameworks"></a>Na základě balíčku architektury

Je obousměrný vztah mezi architektury a balíčků. První část je definice rozhraní API, které jsou k dispozici pro dané rozhraní, například `netstandard1.3`. Balíčky cílené `netstandard1.3` (nebo kompatibilní rozhraní, jako `netstandard1.0`) rozhraní API, které jsou k dispozici pro definování `netstandard1.3`. Který může zvukových jako cyklickou definici, ale není. Na základě toho, "balíček na základě", definice rozhraní API pro architekturu pochází z balíčků. Rozhraní framework samotné nedefinuje žádné rozhraní API.

Druhá část relace je výběr majetku. Balíčky mohou obsahovat prostředky pro více rozhraní. Zadaný odkaz na sadu balíčky nebo metapackages, rozhraní je potřeba určit, které prostředek měla by být vybrána, například `net46` nebo `netstandard1.3`. Je důležité vybrat správnou asset. Například `net46` asset není pravděpodobné, aby byl kompatibilní s rozhraní .NET Framework 4.0 nebo .NET Core 1.0.

![Na základě balíčku Framework složení](./media/packages/package-framework.png)

Tento vztah na obrázku výše vidíte. *Rozhraní API* cílí a definuje *framework*. *Framework* se používá pro *asset výběr*. *Asset* poskytuje rozhraní API.

Dvě primární založené na balíček rozhraní použít s .NET Core jsou:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>Standardní rozhraní .NET

.NET Standard (cíle Přezdívka framework: `netstandard`) framework představuje rozhraní API definované a postavený na [.NET Standard](../standard/net-standard.md). Cílem toto rozhraní by měl být knihovny, které jsou určeny ke spuštění na víc moduly runtime. Že budou podporované v jakékoli standardní .NET kompatibilní běhu, třeba .NET Core, rozhraní .NET Framework a Mono nebo Xamarin. Tyto moduly runtime podporují sadu .NET Standard verze, v závislosti na tom, které rozhraní API implementovat.

`netstandard` Framework implicitně odkazuje [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) metapackage. Například následující soubor projektu nástroje MSBuild znamená, že cíle projektu `netstandard1.6`, který odkazuje [ `NETStandard.Library` verzi 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) metapackage.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ale framework a metapackage odkazy v souboru projektu nemusí odpovídat, a můžete `<NetStandardImplicitPackageVersion>` element v souboru projektu určit verzi framework, která je nižší než verze metapackage. Například následující soubor projektu je platný.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

To nemusí připadat neobvyklé cíl `netstandard1.3` ale verzi pomocí 1.6.0 `NETStandard.Library`. Je platný případ použití, protože metapackage zajišťuje podporu pro starší `netstandard` verze. Může to být případ jste standardizované na 1.6.0 verzi metapackage a použít jej pro všechny vaše knihovny, které cílí na celou řadu `netstandard` verze. S tímto přístupem, je potřeba jenom obnovit `NETStandard.Library` 1.6.0 a ne starší verze. 

Naopak nebude platný: cílení na `netstandard1.6` s 1.3.0 verzi `NETStandard.Library`. Cílem nemůže vyšší framework s nižší metapackage, protože nižší verze metapackage nebude vystavit všechny prostředky dané vyšší platformy. Správa verzí schéma pro metapackages vyhodnotí, že metapackages odpovídají nejvyšší verzi rozhraní, které popisují. Na základě schématu Správa verzí, první verze součásti `NETStandard.Library` je v1.6.0 vzhledem k tomu, že obsahuje `netstandard1.6` prostředky. V1.3.0 se používá v příkladu výše, symetrie s v předchozím příkladu, ale ve skutečnosti neexistuje.

### <a name="net-core-application"></a>Aplikace .NET core

Aplikace .NET Core (TFM: `netcoreapp`) framework představuje balíčky a přidružených rozhraní API, které jsou součástí distribuční .NET Core a model aplikace konzoly, který poskytuje. Aplikace .NET core musí používat toto rozhraní, z důvodu cílení na konzole modelu aplikace, jako by měl knihovny, které mají být spouštěn jen na .NET Core. Toto rozhraní pomocí omezuje aplikace a knihovny spuštěna pouze na .NET Core. 

`Microsoft.NETCore.App` Metapackage cíle `netcoreapp` framework. Poskytuje přístup k ~ 60 knihovny, ~ 40 poskytované `NETStandard.Library` balíček a další v přidání ~ 20. Další knihovny můžete odkazovat cílených `netcoreapp` nebo kompatibilní rozhraní, jako například `netstandard`, abyste získali přístup k další rozhraní API. 

Většina další knihovny poskytované `Microsoft.NETCore.App` také cíle `netstandard` vzhledem k tomu, že jejich závislostí jiná `netstandard` knihovny. To znamená, že `netstandard` knihovny lze také odkazovat na tyto balíčky jako závislosti. 
