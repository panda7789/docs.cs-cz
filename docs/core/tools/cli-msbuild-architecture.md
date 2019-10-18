---
title: Architektura nástrojů příkazového řádku .NET Core
description: Přečtěte si o vrstvách nástrojů .NET Core a o tom, co se změnilo v posledních verzích.
ms.date: 03/06/2017
ms.openlocfilehash: 05183a9edc26615e00d6383043fd10d8bec06f2b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521308"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Podrobný přehled změn v nástrojích .NET Core

Tento dokument popisuje změny spojené s přesunutím z *Project. JSON* na MSBuild a systém projektu *csproj* s informacemi o změnách vrstev nástrojů .NET Core a implementaci příkazů CLI. K těmto změnám došlo s vydáním .NET Core SDK 1,0 a sady Visual Studio 2017 7. března 2017 (viz [oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), ale byly původně implementovány s vydáním .NET Core SDK Preview 3.

## <a name="moving-away-from-projectjson"></a>Přesun mimo Project. JSON

Největší změna v nástrojích pro .NET Core je určitě [z Project. JSON přejít na csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) jako systém projektu. Nejnovější verze nástrojů příkazového řádku nepodporují soubory *Project. JSON* . To znamená, že se nedá použít k sestavení, spuštění nebo publikování aplikací a knihoven založených na Project. JSON. Aby bylo možné používat tuto verzi nástrojů, budete muset migrovat existující projekty nebo začít novými. 

V rámci tohoto přesunu byl vlastní modul sestavení vyvinutý pro sestavení projektů Project. JSON nahrazen vyspělým a plně schopným sestavovacím modulem s názvem [MSBuild](https://github.com/Microsoft/msbuild). MSBuild je známý modul v komunitě .NET, protože se od první verze platformy stal klíčovou technologií. Samozřejmě, protože potřebuje sestavovat aplikace .NET Core, MSBuild byl předaný do .NET Core a lze ho použít na libovolné platformě, na které běží .NET Core. Jednou z hlavních příslibů .NET Core je sada pro vývoj pro různé platformy a zajistili jsme, že tento přesun neruší tento příslib.

> [!NOTE]
> Pokud s nástrojem MSBuild začínáte a chcete získat další informace o této službě, můžete začít načtením článku [koncepty nástroje MSBuild](/visualstudio/msbuild/msbuild-concepts) . 

## <a name="the-tooling-layers"></a>Vrstvy nástrojů

Když se přesunete z existujícího projektového systému i s přepínači pro sestavování strojového stroje, otázka, kterou přirozeně následuje, provede některé z těchto změn. celkové "vrstvení" celého ekosystému nástrojů .NET Core? Existují nové bity a součásti?

Pojďme začít s rychlým aktualizačním rozhraním ve verzi Preview 2, jak je znázorněno na následujícím obrázku:

![Preview 2 – architektura vysoké úrovně nástrojů](media/cli-msbuild-architecture/p2-arch.png)

Vrstvení nástrojů je poměrně jednoduché. V dolní části máme jako základ nástroje příkazového řádku .NET Core. Všechny ostatní nástroje vyšší úrovně, jako je například Visual Studio nebo Visual Studio Code, závisí a spoléhají na rozhraní příkazového řádku pro sestavování projektů, obnovování závislostí a tak dále. To znamená, že například pokud aplikace Visual Studio chtěla provést operaci obnovení, měla by zavolat do `dotnet restore` ([Viz poznámku](#dotnet-restore-note)) v rozhraní příkazového řádku. 

Při přesunu na nový systém projektu se změní předchozí diagram: 

![Architektura vysoké úrovně .NET Core SDK 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Hlavním rozdílem je, že rozhraní příkazového řádku již není základní vrstva; Tato role je nyní vyplněna "sdílenou komponentou sady SDK". Tato sdílená součást sady SDK je sada cílů a přidružených úloh, které jsou zodpovědné za kompilování kódu, publikování a balení balíčků NuGet atd. Samotný SDK je open source a je k dispozici na GitHubu v [úložišti SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> "Target" je výraz MSBuild, který označuje pojmenovanou operaci, kterou může nástroj MSBuild vyvolat. Obvykle je spojen s jednou nebo více úlohami, které spouštějí určitou logiku, kterou by měl cíl provádět. Nástroj MSBuild podporuje mnoho předem připravených cílů, jako `Copy` nebo `Execute`; umožňuje také uživatelům psát vlastní úkoly pomocí spravovaného kódu a definovat cíle pro provádění těchto úkolů. Další informace najdete v tématu [úlohy nástroje MSBuild](/visualstudio/msbuild/msbuild-tasks). 

Všechny sady nástrojů teď využívají sdílenou součást sady SDK a její cíle, včetně rozhraní příkazového řádku. Například další verze sady Visual Studio nebude volat příkaz `dotnet restore` ([Viz poznámku](#dotnet-restore-note)) pro obnovení závislostí pro projekty .NET Core, bude používat cíl "obnovit" přímo. Vzhledem k tomu, že se jedná o cíle nástroje MSBuild, můžete pomocí příkazu [dotnet MSBuild](dotnet-msbuild.md) spustit také nezpracovaný nástroj MSBuild. 

### <a name="cli-commands"></a>Příkazy rozhraní příkazového řádku
Sdílená součást sady SDK znamená, že většina existujících příkazů rozhraní příkazového řádku byla znovu implementována jako úlohy a cíle nástroje MSBuild. Co to znamená pro příkazy rozhraní příkazového řádku a vaše využití sady nástrojů? 

Z perspektivy využití se nezmění způsob, jakým rozhraní příkazového řádku používáte. Rozhraní příkazového řádku má stále základní příkazy, které existují ve verzi Preview 2:

- `new`
- `restore`
- `run` 
- `build`
- `publish`
- `test`
- `pack` 

Tyto příkazy pořád dělají, co očekáváte (nový projekt, sestavte ho, publikujte ho, probalíte a tak dále). Většina možností se nezměnila a stále existují a můžete se obrátit na obrazovky s nápovědami (pomocí `dotnet <command> --help`) nebo v dokumentaci k tomuto webu, abyste se seznámili se změnami. 

Z perspektivy provádění budou příkazy rozhraní příkazového řádku přebírat své parametry a sestavit volání "raw" MSBuild, které nastaví požadované vlastnosti a spustí požadovaný cíl. K lepší ilustraci byste měli vzít v úvahu následující příkaz: 

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```
    
Tento příkaz publikuje aplikaci do složky `pub` s použitím konfigurace Release. Interně se tento příkaz převede do následujícího vyvolání MSBuild: 

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Významnou výjimkou z tohoto pravidla jsou příkazy `new` a `run`, protože nebyly implementovány jako cíle nástroje MSBuild.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
