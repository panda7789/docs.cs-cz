---
title: Vytvořit novou sadu šablon pro dotnet
description: Zjistěte, jak vytvořit soubor csproj, který se sestaví balíček šablon pro nový příkaz dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877183"
---
# <a name="tutorial-create-a-template-pack"></a>Kurz: Vytvoření balíčku šablony

S .NET Core můžete vytvořit a nasadit šablon, které generují projektů, souborů, dokonce i prostředky. Tento kurz je třetí částí série, která vás naučí, jak vytvořit, instalaci a odinstalaci, šablony pro použití se službou `dotnet new` příkazu.

V této části této série se dozvíte jak:

> [!div class="checklist"]
> * Vytvoření projektu _.csproj* k vytvoření balíčku šablony
> * Konfigurovat soubor projektu pro balení
> * Instalace šablony ze souboru balíčku NuGet
> * Odinstalace šablony podle ID balíčku

## <a name="prerequisites"></a>Požadavky

* Kompletní [1. část](cli-templates-create-item-template.md) a [2. část](cli-templates-create-project-template.md) této série kurzů.

  Tento kurz používá dvě šablony vytvořené v prvních dvou částech tohoto kurzu. Je možné, můžete použít jinou šablonu, za předpokladu, zkopírujte šablony jako složku do _working\templates\\_  složky.

* Otevřete terminál a přejděte _working\templates\\_  složky.

## <a name="create-a-template-pack-project"></a>Vytvořte projekt balíčku šablony

Balíček šablony je jedna nebo více šablon zabalené do souboru. Při instalaci nebo odinstalaci aktualizací Service pack, jsou všechny šablony, které jsou součástí této sady přidaly nebo odebraly v uvedeném pořadí. Předchozí části této série kurzů pouze pracovali jednotlivé šablony. Sdílení šablony nezabalených, budete muset zkopírovat do složky šablony a nainstalovat prostřednictvím této složky. Protože šablonovaný balíček může mít více než jedna šablona v něm a je jeden soubor, sdílení je jednodušší.

Šablonované balíčky jsou reprezentované prostřednictvím balíčku NuGet ( _.nupkg_) soubor. A stejně jako libovolný balíček NuGet můžete nahrát šablonovaný balíček NuGet informačního kanálu. `dotnet new -i` Příkaz podporuje instalaci šablonovaný balíček z informačního kanálu balíčku NuGet. Kromě toho můžete nainstalovat balíček ze šablon _.nupkg_ přímo soubor.

Obvykle použijete C# soubor projektu a kompilaci kódu a vytvoří binární soubor. Ale projektu lze také generovat balíček šablon. Změnou nastavení _.csproj_, můžete zabránit kompilaci libovolný kód a místo toho zahrnout všechny prostředky k šablonám jako prostředky. Když tento projekt se vytvořil, vytvoří šablonovaný balíček balíček NuGet.

Bude obsahovat pack, kterou vytvoříte [šablony položky](cli-templates-create-item-template.md) a [balíček šablony](cli-templates-create-project-template.md) předtím vytvořili. Protože jsme seskupit dvou šablon do _working\templates\\_  složky, můžeme použít _práce_ složku pro _.csproj_ souboru.

V terminálu přejděte _práce_ složky. Vytvořte nový projekt a nastavte její název na `templatepack` a složku výstupu do aktuální složky.

```console
dotnet new console -n templatepack -o .
```

`-n` Sady parametrů _.csproj_ název souboru k _templatepack.csproj_ a `-o` parametry vytvoří soubory v aktuálním adresáři. Zobrazí se výsledek podobný následující výstup.

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Dále otevřete _templatepack.csproj_ souboru ve svém oblíbeném editoru a nahraďte obsah následujícím XML:

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

`<PropertyGroup>` Nastavení v souboru XML výše je rozdělená do tří skupin. První skupina se zabývá vlastnosti požadované pro balíček NuGet. Tři `<Package` nastavení muset s NuGet vlastnosti balíčku k identifikaci vašeho balíčku na informačního kanálu NuGet. Konkrétně `<PacakgeId>` hodnota slouží k odinstalaci šablonovaný balíček s jedním názvem, ne cestu k adresáři. To lze také nainstalovat šablonovaný balíček z informačního kanálu NuGet. Zbývající nastavení, jako `<Title>` a `<Tags>` muset s metadaty zobrazené na NuGet informačního kanálu. Další informace o nastavení NuGet naleznete v tématu [vlastnosti nástroje MSBuild a NuGet](/nuget/reference/msbuild-targets).

`<TargetFramework>` Nastavení musí být nastavené tak, aby při spuštění příkazu pack ke kompilaci a aktualizací Service pack projekt bude správně fungovat MSBuild.

Poslední tři nastavení muset nakonfigurovat projekt správně mají být zahrnuty šablony do odpovídající složky v balíčku NuGet pack při jeho vytváření.

`<ItemGroup>` Obsahuje dvě nastavení. Nejprve je potřeba `<Content>` nastavení zahrnuje všechno, co v _šablony_ složky jako obsah. Má také nastavit nevylučovala žádná _bin_ složky nebo _obj_ složky zabránit zkompilovaného kódu (Pokud je testován a kompilaci šablony) nebudou zahrnuty. Druhý, `<Compile>` vyloučí všechny soubory s kódem v kompilaci bez ohledu na to, kde jsou umístěny. Toto nastavení brání použity k vytvoření balíčku šablony v pokusu o zkompilování kódu v projektu _šablony_ hierarchii složek.

## <a name="build-and-install"></a>Sestavení a instalace

Uložte tento soubor a pak spusťte příkaz pack

```console
dotnet pack
```

Tento příkaz se sestavení projektu a vytvořit by měla být v tomto balíčku NuGet _working\bin\Debug_ složky.

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

V dalším kroku instalovat balíček soubor šablony s `dotnet new -i PATH_TO_NUPKG_FILE` příkazu.

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

Pokud jste nahráli do informačního kanálu NuGet balíčku NuGet, můžete použít `dotnet new -i PACKAGEID` příkazu, kde `PACKAGEID` je stejné jako `<PackageId>` nastavení z _.csproj_ souboru. Toto ID balíčku je stejný jako identifikátor balíčku NuGet.

## <a name="uninstall-the-template-pack"></a>Odinstalace balíčku šablony

Bez ohledu na to, jak jste nainstalovali sadu šablon, buď pomocí _.nupkg_ souboru přímo nebo pomocí NuGet informačního kanálu, odebírá se balíček šablon jsou stejné. Použití `<PackageId>` šablony, kterou chcete odinstalovat. Můžete získat seznam šablon, které jsou nainstalovány spuštěním `dotnet new -u` příkazu.

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

Spustit `dotnet new -u AdatumCorporation.Utility.Templates` odinstalace šablony. `dotnet new` Příkaz na výstupu informace nápovědy, která by vynechání šablony, které jste dříve nainstalovali.

Blahopřejeme! jste instaluje a odinstaluje balíček šablon. 

## <a name="next-steps"></a>Další kroky

Další informace o šablony, většina z nich jste už zjistili, najdete v článku [vlastních šablon pro dotnet nové](../tools/custom-templates.md) článku.

* [úložiště GitHub DotNet/šablonování Wiki](https://github.com/dotnet/templating/wiki)
* [úložiště GitHub DotNet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)
* [*Template.JSON* schématu na Store schématu JSON](http://json.schemastore.org/template)
