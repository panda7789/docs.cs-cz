---
title: Správa verzí a knihovny .NET
description: Doporučení osvědčených postupů pro správu verzí knihoven .NET.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745027"
---
# <a name="versioning"></a>Správa verzí

Knihovna softwaru je ve verzi 1,0 jenom zřídka. Dobrá knihovna se vyvíjí v průběhu času, přidávání funkcí, opravy chyb a zlepšení výkonu. Je důležité, abyste si vyuvolnili nové verze knihovny .NET, která poskytuje další hodnotu s každou verzí bez přerušení stávajících uživatelů.

## <a name="breaking-changes"></a>Změny způsobující chyby

Informace o zpracování nejnovějších změn mezi verzemi najdete v tématu [přerušující změny](./breaking-changes.md).

## <a name="version-numbers"></a>Čísla verzí

Knihovna .NET má mnoho způsobů, jak určit verzi. Nejdůležitější jsou tyto verze:

### <a name="nuget-package-version"></a>Verze balíčku NuGet

[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazuje v NuGet.org, správce balíčků NuGet sady Visual Studio a při použití balíčku se přidá do zdrojového kódu. Verze balíčku NuGet je číslo verze, které se uživatelům obvykle uvidí a na něj budou odkazovat, když budou komunikovat s verzí knihovny, kterou používají. Verzi balíčku NuGet používá NuGet a nemá žádný vliv na chování za běhu.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identifikátor balíčku NuGet v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku v NuGet. Příklad: `Newtonsoft.Json` + `11.0.2`. Balíček s příponou je předběžná verze balíčku a má speciální chování, které je ideální pro testování. Další informace najdete v tématu [předběžné verze balíčků](./nuget.md#pre-release-packages).

Vzhledem k tomu, že verze balíčku NuGet je nejvíce viditelná pro vývojáře, je vhodné ji aktualizovat pomocí [sémantického správy verzí (SemVer)](https://semver.org/). SemVer označuje význam změn mezi vydanými verzemi a pomáhá vývojářům v rozhodování o tom, jaká verze se má použít. Například z `1.0` na `2.0` znamená, že existují potenciálně zásadní změny.

✔️ Zvažte použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.

✔️ použít verzi balíčku NuGet ve veřejné dokumentaci, protože se jedná o číslo verze, které se uživatelům běžně zobrazuje.

při uvolňování nestabilního balíčku ✔️ zahrnout příponu předběžné verze.

> Uživatelé musí souhlasit s načtením předběžných balíčků, aby porozuměli tomu, že balíček není kompletní.

### <a name="assembly-version"></a>Verze sestavení

Verze sestavení je to, co modul CLR používá za běhu k výběru verze sestavení, které se má načíst. Výběr sestavení pomocí správy verzí se vztahuje pouze na sestavení se silným názvem.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework CLR požaduje přesnou shodu pro načtení silného pojmenovaného sestavení. Například `Libary1, Version=1.0.0.0` byla zkompilována s odkazem na `Newtonsoft.Json, Version=11.0.0.0`. .NET Framework načte jenom přesnou verzi `11.0.0.0`. Pro načtení jiné verze za běhu musí být přesměrování vazby přidáno do konfiguračního souboru aplikace .NET.

Silné pojmenování v kombinaci s verzí sestavení umožňuje [striktní načítání verzí sestavení](../assembly/versioning.md). I když silné pojmenování knihovny má několik výhod, často má za následek výjimku za běhu, kterou nelze najít, a [vyžaduje přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) v `app.config`/`web.config` k tomu, aby je bylo možné opravit. Načítání sestavení .NET Core bylo uvolněno a modul CLR .NET Core bude automaticky načítat sestavení za běhu s vyšší verzí.

✔️ Zvažte pouze hlavní verzi v AssemblyVersion.

> například knihovna 1,0 a 1.0.1 knihovny mají AssemblyVersion `1.0.0.0`, zatímco knihovna 2,0 obsahuje AssemblyVersion `2.0.0.0`. Pokud se verze sestavení nemění méně často, snižuje se přesměrování vazby.

✔️ Zvažte zachování hlavního čísla verze AssemblyVersion a verze balíčku NuGet v synchronizaci.

> AssemblyVersion je součástí některých informačních zpráv zobrazených uživateli, například název sestavení a kvalifikované typy názvů sestavení ve zprávách o výjimkách. Udržování vztahu mezi verzemi poskytuje další informace pro vývojáře, kteří používají verzi.

❌ nemají pevně AssemblyVersion.

> I když nezměněný AssemblyVersion vybrání nutnosti přesměrování vazby, znamená to, že v globální mezipaměti sestavení (GAC) může být nainstalována pouze jedna verze sestavení. Aplikace, které odkazují na sestavení v globální mezipaměti sestavení (GAC), budou také přerušit, pokud jiná aplikace aktualizuje sestavení GAC s nezměněnými změnami.

### <a name="assembly-file-version"></a>Verze souboru sestavení

Verze souboru sestavení se používá k zobrazení verze souboru ve Windows a nemá žádný vliv na chování za běhu. Nastavení této verze je volitelné. Zobrazuje se v dialogovém okně Vlastnosti souboru v Průzkumníkovi Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumník Windows")

✔️ Zvažte zahrnutí čísla sestavení průběžné integrace jako revize AssemblyFileVersion.

> Například sestavíte 1.0.0 verze projektu a číslo sestavení průběžné integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.

pro verzi souboru ✔️ použít formát `Major.Minor.Build.Revision`.

> I když verze souboru není rozhraním .NET nikdy používána, [systém Windows očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) je ve formátu `Major.Minor.Build.Revision`. Pokud verze nedodržuje tento formát, bude vyvolána výstraha.

### <a name="assembly-informational-version"></a>Informační verze sestavení

Informační verze sestavení se používá k záznamu dalších informací o verzi a nemá žádný vliv na chování za běhu. Nastavení této verze je volitelné. Pokud používáte zdrojový odkaz, bude tato verze nastavena pro sestavení s verzí balíčku NuGet a verzí správy zdrojového kódu. Například `1.0.0-beta1+204ff0a` obsahuje hodnotu hash potvrzení zdrojového kódu, ze kterého bylo sestavení sestaveno. Další informace najdete v tématu [zdrojový odkaz](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Starší verze sady Visual Studio vyvolají upozornění sestavení, pokud tato verze nedodržuje formát `Major.Minor.Build.Revision`. Upozornění lze bezpečně ignorovat.

❌ se vyhnout nastavení informační verze sestavení sami.

> Povolí, aby SourceLink automaticky vygenerovala verzi, která obsahuje metadata nástroje NuGet a správy zdrojového kódu.

>[!div class="step-by-step"]
>[Předchozí](publish-nuget-package.md)
>[Další](breaking-changes.md)
