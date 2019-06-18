---
title: Vlastních šablon pro dotnet nové
description: Další informace o vlastních šablon pro jakýkoli druh projektu .NET nebo soubory.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: d7e9c549ff132deb4682ba81ab5ff354d6cc1522
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169634"
---
# <a name="custom-templates-for-dotnet-new"></a>Vlastních šablon pro dotnet nové

[.NET Core SDK](https://www.microsoft.com/net/download/core) se dodává s mnoha šablony už nainstalované a připravené k použití. [ `dotnet new` Příkaz](dotnet-new.md) není pouze způsob, jak používat šablony, ale také jak nainstalovat a odinstalovat šablony. Od verze rozhraní .NET Core 2.0, můžete vytvořit vlastní šablony pro každý typ projektu, například aplikace, služby, nástroje nebo knihovny tříd. Můžete dokonce vytvořit šablonu, jejichž výstupem jsou jeden nebo více nezávislých souborech, jako je konfigurační soubor.

Vlastní šablony můžete nainstalovat z balíčku NuGet na jakékoli NuGet kanálu pomocí odkazu na NuGet *.nupkg* souboru přímo, nebo zadáním systémový adresář souboru, který obsahuje šablonu. Modul šablon nabízí funkce, které umožňují nahraďte hodnotami, zahrnutí a vyloučení souborů a provádění vlastního zpracování operací při použití šablony.

Modul šablon je typu open source a úložiště online kódu je na [dotnet/šablonování](https://github.com/dotnet/templating/) na Githubu. Přejděte [dotnet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples) úložiště pro ukázky šablon. Další šablony, včetně šablon od třetích stran, se nacházejí v [dostupných šablon pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na Githubu. Další informace o vytváření a používání vlastních šablon najdete v tématu [tom, jak vytvořit nové vlastní šablony pro dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [úložiště GitHub dotnet/šablonování Wiki](https://github.com/dotnet/templating/wiki).

Postupujte podle průvodce a vytvoření šablony najdete v tématu [vytvořit nové vlastní šablony pro dotnet](~/docs/core/tutorials/create-custom-template.md) kurzu.

### <a name="net-default-templates"></a>Výchozí šablony .NET

Při instalaci [.NET Core SDK](https://www.microsoft.com/net/download/core), obdržíte více než tucet předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolové aplikace, knihovny tříd, jednotky testování projektů, aplikace ASP.NET Core (včetně [Angular](https://angular.io/) a [React](https://facebook.github.io/react/) projekty) a konfigurační soubory. Chcete-li seznam integrovaných šablon, spusťte `dotnet new` příkaz `-l|--list` možnost:

```console
dotnet new --list
```

## <a name="configuration"></a>Konfiguraci

Šablona se skládá z následujících částí:

- Zdrojové soubory a složky.
- Konfigurační soubor (*template.json*).

### <a name="source-files-and-folders"></a>Zdrojové soubory a složky

Zdrojové soubory a složky patří libovolné soubory a složky šablona modul mají použít, když `dotnet new <TEMPLATE>` příkaz spustit. Modul šablon je navržen pro použití *spustitelné projekty* jako zdrojový kód k vytvoření projektů. To má několik výhod:

- Modul šablon nevyžaduje vložit speciální tokeny do zdrojového kódu.
- Soubory kódu nejsou speciální soubory nebo pro práci s modulem šablony žádným způsobem upravit. Nástroje, které standardně používáte při práci s projekty tedy také pracovat obsah šablony.
- Sestavení, spouštět a ladit vaše projekty ze šablony, stejně, jako je tomu u vašich projektů.
- Můžete rychle vytvořit šablonu z existujícího projektu pouhým přidáním *./.template.config/template.json* konfigurační soubor do projektu.

Soubory a složky uložené v šabloně nejsou omezené na formální typy projektů .NET. Zdrojové soubory a složky může obsahovat veškerý obsah, který chcete vytvořit při použití této šablony i v případě, že modul šablony vytvoří jenom jeden soubor jako výstup.

Soubory generované záznamem šablony lze upravit na základě logiky a jste zadali v nastavení *template.json* konfigurační soubor. Uživatel může přepsat tato nastavení pomocí předání možností `dotnet new <TEMPLATE>` příkazu. Běžným příkladem vlastní logiku poskytuje název pro třídu nebo proměnné ve zdrojovém souboru, který je nasazený v šabloně.

### <a name="templatejson"></a>template.json

*Template.json* soubor umístěn v *. template.config* složku v kořenovém adresáři šablony. Soubor obsahuje informace o konfiguraci pro modul šablony. Minimální požadavky na konfiguraci vyžaduje členů je znázorněno v následující tabulce, což je dostatečná pro vytvoření funkční šablony.

| Člen            | Type          | Popis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identifikátor URI           | Schéma JSON pro *template.json* souboru. Editory, které podporují schémat JSON povolte úpravy v editoru JSON funkce-li zadána schématu. Například [Visual Studio Code](https://code.visualstudio.com/) vyžaduje tento člen pro povolení technologie IntelliSense. Použijte hodnotu `http://json.schemastore.org/template`. |
| `author`          | odkazy řetězců        | Autor šablony. |
| `classifications` | Array(String) | Nula nebo více vlastností šablony, která uživatel může použít k vyhledávání pro něj najít šablonu. Klasifikace se také zobrazují v *značky* sloupce, když se objeví v seznamu šablon vytvořený pomocí `dotnet new -l|--list` příkazu. |
| `identity`        | odkazy řetězců        | Jedinečný název pro tuto šablonu. |
| `name`            | odkazy řetězců        | Název pro šablonu, kterou uživatelé měli vidět. |
| `shortName`       | odkazy řetězců        | Výchozí název Zkrácený tvar vlastností pro výběr šablonu, která se vztahuje na prostředí, kde název šablony je uživatel zadá, není vybrána přes grafické uživatelské rozhraní. Krátký název například je užitečné při použití šablony z příkazového řádku pomocí příkazů rozhraní příkazového řádku. |

Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template). Další informace o *template.json* souboru, najdete v článku [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Příklad

Například tady je složka šablony, která obsahuje dva soubory obsahu: *console.cs* a *readme.txt*. Všimněte si, že je k požadované složce s názvem trvat *. template.config* obsahující *template.json* souboru.

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

*Template.json* soubor bude vypadat nějak takto:

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

*Moje_šablona* Instalovatelné šablonovaný balíček je složka. Po instalaci této sady `shortName` jde použít s `dotnet new` příkazu. Například `dotnet new adatumconsole` by výstup `console.cs` a `readme.txt` soubory do aktuální složky.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Balení šablonu do balíčku NuGet (soubor nupkg)

Vlastní šablony, jsou vybavené [balíčku dotnet](dotnet-pack.md) příkazu a *.csproj* souboru. Alternativně [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) jde použít s [balíčku nuget](https://docs.microsoft.com/nuget/tools/cli-ref-pack) příkaz spolu s *souboru .nuspec* souboru. Ale NuGet vyžaduje rozhraní .NET Framework na Windows a [Mono](https://www.mono-project.com/) v Linuxu a MacOS.

*.Csproj* souboru se mírně liší od tradiční projekt kódu *.csproj* souboru. Mějte na paměti následující nastavení:

01. `<PackageType>` Nastavení přidán a nastavit na `Template`.
01. `<PackageVersion>` Přidán a nastaven na platné nastavení [číslo verze NuGet](/nuget/reference/package-versioning).
01. `<PackageId>` Nastavení přidán a nastavit na jedinečný identifikátor. Tento identifikátor slouží k odinstalaci šablonovaný balíček a používá NuGet informační kanály k registraci šablonovaný balíček.
01. Nastavení obecných metadat by měla být nastavena: `<Title>`, `<Authors>`, `<Description>`, a `<Tags>`.
01. `<TargetFramework>` Nastavení musí být nastaveno, i když se nepoužije binární soubor vytvořený pomocí šablony procesu. V následujícím příkladu je nastavena `netstandard2.0`.

Šablonovaný balíček ve formě *.nupkg* balíčku NuGet, vyžaduje uložení všechny šablony v *obsah* složky v rámci balíčku. Existuje několik dalších nastavení pro přidání do *.csproj* soubor a zkontrolujte, že generované *.nupkg* je možné nainstalovat jako šablonovaný balíček:

01. `<IncludeContentInPack>` Nastavená na `true` zahrnout všechny soubory projektu se nastaví jako **obsah** v balíčku NuGet.
01. `<IncludeBuildOutput>` Nastavená na `false` vyloučit všechny binární soubory generované kompilátorem z balíčku NuGet.
01. `<ContentTargetFolders>` Nastavená na `content`. Tím je zajištěno, že soubory nastavit jako **obsah** jsou uloženy v *obsah* složky v balíčku NuGet. Tato složka v balíčku NuGet je analyzován systémem šablony pro dotnet.

Snadný způsob, jak vyloučit všechny soubory kódu z kompilovaná pomocí šablony projektu je pomocí `<Compile Remove="**\*" />` uvnitř položky v souboru projektu `<ItemGroup>` elementu.

Snadný způsob, jak strukturovat váš balíček šablony je umístit všechny šablony do jednotlivé složky a potom každé šablony složky uvnitř *šablony* složku, která se nachází ve stejném adresáři jako vaše *.csproj* soubor. Tímto způsobem můžete pomocí jednoho projektu položky zahrnout všechny soubory a složky v *šablony* jako **obsah**. Uvnitř `<ItemGroup>` elementu, vytvořit `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` položky.

Tady je příklad *.csproj* souboru, který následuje všechny výše uvedené pokyny. Jeho balíčky *šablony* podřízené složky do *obsah* balíček složky a vyloučí všechny soubory kódu z kompilován.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <Tags>dotnet-new;templates;contoso</Tags>
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

Následující příklad ukazuje strukturu souborů a složek pomocí *.csproj* vytvořit balíček šablon. *MyDotnetTemplates.csproj* souboru a *šablony* složky jsou umístěné v kořenovém adresáři s názvem *project_folder*. *Šablony* složka obsahuje dvě šablony *mytemplate1* a *mytemplate2*. Každá šablona má soubory obsahu a *. template.config* složka s *template.json* konfiguračního souboru.

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

Použití [dotnet nové -i |--nainstalovat](dotnet-new.md) příkaz k instalaci balíčku.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li nainstalovat šablony z balíčku NuGet uloženou v nuget.org

Použijte identifikátor balíčku NuGet k instalaci balíčku šablony.

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Chcete-li nainstalovat šablony ze souboru místní nupkg

Zadejte cestu k *.nupkg* soubor balíčku NuGet.

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Chcete-li nainstalovat šablony z adresáře systému souborů

Šablony si můžete nainstalovat pomocí složky šablony, jako *mytemplate1* složky jako v předchozím příkladu. Zadejte cestu ke složce aplikace *. template.config* složky. Cesta k adresáři šablony nemusí být absolutní. Absolutní cesta je však nutné odinstalovat šablonu, která je nainstalovaná ze složky.

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Získání seznamu nainstalovaných šablon

Příkaz odinstalace, bez jakékoli další parametry, zobrazí se seznam všech nainstalovaných šablon.

```console
dotnet new -u
```

Tento příkaz vrátí podobně jako následující výstup:

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

První úroveň položky po `Currently installed items:` jsou identifikátory použitými v odinstalaci šablony. A v příkladu výše `Microsoft.DotNet.Common.ItemTemplates` a `Microsoft.DotNet.Common.ProjectTemplates.3.0` jsou uvedeny. Pokud šablona byla nainstalována pomocí cestu systému souborů, bude tento identifikátor cesta ke složce *. template.config* složky.

## <a name="uninstalling-a-template"></a>Odinstalace šablony

Použití [dotnet nové -u |--odinstalovat](dotnet-new.md) příkaz pro odinstalaci balíčku.

Pokud balíček nainstaloval kanál NuGet nebo parametrem *.nupkg* přímo soubor, zadejte identifikátor.

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

Pokud zadáte cestu k byl nainstalován balíček *. template.config* složky, použít **absolutní** cestu k odinstalaci balíčku. Zobrazí se absolutní cesta šablony v výstup poskytovaný `dotnet new -u` příkazu. Další informace najdete v tématu [získání seznamu nainstalovaných šablon](#get-a-list-of-installed-templates) výše uvedené části.

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Vytvořte projekt pomocí vlastní šablony

Po instalaci šablony, použijte šablonu pomocí provádí `dotnet new <TEMPLATE>` příkaz stejně jako u jiných předem nainstalovaných šablon. Můžete také určit [možnosti](dotnet-new.md#options) k `dotnet new` příkazu, včetně možnosti specifické pro šablony jste nakonfigurovali v nastavení šablony. Zadejte krátký název šablony přímo k příkazu:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastní šablony pro dotnet new (kurz)](../tutorials/create-custom-template.md)
- [úložiště GitHub DotNet/šablonování Wiki](https://github.com/dotnet/templating/wiki)
- [úložiště GitHub DotNet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)
- [Jak vytvořit nové vlastní šablony pro dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* schématu na Store schématu JSON](http://json.schemastore.org/template)
