---
title: Instalace a Správa šablon sady SDK – .NET Core
description: Naučte se instalovat šablony .NET Core v systémech Windows, Linux a macOS.
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324488"
---
# <a name="manage-net-project-and-item-templates"></a>Správa projektů a šablon položek .NET

.NET Core poskytuje systém šablon, který umožňuje uživatelům instalovat nebo odinstalovat šablony ze služby NuGet, souboru balíčku NuGet nebo adresáře systému souborů. Tento článek popisuje, jak spravovat šablony .NET Core prostřednictvím rozhraní příkazového řádku .NET Core SDK.

Další informace o vytváření šablon najdete v tématu [kurz: vytvoření šablon](../tutorials/cli-templates-create-item-template.md).

## <a name="install-template"></a>Nainstalovat šablonu

Šablony jsou nainstalovány prostřednictvím [dotnet new](../tools/dotnet-new.md) příkazu sady SDK s `-i` parametrem. Můžete buď zadat identifikátor balíčku NuGet šablony, nebo složku, která obsahuje soubory šablon.

### <a name="nuget-hosted-package"></a>Hostovaný balíček NuGet

Šablony rozhraní .NET CLI se nahrají do [NuGet](https://www.nuget.org/) pro rozsáhlou distribuci. Šablony je také možné instalovat z privátního informačního kanálu. Místo nahrání šablony do informačního kanálu NuGet lze soubory šablon *nupkg* distribuovat a ručně nainstalovat, jak je popsáno v části [místní balíček NuGet](#local-nuget-package) .

Další informace o konfiguraci kanálů NuGet najdete v tématu [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) .

K instalaci sady šablon z výchozího kanálu NuGet použijte `dotnet new -i {package-id}` příkaz:

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

Chcete-li nainstalovat sadu šablon z výchozího informačního kanálu NuGet s konkrétní verzí, použijte `dotnet new -i {package-id}::{version}` příkaz:

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a>Místní balíček NuGet

Při vytvoření balíčku šablony se vygeneruje soubor *nupkg* . Pokud máte soubor *nupkg* obsahující šablony, můžete ho nainstalovat pomocí `dotnet new -i {path-to-package}` příkazu:

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a>Složka

Jako alternativu k instalaci šablony ze souboru *nupkg* můžete také nainstalovat šablony ze složky přímo pomocí `dotnet new -i {folder-path}` příkazu. Zadaná složka je považována za identifikátor sady šablon pro libovolnou nalezenou šablonu. V hierarchii zadané složky se nainstalují všechny šablony.

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

`{folder-path}`Zadaný v příkazu se zobrazí jako identifikátor sady šablon pro všechny nalezené šablony. Jak je uvedeno v části [šablony seznamu](#list-templates) , můžete získat seznam šablon nainstalovaných pomocí `dotnet new -u` příkazu. V tomto příkladu je identifikátor sady šablon zobrazen jako složka použitá pro instalaci:

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a>Odinstalace šablony

Šablony se odinstalují pomocí [dotnet new](../tools/dotnet-new.md) příkazu SDK s `-u` parametrem. Můžete buď zadat identifikátor balíčku NuGet šablony, nebo složku, která obsahuje soubory šablon.

### <a name="nuget-package"></a>Balíček NuGet

Po instalaci balíčku šablon NuGet buď z kanálu NuGet, nebo ze souboru *nupkg* ho můžete odinstalovat pomocí odkazu na identifikátor balíčku NuGet.

K odinstalaci sady šablon použijte `dotnet new -u {package-id}` příkaz:

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a>Složka

Pokud jsou šablony nainstalovány prostřednictvím [cesty ke složce](#folder), cesta ke složce se bude identifikátorem sady šablon.

K odinstalaci sady šablon použijte `dotnet new -u {package-folder-path}` příkaz:

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a>Seznam šablon

Pomocí příkazu standardní odinstalace bez identifikátoru balíčku se zobrazí seznam nainstalovaných šablon spolu s příkazem, který odinstaluje jednotlivé šablony.

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a>Instalace šablon z jiných sad SDK

Pokud jste nainstalovali jednotlivé verze sady SDK postupně, například jste nainstalovali sadu SDK 2,0, potom sadu SDK 2,1 a tak dále, budete mít nainstalovány všechny šablony sady SDK. Pokud však začnete s novější verzí sady SDK, například 3,1, jsou zahrnuty pouze šablony pro [LTS (dlouhodobá podpora)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což v době vydání sady SDK 3,1 je sada SDK 2,1 a sada SDK 3,1. Šablony pro všechny ostatní vydané verze nejsou zahrnuté.

Šablony .NET Core jsou dostupné v NuGet a můžete je nainstalovat stejně jako jakoukoli jinou šablonu. Další informace najdete v tématu [Instalace hostovaného balíčku NuGet](#nuget-hosted-package).

| Sada SDK              | Identifikátor balíčku NuGet                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| .NET Core 2.1    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| .NET Core 2.2    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| .NET Core 3.0    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| .NET Core 3,1    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| ASP.NET Core 2,1 | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| ASP.NET Core 2,2 | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| ASP.NET Core 3,0 | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| ASP.NET Core 3,1 | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

Například .NET Core SDK obsahuje šablony pro konzolovou aplikaci cílící na rozhraní .NET Core 2,1 a .NET Core 3,1. Pokud jste chtěli cílit na .NET Core 3,0, budete muset nainstalovat šablony 3,0.

01. Zkuste vytvořit aplikaci, která cílí na .NET Core 3,0.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Pokud se zobrazí chybová zpráva, je nutné nainstalovat šablony.

    > Nepovedlo se najít nainstalovanou šablonu, která by odpovídala vstupu, a hledá to online...

01. Nainstalujte šablony projektu .NET Core 3,0.

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. Zkuste aplikaci vytvořit podruhé.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Měla by se zobrazit zpráva oznamující, že projekt byl vytvořen.

    > Šablona "Konzolová aplikace" byla úspěšně vytvořena.
    >
    > Zpracovávají se akce po vytvoření... Spouští se dotnet restore v path-to-Project-File. csproj... Zjišťují se projekty, které se mají obnovit... Obnovení bylo dokončeno za 1,05 sec pro path-to-Project-File. csproj.
    >
    > Obnovení bylo úspěšné.

## <a name="see-also"></a>Viz také

- [Kurz: Vytvoření šablony položky](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
