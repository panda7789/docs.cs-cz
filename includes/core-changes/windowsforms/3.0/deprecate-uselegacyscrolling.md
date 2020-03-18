---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937116"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility DomainUpDown.UseLegacyScrolling není podporován.

Přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility, který byl zaveden v rozhraní .NET Framework 4.7.1, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Framework 4.7.1 přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility umožnil <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> vývojářům odhlásit se z nezávislých a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí. Přepínač obnovil starší verze chování, <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve kterém je ignorována, pokud je přítomen <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> kontextový text a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> vývojář je povinen použít akci na ovládací prvek před akcí. Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` Core není přepínač podporován.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Odstraňte spínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

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
