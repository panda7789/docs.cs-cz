---
title: Vytvoření šablony položky pro dotnet new - .NET Core CLI
description: Přečtěte si, jak vytvořit šablonu položky pro nový příkaz dotnet. Šablony položek mohou obsahovat libovolný počet souborů.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503553"
---
# <a name="tutorial-create-an-item-template"></a>Kurz: Vytvoření šablony položky

Pomocí rozhraní .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory, dokonce i prostředky. Tento kurz je první částí řady, která vás naučí vytvářet, instalovat a odinstalovat šablony pro použití s příkazem. `dotnet new`

V této části seriálu se dozvíte, jak:

> [!div class="checklist"]
>
> * Vytvoření třídy pro šablonu položky
> * Vytvoření konfigurační složky a souboru šablony
> * Instalace šablony z cesty k souboru
> * Testování šablony položky
> * Odinstalace šablony položky

## <a name="prerequisites"></a>Požadavky

* [Sada .NET Core 2.2 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
* Přečtěte si referenční článek [Vlastní šablony pro dotnet new](../tools/custom-templates.md).

  Referenční článek vysvětluje základy o šablonách a o tom, jak jsou sestaveny. Některé z těchto informací budou zopakovány zde.

* Otevřete terminál a přejděte do složky _working\templates._

## <a name="create-the-required-folders"></a>Vytvoření požadovaných složek

Tato řada používá "pracovní složku", kde je zdroj šablony obsažen, a "testovací složku" používanou k testování šablon. Pracovní složka a testovací složka by měly být pod stejnou nadřazenou složkou.

Nejprve vytvořte nadřazenou složku, na názvu nezáleží. Potom vytvořte podsložku s názvem _Pracovní_. Uvnitř _pracovní_ složky vytvořte podsložku s názvem _šablony_.

Dále vytvořte složku pod nadřazenou složku s názvem _Test_. Struktura složek by měla vypadat takto.

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Vytvoření šablony položky

Šablona položky je specifický typ šablony, který obsahuje jeden nebo více souborů. Tyto typy šablon jsou užitečné, pokud chcete vygenerovat něco jako config, kód nebo soubor řešení. V tomto příkladu vytvoříte třídu, která přidá metodu rozšíření k typu řetězce.

V terminálu přejděte do složky _Working\templates_ a vytvořte novou podsložku s názvem _Extensions_. Zadejte složku.

```console
working
└───templates
    └───extensions
```

Vytvořte nový soubor s názvem _CommonExtensions.cs_ a otevřete jej pomocí oblíbeného textového editoru. Tato třída bude poskytovat `Reverse` metodu rozšíření s názvem, která obrátí obsah řetězce. Vložte do následujícího kódu a uložte soubor:

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

Nyní, když máte obsah šablony vytvořené, musíte vytvořit konfiguraci šablony v kořenové složce šablony.

## <a name="create-the-template-config"></a>Vytvoření konfigurace šablony

Šablony jsou v rozhraní .NET Core rozpoznány speciální složkou a konfiguračním souborem, které existují v kořenovém adresáři šablony. V tomto kurzu je složka šablony umístěna v _working\templates\extensions_.

Při vytváření šablony jsou všechny soubory a složky ve složce šablony zahrnuty jako součást šablony s výjimkou speciální složky konfigurace. Tato složka konfigurace má název _.template.config_.

Nejprve vytvořte novou podsložku s názvem _.template.config_, zadejte ji. Potom vytvořte nový soubor s názvem _template.json_. Struktura složek by měla vypadat takto:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Otevřete _template.json_ s vaším oblíbeným textovým editorem a vložte do následujícího kódu JSON a uložte jej.

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

Tento konfigurační soubor obsahuje všechna nastavení šablony. Můžete zobrazit základní nastavení, `name` například a `shortName`, ale `tags/type` je zde `item`také hodnota, která je nastavena na . Tím se šablona zařazuje do kategorií jako šablona položky. Neexistuje žádné omezení typu šablony, kterou vytvoříte. Hodnoty `item` `project` a jsou běžné názvy, které doporučuje rozhraní .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.

Položka `classifications` představuje sloupec **značek,** který `dotnet new` se zobrazí při spuštění a získáte seznam šablon. Uživatelé mohou také vyhledávat na základě klasifikačních značek. Nezaměňujte `tags` vlastnost v \*souboru JSON `classifications` se seznamem značek. Jsou to dvě různé věci, bohužel pojmenované podobně. Úplné schéma souboru *template.json* se nachází v [úložišti schématu JSON](http://json.schemastore.org/template). Další informace o souboru *template.json* naleznete [na wiki dotnet templating](https://github.com/dotnet/templating/wiki).

Nyní, když máte platný soubor _.template.config/template.json,_ je šablona připravena k instalaci. V terminálu přejděte do složky _rozšíření_ a spusťte následující příkaz pro instalaci šablony umístěné v aktuální složce:

* **Ve Windows**:`dotnet new -i .\`
* **Na Linuxu nebo macOS**:`dotnet new -i ./`

Tento příkaz vypíše seznam nainstalovaných šablon, které by měly zahrnovat vaše.

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

## <a name="test-the-item-template"></a>Otestovat šablonu položky

Nyní, když máte nainstalovanou šablonu položky, otestujte ji. Přejděte do _složky test/_ a `dotnet new console`vytvořte novou konzolovou aplikaci s . Tím se vygeneruje pracovní projekt, `dotnet run` který můžete snadno testovat pomocí příkazu.

```dotnetcli
dotnet new console
```

Získáte výstup podobný následující.

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

Spusťte projekt s.

```dotnetcli
dotnet run
```

Získáte následující výstup.

```console
Hello World!
```

Dále spusťte `dotnet new stringext` a vygenerujte _CommonExtensions.cs_ ze šablony.

```dotnetcli
dotnet new stringext
```

Získáte následující výstup.

```console
The template "Example templates: string extensions" was created successfully.
```

Změňte kód _Program.cs_ v Program.cs `"Hello World"` stornovat řetězec s metodou rozšíření poskytované šablonou.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Spusťte program znovu a uvidíte, že výsledek je obrácený.

```dotnetcli
dotnet run
```

Získáte následující výstup.

```console
!dlroW olleH
```

Blahopřejeme! Vytvořili jste a nasadili šablonu položky s jádrem .NET Core. Při přípravě na další část této série kurzů je nutné odinstalovat šablonu, kterou jste vytvořili. Ujistěte se, že odstranit všechny soubory z _testovací_ složky příliš. Tím se vrátíte do čistého stavu připraveného pro další hlavní část tohoto kurzu.

## <a name="uninstall-the-template"></a>Odinstalace šablony

Vzhledem k tomu, že jste šablonu nainstalovali podle cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru. Seznam šablon nainstalovaných můžete zobrazit spuštěním příkazu. `dotnet new -u` Šablona by měla být uvedena jako poslední. Pomocí uvedené cesty odinstalujte `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` šablonu pomocí příkazu.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

Chcete-li šablonu odinstalovat, spusťte následující příkaz.

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili šablonu položky. Chcete-li se dozvědět, jak vytvořit šablonu projektu, pokračujte v této sérii kurzů.

> [!div class="nextstepaction"]
> [Vytvoření šablony projektu](cli-templates-create-project-template.md)
