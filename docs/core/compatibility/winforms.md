---
title: model Windows Forms přerušující změny
description: Obsahuje seznam nejnovějších změn v model Windows Forms pro .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: bd87e438ecf9930bfcd5377f9a3799d5f3693f49
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702465"
---
# <a name="breaking-changes-in-windows-forms"></a>Průlomové změny v model Windows Forms

Do .NET Core ve verzi 3,0 se přidala podpora model Windows Forms. V tomto článku jsou uvedeny zásadní změny model Windows Forms ve verzi .NET Core, ve které byly zavedeny. Pokud upgradujete model Windows Forms aplikaci z .NET Framework nebo z předchozí verze rozhraní .NET Core (3,0 nebo novější), můžete tento článek použít pro vás.

Na této stránce jsou popsány následující přerušující se změny:

| Zásadní změna | Představená verze |
| - | :-: |
| [Odebrané ovládací prvky stavového řádku](#removed-status-bar-controls) | 5.0 |
| [Metody WinForms teď vyvolávají výjimku ArgumentException.](#winforms-methods-now-throw-argumentexception) | 5.0 |
| [Metody WinForms teď vyvolávají ArgumentNullException](#winforms-methods-now-throw-argumentnullexception) | 5.0 |
| [Vlastnosti WinForms teď vyvolávají výjimku ArgumentOutOfRangeException.](#winforms-properties-now-throw-argumentoutofrangeexception) | 5.0 |
| [Odebrané ovládací prvky](#removed-controls) | 3.1 |
| [Pokud je zobrazený popis, událost CellFormatting se neaktivuje.](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3.1 |
| [Control. DefaultFont se změnil na Segoe UI 9 bodů.](#default-control-font-changed-to-segoe-ui-9-pt) | 3.0 |
| [Modernizace FolderBrowserDialog](#modernization-of-the-folderbrowserdialog) | 3.0 |
| [SerializableAttribute byl odebrán z některých typů model Windows Forms.](#serializableattribute-removed-from-some-windows-forms-types) | 3.0 |
| [Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility UseLegacyImages se nepodporuje.](#uselegacyimages-compatibility-switch-not-supported) | 3.0 |
| [Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem) | 3.0 |
| [Odebrala se duplicitní rozhraní API z model Windows Forms.](#duplicated-apis-removed-from-windows-forms) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a>.NET Core 3,1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Viz také:

- [Port model Windows Forms aplikace do .NET Core](../porting/winforms.md)
