---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644031"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. UseLegacyImages není podporovaný.

Přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyImages`, který byl představen v .NET Framework 4,8, není podporován v model Windows Forms v rozhraní .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

Počínaje verzí .NET Framework 4,8 se `Switch.System.Windows.Forms.UseLegacyImages` přepínač kompatibility, který se zabývá možnými problémy s škálováním obrazu ve scénářích ClickOnce v prostředích s vysokým rozlišením DPI. Když nastavíte `true`, přepínač umožní uživateli obnovit velikost starší verze obrazu na vysokém rozlišení DPI, u kterých je měřítko nastavené na větší než 100%. Další informace najdete v [poznámkách k verzi .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.UseLegacyImages` podporován.

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
