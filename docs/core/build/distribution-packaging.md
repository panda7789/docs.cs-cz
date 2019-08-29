---
title: Vytváření distribučních balíčků .NET Core
description: Naučte se, jak zabalit, pojmenovat a verze .NET Core pro distribuci.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: 5d23147c8a38fbeea9e88c0a18e1f220e854fec1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105419"
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

- (1) **dotnet** hostitel (označovaný také jako "muxer") má dvě odlišné role: aktivujte modul runtime pro spuštění aplikace a aktivujte sadu SDK k odeslání příkazů do ní. Hostitel je nativní spustitelný soubor (`dotnet.exe`).

I když existuje jeden hostitel, většina ostatních komponent je v adresářích se správou verzí (2, 3, 5, 6). To znamená, že v systému může být k dispozici více verzí, protože jsou nainstalovány vedle sebe.

- (2) **hostitel/FXR/\<FXR verze >** obsahuje logiku překladu rozhraní, kterou používá hostitel. Hostitel používá nejnovější hostfxr, která je nainstalována. Hostfxr zodpovídá za výběr vhodného modulu runtime při spouštění aplikace .NET Core. Například aplikace sestavená pro .NET Core 2.0.0 používá modul runtime 2.0.5, pokud je k dispozici. Podobně hostfxr vybere vhodnou sadu SDK během vývoje.

- (3) **sada SDK\</SDK verze >** sadě SDK (také označované jako "nástroje") je sada spravovaných nástrojů, které se používají k psaní a vytváření knihoven a aplikací .NET Core. Sada SDK obsahuje rozhraní příkazového řádku (CLI) .NET Core, kompilátory spravovaných jazyků, MSBuild a přidružené úlohy a cíle sestavení, NuGet, nové šablony projektů a tak dále.

- (4) **sada SDK/NuGetFallbackFolder** obsahuje mezipaměť balíčků NuGet, které sada SDK používá během operace obnovení, například při spuštění `dotnet restore` nebo. `dotnet build /t:Restore`

**Sdílená** složka obsahuje rozhraní. Sdílené rozhraní poskytuje sadu knihoven v centrálním umístění, aby mohly být používány různými aplikacemi.

- (5) **Shared/Microsoft. NETCore. app\</runtime verze >** toto rozhraní obsahuje modul runtime .NET Core a podporuje spravované knihovny.

- (6, 7) **Shared/Microsoft. AspNetCore. { Aplikace, všechny verze}\</aspnetcore >** obsahuje ASP.NET Core knihovny. Knihovny `Microsoft.AspNetCore.App` jsou vyvíjeny a podporovány v rámci projektu .NET Core. Knihovny jsou v `Microsoft.AspNetCore.All` oblasti nadmnožinou, které také obsahují knihovny třetích stran.

- (8) **License. txt, ThirdPartyNotices. txt** jsou licence .NET Core a licence knihoven třetích stran používané v .NET Core v uvedeném pořadí.

