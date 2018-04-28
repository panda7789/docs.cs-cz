---
title: Balení distribuční .NET core
description: Informace k balíčkování, název a verze .NET Core pro distribuci.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 63ff542dbde30f8ff72a2d257a16a18b2a9e71b8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-distribution-packaging"></a>Balení distribuční .NET core

Jakmile .NET Core k dispozici na více platforem, je užitečné informace k balíčkování, název a verze ho. Tímto způsobem údržby balíček programu může pomoci zajistit konzistentní prostředí bez ohledu na to, kde uživatelé zvolit spuštění rozhraní .NET.

## <a name="disk-layout"></a>Rozložení disku

Při instalaci .NET Core se skládá z několika komponent, které jsou layed se následujícím způsobem v systému souborů:

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
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** dvě odlišné role má hostitel (také označované jako "multiplexor"): aktivovat runtime spuštění aplikace a aktivujte sady SDK k odesílání příkazů do ní. Hostitel je nativní spustitelný soubor (`dotnet.exe`).

Zatímco je jeden hostitel, většina ostatní součásti jsou v verzí adresáře (2,3,5,6). Tyto prostředky několik verzí může být v systému, protože jsou nainstalované-souběžného.

- (2) **hostitele nebo fxr/\<fxr verze >** obsahuje logiku framework řešení používá hostitel. Hostitel používá nejnovější hostfxr, který je nainstalován. Hostfxr zodpovídá za výběrem příslušné runtime při spouštění aplikace .NET Core. Například aplikace vytvořené pro .NET Core 2.0.0 použije 2.0.5 runtime, jakmile bude k dispozici. Podobně hostfxr vybere odpovídající SDK během vývoje.

- (3) **sdk /\<verze sady sdk >** sadu spravovaných nástrojů, které lze použít k zápisu a vytvářet knihovny .NET Core a aplikace je sada SDK (také označované jako "nástrojů"). Sada SDK zahrnuje rozhraní příkazového řádku, Roslyn kompilátoru, MSBuild a úlohy přidružené sestavení a cíle, NuGet, nové šablony projektu atd.

- (4) **sdk/NuGetFallbackFolder** obsahuje mezipaměť balíčky NuGet použité SDK během `dotnet restore` krok.

**Sdílené** složka obsahuje rozhraní. Sdílený framework poskytuje sadu knihoven do centrálního umístění, takže je můžete použít různé aplikace.

- (5) **shared/Microsoft.NETCore.App/\<verzi modulu runtime >** toto rozhraní obsahuje na .NET Core runtime a podpůrné spravované knihovny.

- (6,7) **shared/Microsoft.AspNetCore. { Aplikace, všechny} /\<aspnetcore verze >** obsahuje ASP.NET Core libraries. Knihovny pod `Microsoft.AspNetCore.App` vyvinutých, podporované jako součást projektu .NET Core. Knihovny pod `Microsoft.AspNetCore.All` je nadmnožinou, který také obsahuje 3. stran knihovny.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** jsou licence .NET Core a licencí knihovny třetích stran používané v .NET Core.

