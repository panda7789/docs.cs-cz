---
title: "Balení distribuční .NET core"
description: "Informace k balíčkování, název a verze .NET Core pro distribuci."
keywords: "Zdroj rozhraní .NET, .NET core, sestavení"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 71b9d722-c5a8-4271-9ce1-d87e7ae2494d
ms.workload: dotnetcore
ms.openlocfilehash: 9f5cd2f7c4fec553dfdfaf1765663b6896b3061d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-distribution-packaging"></a>Balení distribuční .NET core

Jakmile .NET Core k dispozici na více platforem, je užitečné informace k balíčkování, název a verze ho. Tímto způsobem údržby balíček programu může pomoci zajistit konzistentní prostředí bez ohledu na to, kde uživatelé zvolit spuštění rozhraní .NET.

## <a name="net-core-components"></a>Součásti .NET core

.NET core přišla ze tří hlavních částí, které musí být zabalené:

1. **Hostitel** (také označované jako "multiplexor") má dvě odlišné role: aktivovat runtime spuštění aplikace a aktivujte sady SDK k odesílání příkazů do ní. Hostitel je nativní spustitelný soubor (`dotnet.exe`) a jeho podpůrné zásad knihovny (nainstalované v `host/fxr`). Je sestaven z kód [ `dotnet/core-setup` ](https://github.com/dotnet/core-setup/) úložiště. Je obvykle pouze jednoho hostitele na daný počítač, i když se nejedná o explicitní požadavek.
2. **Rozhraní framework** se provádí modulu runtime a podpůrné spravované knihovny. Rozhraní framework může být nainstalovaná jako součást aplikace nebo jako sdílený framework v centrálním umístění, které můžete opakovaně použít více aplikacemi. Může existovat libovolný počet sdílené rozhraní, které jsou nainstalovány na daném počítači. Sdílené rozhraní za provozu v rámci `shared/Microsoft.NETCore.App/<version>`. Hostitel posunete mezi verzemi opravy. Pokud aplikace cílena `Microsoft.NETCore.App` 1.0.0 a pouze 1.0.4 je k dispozici, proti 1.0.4 spuštění aplikace.
3. **Sada SDK** (také označované jako "nástrojů") je sada spravované nástroje, které lze použít k zápisu a vytvářet knihovny .NET Core a aplikace. Sada SDK zahrnuje rozhraní příkazového řádku, MSBuild a úlohy přidružené sestavení a cíle, NuGet, nové šablony projektu atd. Je možné, že více sad SDK na počítači (například k sestavení projektů, které explicitně vyžadují starší verze), ale doporučuje se používat nejnovější vydaná nástroje.

## <a name="recommended-package-names"></a>Názvy doporučené balíčku

Naše doporučení pro názvy balíčku jsou následující pokyny. Funkce maintainer balíček rozhodnout vycházející z podle z různých důvodů, jako jiný tradici, které jste v cílení na konkrétní rozdělení.

### <a name="minimum-package-set"></a>Minimální balíčku sady

* `dotnet-runtime-[major].[minor]`: sdílený framework se zadanou verzí (pouze nejnovější verzi oprav pro danou hlavní + menší kombinaci by měl být k dispozici v Správce balíčků). **závislosti**:`dotnet-host`
* `dotnet-sdk`: nejnovější sadu SDK. **závislosti**: nejnovější `dotnet-sdk-[major].[minor]`.
* `dotnet-sdk-[major].[minor]`: Sada SDK se zadanou verzí. Verze zadaná je nejvyšší verze součástí zahrnuty sdílené rozhraní, tak, aby uživatelé můžete snadno týkají sady SDK sdílený framework. **závislosti**: `dotnet-host`, jeden nebo více `dotnet-runtime-[major].[minor]` (jeden moduly runtime se používá ve samotný kód SDK, jiné jsou zde uživatelům sestavení a spuštění).
* `dotnet-host`: nejnovější hostitele.

#### <a name="preview-versions"></a>Verze Preview

Balíček pracovníků programu rozhodnout pro zahrnují verze preview sdílený framework a sady SDK. Ty nikdy musí být obsažena ve bez uvedené verze `dotnet-sdk` balíček, ale může pomocí další preview připojí k hlavní verze a podverze části názvu vydané jako verzí balíčků. Například může existovat `dotnet-sdk-2.0-preview-final` balíčku.

### <a name="optional-additional-packages"></a>Volitelné další balíčky

Některé údržby programu rozhodnout zajistit další balíčky:

* `dotnet-lts`: nejnovější verzi rozhraní sdílené dlouhodobé podporu (LTS). [LTS a aktuální verze vlaky](~/docs/core/versions/lts-current.md) odpovídají různé cadences, na kterých získá vydané .NET Core. Uživatelé si zvolit, zda přijetí jednu nebo jiných train založené na tom, jak často jsou se aktualizovat. Toto je také vázanou podpora pro úrovně, takže může nebo nemusí mít smysl v závislosti na distro za koncept.

## <a name="disk-layout"></a>Rozložení disku

Při instalaci .NET Core balíčky, podstatné relativní umístění jejich cílové umístění na disku.
`dotnet.exe` Hostitele musí být umístěny vedle `sdk` a `shared` složek, které obsahují verzí obsah `dotnet-sdk` SDK balíčky a `dotnet-runtime` sdílený framework balíčky.

Rozložení disku souborů a adresářů uvnitř balíčky je verzí. To znamená, že aktualizace na nejnovější `dotnet-runtime` nainstaluje novou verzi vedle sebe s předchozími verzemi, snižuje možnost výskytu nekonzistentních porušení existujících aplikací pomocí aktualizace balíčku. Aktualizace balíčku by neměla odebere předchozí verze.

## <a name="update-policies"></a>Aktualizovat zásady

Když `update` je provést, chování každý balíček je následující:

* `dotnet-runtime-[major].[minor]`: nové verze oprava aktualizovat balíček, ale nové menší nebo hlavní verze jsou samostatné balíčky.
* `dotnet-sdk`: `update` vrátí dopředného hlavní, vedlejší a oprava verze.
* `dotnet-sdk-[major].[minor]`: nové verze oprava aktualizovat balíček, ale nové menší nebo hlavní verze jsou samostatné balíčky.
* `dotnet-lts`: `update` vrátí dopředného hlavní, vedlejší a oprava verze.

Toto téma se zobrazí Naše doporučení pro balení .NET Core, ale každý distro je mohou zvolit, jaké verze a nabídnout a kdy. Například distro, že se hodnoty stabilitu více než je aktuální rozhodnout k uvolnění pouze verze, snap s vlakem LTS verze.