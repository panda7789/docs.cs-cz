---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644017"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue není podporovaný.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, který byl představen v .NET Framework 4.7.2.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.7.2, přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` umožňuje vývojářům, aby se odhlásili od nového chování vlastnosti <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, která nyní vrací odkaz na správu zdrojového kódu. Předchozí chování vlastnosti vrátilo `null`. Další informace naleznete v tématu [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` podporován.

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
