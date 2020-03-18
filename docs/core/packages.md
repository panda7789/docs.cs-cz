---
title: Balíčky, metabalíčky a rámce - .NET Core
description: Naučte se terminologii pro balíčky, metabalíčky a architektury.
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 657519edf1c0860ee3222c71ce85723e19029a9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398977"
---
# <a name="packages-metapackages-and-frameworks"></a>Balíčky, metabalíčky a architektury

.NET Core je platforma tvořená balíčky NuGet. Některé zkušenosti s produkty těží z jemnozrnné definice obalů, zatímco jiné z hrubých zrnitých. Pro přizpůsobení této duality je jádro .NET Core distribuováno jako jemně odstupňovaná sada balíčků a v hrubších blocích s typem balíčku neformálně nazývaným [metapackage](#metapackages).

Každý balíček .NET Core podporuje spuštění na více implementacích .NET, reprezentované jako architektury. Některé z těchto rámců jsou `net46`tradiční architektury, například , který představuje rozhraní .NET Framework. Další sadou jsou nové rámce, které lze považovat za "rámce založené na balíčcích", které vytvářejí nový model pro definování rámců. Tyto architektury založené na balíčcích jsou zcela vytvořeny a definovány jako balíčky, které tvoří silný vztah mezi balíčky a rámci.

## <a name="packages"></a>Balíčky

.NET Core je rozdělena do sady balíčků, které poskytují primitiva, vyšší úrovně datových typů, typů složení aplikací a běžných nástrojů. Každý z těchto balíčků představuje jedno sestavení se stejným názvem. Například [balíček System.Runtime](https://www.nuget.org/packages/System.Runtime) obsahuje soubor System.Runtime.dll.

Definování balíčků jemně odstupňovaným způsobem má své výhody:

- Jemně odstupňované obaly mohou být dodávány podle vlastního plánu s relativně omezeným testováním jiných balíků.
- Jemně odstupňované balíčky mohou poskytovat různou podporu operačního režimu a procesoru.
- Jemně odstupňované balíčky mohou mít závislosti specifické pouze pro jednu knihovnu.
- Aplikace jsou menší, protože neodkazované balíčky se nestanou součástí distribuce aplikací.

Některé z těchto výhod se používají pouze za určitých okolností. Například balíčky NET Core se obvykle doručují podle stejného plánu se stejnou podporou platformy. V případě údržby mohou být opravy distribuovány a instalovány jako malé aktualizace jednoho balíčku. Vzhledem k úzkému rozsahu změn je ověření a čas pro zpřístupnění opravy omezen na to, co je potřeba pro jednu knihovnu.

Následuje seznam klíčových balíčků NuGet pro .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) - Nejzákladnější balíček <xref:System.Object>.NET Core, včetně <xref:System.String>, , <xref:System.Array>, <xref:System.Action>a <xref:System.Collections.Generic.IList%601>.
- [System.Collections](https://www.nuget.org/packages/System.Collections) - Sada (především) obecných kolekcí, včetně <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) - Sada typů pro síťovou <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpResponseMessage>komunikaci HTTP, včetně a .
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) - Sada typů pro čtení a zápis do místního <xref:System.IO.File> nebo <xref:System.IO.Directory>síťového úložiště na disku, včetně a .
- [System.Linq](https://www.nuget.org/packages/System.Linq) - Sada typů pro dotazování `Enumerable` <xref:System.Linq.ILookup%602>objektů, včetně a .
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) - Sada typů pro načítání, kontrolu a aktivaci <xref:System.Reflection.TypeInfo> <xref:System.Reflection.MethodInfo>typů, včetně <xref:System.Reflection.Assembly>, a .

Obvykle, spíše než včetně každého balíčku, je to jednodušší a robustnější zahrnout [metabalíček](#metapackages). Však pokud potřebujete jeden balíček, můžete jej zahrnout jako v následujícím příkladu, který odkazuje na [balíček System.Runtime.](https://www.nuget.org/packages/System.Runtime/)

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

Metapackage je NuGet balíček konvence pro popis sadu balíčků, které jsou smysluplné společně. Metabalíček představuje tuto sadu balíčků tím, že je závislosti. Metabalíček můžete volitelně vytvořit rámec pro sadu balíčků zadáním rozhraní.

Předchozí verze nástrojů .NET Core (project.json i csproj-based tools) ve výchozím nastavení zadaly rámec i metabalíček. V současné době je však metabalíček implicitně odkazován cílovým rámcem, takže každý metabalíček je vázán na cílový rámec. `netstandard1.6` Například rozhraní odkazuje na metabalíček NetStandard.Library verze 1.6.0. Podobně `netcoreapp2.1` rozhraní odkazuje na metabalíček Microsoft.NETCore.App verze 2.1.0. Další informace naleznete [v tématu Implicitní odkaz na balíček balíčku metabalíčku v ks tětovce .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Cílení na rozhraní a implicitně odkazující na metabalíček znamená, že ve skutečnosti přidáváte odkaz na každý z jeho závislých balíčků jako jediné gesto. Díky tomu jsou všechny knihovny v těchto balíčcích k dispozici pro technologie IntelliSense (nebo podobné prostředí) a pro publikování aplikace.

Použití metabalíčků má své výhody:

- Poskytuje pohodlné uživatelské prostředí pro odkaz na velkou sadu jemně odstupňovaných balíčků.
- Definuje sadu balíčků (včetně konkrétních verzí), které jsou testovány a dobře spolupracují.

Metabalíček .NET Standard je:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) - Popisuje knihovny, které jsou součástí standardu .NET. Platí pro všechny implementace rozhraní .NET, které podporují standard .NET (například rozhraní .NET Framework, .NET Core a Mono). Vytváří `netstandard` rámec.

Metabalíčky jádra klíče .NET jsou:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) - Popisuje knihovny, které jsou součástí distribuce .NET Core. Vytváří `.NETCoreApp` rámec. Záleží na `NETStandard.Library`menší .
- [Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) - Zahrnuje všechny podporované balíčky z ASP.NET core a entity framework core s výjimkou těch, které obsahují závislosti třetích stran. Další informace naleznete [v metabalíčku Microsoft.AspNetCore.App pro ASP.NET Core.](/aspnet/core/fundamentals/metapackage-app)
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) – zahrnuje všechny podporované balíčky z ASP.NET jádra, entity framework core a interní a třetí strany závislosti používané ASP.NET jádra a entity framework core. Další informace naleznete [v metabalíčku Microsoft.AspNetCore.All pro ASP.NET Core 2.x.](/aspnet/core/fundamentals/metapackage)
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) – Sada fasád kompatibility, které umožňují spouštění knihoven přenosných tříd (PCL) založených na mscorlibu na rozhraní .NET Core.

