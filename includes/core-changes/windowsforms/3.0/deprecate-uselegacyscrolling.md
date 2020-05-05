---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937116"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.

Přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .net Core 3,0.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.7.1 se přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility povolil vývojářům, aby se odhlásili jako nezávisle <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce. Přepínač obnovil chování starší verze, ve kterém <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> se ignoruje, pokud je přítomný kontextový text, a vývojář se musí před <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí použít akci na ovládacím prvku. Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

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

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
