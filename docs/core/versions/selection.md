---
title: Vyberte, kterou verzi .NET Core chcete použít.
description: Zjistěte, jak rozhraní .NET Core automaticky vyhledá a vybere verze za běhu pro váš program. Kromě toho tento článek vás naučí, jak vynutit konkrétní verzi.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.openlocfilehash: 55f04ce81f63753831fca8fa2e44811c44049733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398823"
---
# <a name="select-the-net-core-version-to-use"></a>Vyberte verzi .NET Core, kterou chcete použít.

Tento článek vysvětluje zásady používané nástroji .NET Core, sadou SDK a runtime pro výběr verzí. Tyto zásady poskytují rovnováhu mezi spuštěných aplikací pomocí zadaných verzí a umožňuje snadnou inovaci vývojářských i koncových počítačů. Tyto zásady provádějí následující akce:

- Snadné a efektivní nasazení rozhraní .NET Core, včetně aktualizací zabezpečení a spolehlivosti.
- Používejte nejnovější nástroje a příkazy nezávisle na cílovém běhu.

Dojde k výběru verze:

- Při spuštění příkazu sady SDK používá sada [SDK nejnovější nainstalovanou verzi](#the-sdk-uses-the-latest-installed-version).
- Při vytváření sestavení, [zástupné názvy rozhraní cíl definovat rozhraní API čas sestavení](#target-framework-monikers-define-build-time-apis).
- Při spuštění aplikace .NET Core se [aplikace závislé na cílovém rámci posunou vpřed](#framework-dependent-apps-roll-forward).
- Při publikování samostatné [aplikace, samostatná nasazení zahrnují vybraný runtime](#self-contained-deployments-include-the-selected-runtime).

Zbytek tohoto dokumentu zkoumá tyto čtyři scénáře.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Sada SDK používá nejnovější nainstalovanou verzi

Příkazy sady SDK zahrnují `dotnet new` a `dotnet run`. Rozhraní příkazového příkazu .NET Core cli `dotnet` musí zvolit verzi sady SDK pro každý příkaz. Ve výchozím nastavení používá nejnovější sadu SDK nainstalovanou v počítači, a to i v případě, že:

- Projekt cílí na starší verzi zaběhu .NET Core.
- Nejnovější verze sady .NET Core SDK je verze preview.

Můžete využít nejnovější funkce sady SDK a vylepšení při cílení na starší verze prostředí .NET Core runtime. Můžete cílit více runtime verze .NET Core na různé projekty, pomocí stejných nástrojů sady SDK pro všechny projekty.

Ve výjimečných případech může být nutné použít starší verzi sady SDK. Tuto verzi zadáte v [souboru *global.json* ](../tools/global-json.md). Zásada "Použít nejnovější" znamená, že *global.json* používáte pouze k určení verze sady .NET Core SDK dříve než nejnovější nainstalovaná verze.

*global.json* lze umístit kdekoli v hierarchii souborů. Rozhraní se křidýlku vyhledá v adresáři projektu směrem nahoru pro první *global.json,* který najde. Můžete určit, které projekty dané *global.json* platí podle jeho místo v systému souborů. Rozhraní .NET CLI vyhledá soubor *global.json,* který iterativně naviguje cestu směrem nahoru od aktuálního pracovního adresáře. První nalezený soubor *global.json* určuje použitou verzi. Pokud je nainstalována tato verze sady SDK, použije se tato verze. Pokud sada SDK zadaná v *souboru global.json* není nalezena, rozhraní .NET CLI použije odpovídající [pravidla](../tools/global-json.md#matching-rules) k výběru kompatibilní sady SDK nebo selže, pokud není nalezena žádná.

Následující příklad ukazuje syntaxi *global.json:*

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

Proces výběru verze sady SDK je:

1. `dotnet`Vyhledá soubor *global.json,* který iterativně naviguje cestu směrem nahoru od aktuálního pracovního adresáře.
1. `dotnet`Používá sadu SDK zadanou v prvním souboru *global.json* nalezen.
1. `dotnet`Používá nejnovější nainstalovanou sadu SDK, pokud není nalezen žádný *global.json.*

Další informace o výběru verze sady SDK naleznete v části [Odpovídající pravidla](../tools/global-json.md#matching-rules) v článku *global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Cílové rámcové monikers definovat rozhraní API času sestavení

Sestavení projektu proti rozhraní API definované v **zástupný název cílového rámce** (TFM). V souboru projektu zadáte [cílovou architekturu.](../../standard/frameworks.md) Nastavte `TargetFramework` prvek v souboru projektu, jak je znázorněno v následujícím příkladu:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Můžete vytvořit projekt proti více TFM. Nastavení více cílových rozhraní je běžnější pro knihovny, ale lze provést také s aplikacemi. Zadáte `TargetFrameworks` vlastnost (množné `TargetFramework`číslo). Cílové rámce jsou středník-oddělené, jak je znázorněno v následujícím příkladu:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Daná sada SDK podporuje pevnou sadu rámců, která je omezena na cílovou architekturu runtime, se kterým je dodávána. Například sada .NET Core 2.0 SDK obsahuje runtime .NET Core 2.0, což je implementace cílového `netcoreapp2.0` rozhraní. Sada .NET Core 2.0 `netcoreapp1.0`SDK podporuje , `netcoreapp1.1`a , a `netcoreapp2.0` ale ne `netcoreapp2.1` (nebo vyšší). Nainstalujete .NET Core 2.1 SDK sestavit pro `netcoreapp2.1`.

.NET Standardní cílové architektury jsou také omezeny na cílové rozhraní runtime SDK dodává s. Sada .NET Core 2.0 SDK `netstandard2.0`je omezena na .

## <a name="framework-dependent-apps-roll-forward"></a>Aplikace závislé na rámci se posunou vpřed

Při spuštění aplikace ze [`dotnet run`](../tools/dotnet-run.md)zdroje s , z [`dotnet myapp.dll`](../tools/dotnet.md#description)nasazení závislé na [**rozhraní**](../deploying/index.md#publish-runtime-dependent) s , nebo z [**spustitelného souboru závislého na rozhraní**](../deploying/index.md#publish-runtime-dependent) s `myapp.exe`, `dotnet` spustitelný soubor je **hostitelem** pro aplikaci.

Hostitel zvolí nejnovější verzi opravy nainstalovanou v počítači. Pokud jste například `netcoreapp2.0` zadali v `2.0.4` souboru projektu a je nejnovější `2.0.4` nainstalovaný soubor .NET, použije se tento čas.

Pokud není `2.0.*` nalezena žádná přijatelná verze, použije se nová `2.*` verze. Pokud jste například `netcoreapp2.0` zadali a je nainstalována pouze `2.1.0` aplikace, aplikace se spustí pomocí `2.1.0` runtime. Toto chování se označuje jako "dílčí verze roll-forward." Nižší verze také nebudou považovány za. Pokud není nainstalován žádný přijatelný běh, aplikace nebude spuštěna.

Několik příkladů použití ukazují chování, pokud cíl 2.0:

- 2.0 je specifikováno. 2.0.5 je nejvyšší nainstalovaná verze opravy. 2.0.5.
- 2.0 je specifikováno. Nejsou nainstalovány verze 2.0.*. 1.1.1 je nejvyšší doba běhu nainstalována. Zobrazí se chybová zpráva.
- 2.0 je specifikováno. Nejsou nainstalovány verze 2.0.*. 2.2.2 je nejvyšší nainstalovaná verze runtime 2.x. 2.2.2.
- 2.0 je specifikováno. Nejsou nainstalovány žádné verze 2.x. 3.0.0. Zobrazí se chybová zpráva.

Dílčí verze roll-forward má jeden vedlejší účinek, který může ovlivnit koncové uživatele. Představte si následující scénář:

1. Aplikace určuje, že je vyžadována verze 2.0.
2. Při spuštění verze 2.0.* není nainstalována, ale 2.2.2 je. Bude použita verze 2.2.2.
3. Později uživatel nainstaluje 2.0.5 a spustí aplikaci znovu, 2.0.5 bude nyní použit.

Je možné, že 2.0.5 a 2.2.2 se chovají odlišně, zejména pro scénáře, jako je serializace binárních dat.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Samostatná nasazení zahrnují vybranou dobu běhu

Aplikaci můžete publikovat jako [**samostatnou distribuci**](../deploying/index.md#publish-self-contained). Tento přístup sdružuje runtime .NET Core a knihovny s vaší aplikací. Samostatná nasazení nemají závislost na prostředí chodu runtime. Výběr verze runtime probíhá v době publikování, nikoli v době spuštění.

Proces publikování vybere nejnovější verzi opravy dané řady runtime. Například `dotnet publish` vybere .NET Core 2.0.4, pokud se jedná o nejnovější verzi opravy v rodině runtime .NET Core 2.0. Cílový rámec (včetně nejnovějších nainstalovaných oprav zabezpečení) je zabalen s aplikací.

Je to chyba, pokud není splněna minimální verze zadaná pro aplikaci. `dotnet publish`váže na nejnovější verzi opravy runtime (v rámci dané řady hlavních verzí major.minor). `dotnet publish`nepodporuje sémantiku .forward-forward `dotnet run`sémantiku . Další informace o opravách a samostatných nasazeních naleznete v článku o [výběru oprav za běhu](../deploying/runtime-patch-selection.md) při nasazování aplikací .NET Core.

Samostatná nasazení mohou vyžadovat konkrétní verzi opravy. Můžete přepsat minimální runtime patch verze (na vyšší nebo nižší verze) v souboru projektu, jak je znázorněno v následujícím příkladu:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

Prvek `RuntimeFrameworkVersion` přepíše zásady výchozí verze. Pro samostatná nasazení `RuntimeFrameworkVersion` určuje verze *přesného* rozhraní runtime framework. Pro aplikace závislé na `RuntimeFrameworkVersion` rámci určuje *minimální* požadovanou verzi rozhraní runtime framework.