## <a name="frameworks"></a>Rozhraní

Balíčky .NET Core podporují sadu runtime frameworků. Architektury popisují dostupnou sadu rozhraní API (a potenciálně další charakteristiky), na kterou se můžete spolehnout, když cílíte na danou architekturu. Jsou verzí jako nová úložiště API jsou přidány.

Systém [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) například podporuje následující architektury:

- . NETFramework,Verze=4.6
- . NETStandard,Verze=1,3
- 6 platforem Xamarin (například xamarinios10)

Je užitečné kontrastovat první dva z těchto rámců, protože jsou příklady dvou různých způsobů, které jsou definovány rámce:

- Rozhraní `.NETFramework,Version=4.6` framework představuje dostupná rozhraní API v rozhraní .NET Framework 4.6. Můžete vytvářet knihovny zkompilované pomocí referenčních sestavení rozhraní .NET Framework 4.6 a pak tyto knihovny distribuovat v balíčcích NuGet ve složce net46 lib. Bude se používat pro aplikace, které cílí na rozhraní .NET Framework 4.6 nebo které jsou s ním kompatibilní. Takto tradičně fungovaly všechny rámce.

- Rámec `.NETStandard,Version=1.3` je rámec založený na balíčcích. Spoléhá na balíčky, které se zaměřují na rozhraní definovat a vystavit rozhraní API z hlediska rozhraní.

## <a name="package-based-frameworks"></a>Rámce založené na balíčcích

Existuje obousměrný vztah mezi rámci a balíčky. První část je definování rozhraní API, která jsou `netstandard1.3`k dispozici pro daný rámec, například . Balíčky, `netstandard1.3` které cílí (nebo kompatibilní architektury, jako je `netstandard1.0`) definovat rozhraní API k dispozici pro `netstandard1.3`. To může znít jako kruhová definice, ale není. Na základě toho, že "založené na balíčcích", definice rozhraní API pro rozhraní framework pochází z balíčků. Samotný rámec nedefinuje žádná rozhraní API.

