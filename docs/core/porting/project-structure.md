---
title: Uspořádání projektu pro podporu rozhraní .NET Framework a .NET Core
description: Nápověda pro vlastníky projektu, kteří chtějí zkompilovat své řešení pro rozhraní .NET Framework a .NET Core-souběžného.
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.openlocfilehash: e6cd9c6d66996d9fd24fe71d48091723143e5849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Uspořádání projektu pro podporu rozhraní .NET Framework a .NET Core

Tento článek pomůže vlastníky projektu, kteří chtějí zkompilovat své řešení pro rozhraní .NET Framework a .NET Core-souběžného. Nabízí několik možností pro uspořádání projekty tak, aby pomoci vývojářům při dosažení tohoto cíle. Následující seznam uvádí některé typické scénáře, které je třeba zvážit, když jste rozhodování, jak nastavit rozložení projektu s .NET Core. V seznamu nemusí zahrnovat všechny objekty, které chcete zjistit. určení priority podle potřeb vašeho projektu.

* [**Existující projekty a .NET Core projekty zkombinovat do jednoho projektů**][option-csproj]

  *Co to je vhodné pro:*
  * Ke zjednodušení procesu sestavení kompilování jeden projekt spíše než kompilování více projektů každý cílení na různé verze rozhraní .NET Framework nebo platformu.
  * Ke zjednodušení souboru správy zdrojů pro cílové více projektů, protože se musí spravovat jediného souboru projektu. Při přidávání nebo odebírání zdrojových souborů, alternativ vyžadují, abyste tato nastavení u jiných projekty synchronizovat ručně.
  * Snadno generování balíčku NuGet pro používání.
  * Můžete napsat kód pro konkrétní verzi rozhraní .NET Framework ve vašich knihovnách prostřednictvím direktivy kompilátoru.

  *Nepodporované scénáře:*
  * Vyžaduje vývojářům používat Visual Studio 2017 otevřete existující projekty. K podpoře starší verze sady Visual Studio, [udržování souborů projektu v různých složkách](#support-vs) není lepší volbou.

* <a name="support-vs"></a>[**Oddělit existující projekty a nové projekty .NET Core**][option-csproj-folder]

  *Co to je vhodné pro:*
  * Pokračovat bez nutnosti upgradu pro vývojáře nebo přispěvatelé, kteří nemusí mít Visual Studio 2017 podporují vývoj na existující projekty.
  * Snížení možnost vytvoření nové chyby v existující projekty, protože žádné změny kódu se vyžaduje v těchto projektech.

## <a name="example"></a>Příklad

Vezměte v úvahu následující úložiště:

![Existující projekt][example-initial-project]

[**Zdrojový kód**][example-initial-project-code]

Následující část popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na složitosti existující projekty a omezení.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Nahradit existující projekty s projektem cílové více .NET Core

Reorganizovat úložiště, který všechny existující  *\*.csproj* soubory jsou odebrané a jednu  *\*.csproj* soubor je vytvořen zacílený více rozhraní. Toto je skvělou možnost, protože jeden projekt je ke zkompilování pro různé rozhraní. Je také napájení pro zpracování různých kompilace možnosti a závislosti na cílové rozhraní.

![Vytvoření csproj, která je cílena více rozhraní][example-csproj]

[**Zdrojový kód**][example-csproj-code]

Poznámka: změny se:
* Nahrazení *packages.config* a  *\*.csproj* s novou [.NET Core  *\*.csproj* ] [ example-csproj-netcore]. Balíčky NuGet se zadaným `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachovat existující projekty a vytvoření projektu .NET Core

Pokud je existující projekty, které používají starší architektury, můžete ponechat beze změny těchto projektů a použití .NET Core projektu pro budoucí architektury.

![Projekt .NET core pomocí existující projekt v jiné složce][example-csproj-different-folder]

[**Zdrojový kód**][example-csproj-different-code]

Poznámka: změny se:
* .NET Core a existující projekty jsou uchovávány v samostatné složky.
    * Udržování projektů v samostatné složky zabraňuje vynucení, abyste měli Visual Studio 2017. Můžete vytvořit samostatné řešení, které pouze otevře staré projekty.

## <a name="see-also"></a>Viz také

Podrobnosti najdete [.NET Core portování dokumentaci] [ porting-doc] o další pokyny k migraci na .NET Core.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Existující projekt"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Vytvoření csproj, která je cílena více rozhraní"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projekt .NET core pomocí stávající PCL v jiné složce"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
