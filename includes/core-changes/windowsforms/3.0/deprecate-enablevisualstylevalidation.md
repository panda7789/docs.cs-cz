---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937014"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.

Přepínač kompatibility `Switch.System.Windows.Forms.EnableVisualStyleValidation` není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

V .NET Framework přepínač kompatibility `Switch.System.Windows.Forms.EnableVisualStyleValidation` povolil aplikaci, aby se odhlásila od ověření vizuálních stylů dodaných v číselném tvaru.

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.EnableVisualStyleValidation` podporován.

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
