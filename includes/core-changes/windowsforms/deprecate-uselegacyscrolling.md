---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181832"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DomainUpDown. UseLegacyScrolling není podporován.

Přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.7.1 se přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility povolil vývojářům, aby se odhlásili jako nezávisle <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce. Přepínač obnovil chování starší verze, ve kterém <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> se ignoruje, pokud je přítomný kontextový text, a vývojář se musí před <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> použít akci na ovládacím prvku. Další informace naleznete v tématu [ \<AppContextSwitchOverrides > element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

V rozhraní .NET Core `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` není přepínač podporován.

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
