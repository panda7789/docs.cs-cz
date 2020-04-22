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
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Nejnovější změny pro migraci z rozhraní .NET Framework na .NET Core

Pokud migrujete aplikaci z rozhraní .NET Framework do .NET Core, mohou vás mít vliv narušující změny uvedené v tomto článku. Nejnovější změny jsou seskupeny podle kategorie a v rámci těchto kategorií podle verze .NET Core, ve kterém byly zavedeny.

> [!NOTE]
> Tento článek není úplný seznam narušující změny mezi rozhraním .NET Framework a .NET Core. Nejdůležitější změny jsou přidány zde, jak jsme se dozvěděli o nich.

## <a name="core-net-libraries"></a>Základní knihovny .NET

- [Změna výchozí hodnoty useShellExecute](#change-in-default-value-of-useshellexecute)
- [UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Jádro 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Kryptografie

- [Logický parametr SignedCms.ComputeSignature je respektován](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Podpora windows forms byla přidána do rozhraní .NET Core ve verzi 3.0. Pokud migrujete aplikaci windows forms z rozhraní .NET Framework na .NET Core, narušující změny uvedené zde mohou mít vliv na vaši aplikaci.

- [Odebrané ovládací prvky](#removed-controls)
- [Událost CellFormatting není vyvolána, pokud je zobrazen popisek](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont změněn na Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernizace dialogového okna FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [Serializovatelný atribut odebraný z některých typů formulářů systému Windows](#serializableattribute-removed-from-some-windows-forms-types)
- [Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Přepínač kompatibility DomainUpDown.UseLegacyScrolling není podporován.](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Přepínač kompatibility DontSupportReentrantFilterMessage není podporován.](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Přepínač kompatibility EnableVisualStyleValidation není podporován.](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Přepínač kompatibility UseLegacyContextMenuStripSourceSourceControlValue není podporován.](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Přepínač kompatibility UseLegacyImages není podporován.](#uselegacyimages-compatibility-switch-not-supported)
- [Změna přístupu pro AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Duplicitní api odebraná z formulářů systému Windows Forms](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Jádro 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Viz také

- [Rozhraní API, která vždy vyzvou výjimky na jádru .NET](unsupported-apis.md)
- [Technologie rozhraní .NET Framework nejsou v jádru rozhraní .NET k dispozici](../porting/net-framework-tech-unavailable.md)
