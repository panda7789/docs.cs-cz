---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937014"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Přepínač kompatibility EnableVisualStyleValidation není podporován.

Přepínač `Switch.System.Windows.Forms.EnableVisualStyleValidation` kompatibility není ve Formulářích systému Windows v rozhraní .NET Core 3.0 podporován.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET `Switch.System.Windows.Forms.EnableVisualStyleValidation` Framework přepínač kompatibility povolil aplikaci odhlásit se z ověřování vizuálních stylů dodávaných v číselné podobě.

V rozhraní .NET `Switch.System.Windows.Forms.EnableVisualStyleValidation` Core není přepínač podporován.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Odstraňte spínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádný

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
