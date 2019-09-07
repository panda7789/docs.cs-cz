---
title: Vytváření distribučních balíčků .NET Core
description: Naučte se, jak zabalit, pojmenovat a verze .NET Core pro distribuci.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394163"
---
# <a name="net-core-distribution-packaging"></a>Vytváření distribučních balíčků .NET Core

Rozhraní .NET Core bude k dispozici na více a více platformách. je vhodné se naučit, jak balíček, název a verzi. Tímto způsobem můžou údržba balíčků pomáhat zajistit konzistentní prostředí bez ohledu na to, kde se uživatelé spouštějí .NET. Tento článek je užitečný pro uživatele, kteří jsou:

- Probíhá pokus o sestavení .NET Core ze zdroje.
- Chcete provádět změny .NET Core CLI, které by mohly mít vliv na výsledné rozložení nebo vytvořené balíčky.

## <a name="disk-layout"></a>Rozložení disku

Při instalaci nástroje .NET Core se skládá z několika součástí, které jsou v systému souborů uvedeny následovně:

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** hostitel (označovaný také jako "muxer") má dvě odlišné role: aktivujte modul runtime pro spuštění aplikace a aktivujte sadu SDK k odeslání příkazů do ní. Hostitel je nativní spustitelný soubor (`dotnet.exe`).

I když existuje jeden hostitel, většina ostatních komponent je v adresářích se správou verzí (2, 3, 5, 6). To znamená, že v systému může být k dispozici více verzí, protože jsou nainstalovány vedle sebe.

- (2) **hostitel/FXR/\<FXR verze >** obsahuje logiku překladu rozhraní, kterou používá hostitel. Hostitel používá nejnovější hostfxr, která je nainstalována. Hostfxr zodpovídá za výběr vhodného modulu runtime při spouštění aplikace .NET Core. Například aplikace sestavená pro .NET Core 2.0.0 používá modul runtime 2.0.5, pokud je k dispozici. Podobně hostfxr vybere vhodnou sadu SDK během vývoje.

- (3) **sada SDK\</SDK verze >** sadě SDK (také označované jako "nástroje") je sada spravovaných nástrojů, které se používají k psaní a vytváření knihoven a aplikací .NET Core. Sada SDK obsahuje rozhraní příkazového řádku (CLI) .NET Core, kompilátory spravovaných jazyků, MSBuild a přidružené úlohy a cíle sestavení, NuGet, nové šablony projektů a tak dále.

- (4) **sada SDK/NuGetFallbackFolder** obsahuje mezipaměť balíčků NuGet, které sada SDK používá během operace obnovení, například při spuštění `dotnet restore` nebo. `dotnet build /t:Restore` Tato složka se používá pouze před rozhraním .NET Core 3,0. Nemůže být sestaven ze zdroje, protože obsahuje předem sestavené binární prostředky z `nuget.org`.

**Sdílená** složka obsahuje rozhraní. Sdílené rozhraní poskytuje sadu knihoven v centrálním umístění, aby mohly být používány různými aplikacemi.

- (5) **Shared/Microsoft. NETCore. app\</runtime verze >** toto rozhraní obsahuje modul runtime .NET Core a podporuje spravované knihovny.

- (6) **Shared/Microsoft. AspNetCore. { Aplikace, všechny verze}\</aspnetcore >** obsahuje ASP.NET Core knihovny. Knihovny `Microsoft.AspNetCore.App` jsou vyvíjeny a podporovány v rámci projektu .NET Core. Knihovny jsou v `Microsoft.AspNetCore.All` oblasti nadmnožinou, které také obsahují knihovny třetích stran.

- (7) **Shared/Microsoft. Desktop. app\</Desktop verze aplikace >** obsahuje knihovny desktopů Windows. Tato součást není zahrnutá na platformách jiných než Windows.

- (8) **License. txt, ThirdPartyNotices. txt** jsou licence .NET Core a licence knihoven třetích stran používané v .NET Core v uvedeném pořadí.

