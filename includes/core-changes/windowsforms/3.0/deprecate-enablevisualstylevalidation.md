---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721334"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.

`Switch.System.Windows.Forms.EnableVisualStyleValidation`V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility.

#### <a name="change-description"></a>Popis změny

V .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru.

V rozhraní .NET Core není `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
