---
title: Uspořádání projektů pro .NET Framework a .NET Core
description: Pomáhat pro vlastníky projektů, kteří chtějí kompilovat své řešení před .NET Framework a .NET Core souběžně.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: acb73720d231bdb9f27eb0b75b3383c33cef2202
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343542"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Uspořádání projektu pro podporu .NET Framework a .NET Core

Přečtěte si, jak vytvořit řešení, které se zkompiluje jak pro .NET Framework, tak i .NET Core souběžně. Prohlédněte si několik možností uspořádání projektů, které vám pomůžou dosáhnout tohoto cíle. Tady jsou některé typické scénáře, které je potřeba vzít v úvahu při rozhodování o tom, jak nastavit rozložení projektu pomocí .NET Core. Seznam nemusí zahrnovat všechno, co potřebujete; nastavte prioritu podle potřeb vašeho projektu.

- [**Kombinování stávajících projektů a projektů .NET Core do samostatných projektů**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Co je dobré pro:*
  - Zjednodušení procesu sestavení kompilováním jediného projektu namísto kompilace více projektů, z nichž každý cílí na jinou .NET Framework verzi nebo platformu.
  - Zjednodušení správy zdrojového souboru pro projekty cílené na více lokalit, protože je nutné spravovat jeden soubor projektu. Když přidáváte nebo odebíráte zdrojové soubory, alternativy vyžadují ruční synchronizaci těchto souborů s ostatními projekty.
  - Snadné generování balíčku NuGet pro spotřebu
  - Umožňuje psát kód pro konkrétní .NET Frameworkovou verzi v knihovnách pomocí direktiv kompilátoru.

  *Nepodporované scénáře:*
  - Pro otevření stávajících projektů vyžaduje, aby vývojáři používali Visual Studio 2017 nebo novější verzi. Aby bylo možné podporovat starší verze sady Visual Studio, je lepší volbou [souborů projektu v různých složkách](#support-vs) .

- <a name="support-vs"></a>[**Zachovat existující projekty a nové projekty .NET Core oddělené**](#keep-existing-projects-and-create-a-net-core-project)

  *Co je dobré pro:*
  - Podpora vývoje u stávajících projektů vývojářům a přispěvatelům, kteří nemusí mít Visual Studio 2017 nebo novější verzi.
  - Snížení možnosti vytváření nových chyb v existujících projektech, protože v těchto projektech nejsou vyžadovány žádné změny kódu.

## <a name="example"></a>Příklad

Vezměte v úvahu úložiště níže:

![Existující projekt](./media/project-structure/existing-project-structure.png)

[**Zdrojový kód**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

Následující článek popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na omezeních a složitosti stávajících projektů.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Nahradit existující projekty více cíleným projektem .NET Core

Znovu uspořádejte úložiště tak, aby všechny existující *\*soubory. csproj* byly odebrány a byl vytvořen jediný soubor *\*. csproj* , který cílí na více platforem. Tato možnost je skvělá, protože jeden projekt je schopný kompilovat pro různá rozhraní. Má také možnost zvládnout různé možnosti kompilace a závislosti na cílové rozhraní.

![Vytvoření csproj, který se zaměřuje na více platforem](./media/project-structure/multi-targeted-project.png)

[**Zdrojový kód**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Změny poznámky jsou:

- Nahrazení souboru *Packages. config* a *\*. csproj* novým [rozhraním .NET Core *\*. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Balíčky NuGet se zadává pomocí `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachovat existující projekty a vytvořit projekt .NET Core

Pokud existují projekty, které jsou cíleny na starší verze rozhraní, je vhodné ponechat tyto projekty nezměněný a použít projekt .NET Core k zacílení budoucích rozhraní.

![Projekt .NET Core se stávajícím projektem v jiné složce](./media/project-structure/separate-projects-same-source.png)

[**Zdrojový kód**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Změny poznámky jsou:

- Rozhraní .NET Core a existující projekty jsou uchovávány v samostatných složkách.
  - Udržování projektů v samostatných složkách zabraňuje vynucení sady Visual Studio 2017 nebo novější verze. Můžete vytvořit samostatné řešení, které otevírá jenom staré projekty.

## <a name="see-also"></a>Viz také:

- [Dokumentace k portům .NET Core](index.md)
