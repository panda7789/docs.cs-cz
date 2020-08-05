---
title: model Windows Forms přerušující změny
description: Obsahuje seznam nejnovějších změn v model Windows Forms pro .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: beb9a42e4b5007f03480cd74f57bbfbbfc3f48b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556160"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="9fbb4-103">Průlomové změny v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9fbb4-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="9fbb4-104">Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="9fbb4-105">V tomto článku jsou uvedeny zásadní změny model Windows Forms ve verzi .NET Core, ve které byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="9fbb4-106">Pokud upgradujete model Windows Forms aplikaci z .NET Framework nebo z předchozí verze rozhraní .NET Core (3,0 nebo novější), můžete tento článek použít pro vás.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="9fbb4-107">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="9fbb4-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9fbb4-108">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="9fbb4-108">Breaking change</span></span> | <span data-ttu-id="9fbb4-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9fbb4-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9fbb4-110">Odebrané ovládací prvky stavového řádku</span><span class="sxs-lookup"><span data-stu-id="9fbb4-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="9fbb4-111">5.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-111">5.0</span></span> |
| [<span data-ttu-id="9fbb4-112">Metody WinForms teď vyvolávají výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="9fbb4-113">5.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-113">5.0</span></span> |
| [<span data-ttu-id="9fbb4-114">Metody WinForms teď vyvolávají ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="9fbb4-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="9fbb4-115">5.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-115">5.0</span></span> |
| [<span data-ttu-id="9fbb4-116">Vlastnosti WinForms teď vyvolávají výjimku ArgumentOutOfRangeException.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-116">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="9fbb4-117">5.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-117">5.0</span></span> |
| [<span data-ttu-id="9fbb4-118">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="9fbb4-118">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="9fbb4-119">3.1</span><span class="sxs-lookup"><span data-stu-id="9fbb4-119">3.1</span></span> |
| [<span data-ttu-id="9fbb4-120">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="9fbb4-121">3.1</span><span class="sxs-lookup"><span data-stu-id="9fbb4-121">3.1</span></span> |
| [<span data-ttu-id="9fbb4-122">Control. DefaultFont se změnil na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="9fbb4-123">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-123">3.0</span></span> |
| [<span data-ttu-id="9fbb4-124">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="9fbb4-124">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="9fbb4-125">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-125">3.0</span></span> |
| [<span data-ttu-id="9fbb4-126">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-126">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="9fbb4-127">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-127">3.0</span></span> |
| [<span data-ttu-id="9fbb4-128">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-128">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-129">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-129">3.0</span></span> |
| [<span data-ttu-id="9fbb4-130">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-130">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-131">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-131">3.0</span></span> |
| [<span data-ttu-id="9fbb4-132">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-132">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-133">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-133">3.0</span></span> |
| [<span data-ttu-id="9fbb4-134">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-134">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-135">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-135">3.0</span></span> |
| [<span data-ttu-id="9fbb4-136">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-137">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-137">3.0</span></span> |
| [<span data-ttu-id="9fbb4-138">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-138">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-139">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-139">3.0</span></span> |
| [<span data-ttu-id="9fbb4-140">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-140">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-141">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-141">3.0</span></span> |
| [<span data-ttu-id="9fbb4-142">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9fbb4-142">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="9fbb4-143">3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-143">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="9fbb4-144">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-144">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="9fbb4-145">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9fbb4-145">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="9fbb4-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9fbb4-146">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9fbb4-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fbb4-147">See also</span></span>

- [<span data-ttu-id="9fbb4-148">Port model Windows Forms aplikace do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9fbb4-148">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
