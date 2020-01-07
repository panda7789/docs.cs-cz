---
title: Vytvoření balíčku šablon pro dotnet New
description: Naučte se vytvořit soubor CSPROJ, který vytvoří balíček šablon pro příkaz dotnet New.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: a4723d6d63c5739123fad774bc75fae7c9fd6703
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340179"
---
# <a name="tutorial-create-a-template-pack"></a>Kurz: vytvoření balíčku šablon

Pomocí .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory i prostředky. Tento kurz je třetí částí série, která vás seznámí s postupem vytvoření, instalace a odinstalace, šablon pro použití s příkazem `dotnet new`.

V této části série se naučíte:

> [!div class="checklist"]
>
> * Vytvoření projektu \*. csproj pro sestavení sady šablon
> * Konfigurace souboru projektu pro balení
> * Instalace šablony ze souboru balíčku NuGet
> * Odinstalace šablony podle ID balíčku

## <a name="prerequisites"></a>Požadavky

* Dokončete [část 1](cli-templates-create-item-template.md) a [část 2](cli-templates-create-project-template.md) této série kurzů.

  V tomto kurzu se používají dvě šablony vytvořené v první dvou částech tohoto kurzu. Můžete použít jinou šablonu, pokud zkopírujete šablonu jako složku do složky _working\templates\\_ .

* Otevřete terminál a přejděte do složky _work\\_ .

## <a name="create-a-template-pack-project"></a>Vytvoření projektu Template Pack

Template Pack je jeden nebo více šablon zabalených do souboru. Při instalaci nebo odinstalaci balíčku se všechny šablony obsažené v balíčku přidají nebo odeberou v uvedeném pořadí. Předchozí části této série kurzů se pracovaly jenom s jednotlivými šablonami. Chcete-li sdílet nesbalenou šablonu, je nutné zkopírovat složku šablony a nainstalovat ji prostřednictvím této složky. Vzhledem k tomu, že balíček šablon může obsahovat více než jednu šablonu a je jedním souborem, sdílení je snazší.

Balíčky šablon jsou reprezentovány souborem balíčku NuGet ( _. nupkg_). A podobně jako jakýkoli balíček NuGet můžete nahrát balíček šablony do informačního kanálu NuGet. Příkaz `dotnet new -i` podporuje instalaci balíčku šablon z informačního kanálu balíčku NuGet. Kromě toho můžete nainstalovat sadu šablon přímo ze souboru _. nupkg_ .

Obvykle používáte soubor C# projektu ke kompilaci kódu a vytvoření binárního souboru. Projekt však lze použít také k vygenerování balíčku šablon. Změnou nastavení v _. csproj_můžete zabránit tomu, aby se v kompilování kódu a místo toho zahrnuly všechny prostředky vašich šablon jako prostředky. Při sestavení tohoto projektu vytvoří balíček NuGet sady Template Pack.

Balíček, který vytvoříte, bude obsahovat [šablonu položky](cli-templates-create-item-template.md) a [šablonu balíčku](cli-templates-create-project-template.md) , která byla dříve vytvořena. Vzhledem k tomu, že se tyto dvě šablony seskupují do složky _working\templates\\_ , můžeme použít _pracovní_ složku pro soubor _. csproj_ .

V terminálu přejděte do _pracovní_ složky. Vytvořte nový projekt a nastavte jeho název na `templatepack` a výstupní složku do aktuální složky.

```dotnetcli
dotnet new console -n templatepack -o .
```

Parametr `-n` nastaví soubor _. csproj_ filename na _templatepack. csproj_ a parametry `-o` vytvoří soubory v aktuálním adresáři. Měl by se zobrazit výsledek podobný následujícímu výstupu.

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Potom v oblíbeném editoru otevřete soubor _templatepack. csproj_ a nahraďte jeho obsah následujícím kódem XML:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

