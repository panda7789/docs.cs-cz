---
title: Vytvoření nové vlastní šablony pro dotnet
description: Zjistěte, jak vytvořit vlastní šablonu pro nový příkaz dotnet v tuhle zábavnou kurzu.
author: guardrex
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 3b45a24c8a249eeb99fb1a4b14918483b978980b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676444"
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Vytvoření nové vlastní šablony pro dotnet

V tomto kurzu se dozvíte, jak do:

- Vytvoření základní šablony z existujícího projektu nebo nový projekt konzolové aplikace.
- Balíček šablony pro distribuci na nuget.org z místního *nupkg* souboru.
- Instalace šablony z nuget.org, místní *nupkg* souboru nebo místního systému souborů.
- Odinstalujte šablony.

Pokud budete chtít pokračovat v průběhu kurzu s úplnou ukázku, stáhněte si [Ukázková šablona projektu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). Ukázková šablona je nakonfigurován pro distribuci NuGet.

Pokud chcete použít stažené ukázky s distribucí systému souborů, postupujte takto:

- Přesunout obsah *obsah* vzorku nahoru o jednu úroveň do složky *GarciaSoftware.ConsoleTemplate.CSharp* složky.
- Odstranit prázdné *obsah* složky.
- Odstranit *nuspec* souboru.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) nebo novější verze.
- Přečtěte si téma referenčních informací [vlastních šablon pro dotnet nové](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Vytvoření šablony z projektu

Použití existujícího projektu, který ověření, že zkompiluje a spustí nebo vytvořte nový projekt konzolové aplikace do složky na pevném disku. V tomto kurzu se předpokládá, že je název složky projektu *GarciaSoftware.ConsoleTemplate.CSharp* uloženou v *Documents\Templates* v profilu uživatele. Název šablony projektu kurz je ve formátu  *\<název společnosti >.\< Typ šablony >. \<Programovací jazyk >*, ale můžete zdarma na název projektu a šablony, cokoli si přejete.

1. Přidat složku do kořenového adresáře projektu s názvem *. template.config*.
1. Uvnitř *. template.config* složku, vytvořte *template.json* souboru konfigurace šablony. Pro další informace a člen definice pro *template.json* souboru, najdete v článku [vlastních šablon pro dotnet nové](../tools/custom-templates.md#templatejson) tématu a [ *template.json* schéma na Store schématu JSON](http://json.schemastore.org/template).

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

Šablona je ukončena. V tomto okamžiku máte dvě možnosti pro distribuci šablon. Chcete-li pokračovat v tomto kurzu, zvolte jednu cestu, nebo druhé:

1. [Distribuce NuGet](#use-nuget-distribution): nainstalovat šablony z NuGet nebo místní *nupkg* souborů a použití instalované šablony.
2. [Soubor distribuce systému](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>Použít rozdělení NuGet

### <a name="pack-the-template-into-a-nuget-package"></a>Balíček šablony do balíčku NuGet

1. Vytvořte složku pro balíček NuGet. Pro tento kurz, název složky *GarciaSoftware.ConsoleTemplate.CSharp* se používá, a vytvoří se ve složce *Documents\NuGetTemplates* složky v profilu uživatele. Vytvořte složku s názvem *obsah* uvnitř nové šablony složky pro uložení souborů projektu.
1. Zkopírujte obsah složky projektu, společně s jeho *.template.config/template.json* souboru, do *obsah* složky, které jste vytvořili.
1. Vedle položky *obsah* složky, přidejte [ *souboru nuspec* soubor](/nuget/create-packages/creating-a-package). Soubor nuspec je soubor manifestu XML, který popisuje obsah balíčku a řídí proces vytvoření balíčku NuGet.

   ![Adresářová struktura znázorňující rozložení balíčku NuGet.](./media/create-custom-template/nuget-directory-layout.png)

1. Uvnitř  **\<packageTypes >** element v *nuspec* souboru, zahrnují  **\<packageType >** element s `name` Hodnota atributu `Template`. Oba *obsah* složky a *nuspec* soubor by měl být uložený ve stejném adresáři. V tabulce jsou uvedeny minimální *nuspec* souboru prvků vyžadovaných pro vytvoření šablony jako balíček NuGet.

   | Prvek            | Typ   | Popis |
   | ------------------ | ------ | ----------- |
   | **\<authors>**     | odkazy řetězců | Čárkou oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Autoři se zobrazí v galerii NuGet na nuget.org a slouží k křížový odkaz balíčky stejné autory. |
   | **\<description>** | odkazy řetězců | Dlouhý popis balíčku zobrazí v uživatelském rozhraní. |
   | **\<id>**          | odkazy řetězců | Identifikátor balíčku velká a malá písmena, která musí být jedinečný v rámci nuget.org nebo cokoli, co se bude balíček nacházet v galerii. ID nesmí obsahovat mezery nebo znaky, které nejsou platné pro adresu URL a obvykle postupují podle pravidla oboru názvů .NET. Zobrazit [výběr balíčku jedinečný identifikátor a nastaví číslo verze](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) pokyny. |
   | **\<packageType>** | odkazy řetězců | Umístit tento element uvnitř,  **\<packageTypes >** element mezi  **\<metadat >** elementy. Nastavte `name` atribut  **\<packageType >** elementu `Template`. |
   | **\<version>**     | odkazy řetězců | Verze balíčku, následující vzor hlavníverze.podverze.oprava. Čísla verzí může obsahovat příponu předběžné verze, jak je popsáno v [předběžných verzí](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Najdete v článku [souboru .nuspec odkaz](/nuget/schema/nuspec) pro kompletní *nuspec* schéma souboru reklamy.

   *Nuspec* souboru pro tento kurz je s názvem *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* a obsahuje následující obsah:

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

1. [Vytvoření balíčku](/nuget/create-packages/creating-a-package#creating-the-package) pomocí `nuget pack <PATH_TO_NUSPEC_FILE>` příkazu. Následující příkaz předpokládá, že je složka, která obsahuje prostředky NuGet na *C:\Users\\\<uživatele > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*. Všude, kde umístění složky ve vašem systému, ale `nuget pack` příkazu zadat cestu k *nuspec* souboru:

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Publikování balíčku na nuget.org

Publikování balíčku NuGet, postupujte podle pokynů [vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tématu. Doporučujeme však, že není publikování kurz šablony nuget, jak je lze nikdy odstranit po publikování, jen delisted. Teď, když máte v podobě balíčku NuGet *nupkg* souborů, doporučujeme, abyste postupovali podle pokynů k instalaci šablony přímo z místní *nupkg* souboru.

### <a name="install-the-template-from-a-nuget-package"></a>Instalace šablony z balíčku NuGet

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Instalace šablony z místního *nupkg* souboru

Instalace šablony ze *nupkg* souboru, který je vytvořil, použijte `dotnet new` příkazů `-i|--install` možnost a zadejte cestu k *nupkg* souboru:

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Instalace šablony z balíčku NuGet uloženou v nuget.org

Pokud chcete nainstalovat z balíčku NuGet uloženou v nuget.org, použijte šablonu `dotnet new` příkazů `-i|--install` možnost a zadejte název balíčku NuGet:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> V příkladu je pouze pro demonstrační účely. Není k dispozici `GarciaSoftware.ConsoleTemplate.CSharp` balíček NuGet na nuget.org, a nedoporučujeme publikovat a využívat testovací šablony z NuGet. Pokud spustíte příkaz, nainstaluje se žádná šablona. Však můžete nainstalovat šablonu, která nebyla publikována na nuget.org odkazováním *nupkg* souboru přímo na vašem místním systému souborů, jak je znázorněno v předchozí části [instalaci z místní soubor nupkg šablony soubor](#install-the-template-from-the-local-nupkg-file).

Pokud byste o ni živé příklad toho, jak nainstalovat šablony z balíčků na nuget.org, můžete použít [NUnit 3 šablony pro dotnet nové](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Tato šablona nastaví projekt tak, aby pomocí testování částí NUnit. K jeho instalaci, použijte následující příkaz:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Pokud uvedete šablon pomocí `dotnet new -l`, uvidíte *NUnit 3 Test projektu* s krátký název *nunit* v seznamu šablon. Jste připraveni použít šablonu v další části.

![Okno konzoly NUnit šablony s ostatními šablonami](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a>Vytvoření projektu ze šablony

Po instalaci šablony z Nugetu, použijte šablonu pomocí provádí `dotnet new <TEMPLATE>` výstupní umístit příkaz z adresáře, kam chcete modulu šablon (Pokud používáte `-o|--output` můžete zadat konkrétní adresář). Další informace najdete v tématu [ `dotnet new` možnosti](~/docs/core/tools/dotnet-new.md#options). Zadejte krátký název šablony přímo `dotnet new` příkazu. Vytvoření projektu ze šablony NUnit, spusťte následující příkaz:

```console
dotnet new nunit
```

Konzola ukazuje, že projekt je vytvořen a že obnovení balíčků projektu. Po spuštění příkazu projekt je připravený k použití.

![Okno konzoly zobrazí výstup dotnet nové nunit včetně obnovení závislostí projektu](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Chcete-li odinstalovat šablonu z balíčku NuGet uloženou v nuget.org

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> V příkladu je pouze pro demonstrační účely. Není k dispozici `GarciaSoftware.ConsoleTemplate.CSharp` NuGet balíčků na nuget.org nebo nainstalovaných v .NET Core SDK. Pokud spustíte příkaz, odinstalovat balíček či šablonu a zobrazí se následující výjimka:
>
> > Nelze najít něco, co můžete odinstalovat nazývá "GarciaSoftware.ConsoleTemplate.CSharp".

Pokud jste nainstalovali [NUnit 3 šablony pro dotnet nové](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) a chcete ji odinstalovat, použijte následující příkaz:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Odinstalace šablony ze souboru místní nupkg

Pokud chcete odinstalovat šablony, nepokoušejte se použít cestu k *nupkg* souboru. *Pokus o odinstalaci šablony pomocí `dotnet new -u <PATH_TO_NUPKG_FILE>` selže.* Odkázat na balíček podle jeho `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Použít rozdělení systému souborů

K distribuci šablony, umístíte do složky šablony projektu v umístění přístupný pro uživatele ve vaší síti. Použití `dotnet new` příkazů `-i|--install` možnost a zadejte cestu ke složce šablon (projektu složku obsahující projekt a *. template.config* složky).

Kurz předpokládá, že šablona projektu jsou uloženy v *dokumenty a šablony* složce profilu uživatele. Z tohoto umístění instalace šablony pomocí následujícího příkazu nahraďte \<uživatele > název profilu uživatele:

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Vytvoření projektu ze šablony

Po instalaci šablony ze systému souborů pomocí šablony pomocí provádí `dotnet new <TEMPLATE>` výstupní umístit příkaz z adresáře, kam chcete modulu šablon (Pokud používáte `-o|--output` můžete zadat konkrétní adresář). Další informace najdete v tématu [ `dotnet new` možnosti](~/docs/core/tools/dotnet-new.md#options). Zadejte krátký název šablony přímo `dotnet new` příkazu.

Z nové složky projektu, který vytvořil *C:\Users\\\<uživatele > \Documents\Projects\MyConsoleApp*, vytvoření projektu z `garciaconsole` šablony:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Odinstalace šablony

Pokud jste vytvořili šablonu na vašem místním systému souborů v *C:\Users\\\<uživatele > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, odinstalujte ho pomocí `-u|--uninstall` přepínače a cestu do složky šablony:

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Chcete-li odinstalovat šablony z vašeho místního systému souborů, plně kvalifikovanou cestu. Například *C:\Users\\\<uživatele > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky nebudou.
> Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.

## <a name="see-also"></a>Viz také:

- [úložiště GitHub DotNet/šablonování Wiki](https://github.com/dotnet/templating/wiki)
- [úložiště GitHub DotNet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)
- [Jak vytvořit nové vlastní šablony pro dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* schématu na Store schématu JSON](http://json.schemastore.org/template)
