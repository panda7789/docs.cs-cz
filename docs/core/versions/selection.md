---
title: Vyberte verzi rozhraní .NET Core, která se má použít.
description: Přečtěte si, jak rozhraní .NET Core automaticky najde a zvolí verze modulu runtime pro váš program. V tomto článku se naučíte, jak vynutit konkrétní verzi.
author: adegeo
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: faaa638905bb3c8e9cd4c09af83979d90698df3d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803115"
---
# <a name="select-the-net-core-version-to-use"></a>Vyberte verzi .NET Core, kterou chcete použít.

Tento článek vysvětluje zásady používané nástroji .NET Core, sadou SDK a modulem runtime pro výběr verzí. Tyto zásady poskytují rovnováhu mezi běžícími aplikacemi, které používají zadané verze, a umožňují snadno upgradovat počítače vývojářů i koncových uživatelů. Tyto zásady provádějí následující akce:

- Snadné a efektivní nasazení rozhraní .NET Core, včetně aktualizací zabezpečení a spolehlivosti.
- Použijte nejnovější nástroje a příkazy nezávisle na cílovém modulu runtime.

Výběr verze nastane:

- Při spuštění příkazu sady SDK [používá sada SDK nejnovější nainstalovanou verzi](#the-sdk-uses-the-latest-installed-version).
- Když sestavíte sestavení, [monikery cílového rozhraní definují rozhraní API doby sestavení](#target-framework-monikers-define-build-time-apis).
- Když spustíte aplikaci .NET Core, [předají se závislé aplikace cílové architektury na více systémů](#framework-dependent-apps-roll-forward).
- Když publikujete samostatnou aplikaci, [samostatná nasazení zahrnují vybraný modul runtime](#self-contained-deployments-include-the-selected-runtime).

Zbytek tohoto dokumentu prověřuje tyto čtyři scénáře.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Sada SDK používá nejnovější nainstalovanou verzi.

Příkazy sady SDK zahrnují `dotnet new` a `dotnet run` . .NET Core CLI musí zvolit verzi sady SDK pro každý `dotnet` příkaz. Ve výchozím nastavení používá nejnovější sadu SDK nainstalovanou na počítači, a to i v případě, že:

- Projekt cílí na starší verzi modulu runtime .NET Core.
- Nejnovější verze .NET Core SDK je verze Preview.

Můžete využít výhod nejnovějších funkcí sady SDK a vylepšení při zaměření na dřívější verze modulu runtime .NET Core. Pomocí stejných nástrojů sady SDK pro všechny projekty můžete cílit na více verzí modulu runtime .NET Core v různých projektech.

Ve výjimečných případech možná budete muset použít starší verzi sady SDK. Tuto verzi zadáte v [ *global.js* souboru](../tools/global-json.md). Zásada použít nejnovější znamená, že k určení .NET Core SDK verze starší než nejnovější nainstalovaná verze používáte jenom *global.js* .

*global.jsna* může být umístěn kdekoli v hierarchii souborů. Rozhraní příkazového řádku vyhledá u prvního *global.js* směrem nahoru z adresáře projektu. Můžete řídit, které projekty, *na kterýchglobal.jsna* platit, na základě jejího umístění v systému souborů. Rozhraní .NET CLI vyhledává *global.jsv* souboru iterativním procházením cesty směrem nahoru od aktuálního pracovního adresáře. Prvníglobal.jsnalezené *v* souboru určuje použitou verzi. Pokud je nainstalována tato verze sady SDK, je použita tato verze. Pokud sada SDK zadaná v *global.js* není nalezena, rozhraní .NET CLI používá pro výběr kompatibilní sady SDK [pravidla pro porovnání](../tools/global-json.md#matching-rules) , nebo se nepovede, pokud se nenajde žádná.

Následující příklad ukazuje *global.js* syntaxe:

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

Postup pro výběr verze sady SDK:

1. `dotnet`vyhledává *global.jsv* souboru iterativním zpětným procházením cesty směrem nahoru od aktuálního pracovního adresáře.
1. `dotnet`používá sadu SDK určenou v prvním *global.js* , kterou najdete.
1. `dotnet`Pokud se nenajde žádná *global.js* , použije se nejnovější nainstalovaná sada SDK.

Další informace o výběru verze sady SDK najdete v části [pravidla pro hledání](../tools/global-json.md#matching-rules) v článku o *global.js*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Monikery cílového rozhraní definují rozhraní API pro čas sestavení

Projekt sestavíte proti rozhraním API definovaným v **monikeru cílového rozhraní** (TFM). V souboru projektu zadáte [cílovou architekturu](../../standard/frameworks.md) . Nastavte `TargetFramework` prvek v souboru projektu, jak je znázorněno v následujícím příkladu:

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Projekt můžete sestavit na více TFM. Nastavení více cílových rozhraní je pro knihovny běžnější, ale lze je provádět i s aplikacemi. Zadejte `TargetFrameworks` vlastnost (plural `TargetFramework` ). Cílové rozhraní jsou odděleny středníkem, jak je znázorněno v následujícím příkladu:

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

Daná sada SDK podporuje pevnou sadu rozhraní omezené do cílové architektury modulu runtime, se kterým se dodává. Například sada .NET Core 3,0 SDK obsahuje modul runtime .NET Core 3,0, což je implementace `netcoreapp3.0` cílové architektury. Sada SDK .NET Core 3,0 podporuje `netcoreapp2.1` , `netcoreapp2.2` , `netcoreapp3.0` , ale ne `netcoreapp3.1` (nebo vyšší). Nainstalujete sadu SDK .NET Core 3,1 k sestavení pro `netcoreapp3.1` .

.NET Standard cílové architektury jsou také omezené do cílové architektury modulu runtime, se kterým sada SDK dodává. Sada .NET Core 3,1 SDK je omezené na `netstandard2.1` . Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).

## <a name="framework-dependent-apps-roll-forward"></a>Aplikace závislé na architektuře – předávají změny

Spouštíte-li aplikaci ze zdroje s nástrojem, [`dotnet run`](../tools/dotnet-run.md) z [**nasazení závislého**](../deploying/index.md#publish-runtime-dependent) na rozhraní s nástrojem [`dotnet myapp.dll`](../tools/dotnet.md#description) nebo z [**spustitelného souboru závislého na rozhraní**](../deploying/index.md#publish-runtime-dependent) `myapp.exe` , `dotnet` je spustitelný soubor **hostitelem** aplikace.

Hostitel zvolí nejnovější verzi opravy nainstalovanou v počítači. Například pokud jste zadali `netcoreapp3.0` v souboru projektu a `3.0.2` je nainstalován nejnovější modul runtime .NET, `3.0.2` je použit modul runtime.

Pokud `3.0.*` se nenajde žádná přijatelná verze, `3.*` použije se nová verze. Pokud jste například zadali `netcoreapp3.0` a pouze `3.1.0` nainstalovali, aplikace se spustí pomocí `3.1.0` modulu runtime. Toto chování se označuje jako "dílčí verze – přeposílání". Nižší verze se taky nepovažují za. Pokud není nainstalován žádný přijatelný modul runtime, aplikace se nespustí.

Několik příkladů použití ukazuje chování, pokud cílíte na 3,0:

- je určena ✔️ 3,0. 3.0.3 je nejvyšší nainstalovaná verze opravy. 3.0.3 se používá.
- ❌je zadáno 3,0. Nejsou nainstalovány žádné 3,0. * verzí. 2.1.1 je nejvyšší instalovaný modul runtime. Zobrazí se chybová zpráva.
- je určena ✔️ 3,0. Nejsou nainstalovány žádné 3,0. * verzí. 3.1.0 je nejvyšší nainstalovaná verze modulu runtime. 3.1.0 se používá.
- ❌je zadáno 2,0. Nejsou nainstalovány žádné 2. verze x. 3.0.0 je nejvyšší instalovaný modul runtime. Zobrazí se chybová zpráva.

Dílčí verze s přesměrováním obsahuje jeden vedlejší dopad, který může mít vliv na koncové uživatele. Představte si následující scénář:

1. Aplikace určuje, že se vyžaduje 3,0.
2. Pokud je spuštěná, verze 3,0. * není nainstalovaná, ale 3.1.0 je. Bude použita verze 3.1.0.
3. Později uživatel nainstaluje 3.0.3 a znovu spustí aplikaci, 3.0.3 se teď použije.

Je možné, že 3.0.3 a 3.1.0 se chovají jinak, zejména u scénářů, jako je serializace binárních dat.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Samostatně zahrnutá nasazení zahrnují vybraný modul runtime.

Aplikaci můžete publikovat jako [**samostatně uzavřenou distribuci**](../deploying/index.md#publish-self-contained). Tento přístup naváže modul runtime a knihovny .NET Core s vaší aplikací. Samostatně obsažená nasazení nemají závislost na běhových prostředích. K výběru verze modulu runtime dojde v době publikování, nikoli v době běhu.

Proces publikování vybere nejnovější verzi opravy dané rodiny modulu runtime. Například `dotnet publish` vybere .NET Core 3.0.3, pokud se jedná o nejnovější verzi opravy v rodině runtime .NET Core 3,0. Cílová architektura (včetně nejnovějších nainstalovaných oprav zabezpečení) je zabalená spolu s aplikací.

Jedná se o chybu, pokud není splněna minimální verze určená pro aplikaci. `dotnet publish`váže se k nejnovější verzi opravy modulu runtime (v rámci dané hlavní skupiny. podverze). `dotnet publish`nepodporují sémantiku předávaného při přeposílání `dotnet run` . Další informace o opravách a samostatných nasazeních najdete v článku o [výběru oprav pro modul runtime](../deploying/runtime-patch-selection.md) v tématu nasazení aplikací .NET Core.

Samostatně obsažená nasazení mohou vyžadovat konkrétní verzi opravy. Můžete přepsat minimální verzi opravy modulu runtime (na vyšší nebo nižší verze) v souboru projektu, jak je znázorněno v následujícím příkladu:

``` xml
<RuntimeFrameworkVersion>3.0.3</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion`Element přepíše výchozí zásadu verze. Pro samostatně obsažená nasazení `RuntimeFrameworkVersion` určuje aplikace *přesnou* verzi rozhraní Runtime. U aplikací závislých na rozhraní `RuntimeFrameworkVersion` Určuje *minimální* požadovanou verzi rozhraní Runtime.

## <a name="see-also"></a>Viz také:

- [Stáhněte a nainstalujte .NET Core](../install/index.yml).
- [Jak odebrat modul runtime .NET Core a sadu SDK](../install/remove-runtime-sdk-versions.md).
