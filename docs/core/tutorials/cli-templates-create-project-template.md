---
title: Vytvoření šablony projektu pro dotnet new
description: Přečtěte si, jak vytvořit šablonu projektu pro nový příkaz dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503531"
---
# <a name="tutorial-create-a-project-template"></a>Kurz: Vytvoření šablony projektu

Pomocí rozhraní .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory, dokonce i prostředky. Tento kurz je druhá část série, která vás naučí, jak vytvořit, nainstalovat a `dotnet new` odinstalovat šablony pro použití s příkazem.

V této části seriálu se dozvíte, jak:

> [!div class="checklist"]
>
> * Vytvoření zdrojů šablony projektu
> * Vytvoření konfigurační složky a souboru šablony
> * Instalace šablony z cesty k souboru
> * Testování šablony položky
> * Odinstalace šablony položky

## <a name="prerequisites"></a>Požadavky

* Dokončení [části 1](cli-templates-create-item-template.md) této série kurzů.
* Otevřete terminál a přejděte do složky _working\templates._

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

Šablony projektů vytvářejí projekty připravené ke spuštění, které uživatelům usnadňují spouštění pracovní sady kódu. .NET Core obsahuje několik šablon projektu, jako je například konzolová aplikace nebo knihovna tříd. V tomto příkladu vytvoříte nový projekt konzoly, který umožňuje C# 8.0 a vytvoří `async main` vstupní bod.

V terminálu přejděte do složky _Working\templates_ a vytvořte novou podsložku s názvem _consoleasync_. Zadejte podsložku `dotnet new console` a spusťte pro generování standardní konzolové aplikace. Budete upravovat soubory vytvořené touto šablonou a vytvořit tak novou šablonu.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Upravit Program.cs

Otevřete _soubor program.cs._ Projekt konzoly nepoužívá asynchronní vstupní bod, takže to přidáme. Změňte kód na následující a uložte soubor.

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>Změnit consoleasync.csproj

Pojďme aktualizovat jazykovou verzi jazyka C#, kterou projekt používá, na verzi 8.0. Upravte soubor _consoleasync.csproj_ `<LangVersion>` a přidejte nastavení do `<PropertyGroup>` uzlu.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Sestavení projektu

Před dokončením šablony projektu byste ji měli otestovat, abyste se ujistili, že se zkompiluje a spustí správně.

V terminálu spusťte následující příkaz.

```dotnetcli
dotnet run
```

Získáte následující výstup.

```console
Hello World with C# 8.0!
```

Složky _obj_ a _bin_ vytvořené `dotnet run`pomocí aplikace můžete odstranit . Odstraněním těchto souborů zajistíte, že šablona bude mít pouze soubory související se šablonou a ne všechny soubory, které jsou výsledkem akce sestavení.

Nyní, když máte obsah šablony vytvořené, musíte vytvořit konfiguraci šablony v kořenové složce šablony.

## <a name="create-the-template-config"></a>Vytvoření konfigurace šablony

Šablony jsou v rozhraní .NET Core rozpoznány speciální složkou a konfiguračním souborem, které existují v kořenovém adresáři šablony. V tomto kurzu je složka šablony umístěna na _adrese working\templates\consoleasync_.

Při vytváření šablony jsou všechny soubory a složky ve složce šablony zahrnuty jako součást šablony s výjimkou speciální složky konfigurace. Tato složka konfigurace má název _.template.config_.

Nejprve vytvořte novou podsložku s názvem _.template.config_, zadejte ji. Potom vytvořte nový soubor s názvem _template.json_. Struktura složek by měla vypadat takto.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Otevřete _template.json_ s vaším oblíbeným textovým editorem a vložte do následujícího kódu json a uložte jej.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

Tento konfigurační soubor obsahuje všechna nastavení šablony. Můžete vidět základní nastavení, `name` `shortName` jako je a `tags/type` ale také je `project`zde hodnota, která je nastavena na . Tím označíte šablonu jako šablonu projektu. Neexistuje žádné omezení typu šablony, kterou vytvoříte. Hodnoty `item` `project` a jsou běžné názvy, které doporučuje rozhraní .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.

Položka `classifications` představuje sloupec **značek,** který `dotnet new` se zobrazí při spuštění a získáte seznam šablon. Uživatelé mohou také vyhledávat na základě klasifikačních značek. Nepleťte si `tags` vlastnost v souboru json se seznamem `classifications` značek. Jsou to dvě různé věci, bohužel pojmenované podobně. Úplné schéma souboru *template.json* se nachází v [úložišti schématu JSON](http://json.schemastore.org/template). Další informace o souboru *template.json* naleznete [na wiki dotnet templating](https://github.com/dotnet/templating/wiki).

Nyní, když máte platný soubor _.template.config/template.json,_ je šablona připravena k instalaci. Před instalací šablony se ujistěte, že jste odstranili všechny další složky souborů a soubory, které nechcete zahrnout do šablony, jako jsou složky _bin_ nebo _obj._ V terminálu přejděte do složky `dotnet new -i .\` _consoleasync_ a spusťte instalaci šablony umístěné v aktuální složce. Pokud používáte operační systém Linux nebo macOS, použijte `dotnet new -i ./`lomítko: .

Tento příkaz vypíše seznam nainstalovaných šablon, které by měly zahrnovat vaše.

```dotnetcli
dotnet new -i .\
```

Získáte výstup podobný následující.

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a>Testování šablony projektu

Nyní, když máte nainstalovanou šablonu položky, otestujte ji.

1. Přechod do _testovací_ složky

1. Vytvořte novou konzolovou aplikaci s následujícím příkazem, který `dotnet run` generuje pracovní projekt, který můžete snadno testovat pomocí příkazu.

    ```dotnetcli
    dotnet new consoleasync
    ```

    Získáte následující výstup.

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. Spusťte projekt pomocí následujícího příkazu.

    ```dotnetcli
    dotnet run
    ```

    Získáte následující výstup.

    ```console
    Hello World with C# 8.0!
    ```

Blahopřejeme! Vytvořili jste a nasadili šablonu projektu s jádrem .NET Core. Při přípravě na další část této série kurzů je nutné odinstalovat šablonu, kterou jste vytvořili. Ujistěte se, že odstranit všechny soubory z _testovací_ složky příliš. Tím se vrátíte do čistého stavu připraveného pro další hlavní část tohoto kurzu.

### <a name="uninstall-the-template"></a>Odinstalace šablony

Vzhledem k tomu, že jste šablonu nainstalovali pomocí cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru. Seznam šablon nainstalovaných můžete zobrazit spuštěním příkazu. `dotnet new -u` Šablona by měla být uvedena jako poslední. Pomocí uvedené cesty odinstalujte `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` šablonu pomocí příkazu.

```dotnetcli
dotnet new -u
```

Získáte výstup podobný následující.

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

Chcete-li šablonu odinstalovat, spusťte následující příkaz.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili šablonu projektu. Chcete-li se dozvědět, jak zabalit šablony položky i projektdo snadno použitelného souboru, pokračujte v této sérii kurzů.

> [!div class="nextstepaction"]
> [Vytvoření balíčku šablon](cli-templates-create-template-pack.md)
