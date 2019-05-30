---
title: Vlastních šablon pro dotnet nové
description: Další informace o vlastních šablon pro jakýkoli druh projektu .NET nebo soubory.
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 6ce53cab308ed404974e4d736e735bc82ac04fe6
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299912"
---
# <a name="custom-templates-for-dotnet-new"></a>Vlastních šablon pro dotnet nové

[.NET Core SDK](https://www.microsoft.com/net/download/core) se dodává s mnoha šablon pro použití s předinstalovaným [ `dotnet new` příkaz](dotnet-new.md). Od verze rozhraní .NET Core 2.0, můžete vytvořit vlastní šablony pro každý typ projektu, například aplikace, služby, nástroje nebo knihovny tříd. Můžete dokonce vytvořit šablonu, jejichž výstupem jsou jeden nebo více nezávislých souborech, jako je konfigurační soubor.

Vlastní šablony můžete nainstalovat z balíčku NuGet na jakékoli NuGet kanálu pomocí odkazu na NuGet *nupkg* souboru přímo, nebo zadáním systémový adresář souboru, který obsahuje šablonu. Modul šablon nabízí funkce, které umožňují nahraďte hodnotami, zahrnout a vyloučit soubory a oblasti souborů a provádění vlastního zpracování operací při použití šablony.

Modul šablon je typu open source a úložiště online kódu je na [dotnet/šablonování](https://github.com/dotnet/templating/) na Githubu. Přejděte [dotnet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples) úložiště pro ukázky šablon. Další šablony, včetně šablon od třetích stran, se nacházejí v [dostupných šablon pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na Githubu. Další informace o vytváření a používání vlastních šablon najdete v tématu [tom, jak vytvořit nové vlastní šablony pro dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [úložiště GitHub dotnet/šablonování Wiki](https://github.com/dotnet/templating/wiki).

Postupujte podle průvodce a vytvoření šablony najdete v tématu [vytvořit nové vlastní šablony pro dotnet](~/docs/core/tutorials/create-custom-template.md) kurzu.

## <a name="configuration"></a>Konfiguraci

Šablona se skládá z následujících součástí:

- Zdrojové soubory a složky
- Konfigurační soubor (*template.json*)

### <a name="source-files-and-folders"></a>Zdrojové soubory a složky

Zdrojové soubory a složky patří libovolné soubory a složky šablona modul mají použít, když `dotnet new <TEMPLATE>` spuštění příkazu. Modul šablon je navržen pro použití *spustitelné projekty* jako zdrojový kód k vytvoření projektů. To má několik výhod:

- Modul šablon nevyžaduje vložit speciální tokeny do zdrojového kódu.
- Soubory kódu nejsou speciální soubory nebo pro práci s modulem šablony žádným způsobem upravit. Nástroje, které standardně používáte při práci s projekty tedy také pracovat obsah šablony.
- Sestavení, spouštět a ladit vaše projekty ze šablony, stejně, jako je tomu u vašich projektů.
- Můžete rychle vytvořit šablonu z existujícího projektu pouhým přidáním *template.json* konfigurační soubor do projektu.

Soubory a složky uložené v šabloně nejsou omezené na formální typy projektů .NET, jako jsou například řešení .NET Core nebo .NET Framework. Veškerý obsah, který chcete vytvořit při použití této šablony i v případě, že modul šablony vytvoří jenom jeden soubor pro její výstup, jako je například konfigurační soubor nebo soubor řešení může obsahovat zdrojové soubory a složky. Můžete například vytvořit šablonu, která obsahuje *web.config* zdrojového souboru a vytvoří upravené *web.config* souboru pro projekty, ve kterém se používá šablonu. Změny zdrojové soubory jsou založeny na logiku a jste zadali v nastavení *template.json* konfiguračního souboru spolu s uživatelem zadané hodnoty předané jako možnosti k `dotnet new <TEMPLATE>` příkazu.

### <a name="templatejson"></a>template.json

*Template.json* soubor umístěn v *. template.config* složku v kořenovém adresáři šablony. Soubor obsahuje informace o konfiguraci pro modul šablony. Minimální požadavky na konfiguraci vyžaduje členů je znázorněno v následující tabulce, což je dostatečná pro vytvoření funkční šablony.

| Člen            | Type          | Popis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identifikátor URI           | Schéma JSON pro *template.json* souboru. Editory, které podporují schémat JSON povolte úpravy v editoru JSON funkce-li zadána schématu. Například [Visual Studio Code](https://code.visualstudio.com/) vyžaduje tento člen pro povolení technologie IntelliSense. Použijte hodnotu `http://json.schemastore.org/template`. |
| `author`          | odkazy řetězců        | Autor šablony. |
| `classifications` | Array(String) | Nula nebo více vlastností šablony, která uživatel může použít k vyhledávání pro něj najít šablonu. Klasifikace se také zobrazují v *značky* sloupce, když se objeví v seznamu šablon vytvořený pomocí <code>dotnet new -l&#124;--list</code> příkazu. |
| `identity`        | odkazy řetězců        | Jedinečný název pro tuto šablonu. |
| `name`            | odkazy řetězců        | Název pro šablonu, kterou uživatelé měli vidět. |
| `shortName`       | odkazy řetězců        | Výchozí zkratka pro výběr šablonu, která se vztahuje na prostředí, kde název šablony je uživatel zadá, není vybrána přes grafické uživatelské rozhraní. Krátký název například je užitečné při použití šablony z příkazového řádku pomocí příkazů rozhraní příkazového řádku. |

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

Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>Výchozí šablony .NET

Při instalaci [.NET Core SDK](https://www.microsoft.com/net/download/core), obdržíte více než tucet předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolové aplikace, knihovny tříd, jednotky testování projektů, aplikace ASP.NET Core (včetně [Angular](https://angular.io/) a [React](https://facebook.github.io/react/) projekty) a konfigurační soubory. Seznam předdefinovaných šablon, spusťte `dotnet new` příkazů `-l|--list` možnost:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Balení šablonu do balíčku NuGet (soubor nupkg)

V současné době je zabalena vlastní šablony na Windows s [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (ne [balíčku dotnet](dotnet-pack.md)). Pro různé platformy balení, zvažte použití [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

Obsah složky projektu, který je společně s jeho *.template.config/template.json* souboru, se umístí do složky s názvem *obsah*. Vedle položky *obsah* složky, přidejte [ *nuspec* souboru](/nuget/create-packages/creating-a-package), souboru manifestu XML, který popisuje obsah balíčku a řídí proces vytvoření balíčku NuGet. Uvnitř  **\<packageTypes >** element v *nuspec* souboru, zahrnují  **\<packageType >** element s `name` Hodnota atributu `Template`. Oba *obsah* složky a *nuspec* soubor by měl být uložený ve stejném adresáři. V tabulce jsou uvedeny minimální *nuspec* souboru prvků vyžadovaných pro vytvoření šablony jako balíček NuGet.

| Prvek            | Type   | Popis |
| ------------------ | ------ | ----------- |
| **\<authors>**     | odkazy řetězců | Čárkou oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Autoři se zobrazí v galerii NuGet na nuget.org a slouží k křížový odkaz balíčky stejné autory. |
| **\<description>** | odkazy řetězců | Dlouhý popis balíčku zobrazí v uživatelském rozhraní. |
| **\<id>**          | odkazy řetězců | Identifikátor balíčku velká a malá písmena, která musí být jedinečný v rámci nuget.org nebo cokoli, co se bude balíček nacházet v galerii. ID nesmí obsahovat mezery nebo znaky, které nejsou platné pro adresu URL a obvykle postupují podle pravidla oboru názvů .NET. Zobrazit [výběr balíčku jedinečný identifikátor a nastaví číslo verze](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) pokyny. |
| **\<packageType>** | odkazy řetězců | Umístit tento element uvnitř,  **\<packageTypes >** element mezi  **\<metadat >** elementy. Nastavte `name` atribut  **\<packageType >** elementu `Template`. |
| **\<version>**     | odkazy řetězců | Verze balíčku, následující vzor hlavníverze.podverze.oprava. Čísla verzí může obsahovat příponu předběžné verze, jak je popsáno v [předběžných verzí](/nuget/create-packages/prerelease-packages#semantic-versioning) tématu. |

Najdete v článku [souboru .nuspec odkaz](/nuget/schema/nuspec) pro kompletní *nuspec* schéma souboru reklamy. Příklad *nuspec* souborů pro šablony se zobrazí v [vytvořit nové vlastní šablony pro dotnet](~/docs/core/tutorials/create-custom-template.md) kurzu.

[Vytvoření balíčku](/nuget/create-packages/creating-a-package#creating-the-package) pomocí `nuget pack <PATH_TO_NUSPEC_FILE>` příkazu.

## <a name="installing-a-template"></a>Instalace šablony

Nainstalujte vlastní šablonu z balíčku NuGet na jakékoli NuGet kanálu odkazováním *nupkg* souboru přímo nebo tak, že určíte adresář systému souboru, který obsahuje konfiguraci šablon. Použití `-i|--install` spolu s možností [dotnet nové](dotnet-new.md) příkazu.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li nainstalovat šablony z balíčku NuGet uloženou v nuget.org

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Chcete-li nainstalovat šablony ze souboru místní nupkg

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Chcete-li nainstalovat šablony z adresáře systému souborů

`FILE_SYSTEM_DIRECTORY` Je projekt složku obsahující projekt a *. template.config* složky:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Odinstalace šablony

Odinstalace vlastní šablonu pomocí odkazu na balíček NuGet podle jeho `id` nebo tak, že určíte adresář systému souboru, který obsahuje konfiguraci šablon. Použití `-u|--uninstall` možnost pomocí instalace [dotnet nové](dotnet-new.md) příkaz.

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li odinstalovat šablonu z balíčku NuGet uloženou v nuget.org

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Chcete-li odinstalovat šablony ze souboru místní nupkg

K odinstalaci šablony, nepokoušejte se použít cestu k *nupkg* souboru. Pokus o odinstalaci šablony pomocí `dotnet new -u <PATH_TO_NUPKG_FILE>` selže. Odkázat na balíček podle jeho `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Chcete-li odinstalovat šablonu z adresáře systému souborů

`FILE_SYSTEM_DIRECTORY` Je projekt složku obsahující projekt a *. template.config* složky. Zadaná cesta musí být absolutní cesta. Pokus odinstalovat sadu pomocí šablony, relativní cesta selhání. Další informace najdete v tématu [dotnet nové](dotnet-new.md) článku.

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Vytvořte projekt pomocí vlastní šablony

Po instalaci šablony, použijte šablonu pomocí provádí `dotnet new <TEMPLATE>` příkaz stejně jako u jiných předem nainstalovaných šablon. Můžete také určit [možnosti](dotnet-new.md#options) k `dotnet new` příkazu, včetně možnosti konkrétní šablony jste nakonfigurovali v nastavení šablony. Zadejte krátký název šablony přímo k příkazu:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastní šablony pro dotnet new (kurz)](../tutorials/create-custom-template.md)
- [úložiště GitHub DotNet/šablonování Wiki](https://github.com/dotnet/templating/wiki)
- [úložiště GitHub DotNet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)
- [Jak vytvořit nové vlastní šablony pro dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* schématu na Store schématu JSON](http://json.schemastore.org/template)
