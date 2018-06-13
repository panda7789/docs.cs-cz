---
title: Vlastní šablony pro nové dotnet.
description: Další informace o vlastních šablon pro jakýkoli typ rozhraní .NET projektu nebo soubory.
author: guardrex
ms.author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: fe888d0bfeeb51d77b73ec481b93fec9b40aa6ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217318"
---
# <a name="custom-templates-for-dotnet-new"></a>Vlastní šablony pro nové dotnet.

[.NET Core SDK](https://www.microsoft.com/net/download/core) se dodává s mnoha šablony pro použití s předinstalovaným [ `dotnet new` příkaz](dotnet-new.md). Od verze rozhraní .NET Core 2.0, můžete vytvořit vlastní šablony pro jakýkoli typ projektu, například aplikace, služby, nástroj nebo knihovny tříd. Můžete dokonce vytvořit šablonu, která výstupy jeden nebo více nezávislých souborech, jako je konfigurační soubor.

Vlastní šablony můžete nainstalovat z balíčku NuGet na všechny NuGet kanálu pod položkou NuGet *nupkg* souboru přímo, nebo určením adresář systému souborů, který obsahuje šablonu. Modul šablony nabízí funkce, které vám umožní nahradit hodnoty, zahrnout a vyloučit soubory a oblastí, souborů a provedení operací vlastní zpracování, pokud je vaše šablony.

Modul šablony je open source a je úložiště online kódu na [dotnet/ukázka](https://github.com/dotnet/templating/) na Githubu. Přejděte [dotnet/dotnet šablony samples](https://github.com/dotnet/dotnet-template-samples) úložišti pro ukázky šablon. Více šablon, včetně šablon od jiných výrobců, které se nacházejí v [dostupných šablon pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na Githubu. Další informace o vytváření a používání vlastních šablon najdete v tématu [postup vytvoření nové vlastní šablony pro dotnet](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/) a [úložiště GitHub dotnet/ukázka Wiki](https://github.com/dotnet/templating/wiki).

Postupujte podle návod a vytvoření šablony najdete v tématu [vytvoření nové vlastní šablony pro dotnet](~/docs/core/tutorials/create-custom-template.md) kurzu.

## <a name="configuration"></a>Konfigurace

Šablona se skládá z následujících součástí:

- Zdrojové soubory a složky
- Konfigurační soubor (*template.json*)

### <a name="source-files-and-folders"></a>Zdrojové soubory a složky

Zdrojové soubory a složky patří, ať soubory a složky, které chcete šablonu modul má použít při `dotnet new <TEMPLATE>` se spustí příkaz. Modul šablony slouží k použití *spustitelného projekty* jako zdrojový kód k vytvoření projektů. To má několik výhod:

- Modul šablony nevyžaduje speciální tokeny vložit do vašeho projektu zdrojového kódu.
- Soubory kódu jsou speciální soubory nebo upravena žádným způsobem pro práci s modulem šablony. Ano nástroje, které standardně používáte při práci s projekty také pracovat se obsah šablony.
- Sestavení, spuštění a ladění vašich projektů šablony stejně, jako je tomu u žádné jiné projekty.
- Můžete rychle vytvořit šablonu z existující projekt právě přidáním *template.json* konfigurační soubor do projektu.

Soubory a složky v šabloně nejsou omezeny na formální projektu typy .NET, jako je řešení pro .NET Core a rozhraní .NET Framework. Veškerý obsah, který chcete vytvořit, když šablona se používá, i v případě, že modul šablona vytváří jenom jeden soubor pro její výstup, jako je konfigurační soubor nebo soubor řešení může obsahovat zdrojové soubory a složky. Můžete například vytvořit šablonu, která obsahuje *web.config* zdrojového souboru a vytvoří upravené *web.config* soubor pro projekty, kde se používá šablonu. Úpravy na zdrojové soubory jsou založené na logiku a nastavení, které jste zadali v *template.json* předaný konfigurační soubor společně s hodnoty zadané uživatelem jako možnosti k `dotnet new <TEMPLATE>` příkaz.

### <a name="templatejson"></a>Template.JSON

*Template.json* soubor je umístěn v *. template.config* složku v kořenovém adresáři šablony. Soubor obsahuje informace o konfiguraci k modulu šablony. Minimální konfigurace vyžaduje členy zobrazené v následující tabulce, což je dostačující k vytvoření šablony funkční.

| Člen            | Typ          | Popis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identifikátor URI           | Schéma JSON pro *template.json* souboru. Editory, které podporují JSON schémata JSON úpravy funkce povolit, když je zadané schéma. Například [Visual Studio Code](https://code.visualstudio.com/) vyžaduje povolení IntelliSense tohoto člena. Použít hodnotu `http://json.schemastore.org/template`. |
| `author`          | odkazy řetězců        | Autor šablony. |
| `classifications` | Array(String) | Nula nebo více vlastností šablony, která uživatel může použít při hledání se najít šablonu. Klasifikace se zobrazí také v *značky* sloupce, když se objeví v seznamu šablon vytvořeného pomocí <code>dotnet new -l&#124;--list</code> příkaz. |
| `identity`        | odkazy řetězců        | Jedinečný název pro tuto šablonu. |
| `name`            | odkazy řetězců        | Název pro šablonu, která uživatelé měli vidět. |
| `shortName`       | odkazy řetězců        | Sdružená vlastnost výchozí pro výběr šablony, která platí pro prostředí, kde je název šablony zadanou uživatelem, není vybrána prostřednictvím grafickým uživatelským rozhraním. Například krátký název je užitečné při použití šablony z příkazového řádku pomocí rozhraní příkazového řádku. |

#### <a name="example"></a>Příklad:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

Úplné schéma pro *template.json* soubor se nachází zde [úložiště schématu JSON](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>Rozhraní .NET výchozí šablony

Při instalaci [.NET Core SDK](https://www.microsoft.com/net/download/core), dostanete přes tucet integrované šablony pro vytváření projektů a soubory, včetně aplikace konzoly, knihovny tříd, jednotky testování projektů ASP.NET Core aplikace (včetně [úhlová](https://angular.io/) a [reagovat](https://facebook.github.io/react/) projekty) a konfigurační soubory. Seznam integrovaných šablon, spusťte `dotnet new` s `-l|--list` možnost:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Balení šablonu do balíčku NuGet (soubor nupkg)

V současné době je vlastní šablony mnoha funkcemi v systému Windows se [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (ne [dotnet pack](dotnet-pack.md)). Pro různé platformy balení, zvažte použití [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

Obsah složky projektu, společně s jeho *.template.config/template.json* souboru, se umístí do složky s názvem *obsah*. Vedle položky *obsah* složky, přidejte [ *nuspec* souboru](/nuget/create-packages/creating-a-package), což je soubor XML manifestu, který popisuje obsah balíčku a disky proces vytvoření balíčku NuGet. Uvnitř  **\<packageTypes >** element v *nuspec* souboru, zahrnout  **\<packageType >** element s `name` Hodnota atributu `Template`. Obě *obsah* složky a *nuspec* soubor by měl být uložený ve stejném adresáři. V tabulce jsou uvedeny minimální *nuspec* souboru elementy, které jsou potřebné k vytvoření šablony jako balíčku NuGet.

| Prvek            | Typ   | Popis |
| ------------------ | ------ | ----------- |
| **\<Autoři >**     | odkazy řetězců | Seznam balíčků autoři, odpovídající profil názvy v nuget.org oddělených čárkami. Autoři jsou zobrazeny v galerii NuGet v nuget.org a jsou používané pro křížovou balíčky autory stejné. |
| **\<Popis >** | odkazy řetězců | Dlouhý popis balíčku pro zobrazení uživatelského rozhraní. |
| **\<id>**          | odkazy řetězců | Identifikátor balíčku velká a malá písmena, která musí být jedinečný v rámci nuget.org nebo jiná bude balíček nacházet v galerii. ID nesmí obsahovat mezery ani znaky, které nejsou platné pro adresu URL a obecně se řídí pravidly obor názvů .NET. V tématu [výběr balíčku jedinečný identifikátor a nastavení číslo verze](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) pokyny. |
| **\<packageType>** | odkazy řetězců | Umístěte tento element uvnitř  **\<packageTypes >** element mezi  **\<metadata >** elementy. Nastavte `name` atribut  **\<packageType >** element `Template`. |
| **\<verze >**     | odkazy řetězců | Verze balíčku, následující vzoru major.minor.patch. Čísla verzí může zahrnovat příponu předběžné verze, jak je popsáno v [předprodejní verze](/nuget/create-packages/prerelease-packages#semantic-versioning) tématu. |

Najdete v článku [odkaz příponou .nuspec](/nuget/schema/nuspec) pro kompletní *nuspec* schéma souboru. Příklad *nuspec* soubor pro šablonu se zobrazí v [vytvoření nové vlastní šablony pro dotnet](~/docs/core/tutorials/create-custom-template.md) kurzu.

[Vytvoření balíčku](/nuget/create-packages/creating-a-package#creating-the-package) pomocí `nuget pack <PATH_TO_NUSPEC_FILE>` příkaz.

## <a name="installing-a-template"></a>Instalace šablony

Nainstalujte vlastní šablonu z balíčku NuGet na všechny NuGet kanálu odkazem *nupkg* souboru přímo, nebo zadáním adresář systému souborů, který obsahuje konfiguraci ukázka. Použití `-i|--install` možnost s [dotnet nové](dotnet-new.md) příkaz.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li nainstalovat šablonu z balíčku NuGet uložené v nuget.org

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Instalace šablony ze souboru místní nupkg

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Chcete-li nainstalovat šablonu z adresáře systému souborů

`FILE_SYSTEM_DIRECTORY` Je složka projekt obsahující projekt a *. template.config* složky:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Odinstalace šablonu

Odinstalujte vlastní šablony pomocí odkazující na balíček NuGet podle jeho `id` nebo zadáním adresář systému souborů, který obsahuje konfiguraci ukázka. Použití `-u|--uninstall` nainstalovat možnost s [dotnet nové](dotnet-new.md) příkaz.

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li odinstalovat šablonu z balíčku NuGet uložené v nuget.org

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Chcete-li odinstalovat šablony ze souboru místní nupkg

Pokud chcete odinstalovat šablony, nemusíte pokus o použití cesty k *nupkg* souboru. *Probíhá pokus o odinstalaci šablony pomocí `dotnet new -u <PATH_TO_NUPKG_FILE>` selže.* Odkazují na balíček podle jeho `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Chcete-li odinstalovat šablonu z adresáře systému souborů

`FILE_SYSTEM_DIRECTORY` Je složka projekt obsahující projekt a *. template.config* složky:

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Vytvoření projektu pomocí vlastní šablony

Po instalaci šablony, použijte šablonu spuštěním `dotnet new <TEMPLATE>` příkaz stejně jako u jiných předem nainstalované šablony. Můžete také zadat [možnosti](dotnet-new.md#options) k `dotnet new` příkazu, včetně šablony konkrétní možnosti jste nakonfigurovali v nastavení šablony. Zadejte krátký název šablony přímo k příkazu:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Viz také

[Vytvořit vlastní šablonu pro nové dotnet (kurz)](../tutorials/create-custom-template.md)  
[úložiště GitHub DotNet/ukázka Wiki](https://github.com/dotnet/templating/wiki)  
[úložiště GitHub DotNet/dotnet šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)  
[Jak vytvořit nové vlastní šablony pro dotnet.](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[*Template.JSON* schématu na úložiště schématu JSON](http://json.schemastore.org/template)  
