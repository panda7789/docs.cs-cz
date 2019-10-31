---
title: Model Windows Forms zásadní změny – .NET Core
description: Obsahuje seznam nejnovějších změn v model Windows Forms pro .NET Core.
ms.date: 09/20/2019
ms.openlocfilehash: 2aac8c81372a36f00df1b7f3ccd3432409f6c834
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092906"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="2d438-103">Průlomové změny v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d438-103">Breaking changes in Windows Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d438-104">Tento článek je v rámci konstrukce.</span><span class="sxs-lookup"><span data-stu-id="2d438-104">This article is under construction.</span></span> <span data-ttu-id="2d438-105">Nejedná se o úplný seznam nejnovějších změn .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d438-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="2d438-106">Další informace o nejnovějších změnách .NET Core můžete v úložišti dotnet/Docs na GitHubu kontrolovat jednotlivé [problémy se změnami](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) .</span><span class="sxs-lookup"><span data-stu-id="2d438-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span>

<span data-ttu-id="2d438-107">Následuje seznam nejnovějších změn v model Windows Forms verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d438-107">The following is a list of breaking changes in Windows Forms by .NET Core version.</span></span>

## <a name="net-core-30-preview-9"></a><span data-ttu-id="2d438-108">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="2d438-108">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/remove-serializationattribute.md)]

## <a name="net-core-30-rc1"></a><span data-ttu-id="2d438-109">.NET Core 3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="2d438-109">.NET Core 3.0 RC1</span></span>

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/remove-duplicated-apis.md)]

## <a name="net-core-30"></a><span data-ttu-id="2d438-110">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2d438-110">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]
