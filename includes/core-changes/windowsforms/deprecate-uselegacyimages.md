---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181793"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. UseLegacyImages není podporovaný.

Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4,8, není podporován v model Windows Forms v rozhraní .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4,8 se přepínač kompatibility, `Switch.System.Windows.Forms.UseLegacyImages` který se zabývá možnostmi problémy s škálováním obrazu ve scénářích ClickOnce v prostředích s vysokým rozlišením DPI. Když je tato `true`možnost nastavená na, přepínač umožní uživateli obnovit starší verzi obrazu na vysokém rozlišení DPI, jejichž škálování je nastavené na větší než 100%. Další informace najdete v [poznámkách k verzi .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.

V rozhraní .NET Core `Switch.System.Windows.Forms.UseLegacyImages` není přepínač podporován.

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
