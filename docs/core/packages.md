---
title: Balíčky, metabalíčky a architektury – .NET Core
description: Přečtěte si terminologie pro balíčky, metabalíčky a architektury.
author: richlander
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: a03a4961b116b05468ac6c6ce5e648c07a77b7f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663321"
---
# <a name="packages-metapackages-and-frameworks"></a>Balíčky, metabalíčky a architektury

.NET core je platforma provedené balíčků NuGet. Některé produktu prostředí je výhodné podrobných definice balíčků některá z hrubých. Přizpůsobí tento duality produktu je distribuován jako podrobné sada balíčků a hrubší bloků dat s neformálně označované jako typ balíčku [Microsoft.aspnetcore.all](#metapackages).

Každý z balíčků .NET Core podporují, běží na několika implementace .NET reprezentovaná jako rozhraní. Některé z těchto rozhraní jsou tradiční architektur, jako je třeba `net46`, představující rozhraní .NET Framework. Další sady je nová rozhraní, které si lze představit jako "na základě balíčku rozhraní", které vytvořit nový model pro definování rozhraní. Tyto architektury využívající balíčky jsou zcela vytvořen a definovány jako balíčky, které tvoří silný vztah mezi balíčky a architektur.

## <a name="packages"></a>Balíčky

.NET core je rozdělit na sadu balíčků, které poskytují primitiv, vyšší úrovně datové typy, typy složení aplikace a společné nástroje. Každá z těchto balíčků představují jednoho sestavení se stejným názvem. Například [System.Runtime](https://www.nuget.org/packages/System.Runtime) obsahuje System.Runtime.dll. 

Existují výhody podrobných způsobem definování balíčky:

- Detailní balíčky se dají dodávat podle svého vlastního plánu s relativně omezené testování další balíčky.
- Detailní balíčky můžete zadat rozdílné podporu operačního systému a procesoru.
- Detailní balíčky může obsahovat závislosti, které jsou specifické pouze jedna knihovna.
- Aplikace jsou menší, protože neodkazovaná balíčky nebudou součástí distribuce aplikací.

Některé z těchto výhod používají pouze za určitých okolností. Balíčky .NET Core bude obvykle dodávat podle stejného plánu s podporou platforem pro stejné. V případě údržby, můžete distribuci a instalaci jako malé jeden balíček aktualizace opravy. Z důvodu úzký rozsah změn je omezený na toho, co je potřeba pro jednu knihovnu ověřování a čas, aby k dispozici oprava.

Následuje seznam klíčů balíčky NuGet pro .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) -nejzákladnější balíček .NET Core včetně <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>, a <xref:System.Collections.Generic.IList%601>.
- [System.Collections –](https://www.nuget.org/packages/System.Collections) – sada (primárně) obecných kolekcí, včetně <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) -sadu typů pro komunikaci pomocí protokolu HTTP sítě, včetně <xref:System.Net.Http.HttpClient> a <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -sadu typů pro čtení a zápis na místním nebo síťovém disku úložiště, včetně <xref:System.IO.File> a <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) -sadu typů objektů, včetně dotazování `Enumerable` a <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) -sadu typů pro načítání, kontrolu a aktivaci typů, včetně <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> a <xref:System.Reflection.MethodInfo>.

Obvykle místo včetně každý balíček, je jednodušší a robustnější zahrnout [Microsoft.aspnetcore.all](#metapackages). Ale když budete potřebovat jeden balíček, kterou můžete zahrnout jako v následujícím příkladu, který odkazuje [System.Runtime](https://www.nuget.org/packages/System.Runtime/) balíčku. 

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

Metabalíčky jsou zásady balíčku NuGet pro sadu balíčků, které mají smysl v daném společně s popisem. Tato sada balíčků představují tím, že jejich závislosti. Rozhraní pro tuto sadu balíčků, Volitelně můžete vytvořit zadáním rozhraní. 

Předchozí verze nástroje .NET Core (project.json a csproj nástrojů) ve výchozím nastavení zadané rozhraní i Microsoft.aspnetcore.all. V současné době ale Microsoft.aspnetcore.all implicitně odkazuje cílovou architekturu, tak, aby každý Microsoft.aspnetcore.all je vázán na rozhraní .NET framework. Například `netstandard1.6` framework odkazuje Microsoft.aspnetcore.all NetStandard.Library verze 1.6.0. Podobně platí `netcoreapp2.1` framework odkazuje na balíčky Microsoft.NETCore.App verze 2.1.0 Microsoft.aspnetcore.all. Další informace najdete v tématu [Microsoft.aspnetcore.all implicitní odkaz na balíček v .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Cílení na rozhraní framework a implicitně odkazující Microsoft.aspnetcore.all znamená, že výsledkem bude přidáte odkaz na každý z jeho závislých balíčků jako jedním gestem. Díky tomu všech knihoven do těchto balíčků k dispozici pro IntelliSense (nebo podobné možnosti) a pro publikování vaší aplikace.  

Existují výhody použití metabalíčky:

- Poskytuje pohodlné uživatelské prostředí tak, aby odkazovaly velké sady podrobných balíčků. 
- Definuje sadu balíčků (včetně konkrétních verzí), které jsou testovány a fungují dobře spolupracovaly.

.NET Standard Microsoft.aspnetcore.all je:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) -popisuje knihoven, které jsou součástí na ".NET Standard". Platí pro všechny implementace .NET (například rozhraní .NET Framework, .NET Core a Mono), které podporují .NET Standard. Vytváří rámec "netstandard".

Klíče metabalíčky .NET Core jsou:

- [Balíčky Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) -popisuje knihoven, které jsou součástí distribuce .NET Core. Vytváří [ `.NETCoreApp` framework](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Závisí na menší `NETStandard.Library`.
- [Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) – zahrnuje všechny podporované balíčky z ASP.NET Core a Entity Framework Core s výjimkou těch, které obsahují závislostí třetích stran. Zobrazit [Microsoft.AspNetCore.App Microsoft.aspnetcore.all pro ASP.NET Core](/aspnet/core/fundamentals/metapackage) Další informace.
- [Metabalíček](https://www.nuget.org/packages/Microsoft.AspNetCore.All) – zahrnuje všechny podporované balíčky od třetích stran a vnitřní závislosti používat ASP.NET Core a Entity Framework Core, Entity Framework Core a ASP.NET Core. Zobrazit [metabalíček Microsoft.aspnetcore.all pro ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage) Další informace.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) -sadu fasády kompatibility, které umožňují na základě mscorlib přenosné knihovny tříd (PCLs) ke spuštění v rozhraní .NET Core.

## <a name="frameworks"></a>Architektury

.NET core balíčky podporují sadu rozhraní modulu runtime. Architektury popisují dostupné sady rozhraní API (a případně také další vlastnosti), že se můžete spolehnout na při použití prostředí dané rozhraní. Systémovou správou verzí se při přidání nového rozhraní API.

Například [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) podporuje následující architektury:

- .NETFramework,Version=4.6
- . NETStandard, verze = 1,3
- 6 Xamarin platformy (například xamarinios10)

Je užitečné porovnání první dva z těchto platforem, protože jsou příklady dvěma různými způsoby, že jsou definovány architektury.

`.NETFramework,Version=4.6` Framework představuje dostupná rozhraní API v rozhraní .NET Framework 4.6. Můžete vytvářet knihovny zkompilovaná referenční sestavení rozhraní .NET Framework 4.6 a pak distribuovat těchto knihoven v balíčcích NuGet ve složce lib net46. Použije se pro aplikace, které cílí rozhraní .NET Framework 4.6 nebo které jsou kompatibilní s ním. Toto je způsob, jakým se všemi architekturami tradičně již dříve pracovali.

`.NETStandard,Version=1.3` Framework je platforma využívající balíčky. Spoléhá na balíčky, které se zaměřují na rozhraní framework a definovat tak a zpřístupnit z hlediska rozhraní API.

## <a name="package-based-frameworks"></a>Architektury založené na balíček

Existuje obousměrný vztah mezi rozhraní a balíčků. První část jedná o definici rozhraní API dostupná pro danou platformu, například `netstandard1.3`. Balíčky, které se zaměřují `netstandard1.3` (nebo kompatibilní architektur, jako `netstandard1.0`) definice rozhraní API dostupná pro `netstandard1.3`. Který může připadat jako cyklickou definici, ale není. Tím, že přináší "balíček", definice rozhraní API pro architekturu pochází z balíčků. Samotného rozhraní nedefinuje žádné rozhraní API.

Druhá část relace je výběr majetku. Balíčky mohou obsahovat prostředky pro více platforem. Zadaný odkaz na sadu balíčků a/nebo metabalíčky, rozhraní, je potřeba určit, který prostředek by měla být zaškrtnutá, například `net46` nebo `netstandard1.3`. Je důležité vybrat správný prostředek. Například `net46` asset není pravděpodobné, aby byl kompatibilní s .NET Framework 4.0 nebo .NET Core 1.0.

Zobrazí se tento vztah na následujícím obrázku. *API* cílí a definuje *framework*. *Framework* se používá pro *výběr majetku*. *Asset* poskytuje rozhraní API.

![Architektura využívající balíčku sestavení](./media/packages/package-framework.png)

Dvě primární založené na balíčku architektury použít s .NET Core jsou:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET Standard ([Moniker cílového rozhraní](../standard/frameworks.md): `netstandard`) představuje rozhraní API určené a zabudovány nad rámec [.NET Standard](../standard/net-standard.md). Cílem tohoto rozhraní by měl knihovny, které jsou určeny ke spuštění ve více modulů – runtime. Se bude podporovat na jakékoli .NET Standard kompatibilní modul runtime, jako je .NET Core, .NET Framework a Mono/Xamarin. Každá z těchto modulů runtime podporuje .NET Standard verze, v závislosti na tom, které rozhraní API implementovat.

`netstandard` Framework implicitně odkazuje [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) Microsoft.aspnetcore.all. Například následující soubor projektu MSBuild znamená, že projekt cílí `netstandard1.6`, které odkazuje [ `NETStandard.Library` verze 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) Microsoft.aspnetcore.all.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ale rozhraní framework a Microsoft.aspnetcore.all odkazy v souboru projektu nemusí odpovídat, a můžete použít `<NetStandardImplicitPackageVersion>` prvku v souboru projektu, chcete-li určit verzi rozhraní framework, která je nižší než verze Microsoft.aspnetcore.all. Například následující soubor projektu je neplatný.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

To může zdát neobvyklé k cíli `netstandard1.3` , ale 1.6.0 použitelná verze výsledku `NETStandard.Library`. Je platný případ použití, protože Microsoft.aspnetcore.all udržuje podpora pro starší `netstandard` verze. Může to být případ jste standardizované pro 1.6.0 verzi Microsoft.aspnetcore.all a použít ho pro všechny vaše knihovny, které cílí na širokou škálu `netstandard` verze. Díky tomuto přístupu je potřeba jenom obnovit `NETStandard.Library` 1.6.0 a ne starší verze. 

Naopak autoritou nebude platný: cílení na `netstandard1.6` s 1.3.0 verzi `NETStandard.Library`. Vyšší framework s nižší Microsoft.aspnetcore.all nelze cílit, protože nižší verze Microsoft.aspnetcore.all nebude zveřejnit žádné prostředky pro dané vyšší rozhraní. Schéma vytváření verzí pro metabalíčky vyhodnotí, metabalíčky odpovídají nejvyšší verzi rozhraní framework, které popisují. Tím, že schéma vytváření verzí, první verzi `NETStandard.Library` je v1.6.0 vzhledem k tomu, aby obsahoval `netstandard1.6` prostředky. V1.3.0 se používá v příkladu výše pro symetrie s výše uvedený příklad, ale ve skutečnosti neexistuje.

### <a name="net-core-application"></a>Aplikace .NET core

.NET Core ([Moniker cílového rozhraní](../standard/frameworks.md): `netcoreapp`) framework představuje balíčky a přidružených rozhraní API, které jsou součástí distribuce .NET Core a konzoly aplikační model, který poskytuje. Aplikace pro .NET core musí používat tento systém, kvůli cílené na konzole aplikační model, jako by měl knihovny, které mají být spouštěny pouze v rozhraní .NET Core. Pomocí tohoto rozhraní omezuje aplikací a knihoven ke spuštění pouze v rozhraní .NET Core. 

`Microsoft.NETCore.App` Microsoft.aspnetcore.all cílí `netcoreapp` rozhraní framework. Poskytuje přístup k knihovny přibližně 60, přibližně 40 poskytované `NETStandard.Library` balíčku a další v přidání přibližně 20. Můžete odkazovat na další knihovny, které se zaměřují `netcoreapp` nebo kompatibilní rozhraní, jako například `netstandard`, abyste získali přístup k další rozhraní API. 

Většina další knihovny poskytované `Microsoft.NETCore.App` také směrovat `netstandard` vzhledem k tomu, že jejich závislosti jsou splněny jiná `netstandard` knihovny. To znamená, že `netstandard` knihovny lze také odkazovat na tyto balíčky jako závislosti. 
