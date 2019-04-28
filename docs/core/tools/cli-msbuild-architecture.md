---
title: Architektura nástroje příkazového řádku .NET core
description: Další informace o .NET Core, nástroje vrstvy a co se změnilo v nejnovější verze.
ms.date: 03/06/2017
ms.openlocfilehash: e9226a314932eb73c6474c0fd17c77c87683e6db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665503"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Podrobný přehled změn v nástrojích pro .NET Core

Tento dokument popisuje změny spojené s přesunem z *project.json* nástroji MSBuild a *csproj* projektu systému s informacemi o změnách u rozvrstvení nástrojů .NET Core a provádění příkazů rozhraní příkazového řádku. Tyto změny došlo k .NET Core SDK 1.0 a Visual Studio 2017 verze 7. března 2017 (viz [oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), ale byly původně implementované ve verzi rozhraní .NET Core SDK ve verzi Preview 3.

## <a name="moving-away-from-projectjson"></a>Přesun směrem od project.json
Největší změnou v nástroje pro .NET Core je určitě [přesunout mimo project.json na csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) jako systém projektu. Nejnovější verze nástroje příkazového řádku nepodporují *project.json* soubory. To znamená, že nelze použít k vytvoření, spuštění nebo publikovat project.json na základě aplikací a knihoven. Pokud chcete používat tuto verzi nástrojů, je potřeba migrovat existující projekty nebo spuštění nové značky. 

Jako součást tento přesun, modul vlastní sestavení, který byl vyvinut vytvářet projekty project.json byl nahrazen sestavení až po zralé a plně podporuje modul volá [MSBuild](https://github.com/Microsoft/msbuild). Nástroj MSBuild je dobře známé modul v komunitě .NET, protože jejím klíčových technologií od první verze platformy. Samozřejmě protože je nutné k vytváření aplikací .NET Core, nástroj MSBuild byla přenést až po .NET Core a lze použít na libovolné platformě, na kterém běží .NET Core na. Jeden z hlavních příslibů .NET Core je, že zásobníku vývoj pro různé platformy a jste zkontrolovali jsme, že tento přesun nedojde k poškození tento příslib.

> [!NOTE]
> Pokud teprve začínáte MSBuild a chcete další informace o tom, můžete začít čtením [koncepty nástroje MSBuild](/visualstudio/msbuild/msbuild-concepts) článku. 

## <a name="the-tooling-layers"></a>Nástroje vrstvy
S přechodem na od existující systém projektu i k vytváření aplikací modul přepínače je dotaz, který následuje přirozeně, tyto změny Změna celkové "rozvrstvení" celý ekosystém nástrojů .NET Core? Existují nové bity a komponenty?

Začněme s si můžete rychle znovu projít vrstvení ve verzi Preview 2, jak je znázorněno na následujícím obrázku:

![Základní architektura služby nástroje ve verzi Preview 2](media/cli-msbuild-architecture/p2-arch.png)

Vrstvení nástroje je poměrně jednoduché. V dolní části máme jako základ nástrojů příkazového řádku .NET Core. Všechny nástroje, které vyšší úrovně, jako jsou Visual Studio nebo Visual Studio Code, závislé a Spolehněte se na rozhraní příkazového řádku k sestavení projektů, obnovte závislosti a tak dále. To znamená, že například pokud aplikace Visual Studio k provedení operace obnovení, zavolali jsme do `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) v rozhraní příkazového řádku. 

S přechodem na nový systém projektů se změní na předchozím obrázku: 

![Základní architektura služby sady SDK .NET core 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Hlavní rozdíl je, že rozhraní příkazového řádku základní vrstvě už není; Tato role je nyní vyplněny "sdílené komponenty sady SDK". Tato sdílená komponenta SDK je sada cílů a přidružených úkolů, které jsou zodpovědné za kompilace kódu, jeho publikování, balení balíčky NuGet atd. Samotné sady SDK je open source a je k dispozici na Githubu na [úložišti SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> "Cíl" je MSBuild termín, který určuje operaci s názvem, který může vyvolat MSBuild. To je obvykle párována s jednu nebo více úloh, které jsou spouštěny některé logiku, která cíl by měl provést. Nástroj MSBuild podporuje mnoho předdefinovaných cílů, jako `Copy` nebo `Execute`; také umožňuje psát vlastní úlohy pomocí spravovaného kódu a definování cílů ke spuštění těchto úloh. Další informace najdete v tématu [úlohy nástroje MSBuild](/visualstudio/msbuild/msbuild-tasks). 

Všechny sady nástrojů nyní využívat sdílené komponenty sady SDK a cíle, rozhraní příkazového řádku zahrnutý. Například nebude volat další verze sady Visual Studio `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz pro obnovení závislostí pro projekty .NET Core, cíl "Obnovení" se bude používat přímo. Protože se jedná o cíle nástroje MSBuild, můžete také pomocí nezpracované nástroje MSBuild je spouštět pomocí [dotnet msbuild](dotnet-msbuild.md) příkazu. 

### <a name="cli-commands"></a>Příkazy rozhraní příkazového řádku
Sdílené komponenty SDK znamená, že, většinou existující příkazy rozhraní příkazového řádku byly znovu implementovaná jako úlohy MSBuild a cíle. Co to znamená pro vaše využití sady nástrojů a příkazů rozhraní příkazového řádku? 

Z hlediska využití neprojeví tak, jak používat rozhraní příkazového řádku. Rozhraní příkazového řádku stále obsahuje základní příkazy, které existují ve verzi Preview 2:

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Tyto příkazy stále to, co očekáváte, že jim (nový projekt, sestavte ho, publikujte ho, pack a tak dále). Většinu možností se nezmění a stále existují, a můžete konzultovat obrazovky nápovědy příkazy, buď (pomocí `dotnet <command> --help`) nebo v dokumentaci na tomto webu a seznamte se se změnami. 

Z hlediska provádění příkazů rozhraní příkazového řádku se jejich parametry a vytvořit volání "neupravené" MSBuild, který bude potřebné vlastnosti nastavit a spustit na požadovaný cíl. Pro lepší znázornění, vezměte v úvahu následující příkaz: 

   `dotnet publish -o pub -c Release`
    
Tento příkaz je publikování aplikace do `pub` složky pomocí konfigurace "Verze". Tento příkaz načte interně přeloženy do následující vyvolání MSBuild: 

   `dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release`

Významné výjimka tohoto pravidla jsou `new` a `run` příkazy, protože nejsou implementované jako cílů MSBuild.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
