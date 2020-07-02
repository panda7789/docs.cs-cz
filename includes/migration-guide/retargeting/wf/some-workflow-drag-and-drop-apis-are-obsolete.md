---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617223"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Některá rozhraní API pro přetažení pracovního postupu jsou zastaralá.

#### <a name="details"></a>Podrobnosti

Rozhraní API pro přetažení tohoto pracovního postupu je zastaralé a způsobí upozornění kompilátoru, pokud je aplikace znovu vytvořená proti 4,5.

#### <a name="suggestion"></a>Návrh

<xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName>Místo toho by se měla použít nová rozhraní API podporující operace s více objekty. Alternativně lze upozornění sestavení potlačit nebo je lze zabránit pomocí staršího kompilátoru. Rozhraní API jsou pořád podporovaná.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
