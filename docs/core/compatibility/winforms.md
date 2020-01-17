---
title: Model Windows Forms zásadní změny – .NET Core
description: Obsahuje seznam nejnovějších změn v model Windows Forms pro .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 44bcde60f9e08d2e06a69c55e4ebe904bf5c449b
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116454"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="ae7ec-103">Průlomové změny v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae7ec-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="ae7ec-104">Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="ae7ec-105">V tomto článku jsou uvedeny zásadní změny model Windows Forms ve verzi .NET Core, ve které byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="ae7ec-106">Pokud upgradujete model Windows Forms aplikaci z .NET Framework nebo z předchozí verze rozhraní .NET Core (3,0 nebo novější), můžete tento článek použít pro vás.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="ae7ec-107">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="ae7ec-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="ae7ec-108">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="ae7ec-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="ae7ec-109">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="ae7ec-110">Control. DefaultFont se změnil na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="ae7ec-111">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="ae7ec-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="ae7ec-112">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="ae7ec-113">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-114">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-115">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-116">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-117">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-118">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-119">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-120">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="ae7ec-121">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="ae7ec-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="ae7ec-122">Odebrala se duplicitní rozhraní API z model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ae7ec-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="ae7ec-123">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ae7ec-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="ae7ec-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ae7ec-124">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="ae7ec-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae7ec-125">See also</span></span>

- [<span data-ttu-id="ae7ec-126">Port model Windows Forms aplikace do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae7ec-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