- (9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` je ruční stránka dotnet. `dotnet`je symlink na hostitele dotnet (1). Tyto soubory jsou nainstalovány ve dobře známých umístěních pro integraci systému.

## <a name="recommended-packages"></a>Doporučené balíčky

Verze .NET Core je založena na číslech verzí komponenty `[major].[minor]` modulu runtime.
Verze SDK používá stejný `[major].[minor]` a má nezávisle `[patch]` , která kombinuje sémantiku funkcí a oprav pro sadu SDK.
Příklad: Sada SDK verze 2.2.302 je druhá verze verze sady SDK pro třetí funkce, která podporuje modul runtime 2,2. Další informace o tom, jak funguje Správa verzí, najdete v tématu [Přehled verzí .NET Core](../versions/index.md).

Některé balíčky obsahují část čísla verze v názvu. To vám umožní nainstalovat určitou verzi.
Zbytek verze není zahrnutý v názvu verze. Správce balíčků operačního systému tak může aktualizovat balíčky (například automaticky instalovat opravy zabezpečení). Podporovaní správci balíčků jsou specifická pro Linux.

Doporučené balíčky jsou uvedeny v následující tabulce:

| Name                                    | Příklad                | Případ použití: Nainstalovat...           | Obsahuje           | Závislosti                                   | Version            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Nejnovější sada SDK pro hlavní modul runtime    |                    | dotnet-sdk-[major].[latestminor]               | \<> verze sady SDK     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Nejnovější sada SDK pro konkrétní modul runtime |                    | dotnet-SDK-[hlavní]. [vedlejší]. [nejnovější sada SDK Feat] XX | \<> verze sady SDK     |
| dotnet-SDK-[hlavní]. [vedlejší]. [SDK Feat] XX | dotnet-sdk-2.1.3xx     | Konkrétní verze funkce sady SDK    | (3),(4)            | aspnetcore-runtime-[hlavní]. moll             | \<> verze sady SDK     |
| aspnetcore-runtime-[hlavní]. moll      | aspnetcore-runtime-2,1 | Konkrétní modul runtime ASP.NET Core   | (6), [(7)]          | dotnet – modul runtime-[hlavní]. moll                 | \<verze modulu runtime > |
| dotnet – modul runtime-[hlavní]. moll          | dotnet – modul runtime-2,1     | Konkrétní modul runtime                | čl                | Hostitel – FXR:\<verze modulu runtime > +                   | \<verze modulu runtime > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _závislosti_                    | odst                | Hostitel:\<verze modulu runtime > +                       | \<verze modulu runtime > |
| dotnet – hostitel                             | dotnet – hostitel            | _závislosti_                    | (1), (8), (9), (10)   |                                                | \<verze modulu runtime > |

Většina distribucí vyžaduje, aby všechny artefakty byly sestaveny ze zdroje. To má nějaký dopad na balíčky:

- Knihovny třetích stran v části `shared/Microsoft.AspNetCore.All` nejde snadno sestavit ze zdroje. Takže se složka z `aspnetcore-runtime` balíčku vynechá.

- Je naplněno pomocí binárních artefaktů z `nuget.org`. `NuGetFallbackFolder` Měla by zůstat prázdná.

Více `dotnet-sdk` balíčků může poskytovat stejné soubory `NuGetFallbackFolder`pro. Aby se zabránilo problémům se správcem balíčků, měly by být tyto soubory stejné (kontrolní součet, datum změny atd.).

### <a name="preview-versions"></a>Verze Preview

Údržba balíčků se můžou rozhodnout poskytnout verzi Preview sdílených rozhraní a sady SDK. Verze Preview můžou být k `dotnet-sdk-[major].[minor].[sdk feat]xx`dispozici pomocí balíčků, `dotnet-runtime-[major].[minor]` `aspnetcore-runtime-[major].[minor]`nebo. U verzí Preview musí být hlavní verze balíčku nastavená na hodnotu nula. Tímto způsobem je finální verze nainstalovaná jako upgrade balíčku.

### <a name="patch-packages"></a>Balíčky oprav

Vzhledem k tomu, že verze opravy balíčku může způsobit zásadní změnu, může být vhodné, aby balíček pro správu zavedl _balíčky oprav_. Tyto balíčky umožňují nainstalovat specifickou verzi opravy, která se automaticky neupgraduje. Balíčky oprav používejte jenom ve výjimečných případech, protože se neupgradují pomocí oprav (zabezpečení).

Následující tabulka uvádí doporučené balíčky a **balíčky oprav**:

| Name                                           | Příklad                  | Obsahuje         | Závislosti                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | dotnet-SDK-[hlavní]. [poslední verze sady SDK]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | dotnet-SDK-[hlavní]. [vedlejší]. [nejnovější sada SDK Feat] XX            |
| dotnet-SDK-[hlavní]. [vedlejší]. [SDK Feat] XX        | dotnet-sdk-2.1.3xx       |                  | dotnet-SDK-[hlavní]. [vedlejší]. [nejnovější Oprava sady SDK]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore-runtime-[hlavní]. [vedlejší]. [oprava modulu runtime sady SDK]    |
| aspnetcore-runtime-[hlavní]. moll             | aspnetcore-runtime-2,1   |                  | aspnetcore-runtime-[hlavní]. [vedlejší]. [nejnovější oprava modulu runtime] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore – modul runtime – 2.1.0 | (6), [(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet – modul runtime-[hlavní]. moll                 | dotnet – modul runtime-2,1       |                  | dotnet – modul runtime-[hlavní]. [vedlejší]. [nejnovější oprava modulu runtime]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | čl              | Hostitel – FXR:\<verze modulu runtime > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | odst              | Hostitel:\<verze modulu runtime > +                                  |
| dotnet – hostitel                                    | dotnet – hostitel              | (1), (8), (9), (10) |                                                           |

Alternativou k použití opravných balíčků je připnutí balíčků ke konkrétní verzi pomocí Správce balíčků. Aby nedošlo k ovlivnění jiných aplikací nebo uživatelů, takové aplikace mohou být sestaveny a nasazeny v kontejneru.

## <a name="building-packages"></a>Vytváření balíčků

Úložiště [dotnet/source-Build](https://github.com/dotnet/source-build) poskytuje pokyny pro sestavení zdrojové tarballu .NET Core SDK a všech jeho součástí. Výstup úložiště zdrojového sestavení odpovídá rozložení popsanému v první části tohoto článku.
