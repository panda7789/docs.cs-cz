---
title: Průlomové změny – .NET Framework do .NET Core
titleSuffix: ''
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 6a6cbffed5a54e3683832da54d408d77bb553cf1
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135621"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="6c2e5-103">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c2e5-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="6c2e5-104">Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="6c2e5-105">Zásadní změny jsou seskupené podle kategorií a v rámci těchto kategorií podle verze rozhraní .NET Core, ve které byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="6c2e5-106">Tento článek není úplný seznam průlomových změn mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="6c2e5-107">Nejdůležitější nedůležité změny se tady přidají, jak je máme vědět.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="6c2e5-108">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="6c2e5-108">Core .NET libraries</span></span>

- [<span data-ttu-id="6c2e5-109">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="6c2e5-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="6c2e5-110">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="6c2e5-111">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)

### <a name="net-core-21"></a><span data-ttu-id="6c2e5-112">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c2e5-112">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="6c2e5-113">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6c2e5-113">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="6c2e5-114">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="6c2e5-114">Cryptography</span></span>

- [<span data-ttu-id="6c2e5-115">Je respektován logický parametr SignedCms. ComputeSignature.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="6c2e5-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c2e5-116">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="6c2e5-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c2e5-117">Windows Forms</span></span>

<span data-ttu-id="6c2e5-118">Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-118">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="6c2e5-119">Pokud migrujete aplikaci model Windows Forms z .NET Framework na .NET Core, můžou se tyto změny týkat vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-119">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="6c2e5-120">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="6c2e5-120">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="6c2e5-121">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-121">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="6c2e5-122">Control. DefaultFont se změnil na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="6c2e5-123">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="6c2e5-123">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="6c2e5-124">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="6c2e5-125">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-125">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-126">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-126">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-127">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-127">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-128">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-129">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-129">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-130">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-131">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-131">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-132">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-132">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="6c2e5-133">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="6c2e5-133">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="6c2e5-134">Odebrala se duplicitní rozhraní API z model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c2e5-134">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="6c2e5-135">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="6c2e5-135">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="6c2e5-136">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6c2e5-136">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6c2e5-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c2e5-137">See also</span></span>

- [<span data-ttu-id="6c2e5-138">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c2e5-138">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="6c2e5-139">Technologie .NET Framework nedostupné v .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c2e5-139">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
