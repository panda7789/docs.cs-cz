---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937117"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Přepínač kompatibility UseLegacyImages není podporován.

Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl zaveden v rozhraní .NET Framework 4.8, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Framework 4.8, přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility řeší možné problémy s škálováním obrázků ve scénářích ClickOnce v prostředích s vysokým dpi. Pokud je `true`přepínač nastaven na , umožňuje uživateli obnovit změnu velikosti starších bitů na displejích s vysokým rozlišením DPI, jejichž měřítko je nastaveno na více než 100 %. Další informace najdete [v tématu .NET Framework 4.8 Poznámky k verzi](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.

V rozhraní .NET `Switch.System.Windows.Forms.UseLegacyImages` Core není přepínač podporován.

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
