---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088482"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Některá rozhraní API a přetahování pracovního postupu jsou popsané zastaralé

|   |   |
|---|---|
|Podrobnosti|Toto rozhraní API a přetažení pracovní postup je zastaralá a způsobí upozornění kompilátoru, že pokud aplikace je znovu sestavit na 4.5.|
|Doporučení|Nové <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> by místo toho použít rozhraní API, které podporují operace s více objekty. Alternativně lze potlačit upozornění sestavení nebo lze se vyhnout pomocí staršího kompilátoru. Rozhraní API jsou stále podporovány.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
