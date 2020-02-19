---
title: Průlomové změny – .NET Framework do .NET Core
titleSuffix: ''
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449391"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="93021-103">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="93021-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="93021-104">Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="93021-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="93021-105">Zásadní změny jsou seskupené podle kategorií a v rámci těchto kategorií podle verze rozhraní .NET Core, ve které byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="93021-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="93021-106">Tento článek není úplný seznam průlomových změn mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="93021-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="93021-107">Nejdůležitější nedůležité změny se tady přidají, jak je máme vědět.</span><span class="sxs-lookup"><span data-stu-id="93021-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="93021-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="93021-108">CoreFx</span></span>

- [<span data-ttu-id="93021-109">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="93021-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="93021-110">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="93021-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a><span data-ttu-id="93021-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="93021-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="93021-112">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="93021-112">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="93021-113">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="93021-113">Cryptography</span></span>

- [<span data-ttu-id="93021-114">Je respektován logický parametr SignedCms. ComputeSignature.</span><span class="sxs-lookup"><span data-stu-id="93021-114">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="93021-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="93021-115">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="93021-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93021-116">Windows Forms</span></span>

<span data-ttu-id="93021-117">Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="93021-117">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="93021-118">Pokud migrujete aplikaci model Windows Forms z .NET Framework na .NET Core, můžou se tyto změny týkat vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="93021-118">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="93021-119">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="93021-119">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="93021-120">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="93021-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="93021-121">Control. DefaultFont se změnil na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="93021-121">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="93021-122">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="93021-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="93021-123">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="93021-123">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="93021-124">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-124">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-125">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-125">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-126">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-127">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-127">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-128">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-129">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-129">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-130">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-130">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-131">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="93021-131">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="93021-132">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="93021-132">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="93021-133">Odebrala se duplicitní rozhraní API z model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="93021-133">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="93021-134">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="93021-134">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="93021-135">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="93021-135">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="93021-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="93021-136">See also</span></span>

- [<span data-ttu-id="93021-137">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="93021-137">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="93021-138">Technologie .NET Framework nedostupné v .NET Core</span><span class="sxs-lookup"><span data-stu-id="93021-138">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
