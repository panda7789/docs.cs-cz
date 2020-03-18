---
title: Architektura nástrojů příkazového řádku .NET Core
description: Přečtěte si o vrstvách nástrojů .NET Core a o tom, co se změnilo v posledních verzích.
ms.date: 03/06/2017
ms.openlocfilehash: fde1a0acb6af9dd65aa3466b4ea37473b2eab6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092912"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Přehled změn v nástrojích .NET Core na vysoké úrovni

Tento dokument popisuje změny spojené s přechodem z *project.json* na MSBuild a *csproj* projektový systém s informacemi o změnách vrstvení nástrojů .NET Core a implementaci příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU. K těmto změnám došlo s vydáním .NET Core SDK 1.0 a Visual Studio 2017 dne 7. [announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)

## <a name="moving-away-from-projectjson"></a>Odklon od project.json

Největší změnou v nástrojích pro .NET Core je jistě [přechod od project.json k csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) jako projektový systém. Nejnovější verze nástrojů příkazového řádku nepodporují soubory *project.json.* To znamená, že jej nelze použít k vytváření, spouštění nebo publikování aplikací a knihoven založených na projektu. Chcete-li použít tuto verzi nástrojů, migrujte existující projekty nebo začněte nové.

V rámci tohoto pohybu byl vlastní modul sestavení, který byl vyvinut k sestavení projektů project.json, nahrazen zralým a plně schopným modulem sestavení s názvem [MSBuild](https://github.com/Microsoft/msbuild). MSBuild je známý modul v komunitě .NET. To bylo klíčové technologie od prvního vydání platformy. Protože je potřeba vytvářet aplikace .NET Core, msbuild byl portován na .NET Core a lze použít na libovolné platformě, která .NET Core běží na. Jedním z hlavních slibů .NET Core je zásobník vývoje napříč platformami a ujistili jsme se, že tento krok tento slib neporuší.

> [!TIP]
> Pokud jste na MSBuild a chcete se dozvědět více o tom, můžete začít čtením [msbuild koncepty](/visualstudio/msbuild/msbuild-concepts) článku.

## <a name="the-tooling-layers"></a>Vrstvy nástrojů

Se změnou v sestavení motoru a odklon od stávajícího systému projektu, některé otázky přirozeně následovat. Mění některá z těchto změn celkové "vrstvení" ekosystému nástrojů .NET Core? Existují nové bity a součásti?

Začněme s rychlým osvěžením při vrstvách náhledu 2, jak je znázorněno na následujícím obrázku:

![Náhled 2 nástrojů architektury na vysoké úrovni](media/cli-msbuild-architecture/p2-arch.png)

Vrstvení nástrojů v náhledu 2 je jednoduché. V dolní části je základem rozhraní PŘÍKAZOVÉHO ŘÁDKU jádra .NET. Všechny ostatní nástroje vyšší úrovně, jako je například Visual Studio nebo Visual Studio Code, závisí a spoléhají na cli k vytváření projektů, obnovení závislostí a tak dále. Například pokud Visual Studio chtěl provést operaci obnovení, `dotnet restore` by volání do příkazu ([viz poznámka](#dotnet-restore-note)) v příkazu cli.

S přechodem na nový systém projektu se předchozí diagram změní:

![Architektura na vysoké úrovni .NET Core SDK 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Hlavní rozdíl je v tom, že CLI již není základní vrstvou; tuto roli nyní plní "sdílená součást sady SDK". Tato sdílená součást sady SDK je sada cílů a přidružených úloh, které jsou zodpovědné za kompilaci kódu, jeho publikování, balení balíčků NuGet a tak dále. Sada .NET Core SDK je open source a je k dispozici na GitHubu v [úložišti sady SDK](https://github.com/dotnet/sdk).

> [!NOTE]
> "Cíl" je termín MSBuild, který označuje pojmenovanou operaci, kterou může MSBuild vyvolat. Obvykle je spojen s jedním nebo více úloh, které provádějí některé logiky, které cíl má dělat. MSBuild podporuje mnoho hotových `Copy` cílů, jako je například nebo `Execute`; umožňuje také uživatelům psát vlastní úkoly pomocí spravovaného kódu a definovat cíle pro provádění těchto úkolů. Další informace naleznete v tématu [MSBuild tasks](/visualstudio/msbuild/msbuild-tasks).

Všechny sady nástrojů nyní spotřebovávají sdílenou komponentu Sady SDK a její cíle, včetně cli. Například Visual Studio 2019 nevolá `dotnet restore` do příkazu ([viz poznámka](#dotnet-restore-note)) k obnovení závislostí pro projekty .NET Core. Místo toho používá cíl "Obnovit" přímo. Vzhledem k tomu, že se jedná o cíle MSBuild, můžete také použít nezpracovaná MSBuild k jejich spuštění pomocí příkazu [dotnet msbuild.](dotnet-msbuild.md)

### <a name="cli-commands"></a>Příkazy příkazového příkazu

Sdílená součást sady SDK znamená, že většina existujících příkazů příkazového příkazu příkazového příkazu byla znovu implementována jako úlohy a cíle msbuild. Co to znamená pro příkazy příkazu příkazu příkazu příkazu příkazu a vaše použití sady nástrojů?

Z hlediska využití nezmění způsob použití cli. Rozhraní příkazového příkazu má stále základní příkazy, které existovaly ve verzi .NET Core 1.0 Preview 2:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Tyto příkazy stále dělají to, co očekáváte, že budou dělat (nové projekty, sestavení, publikování, balení a tak dále). Můžete se seznámit s jejich chováním `dotnet <command> --help`na obrazovce nápovědy příkazu (pomocí) nebo v dokumentaci na tomto webu.

Z hlediska provádění příkazy rozhraní příkazu převzít jejich parametry a vytvořit volání "raw" MSBuild, který nastaví potřebné vlastnosti a spustí požadovaný cíl. Chcete-li to lépe ilustrovat, zvažte následující příkaz:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

Tento příkaz publikuje aplikaci do `pub` složky pomocí konfigurace "Release". Interně tento příkaz získá přeloženy do následující ho vyvolání MSBuild:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Významné výjimky z tohoto `new` `run` pravidla jsou příkazy a. Nebyly implementovány jako cíle MSBuild.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
