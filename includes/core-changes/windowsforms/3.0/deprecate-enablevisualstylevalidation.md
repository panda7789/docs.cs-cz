---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937014"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.

V `Switch.System.Windows.Forms.EnableVisualStyleValidation` model Windows Forms .net Core 3,0 není podporován přepínač kompatibility.

#### <a name="change-description"></a>Popis změny

V .NET Framework přepínač `Switch.System.Windows.Forms.EnableVisualStyleValidation` kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru.

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

### Affected APIs

- Not detectable via API analysis

-->
