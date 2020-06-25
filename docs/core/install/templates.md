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
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="96f04-103">Správa projektů a šablon položek .NET</span><span class="sxs-lookup"><span data-stu-id="96f04-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="96f04-104">.NET Core poskytuje systém šablon, který umožňuje uživatelům instalovat nebo odinstalovat šablony ze služby NuGet, souboru balíčku NuGet nebo adresáře systému souborů.</span><span class="sxs-lookup"><span data-stu-id="96f04-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="96f04-105">Tento článek popisuje, jak spravovat šablony .NET Core prostřednictvím rozhraní příkazového řádku .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="96f04-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="96f04-106">Další informace o vytváření šablon najdete v tématu [kurz: vytvoření šablon](../tutorials/cli-templates-create-item-template.md).</span><span class="sxs-lookup"><span data-stu-id="96f04-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="96f04-107">Nainstalovat šablonu</span><span class="sxs-lookup"><span data-stu-id="96f04-107">Install template</span></span>

<span data-ttu-id="96f04-108">Šablony jsou nainstalovány prostřednictvím [dotnet new](../tools/dotnet-new.md) příkazu sady SDK s `-i` parametrem.</span><span class="sxs-lookup"><span data-stu-id="96f04-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="96f04-109">Můžete buď zadat identifikátor balíčku NuGet šablony, nebo složku, která obsahuje soubory šablon.</span><span class="sxs-lookup"><span data-stu-id="96f04-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="96f04-110">Hostovaný balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="96f04-110">NuGet hosted package</span></span>