- (9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` je ruční stránka dotnet. `dotnet`je symlink na hostitele dotnet (1). Tyto soubory jsou nainstalovány ve dobře známých umístěních pro integraci systému.

- (11.12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref** popisují rozhraní API `x.y` verze .NET Core a ASP.NET Core v uvedeném pořadí. Tyto sady jsou používány při kompilování pro tyto cílové verze.

- (13) **Microsoft. NETCore. app. Host.\< > identifikátorů RID** obsahuje nativní binární soubor `rid`pro platformu. Tento binární soubor je šablonou při kompilování aplikace .NET Core do nativního binárního souboru pro danou platformu.

- (14) **Microsoft. WindowsDesktop. app. ref** popisuje rozhraní API `x.y` aplikací klasické pracovní plochy systému Windows. Tyto soubory se používají při kompilování pro daný cíl. Tento příkaz není k dispozici na platformách jiných než Windows.

- (15) **NETStandard. Library. ref** popisuje rozhraní NETStandard `x.y` API. Tyto soubory se používají při kompilování pro daný cíl.

- (16) **/etc/dotnet/install_location** je soubor, který obsahuje úplnou cestu ke složce, která obsahuje `dotnet` binární soubor hostitele. Cesta může být ukončena novým řádkem. Není nutné přidávat tento soubor, pokud je `/usr/share/dotnet`kořenový adresář.

- (17) **šablony** obsahují šablony používané sadou SDK. Například `dotnet new` vyhledá šablony projektu zde.

## <a name="recommended-packages"></a>Doporučené balíčky

Verze .NET Core je založena na číslech verzí komponenty `[major].[minor]` modulu runtime.
Verze SDK používá stejný `[major].[minor]` a má nezávisle `[patch]` , která kombinuje sémantiku funkcí a oprav pro sadu SDK.
Příklad: Sada SDK verze 2.2.302 je druhá verze verze sady SDK pro třetí funkce, která podporuje modul runtime 2,2. Další informace o tom, jak funguje Správa verzí, najdete v tématu [Přehled verzí .NET Core](../versions/index.md).

Některé balíčky obsahují část čísla verze v názvu. To vám umožní nainstalovat určitou verzi.
Zbytek verze není zahrnutý v názvu verze. Správce balíčků operačního systému tak může aktualizovat balíčky (například automaticky instalovat opravy zabezpečení). Podporovaní správci balíčků jsou specifická pro Linux.

Následující seznam obsahuje doporučené balíčky:

- `dotnet-sdk-[major].[minor]`– Nainstaluje nejnovější sadu SDK pro konkrétní modul runtime.
  - **Verze:** \<verze modulu runtime >
  - **Příklad:** dotnet-sdk-2,1
  - **Zobrazí** (3),(4)
  - **Závislosti:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`– Nainstaluje konkrétní modul runtime ASP.NET Core.
  - **Verze:** \<> verze modulu runtime aspnetcore
  - **Příklad:** aspnetcore-runtime-2,1
  - **Zobrazí** 6
  - **Závislosti:** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _(Volitelné)_ – nainstaluje závislosti pro spouštění aplikací, které jsou součástí sebe.
  - **Verze:** \<verze modulu runtime >
  - **Příklad:** dotnet-runtime-deps-2,1
  - **Závislosti:** _distribuce specifické závislosti_

- `dotnet-runtime-[major].[minor]`– Nainstaluje konkrétní modul runtime.
  - **Verze:** \<verze modulu runtime >
  - **Příklad:** dotnet-runtime-2,1
  - **Zobrazí** čl
  - **Závislosti:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr`-Dependency
  - **Verze:** \<verze modulu runtime >
  - **Příklad:** dotnet-hostfxr
  - **Zobrazí** odst
  - **Závislosti:** `host:<runtime version>+`

- `dotnet-host`-Dependency
  - **Verze:** \<verze modulu runtime >
  - **Příklad:** dotnet-Host
  - **Zobrazí** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]`-Dependency
  - **Verze:** \<verze modulu runtime >
  - **Zobrazí** 13,5

- `dotnet-targeting-pack-[major].[minor]`– Umožňuje zaměřit se na nenejnovější modul runtime.
  - **Verze:** \<verze modulu runtime >
  - **Zobrazí** 12,5

- `aspnetcore-targeting-pack-[major].[minor]`– Umožňuje zaměřit se na nenejnovější modul runtime.
  - **Verze:** \<> verze modulu runtime aspnetcore
  - **Zobrazí** odst

- `netstandard-targeting-pack-[major].[minor]`– Povoluje cílení na verzi netstandard
  - **Verze:** \<> verze sady SDK
  - **Zobrazí** 15

- `dotnet-templates-[major].[minor]`
  - **Verze:** \<> verze sady SDK
  - **Zobrazí** 15

Vyžaduje porozumění _distribuce specifickým závislostem._ `dotnet-runtime-deps-[major].[minor]` Vzhledem k tomu, že systém sestavení distribuce může být schopný tuto hodnotu automaticky odvodit, balíček je volitelný. v takovém případě se tyto závislosti `dotnet-runtime-[major].[minor]` přidávají přímo do balíčku.

Když je obsah balíčku ve složce se správou verzí, název `[major].[minor]` balíčku se shoduje s názvem složky se správou verzí. Pro všechny balíčky s výjimkou `netstandard-targeting-pack-[major].[minor]`, to se také shoduje s verzí .NET Core.

Závislosti mezi balíčky by měly používat požadavek _rovnající se nebo vyšší_ verze. Například `dotnet-sdk-2.2:2.2.401` vyžaduje `aspnetcore-runtime-2.2 >= 2.2.6`. Díky tomu může uživatel upgradovat instalaci prostřednictvím kořenového balíčku (např. `dnf update dotnet-sdk-2.2`).

Většina distribucí vyžaduje, aby všechny artefakty byly sestaveny ze zdroje. To má nějaký dopad na balíčky:

- Knihovny třetích stran v části `shared/Microsoft.AspNetCore.All` nejde snadno sestavit ze zdroje. Takže se složka z `aspnetcore-runtime` balíčku vynechá.

- Je naplněno pomocí binárních artefaktů z `nuget.org`. `NuGetFallbackFolder` Měla by zůstat prázdná.

Více `dotnet-sdk` balíčků může poskytovat stejné soubory `NuGetFallbackFolder`pro. Aby se zabránilo problémům se správcem balíčků, měly by být tyto soubory stejné (kontrolní součet, datum změny atd.).

## <a name="building-packages"></a>Vytváření balíčků

Úložiště [dotnet/source-Build](https://github.com/dotnet/source-build) poskytuje pokyny pro sestavení zdrojové tarballu .NET Core SDK a všech jeho součástí. Výstup úložiště zdrojového sestavení odpovídá rozložení popsanému v první části tohoto článku.
