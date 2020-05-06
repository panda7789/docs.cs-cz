---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937117"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Přepínač kompatibility UseLegacyImages se nepodporuje.

Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4,8, není podporován v model Windows Forms v rozhraní .net Core 3,0.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4,8 se přepínač kompatibility, `Switch.System.Windows.Forms.UseLegacyImages` který se zabývá možnostmi problémy s škálováním obrazu ve scénářích ClickOnce v prostředích s VYSOKÝm rozlišením DPI. Když je tato `true`možnost nastavená na, přepínač umožní uživateli obnovit starší verzi obrazu na vysokém rozlišení DPI, jejichž škálování je nastavené na větší než 100%. Další informace najdete v [poznámkách k verzi .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.

V rozhraní .NET Core není `Switch.System.Windows.Forms.UseLegacyImages` přepínač podporován.

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
