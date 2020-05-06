---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937079"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.

Přepínač `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` kompatibility, který byl představen v .NET Framework 4.7.2, není podporován v model Windows Forms .net Core 3,0.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.7.2, přepínač `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` kompatibility umožňuje vývojářům, aby se odhlásili od nového chování <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnosti, který nyní vrací odkaz na správu zdrojového kódu. Předchozí chování vlastnosti bylo vráceno `null`. Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core není `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` přepínač podporován.

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
