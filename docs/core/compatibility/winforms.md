---
title: Změny rozdělení formulářů Systému Windows
description: Uvádí nejnovější změny ve formulářích Windows pro .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399096"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="a7b64-103">Nejnovější změny ve formulářích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7b64-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="a7b64-104">Podpora windows forms byla přidána do rozhraní .NET Core ve verzi 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7b64-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="a7b64-105">Tento článek uvádí nejnovější změny pro Windows Forms podle verze .NET Core, ve kterém byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="a7b64-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="a7b64-106">Pokud upgradujete aplikaci pro Windows Forms z rozhraní .NET Framework nebo z předchozí verze rozhraní .NET Core (3.0 nebo novější), platí pro vás tento článek.</span><span class="sxs-lookup"><span data-stu-id="a7b64-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="a7b64-107">Na této stránce jsou popsány následující změny:</span><span class="sxs-lookup"><span data-stu-id="a7b64-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="a7b64-108">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="a7b64-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="a7b64-109">Událost CellFormatting není vyvolána, pokud je zobrazen popisek</span><span class="sxs-lookup"><span data-stu-id="a7b64-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="a7b64-110">Control.DefaultFont změněn na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="a7b64-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="a7b64-111">Modernizace dialogového okna FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="a7b64-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="a7b64-112">Serializovatelný atribut odebraný z některých typů formulářů systému Windows</span><span class="sxs-lookup"><span data-stu-id="a7b64-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="a7b64-113">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-114">Přepínač kompatibility DomainUpDown.UseLegacyScrolling není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-115">Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-116">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován</span><span class="sxs-lookup"><span data-stu-id="a7b64-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-117">Přepínač kompatibility DontSupportReentrantFilterMessage není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-118">Přepínač kompatibility EnableVisualStyleValidation není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-119">Přepínač kompatibility UseLegacyContextMenuStripSourceSourceControlValue není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-120">Přepínač kompatibility UseLegacyImages není podporován.</span><span class="sxs-lookup"><span data-stu-id="a7b64-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="a7b64-121">Změna přístupu pro AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="a7b64-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="a7b64-122">Duplicitní api odebraná z formulářů systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7b64-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="a7b64-123">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="a7b64-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="a7b64-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a7b64-124">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a7b64-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7b64-125">See also</span></span>

- [<span data-ttu-id="a7b64-126">Port aplikace Windows Forms na jádro .NET Core</span><span class="sxs-lookup"><span data-stu-id="a7b64-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
