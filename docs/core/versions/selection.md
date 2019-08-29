---
title: Vyberte verzi rozhraní .NET Core, která se má použít.
description: Přečtěte si, jak rozhraní .NET Core automaticky najde a zvolí verze modulu runtime pro váš program. V tomto článku se naučíte, jak vynutit konkrétní verzi.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.custom: seodec18
ms.openlocfilehash: db42ba4916aad739bd2c9d8b547f16022fce44bd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104938"
---
# <a name="select-the-net-core-version-to-use"></a>Vyberte verzi .NET Core, kterou chcete použít.

Tento článek vysvětluje zásady používané nástroji .NET Core, sadou SDK a modulem runtime pro výběr verzí. Tyto zásady poskytují rovnováhu mezi běžícími aplikacemi, které používají zadané verze, a umožňují snadno upgradovat počítače vývojářů i koncových uživatelů. Tyto zásady provádějí následující akce:

- Snadné a efektivní nasazení rozhraní .NET Core, včetně aktualizací zabezpečení a spolehlivosti.
- Použijte nejnovější nástroje a příkazy nezávisle na cílovém modulu runtime.

Výběr verze nastane:

- Při spuštění příkazu sady SDK [používá sada SDK nejnovější nainstalovanou verzi](#the-sdk-uses-the-latest-installed-version).
- Když sestavíte sestavení, [monikery cílového rozhraní definují rozhraní API doby sestavení](#target-framework-monikers-define-build-time-apis).
- Když spustíte aplikaci .NET Core, předají se [závislé aplikace cílové architektury na více systémů](#framework-dependent-apps-roll-forward).
- Když publikujete samostatnou aplikaci, [samostatná nasazení zahrnují vybraný modul runtime](#self-contained-deployments-include-the-selected-runtime).

Zbytek tohoto dokumentu prověřuje tyto čtyři scénáře.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Sada SDK používá nejnovější nainstalovanou verzi.

Příkazy sady SDK `dotnet new` zahrnují `dotnet run`a. .NET Core CLI musí zvolit verzi sady SDK pro každý `dotnet` příkaz. Ve výchozím nastavení používá nejnovější sadu SDK nainstalovanou na počítači, a to i v případě, že:

- Projekt cílí na starší verzi modulu runtime .NET Core.
- Nejnovější verze .NET Core SDK je verze Preview.

Můžete využít výhod nejnovějších funkcí sady SDK a vylepšení při zaměření na dřívější verze modulu runtime .NET Core. Pomocí stejných nástrojů sady SDK pro všechny projekty můžete cílit na více verzí modulu runtime .NET Core v různých projektech.

Ve výjimečných případech možná budete muset použít starší verzi sady SDK. Tuto verzi zadáte v [ *globálním souboru. JSON* ](../tools/global-json.md). Zásada použít nejnovější znamená, že k určení .NET Core SDK verze starší než nejnovější nainstalovaná verze použijete jenom *Global. JSON* .

soubor *Global. JSON* lze umístit kdekoli v hierarchii souborů. Rozhraní příkazového řádku vyhledá v prvním *globálním formátu JSON* směrem nahoru z adresáře projektu. Můžete určit, na které projekty se má daný soubor *Global. JSON* vztahovat na místo v systému souborů. Rozhraní .NET CLI vyhledává soubor *Global. JSON* iterativním procházením cesty směrem nahoru od aktuálního pracovního adresáře. První nalezený soubor *Global. JSON* určuje použitou verzi. Pokud je tato verze nainstalovaná, použije se tato verze. Pokud se sada SDK zadaná v *globálním formátu JSON* nenajde, rozhraní .NET CLI se vrátí na nejnovější NAINSTALOVANOU sadu SDK. Funkce přeposlání je stejná jako výchozí chování, pokud se nenajde soubor *Global. JSON* .

Následující příklad ukazuje syntaxi *Global. JSON* :

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

Postup pro výběr verze sady SDK:

1. `dotnet`vyhledává soubor *Global. JSON* iterativním zpětným procházením cesty směrem nahoru od aktuálního pracovního adresáře.
1. `dotnet`používá sadu SDK zadanou v prvním *globálním. JSON* , kterou jsme našli.
1. `dotnet`používá nejnovější nainstalovanou sadu SDK, pokud nebyl nalezen žádný *globální. JSON* .

Další informace o výběru verze sady SDK najdete v části [pravidla pro porovnání](../tools/global-json.md#matching-rules) článku v tématu *Global. JSON*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Monikery cílového rozhraní definují rozhraní API pro čas sestavení

Projekt sestavíte proti rozhraním API definovaným v **monikeru cílového rozhraní** (TFM). V souboru projektu zadáte [cílovou architekturu](../../standard/frameworks.md) . `TargetFramework` Nastavte prvek v souboru projektu, jak je znázorněno v následujícím příkladu:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Projekt můžete sestavit na více TFM. Nastavení více cílových rozhraní je pro knihovny běžnější, ale lze je provádět i s aplikacemi. Zadejte `TargetFrameworks` vlastnost ( `TargetFramework`plural). Cílové rozhraní jsou odděleny středníkem, jak je znázorněno v následujícím příkladu:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Daná sada SDK podporuje pevnou sadu rozhraní omezené do cílové architektury modulu runtime, se kterým se dodává. Například sada .NET Core 2,0 SDK obsahuje modul runtime .NET Core 2,0, což je implementace `netcoreapp2.0` cílové architektury. Sada SDK .NET Core 2,0 podporuje `netcoreapp1.0`, `netcoreapp1.1`, a `netcoreapp2.0` nikoli `netcoreapp2.1` (nebo vyšší). Nainstalujete sadu SDK .NET Core 2,1 k sestavení pro `netcoreapp2.1`.

.NET Standard cílové architektury jsou také omezené do cílové architektury modulu runtime, se kterým sada SDK dodává. Sada .NET Core 2,0 SDK je omezené na `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Aplikace závislé na architektuře – předávají změny

Spouštíte-li aplikaci ze zdroje s [`dotnet run`](../tools/dotnet-run.md)nástrojem, z [**nasazení závislého**](../deploying/index.md#framework-dependent-deployments-fdd) na rozhraní [`dotnet myapp.dll`](../tools/dotnet.md#description)s nástrojem nebo `myapp.exe`z [**spustitelného souboru závislého**](../deploying/index.md#framework-dependent-executables-fde) na rozhraní `dotnet` , je spustitelný soubor **hostitelem** pro aplikaci.

Hostitel zvolí nejnovější verzi opravy nainstalovanou v počítači. Například pokud jste zadali `netcoreapp2.0` v souboru projektu a `2.0.4` je nainstalován nejnovější modul runtime `2.0.4` .NET, je použit modul runtime.

Pokud se nenajde `2.0.*` žádná přijatelná verze, použije se `2.*` nová verze. Pokud jste například zadali `netcoreapp2.0` a pouze `2.1.0` nainstalovali, aplikace se spustí pomocí `2.1.0` modulu runtime. Toto chování se označuje jako "dílčí verze – přeposílání". Nižší verze se taky nepovažují za. Pokud není nainstalován žádný přijatelný modul runtime, aplikace se nespustí.

Několik příkladů použití ukazuje chování, pokud cílíte na 2,0:

- je zadáno 2,0. 2.0.5 je nejvyšší nainstalovaná verze opravy. 2.0.5 se používá.
- je zadáno 2,0. Nejsou nainstalovány žádné 2,0. * verzí. 1.1.1 je nejvyšší instalovaný modul runtime. Zobrazí se chybová zpráva.
- je zadáno 2,0. Nejsou nainstalovány žádné 2,0. * verzí. 2.2.2 je nainstalovaná nejvyšší verze 2. x modulu runtime. 2.2.2 se používá.
- je zadáno 2,0. Nejsou nainstalovány žádné 2. verze x. 3.0.0 je nainstalován. Zobrazí se chybová zpráva.

Dílčí verze s přesměrováním obsahuje jeden vedlejší dopad, který může mít vliv na koncové uživatele. Vezměte v úvahu následující scénář:

1. Aplikace určuje, že se vyžaduje 2,0.
2. Pokud je spuštěná, verze 2,0. * není nainstalovaná, ale je 2.2.2. Bude použita verze 2.2.2.
3. Později uživatel nainstaluje 2.0.5 a znovu spustí aplikaci, 2.0.5 se teď použije.

Je možné, že se 2.0.5 a 2.2.2 chovají jinak, zejména u scénářů, jako je serializace binárních dat.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Samostatně zahrnutá nasazení zahrnují vybraný modul runtime.

Aplikaci můžete publikovat jako [**samostatně uzavřenou distribuci**](../deploying/index.md#self-contained-deployments-scd). Tento přístup naváže modul runtime a knihovny .NET Core s vaší aplikací. Samostatně obsažená nasazení nemají závislost na běhových prostředích. K výběru verze modulu runtime dojde v době publikování, nikoli v době běhu.

Proces publikování vybere nejnovější verzi opravy dané rodiny modulu runtime. Například `dotnet publish` vybere .NET Core 2.0.4, pokud se jedná o nejnovější verzi opravy v rodině runtime .NET Core 2,0. Cílová architektura (včetně nejnovějších nainstalovaných oprav zabezpečení) je zabalená spolu s aplikací.

Jedná se o chybu, pokud není splněna minimální verze určená pro aplikaci. `dotnet publish`váže se k nejnovější verzi opravy modulu runtime (v rámci dané hlavní skupiny. podverze). `dotnet publish`nepodporují sémantiku `dotnet run`předávaného při přeposílání. Další informace o opravách a samostatných nasazeních najdete v článku o [výběru oprav pro modul runtime](../deploying/runtime-patch-selection.md) v tématu nasazení aplikací .NET Core.

Samostatně obsažená nasazení mohou vyžadovat konkrétní verzi opravy. Můžete přepsat minimální verzi opravy modulu runtime (na vyšší nebo nižší verze) v souboru projektu, jak je znázorněno v následujícím příkladu:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` Element přepíše výchozí zásadu verze. Pro samostatně obsažená nasazení `RuntimeFrameworkVersion` určuje aplikace *přesnou* verzi rozhraní Runtime. U aplikací závislých na `RuntimeFrameworkVersion` rozhraní určuje *minimální* požadovanou verzi rozhraní Runtime.
