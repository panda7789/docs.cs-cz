---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643968"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DomainUpDown. UseLegacyScrolling není podporován.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, který byl představen v .NET Framework 4.7.1.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.7.1 se přepínač kompatibility `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` povolil vývojářům, aby se odhlásili od nezávislých <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí. Přepínač obnovil chování starší verze, ve kterém se <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje v případě, že je přítomný kontextový text, a vývojář se musí před akcí <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce použít <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akci ovládacího prvku. Další informace naleznete v tématu [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
