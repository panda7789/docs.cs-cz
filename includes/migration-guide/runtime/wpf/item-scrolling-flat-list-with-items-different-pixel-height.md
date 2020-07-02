---
ms.openlocfilehash: fbf3c0c8f1d11f9f5997a4d1027242c4710c7107
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621784"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Item – posouvání nestrukturovaného seznamu s položkami různých pixelů na výšku

#### <a name="details"></a>Podrobnosti

Když <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> zobrazí kolekci pomocí virtualizace ( <code>IsVirtualizing=true</code> ) a posouvání položek ( <code>ScrollUnit=Item</code> ), a když se ovládací prvek posune k zobrazení položky, jejíž výška v pixelech se liší od sousedů, <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> prochází všechny položky v kolekci. Uživatelské rozhraní nereaguje během této iterace; Pokud je kolekce velká, lze ji vnímat jako zablokování. K iteraci dochází v jiných případech, dokonce i v předchozích verzích .NET Framework. Například k tomu dochází, když se posune pixel ( <code>ScrollUnit=Pixel</code> ) při zjištění položky s jinou výškou, a když jsou hierarchická data posouvání položky (například <xref:System.Windows.Controls.TreeView?displayProperty=fullName> <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> s povoleným seskupováním) při zjištění položky s jiným počtem následníků, než je jejich soused. V případě posunu položek a jiné výšky v pixelech byl iterace představena v .NET Framework 4.6.1, aby opravila chyby v rozložení hierarchických dat.  Není potřeba, pokud jsou data plochá (bez hierarchie) a .NET Framework 4.6.2 v tomto případě to neudělá.

#### <a name="suggestion"></a>Návrh

Pokud se iterace vyskytne v .NET Framework 4.6.1, ale ne v dřívějších verzích – to znamená, že pokud se jedná o položku, která je v <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> nestrukturovaném seznamu s položkami jiné výšky v pixelech, existují dvě nápravná opatření:<ol><li>Nainstalujte .NET Framework 4.6.2.</li><li>Nainstalujte opravu hotfix HR 1605 pro .NET Framework 4.6.1.</li></ol>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
