---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620080"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus se volá opakovaně, pokud jeho obslužná rutina zobrazuje okno se zprávou model Windows Forms.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5, volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> obslužné rutiny způsobí, že se obslužná rutina znovu aktivuje při zavření okna se zprávou, což může vést k nekonečné smyčce oken se zprávami.

#### <a name="suggestion"></a>Návrh

Tento problém můžete vyřešit dvěma způsoby:<ol><li>Je možné se vyhnout voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> místo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> .</li><li>Je možné se vyhnout zobrazením okna se zprávou z <xref:System.Windows.UIElement.LostKeyboardFocus> obslužné rutiny události (na rozdíl od <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> obslužné rutiny události).</li></ol>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
