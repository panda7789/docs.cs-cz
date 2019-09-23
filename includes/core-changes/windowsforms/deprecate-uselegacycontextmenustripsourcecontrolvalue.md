---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181730"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue není podporovaný.

Přepínač `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` kompatibility, který byl představen v .NET Framework 4.7.2, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` přepínač kompatibility umožňuje vývojářům, aby se odhlásili od nového chování <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnosti, který nyní vrací odkaz na správu zdrojového kódu. Předchozí chování vlastnosti bylo vráceno `null`. Další informace naleznete v tématu [ \<AppContextSwitchOverrides > element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` není přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
