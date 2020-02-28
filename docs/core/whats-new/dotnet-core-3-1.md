---
title: Co je nového v .NET Core 3.1
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3,1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156553"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="5c9bc-103">Co je nového v .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5c9bc-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="5c9bc-104">Tento článek popisuje, co je v .NET Core 3,1 novinkou.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="5c9bc-105">Tato verze obsahuje menší vylepšení .NET Core 3,0 a zaměřuje se na malé, ale důležité opravy.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="5c9bc-106">Nejdůležitější funkcí pro .NET Core 3,1 je, že se jedná o [dlouhodobou podporu (LTS)](#long-term-support) .</span><span class="sxs-lookup"><span data-stu-id="5c9bc-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="5c9bc-107">Pokud používáte Visual Studio 2019, musíte aktualizovat na [Visual studio 2019 verze 16,4](https://visualstudio.microsoft.com/downloads/) pro práci s projekty .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="5c9bc-108">Další informace o tom, co je nového v aplikaci Visual Studio, naleznete v tématu [novinky v aplikaci Visual studio 2019 verze 16,4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="5c9bc-108">For more information on what's new in Visual Studio, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="5c9bc-109">Visual Studio pro Mac také podporuje a zahrnuje .NET Core 3,1 v Visual Studio pro Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="5c9bc-110">Další informace o této verzi najdete v tématu [oznámení .NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="5c9bc-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="5c9bc-111">[Stáhněte si a začněte s .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) na Windows, MacOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="5c9bc-112">Dlouhodobá podpora</span><span class="sxs-lookup"><span data-stu-id="5c9bc-112">Long-term support</span></span>

<span data-ttu-id="5c9bc-113">.NET Core 3,1 je LTS verze s podporou Microsoftu pro následující tři roky.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="5c9bc-114">Důrazně doporučujeme přesunout své aplikace do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="5c9bc-115">Aktuální životní cyklus dalších hlavních vydání je následující:</span><span class="sxs-lookup"><span data-stu-id="5c9bc-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="5c9bc-116">Vydat</span><span class="sxs-lookup"><span data-stu-id="5c9bc-116">Release</span></span> | <span data-ttu-id="5c9bc-117">Poznámka</span><span class="sxs-lookup"><span data-stu-id="5c9bc-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="5c9bc-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5c9bc-118">.NET Core 3.0</span></span> | <span data-ttu-id="5c9bc-119">Konec životnosti 3. března 2020.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="5c9bc-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5c9bc-120">.NET Core 2.2</span></span> | <span data-ttu-id="5c9bc-121">Konec životnosti 23. prosince 2019.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="5c9bc-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c9bc-122">.NET Core 2.1</span></span> | <span data-ttu-id="5c9bc-123">Konec životnosti 21. srpna 2021.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="5c9bc-124">Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="5c9bc-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="5c9bc-125">macOS appHost a notarization</span><span class="sxs-lookup"><span data-stu-id="5c9bc-125">macOS appHost and notarization</span></span>

<span data-ttu-id="5c9bc-126">*jenom macOS*</span><span class="sxs-lookup"><span data-stu-id="5c9bc-126">*macOS only*</span></span>

<span data-ttu-id="5c9bc-127">Od notarized .NET Core SDK 3,1 pro macOS je nastavení appHost ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="5c9bc-128">Další informace najdete v tématu [MacOS Catalina notarization a dopad na stažení a projekty .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="5c9bc-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="5c9bc-129">Když je povolené nastavení appHost, .NET Core při sestavování nebo publikování generuje nativní spustitelný soubor strojového souboru.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="5c9bc-130">Vaše aplikace běží v kontextu appHost, když je spuštěná ze zdrojového kódu pomocí příkazu `dotnet run`, nebo spuštěním spustitelného souboru stroj-O přímo.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="5c9bc-131">Bez appHost je jediným způsobem, jak může uživatel spustit aplikaci [závislou na běhu](../deploying/index.md#publish-runtime-dependent) , je pomocí příkazu `dotnet <filename.dll>`.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="5c9bc-132">AppHost se vždy vytvoří při publikování [vlastní](../deploying/index.md#publish-self-contained)aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="5c9bc-133">Můžete buď nakonfigurovat appHost na úrovni projektu, nebo přepnout appHost pro konkrétní `dotnet` příkaz s parametrem `-p:UseAppHost`:</span><span class="sxs-lookup"><span data-stu-id="5c9bc-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="5c9bc-134">Soubor projektu</span><span class="sxs-lookup"><span data-stu-id="5c9bc-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="5c9bc-135">Parametr příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5c9bc-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="5c9bc-136">Další informace o nastavení `UseAppHost` naleznete v tématu [Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="5c9bc-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="5c9bc-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c9bc-137">Windows Forms</span></span>

<span data-ttu-id="5c9bc-138">*Pouze Windows*</span><span class="sxs-lookup"><span data-stu-id="5c9bc-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="5c9bc-139">V model Windows Forms došlo k zásadním změnám.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="5c9bc-140">Starší ovládací prvky byly zahrnuty do model Windows Forms, které byly v sadě nástrojů návrháře sady Visual Studio v některých časových intervalech nedostupné.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="5c9bc-141">Ty se nahradily novými ovládacími prvky zpátky v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="5c9bc-142">Ty se odebraly ze sady Desktop SDK pro .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="5c9bc-143">Odebraný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="5c9bc-143">Removed control</span></span> | <span data-ttu-id="5c9bc-144">Doporučená náhrada</span><span class="sxs-lookup"><span data-stu-id="5c9bc-144">Recommended replacement</span></span> | <span data-ttu-id="5c9bc-145">Odebraná přidružená rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5c9bc-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="5c9bc-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5c9bc-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="5c9bc-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="5c9bc-147">DataGridCell</span></span><br/><span data-ttu-id="5c9bc-148">Hodnota DataGridRow</span><span class="sxs-lookup"><span data-stu-id="5c9bc-148">DataGridRow</span></span><br/><span data-ttu-id="5c9bc-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="5c9bc-149">DataGridTableCollection</span></span><br/><span data-ttu-id="5c9bc-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="5c9bc-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="5c9bc-151">Styl DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="5c9bc-151">DataGridTableStyle</span></span><br/><span data-ttu-id="5c9bc-152">Styl DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="5c9bc-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="5c9bc-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="5c9bc-153">DataGridLineStyle</span></span><br/><span data-ttu-id="5c9bc-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="5c9bc-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="5c9bc-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="5c9bc-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="5c9bc-156">Funkce DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="5c9bc-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="5c9bc-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="5c9bc-157">DataGridTextBox</span></span><br/><span data-ttu-id="5c9bc-158">Kolekce GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="5c9bc-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="5c9bc-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="5c9bc-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="5c9bc-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="5c9bc-160">HitTestType</span></span> |
| <span data-ttu-id="5c9bc-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="5c9bc-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="5c9bc-162">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="5c9bc-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="5c9bc-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="5c9bc-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="5c9bc-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="5c9bc-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="5c9bc-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="5c9bc-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="5c9bc-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="5c9bc-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="5c9bc-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="5c9bc-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="5c9bc-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="5c9bc-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="5c9bc-169">MenuItemcollection</span><span class="sxs-lookup"><span data-stu-id="5c9bc-169">MenuItemCollection</span></span> |
| <span data-ttu-id="5c9bc-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="5c9bc-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="5c9bc-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="5c9bc-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="5c9bc-172">Doporučujeme aktualizovat aplikace na .NET Core 3,1 a přejít na ovládací prvky pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="5c9bc-173">Nahrazení ovládacích prvků je jednoduchý proces, v podstatě "najít a nahradit" na typ.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="5c9bc-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="5c9bc-174">C++/CLI</span></span>

<span data-ttu-id="5c9bc-175">*Pouze Windows*</span><span class="sxs-lookup"><span data-stu-id="5c9bc-175">*Windows only*</span></span>

<span data-ttu-id="5c9bc-176">Přidala se podpora pro vytváření C++projektů/CLI (označovaných také jako C++"spravované").</span><span class="sxs-lookup"><span data-stu-id="5c9bc-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="5c9bc-177">Binární soubory vytvořené z těchto projektů jsou kompatibilní s .NET Core 3,0 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="5c9bc-178">Pokud chcete přidat podporu C++pro/CLI v aplikaci Visual Studio 2019 verze 16,4, nainstalujte [desktopový C++ vývoj s](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)využitím úlohy.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="5c9bc-179">Tato úloha přidá dvě šablony do sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5c9bc-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="5c9bc-180">Knihovna tříd CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="5c9bc-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="5c9bc-181">Prázdný projekt CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="5c9bc-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="5c9bc-182">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5c9bc-182">Next steps</span></span>

- [<span data-ttu-id="5c9bc-183">Přečtěte si o nejnovějších změnách mezi .NET Core 3,0 a 3,1.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="5c9bc-184">Přečtěte si o nejnovějších změnách v .NET Core 3,1 pro aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5c9bc-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
