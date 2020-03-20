---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857590"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Změna vlastnosti IsEnabled nadřazeného ovládacího prvku TextBlock ovlivní všechny podřízené ovládací prvky.

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6.2 má změna <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> <xref:System.Windows.Controls.TextBlock?displayProperty=name> vlastnosti nadřazeného ovládacího prvku vliv <xref:System.Windows.Controls.TextBlock?displayProperty=name> na všechny podřízené ovládací prvky (například hypertextové odkazy a tlačítka) ovládacího prvku. V rozhraní .NET Framework 4.6.1 a starší <xref:System.Windows.Controls.TextBlock?displayProperty=name> verze ovládací prvky <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> uvnitř ne <xref:System.Windows.Controls.TextBlock?displayProperty=name> vždy odrážet stav vlastnosti nadřazené.|
|Návrh|Žádné. Tato změna odpovídá očekávané chování pro <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládací prvky uvnitř ovládacího prvku.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
