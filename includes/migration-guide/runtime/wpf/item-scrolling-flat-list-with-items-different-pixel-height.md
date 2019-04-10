---
ms.openlocfilehash: 088ebad0f822f791d05a8a8dafb0f7fd74f5581a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234125"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Seznam bez stromové struktury s položek různé výšky pixel posouvání položek

|   |   |
|---|---|
|Podrobnosti|Když <xref:System.Windows.Controls.ItemsControl?displayProperty=name> zobrazuje kolekci pomocí virtualizace (<code>IsVirtualizing=true</code>) a položky posouvání (<code>ScrollUnit=Item</code>), a posune ovládací prvek k zobrazení položek se liší od jeho okolím, jejichž výšku v pixelech <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> Iteruje přes všechny položky v kolekci. Uživatelské rozhraní přestane reagovat při této iterace; Pokud kolekce je velká, to může být vnímané jako zablokování. Iterace dojde za jiných okolností, dokonce i v předchozích verzích rozhraní .NET Framework. Například dochází při posouvání pixel (<code>ScrollUnit=Pixel</code>) při zjištění položku s jinou výšku a při posouvání položek hierarchická data (, jako <xref:System.Windows.Controls.TreeView?displayProperty=name> nebo <xref:System.Windows.Controls.ItemsControl?displayProperty=name> s seskupení povoleno) při zjištění položka se odlišný počet podřízených položek než jeho okolím. Pro případ výšku položky posouvání a jiné pixel iterace byla zavedena v rozhraní .NET Framework 4.6.1 opravit chyby v rozložení hierarchická data.  Pokud jsou data s plochou (žádnou hierarchii) a rozhraní .NET Framework 4.6.2 není nutné ho v tomto případě není potřeba.|
|Doporučení|Dojde k iteraci v rozhraní .NET Framework 4.6.1, ale ne v dřívějších verzích – to znamená, pokud <xref:System.Windows.Controls.ItemsControl?displayProperty=name> je položka-posouvání plochý seznam s položkami jinou vyska - existují dvě náhrad:<ol><li>Nainstalujte rozhraní .NET Framework 4.6.2.</li><li>Nainstalujte opravu hotfix HR 1605 pro rozhraní .NET Framework 4.6.1.</li></ol>|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
