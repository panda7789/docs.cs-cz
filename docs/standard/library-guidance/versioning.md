---
title: Správa verzí a knihovny .NET
description: Doporučení osvědčených postupů pro správu verzí knihoven .NET.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400398"
---
# <a name="versioning"></a>Správa verzí

Softwarová knihovna je zřídka dokončena ve verzi 1.0. Dobré knihovny se v průběhu času vyvíjejí, přidávají funkce, opravují chyby a zlepšují výkon. Je důležité, abyste uvolnili nové verze knihovny .NET, které poskytují další hodnotu s každou verzí, aniž by došlo k porušení stávajících uživatelů.

## <a name="breaking-changes"></a>Změny způsobující chyby

Informace o zpracování narušujících změn mezi verzemi naleznete v tématu [Breaking changes](./breaking-changes.md).

## <a name="version-numbers"></a>Čísla verzí

Knihovna .NET má mnoho způsobů, jak určit verzi. Tyto verze jsou nejdůležitější:

### <a name="nuget-package-version"></a>Verze balíčku NuGet

[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazí na NuGet.org, Visual Studio NuGet správce balíčků a je přidán do zdrojového kódu při použití balíčku. Verze balíčku NuGet je číslo verze, které uživatelé běžně uvidí, a budou na něj odkazovat, když mluví o verzi knihovny, kterou používají. Verze balíčku NuGet se používá NuGet a nemá žádný vliv na chování za běhu.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identifikátor balíčku NuGet v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku v NuGet. Příklad: `Newtonsoft.Json` + `11.0.2`. Balíček s příponou je předběžný balíček a má speciální chování, které je ideální pro testování. Další informace naleznete [v tématu Předběžné verze balíčků](./nuget.md#pre-release-packages).

Vzhledem k tomu, že verze balíčku NuGet je nejviditelnější verze pro vývojáře, je vhodné ji aktualizovat pomocí [sémantické versioning (SemVer)](https://semver.org/). SemVer označuje význam změn mezi vydáním a pomáhá vývojářům učinit informované rozhodnutí při výběru, jakou verzi použít. Například přejdete `1.0` `2.0` od k označuje, že potenciálně narušují změny.

✔️ zvažte použití [SemVer 2.0.0](https://semver.org/) k verzi balíčku NuGet.

✔️ do použít balíček NuGet verze ve veřejné dokumentaci, protože je to číslo verze, které uživatelé budou běžně vidět.

✔️ DO zahrnují předběžnou příponu při uvolnění nestabilního balíčku.

> Uživatelé se musí přihlásit k získání předběžných balíčků, aby pochopili, že balíček není dokončen.

### <a name="assembly-version"></a>Verze sestavení

Verze sestavení je to, co CLR používá za běhu k výběru verze sestavení, které chcete načíst. Výběr sestavení pomocí správy verzí platí pouze pro sestavení se silným názvem.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Rozhraní CLR rozhraní Windows .NET Framework vyžaduje přesnou shodu k načtení silného pojmenovanésestavení. Například `Libary1, Version=1.0.0.0` byl zkompilován `Newtonsoft.Json, Version=11.0.0.0`s odkazem na . Rozhraní .NET Framework načte `11.0.0.0`pouze tuto přesnou verzi . Chcete-li načíst jinou verzi za běhu, musí být do konfiguračního souboru aplikace .NET přidáno přesměrování vazby.

Silné pojmenování v kombinaci s verzí sestavení umožňuje [přísné načítání verze sestavení](../assembly/versioning.md). Zatímco silné pojmenování knihovny má řadu výhod, často vede k výjimkám za běhu, že sestavení `app.config` / `web.config` nelze najít a vyžaduje, aby byla [opravena přesměrování vazeb.](../../framework/configure-apps/redirect-assembly-versions.md) Načítání sestavení .NET Core bylo uvolněno a clr jádra .NET bude automaticky načítat sestavení za běhu s vyšší verzí.

✔️ ZVÁŽIT pouze včetně hlavní verze v AssemblyVersion.

> například Knihovna 1.0 a Knihovna 1.0.1 `1.0.0.0`mají verzi AssemblyVersion of , `2.0.0.0`zatímco knihovna 2.0 má Version assemblyversion . Když se verze sestavení mění méně často, snižuje přesměrování vazby.

✔️ zvážit zachování hlavní číslo verze AssemblyVersion a NuGet verze balíčku v synchronizaci.

> AssemblyVersion je součástí některých informačních zpráv zobrazených uživateli, například název sestavení a sestavení kvalifikované názvy typů ve zprávách výjimek. Udržování vztahu mezi verzemi poskytuje vývojářům další informace o tom, kterou verzi používají.

❌Nemají pevnou AssemblyVersion.

> Zatímco neměnné AssemblyVersion vyhýbá nutnosti přesměrování vazby, znamená to, že pouze jednu verzi sestavení lze nainstalovat v globální mezipaměti sestavení (GAC). Také aplikace, které odkazují na sestavení v GAC se přeruší, pokud jiná aplikace aktualizuje sestavení GAC s nejnovější změny.

### <a name="assembly-file-version"></a>Verze souboru sestavení

Verze souboru sestavení se používá k zobrazení verze souboru v systému Windows a nemá žádný vliv na chování za běhu. Nastavení této verze je volitelné. Je viditelná v dialogovém okně Vlastnosti souboru v Průzkumníkovi Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumník Windows")

✔️ ZVÁŽIT včetně průběžné integrace sestavení číslo jako revize AssemblyFileVersion.

> Například vytváříte verzi 1.0.0 projektu a číslo sestavení průběžné integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.

✔️ DO použít `Major.Minor.Build.Revision` formát pro verzi souboru.

> Zatímco verze souboru není nikdy používána rozhraním .NET, `Major.Minor.Build.Revision` systém Windows [očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) bude ve formátu. Upozornění je aktivována, pokud verze nesleduje tento formát.

### <a name="assembly-informational-version"></a>Informační verze sestavení

Informační verze sestavení se používá k záznamu další informace o verzi a nemá žádný vliv na chování za běhu. Nastavení této verze je volitelné. Pokud používáte zdrojový odkaz, tato verze bude nastavena na sestavení s verzí balíčku NuGet plus verze správy zdrojového kódu. Například `1.0.0-beta1+204ff0a` zahrnuje hash potvrzení zdrojového kódu, ze kterého bylo sestavení sestavení sestavení. Další informace naleznete [v tématu Zdrojový odkaz](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Starší verze sady Visual Studio vyvolávají upozornění sestavení, pokud `Major.Minor.Build.Revision`tato verze nedodržuje formát . Upozornění lze bezpečně ignorovat.

❌Vyhněte se nastavení informační verze sestavení sami.

> Povolit SourceLink automaticky generovat verzi obsahující NuGet a source control metadata.

>[!div class="step-by-step"]
>[Předchozí](publish-nuget-package.md)
>[další](breaking-changes.md)
