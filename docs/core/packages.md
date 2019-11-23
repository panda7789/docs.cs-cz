---
title: Balíčky, metabalíčky a architektury – .NET Core
description: Naučte se terminologie pro balíčky, metabalíčky a rozhraní.
author: richlander
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7b019686df195a8cebdce126f7a0b2d22548dc0e
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275761"
---
# <a name="packages-metapackages-and-frameworks"></a>Balíčky, metabalíčky a architektury

.NET Core je platforma vytvořená v balíčcích NuGet. Některé zkušenosti s produktem přináší z jemně odstupňované definice balíčků, zatímco jiné jsou hrubě odstupňované. Pro uspokojení této duální sady je produkt distribuován jako jemně odstupňovanou sadu balíčků a v hrubých blocích s typem balíčku, který se neformálně nazývá [Metapackage](#metapackages).

Každý balíček .NET Core podporuje spouštění na několika implementacích rozhraní .NET, které jsou reprezentovány jako rozhraní. Některé z těchto rozhraní jsou tradičními rozhraními, jako je `net46`, které představují .NET Framework. Další sadou je nová rozhraní, která je možné chápat jako "architektury založené na balíčku", která vytváří nový model pro definování rozhraní. Tyto architektury založené na balíčku jsou zcela vytvořeny a definovány jako balíčky a tvoří silný vztah mezi balíčky a architekturami.

## <a name="packages"></a>Balíčky

.NET Core je rozdělené do sady balíčků, které poskytují primitivní typy, typy dat vyšší úrovně, typy kompozic aplikací a běžné pomůcky. Každý z těchto balíčků představuje jedno sestavení se stejným názvem. Například [System. Runtime](https://www.nuget.org/packages/System.Runtime) obsahuje System. Runtime. dll. 

Je výhodné definovat balíčky v jemně odstupňovaném způsobem:

- Jemně odstupňované balíčky se dají dodávat podle vlastního plánu s poměrně omezeným testováním jiných balíčků.
- Jemně odstupňované balíčky můžou mít různou podporu operačního systému a procesoru.
- Jemně odstupňované balíčky mohou mít závislosti specifické pouze pro jednu knihovnu.
- Aplikace jsou menší, protože neodkazované balíčky se nestanou součástí distribuce aplikace.

Některé z těchto výhod se používají jenom za určitých okolností. Například balíčky NET Core budou obvykle dodány na stejný plán se stejnou podporou platformy. V případě údržby je možné opravy distribuovat a instalovat jako malé aktualizace jednoho balíčku. Vzhledem k úzkému rozsahu změn je ověřování a čas potřebný k opravě k dispozici pouze na to, co je potřeba pro jednu knihovnu.

Následuje seznam klíčových balíčků NuGet pro .NET Core:

- [System. Runtime](https://www.nuget.org/packages/System.Runtime) – nejvíce základní balíček .NET Core, včetně <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>a <xref:System.Collections.Generic.IList%601>.
- [System. Collections](https://www.nuget.org/packages/System.Collections) – sada (primárně) obecných kolekcí, včetně <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>.
- [System .NET. http](https://www.nuget.org/packages/System.Net.Http) – sada typů pro síťovou komunikaci HTTP, včetně <xref:System.Net.Http.HttpClient> a <xref:System.Net.Http.HttpResponseMessage>.
- [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) – sada typů pro čtení a zápis do místního nebo síťového úložiště založeného na disku, včetně <xref:System.IO.File> a <xref:System.IO.Directory>.
- [System. Linq](https://www.nuget.org/packages/System.Linq) – sada typů pro dotazování objektů, včetně `Enumerable` a <xref:System.Linq.ILookup%602>.
- [System. Reflection](https://www.nuget.org/packages/System.Reflection) – sada typů pro načítání, kontrolu a aktivaci typů, včetně <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> a <xref:System.Reflection.MethodInfo>.

Místo zahrnutí jednotlivých balíčků je obvykle snazší a pružnější, aby zahrnovaly [Metapackage](#metapackages). Pokud však potřebujete jeden balíček, můžete jej zahrnout jako v následujícím příkladu, který odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) . 

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

## <a name="metapackages"></a>Metabalíčky

Metabalíčky jsou konvence balíčku NuGet pro popis sady balíčků, které jsou smysluplné dohromady. Představují tuto sadu balíčků tím, že je provedou závislosti. Mohou volitelně vytvořit architekturu pro tuto sadu balíčků určením architektury. 

Předchozí verze nástrojů .NET Core (nástroje na bázi Project. JSON a csproj) standardně určily rozhraní a Metapackage. V současné době se však Metapackage implicitně odkazuje na cílovou architekturu, takže každá Metapackage je svázána s cílovou architekturou. Například rozhraní `netstandard1.6` Framework odkazuje na verzi NetStandard. Library 1.6.0 Metapackage. Podobně rozhraní `netcoreapp2.1` Framework odkazuje na Microsoft. NETCore. app verze 2.1.0 Metapackage. Další informace naleznete v tématu [implicitní odkaz na balíček Metapackage v .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Cílení na architekturu a implicitně odkazující na Metapackage znamená, že přidáváte odkaz na každý z jeho závislých balíčků jako jeden gesto. Díky tomu jsou všechny knihovny v těchto balíčcích k dispozici pro IntelliSense (nebo podobné prostředí) a pro publikování vaší aplikace.  

Existují výhody použití metabalíčky:

- Poskytuje pohodlný uživatelské prostředí pro odkazování na velkou sadu jemně odstupňovaných balíčků. 
- Definuje sadu balíčků (včetně specifických verzí), které jsou testovány a dobře spolupracují.

.NET Standard Metapackage je:

- [NETStandard. Library](https://www.nuget.org/packages/NETStandard.Library) – popisuje knihovny, které jsou součástí ".NET Standard". Platí pro všechny implementace rozhraní .NET (například .NET Framework, .NET Core a mono), které podporují .NET Standard. Vytvoří architekturu ' netstandard '.

Klíč .NET Core metabalíčky jsou:

- [Microsoft. NETCore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) -popisuje knihovny, které jsou součástí distribuce .NET Core. Vytvoří rozhraní [`.NETCoreApp` Framework](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Závisí na menším `NETStandard.Library`.
- [Microsoft. AspNetCore. app](https://www.nuget.org/packages/Microsoft.AspNetCore.App) -zahrnuje všechny podporované balíčky z ASP.NET Core a Entity Framework Core s výjimkou těch, které obsahují závislosti třetích stran. Další informace najdete v článku [Microsoft. AspNetCore. app Metapackage pro ASP.NET Core](/aspnet/core/fundamentals/metapackage-app) .
- [Microsoft. AspNetCore. All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) – zahrnuje všechny podporované balíčky z ASP.NET Core, Entity Framework Core a interních a jiných závislostí, které používají ASP.NET Core a Entity Framework Core. Další informace najdete v tématu [Microsoft. AspNetCore. All Metapackage for ASP.NET Core 2. x](/aspnet/core/fundamentals/metapackage) .
- [Microsoft. NETCore. Portable. Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) – sada Facade kompatibility, která umožňuje spuštění přenosných knihoven tříd (PCLS) založených na rozhraní .NET Core.

## <a name="frameworks"></a>Architektury

Balíčky .NET Core každý podporují sadu rozhraní Runtime. Rozhraní popisují dostupnou sadu rozhraní API (a potenciálně jiné vlastnosti), které můžete spoléhat na to, kdy cílíte na dané rozhraní. Používají se ve verzi, protože se přidají nová rozhraní API.

Například [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) podporuje následující architektury:

- . NETFramework, verze = 4.6
- . NETStandard, verze = 1.3
- 6 platforem Xamarin (například xamarinios10)

Je užitečné, abyste nališili první dvě z těchto rozhraní, protože jsou to příklady dvou různých způsobů, které jsou definovány v rozhraních.

Rozhraní `.NETFramework,Version=4.6` Framework představuje dostupná rozhraní API v .NET Framework 4,6. Můžete vytvořit knihovny zkompilované pomocí referenčních sestavení .NET Framework 4,6 a potom tyto knihovny distribuovat do balíčků NuGet ve složce net46 lib. Bude se používat pro aplikace, které cílí na .NET Framework 4,6 nebo které jsou s ním kompatibilní. To je způsob, jak všechny architektury tradičně pracovaly.

Rozhraní `.NETStandard,Version=1.3` Framework je architekturou založenou na balíčku. Spoléhá na balíčky, které cílí na rozhraní a definují a zveřejňují rozhraní API v souvislosti s rozhraním.

## <a name="package-based-frameworks"></a>Rozhraní založená na balíčcích

Mezi architekturami a balíčky existuje obousměrný vztah. První část definuje rozhraní API dostupná pro danou architekturu, například `netstandard1.3`. Balíčky, které cílí na `netstandard1.3` (nebo kompatibilní architektury, jako je `netstandard1.0`) definují rozhraní API, které jsou k dispozici pro `netstandard1.3`. To může být zvukové jako cyklická definice, ale ne. Na základě typu "založeného na balíčku" je definice rozhraní API pro rozhraní dodávána z balíčků. Rozhraní samotné nedefinuje žádná rozhraní API.

Druhá část vztahu je výběr assetu. Balíčky mohou obsahovat prostředky pro více platforem. Vzhledem k tomu, že se používá odkaz na sadu balíčků nebo metabalíčky, je nutné určit, který prostředek se má vybrat, například `net46` nebo `netstandard1.3`. Je důležité vybrat správný Asset. Například `net46` Asset není pravděpodobně kompatibilní s .NET Framework 4,0 nebo .NET Core 1,0.

Tuto relaci můžete zobrazit na následujícím obrázku. *Rozhraní API* cílí a definuje rozhraní *.* *Rozhraní* se používá pro *Výběr prostředku*. *Asset* poskytuje rozhraní API.

![Složení architektury založené na balíčku](./media/packages/package-framework.png)

Mezi dvě primární architektury založené na balíčku, které se používají s .NET Core, patří:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

Rozhraní .NET Standard ([moniker cílového rozhraní Framework](../standard/frameworks.md): `netstandard`) představuje rozhraní API definovaná a postavená nad [.NET Standard](../standard/net-standard.md). Knihovny určené ke spuštění na více modulech runtime by měly cílit na toto rozhraní. Budou podporovány v jakémkoli prostředí runtime kompatibilním .NET Standard, jako je .NET Core, .NET Framework a mono/Xamarin. Každý z těchto modulů runtime podporuje sadu .NET Standard verzí v závislosti na tom, jaká rozhraní API implementují.

Rozhraní `netstandard` Framework implicitně odkazuje na [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) Metapackage. Například následující soubor projektu MSBuild označuje, že projekt cílí na `netstandard1.6`, které odkazují na [`NETStandard.Library` verze 1,6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) Metapackage.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Nicméně odkazy rozhraní .NET Framework a Metapackage v souboru projektu nemusejí odpovídat a můžete použít prvek `<NetStandardImplicitPackageVersion>` v souboru projektu k určení verze rozhraní, která je nižší než verze Metapackage. Například následující soubor projektu je platný.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Může se stát, že se nezvykle cílit na `netstandard1.3`, ale použijte verzi 1.6.0 `NETStandard.Library`. Je to platný případ použití, protože Metapackage udržuje podporu pro starší verze `netstandard`. Může se jednat o případ, který jste standardizováni ve verzi 1.6.0 Metapackage, a použít ho pro všechny knihovny, které cílí na různé verze `netstandard`. S tímto přístupem je potřeba obnovit jenom `NETStandard.Library` 1.6.0 a ne předchozí verze. 

Opačný počet by neměl být platný: cílový `netstandard1.6` s verzí 1.3.0 `NETStandard.Library`. Nejde cílit na vyšší rámec s nižším Metapackage, protože nižší verze Metapackage nebude zveřejňovat žádné prostředky pro toto rozhraní vyšší úrovně. Schéma správy verzí pro metabalíčky vyhodnotí, že metabalíčky odpovídá nejvyšší verzi rozhraní Framework, které popisují. Na základě schématu správy verzí je první verze `NETStandard.Library` v 1.6.0 s tím, že obsahuje `netstandard1.6` assety. v 1.3.0 se používá v příkladu výše, pro symetrii s výše uvedeným příkladem, ale ve skutečnosti neexistuje.

### <a name="net-core-application"></a>Aplikace .NET Core

Rozhraní .NET Core ([moniker cílového rozhraní Framework](../standard/frameworks.md): `netcoreapp`) představuje balíčky a přidružená rozhraní API, která jsou součástí distribuce .NET Core a modelu konzolové aplikace, kterou poskytuje. Aplikace .NET Core musí používat toto rozhraní, protože by se měly zaměřit na model konzolové aplikace, stejně jako knihovny, které mají být spouštěny pouze v rozhraní .NET Core. Použití tohoto rozhraní omezuje aplikace a knihovny na spouštění pouze v .NET Core. 

`Microsoft.NETCore.App` Metapackage cílí na `netcoreapp` Framework. Poskytuje přístup k knihovnám ~ 60, ~ 40, které poskytuje balíček `NETStandard.Library`, a navíc další. K získání přístupu k dalším rozhraním API můžete odkazovat na další knihovny, které cílí na `netcoreapp` nebo kompatibilní architektury, jako je například `netstandard`. 

Většina dalších knihoven poskytovaných `Microsoft.NETCore.App` také cílí na `netstandard` s ohledem na to, že jejich závislosti jsou splněné jinými knihovnami `netstandard`. To znamená, že `netstandard` knihovny také mohou odkazovat na tyto balíčky jako závislosti. 