Nastavení `<PropertyGroup>` v souboru XML výše je rozděleno do tří skupin. První skupina se zabývá vlastnostmi vyžadovanými pro balíček NuGet. Tři `<Package` nastavení musí udělat s vlastnostmi balíčku NuGet k identifikaci balíčku na informačním kanálu NuGet. Konkrétně hodnota `<PacakgeId>` slouží k odinstalování sady šablon s jedním názvem, nikoli cestou k adresáři. Dá se použít taky k instalaci balíčku šablon z informačního kanálu NuGet. Zbývající nastavení, například `<Title>` a `<Tags>` musí dělat s metadaty zobrazenými v informačním kanálu NuGet. Další informace o nastaveních NuGet naleznete v tématu [vlastnosti NuGet a MSBuild](/nuget/reference/msbuild-targets).

Nastavení `<TargetFramework>` musí být nastavené tak, aby nástroj MSBuild běžel správně při spuštění příkazu Pack pro zkompilování a sbalení projektu.

Poslední tři nastavení musí udělat s tím, že správně nakonfigurujete projekt tak, aby zahrnoval šablony do příslušné složky v balíčku NuGet, když se vytvoří.

`<ItemGroup>` obsahuje dvě nastavení. Nejprve nastavení `<Content>` zahrnuje vše ve složce _šablony_ jako obsah. Také je nastavené pro vyloučení složky _bin_ nebo složky _obj_ , aby se zabránilo zahrnutí zkompilovaného kódu (Pokud jste otestovali a nakompilováni šablony). Druhé nastavení `<Compile>` vyloučí všechny soubory kódu z kompilace bez ohledu na to, kde se nacházejí. Toto nastavení brání projektu, který se používá k vytvoření sady šablon z pokusu o zkompilování kódu v hierarchii složek _šablon_ .

## <a name="build-and-install"></a>Sestavení a instalace

Uložte tento soubor a potom spusťte příkaz Pack.

```dotnetcli
dotnet pack
```

Tento příkaz sestaví projekt a vytvoří balíček NuGet v tomto umístění by měl být složka _working\bin\Debug_ .

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Dále nainstalujte soubor Template Pack pomocí příkazu `dotnet new -i PATH_TO_NUPKG_FILE`.

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

Pokud jste nahráli balíček NuGet do informačního kanálu NuGet, můžete použít příkaz `dotnet new -i PACKAGEID`, kde `PACKAGEID` je stejný jako nastavení `<PackageId>` ze souboru _. csproj_ . ID tohoto balíčku je stejné jako identifikátor balíčku NuGet.

## <a name="uninstall-the-template-pack"></a>Odinstalace balíčku šablon

Bez ohledu na to, jakým způsobem jste balíček šablon nainstalovali, buď pomocí souboru _. nupkg_ přímo nebo pomocí kanálu NuGet, je odebrání balíčku šablon stejné. Použijte `<PackageId>` šablony, kterou chcete odinstalovat. Seznam šablon, které jsou nainstalovány, můžete získat spuštěním příkazu `dotnet new -u`.

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
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

K odinstalaci šablony spusťte `dotnet new -u AdatumCorporation.Utility.Templates`. Příkaz `dotnet new` zobrazí výstup informací o nápovědě, které by měly vynechat šablony, které jste nainstalovali dříve.

Blahopřejeme! nainstalovali jste a odinstalovali balíček šablon. 

## <a name="next-steps"></a>Další kroky

Další informace o šablonách, ze kterých už jste se seznámili, najdete v článku [vlastní šablony pro dotnet nový](../tools/custom-templates.md) článek.

* [dotnet/šablonování wiki úložiště GitHub](https://github.com/dotnet/templating/wiki)
* [dotnet/dotnet-Template-Samples – úložiště GitHub](https://github.com/dotnet/dotnet-template-samples)
* [*template. JSON* – schéma v ÚLOŽIŠTI schémat JSON](http://json.schemastore.org/template)
