---
title: Vlastní šablony pro dotnet nové
description: Přečtěte si o vlastních šablonách pro jakýkoli typ projektu nebo souborů .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420881"
---
# <a name="custom-templates-for-dotnet-new"></a>Vlastní šablony pro dotnet nové

Sada [.NET Core SDK](https://dotnet.microsoft.com/download) je dodávána s mnoha šablonami, které jsou již nainstalovány a připraveny k použití. [ `dotnet new` Příkaz](dotnet-new.md) není pouze způsob použití šablony, ale také způsob instalace a odinstalace šablon. Počínaje rozhraním .NET Core 2.0 můžete vytvořit vlastní šablony pro libovolný typ projektu, například pro aplikaci, službu, nástroj nebo knihovnu tříd. Můžete dokonce vytvořit šablonu, která vypíše jeden nebo více nezávislých souborů, například konfigurační soubor.

Vlastní šablony z balíčku NuGet můžete nainstalovat do libovolného informačního kanálu NuGet, odkazováním přímo na soubor NuGet *.nupkg* nebo zadáním adresáře systému souborů, který obsahuje šablonu. Modul šablony nabízí funkce, které umožňují nahradit hodnoty, zahrnout a vyloučit soubory a provádět vlastní operace zpracování při použití šablony.

Modul šablony je open source a úložiště online kódu je na [dotnet/templating](https://github.com/dotnet/templating/) na GitHubu. Navštivte [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo pro ukázky šablon. Další šablony, včetně šablon od třetích stran, najdete na [dostupné šablony pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na GitHubu. Další informace o vytváření a používání vlastních šablon najdete v tématu [Jak vytvořit vlastní šablony pro dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).

Pokud chcete postupovat podle návodu a vytvořit šablonu, přečtěte si viz [Vytvoření vlastní šablony pro dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.

### <a name="net-default-templates"></a>Výchozí šablony rozhraní .NET

Při instalaci [sady .NET Core SDK](https://dotnet.microsoft.com/download)získáte více než tucet předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolových aplikací, knihoven tříd, projektů testování částí, aplikací ASP.NET Core (včetně [projektů Angular](https://angular.io/) a [React)](https://facebook.github.io/react/) a konfiguračních souborů. Chcete-li zobrazit seznam předdefinovaných `dotnet new` šablon, `-l|--list` spusťte příkaz s možností:

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a>Konfigurace

Šablona se skládá z následujících částí:

- Zdrojové soubory a složky.
- Konfigurační soubor (*template.json*).

### <a name="source-files-and-folders"></a>Zdrojové soubory a složky

Zdrojové soubory a složky obsahují libovolné soubory a složky, které chcete, aby modul šablony používal při spuštění příkazu. `dotnet new <TEMPLATE>` Modul šablony je navržen tak, aby používal *spustitelné projekty* jako zdrojový kód k vytváření projektů. To má několik výhod:

- Modul šablony nevyžaduje, abyste do zdrojového kódu projektu vnesli speciální tokeny.
- Soubory kódu nejsou speciální soubory nebo upraveny v žádném případě pracovat s šablonou motoru. Nástroje, které běžně používáte při práci s projekty, tedy pracují také s obsahem šablony.
- Sestavení, spuštění a ladění projektů šablony stejně jako u jiných projektů.
- Šablonu z existujícího projektu můžete rychle vytvořit pouhým přidáním konfiguračního souboru *./.template.config/template.json* do projektu.

Soubory a složky uložené v šabloně nejsou omezeny na formální typy projektů .NET. Zdrojové soubory a složky se mohou skládat z libovolného obsahu, který chcete vytvořit při použití šablony, i když modul šablony vytvoří jako výstup pouze jeden soubor.

Soubory generované šablonou lze upravit na základě logiky a nastavení, které jste zadali v konfiguračním souboru *template.json.* Uživatel může přepsat tato nastavení předáním `dotnet new <TEMPLATE>` možnosti příkazu. Běžným příkladem vlastní logiky je poskytnutí názvu pro třídu nebo proměnnou v souboru kódu, který je nasazen šablonou.

### <a name="templatejson"></a>šablona.json

Soubor *template.json* je umístěn do složky *.template.config* v kořenovém adresáři šablony. Soubor poskytuje informace o konfiguraci modulu šablony. Minimální konfigurace vyžaduje členy uvedené v následující tabulce, která je dostatečná k vytvoření funkční šablony.

| Člen            | Typ          | Popis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identifikátor URI           | Schéma JSON pro soubor *template.json.* Editory, které podporují schémata JSON, umožňují funkce úprav JSON, pokud je zadáno schéma. [Například Visual Studio Code](https://code.visualstudio.com/) vyžaduje tento člen povolit IntelliSense. Použijte hodnotu `http://json.schemastore.org/template`. |
| `author`          | řetězec        | Autor šablony. |
| `classifications` | array(řetězec) | Nula nebo více charakteristik šablony, které může uživatel použít k vyhledání šablony při hledání. Klasifikace se také zobrazí ve sloupci *Tagy,* když se zobrazí `dotnet new -l|--list` v seznamu šablon vytvořených pomocí příkazu. |
| `identity`        | řetězec        | Jedinečný název této šablony. |
| `name`            | řetězec        | Název šablony, kterou by měli uživatelé vidět. |
| `shortName`       | řetězec        | Výchozí zkrácený název pro výběr šablony, která se vztahuje na prostředí, kde je název šablony určen uživatelem, není vybrán pomocí grafického uživatelského rozhraní. Krátký název je například užitečný při použití šablon z příkazového řádku s příkazy příkazového řádku. |

Úplné schéma souboru *template.json* se nachází v [úložišti schématu JSON](http://json.schemastore.org/template). Další informace o souboru *template.json* naleznete [na wiki dotnet templating](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Příklad

Zde je například složka šablony, která obsahuje dva soubory obsahu: *console.cs* a *readme.txt*. Všimněte si, že existuje požadovaná složka s názvem *.template.config,* která obsahuje soubor *template.json.*

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

Soubor *template.json* vypadá takto:

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

Složka *mytemplate* je instalovatelná sada šablon. Jakmile je balíček `shortName` nainstalován, lze `dotnet new` jej použít pomocí příkazu. Například `dotnet new adatumconsole` by výstup `console.cs` `readme.txt` a soubory do aktuální složky.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Balení šablony do balíčku NuGet (soubor nupkg)

Vlastní šablona je plná příkazu [dotnet pack](dotnet-pack.md) a souboru *.csproj.* Alternativně [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) lze použít s [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) příkaz spolu se souborem *.nuspec.* NuGet však vyžaduje rozhraní .NET Framework v systému Windows a [Mono](https://www.mono-project.com/) v systémech Linux a MacOS.

Soubor *.csproj* se mírně liší od tradičního souboru *code-project .csproj.* Všimněte si těchto nastavení:

01. Nastavení `<PackageType>` je přidáno `Template`a nastaveno na .
01. Toto `<PackageVersion>` nastavení je přidáno a nastaveno na platné [číslo verze NuGet](/nuget/reference/package-versioning).
01. Nastavení `<PackageId>` je přidáno a nastaveno na jedinečný identifikátor. Tento identifikátor se používá k odinstalaci balíčku šablon a používá se nugetské kanály k registraci sady šablon.
01. Měla by být nastavena `<Title>` `<Authors>`obecná `<Description>`nastavení `<PackageTags>`metadat: , , a .
01. Nastavení `<TargetFramework>` musí být nastaveno, i když se nepoužije binární soubor vytvořený procesem šablony. V níže uvedeném příkladu `netstandard2.0`je nastavena na .

Balíček šablon ve formě balíčku *.nupkg* NuGet vyžaduje, aby všechny šablony byly uloženy ve složce *obsahu* v rámci balíčku. Existuje několik dalších nastavení, které je třeba přidat do souboru *.csproj,* abyste zajistili, že generovaná *.nupkg* může být nainstalována jako balíček šablon:

01. Nastavení `<IncludeContentInPack>` je nastaveno tak, aby `true` zahrnovalo všechny soubory, které projekt nastaví jako **obsah** v balíčku NuGet.
01. Nastavení `<IncludeBuildOutput>` je nastaveno tak, aby `false` vyloučilo všechny binární soubory generované kompilátorem z balíčku NuGet.
01. Nastavení `<ContentTargetFolders>` je nastaveno na . `content` Tím zajistíte, že soubory nastavené jako **obsah** jsou uloženy ve složce *obsahu* v balíčku NuGet. Tato složka v balíčku NuGet je analyzována systémem šablony dotnet.

Snadný způsob, jak vyloučit všechny soubory kódu z kompilovány `<Compile Remove="**\*" />` projektem šablony je `<ItemGroup>` pomocí položky v souboru projektu, uvnitř prvku.

Snadný způsob, jak strukturovat sadu šablon, je umístit všechny šablony do jednotlivých složek a potom každou složku šablony uvnitř složky *šablon,* která je umístěna ve stejném adresáři jako soubor *.csproj.* Tímto způsobem můžete použít jednu položku projektu k zahrnutí všech souborů a složek do *šablon* jako **obsahu**. Uvnitř `<ItemGroup>` prvku vytvořte `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` položku.

Zde je příklad *souboru .csproj,* který se řídí všemi výše uvedenými pokyny. Zabalí *podřízenou* složku šablon do složky balíčku *obsahu* a vyloučí z kompilován libovolný soubor kódu.

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

Následující příklad ukazuje strukturu souborů a složek pomocí *souboru .csproj* k vytvoření balíčku šablon. Složka *MyDotnetTemplates.csproj* souboru a šablon jsou *umístěny* v kořenovém adresáři adresáře s názvem *project_folder*. Složka *šablony* obsahuje dvě šablony, *mytemplate1* a *mytemplate2*. Každá šablona obsahuje soubory obsahu a složku *.template.config* s konfiguračním souborem *template.json.*

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

K instalaci balíčku použijte příkaz [dotnet new -i|--install.](dotnet-new.md)

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Instalace šablony z balíčku NuGet uloženého v nuget.org

K instalaci balíčku šablony použijte identifikátor balíčku NuGet.

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Instalace šablony z místního souboru nupkg

Zadejte cestu k souboru balíčku *.nupkg* NuGet.

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Instalace šablony z adresáře systému souborů

Šablony lze nainstalovat ze složky šablony, například ze složky *mytemplate1* z výše uvedeného příkladu. Zadejte cestu ke složce *.template.config.* Cesta k adresáři šablony nemusí být absolutní. K odinstalaci šablony, která je nainstalována ze složky, je však vyžadována absolutní cesta.

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Získání seznamu nainstalovaných šablon

Příkaz odinstalovat bez dalších parametrů zobrazí seznam všech nainstalovaných šablon.

```dotnetcli
dotnet new -u
```

Tento příkaz vrátí něco podobného následující výstup:

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

První úroveň položek `Currently installed items:` po jsou identifikátory používané při odinstalaci šablony. A ve výše `Microsoft.DotNet.Common.ItemTemplates` uvedeném příkladu, a `Microsoft.DotNet.Common.ProjectTemplates.3.0` jsou uvedeny. Pokud byla šablona nainstalována pomocí cesty k systému souborů, bude tento identifikátor cesta ke složce *.template.config.*

## <a name="uninstalling-a-template"></a>Odinstalace šablony

Chcete-li odinstalovat balíček, použijte příkaz [dotnet new -u|--uninstall.](dotnet-new.md)

Pokud byl balíček nainstalován zdrojem NuGet nebo přímo souborem *.nupkg,* zadejte identifikátor.

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

Pokud byl balíček nainstalován zadáním cesty ke složce *.template.config,* odinstalujte balíček pomocí **této absolutní** cesty. Absolutní cesta šablony můžete vidět ve výstupu poskytnutém `dotnet new -u` příkazem. Další informace naleznete v části [Získání seznamu nainstalovaných šablon](#get-a-list-of-installed-templates) výše.

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Vytvoření projektu pomocí vlastní šablony

Po instalaci šablony použijte šablonu provedením `dotnet new <TEMPLATE>` příkazu stejně jako u jakékoli jiné předinstalované šablony. Můžete také určit [možnosti](dotnet-new.md#options) příkazu, `dotnet new` včetně možností specifických pro šablonu, které jste nakonfigurovali v nastavení šablony. Zadej krátký název šablony přímo do příkazu:

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Viz také

- [Vytvoření vlastní šablony pro dotnet new (kurz)](../tutorials/cli-templates-create-item-template.md)
- [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)
- [úložiště GitHub u dotnet/dotnet-template-samples GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Jak vytvořit vlastní šablony pro dotnet nové](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*template.json* schéma v obchodě Schema JSON](http://json.schemastore.org/template)
