---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617223"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="e93fd-101">Některá rozhraní API pro přetažení pracovního postupu jsou zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e93fd-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="e93fd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e93fd-102">Details</span></span>

<span data-ttu-id="e93fd-103">Rozhraní API pro přetažení tohoto pracovního postupu je zastaralé a způsobí upozornění kompilátoru, pokud je aplikace znovu vytvořená proti 4,5.</span><span class="sxs-lookup"><span data-stu-id="e93fd-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e93fd-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="e93fd-104">Suggestion</span></span>

<span data-ttu-id="e93fd-105"><xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName>Místo toho by se měla použít nová rozhraní API podporující operace s více objekty.</span><span class="sxs-lookup"><span data-stu-id="e93fd-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="e93fd-106">Alternativně lze upozornění sestavení potlačit nebo je lze zabránit pomocí staršího kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e93fd-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="e93fd-107">Rozhraní API jsou pořád podporovaná.</span><span class="sxs-lookup"><span data-stu-id="e93fd-107">The APIs are still supported.</span></span>

| <span data-ttu-id="e93fd-108">Name</span><span class="sxs-lookup"><span data-stu-id="e93fd-108">Name</span></span>    | <span data-ttu-id="e93fd-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e93fd-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e93fd-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e93fd-110">Scope</span></span>   | <span data-ttu-id="e93fd-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e93fd-111">Minor</span></span>       |
| <span data-ttu-id="e93fd-112">Verze</span><span class="sxs-lookup"><span data-stu-id="e93fd-112">Version</span></span> | <span data-ttu-id="e93fd-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e93fd-113">4.5</span></span>         |
| <span data-ttu-id="e93fd-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e93fd-114">Type</span></span>    | <span data-ttu-id="e93fd-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e93fd-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e93fd-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e93fd-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