- (9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` je stránka man dotnet. `dotnet` je symlink k dotnet host(1). Tyto soubory jsou nainstalovány v dobře známé umístění pro integraci systému.

## <a name="recommended-packages"></a>Doporučené balíčky

Správa verzí .NET core je založen na součásti modulu runtime `[major].[minor]` čísla verzí.
Verze sady SDK používá stejnou `[major].[minor]` a má nezávislou `[patch]` který kombinuje sémantiku funkce a opravy pro sadu SDK.
Příklad: je sada SDK verze 2.2.302 2. Oprava verze 3. vydání funkce sady SDK, která podporuje 2.2 modulu runtime.

Některé balíčky v názvu zahrnují součástí číslo verze. To umožňuje koncového uživatele k instalaci na konkrétní verzi.
Zbývající část verze není součástí název verze. To umožňuje balíček operačního systému manager aktualizoval balíčky (například zabezpečení instalace automaticky opravuje).

Následující tabulky uvádí doporučené balíčky.

| Název                                    | Příklad                | Případ použití: nainstalujte...           | Obsahuje           | Závislosti                                   | Version            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Nejnovější sady sdk pro hlavní modulu runtime    |                    | dotnet-sdk-[major].[latestminor]               | \<verze sady SDK >     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Nejnovější sady sdk pro konkrétní modul runtime |                    | DotNet - sdk-[hlavní]. [vedlejší]. [nejnovější sady sdk feat] xx | \<verze sady SDK >     |
| DotNet - sdk-[hlavní]. [vedlejší]. xx [sdk feat] | dotnet-sdk-2.1.3xx     | Funkce verze konkrétní sady sdk    | (3),(4)            | aspnetcore - runtime-[hlavní]. [menší]             | \<verze sady SDK >     |
| aspnetcore - runtime-[hlavní]. [menší]      | aspnetcore. modul runtime 2.1 | Konkrétní ASP.NET Core runtime   | (6),[(7)]          | DotNet - runtime-[hlavní]. [menší]                 | \<verze runtime > |
| DotNet - runtime-[hlavní]. [menší]          | DotNet. modul runtime 2.1     | Konkrétní modul runtime                | (5)                | hostitele fxr:\<verzi modulu runtime > +                   | \<verze runtime > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _závislosti_                    | (2)                | hostitele:\<verzi modulu runtime > +                       | \<verze runtime > |
| hostitele DotNet.                             | hostitele DotNet.            | _závislosti_                    | (1),(8),(9),(10)   |                                                | \<verze runtime > |

Většina distribuce vyžadují všechny artefakty má být sestaven ze zdroje. To má dopad na některé u balíčků:

- 3. stran knihovny pod `shared/Microsoft.AspNetCore.All` nelze snadno vytvořené ze zdroje. Tak je vynechaný této složky `aspnetcore-runtime` balíčku.

- `NuGetFallbackFolder` Vyplní pomocí binární artefakty z `nuget.org`. By měla zůstat prázdná.

Více `dotnet-sdk` balíčky může poskytovat stejné soubory, které pro `NuGetFallbackFolder`. Abyste předešli problémům s Správce balíčků, tyto soubory musí být identické (kontrolního součtu, datum změny,...).

#### <a name="preview-versions"></a>Verze Preview

Balíček pracovníků programu rozhodnout zajistit verze preview sdílený framework a sady SDK. Verze Preview, může být zadán pomocí `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]` balíčky. Pro verze preview musí být hlavní verze balíčku nastavit na nulu. Tímto způsobem finální verzi bude nainstalována jako upgrade balíčku.

#### <a name="patch-packages"></a>Oprava balíčků

Vzhledem k tomu, že oprava verzi balíčky může způsobit narušující změně, funkce maintainer balíček chtít zadat _oprava balíčky_. Tyto balíčky umožňuje nainstalovat verzi konkrétní opravy, které není automaticky aktualizovány. Balíčky opravy by měl použít pouze ve výjimečných případech jako nebudou opravy upgradovaný (zabezpečení).

V následující tabulce jsou uvedeny doporučené balíčky a **oprava balíčky**.

| Název                                           | Příklad                  | Obsahuje         | Závislosti                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[hlavní]. [menší nejnovější sdk]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | DotNet - sdk-[hlavní]. [vedlejší]. [nejnovější sady sdk feat] xx            |
| DotNet - sdk-[hlavní]. [vedlejší]. xx [sdk feat]        | dotnet-sdk-2.1.3xx       |                  | DotNet - sdk-[hlavní]. [vedlejší]. [nejnovější opravy sdk]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore - runtime-[hlavní]. [vedlejší]. [opravy runtime sdk]    |
| aspnetcore - runtime-[hlavní]. [menší]             | aspnetcore. modul runtime 2.1   |                  | aspnetcore - runtime-[hlavní]. [vedlejší]. [nejnovější opravy runtime] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore. modul runtime 2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| DotNet - runtime-[hlavní]. [menší]                 | DotNet. modul runtime 2.1       |                  | DotNet - runtime-[hlavní]. [vedlejší]. [nejnovější opravy runtime]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | hostitele fxr:\<verzi modulu runtime > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | hostitele:\<verzi modulu runtime > +                                  |
| hostitele DotNet.                                    | hostitele DotNet.              | (1),(8),(9),(10) |                                                           |

Alternativu k použití balíčky opravy je _Připnutí_ balíčky na konkrétní verzi pomocí Správce balíčků. Pokud chcete vyhnout, které mají vliv na ostatní aplikace nebo uživatele, můžete tyto aplikace vytvořené a nasazené v kontejneru.

## <a name="building-packages"></a>Vytváření balíčků

https://github.com/dotnet/source-build Úložiště obsahuje pokyny, jak vytvořit zdroj tarball .NET Core SDK a všech jeho součástí. Výstup sestavení zdroje úložiště odpovídá rozložení popsané v první části tohoto článku.