---
title: Vytváření distribučních balíčků .NET core
description: Zjistěte, jak zabalit, název a verzi .NET Core pro distribuci.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: be5767351ad1cdac15c73f718f67a0d120cf65b0
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170415"
---
# <a name="net-core-distribution-packaging"></a>Vytváření distribučních balíčků .NET core

Jak bude k dispozici na více platformách .NET Core, je užitečné informace k balíčkování, název a verze ho. Tímto způsobem programu balíčku může pomoct zajistit konzistentní prostředí bez ohledu na to, kde uživatelé zvolit spuštění rozhraní .NET.

## <a name="disk-layout"></a>Rozložení disku

Při instalaci .NET Core se skládá z několika komponent, které jsou layed si, jak je uvedeno v systému souborů:

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

- (1) **dotnet** hostitele (označované také jako "multiplexor") má dvě odlišné role: Aktivace modulu runtime pro spuštění aplikace a aktivovat sadu SDK a odesílat příkazy do něj. Hostitel je nativní spustitelný soubor (`dotnet.exe`).

Během jednoho hostitele se většina jiných komponent jsou v označené verzí adresáře (2,3,5,6). To znamená, že více verzí může být k dispozici v systému, protože jsou nainstalované vedle sebe.

- (2) **hostitele/fxr/\<fxr verze >** obsahuje logiku rozlišení framework používá hostitel. Hostitel používá nejnovější hostfxr, který je nainstalován. Hostfxr zodpovídá za výběr vhodné runtime při spuštění aplikace .NET Core. Například aplikace vytvořené pro .NET Core 2.0.0 použije 2.0.5 modulu runtime, až bude k dispozici. Obdobně hostfxr vybere vhodnou sadu SDK během vývoje.

- (3) **sdk /\<verze sady sdk >** sadu spravovaných nástroje, které lze použít k zápisu a vytvoření aplikací a knihoven .NET Core je sada SDK (označované také jako "nástroje"). Sada SDK zahrnuje rozhraní příkazového řádku, platformě Roslyn kompilátoru, MSBuild a přidružené sestavení úlohy a cíle, NuGet, nové šablony projektu, atd.

- (4) **sdk/NuGetFallbackFolder** obsahuje mezipaměť balíčků NuGet, které používají sadu SDK během `dotnet restore` kroku.

**Sdílené** složka obsahuje rozhraní. Sdílené architektuře poskytuje sadu knihoven v centrálním umístění, může využívat různé aplikace.

- (5) **shared/Microsoft.NETCore.App/\<verze modulu runtime >** toto rozhraní obsahuje modul runtime .NET Core a podpůrné spravované knihovny.

- (6,7) **shared/Microsoft.AspNetCore. { Aplikace, všechny} /\<aspnetcore verze >** obsahuje knihovny ASP.NET Core. Knihovny pod `Microsoft.AspNetCore.App` jsou vyvíjeny a podporované jako součást projektu .NET Core. Knihovny pod `Microsoft.AspNetCore.All` je nadmnožinou, která také obsahuje knihovny 3. stran.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** licence .NET Core a licence použít v .NET Core knihovny třetích stran.

