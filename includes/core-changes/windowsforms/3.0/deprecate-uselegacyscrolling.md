---
ms.openlocfilehash: ee4a27dde9f1e7756401e3d8b709514082f5d3b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556157"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.

`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.7.1 se `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač kompatibility povolil vývojářům, aby si nezávisle a akce odhlásili <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Přepínač obnovil chování starší verze, ve kterém se <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje, pokud je přítomný kontextový text, a vývojář se musí <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> před akcí použít akci na ovládacím prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3.0

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
