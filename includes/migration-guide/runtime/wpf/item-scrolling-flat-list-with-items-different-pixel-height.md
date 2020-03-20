---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997587"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Posouvání položek v plochém seznamu s položkami s různou výškou obrazových bodů

|   |   |
|---|---|
|Podrobnosti|Když <xref:System.Windows.Controls.ItemsControl?displayProperty=name> se zobrazí kolekce pomocí<code>IsVirtualizing=true</code>virtualizace ( )<code>ScrollUnit=Item</code>a položky posouvání ( ), a když ovládací prvek posouvá <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> zobrazení položky, jejíž výška v pixelech se liší od jeho sousedy, iteruje přes všechny položky v kolekci. Uživatelské rozhraní během této iterace neodpovídá. Pokud je kolekce velká, může to být vnímáno jako hang. Iterace se vyskytuje za jiných okolností, a to i v předchozích verzích rozhraní .NET Framework. Například k tomu dochází, když<code>ScrollUnit=Pixel</code>pixel-scrolling ( ) při setkání s položkou s jinou výškou obrazového bodu a když položky rolování hierarchická data (například <xref:System.Windows.Controls.TreeView?displayProperty=name> nebo <xref:System.Windows.Controls.ItemsControl?displayProperty=name> s seskupení povoleno) při setkání položky s jiným počtem položek následovníků než jeho sousedé. Pro případ posouvání položek a různé výšky pixelů byla iterace zavedena v rozhraní .NET Framework 4.6.1, aby opravila chyby v rozložení hierarchických dat.  Není potřeba, pokud jsou data plochá (žádná hierarchie) a rozhraní .NET Framework 4.6.2 v takovém případě neprovádí.|
|Návrh|Pokud dojde k iteraci v rozhraní .NET Framework 4.6.1, <xref:System.Windows.Controls.ItemsControl?displayProperty=name> ale ne v dřívějších verzích - to znamená, pokud je položka- posouvání plochý seznam s položkami různé výšky pixelů - existují dvě opravné prostředky:<ol><li>Nainstalujte rozhraní .NET Framework 4.6.2.</li><li>Nainstalujte opravu hotfix HR 1605 pro rozhraní .NET Framework 4.6.1.</li></ol>|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
