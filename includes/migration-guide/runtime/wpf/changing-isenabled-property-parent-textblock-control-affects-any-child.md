---
ms.openlocfilehash: 38dd0b33202b8e8f1708ebec689333bd5367c93f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857590"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Změna vlastnosti IsEnabled nadřazeného prvku TextBlock – ovládací prvek má vliv na všechny podřízené ovládací prvky

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, změna <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> vlastnost člena nadřazeného člena <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládací prvek má vliv na všechny podřízené ovládací prvky (jako jsou hypertextové odkazy a tlačítka) <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládacího prvku. V rozhraní .NET Framework 4.6.1 a dřívějších verzích, ovládací prvky uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=name> vždy neodrážejí stav <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> vlastnost <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadřazené.|
|Doporučení|Žádné Tato změna odpovídá očekávané chování u ovládacích prvků <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládacího prvku.|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

