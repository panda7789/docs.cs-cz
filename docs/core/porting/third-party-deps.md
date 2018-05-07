---
title: Portování do .NET Core - analyzovat závislostmi třetích stran
description: Zjistěte, jak analyzovat závislosti třetích stran k portu z rozhraní .NET Framework projektu na .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: a5affd8f1c493a87b2a4f7cd4096d168d404626a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="analyze-your-third-party-dependencies"></a>Analýza závislostmi třetích stran

Pokud hledáte, můžete k portu kódu .NET Core nebo .NET Standard, je prvním krokem v procesu přenosem pochopit závislostmi třetích stran. Třetí strany závislosti jsou buď [balíčky NuGet](#analyze-referenced-nuget-packages-on-your-project) nebo [knihovny DLL](#analyze-dependencies-that-arent-nuget-packages) jste odkazující na ve vašem projektu. Posuďte každá závislost a vytvořte pohotovostní plán závislosti, které nejsou kompatibilní s .NET Core. Tento článek ukazuje, jak zjistit, jestli závislost kompatibilní s .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Analýza odkazované balíčky NuGet ve vašem projektu

Pokud jste odkazování balíčky NuGet ve vašem projektu, je třeba ověřit, pokud jsou kompatibilní s .NET Core.
To provést dvěma způsoby:

* [Pomocí Průzkumníku balíčků NuGet aplikace](#analyze-nuget-packages-using-nuget-package-explorer) (nejspolehlivější způsob).
* [Pomocí webu nuget.org](#analyze-nuget-packages-using-nugetorg).

Po analýze balíčků, pokud nejsou kompatibilní s .NET Core a pouze cílové rozhraní .NET Framework, můžete zkontrolovat, pokud [režim kompatibility rozhraní .NET Framework](#net-framework-compatibility-mode) může pomoct s přenosem procesu.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analýza balíčků NuGet pomocí Průzkumníku balíčků NuGet

Balíček NuGet je sám sadu složek, které obsahují sestavení specifické pro platformu. Proto je třeba zkontrolovat, zda je složka, která obsahuje kompatibilní sestavení uvnitř balíčku.

Nejjednodušší způsob, jak zkontrolovat balíček NuGet složek se má používat [Explorer balíček NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) nástroj. Po instalaci ji, použijte následující postup zobrazíte názvy složek:

1. Otevřete Průzkumníka balíček NuGet.
2. Klikněte na tlačítko **otevřít balíček z online kanálu**.
3. Vyhledejte název balíčku.
4. Ve výsledcích hledání vyberte název balíčku a klikněte na tlačítko **otevřete**.
5. Rozbalte *lib* složky na pravé straně a podívejte se na názvy složek.

Vyhledejte složku s žádným z následujících názvů:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Tyto hodnoty jsou [cílový Framework Monikery (TFMs)](../../standard/frameworks.md) , mapování na verzích [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční profily přenosných třída knihovny PCL (), které jsou kompatibilní s .NET Core.

> [!IMPORTANT]
> Při prohlížení TFMs, které podporuje balíček, Všimněte si, že `netcoreapp*`, při kompatibilní, jenom .NET Core projekty a ne pro rozhraní .NET standardní projekty.
> Knihovny, který se zaměřuje jenom `netcoreapp*` a není `netstandard*` pouze mohou být využívány službou jiných aplikací .NET Core.

Existují také některé starší verze TFMs v předběžné verze jádra rozhraní .NET, která je také možné kompatibilní:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Při těchto TFMs pravděpodobně pracovat s kódu, neexistuje žádná záruka kompatibility. Balíčky s tyto TFMs nebyly vytvořené s balíčky předběžné verze .NET Core. Poznamenejte si při (nebo pokud) balíčky pomocí těchto TFMs jsou aktualizovány na .NET Standard na základě.

> [!NOTE]
> Chcete-li použít balíček cílení tradiční PCL nebo předběžné verze .NET Core cíl, je nutné použít `PackageTargetFallback` MSBuild element v souboru projektu.
> Další informace o tomto prvku MSBuild najdete v tématu [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analýza balíčků NuGet pomocí nuget.org

Alternativně uvidíte TFMs, které podporuje každý balíček na [nuget.org](https://www.nuget.org/) pod **závislosti** části stránky balíčku.

I když pomocí webu je jednodušší metodu k ověření kompatibility, **závislosti** informace nejsou k dispozici na webu pro všechny balíčky.

### <a name="net-framework-compatibility-mode"></a>Režim kompatibility rozhraní .NET framework

Po analýze balíčky NuGet, je možné, že pouze cílové rozhraní .NET Framework, stejně jako většinu balíčky NuGet.

Od verze rozhraní .NET 2.0 standardní, byla zavedena režimu kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje .NET Standard a .NET Core projekty tak, aby odkazovaly knihovny rozhraní .NET Framework. Odkazování na rozhraní .NET Framework knihovny nefunguje pro všechny projekty, jako třeba když knihovny používá Windows Presentation Foundation (WPF) rozhraní API, ale jeho odblokování mnoho scénářů s přenosem.

Při odkazu na balíčky NuGet, cílených na rozhraní .NET Framework v projektu, například [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), se zobrazí upozornění, záložní balíčku ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) podobně jako v následujícím příkladu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Tento upozornění se zobrazí, když přidáte balíček a pokaždé, když vytvoříte a ujistěte se otestování tento balíček v projektu. Pokud projekt funguje podle očekávání, můžete tak, že upravíte vlastnosti balíčku v sadě Visual Studio nebo ruční úpravy souboru projektu ve svém oblíbeném kód editoru potlačit tohoto upozornění.

Potlačit upozornění úpravou souboru projektu, Najít `PackageReference` balíčku pro položku, kterou chcete potlačení upozornění pro a přidat `NoWarn` atribut. `NoWarn` Atribut přijímá seznam všech upozornění ID oddělených čárkami. Následující příklad ukazuje, jak můžete potlačit `NU1701` upozornění pro `Huitian.PowerCollections` balíček úpravou souboru projektu ručně:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Další informace o tom, jak potlačení upozornění kompilátoru v sadě Visual Studio najdete v tématu [potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co dělat, když vaše závislost balíčku NuGet nefunguje v .NET Core

Existuje několik věcí, které můžete provést, pokud nelze spustit na .NET Core balíčku NuGet, které závisí na:

1. Pokud projekt je open source a je hostovaná někde jako GitHub, můžete použít vývojáři přímo.
2. Obraťte se na autora přímo na [nuget.org](https://www.nuget.org/). Vyhledejte balíček a klikněte na **kontaktujte vlastníky** na levé straně stránky daného balíčku.
3. Můžete hledat jiný balíček, který běží na .NET Core, který provede stejnou úlohu jako balíčku, který jste používali.
4. Můžete se pokusit napsat kód, že balíček dělal sami.
5. Závislost na balíček může eliminovat alespoň změnou funkce aplikace, dokud nebude k dispozici kompatibilní verzi balíčku.

Mějte na paměti, že údržby programu open source projektu a vydavatelé balíček NuGet jsou často dobrovolníků. Přispívají, protože zajímají pro danou doménu, provést zdarma a často mají různé denní úlohy. Proto buďte s vědomím, při kontaktování je požádat o podporu .NET Core.

Pokud nelze vyřešit problém s žádným z výše, budete muset port na .NET Core později.

Tým služby .NET chcete vědět, které knihovny jsou nejdůležitější pro podporu s .NET Core. Můžete odeslat e-mail na dotnet@microsoft.com o knihovny, které chcete použít.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analýza závislosti, které nejsou balíčků NuGet

Můžete mít závislost, která není balíčku NuGet, jako je například knihovny DLL v systému souborů. Jediný způsob, jak určit přenositelnost této závislosti se ke spuštění [.NET přenositelnost analyzátor](https://github.com/Microsoft/dotnet-apiport) nástroj. Nástroj můžete analyzovat sestavení cílených na rozhraní .NET Framework a identifikovat rozhraní API, která nejsou přenosný na jiné platformy .NET jako .NET Core. Nástroj můžete spustit jako konzolové aplikace nebo jako [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Další kroky

Pokud jste portování knihovnu, podívejte se na [portování knihovnách](libraries.md).
