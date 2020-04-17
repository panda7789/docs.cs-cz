---
title: Co je nového v .NET Core 3.1
description: Další informace o nových funkcích v rozhraní .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b52615a3fb288a6ca0622deb83f4db3c8e3587fb
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607903"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="2de62-103">Co je nového v .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2de62-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="2de62-104">Tento článek popisuje, co je nového v rozhraní .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="2de62-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="2de62-105">Tato verze obsahuje menší vylepšení .NET Core 3.0, se zaměřením na malé, ale důležité opravy.</span><span class="sxs-lookup"><span data-stu-id="2de62-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="2de62-106">Nejdůležitější funkcí o .NET Core 3.1 je, že se jedná o [vydání dlouhodobé podpory (LTS).](#long-term-support)</span><span class="sxs-lookup"><span data-stu-id="2de62-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="2de62-107">Pokud používáte Visual Studio 2019, musíte aktualizovat na [Visual Studio 2019 verze 16.4 nebo novější,](https://visualstudio.microsoft.com/downloads/) abyste pracovali s projekty .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="2de62-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="2de62-108">Informace o novince ve Visual Studiu verze 16.4 najdete [v tématu Co je nového ve Visual Studiu 2019 verze 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="2de62-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="2de62-109">Visual Studio pro Mac také podporuje a obsahuje .NET Core 3.1 v Visual Studiu pro Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="2de62-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="2de62-110">Další informace o vydání naleznete v [oznámení .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="2de62-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="2de62-111">[Stáhněte si a s rozhraním .NET Core 3.1 můžete začít](https://dotnet.microsoft.com/download/dotnet-core/3.1) ve Windows, macOS nebo Linuxu.</span><span class="sxs-lookup"><span data-stu-id="2de62-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="2de62-112">Dlouhodobá podpora</span><span class="sxs-lookup"><span data-stu-id="2de62-112">Long-term support</span></span>

<span data-ttu-id="2de62-113">.NET Core 3.1 je verze LTS s podporou společnosti Microsoft pro příští tři roky.</span><span class="sxs-lookup"><span data-stu-id="2de62-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="2de62-114">Důrazně doporučujeme přesunout aplikace do .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="2de62-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="2de62-115">Aktuální životní cyklus ostatních hlavních verzí je následující:</span><span class="sxs-lookup"><span data-stu-id="2de62-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="2de62-116">Vydat</span><span class="sxs-lookup"><span data-stu-id="2de62-116">Release</span></span> | <span data-ttu-id="2de62-117">Poznámka</span><span class="sxs-lookup"><span data-stu-id="2de62-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="2de62-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2de62-118">.NET Core 3.0</span></span> | <span data-ttu-id="2de62-119">Konec životnosti 3. března 2020.</span><span class="sxs-lookup"><span data-stu-id="2de62-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="2de62-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2de62-120">.NET Core 2.2</span></span> | <span data-ttu-id="2de62-121">Konec životnosti dne 23.12.2019.</span><span class="sxs-lookup"><span data-stu-id="2de62-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="2de62-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2de62-122">.NET Core 2.1</span></span> | <span data-ttu-id="2de62-123">Konec životnosti 21. srpna 2021.</span><span class="sxs-lookup"><span data-stu-id="2de62-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="2de62-124">Další informace naleznete v [zásadách podpory jádra .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="2de62-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="2de62-125">aplikace macOSHost a notářská izace</span><span class="sxs-lookup"><span data-stu-id="2de62-125">macOS appHost and notarization</span></span>

<span data-ttu-id="2de62-126">*pouze macOS*</span><span class="sxs-lookup"><span data-stu-id="2de62-126">*macOS only*</span></span>

<span data-ttu-id="2de62-127">Počínaje notářsky oznamovaným rozhraním .NET Core SDK 3.1 pro macOS je nastavení appHost ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="2de62-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="2de62-128">Další informace najdete v [tématu macOS Catalina Notarization a dopad na stahování a projekty .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="2de62-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="2de62-129">Když je povoleno nastavení appHost, .NET Core generuje nativní Mach-O spustitelný soubor při vytváření nebo publikování.</span><span class="sxs-lookup"><span data-stu-id="2de62-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="2de62-130">Vaše aplikace běží v kontextu appHost při spuštění ze `dotnet run` zdrojového kódu pomocí příkazu nebo spuštěním spustitelného souboru Mach-O přímo.</span><span class="sxs-lookup"><span data-stu-id="2de62-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="2de62-131">Bez appHost, jediný způsob, jak uživatel může spustit aplikaci `dotnet <filename.dll>` [závislou na běhu](../deploying/index.md#publish-runtime-dependent) je pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="2de62-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="2de62-132">AppHost se vždy vytvoří, když publikujete aplikaci [samostatnou](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="2de62-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="2de62-133">Můžete buď nakonfigurovat appHost na úrovni projektu, nebo přepnout `dotnet` appHost `-p:UseAppHost` pro konkrétní příkaz s parametrem:</span><span class="sxs-lookup"><span data-stu-id="2de62-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="2de62-134">Soubor projektu</span><span class="sxs-lookup"><span data-stu-id="2de62-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="2de62-135">Parametr příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2de62-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="2de62-136">Další informace o `UseAppHost` nastavení naleznete v [tématu Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="2de62-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="2de62-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2de62-137">Windows Forms</span></span>

<span data-ttu-id="2de62-138">*Jen ve Windows*</span><span class="sxs-lookup"><span data-stu-id="2de62-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="2de62-139">Ve Formulářích Windows dojde k průlomové změny.</span><span class="sxs-lookup"><span data-stu-id="2de62-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="2de62-140">Starší ovládací prvky byly zahrnuty ve formulářích systému Windows, které byly po určitou dobu v panelu nástrojů aplikace Visual Studio Designer nedostupné.</span><span class="sxs-lookup"><span data-stu-id="2de62-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="2de62-141">Tyto byly nahrazeny nové ovládací prvky zpět v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="2de62-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="2de62-142">Tyto byly odebrány z sady Desktop SDK pro rozhraní .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="2de62-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="2de62-143">Odebraný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2de62-143">Removed control</span></span> | <span data-ttu-id="2de62-144">Doporučená výměna</span><span class="sxs-lookup"><span data-stu-id="2de62-144">Recommended replacement</span></span> | <span data-ttu-id="2de62-145">Přidružená api byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="2de62-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="2de62-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2de62-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="2de62-147">Datagridcell</span><span class="sxs-lookup"><span data-stu-id="2de62-147">DataGridCell</span></span><br/><span data-ttu-id="2de62-148">Datagridrow</span><span class="sxs-lookup"><span data-stu-id="2de62-148">DataGridRow</span></span><br/><span data-ttu-id="2de62-149">Sběr datagridtable</span><span class="sxs-lookup"><span data-stu-id="2de62-149">DataGridTableCollection</span></span><br/><span data-ttu-id="2de62-150">Datagridcolumncollection</span><span class="sxs-lookup"><span data-stu-id="2de62-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="2de62-151">Datagridtablestyle</span><span class="sxs-lookup"><span data-stu-id="2de62-151">DataGridTableStyle</span></span><br/><span data-ttu-id="2de62-152">Datagridcolumnstyle</span><span class="sxs-lookup"><span data-stu-id="2de62-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="2de62-153">Styl DataGridLine</span><span class="sxs-lookup"><span data-stu-id="2de62-153">DataGridLineStyle</span></span><br/><span data-ttu-id="2de62-154">Popisek DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="2de62-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="2de62-155">DataGridParentRowsLabelStyleStyle</span><span class="sxs-lookup"><span data-stu-id="2de62-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="2de62-156">Datagridboolcolumn</span><span class="sxs-lookup"><span data-stu-id="2de62-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="2de62-157">Datagridtextbox</span><span class="sxs-lookup"><span data-stu-id="2de62-157">DataGridTextBox</span></span><br/><span data-ttu-id="2de62-158">Gridcolumnstylescollection</span><span class="sxs-lookup"><span data-stu-id="2de62-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="2de62-159">Gridtablestylescollection</span><span class="sxs-lookup"><span data-stu-id="2de62-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="2de62-160">Typ přístupového typu</span><span class="sxs-lookup"><span data-stu-id="2de62-160">HitTestType</span></span> |
| <span data-ttu-id="2de62-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="2de62-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="2de62-162">Vzhled panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="2de62-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="2de62-163">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="2de62-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="2de62-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="2de62-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="2de62-165">Obslužné volání toolBarButtonClickEvent</span><span class="sxs-lookup"><span data-stu-id="2de62-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="2de62-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="2de62-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="2de62-167">Zarovnání panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="2de62-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="2de62-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="2de62-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="2de62-169">Kolekce položek MenuCollection</span><span class="sxs-lookup"><span data-stu-id="2de62-169">MenuItemCollection</span></span> |
| <span data-ttu-id="2de62-170">Mainmenu</span><span class="sxs-lookup"><span data-stu-id="2de62-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="2de62-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2de62-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="2de62-172">Doporučujeme aktualizovat aplikace na .NET Core 3.1 a přejít na náhradní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2de62-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="2de62-173">Nahrazení ovládacích prvků je jednoduchý proces, v podstatě "najít a nahradit" na typu.</span><span class="sxs-lookup"><span data-stu-id="2de62-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="2de62-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="2de62-174">C++/CLI</span></span>

<span data-ttu-id="2de62-175">*Jen ve Windows*</span><span class="sxs-lookup"><span data-stu-id="2de62-175">*Windows only*</span></span>

<span data-ttu-id="2de62-176">Byla přidána podpora pro vytváření projektů C++/CLI (označované také jako "spravované C++".</span><span class="sxs-lookup"><span data-stu-id="2de62-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="2de62-177">Binární soubory vytvořené z těchto projektů jsou kompatibilní s rozhraním .NET Core 3.0 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="2de62-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="2de62-178">Chcete-li přidat podporu pro C++/CLI ve Visual Studiu 2019 verze 16.4, nainstalujte [vývoj plochy s úlohami C++](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span><span class="sxs-lookup"><span data-stu-id="2de62-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="2de62-179">Tato úloha přidá do sady Visual Studio dvě šablony:</span><span class="sxs-lookup"><span data-stu-id="2de62-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="2de62-180">Knihovna tříd CLR (jádro.NET)</span><span class="sxs-lookup"><span data-stu-id="2de62-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="2de62-181">Prázdný projekt CLR (jádro.NET)</span><span class="sxs-lookup"><span data-stu-id="2de62-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="2de62-182">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2de62-182">Next steps</span></span>

- [<span data-ttu-id="2de62-183">Zkontrolujte nejnovější změny mezi .NET Core 3.0 a 3.1.</span><span class="sxs-lookup"><span data-stu-id="2de62-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="2de62-184">Projděte si nejnovější změny v rozhraní .NET Core 3.1 pro aplikace pro Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2de62-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
