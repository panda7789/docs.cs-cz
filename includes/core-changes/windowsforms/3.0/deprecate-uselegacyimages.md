---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556153"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Přepínač kompatibility UseLegacyImages se nepodporuje.

`Switch.System.Windows.Forms.UseLegacyImages`Přepínač kompatibility, který byl představen v .NET Framework 4,8, není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4,8 se přepínač kompatibility, který se `Switch.System.Windows.Forms.UseLegacyImages` zabývá možnostmi problémy s škálováním obrazu ve scénářích ClickOnce v prostředích s vysokým rozlišením. Když je tato možnost nastavená na `true` , přepínač umožní uživateli obnovit starší verzi obrazu na vysokém rozlišení DPI, jejichž škálování je nastavené na větší než 100%. Další informace najdete v [poznámkách k verzi .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.

V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.UseLegacyImages` přepínač podporován.

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
