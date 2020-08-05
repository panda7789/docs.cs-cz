---
title: Průlomové změny – .NET Framework do .NET Core
titleSuffix: ''
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 5f7424fdd959044b729dfb04f4f0147fbc946bfd
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556303"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="00ad3-103">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="00ad3-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="00ad3-104">Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="00ad3-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="00ad3-105">Zásadní změny jsou seskupené podle kategorií a v rámci těchto kategorií podle verze rozhraní .NET Core, ve které byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="00ad3-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="00ad3-106">Tento článek není úplný seznam průlomových změn mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00ad3-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="00ad3-107">Nejdůležitější nedůležité změny se tady přidají, jak je máme vědět.</span><span class="sxs-lookup"><span data-stu-id="00ad3-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="00ad3-108">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="00ad3-108">Core .NET libraries</span></span>

- [<span data-ttu-id="00ad3-109">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="00ad3-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="00ad3-110">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="00ad3-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="00ad3-111">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="00ad3-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)
- [<span data-ttu-id="00ad3-112">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="00ad3-112">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters)
- [<span data-ttu-id="00ad3-113">Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.</span><span class="sxs-lookup"><span data-stu-id="00ad3-113">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start)

### <a name="net-core-21"></a><span data-ttu-id="00ad3-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="00ad3-114">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="00ad3-115">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="00ad3-115">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***

## <a name="cryptography"></a><span data-ttu-id="00ad3-116">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="00ad3-116">Cryptography</span></span>

- [<span data-ttu-id="00ad3-117">Je respektován logický parametr SignedCms. ComputeSignature.</span><span class="sxs-lookup"><span data-stu-id="00ad3-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="00ad3-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="00ad3-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a><span data-ttu-id="00ad3-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="00ad3-119">MSBuild</span></span>

- [<span data-ttu-id="00ad3-120">Název souboru manifestu prostředku – změna</span><span class="sxs-lookup"><span data-stu-id="00ad3-120">Resource manifest file name change</span></span>](#resource-manifest-file-name-change)

### <a name="net-core-30"></a><span data-ttu-id="00ad3-121">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="00ad3-121">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a><span data-ttu-id="00ad3-122">Sítě</span><span class="sxs-lookup"><span data-stu-id="00ad3-122">Networking</span></span>

- [<span data-ttu-id="00ad3-123">WebClient. CancelAsync nevždycky zruší hned</span><span class="sxs-lookup"><span data-stu-id="00ad3-123">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a><span data-ttu-id="00ad3-124">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="00ad3-124">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="00ad3-125">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00ad3-125">Windows Forms</span></span>

<span data-ttu-id="00ad3-126">Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="00ad3-126">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="00ad3-127">Pokud migrujete aplikaci model Windows Forms z .NET Framework na .NET Core, můžou se tyto změny týkat vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="00ad3-127">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="00ad3-128">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="00ad3-128">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="00ad3-129">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-129">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="00ad3-130">Control. DefaultFont se změnil na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="00ad3-130">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="00ad3-131">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="00ad3-131">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="00ad3-132">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="00ad3-132">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="00ad3-133">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-133">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-134">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-134">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-135">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-135">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-136">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-136">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-137">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-137">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-138">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-138">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-139">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-139">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="00ad3-140">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="00ad3-140">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)

### <a name="net-core-31"></a><span data-ttu-id="00ad3-141">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="00ad3-141">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="00ad3-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="00ad3-142">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="00ad3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="00ad3-143">See also</span></span>

- [<span data-ttu-id="00ad3-144">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="00ad3-144">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="00ad3-145">Technologie .NET Framework nedostupné v .NET Core</span><span class="sxs-lookup"><span data-stu-id="00ad3-145">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
