---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937079"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, který byl představen v .NET Framework 4.7.2.

#### <a name="change-description"></a>Popis změny

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
