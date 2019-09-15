---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997587"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Item – posouvání nestrukturovaného seznamu s položkami různých pixelů na výšku

|   |   |
|---|---|
|Podrobnosti|Když zobrazí kolekci pomocí virtualizace (<code>IsVirtualizing=true</code>) a posouvání položek (<code>ScrollUnit=Item</code>), a když se ovládací prvek posune k zobrazení položky, jejíž výška v <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> pixelech se liší od sousedů, iterace všech <xref:System.Windows.Controls.ItemsControl?displayProperty=name> položky v kolekci. Uživatelské rozhraní nereaguje během této iterace; Pokud je kolekce velká, lze ji vnímat jako zablokování. K iteraci dochází v jiných případech, dokonce i v předchozích verzích .NET Framework. K tomu dochází například v případě, že se při<code>ScrollUnit=Pixel</code>zjištění položky s jinou výškou v pixelech posune pixely () a když se při <xref:System.Windows.Controls.TreeView?displayProperty=name> <xref:System.Windows.Controls.ItemsControl?displayProperty=name> zjištění položky s různý počet podřízených položek, než jsou sousední. V případě posunu položek a jiné výšky v pixelech byl iterace představena v .NET Framework 4.6.1, aby opravila chyby v rozložení hierarchických dat.  Není potřeba, pokud jsou data plochá (bez hierarchie) a .NET Framework 4.6.2 v tomto případě to neudělá.|
|Doporučení|Pokud se iterace vyskytne v .NET Framework 4.6.1, ale ne v dřívějších verzích – to znamená <xref:System.Windows.Controls.ItemsControl?displayProperty=name> , že pokud se jedná o položku, která je v nestrukturovaném seznamu s položkami jiné výšky v pixelech, existují dvě nápravná opatření:<ol><li>Nainstalujte .NET Framework 4.6.2.</li><li>Nainstalujte opravu hotfix HR 1605 pro .NET Framework 4.6.1.</li></ol>|
|Scope|Vedlejší|
|Version|4.6.1|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