Druhou částí vztahu je výběr majetku. Balíčky mohou obsahovat prostředky pro více architektur. Vzhledem k tomu, odkaz na sadu balíčků a metapackages, rámec je potřeba `net46` určit, který majetek by měl být vybrán, například nebo `netstandard1.3`. Je důležité vybrat správný datový zdroj. Například `net46` datový zdroj není pravděpodobně kompatibilní s rozhraním .NET Framework 4.0 nebo .NET Core 1.0.

Tento vztah můžete vidět na následujícím obrázku. *Rozhraní API* cíle a definuje *rozhraní*. *Rámec* se používá pro *výběr majetku*. *Prostředek* poskytuje rozhraní API.

![Složení rámce založené na balíčcích](./media/packages/package-framework.png)

Dva primární architektury založené na balíčcích používané s .NET Core jsou:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

Rozhraní .NET Standard[(Target Framework Moniker](../standard/frameworks.md): `netstandard`) představuje rozhraní API definovaná a postavená na [rozhraní .NET Standard](../standard/net-standard.md). Knihovny, které jsou určeny ke spuštění na více runtimes by měl cílit na tento rámec. Budou podporovány v libovolném modulu runtime kompatibilním se standardem .NET, například .NET Core, .NET Framework a Mono/Xamarin. Každý z těchto runtimes podporuje sadu verzí .NET Standard, v závislosti na rozhraní API, které implementují.

Rozhraní `netstandard` implicitně odkazuje [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) metapackage. Například následující soubor projektu MSBuild označuje, `netstandard1.6`že projekt cíle , který odkazuje na [ `NETStandard.Library` metapackage verze 1.6.](https://www.nuget.org/packages/NETStandard.Library/1.6.0)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Odkazy na rozhraní a metabalíček v souboru projektu se však `<NetStandardImplicitPackageVersion>` nemusí shodovat a prvek v souboru projektu můžete použít k určení verze architektury, která je nižší než verze metabalíčku. Například následující soubor projektu je platný.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Může se zdát `netstandard1.3` divné zaměřit se, ale použít `NETStandard.Library`verzi 1.6.0 . Jedná se o platný případ použití, protože metabalíček udržuje podporu pro starší `netstandard` verze. Mohlo by to být případ, který jste standardizovali na verzi metabalíčku 1.6.0 a používali ji `netstandard` pro všechny knihovny, které se zaměřují na různé verze. S tímto přístupem stačí `NETStandard.Library` obnovit 1.6.0 a ne starší verze.

Naopak by nebylplatný: `netstandard1.6` cílení s verzí 1.3.0 aplikace `NETStandard.Library`. Vyšší rámec nelze cílit na nižší metapackage, protože metabalíček s nižší verzí nezpřístupní žádné prostředky pro tuto vyšší architekturu. Schéma správy verzí pro metabalíčky tvrdí, že metabalíčky odpovídají nejvyšší verzi rozhraní, které popisují. Na základě systému správy verzí je `NETStandard.Library` první verze verze 1.6.0 vzhledem k tomu, že obsahuje `netstandard1.6` aktiva. (Pro symetrii s předchozím příkladem se zde používá v1.3.0, ale ve skutečnosti neexistuje.)

### <a name="net-core-application"></a>Aplikace v .NET Core

Rozhraní .NET Core ( Target Framework `netcoreapp`[Moniker](../standard/frameworks.md): ) představuje balíčky a přidružená rozhraní API, která jsou dodávána s distribucí .NET Core a modelem aplikace konzoly, který poskytuje. Aplikace .NET Core musí používat tento rámec z důvodu cílení na model aplikace konzoly, stejně jako knihovny, které měly být spuštěny pouze na .NET Core. Použití tohoto rozhraní omezuje aplikace a knihovny na spouštění pouze na .NET Core.

Metabalíček `Microsoft.NETCore.App` se `netcoreapp` zaměřuje na rámec. Poskytuje přístup k ~ 60 knihoven, ~ `NETStandard.Library` 40 poskytované balíček a ~ 20 více navíc. Můžete odkazovat na další `netcoreapp` knihovny, které `netstandard`cílí nebo kompatibilní architektury, například , chcete-li získat přístup k dalším rozhraním API.

Většina dalších knihoven `Microsoft.NETCore.App` poskytovaných `netstandard` také cíl vzhledem k `netstandard` tomu, že jejich závislosti jsou splněny jinými knihovnami. To znamená, že `netstandard` knihovny mohou také odkazovat na tyto balíčky jako závislosti.
