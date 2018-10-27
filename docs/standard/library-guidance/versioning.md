---
title: Knihovny správy verzí a .NET
description: Doporučené osvědčené postupy pro správu verzí knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: f95c8ade1f91af5c13184b839b327c9397c6fe5a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187855"
---
# <a name="versioning"></a>Správa verzí

Softwarová knihovna je jen zřídka dokončena ve verzi 1.0. Dobré knihovny postupně měnit, přidává funkce, opravy chyb a zvýšení výkonu. Je důležité, že vydání nové verze knihovny .NET, zadání další hodnoty s jednotlivými verzemi, aniž by vás to stávající uživatele.

## <a name="breaking-changes"></a>Rozbíjející změny v

Informace o zpracování zásadní změny mezi verzí najdete v tématu [Rozbíjející změny v](./breaking-changes.md).

## <a name="version-numbers"></a>Čísla verzí

Knihovna .NET má mnoho způsobů, jak určit verzi. Tyto verze jsou nejdůležitější:

### <a name="nuget-package-version"></a>Verze balíčku NuGet

[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazí na NuGet.org, Správce balíčků NuGet aplikace Visual Studio a že je přidaný do zdrojového kódu při použití balíčku. Verze balíčku NuGet je běžně uvidí uživatelé. číslo verze a budete si ji po hovoří o verzi knihovny, které jste používali. Verze balíčku NuGet používá NuGet a nemá žádný vliv na chování modulu runtime.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identifikátor balíčku NuGet, v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku nuget. Například `Newtonsoft.Json`  +  `11.0.2`. Balíček s příponu předběžné verze balíčků a má zvláštní chování, které je ideální pro testování. Další informace najdete v tématu [balíčky v předběžné verzi](./nuget.md#pre-release-packages).

Protože verze balíčku NuGet je nejviditelnější verze pro vývojáře, je vhodné jej aktualizovat pomocí [Semantic Versioning (SemVer)](https://semver.org/). SemVer určuje význam změny mezi vydání a pomáhá vývojářům provést informované rozhodnutí při výběru jaké verze se má použít. Například, že přejdete z `1.0` k `2.0` označuje, že můžou být dostupné nejnovější změny.

**✔️ ZVAŽTE** pomocí [SemVer 2.0.0](https://semver.org/) verzi balíčku NuGet.

**PROVEĎTE ✔️** použití verze balíčku NuGet ve veřejné dokumentaci, jako je číslo verze, který uživatelé uvidí běžně.

**PROVEĎTE ✔️** obsahovat příponu předběžné verze při uvolnění-stabilní verze balíčku.

> Uživatelé musí přihlásit se k získání balíčky v předběžné verzi, abyste pochopili, že balíček není úplný.

### <a name="assembly-version"></a>Verze sestavení

Verze sestavení je co používá modul CLR za běhu k výběru, kterou verzi sestavení, které chcete načíst. Výběr sestavení pomocí správy verzí pouze se vztahuje na sestavení se silným názvem.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework CLR vyžaduje načtení silné přesnou shodou s názvem sestavení. Například `Libary1, Version=1.0.0.0` byl kompilován s odkazem na `Newtonsoft.Json, Version=11.0.0.0`. Rozhraní .NET Framework pouze načte tento přesnou verzi `11.0.0.0`. Načíst jinou verzi za běhu, musí přidat přesměrování vazby do konfiguračního souboru aplikace .NET.

Silné názvy v kombinaci s verzí sestavení umožňuje [načtení verze striktní sestavení](../../framework/app-domains/assembly-versioning.md). Silné názvy knihovny obsahuje řadu výhod, často výsledkem výjimky modulu CLR, které nelze nalézt sestavení a [vyžaduje přesměrování vazeb](../../framework/configure-apps/redirect-assembly-versions.md) v `app.config` / `web.config` vyřešit. Bylo volný načítání sestavení .NET core a .NET Core CLR bude automaticky načíst sestavení za běhu s vyšší verzí.

**✔️ ZVAŽTE** pouze AssemblyVersion včetně hlavní verze.

> například knihovna 1.0 a knihovny 1.0.1 obě mají AssemblyVersion z `1.0.0.0`, zatímco AssemblyVersion z knihovny 2.0 `2.0.0.0`. Při změně verze sestavení méně často, snižuje přesměrování vazby.

**✔️ ZVAŽTE** udržování synchronizace číslo hlavní verze AssemblyVersion a verze balíčku NuGet.

> AssemblyVersion je součástí některých informační zprávy zobrazí uživateli, například název sestavení a sestavení kvalifikované názvy typů v zprávy o výjimkách. Udržování vztahu mezi verzemi poskytuje další informace pro vývojáře o verzi, které využívají.

**❌ NEPODPORUJÍ** mají pevnou AssemblyVersion.

> Zatímco neměnné AssemblyVersion se vyhnete nutnosti přesměrování vazby, znamená to, pouze jednu verzi sestavení lze nainstalovat v globální mezipaměti sestavení (GAC). Aplikace, které odkazují na toto sestavení v GAC také, přeruší, pokud jiná aplikace aktualizuje s rozbíjející změny v globální mezipaměti sestavení.

### <a name="assembly-file-version"></a>Verze souboru sestavení

Verze souboru sestavení se používá k zobrazení verze souboru ve Windows a nemá žádný vliv na chování modulu runtime. Nastavení této verze je volitelný. Je zobrazen v dialogovém okně vlastností souboru v Průzkumníku Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumníka Windows")

> [!NOTE]
> Sestavení neškodného upozornění je vyvoláno, pokud tato verze formát nedodržuje `Major.Minor.Build.Revision`. Upozornění můžete ignorovat.

**✔️ ZVAŽTE** číslo jako revize AssemblyFileVersion včetně kontinuální integrace sestavení.

> Například vytváříte verze 1.0.0 vašeho projektu a číslo sestavení kontinuální integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.

### <a name="assembly-informational-version"></a>Informační verze sestavení

Informační verze sestavení se používá k zaznamenání Další informace o verzi a nemá žádný vliv na chování modulu runtime. Nastavení této verze je volitelný. Pokud používáte SourceLink, tato verze se nastaví na sestavení se verze balíčku NuGet a verze ovládacího prvku zdroje. Například `1.0.0-beta1+204ff0a` obsahuje hodnotu hash potvrzení sestavení byla vytvořena z zdrojového kódu. Další informace najdete v tématu [SourceLink](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

**❌ Nepoužívejte** nastavení informační verze sestavení sami.

> Povolte SourceLink automaticky generovat verze obsahuje NuGet a zdrojový ovládací prvek metadat.

>[!div class="step-by-step"]
[Předchozí](./publish-nuget-package.md)
[další](./breaking-changes.md)
