---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234668"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="9f1a1-101">Některá rozhraní API a přetahování pracovního postupu jsou popsané zastaralé</span><span class="sxs-lookup"><span data-stu-id="9f1a1-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9f1a1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9f1a1-102">Details</span></span>|<span data-ttu-id="9f1a1-103">Toto rozhraní API a přetažení pracovní postup je zastaralá a způsobí upozornění kompilátoru, že pokud aplikace je znovu sestavit na 4.5.</span><span class="sxs-lookup"><span data-stu-id="9f1a1-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>|
|<span data-ttu-id="9f1a1-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9f1a1-104">Suggestion</span></span>|<span data-ttu-id="9f1a1-105">Nové <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> by místo toho použít rozhraní API, které podporují operace s více objekty.</span><span class="sxs-lookup"><span data-stu-id="9f1a1-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="9f1a1-106">Alternativně lze potlačit upozornění sestavení nebo lze se vyhnout pomocí staršího kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9f1a1-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="9f1a1-107">Rozhraní API jsou stále podporovány.</span><span class="sxs-lookup"><span data-stu-id="9f1a1-107">The APIs are still supported.</span></span>|
|<span data-ttu-id="9f1a1-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9f1a1-108">Scope</span></span>|<span data-ttu-id="9f1a1-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="9f1a1-109">Minor</span></span>|
|<span data-ttu-id="9f1a1-110">Version</span><span class="sxs-lookup"><span data-stu-id="9f1a1-110">Version</span></span>|<span data-ttu-id="9f1a1-111">4.5</span><span class="sxs-lookup"><span data-stu-id="9f1a1-111">4.5</span></span>|
|<span data-ttu-id="9f1a1-112">Type</span><span class="sxs-lookup"><span data-stu-id="9f1a1-112">Type</span></span>|<span data-ttu-id="9f1a1-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="9f1a1-113">Retargeting</span></span>|
|<span data-ttu-id="9f1a1-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9f1a1-114">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