<span data-ttu-id="96f04-111">Šablony rozhraní .NET CLI se nahrají do [NuGet](https://www.nuget.org/) pro rozsáhlou distribuci.</span><span class="sxs-lookup"><span data-stu-id="96f04-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="96f04-112">Šablony je také možné instalovat z privátního informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="96f04-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="96f04-113">Místo nahrání šablony do informačního kanálu NuGet lze soubory šablon *nupkg* distribuovat a ručně nainstalovat, jak je popsáno v části [místní balíček NuGet](#local-nuget-package) .</span><span class="sxs-lookup"><span data-stu-id="96f04-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="96f04-114">Další informace o konfiguraci kanálů NuGet najdete v tématu [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) .</span><span class="sxs-lookup"><span data-stu-id="96f04-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="96f04-115">K instalaci sady šablon z výchozího kanálu NuGet použijte `dotnet new -i {package-id}` příkaz:</span><span class="sxs-lookup"><span data-stu-id="96f04-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="96f04-116">Chcete-li nainstalovat sadu šablon z výchozího informačního kanálu NuGet s konkrétní verzí, použijte `dotnet new -i {package-id}::{version}` příkaz:</span><span class="sxs-lookup"><span data-stu-id="96f04-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="96f04-117">Místní balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="96f04-117">Local NuGet package</span></span>

<span data-ttu-id="96f04-118">Při vytvoření balíčku šablony se vygeneruje soubor *nupkg* .</span><span class="sxs-lookup"><span data-stu-id="96f04-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="96f04-119">Pokud máte soubor *nupkg* obsahující šablony, můžete ho nainstalovat pomocí `dotnet new -i {path-to-package}` příkazu:</span><span class="sxs-lookup"><span data-stu-id="96f04-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

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

### <a name="folder"></a><span data-ttu-id="96f04-120">Složka</span><span class="sxs-lookup"><span data-stu-id="96f04-120">Folder</span></span>

<span data-ttu-id="96f04-121">Jako alternativu k instalaci šablony ze souboru *nupkg* můžete také nainstalovat šablony ze složky přímo pomocí `dotnet new -i {folder-path}` příkazu.</span><span class="sxs-lookup"><span data-stu-id="96f04-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="96f04-122">Zadaná složka je považována za identifikátor sady šablon pro libovolnou nalezenou šablonu.</span><span class="sxs-lookup"><span data-stu-id="96f04-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="96f04-123">V hierarchii zadané složky se nainstalují všechny šablony.</span><span class="sxs-lookup"><span data-stu-id="96f04-123">Any template found in the specified folder's hierarchy is installed.</span></span>

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

<span data-ttu-id="96f04-124">`{folder-path}`Zadaný v příkazu se zobrazí jako identifikátor sady šablon pro všechny nalezené šablony.</span><span class="sxs-lookup"><span data-stu-id="96f04-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="96f04-125">Jak je uvedeno v části [šablony seznamu](#list-templates) , můžete získat seznam šablon nainstalovaných pomocí `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="96f04-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="96f04-126">V tomto příkladu je identifikátor sady šablon zobrazen jako složka použitá pro instalaci:</span><span class="sxs-lookup"><span data-stu-id="96f04-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

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

## <a name="uninstall-template"></a><span data-ttu-id="96f04-127">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="96f04-127">Uninstall template</span></span>

<span data-ttu-id="96f04-128">Šablony se odinstalují pomocí [dotnet new](../tools/dotnet-new.md) příkazu SDK s `-u` parametrem.</span><span class="sxs-lookup"><span data-stu-id="96f04-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="96f04-129">Můžete buď zadat identifikátor balíčku NuGet šablony, nebo složku, která obsahuje soubory šablon.</span><span class="sxs-lookup"><span data-stu-id="96f04-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="96f04-130">Balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="96f04-130">NuGet package</span></span>

<span data-ttu-id="96f04-131">Po instalaci balíčku šablon NuGet buď z kanálu NuGet, nebo ze souboru *nupkg* ho můžete odinstalovat pomocí odkazu na identifikátor balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="96f04-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="96f04-132">K odinstalaci sady šablon použijte `dotnet new -u {package-id}` příkaz:</span><span class="sxs-lookup"><span data-stu-id="96f04-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="96f04-133">Složka</span><span class="sxs-lookup"><span data-stu-id="96f04-133">Folder</span></span>

<span data-ttu-id="96f04-134">Pokud jsou šablony nainstalovány prostřednictvím [cesty ke složce](#folder), cesta ke složce se bude identifikátorem sady šablon.</span><span class="sxs-lookup"><span data-stu-id="96f04-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="96f04-135">K odinstalaci sady šablon použijte `dotnet new -u {package-folder-path}` příkaz:</span><span class="sxs-lookup"><span data-stu-id="96f04-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

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

## <a name="list-templates"></a><span data-ttu-id="96f04-136">Seznam šablon</span><span class="sxs-lookup"><span data-stu-id="96f04-136">List templates</span></span>

<span data-ttu-id="96f04-137">Pomocí příkazu standardní odinstalace bez identifikátoru balíčku se zobrazí seznam nainstalovaných šablon spolu s příkazem, který odinstaluje jednotlivé šablony.</span><span class="sxs-lookup"><span data-stu-id="96f04-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

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

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="96f04-138">Instalace šablon z jiných sad SDK</span><span class="sxs-lookup"><span data-stu-id="96f04-138">Install templates from other SDKs</span></span>

<span data-ttu-id="96f04-139">Pokud jste nainstalovali jednotlivé verze sady SDK postupně, například jste nainstalovali sadu SDK 2,0, potom sadu SDK 2,1 a tak dále, budete mít nainstalovány všechny šablony sady SDK.</span><span class="sxs-lookup"><span data-stu-id="96f04-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="96f04-140">Pokud však začnete s novější verzí sady SDK, například 3,1, jsou zahrnuty pouze šablony pro [LTS (dlouhodobá podpora)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což v době vydání sady SDK 3,1 je sada SDK 2,1 a sada SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="96f04-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="96f04-141">Šablony pro všechny ostatní vydané verze nejsou zahrnuté.</span><span class="sxs-lookup"><span data-stu-id="96f04-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="96f04-142">Šablony .NET Core jsou dostupné v NuGet a můžete je nainstalovat stejně jako jakoukoli jinou šablonu.</span><span class="sxs-lookup"><span data-stu-id="96f04-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="96f04-143">Další informace najdete v tématu [Instalace hostovaného balíčku NuGet](#nuget-hosted-package).</span><span class="sxs-lookup"><span data-stu-id="96f04-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="96f04-144">Sada SDK</span><span class="sxs-lookup"><span data-stu-id="96f04-144">SDK</span></span>              | <span data-ttu-id="96f04-145">Identifikátor balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="96f04-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="96f04-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="96f04-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="96f04-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="96f04-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="96f04-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="96f04-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="96f04-149">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="96f04-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="96f04-150">ASP.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="96f04-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="96f04-151">ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="96f04-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="96f04-152">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="96f04-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="96f04-153">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="96f04-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="96f04-154">Například .NET Core SDK obsahuje šablony pro konzolovou aplikaci cílící na rozhraní .NET Core 2,1 a .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="96f04-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="96f04-155">Pokud jste chtěli cílit na .NET Core 3,0, budete muset nainstalovat šablony 3,0.</span><span class="sxs-lookup"><span data-stu-id="96f04-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="96f04-156">Zkuste vytvořit aplikaci, která cílí na .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="96f04-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="96f04-157">Pokud se zobrazí chybová zpráva, je nutné nainstalovat šablony.</span><span class="sxs-lookup"><span data-stu-id="96f04-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="96f04-158">Nepovedlo se najít nainstalovanou šablonu, která by odpovídala vstupu, a hledá to online...</span><span class="sxs-lookup"><span data-stu-id="96f04-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="96f04-159">Nainstalujte šablony projektu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="96f04-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="96f04-160">Zkuste aplikaci vytvořit podruhé.</span><span class="sxs-lookup"><span data-stu-id="96f04-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="96f04-161">Měla by se zobrazit zpráva oznamující, že projekt byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="96f04-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="96f04-162">Šablona "Konzolová aplikace" byla úspěšně vytvořena.</span><span class="sxs-lookup"><span data-stu-id="96f04-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="96f04-163">Zpracovávají se akce po vytvoření... Spouští se dotnet restore v path-to-Project-File. csproj... Zjišťují se projekty, které se mají obnovit... Obnovení bylo dokončeno za 1,05 sec pro path-to-Project-File. csproj.</span><span class="sxs-lookup"><span data-stu-id="96f04-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="96f04-164">Obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="96f04-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="96f04-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="96f04-165">See also</span></span>

- [<span data-ttu-id="96f04-166">Kurz: Vytvoření šablony položky</span><span class="sxs-lookup"><span data-stu-id="96f04-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
