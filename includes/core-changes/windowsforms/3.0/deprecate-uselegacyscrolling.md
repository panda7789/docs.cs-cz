---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721512"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.

`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.7.1 se `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač kompatibility povolil vývojářům, aby se odhlásili jako nezávisle <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce. Přepínač obnovil chování starší verze, ve kterém se <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje, pokud je přítomný kontextový text, a vývojář se musí <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> před akcí použít akci na ovládacím prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Další informace naleznete v tématu [ \< AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core není `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač podporován.

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

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
