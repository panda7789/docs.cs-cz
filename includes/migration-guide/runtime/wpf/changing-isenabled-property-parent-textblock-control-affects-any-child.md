---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803679"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Změna vlastnosti IsEnabled nadřazeného prvku TextBlock – ovládací prvek má vliv na všechny podřízené ovládací prvky

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, změna <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> vlastnost člena nadřazeného člena <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládací prvek má vliv na všechny podřízené ovládací prvky (jako jsou hypertextové odkazy a tlačítka) <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládacího prvku. V rozhraní .NET Framework 4.6.1 a dřívějších verzích, ovládací prvky uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=name> vždy neodrážejí stav <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> vlastnost <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadřazené.|
|Doporučení|Žádné Tato změna odpovídá očekávané chování u ovládacích prvků <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládacího prvku.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
