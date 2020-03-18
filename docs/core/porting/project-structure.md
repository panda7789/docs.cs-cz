---
title: Uspořádání projektů pro rozhraní .NET Framework a .NET Core
description: Nápověda pro vlastníky projektu, kteří chtějí zkompilovat své řešení proti rozhraní .NET Framework a .NET Core vedle sebe.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777336"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Uspořádání projektu pro podporu rozhraní .NET Framework i .NET Core

Můžete vytvořit řešení, které se zkompiluje pro rozhraní .NET Framework i .NET Core vedle sebe. Tento článek popisuje několik možností organizace projektu, které vám pomohou dosáhnout tohoto cíle. Zde jsou některé typické scénáře, které je třeba zvážit při rozhodování o tom, jak nastavit rozložení projektu pomocí .NET Core. Seznam nemusí zahrnovat vše, co chcete; priority na základě potřeb projektu.

- [**Sloučení stávajících projektů a základních projektů .NET do jednotlivých projektů**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *K čemu je to dobré:*
  - Zjednodušuje proces sestavení kompilací jednoho projektu, nikoli více projektů, které každý cílí na jinou verzi rozhraní .NET Framework nebo platformu.
  - Zjednodušuje správu zdrojových souborů pro víceúčelové projekty, protože je nutné spravovat jeden soubor projektu. Při přidávání nebo odebírání zdrojových souborů vyžadují alternativy jejich ruční synchronizaci s ostatními projekty.
  - Snadno generovat balíček NuGet pro spotřebu.
  - Umožňuje psát kód pro konkrétní verzi rozhraní .NET Framework v knihovnách pomocí direktiv kompilátoru.

  *Nepodporované scénáře:*
  - Vyžaduje, aby vývojáři k otevření existujících projektů používali Visual Studio 2017 nebo novější verzi. Chcete-li podporovat starší verze sady Visual Studio, je lepší volbou [uchovávat soubory projektu v různých složkách.](#support-vs)

- <a name="support-vs"></a>[**Zachování samostatných existujících projektů a nových projektů .NET Core**](#keep-existing-projects-and-create-a-net-core-project)

  *K čemu je to dobré:*
  - Podporuje vývoj existujících projektů pro vývojáře a přispěvatele, kteří nemusí mít Visual Studio 2017 nebo novější verzi.
  - Snižuje možnost vytváření nových chyb v existujících projektech, protože v těchto projektech není vyžadována žádná konve kódu.

## <a name="example"></a>Příklad

Zvažte úložiště níže:

![Stávající projekt](./media/project-structure/existing-project-structure.png)

[**Zdrojový kód**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

Následující popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na omezení a složitost i existující projekty.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Nahrazení stávajících projektů víceúčelovým projektem .NET Core

Reorganizovat úložiště tak, aby všechny existující * \*soubory .csproj* byly odebrány a jeden * \*soubor .csproj* je vytvořen, který se zaměřuje na více rámců. To je skvělá volba, protože jeden projekt je schopen kompilovat pro různé architektury. Má také pravomoc zpracovávat různé možnosti kompilace a závislosti na cílové rozhraní.

![Vytvořte csproj, který se zaměřuje na více rámců](./media/project-structure/multi-targeted-project.png)

[**Zdrojový kód**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Změny poznámky jsou:

- Nahrazení *packages.config* a * \*.csproj* novým [.NET Core * \*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Balíčky NuGet `<PackageReference> ItemGroup`jsou určeny pomocí služby .

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachovat existující projekty a vytvořit projekt .NET Core

Pokud existují existující projekty, které se zaměřují na starší architektury, můžete chtít ponechat tyto projekty nedotčené a použít projekt .NET Core k cílení budoucích architektur.

![Projekt .NET Core s existujícím projektem v jiné složce](./media/project-structure/separate-projects-same-source.png)

[**Zdrojový kód**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Jádro .NET a existující projekty jsou uloženy v samostatných složkách. Udržování projektů v samostatných složkách zabraňuje vynucení mít Visual Studio 2017 nebo novější verze. Můžete vytvořit samostatné řešení, které otevře pouze staré projekty.

## <a name="see-also"></a>Viz také

- [Dokumentace k přenosu jádra .NET](index.md)
