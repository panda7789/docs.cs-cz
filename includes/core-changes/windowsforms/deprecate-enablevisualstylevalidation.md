---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181815"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. EnableVisualStyleValidation není podporovaný.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility.`Switch.System.Windows.Forms.EnableVisualStyleValidation`

#### <a name="change-description"></a>Změnit popis

V .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru. 

V rozhraní .NET Core `Switch.System.Windows.Forms.EnableVisualStyleValidation` není přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
