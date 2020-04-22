---
title: Narušující změny - rozhraní .NET Framework na jádro .NET
titleSuffix: ''
description: Uvádí nejnovější změny z rozhraní .NET Framework na .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: ef16132c8dcffbe9bcfbe02834c9a78d6d0c33e4
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021791"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="db95b-103">Nejnovější změny pro migraci z rozhraní .NET Framework na .NET Core</span><span class="sxs-lookup"><span data-stu-id="db95b-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="db95b-104">Pokud migrujete aplikaci z rozhraní .NET Framework do .NET Core, mohou vás mít vliv narušující změny uvedené v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="db95b-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="db95b-105">Nejnovější změny jsou seskupeny podle kategorie a v rámci těchto kategorií podle verze .NET Core, ve kterém byly zavedeny.</span><span class="sxs-lookup"><span data-stu-id="db95b-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="db95b-106">Tento článek není úplný seznam narušující změny mezi rozhraním .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="db95b-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="db95b-107">Nejdůležitější změny jsou přidány zde, jak jsme se dozvěděli o nich.</span><span class="sxs-lookup"><span data-stu-id="db95b-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="db95b-108">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="db95b-108">Core .NET libraries</span></span>

- [<span data-ttu-id="db95b-109">Změna výchozí hodnoty useShellExecute</span><span class="sxs-lookup"><span data-stu-id="db95b-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="db95b-110">UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="db95b-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a><span data-ttu-id="db95b-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="db95b-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="db95b-112">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="db95b-112">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="db95b-113">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="db95b-113">Cryptography</span></span>

- [<span data-ttu-id="db95b-114">Logický parametr SignedCms.ComputeSignature je respektován</span><span class="sxs-lookup"><span data-stu-id="db95b-114">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="db95b-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="db95b-115">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="db95b-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db95b-116">Windows Forms</span></span>

<span data-ttu-id="db95b-117">Podpora windows forms byla přidána do rozhraní .NET Core ve verzi 3.0.</span><span class="sxs-lookup"><span data-stu-id="db95b-117">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="db95b-118">Pokud migrujete aplikaci windows forms z rozhraní .NET Framework na .NET Core, narušující změny uvedené zde mohou mít vliv na vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db95b-118">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="db95b-119">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="db95b-119">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="db95b-120">Událost CellFormatting není vyvolána, pokud je zobrazen popisek</span><span class="sxs-lookup"><span data-stu-id="db95b-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="db95b-121">Control.DefaultFont změněn na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="db95b-121">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="db95b-122">Modernizace dialogového okna FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="db95b-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="db95b-123">Serializovatelný atribut odebraný z některých typů formulářů systému Windows</span><span class="sxs-lookup"><span data-stu-id="db95b-123">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="db95b-124">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-124">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-125">Přepínač kompatibility DomainUpDown.UseLegacyScrolling není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-125">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-126">Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-127">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován</span><span class="sxs-lookup"><span data-stu-id="db95b-127">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-128">Přepínač kompatibility DontSupportReentrantFilterMessage není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-129">Přepínač kompatibility EnableVisualStyleValidation není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-129">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-130">Přepínač kompatibility UseLegacyContextMenuStripSourceSourceControlValue není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-130">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-131">Přepínač kompatibility UseLegacyImages není podporován.</span><span class="sxs-lookup"><span data-stu-id="db95b-131">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="db95b-132">Změna přístupu pro AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="db95b-132">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="db95b-133">Duplicitní api odebraná z formulářů systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db95b-133">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="db95b-134">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="db95b-134">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="db95b-135">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="db95b-135">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="db95b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="db95b-136">See also</span></span>

- [<span data-ttu-id="db95b-137">Rozhraní API, která vždy vyzvou výjimky na jádru .NET</span><span class="sxs-lookup"><span data-stu-id="db95b-137">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="db95b-138">Technologie rozhraní .NET Framework nejsou v jádru rozhraní .NET k dispozici</span><span class="sxs-lookup"><span data-stu-id="db95b-138">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
