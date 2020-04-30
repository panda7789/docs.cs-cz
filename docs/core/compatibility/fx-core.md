---
title: Průlomové změny – .NET Framework do .NET Core
titleSuffix: ''
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: df5907e05c6a2aed478d64cc40c5d6f051f92f96
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595699"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Zásadní změny migrace z .NET Framework do .NET Core

Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku. Zásadní změny jsou seskupené podle kategorií a v rámci těchto kategorií podle verze rozhraní .NET Core, ve které byly zavedeny.

> [!NOTE]
> Tento článek není úplný seznam průlomových změn mezi .NET Framework a .NET Core. Nejdůležitější nedůležité změny se tady přidají, jak je máme vědět.

## <a name="core-net-libraries"></a>Knihovny Core .NET

- [Změna výchozí hodnoty UseShellExecute objektu Process](#change-in-default-value-of-useshellexecute)
- [UnauthorizedAccessException vyvolaná atributy SystemInfo.](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [Manipulace s poškozenými výjimkami stavu procesu není podporována.](#handling-corrupted-state-exceptions-is-not-supported)
- [Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.](#uribuilder-properties-no-longer-prepend-leading-characters)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

## <a name="cryptography"></a>Kryptografie

- [Je respektován logický parametr SignedCms. ComputeSignature.](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms. Pokud migrujete aplikaci model Windows Forms z .NET Framework na .NET Core, můžou se tyto změny týkat vaší aplikace.

- [Odebrané ovládací prvky](#removed-controls)
- [Pokud je zobrazený popis, událost CellFormatting se neaktivuje.](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control. DefaultFont se změnil na Segoe UI 9 bodů.](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernizace FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute byl odebrán z některých typů model Windows Forms.](#serializableattribute-removed-from-some-windows-forms-types)
- [Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Přepínač kompatibility UseLegacyImages se nepodporuje.](#uselegacyimages-compatibility-switch-not-supported)
- [Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Odebrala se duplicitní rozhraní API z model Windows Forms.](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Core 3,1

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

- [Rozhraní API, která vždy vyvolávají výjimky v .NET Core](unsupported-apis.md)
- [Technologie .NET Framework nedostupné v .NET Core](../porting/net-framework-tech-unavailable.md)
