---
title: Vytvořit šablonu položky pro dotnet new - rozhraní příkazového řádku .NET Core
description: Zjistěte, jak vytvořit šablonu položky pro nový příkaz dotnet. Šablony položek může obsahovat libovolný počet souborů.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877177"
---
# <a name="tutorial-create-an-item-template"></a>Kurz: Vytvořit šablonu položky

S .NET Core můžete vytvořit a nasadit šablon, které generují projektů, souborů, dokonce i prostředky. Tento kurz je druhou částí série, která vás naučí, jak vytvořit, instalaci a odinstalaci, šablony pro použití se službou `dotnet new` příkazu.

V této části této série se dozvíte, jak:

> [!div class="checklist"]
> * Vytvořte třídu pro šablonu položky
> * Vytvoření šablony konfigurace složky a souboru
> * Instalovat z cesty k souboru šablony
> * Test šablony položky
> * Odinstalace šablonu položky

## <a name="prerequisites"></a>Požadavky

* [Sada .NET core 2.2 SDK](https://www.microsoft.com/net/core) nebo novější verze.
* Přečtěte si článek odkaz [vlastních šablon pro dotnet nové](../tools/custom-templates.md).

  Odkaz na článek vysvětluje základní informace o šablonách a že jste čeho. Některé z těchto informací se opakoval tady.

* Otevřete terminál a přejděte _working\templates\\_  složky.

## <a name="create-the-required-folders"></a>Vytvořit požadované složky

Tato série používá "pracovní složku" kde je obsažen zdroje šablony a "testování složku" použily k testování vašich šablon. Pracovní složky a složky testování musí být ve stejné nadřazené složky.

Nejprve vytvořte nadřazené složky, název, nezáleží. Potom vytvořte podsložku s názvem _práce_. Uvnitř _práce_ složce vytvořte podsložku s názvem _šablony_.

V dalším kroku vytvořte složku s nadřazenou složku s názvem _testování_. Struktura složek by měl vypadat nějak takto:

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Vytvořit šablonu položky

Šablony položky je určitý typ šablony, která obsahuje jeden nebo více souborů. Tyto typy šablon jsou užitečné, pokud chcete vygenerovat něco jako config, kód nebo soubor řešení. V tomto příkladu vytvoříte třídu, která přidá metodu rozšíření k tomuto typu řetězec.

V terminálu přejděte _working\templates\\_  složky a vytvořit novou podsložku s názvem _rozšíření_. Zadejte složku.

```console
working
└───templates
    └───extensions
```

Vytvořte nový soubor s názvem _CommonExtensions.cs_ a otevřete jej pomocí oblíbeného textového editoru. Tato třída bude poskytovat rozšiřující metodu s názvem `Reverse` , který vrátí obsah řetězce. Vložte následující kód a soubor uložte:

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

Teď, když máte obsah šablony, vytvořili, je potřeba vytvořit šablonu config v kořenové složce šablony.

## <a name="create-the-template-config"></a>Vytvoření šablony konfigurace

Šablony jsou rozpoznány v .NET Core ve zvláštní složce a konfiguračním souboru, který existuje v kořenovém adresáři šablony. V tomto kurzu se nachází na složky šablony _working\templates\extensions\\_ .

Když vytvoříte šablonu, všechny soubory a složky ve složce Šablony jsou zahrnuty jako součást šablony s výjimkou složky zvláštní konfigurace. Tato složka config jmenuje _. template.config_.

Nejprve vytvořte novou podsložku s názvem _. template.config_, zadejte ji. Vytvořte nový soubor s názvem _template.json_. Vaše struktura složky by měl vypadat nějak takto:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Otevřít _template.json_ pomocí oblíbeného textového editoru a vložte následující kód JSON kód a uložte ho:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

Tento konfigurační soubor obsahuje všechna nastavení pro šablonu. Vidíte základní nastavení, jako například `name` a `shortName`, ale k dispozici je také `tags/type` hodnotu, která je nastavena na `item`. To slouží ke kategorizaci do šablony jako šablonu položky. Neexistuje žádné omezení typu šablony, které vytvoříte. `item` a `project` hodnoty jsou běžné názvy, které doporučuje .NET Core tak, aby uživatelé mohou snadno filtrovat typ šablony, které hledají.

`classifications` Položka představuje **značky** sloupce se zobrazí při spuštění `dotnet new` a získat seznam šablon. Můžete také vyhledat uživatele podle klasifikační značky. Nepleťte si `tags` vlastnost \*soubor .json s `classifications` seznam značek. Jsou to dvě různé věci bohužel s názvem podobně. Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template). Další informace o *template.json* souboru, najdete v článku [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).

Teď, když máte platný _.template.config/template.json_ souboru je šablona připravena k instalaci. V terminálu přejděte _rozšíření_ složky a spusťte následující příkaz k instalaci šabloně nachází v aktuální složce:

* **Na Windows**: `dotnet new -i .\`
* **V systému Linux nebo macOS**: `dotnet new -i ./`

Tento příkaz vypíše seznam nainstalované, šablony, které by měl obsahovat vaše.

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a>Test šablony položky

Teď, když máte nainstalované šablony položky, otestujte ji. Přejděte _testování /_ složky a vytvořte novou konzolovou aplikaci s `dotnet new console`. Tím se vytvoří projekt práci snadno můžete otestovat s `dotnet run` příkazu.

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

Potom spusťte `dotnet new stringext` ke generování _CommonExtensions.cs_ ze šablony.

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

Změňte kód v _Program.cs_ vrátit `"Hello World"` řetězec pomocí metody rozšíření poskytované šablony.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Znovu spusťte program a zobrazí se vám, že výsledek je obrácený.

```console
C:\test> dotnet run
!dlroW olleH
```

Blahopřejeme! Vytvoření a nasazení šablony položky s .NET Core. Během přípravy na další části této série kurzů je nutné odinstalovat šablona, kterou jste vytvořili. Ujistěte se, že chcete odstranit všechny soubory z _testování_ složky příliš. Získáte zpět do čistého stavu Připraveno pro další hlavní části tohoto kurzu.

## <a name="uninstall-the-template"></a>Odinstalace šablony

Vzhledem k tomu, že jste nainstalovali pomocí cesta k souboru šablony, je nutné odinstalovat ji **absolutní** cesta k souboru. Zobrazí se seznam šablon instalaci spuštěním `dotnet new -u` příkazu. Vaše šablona by měla být uvedená jako poslední. Použití cesty uvedené odinstalace svou šablonu pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili šablonu položky. Chcete-li zjistěte, jak vytvořit šablonu projektu, pokračujte v této sérii kurzů.

> [!div class="nextstepaction"]
> [Vytvoření šablony projektu](cli-templates-create-project-template.md)
