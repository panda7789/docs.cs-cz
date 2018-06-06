---
title: Architektura nástrojů příkazového řádku .NET core
description: Další informace o .NET Core tooling vrstvy a co se změnilo v nejnovější verze.
author: blackdwarf
ms.date: 03/06/2017
ms.openlocfilehash: 1d96a0b1e19bf84af0ab645ebd104afc899ae656
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696540"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Přehled změn v nástrojích pro .NET Core

Tento dokument popisuje změny přidružené přechod z *project.json* k MSBuild a *csproj* projektu systému s informacemi o změny rozvrstvení nástrojů .NET Core a implementace rozhraní příkazového řádku. Tyto změny došlo oproti verzi rozhraní .NET Core SDK 1.0 a Visual Studio 2017 na 7 března 2017 (najdete v článku [oznámení](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/)), ale byly původně implementována ve verzi .NET Core SDK Preview 3.

## <a name="moving-away-from-projectjson"></a>Přesun mimo project.json
Největší změnou v nástroji pro .NET Core je určitě [přesunout mimo project.json do csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) jako systém projektu. Nejnovější verze nástroje příkazového řádku nepodporují *project.json* soubory. To znamená, že nelze použít k vytvoření, spuštění nebo publikování aplikací na základě project.json a knihovny. Chcete-li použít tuto verzi nástroje, musíte migrovat existující projekty nebo nové spuštění. 

Jako součást tento přesun byl nahrazený vlastní sestavovací modulem, který byl vyvinutý k sestavení projektů project.json modul vyspělá a plně podporuje sestavení s názvem [MSBuild](https://github.com/Microsoft/msbuild). MSBuild je dobře známé stroje v rozhraní .NET komunitě, vzhledem k tomu, že byla klíčová technologie od prvního vydání platformu. Samozřejmě protože je nutné k vytváření aplikací .NET Core, MSBuild má byly přesně na .NET Core a můžete použít na jakékoli platformě, která .NET Core běží na. Jedním z hlavních lišící jádra .NET je, že zásobníku vývoj napříč platformami a jsme provedli jistotu, že tento přesun se nezalamuje této promise.

> [!NOTE]
> Pokud se nový MSBuild a chcete další informace o tom, můžete spustit načtením [koncepty nástroje MSBuild](/visualstudio/msbuild/msbuild-concepts) článku. 

## <a name="the-tooling-layers"></a>Vrstvy nástrojů
S přechodem od existujícího projektu systému a také při budování modul přepínače je na otázku, která následuje přirozeně, některou z těchto změn Změna celkové "rozvrstvení" celý ekosystém nástrojů .NET Core? Existují nové službě bits a součásti?

Začněme s rychlé aktualizačnímu programu na rozvrstvení Preview 2, jak je znázorněno na následujícím obrázku:

![Architektura vysoké úrovně nástrojů Preview 2](media/cli-msbuild-architecture/p2-arch.png)

Rozvrstvení nástroje je poměrně jednoduché. V dolní části máme jako základ nástroje příkazového řádku .NET Core. Všechny nástroje, které vyšší úrovně, jako je Visual Studio nebo Visual Studio Code závisí a spoléhá na rozhraní příkazového řádku k vytvoření projektů, obnovte závislosti a tak dále. Vynutila si, že například pokud Visual Studio se chtěli provést operaci obnovení, bylo by zavolat do `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) v rozhraní příkazového řádku. 

S přechodem na nový systém projektu se změní na předchozím diagramu: 

![Architektura vysoké úrovně .NET core SDK 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Hlavní rozdíl je, že rozhraní příkazového řádku není základní vrstvě už; Tato role je nyní vyplněn "sdílené SDK součástí". Tato sdílená součást SDK je sada cílů a související úlohy, které zodpovídají za kompilace kódu, publikování, balení balíčky NuGet atd. Sada SDK, samotné je open source a je k dispozici na webu GitHub na [SDK úložišti](https://github.com/dotnet/sdk). 

> [!NOTE]
> "Cíl" je MSBuild termín, který určuje pojmenované operace, který lze vyvolat MSBuild. Toto pravidlo je kombinaci obvykle s jedné nebo více úloh, které provést některé logiky, která by měla provést cíl. MSBuild podporuje mnoho předdefinovaných cílů například `Copy` nebo `Execute`; také umožňuje uživatelům napsat vlastní úlohy pomocí spravovaného kódu a definovat cíle k provedení těchto úloh. Další informace najdete v tématu [úlohy nástroje MSBuild](/visualstudio/msbuild/msbuild-tasks). 

Všechny modulové nyní využívat sdílená součást sady SDK a jeho cíle, rozhraní příkazového řádku zahrnutý. Například nebude další verze sady Visual Studio volání do `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz, který má obnovit závislosti pro projekty .NET Core, cíl "Obnovení" se bude používat přímo. Vzhledem k tomu, že jsou tyto cíle MSBuild, můžete také použít nezpracovaná MSBuild provést je pomocí [dotnet msbuild](dotnet-msbuild.md) příkaz. 

### <a name="cli-commands"></a>Rozhraní příkazového řádku
Sdílená součást SDK znamená, že většina existující rozhraní příkazového řádku byla znovu implementovaná jako úlohy nástroje MSBuild a cíle. Co to znamená rozhraní příkazového řádku a vaše používání sady nástrojů? 

Z hlediska využití nemění způsobu, jakým používáte rozhraní příkazového řádku. Rozhraní příkazového řádku má stále základní příkazy, které existují v verzi Preview 2:

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Tyto příkazy stále udělat, co můžete očekávat, aby (nové vytvořte projekt sestavení ji publikovat, sady pack a tak dále). Většina možností se nezmění a stále existují a poraďte se se příkazy, buď obrazovky nápovědy (pomocí `dotnet <command> --help`) nebo v dokumentaci na tomto webu, abyste se seznámili s případnými změnami. 

Z hlediska provádění rozhraní příkazového řádku vezme jejich parametrů a vytvořit volání "nezpracovaných" MSBuild, který bude nastavit potřebné vlastnosti a spustit na požadovaný cíl. Pro lepší znázornění, vezměte v úvahu následující příkaz: 

   `dotnet publish -o pub -c Release`
    
Tento příkaz je publikování aplikace do aplikace `pub` složku pomocí konfigurace "Verze". Tento příkaz načte interně přeložit na následující MSBuild volání: 

   `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

Významné výjimkou tohoto pravidla jsou `new` a `run` příkazy, protože nejsou implementované jako cíle MSBuild.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
