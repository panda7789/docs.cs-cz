---
title: Vytvořit šablonu projektu pro dotnet New
description: Naučte se vytvořit šablonu projektu pro příkaz dotnet New.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 3455720d729f813d9b6f32e433adffa4dc40dce4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926136"
---
# <a name="tutorial-create-a-project-template"></a>Kurz: Vytvoření šablony projektu

Pomocí .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory i prostředky. Tento kurz je druhou částí série, která vás seznámí s postupem vytvoření, instalace a odinstalace šablon pro použití s `dotnet new` příkazem.

V této části série se naučíte:

> [!div class="checklist"]
>
> * Vytvoření prostředků šablony projektu
> * Vytvoření konfigurační složky a souboru šablony
> * Nainstalovat šablonu z cesty k souboru
> * Testování šablony položky
> * Odinstalace šablony položky

## <a name="prerequisites"></a>Požadavky

* Vyplňte [část 1](cli-templates-create-item-template.md) této série kurzů.
* Otevřete terminál a přejděte do složky _working\templates\\_  .

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

Projektové šablony vytvářejí projekty připravené k spuštění, které uživatelům usnadňují spuštění pracovní sady kódu. .NET Core obsahuje několik šablon projektů, jako je například Konzolová aplikace nebo knihovna tříd. V tomto příkladu vytvoříte nový projekt konzoly, který povolí C# 8,0 a vytvoří `async main` vstupní bod.

V terminálu přejděte do složky _working\templates\\_  a vytvořte novou podsložku s názvem _consoleasync_. Zadejte podsložku a spusťte `dotnet new console` příkaz pro vygenerování standardní konzolové aplikace. Pokud chcete vytvořit novou šablonu, budete upravovat soubory vytvořené touto šablonou.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Upravit Program.cs

Otevřete soubor _program.cs_ . Projekt konzoly nepoužívá asynchronní vstupní bod, takže ho přidáváme. Změňte kód na následující a uložte soubor:

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

## <a name="modify-consoleasynccsproj"></a>Upravit consoleasync. csproj

Pojďme aktualizovat C# jazykovou verzi, kterou projekt používá, na verzi 8,0. Upravte soubor _consoleasync. csproj_ a přidejte `<LangVersion>` nastavení do `<PropertyGroup>` uzlu.

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

Před dokončením šablony projektu byste ji měli otestovat, abyste se ujistili, že kompiluje a běží správně. V terminálu spusťte `dotnet run` příkaz a měl by se zobrazit následující výstup:

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

Můžete odstranit složky _obj_ a _bin_ vytvořené pomocí `dotnet run`. Odstranění těchto souborů zajistí, že šablona obsahuje jenom soubory, které souvisejí s vaší šablonou, a ne žádné soubory, které mají za následek akci sestavení.

Teď, když máte vytvořený obsah šablony, je nutné vytvořit šablonu config v kořenové složce šablony.

## <a name="create-the-template-config"></a>Vytvoření šablony konfigurace

Šablony jsou v rozhraní .NET Core rozpoznány pomocí speciální složky a konfiguračního souboru, který se nachází v kořenovém adresáři šablony. V tomto kurzu se složka šablony nachází na adrese _working\templates\consoleasync\\_ .

Když vytvoříte šablonu, všechny soubory a složky ve složce šablon budou zahrnuty jako součást šablony kromě speciální konfigurační složky. Tato konfigurační složka má název _. template. config_.

Nejprve vytvořte novou podsložku s názvem _. template. config_a zadejte ji. Pak vytvořte nový soubor s názvem _template. JSON_. Struktura vaší složky by měla vypadat takto:

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Otevřete _template. JSON_ s oblíbeným textovým editorem a vložte následující kód JSON a uložte ho:

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

Tento konfigurační soubor obsahuje všechna nastavení pro šablonu. Můžete zobrazit základní nastavení, `name` například a `shortName` , `tags/type` ale také existuje hodnota, která je nastavena na `project`. Tím označíte šablonu jako šablonu projektu. Typ šablony, kterou jste vytvořili, není nijak omezen. Hodnoty `item` a`project` jsou běžné názvy, které doporučuje .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.

Položka představuje sloupec **značky** , který se zobrazí při spuštění `dotnet new` a získání seznamu šablon. `classifications` Uživatelé můžou vyhledávat i na základě klasifikačních značek. Nepleťte `tags` si vlastnost v souboru JSON `classifications` se seznamem značek. Existují dvě různé věci, které se nazývají podobně. Úplné schéma pro soubor *template. JSON* najdete v [úložišti schémat JSON](http://json.schemastore.org/template). Další informace o souboru *template. JSON* najdete v tématu [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).

Teď, když máte platný soubor _. template. config/Template. JSON_ , je vaše šablona připravená k instalaci. Před instalací šablony nezapomeňte odstranit všechny složky a soubory s dalšími soubory, které nechcete zahrnout do šablony, jako jsou složky _bin_ nebo _obj_ . V terminálu přejděte do složky _consoleasync_ a spusťte `dotnet new -i .\` instalaci šablony umístěné v aktuální složce. Pokud používáte operační systém Linux nebo MacOS, použijte lomítko: `dotnet new -i ./`.

Tento příkaz vypíše seznam nainstalovaných šablon, které by měly obsahovat vaše.

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

### <a name="test-the-project-template"></a>Testování šablony projektu

Teď, když máte nainstalovanou šablonu položky, otestujte ji. Přejděte do složky _test_ a vytvořte novou konzolovou aplikaci pomocí `dotnet new console`. Tím se vygeneruje pracovní projekt, který lze snadno otestovat `dotnet run` pomocí příkazu.

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

Blahopřejeme! Vytvořili jste a nasadili šablonu projektu pomocí .NET Core. Při přípravě na další část této série kurzů musíte odinstalovat šablonu, kterou jste vytvořili. Přesvědčte se, zda jsou všechny soubory odstraněny také z _testovací_ složky. Tím se vrátíte zpět do připraveného stavu pro další hlavní část tohoto kurzu.

### <a name="uninstall-the-template"></a>Odinstalace šablony

Vzhledem k tomu, že jste šablonu nainstalovali pomocí cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru. Seznam nainstalovaných šablon můžete zobrazit spuštěním `dotnet new -u` příkazu. Vaše šablona by měla být uvedena jako poslední. Použijte cestu uvedenou k odinstalaci šablony pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.

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

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili šablonu projektu. Chcete-li se dozvědět, jak zabalit šablony položek a projektů do snadno použitelného souboru, pokračujte v této sérii kurzů.

> [!div class="nextstepaction"]
> [Vytvoření sady šablon](cli-templates-create-template-pack.md)