- (9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` je stránka man dotnet. `dotnet` je symlink k dotnet host(1). Tyto soubory jsou nainstalovány v dobře známé umístění pro integraci systému.

## <a name="recommended-packages"></a>Doporučené balíčky

Správa verzí rozhraní .NET core je založen na součásti modulu runtime `[major].[minor]` čísla verzí.
Verze sady SDK se používá stejná `[major].[minor]` a má nezávislou `[patch]` zahrnující sémantiku funkce a opravy pro sadu SDK.
Příklad: Sada SDK verze 2.2.302 je 2. Oprava verzi 3. vydání funkcí sady SDK, která podporuje 2.2 modulu runtime.

Některé balíčky v názvu zahrnují část čísla verze. To umožňuje koncového uživatele k instalaci na konkrétní verzi.
Zbývající část verze není součástí název verze. To umožňuje balíčku, operační systém manager aktualizoval balíčky (například zabezpečení instalace automaticky opravuje).

Následující tabulka ukazuje doporučené balíčky.

| Název                                    | Příklad                | Případ použití: Instalace...           | Obsahuje           | Závislosti                                   | Version            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Nejnovější sadu sdk pro modul runtime hlavní    |                    | dotnet-sdk-[major].[latestminor]               | \<verze sady SDK >     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Nejnovější sadu sdk pro konkrétní prostředí runtime |                    | DotNet - sdk-[hlavníverze]. [podverze]. [nejnovější sdk feat] xx | \<verze sady SDK >     |
| DotNet - sdk-[hlavníverze]. [podverze]. xx [sdk feat] | dotnet-sdk-2.1.3xx     | Konkrétní sada sdk vydávání verzí    | (3),(4)            | aspnetcore - runtime-[hlavníverze]. [podverze]             | \<verze sady SDK >     |
| aspnetcore - runtime-[hlavníverze]. [podverze]      | aspnetcore. modul runtime 2.1 | Zvláštní modul runtime ASP.NET Core   | (6),[(7)]          | DotNet – modul runtime-[hlavníverze]. [podverze]                 | \<verze modulu runtime > |
| DotNet – modul runtime-[hlavníverze]. [podverze]          | DotNet – modul runtime-2.1     | Modulu runtime specifické                | (5)                | Hostitel fxr:\<verze modulu runtime > +                   | \<verze modulu runtime > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _Závislost_                    | (2)                | Hostitel:\<verze modulu runtime > +                       | \<verze modulu runtime > |
| DotNet – hostitele                             | DotNet – hostitele            | _Závislost_                    | (1),(8),(9),(10)   |                                                | \<verze modulu runtime > |

Většině distribucí vyžadují všechny artefakty, které má být sestaven ze zdroje. Tato akce nemá dopad na balíčky:

- 3. stran knihovny pod `shared/Microsoft.AspNetCore.All` nedají snadno sestavit ze zdroje. Aby tato složka je vynecháno z `aspnetcore-runtime` balíčku.

- `NuGetFallbackFolder` Je vyplnit hodnotami pomocí binární artefakty z `nuget.org`. By měla zůstat prázdná.

Více `dotnet-sdk` balíčky může poskytovat stejné soubory, které pro `NuGetFallbackFolder`. Abyste předešli problémům s pomocí Správce balíčků, tyto soubory musejí být identické (kontrolního součtu, datum úpravy,...).

#### <a name="preview-versions"></a>Verze Preview

Balíček programu může rozhodnout k poskytování sdílených framework a sady SDK verze preview. Verze Preview může být poskytnuta pomocí `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]` balíčky. Pro verze preview musí být hlavní verze balíčku nastaví na hodnotu nula. Tímto způsobem finální verze se nainstaluje jako upgrade balíčku.

#### <a name="patch-packages"></a>Oprava balíčky

Verze opravy balíčků může způsobit rozbíjející změny, funkce maintainer balíčku může být vhodné poskytnout _oprava balíčky_. Tyto balíčky umožňuje nainstalovat opravu konkrétní verzi, která se automaticky upgraduje. Balíčky oprava by měla sloužit pouze ve výjimečných případech, nebudou opravy upgradovaný (zabezpečení).

V následující tabulce jsou uvedeny doporučené balíčky a **oprava balíčky**.

| Název                                           | Příklad                  | Obsahuje         | Závislosti                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[hlavníverze]. [menší nejnovější sdk]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | DotNet - sdk-[hlavníverze]. [podverze]. [nejnovější sdk feat] xx            |
| DotNet - sdk-[hlavníverze]. [podverze]. xx [sdk feat]        | dotnet-sdk-2.1.3xx       |                  | DotNet - sdk-[hlavníverze]. [podverze]. [oprava nejnovější sdk]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore - runtime-[hlavníverze]. [podverze]. [oprava sady sdk modulu runtime]    |
| aspnetcore - runtime-[hlavníverze]. [podverze]             | aspnetcore. modul runtime 2.1   |                  | aspnetcore - runtime-[hlavníverze]. [podverze]. [nejnovější opravu runtime] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore. modul runtime 2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| DotNet – modul runtime-[hlavníverze]. [podverze]                 | DotNet – modul runtime-2.1       |                  | DotNet – modul runtime-[hlavníverze]. [podverze]. [nejnovější opravu runtime]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | Hostitel fxr:\<verze modulu runtime > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | Hostitel:\<verze modulu runtime > +                                  |
| DotNet – hostitele                                    | DotNet – hostitele              | (1),(8),(9),(10) |                                                           |

Se o alternativu k použití balíčky opravy _Připnutí_ balíčky na konkrétní verzi pomocí Správce balíčků. Pokud chcete vyhnout, tím ovlivnili ostatní aplikace nebo uživatele, můžete takové aplikace vytvořené a nasazené v kontejneru.

## <a name="building-packages"></a>Vytváření balíčků

[Dotnet/zdroj build](https://github.com/dotnet/source-build) úložiště obsahuje pokyny, jak vytvořit zdroj tarballu .NET Core SDK a všech jeho součástí. Výstup sestavení zdrojového úložiště odpovídá rozložení je popsáno v první části tohoto článku.
