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
# <a name="breaking-changes-in-windows-forms"></a>Nejnovější změny ve formulářích Windows Forms

Podpora windows forms byla přidána do rozhraní .NET Core ve verzi 3.0. Tento článek uvádí nejnovější změny pro Windows Forms podle verze .NET Core, ve kterém byly zavedeny. Pokud upgradujete aplikaci pro Windows Forms z rozhraní .NET Framework nebo z předchozí verze rozhraní .NET Core (3.0 nebo novější), platí pro vás tento článek.

Na této stránce jsou popsány následující změny:

| Narušující změny | Zavedená verze |
| - | :-: |
| [WinForms API nyní vyvolat ArgumentNullException](#winforms-apis-now-throw-argumentnullexception) | 5.0 |
| [Odebrané ovládací prvky](#removed-controls) | 3.1 |
| [Událost CellFormatting není vyvolána, pokud je zobrazen popisek](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3.1 |
| [Control.DefaultFont změněn na Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt) | 3.0 |
| [Modernizace dialogového okna FolderBrowserDialog](#modernization-of-the-folderbrowserdialog) | 3.0 |
| [Serializovatelný atribut odebraný z některých typů formulářů systému Windows](#serializableattribute-removed-from-some-windows-forms-types) | 3.0 |
| [Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DomainUpDown.UseLegacyScrolling není podporován.](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility DontSupportReentrantFilterMessage není podporován.](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility EnableVisualStyleValidation není podporován.](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility UseLegacyContextMenuStripSourceSourceControlValue není podporován.](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3.0 |
| [Přepínač kompatibility UseLegacyImages není podporován.](#uselegacyimages-compatibility-switch-not-supported) | 3.0 |
| [Změna přístupu pro AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem) | 3.0 |
| [Duplicitní api odebraná z formulářů systému Windows Forms](#duplicated-apis-removed-from-windows-forms) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a>.NET Jádro 3.1

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

## <a name="see-also"></a>Viz také

- [Port aplikace Windows Forms na jádro .NET Core](../porting/winforms.md)
