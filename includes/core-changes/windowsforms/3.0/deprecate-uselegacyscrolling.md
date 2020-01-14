---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937116"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, který byl představen v .NET Framework 4.7.1.

#### <a name="change-description"></a>Popis změny

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
