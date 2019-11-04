---
title: Vlastní šablony pro dotnet New
description: Seznamte se s vlastními šablonami pro jakýkoli typ projektu nebo souborů .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420881"
---
# <a name="custom-templates-for-dotnet-new"></a>Vlastní šablony pro dotnet New

[.NET Core SDK](https://dotnet.microsoft.com/download) obsahuje mnoho šablon, které jsou už nainstalované a připravené k použití. [Příkaz`dotnet new`](dotnet-new.md) nepoužívá pouze způsob, jak šablonu používat, ale také postup instalace a odinstalace šablon. Počínaje rozhraním .NET Core 2,0 můžete vytvořit vlastní šablony pro jakýkoli typ projektu, například aplikace, služby, nástroje nebo knihovny tříd. Můžete dokonce vytvořit šablonu, která bude vytvářet výstup jednoho nebo více nezávislých souborů, například konfiguračního souboru.

Vlastní šablony můžete nainstalovat z balíčku NuGet v jakémkoli kanálu NuGet, odkazování na soubor NuGet *. nupkg* nebo zadáním adresáře systému souborů, který šablonu obsahuje. Modul šablon nabízí funkce, které umožňují nahradit hodnoty, zahrnout a vyloučit soubory a provádět vlastní operace zpracování při použití šablony.

Modul šablon je open source a online úložiště kódu je v [dotnet/šablonování](https://github.com/dotnet/templating/) na GitHubu. Ukázky šablon najdete v úložišti [dotnet/dotnet-Template-Samples](https://github.com/dotnet/dotnet-template-samples) . Další šablony, včetně šablon od třetích stran, najdete v [dostupných šablonách pro dotnet New](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na GitHubu. Další informace o vytváření a používání vlastních šablon najdete v tématu [jak vytvořit vlastní šablony pro dotnet New](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [wiki pro úložiště GitHubu a šablonování](https://github.com/dotnet/templating/wiki).

Pokud chcete postupovat podle návodu a vytvořit šablonu, přečtěte si článek [Vytvoření vlastní šablony pro dotnet nový](../tutorials/cli-templates-create-item-template.md) kurz.

### <a name="net-default-templates"></a>Výchozí šablony rozhraní .NET

Při instalaci [.NET Core SDK](https://dotnet.microsoft.com/download)obdržíte spoustu předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolových aplikací, knihoven tříd, projektů testování částí, ASP.NET Corech aplikací (včetně [úhlů](https://angular.io/) a [reagujících](https://facebook.github.io/react/) projektů). a konfigurační soubory. Pokud chcete zobrazit seznam předdefinovaných šablon, spusťte příkaz `dotnet new` s možností `-l|--list`:

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a>Konfigurace

Šablona se skládá z následujících částí:

- Zdrojové soubory a složky.
- Konfigurační soubor (*template. JSON*).

### <a name="source-files-and-folders"></a>Zdrojové soubory a složky

Zdrojové soubory a složky zahrnují libovolné soubory a složky, které má modul šablon použít při spuštění příkazu `dotnet new <TEMPLATE>`. Modul šablon je navržen tak, aby používal *projekty spustitelný* jako zdrojový kód k výrobě projektů. Má několik výhod:

- Modul šablon nevyžaduje vložení speciálních tokenů do zdrojového kódu vašeho projektu.
- Soubory s kódem nejsou speciální soubory ani upravovány jakýmkoli způsobem pro práci s modulem šablon. Proto nástroje, které běžně používáte při práci s projekty, fungují také s obsahem šablony.
- Projekty šablon můžete sestavovat, spouštět a ladit stejně jako u všech ostatních projektů.
- Můžete rychle vytvořit šablonu z existujícího projektu pouhým přidáním konfiguračního souboru *./.template.config/Template.JSON* do projektu.

Soubory a složky uložené v šabloně nejsou omezeny na formální typy projektů .NET. Zdrojové soubory a složky mohou být tvořeny jakýmkoli obsahem, který chcete vytvořit při použití šablony, a to i v případě, že modul šablon vytvoří jako výstup pouze jeden soubor.

Soubory vygenerované šablonou lze upravit na základě logiky a nastavení, které jste zadali v konfiguračním souboru *template. JSON* . Uživatel může tato nastavení přepsat předáním možností `dotnet new <TEMPLATE>` příkazu. Běžným příkladem vlastní logiky je poskytnutí názvu pro třídu nebo proměnnou v souboru kódu, který je nasazen šablonou.

### <a name="templatejson"></a>Template. JSON

Soubor *template. JSON* je umístěný ve složce *. template. config* v kořenovém adresáři šablony. Soubor poskytuje konfigurační informace modulu šablony. Minimální konfigurace vyžaduje, aby členové byli uvedeni v následující tabulce, která je dostačující k vytvoření funkční šablony.

| Člen            | Typ          | Popis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identifikátor URI           | Schéma JSON pro soubor *template. JSON* . Editory podporující schémata JSON povolují funkce úprav JSON při určení schématu. Například [Visual Studio Code](https://code.visualstudio.com/) vyžaduje, aby tento člen povoloval technologii IntelliSense. Použijte hodnotu `http://json.schemastore.org/template`. |
| `author`          | odkazy řetězců        | Autor šablony |
| `classifications` | Array (řetězec) | Nula nebo více vlastností šablony, kterou může uživatel použít k vyhledání šablony při jejím hledání. Klasifikace se také zobrazí ve sloupci *značky* , když se objeví v seznamu šablon vytvořených pomocí příkazu `dotnet new -l|--list`. |
| `identity`        | odkazy řetězců        | Jedinečný název pro tuto šablonu. |
| `name`            | odkazy řetězců        | Název šablony, kterou by uživatelé měli vidět. |
| `shortName`       | odkazy řetězců        | Výchozí zkrácený název pro výběr šablony, která se vztahuje na prostředí, kde je název šablony určený uživatelem, který není vybraný prostřednictvím grafického uživatelského rozhraní. Krátký název je například užitečný při použití šablon z příkazového řádku s příkazy CLI. |

Úplné schéma pro soubor *template. JSON* najdete v [úložišti schémat JSON](http://json.schemastore.org/template). Další informace o souboru *template. JSON* najdete v tématu [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Příklad

Tady je například složka šablony, která obsahuje dva soubory obsahu: *Console.cs* a *Readme. txt*. Všimněte si, že existuje požadovaná složka s názvem *. template. config* , která obsahuje soubor *template. JSON* .

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

Soubor *template. JSON* vypadá takto:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

Složka *MyTemplate* je instalovatelný balíček šablon. Po instalaci balíčku se `shortName` dá použít s příkazem `dotnet new`. Například `dotnet new adatumconsole` by měl výstup `console.cs` a `readme.txt` souborů do aktuální složky.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Balení šablony do balíčku NuGet (soubor nupkg)

Vlastní šablona je zabalena pomocí příkazu [dotnet Pack](dotnet-pack.md) a souboru *. csproj* . Případně lze [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) použít společně s příkazem [balíčku NuGet](https://docs.microsoft.com/nuget/tools/cli-ref-pack) spolu se souborem *. nuspec* . NuGet ale vyžaduje .NET Framework ve Windows a [mono](https://www.mono-project.com/) v systémech Linux a MacOS.

Soubor *. csproj* se mírně liší od tradičního souboru Code-Project *. csproj* . Všimněte si následujícího nastavení:

01. Nastavení `<PackageType>` se přidá a nastaví na `Template`.
01. Nastavení `<PackageVersion>` se přidá a nastaví na platné [číslo verze NuGet](/nuget/reference/package-versioning).
01. Nastavení `<PackageId>` se přidá a nastaví na jedinečný identifikátor. Tento identifikátor se používá k odinstalaci balíčku šablon a používá se v kanálech NuGet k registraci balíčku šablon.
01. Měla by být nastavena obecná nastavení metadat: `<Title>`, `<Authors>`, `<Description>`a `<PackageTags>`.
01. Nastavení `<TargetFramework>` musí být nastavené, i když se binární soubor vytvořený procesem šablony nepoužívá. V následujícím příkladu je nastaveno na `netstandard2.0`.

Sada šablon, ve formě balíčku NuGet *. nupkg* , vyžaduje, aby všechny šablony byly uloženy ve složce *obsahu* v rámci balíčku. Je k dispozici několik dalších nastavení pro přidání do souboru *. csproj* , aby bylo zajištěno, že vygenerovaný soubor *. nupkg* může být nainstalován jako balíček šablony:

01. Nastavení `<IncludeContentInPack>` je nastaveno na `true`, aby obsahovalo všechny soubory, které projekt nastaví jako **obsah** v balíčku NuGet.
01. Nastavení `<IncludeBuildOutput>` je nastavené na hodnotu `false`, aby se vyloučily všechny binární soubory vygenerované kompilátorem z balíčku NuGet.
01. Nastavení `<ContentTargetFolders>` je nastaveno na hodnotu `content`. Tím se zajistí, že soubory nastavené jako **obsah** budou uloženy ve složce *obsahu* v balíčku NuGet. Tato složka v balíčku NuGet je analyzována systémem šablony dotnet.

Snadný způsob, jak vyloučit všechny soubory kódu z kompilace pomocí projektu šablony, je použití položky `<Compile Remove="**\*" />` v souboru projektu v rámci `<ItemGroup>` elementu.

Snadný způsob, jak strukturovat balíček šablon, je umístit všechny šablony do jednotlivých složek a následně každou složku šablony do složky *šablony* , která je umístěna ve stejném adresáři jako soubor *. csproj* . Tímto způsobem můžete použít jednu položku projektu pro zahrnutí všech souborů a složek v *šablonách* jako **obsah**. V prvku `<ItemGroup>` vytvořte položku `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />`.

Zde je příklad souboru *. csproj* , který následuje za všemi výše uvedenými pokyny. Sbalí podřízenou složku *šablony* do složky balíčku *obsahu* a vyloučí všechny soubory kódu, které se mají kompilovat.

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

Následující příklad ukazuje strukturu souborů a složek použití souboru *. csproj* k vytvoření sady šablon. Soubor *MyDotnetTemplates. csproj* a složky *šablon* jsou umístěny v kořenu adresáře s názvem *project_folder*. Složka *Templates* obsahuje dvě šablony, *mytemplate1* a *mytemplate2*. Každá šablona má soubory obsahu a složku *. template. config* pomocí konfiguračního souboru *template. JSON* .

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a>Instalace šablony

K instalaci balíčku použijte příkaz [dotnet New-i |--Install](dotnet-new.md) .

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Instalace šablony z balíčku NuGet uloženého na nuget.org

K instalaci balíčku šablony použijte identifikátor balíčku NuGet.

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Instalace šablony z místního souboru nupkg

Zadejte cestu k souboru balíčku NuGet *. nupkg* .

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Instalace šablony z adresáře systému souborů

Šablony lze nainstalovat ze složky šablony, jako je například složka *mytemplate1* z výše uvedeného příkladu. Zadejte cestu ke složce ve složce *. template. config* . Cesta k adresáři šablon nemusí být absolutní. K odinstalaci šablony, která je nainstalovaná ze složky, je ale nutná absolutní cesta.

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Získání seznamu nainstalovaných šablon

Příkaz uninstall bez dalších parametrů zobrazí seznam všech nainstalovaných šablon.

```dotnetcli
dotnet new -u
```

Tento příkaz vrátí něco podobného následujícímu výstupu:

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

První úroveň položek po `Currently installed items:` jsou identifikátory používané při odinstalaci šablony. A v příkladu výše jsou uvedeny `Microsoft.DotNet.Common.ItemTemplates` a `Microsoft.DotNet.Common.ProjectTemplates.3.0`. Pokud byla šablona nainstalována pomocí cesty systému souborů, tento identifikátor bude cestou složky složky *. template. config* .

## <a name="uninstalling-a-template"></a>Odinstalace šablony

K odinstalaci balíčku použijte příkaz [dotnet New-u |--Uninstall](dotnet-new.md) .

Pokud byl balíček nainstalován buď pomocí kanálu NuGet, nebo přímo v souboru *. nupkg* , zadejte identifikátor.

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

Pokud byl balíček nainstalovaný zadáním cesty ke složce *. template. config* , použijte k odinstalaci balíčku tuto **absolutní** cestu. Ve výstupu poskytnutém příkazem `dotnet new -u` lze zobrazit absolutní cestu šablony. Další informace najdete v části [získání seznamu nainstalovaných šablon](#get-a-list-of-installed-templates) výše.

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Vytvoření projektu pomocí vlastní šablony

Po instalaci šablony použijte příkaz `dotnet new <TEMPLATE>` stejným způsobem jako u jakékoli jiné předem instalované šablony. Můžete také zadat [Možnosti](dotnet-new.md#options) příkazu `dotnet new`, včetně možností specifických pro šablonu, které jste nakonfigurovali v nastavení šablony. Zadejte krátký název šablony přímo do příkazu:

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastní šablony pro dotnet New (kurz)](../tutorials/cli-templates-create-item-template.md)
- [dotnet/šablonování wiki úložiště GitHub](https://github.com/dotnet/templating/wiki)
- [dotnet/dotnet-Template-Samples – úložiště GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Jak vytvořit vlastní šablony pro dotnet New](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*template. JSON* – schéma v ÚLOŽIŠTI schémat JSON](http://json.schemastore.org/template)
