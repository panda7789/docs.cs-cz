---
title: Změny rozdělení formulářů Systému Windows
description: Uvádí nejnovější změny ve formulářích Windows pro .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 25c568a8a0092a9c4874419c64c7dcebea4dce9e
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888111"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="c71c8-103">Nejnovější změny ve formulářích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c71c8-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="c71c8-104">Podpora windows forms byla přidána do rozhraní .NET Core ve verzi 3.0.</span><span class="sxs-lookup"><span data-stu-id="c71c8-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="c71c8-105">Tento článek uvádí nejnovější změny pro Windows Forms podle verze .NET Core, ve kterém byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="c71c8-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="c71c8-106">Pokud upgradujete aplikaci pro Windows Forms z rozhraní .NET Framework nebo z předchozí verze rozhraní .NET Core (3.0 nebo novější), platí pro vás tento článek.</span><span class="sxs-lookup"><span data-stu-id="c71c8-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="c71c8-107">Na této stránce jsou popsány následující změny:</span><span class="sxs-lookup"><span data-stu-id="c71c8-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c71c8-108">Narušující změny</span><span class="sxs-lookup"><span data-stu-id="c71c8-108">Breaking change</span></span> | <span data-ttu-id="c71c8-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="c71c8-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c71c8-110">WinForms API nyní vyvolat ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="c71c8-110">WinForms APIs now throw ArgumentNullException</span></span>](#winforms-apis-now-throw-argumentnullexception) | <span data-ttu-id="c71c8-111">5.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-111">5.0</span></span> |
| [<span data-ttu-id="c71c8-112">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c71c8-112">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="c71c8-113">3.1</span><span class="sxs-lookup"><span data-stu-id="c71c8-113">3.1</span></span> |
| [<span data-ttu-id="c71c8-114">Událost CellFormatting není vyvolána, pokud je zobrazen popisek</span><span class="sxs-lookup"><span data-stu-id="c71c8-114">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="c71c8-115">3.1</span><span class="sxs-lookup"><span data-stu-id="c71c8-115">3.1</span></span> |
| [<span data-ttu-id="c71c8-116">Control.DefaultFont změněn na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="c71c8-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="c71c8-117">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-117">3.0</span></span> |
| [<span data-ttu-id="c71c8-118">Modernizace dialogového okna FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="c71c8-118">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="c71c8-119">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-119">3.0</span></span> |
| [<span data-ttu-id="c71c8-120">Serializovatelný atribut odebraný z některých typů formulářů systému Windows</span><span class="sxs-lookup"><span data-stu-id="c71c8-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="c71c8-121">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-121">3.0</span></span> |
| [<span data-ttu-id="c71c8-122">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-122">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-123">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-123">3.0</span></span> |
| [<span data-ttu-id="c71c8-124">Přepínač kompatibility DomainUpDown.UseLegacyScrolling není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-124">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-125">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-125">3.0</span></span> |
| [<span data-ttu-id="c71c8-126">Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-127">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-127">3.0</span></span> |
| [<span data-ttu-id="c71c8-128">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován</span><span class="sxs-lookup"><span data-stu-id="c71c8-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-129">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-129">3.0</span></span> |
| [<span data-ttu-id="c71c8-130">Přepínač kompatibility DontSupportReentrantFilterMessage není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-130">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-131">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-131">3.0</span></span> |
| [<span data-ttu-id="c71c8-132">Přepínač kompatibility EnableVisualStyleValidation není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-132">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-133">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-133">3.0</span></span> |
| [<span data-ttu-id="c71c8-134">Přepínač kompatibility UseLegacyContextMenuStripSourceSourceControlValue není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-134">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-135">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-135">3.0</span></span> |
| [<span data-ttu-id="c71c8-136">Přepínač kompatibility UseLegacyImages není podporován.</span><span class="sxs-lookup"><span data-stu-id="c71c8-136">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="c71c8-137">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-137">3.0</span></span> |
| [<span data-ttu-id="c71c8-138">Změna přístupu pro AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="c71c8-138">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="c71c8-139">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-139">3.0</span></span> |
| [<span data-ttu-id="c71c8-140">Duplicitní api odebraná z formulářů systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c71c8-140">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="c71c8-141">3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-141">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c71c8-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-142">.NET 5.0</span></span>

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="c71c8-143">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="c71c8-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="c71c8-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c71c8-144">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c71c8-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="c71c8-145">See also</span></span>

- [<span data-ttu-id="c71c8-146">Port aplikace Windows Forms na jádro .NET Core</span><span class="sxs-lookup"><span data-stu-id="c71c8-146">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
