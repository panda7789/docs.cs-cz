---
title: model Windows Forms přerušující změny
description: Obsahuje seznam nejnovějších změn v model Windows Forms pro .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 75d369c7fb999da81a50fe46716e125c3840eb7a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158434"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="c8a29-103">Průlomové změny v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8a29-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="c8a29-104">Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8a29-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="c8a29-105">V tomto článku jsou uvedeny zásadní změny model Windows Forms ve verzi .NET Core, ve které byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="c8a29-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="c8a29-106">Pokud upgradujete model Windows Forms aplikaci z .NET Framework nebo z předchozí verze rozhraní .NET Core (3,0 nebo novější), můžete tento článek použít pro vás.</span><span class="sxs-lookup"><span data-stu-id="c8a29-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="c8a29-107">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="c8a29-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c8a29-108">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="c8a29-108">Breaking change</span></span> | <span data-ttu-id="c8a29-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="c8a29-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c8a29-110">Odebrané ovládací prvky stavového řádku</span><span class="sxs-lookup"><span data-stu-id="c8a29-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="c8a29-111">5.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-111">5.0</span></span> |
| [<span data-ttu-id="c8a29-112">Metody WinForms teď vyvolávají výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="c8a29-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="c8a29-113">5.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-113">5.0</span></span> |
| [<span data-ttu-id="c8a29-114">Metody WinForms teď vyvolávají ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="c8a29-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="c8a29-115">5.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-115">5.0</span></span> |
| [<span data-ttu-id="c8a29-116">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c8a29-116">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="c8a29-117">3.1</span><span class="sxs-lookup"><span data-stu-id="c8a29-117">3.1</span></span> |
| [<span data-ttu-id="c8a29-118">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-118">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="c8a29-119">3.1</span><span class="sxs-lookup"><span data-stu-id="c8a29-119">3.1</span></span> |
| [<span data-ttu-id="c8a29-120">Control. DefaultFont se změnil na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="c8a29-120">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="c8a29-121">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-121">3.0</span></span> |
| [<span data-ttu-id="c8a29-122">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="c8a29-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="c8a29-123">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-123">3.0</span></span> |
| [<span data-ttu-id="c8a29-124">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8a29-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="c8a29-125">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-125">3.0</span></span> |
| [<span data-ttu-id="c8a29-126">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-126">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-127">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-127">3.0</span></span> |
| [<span data-ttu-id="c8a29-128">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-128">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-129">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-129">3.0</span></span> |
| [<span data-ttu-id="c8a29-130">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-130">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-131">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-131">3.0</span></span> |
| [<span data-ttu-id="c8a29-132">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-132">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-133">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-133">3.0</span></span> |
| [<span data-ttu-id="c8a29-134">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-134">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-135">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-135">3.0</span></span> |
| [<span data-ttu-id="c8a29-136">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-136">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-137">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-137">3.0</span></span> |
| [<span data-ttu-id="c8a29-138">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-139">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-139">3.0</span></span> |
| [<span data-ttu-id="c8a29-140">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c8a29-140">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="c8a29-141">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-141">3.0</span></span> |
| [<span data-ttu-id="c8a29-142">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="c8a29-142">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="c8a29-143">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-143">3.0</span></span> |
| [<span data-ttu-id="c8a29-144">Odebrala se duplicitní rozhraní API z model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8a29-144">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="c8a29-145">3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-145">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c8a29-146">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c8a29-146">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="c8a29-147">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c8a29-147">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="c8a29-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c8a29-148">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c8a29-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8a29-149">See also</span></span>

- [<span data-ttu-id="c8a29-150">Port model Windows Forms aplikace do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c8a29-150">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
