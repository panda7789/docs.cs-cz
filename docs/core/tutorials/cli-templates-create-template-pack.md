---
title: Vytvořit sadu šablon pro dotnet nové
description: Naučte se, jak vytvořit soubor csproj, který vytvoří balíček šablon pro dotnet nový příkaz.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5bc926861dd6a501d7c2d24bd5f7c4116cc78b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503486"
---
# <a name="tutorial-create-a-template-pack"></a>Kurz: Vytvoření balíčku šablon

Pomocí rozhraní .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory, dokonce i prostředky. Tento kurz je třetí částí řady, která vás naučí vytvářet, instalovat a `dotnet new` odinstalovat šablony pro použití s příkazem.

V této části seriálu se dozvíte, jak:

> [!div class="checklist"]
>
> * Vytvoření \*projektu .csproj pro vytvoření balíčku šablon
> * Konfigurace souboru projektu pro balení
> * Instalace šablony ze souboru balíčku NuGet
> * Odinstalace šablony podle ID balíčku

## <a name="prerequisites"></a>Požadavky

* Dokončení [části 1](cli-templates-create-item-template.md) a části [2](cli-templates-create-project-template.md) této série kurzů.

  Tento kurz používá dvě šablony vytvořené v prvních dvou částech tohoto kurzu. Pokud šablonu zkopírujete jako složku do složky _working\templates,\\ _ můžete ji použít jako složku.

* Otevřete terminál a přejděte do _pracovní\\ _ složky.

## <a name="create-a-template-pack-project"></a>Vytvoření projektu balíčku šablon

Balíček šablon je jedna nebo více šablon zabalených do souboru. Při instalaci nebo odinstalaci balíčku jsou přidány nebo odebrány všechny šablony obsažené v balíčku. Předchozí části této série kurzů fungovaly pouze s jednotlivými šablonami. Chcete-li sdílet nezabalenou šablonu, musíte zkopírovat složku šablony a nainstalovat prostřednictvím této složky. Vzhledem k tomu, že sada šablon může mít v sobě více než jednu šablonu a je to jeden soubor, je sdílení jednodušší.

Balíčky šablon jsou reprezentovány souborem balíčku NuGet (_.nupkg_). A stejně jako každý balíček NuGet, můžete nahrát balíček šablon do informačního kanálu NuGet. Příkaz `dotnet new -i` podporuje instalaci sady šablon z informačního kanálu balíčku NuGet. Kromě toho můžete nainstalovat balíček šablon ze souboru _.nupkg_ přímo.

Obvykle se používá soubor projektu Jazyka C# ke kompilaci kódu a vytvoření binárního souboru. Projekt však lze také použít ke generování šablony pack. Změnou nastavení _.csproj_, můžete zabránit kompilaci libovolného kódu a místo toho zahrnout všechny prostředky šablony jako prostředky. Když je tento projekt sestaven, vytvoří balíček šablony NuGet.

Balíček, který vytvoříte, bude obsahovat dříve vytvořenou [šablonu položky](cli-templates-create-item-template.md) a [šablonu balíčku.](cli-templates-create-project-template.md) Vzhledem k tomu, že jsme tyto dvě šablony seskupili do složky _working\templates,\\ _ můžeme použít _pracovní_ složku pro soubor _.csproj._

V terminálu přejděte do _pracovní_ složky. Vytvořte nový projekt a `templatepack` nastavte název a výstupní složku na aktuální složku.

```dotnetcli
dotnet new console -n templatepack -o .
```

Parametr `-n` nastaví název souboru _.csproj_ na _templatepack.csproj_. Parametr `-o` vytvoří soubory v aktuálním adresáři. Měli byste vidět výsledek podobný následujícímu výstupu.

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Dále otevřete soubor _templatepack.csproj_ ve svém oblíbeném editoru a nahraďte obsah následujícím XML:

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

Nastavení `<PropertyGroup>` ve výše uvedeném xml je rozděleno do tří skupin. První skupina se zabývá vlastnostmi požadovanými pro balíček NuGet. Tři `<Package` nastavení mají co do činění s vlastnostmi balíčku NuGet k identifikaci balíčku na nuget informačníkanál. Konkrétně `<PackageId>` hodnota se používá k odinstalaci šablony pack s jedním názvem namísto cesty k adresáři. Lze také nainstalovat balíček šablon z nugetového kanálu. Zbývající nastavení, jako `<Title>` `<PackageTags>` jsou a mají co do činění s metadaty zobrazenými v informačním kanálu NuGet. Další informace o nastavení NuGet naleznete v [tématu NuGet a MSBuild vlastnosti](/nuget/reference/msbuild-targets).

Nastavení `<TargetFramework>` musí být nastavena tak, aby MSBuild bude fungovat správně při spuštění příkazu pack zkompilovat a zabalit projekt.

Poslední tři nastavení mají co do činění s konfigurací projektu správně zahrnout šablony v příslušné složce v balíčku NuGet při jeho vytvoření.

Obsahuje `<ItemGroup>` dvě nastavení. Nejprve `<Content>` nastavení zahrnuje vše ve složce _šablony_ jako obsah. Je také nastavena tak, aby byla vyloučena jakákoli složka _bin_ nebo _obj,_ aby se zabránilo zahrnutí jakéhokoli kompilovaného kódu (pokud jste testovali a zkompilovali šablony). Za `<Compile>` druhé, nastavení vyloučí všechny soubory kódu z kompilace bez ohledu na to, kde jsou umístěny. Toto nastavení zabrání projektu, který se používá k vytvoření balíčku šablon, aby se pokusil zkompilovat kód v hierarchii složek _šablony._

## <a name="build-and-install"></a>Sestavení a instalace

Uložte tento soubor a spusťte příkaz pack

```dotnetcli
dotnet pack
```

Tento příkaz vytvoří projekt a vytvoří balíček NuGet v tomto poli by měla být _pracovní\bin\Debug._

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Dále nainstalujte soubor sady `dotnet new -i PATH_TO_NUPKG_FILE` šablon pomocí příkazu.

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

Pokud jste nahráli balíček NuGet do informačního `dotnet new -i PACKAGEID` kanálu `PACKAGEID` NuGet, `<PackageId>` můžete použít příkaz, kde je stejný jako nastavení ze souboru _.csproj._ Toto ID balíčku je stejné jako identifikátor balíčku NuGet.

## <a name="uninstall-the-template-pack"></a>Odinstalace sady Template Pack

Bez ohledu na to, jak jste nainstalovali sadu šablon, a to buď se souborem _.nupkg_ přímo, nebo pomocí informačního kanálu NuGet, odebrání balíčku šablon je stejné. Použijte `<PackageId>` šablonu, kterou chcete odinstalovat. Seznam šablon, které jsou nainstalovány, můžete `dotnet new -u` získat spuštěním příkazu.

```dotnetcli
dotnet new -u
```

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
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

Spuštěním `dotnet new -u AdatumCorporation.Utility.Templates` odinstalujte šablonu. Příkaz `dotnet new` bude výstupem nápovědy informace, které by měly vynechat šablony, které jste dříve nainstalovali.

Blahopřejeme! nainstalovali a odinstalovali sadu šablon.

## <a name="next-steps"></a>Další kroky

Další informace o šablonách, z nichž většina se již naučila, najdete v článku Vlastní šablony pro nový článek [dotnet.](../tools/custom-templates.md)

* [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)
* [úložiště GitHub u dotnet/dotnet-template-samples GitHub](https://github.com/dotnet/dotnet-template-samples)
* [*template.json* schéma v obchodě Schema JSON](http://json.schemastore.org/template)
