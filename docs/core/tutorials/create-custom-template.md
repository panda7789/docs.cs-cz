---
title: "Vytvoření nové vlastní šablony pro dotnet."
description: "Naučte se vytvořit vlastní šablonu pro nový příkaz dotnet. v této fun kurzu."
keywords: "Šablona .NET, .NET core, ukázka, kurz, dotnet nové"
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 519b910a-6efe-4394-9b81-0546aa3e7462
ms.openlocfilehash: c3955951c0367e1933342172c1bc1888fb58f60c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Vytvoření nové vlastní šablony pro dotnet.

Tento kurz ukazuje, jak na:

- Vytvořte šablonu základní z existujícího projektu nebo nový projekt konzolové aplikace.
- Pack šablony pro distribuci v nuget.org nebo z místního *nupkg* souboru.
- Instalace šablony z nuget.org, místní *nupkg* soubor nebo místního systému souborů.
- Odinstalujte šablony.

Pokud dáváte přednost pokračujte kurzu s ucelenou ukázku, stáhněte si [šablona projektu vzorku](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). Ukázka šablony je nakonfigurován pro distribuci NuGet.

Pokud chcete stažený ukázku použít s distribučním systému souborů, postupujte takto:

- Přesunout obsah *obsah* vzorku jednu úroveň do složky *GarciaSoftware.ConsoleTemplate.CSharp* složky.
- Odstranit prázdné *obsah* složky.
- Odstranit *nuspec* souboru.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) nebo novější verze.
- Přečtěte si téma odkaz [vlastních šablon pro dotnet nové](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Vytvoření šablony z projektu

Použít existující projekt, který jste potvrzen zkompiluje a spustí nebo vytvořit nový projekt konzolové aplikace do složky na pevném disku. Tento kurz předpokládá, že je název složky projektu *GarciaSoftware.ConsoleTemplate.CSharp* uložené v *dokumenty nebo šablony* v profilu uživatele. Název šablony kurz projektu je ve formátu  *\<název společnosti >.\< Typ šablony >. \<Programovací jazyk >*, však můžete název projektu a šablony nic nechcete.

1. Přidat složku do kořenového adresáře projektu s názvem *. template.config*.
1. Uvnitř *. template.config* složky, vytvoření *template.json* souboru konfigurace šablony. Další informace a člen definice pro *template.json* souborů najdete v tématu [vlastních šablon pro dotnet nové](../tools/custom-templates.md#templatejson) tématu a [ *template.json* schéma na úložiště schématu JSON](http://json.schemastore.org/template).

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

Šablona je dokončena. V tuto chvíli máte dvě možnosti pro distribuci šablony. Chcete-li pokračovat v tomto kurzu, vyberte jednu cestu nebo dalších:

1. [Distribuce NuGet](#use-nuget-distribution): nainstalovat šablonu z NuGet nebo místní *nupkg* souboru a používat nainstalované šablony.
2. [Soubor distribuční systému](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>Použití distribučních NuGet

### <a name="pack-the-template-into-a-nuget-package"></a>Pack šablony do balíčku NuGet

1. Vytvořte složku pro balíček NuGet. Pro tento kurz, název složky *GarciaSoftware.ConsoleTemplate.CSharp* se používá, a je vytvořena uvnitř *dokumenty nebo NuGetTemplates* složky v profilu uživatele. Vytvořte složku s názvem *obsah* uvnitř do nové složky pro uložení souborů projektu šablony.
1. Zkopírujte obsah složky projektu, společně s jeho *.template.config/template.json* souboru do *obsah* složky, které jste vytvořili.
1. Vedle položky *obsah* složky, přidejte [ *nuspec* soubor](/nuget/create-packages/creating-a-package). Soubor nuspec je soubor XML manifestu, který popisuje obsah balíčku a disky proces vytvoření balíčku NuGet.
   
   ![Struktura adresářů znázorňující rozložení balíček NuGet](./media/create-custom-template/nugetdirectorylayout.png)

1. Uvnitř  **\<packageTypes >** element v *nuspec* souboru, zahrnout  **\<packageType >** element s `name` Hodnota atributu `Template`. Obě *obsah* složky a *nuspec* soubor by měl být uložený ve stejném adresáři. V tabulce jsou uvedeny minimální *nuspec* souboru elementy, které jsou potřebné k vytvoření šablony jako balíčku NuGet.

   | Prvek            | Typ   | Popis |
   | ------------------ | ------ | ----------- |
   | **\<Autoři >**     | odkazy řetězců | Seznam balíčků autoři, odpovídající profil názvy v nuget.org oddělených čárkami. Autoři jsou zobrazeny v galerii NuGet v nuget.org a jsou používané pro křížovou balíčky autory stejné. |
   | **\<Popis >** | odkazy řetězců | Dlouhý popis balíčku pro zobrazení uživatelského rozhraní. |
   | **\<ID >**          | odkazy řetězců | Identifikátor balíčku velká a malá písmena, která musí být jedinečný v rámci nuget.org nebo jiná bude balíček nacházet v galerii. ID nesmí obsahovat mezery ani znaky, které nejsou platné pro adresu URL a obecně se řídí pravidly obor názvů .NET. V tématu [výběr balíčku jedinečný identifikátor a nastavení číslo verze](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) pokyny. |
   | **\<packageType >** | odkazy řetězců | Umístěte tento element uvnitř  **\<packageTypes >** element mezi  **\<metadata >** elementy. Nastavte `name` atribut  **\<packageType >** element `Template`. |
   | **\<verze >**     | odkazy řetězců | Verze balíčku, následující vzoru major.minor.patch. Čísla verzí může zahrnovat příponu předběžné verze, jak je popsáno v [předprodejní verze](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Najdete v článku [odkaz příponou .nuspec](/nuget/schema/nuspec) pro kompletní *nuspec* schéma souboru.

   *Nuspec* souborů pro tento kurz je s názvem *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* a obsahuje následující obsah:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. [Vytvoření balíčku](/nuget/create-packages/creating-a-package#creating-the-package) pomocí `nuget pack <PATH_TO_NUSPEC_FILE>` příkaz. Následující příkaz předpokládá, že složka, která obsahuje prostředky NuGet je v *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp/*. Ale kdekoli umístit složku v systému, `nuget pack` v příkazu zadat cestu k *nuspec* souboru:

   ```console
   nuget pack C:/Users/<USER>/Documents/NuGetTemplates/GarciaSoftware.ConsoleTemplate.CSharp/GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Publikování balíčku nuget.org

K publikování balíčku NuGet, postupujte podle pokynů v [vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tématu. Doporučujeme však není publikovat kurz šablony NuGet jako nikdy odstraněním po publikování, pouze delisted. Teď, když máte balíček NuGet ve formě *nupkg* souborů, doporučujeme postupujte podle pokynů k instalaci šablony přímo z místní *nupkg* souboru.

### <a name="install-the-template-from-a-nuget-package"></a>Instalace šablony z balíčku NuGet

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Instalace šablony z místní *nupkg* souboru

Instalace šablony *nupkg* soubor, který je vytvořil, použijte `dotnet new` s `-i|--install` možnost a zadejte cestu k *nupkg* souboru:

```console
dotnet new -i C:/Users/<USER>/GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Instalace šablony z balíčku NuGet uložené v nuget.org

Pokud chcete nainstalovat z balíčku NuGet uložené v nuget.org, použijte šablonu `dotnet new` s `-i|--install` možnost a zadejte název balíčku NuGet:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Příkladem je pouze pro demonstrační účely. Není k dispozici `GarciaSoftware.ConsoleTemplate.CSharp` balíček NuGet v nuget.org, a není doporučeno, publikovat a využívat testovací šablon z NuGet. Pokud příkaz spouštíte, je nainstalována žádná šablona. Však můžete nainstalovat šablonu, která nebyla publikována na nuget.org odkazem *nupkg* souboru přímo na místní systém souborů, jak je uvedeno v předchozí části [nainstalujte šablonu z místní nupkg soubor](#install-the-template-from-the-local-nupkg-file).

Pokud chcete za provozu příklad instalace šablonu z balíčku v nuget.org, můžete použít [NUnit 3 šablonu pro nové dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Tato šablona nastaví projekt tak, aby pomocí testování částí NUnit. Použijte následující příkaz k její instalaci:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Pokud uvedete šablon s `dotnet new -l`, uvidíte *NUnit 3 testovacího projektu* s krátký název *nunit* v seznamu šablon. Jste připravení použít šablonu v další části.

![Okno konzoly zobrazující šabloně NUnit označené Další nainstalované šablony](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a>Vytvoření projektu ze šablony

Po instalaci šablony z NuGet použít šablonu spuštěním `dotnet new <TEMPLATE>` příkaz z adresáře, kam chcete modulu šablon výstupu umístit (Pokud používáte `-o|--output` možnost určení konkrétního adresáře). Další informace najdete v tématu [ `dotnet new` možnosti](~/docs/core/tools/dotnet-new.md#options). Zadejte krátký název šablony přímo na `dotnet new` příkaz. Pokud chcete vytvořit projekt ze šablony NUnit, spusťte následující příkaz:

```console
dotnet new nunit
```

Konzole ukazuje vytvoření projektu a obnovení projektu balíčky. Po spuštění příkazu projekt je připravený k použití.

![Okno konzoly zobrazující výstup příkazu nové dotnet jak vytvoří NUnit projekt a obnoví závislosti projektu](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li odinstalovat šablonu z balíčku NuGet uložené v nuget.org

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Příkladem je pouze pro demonstrační účely. Není k dispozici `GarciaSoftware.ConsoleTemplate.CSharp` NuGet balíčku v nuget.org nebo nainstalovat s .NET Core SDK. Pokud příkaz spouštíte, se Odinstaluje balíček či šablonu a zobrazí se následující výjimky:
> 
> > Nelze najít něco odinstalace volat 'GarciaSoftware.ConsoleTemplate.CSharp'.

Pokud jste nainstalovali [NUnit 3 šablonu pro nové dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) a chcete ji odinstalovat, použijte následující příkaz:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Odinstalujte šablony ze souboru místní nupkg

Pokud chcete odinstalovat šablony, nemusíte pokus o použití cesty k *nupkg* souboru. *Probíhá pokus o odinstalaci šablony pomocí `dotnet new -u <PATH_TO_NUPKG_FILE>` selže.* Odkazují na balíček podle jeho `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Použít distribuci systému souborů

K distribuci šablony, umístíte složce projektu šablony v umístění dostupné pro uživatele ve vaší síti. Použití `dotnet new` s `-i|--install` možnost a zadejte cestu ke složce šablony (složku projekt obsahující projekt a *. template.config* složku).

Kurz předpokládá, že v šabloně projektů je uložen v *dokumentů, šablon* složku profilu uživatele. Z tohoto umístění instalovat šablony s následujícím příkazu nahraďte \<uživatele > s názvem profilu uživatele:

```console
dotnet new -i C:/Users/<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Vytvoření projektu ze šablony

Po instalaci šablony ze systému souborů, použijte šablonu spuštěním `dotnet new <TEMPLATE>` příkaz z adresáře, kam chcete modulu šablon výstupu umístit (Pokud používáte `-o|--output` možnost určení konkrétního adresáře). Další informace najdete v tématu [ `dotnet new` možnosti](~/docs/core/tools/dotnet-new.md#options). Zadejte krátký název šablony přímo na `dotnet new` příkaz.

Ze složky nový projekt vytvořený v *C: či uživatelů nebo\<uživatele >/dokumenty nebo projekty/MyConsoleApp*, vytvoření projektu z `garciaconsole` šablony:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Odinstalujte šablony

Pokud jste vytvořili šablonu v místním systému souborů na *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp*, odinstalujte jej pomocí `-u|--uninstall` přepínač a cestu k šabloně Složka:

```console
dotnet new -u C:/Users/<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Chcete-li odinstalovat šablony z vašeho místního systému souborů, je potřeba plně kvalifikovanou cestu. Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.
> Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.

## <a name="see-also"></a>Viz také

[úložiště GitHub DotNet/ukázka Wiki](https://github.com/dotnet/templating/wiki)  
[úložiště GitHub DotNet/dotnet šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)  
[Jak vytvořit nové vlastní šablony pro dotnet.](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[*Template.JSON* schématu na úložiště schématu JSON](http://json.schemastore.org/template)  
