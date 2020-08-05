---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556152"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.

`Switch.System.Windows.Forms.EnableVisualStyleValidation`Přepínač kompatibility není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

V .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru.

V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3.0

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
