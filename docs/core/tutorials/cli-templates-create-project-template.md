---
title: Vytvoření nové šablony projektu pro dotnet
description: Zjistěte, jak vytvořit šablonu projektu pro nový příkaz dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877180"
---
# <a name="tutorial-create-a-project-template"></a>Kurz: Vytvoření šablony projektu

S .NET Core můžete vytvořit a nasadit šablon, které generují projektů, souborů, dokonce i prostředky. Tento kurz je druhá část série, která vás naučí, jak vytvořit, instalaci a odinstalaci, šablony pro použití se službou `dotnet new` příkazu.

V této části této série se dozvíte jak:

> [!div class="checklist"]
> * Vytvoření prostředků šablony projektu
> * Vytvoření šablony konfigurace složky a souboru
> * Instalovat z cesty k souboru šablony
> * Test šablony položky
> * Odinstalace šablonu položky

## <a name="prerequisites"></a>Požadavky

* Kompletní [1. část](cli-templates-create-item-template.md) této série kurzů.
* Otevřete terminál a přejděte _working\templates\\_  složky.

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

Projekt šablony vytvořit připravené ke spuštění projektů, které usnadňují uživatelům začít s funkční sadu kódu. .NET core obsahuje několik šablon projektů například konzolové aplikace nebo knihovny tříd. V tomto příkladu vytvoříte nový projekt konzoly, která umožňuje C# 8.0 a vytváří `async main` vstupní bod.

V terminálu přejděte _working\templates\\_  složky a vytvořit novou podsložku s názvem _consoleasync_. Zadejte název podsložky a spusťte `dotnet new console` ke generování standardní konzolové aplikace. Budete upravovat soubory vytvořené pomocí této šablony můžete vytvořit novou šablonu.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Úprava souboru Program.cs

Otevřete _program.cs_ souboru. Projekt konzolové není použít asynchronní vstupní bod, Pojďme přidat. Změňte následující kód a soubor uložte:

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

## <a name="modify-consoleasynccsproj"></a>Upravit consoleasync.csproj

Aktualizaci Pojďme C# jazykovou verzi, že projekt používá verzi 8.0. Upravit _consoleasync.csproj_ a přidejte `<LangVersion>` nastavení na hodnotu `<PropertyGroup>` uzlu.

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

Před dokončením šablonu projektu, měli byste otestovat a ujistit se, že se správně zkompiluje a spustí. V terminálu spusťte `dotnet run` příkazu by se měla zobrazit následující výstup:

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

Můžete odstranit _obj_ a _bin_ složky vytvořené využitím `dotnet run`. Odstranění těchto souborů zajišťuje, že šablony obsahuje jenom soubory související s vaší šablony a ne všechny soubory tento výsledek akce sestavení.

Teď, když máte obsah šablony, vytvořili, je potřeba vytvořit šablonu config v kořenové složce šablony.

## <a name="create-the-template-config"></a>Vytvoření šablony konfigurace

Šablony jsou rozpoznány v .NET Core ve zvláštní složce a konfiguračním souboru, který existuje v kořenovém adresáři šablony. V tomto kurzu se nachází na složky šablony _working\templates\consoleasync\\_ .

Když vytvoříte šablonu, všechny soubory a složky ve složce Šablony jsou zahrnuty jako součást šablony s výjimkou složky zvláštní konfigurace. Tato složka config jmenuje _. template.config_.

Nejprve vytvořte novou podsložku s názvem _. template.config_, zadejte ji. Vytvořte nový soubor s názvem _template.json_. Vaše struktura složky by měl vypadat nějak takto:

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Otevřít _template.json_ pomocí oblíbeného textového editoru a vložte následující kód json kód a uložte ho:

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

Tento konfigurační soubor obsahuje všechna nastavení pro šablonu. Vidíte základní nastavení, jako `name` a `shortName` ale také `tags/type` hodnotu, která je nastavena na `project`. To označí jako šablona projektu šablony. Neexistuje žádné omezení typu šablony, které vytvoříte. `item` a `project` hodnoty jsou běžné názvy, které doporučuje .NET Core tak, aby uživatelé mohou snadno filtrovat typ šablony, které hledají.

`classifications` Položka představuje **značky** sloupce se zobrazí při spuštění `dotnet new` a získat seznam šablon. Můžete také vyhledat uživatele podle klasifikační značky. Nepleťte si `tags` vlastnost v souboru json `classifications` seznam značek. Jsou to dvě různé věci bohužel s názvem podobně. Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template). Další informace o *template.json* souboru, najdete v článku [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).

Teď, když máte platný _.template.config/template.json_ souboru je šablona připravena k instalaci. Před instalací šablonu, ujistěte se, že jste odstranili všechny další soubory složky a soubory už nechcete součástí šablony, jako je třeba _bin_ nebo _obj_ složek. V terminálu přejděte _consoleasync_ složky a spusťte `dotnet new -i .\` instalace umístěný ve složce aktuální šablony. Pokud používáte operační systém Linux nebo MacOS, použít lomítko: `dotnet new -i ./`.

Tento příkaz vypíše seznam nainstalované, šablony, které by měl obsahovat vaše.

```console
C:\working\templates\consoleasync> dotnet new -i .\
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

### <a name="test-the-project-template"></a>Test šablony projektu

Teď, když máte nainstalované šablony položky, otestujte ji. Přejděte _testování_ složky a vytvořte novou konzolovou aplikaci s `dotnet new console`. Tím se vytvoří projekt práci snadno můžete otestovat s `dotnet run` příkazu.

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

Blahopřejeme! Vytvoření a nasazení šablonu projektu s .NET Core. Během přípravy na další části této série kurzů je nutné odinstalovat šablona, kterou jste vytvořili. Ujistěte se, že chcete odstranit všechny soubory z _testování_ složky příliš. Získáte zpět do čistého stavu Připraveno pro další hlavní části tohoto kurzu.

### <a name="uninstall-the-template"></a>Odinstalace šablony

Vzhledem k tomu, že jste nainstalovali šablony pomocí cesty k souboru, je nutné odinstalovat ji **absolutní** cesta k souboru. Zobrazí se seznam šablon instalaci spuštěním `dotnet new -u` příkazu. Vaše šablona by měla být uvedená jako poslední. Použití cesty uvedené odinstalace svou šablonu pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.

```console
C:\working> dotnet new -u
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

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Další postup

V tomto kurzu jste vytvořili šablonu projektu. Chcete-li získat informace o balíček šablon položek a projektů do souboru snadným ovládáním, pokračujte v této sérii kurzů.

> [!div class="nextstepaction"]
> [Vytvoření balíčku šablony](cli-templates-create-template-pack.md)
