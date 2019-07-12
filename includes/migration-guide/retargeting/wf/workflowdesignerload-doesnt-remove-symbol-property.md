---
ms.openlocfilehash: 97a92c6bce80b93e9a8bdd863bf881631eaffb27
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804655"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="4541d-101">WorkflowDesigner.Load neodebere vlastnost symbol</span><span class="sxs-lookup"><span data-stu-id="4541d-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4541d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4541d-102">Details</span></span>|<span data-ttu-id="4541d-103">Při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů a načítání 3.5 a znovu hostovaných pracovních postupů s <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> je vyvolána při ukládání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4541d-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="4541d-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="4541d-104">Suggestion</span></span>|<span data-ttu-id="4541d-105">Tato chyba projevuje pouze při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů, takže je možné pracovat kolem tak, že nastavíte <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> na 4.0 .NET Framework.Alternatively může být problém vyhnout použitím <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodu načtení pracovního postupu, místo <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="4541d-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="4541d-106">Scope</span><span class="sxs-lookup"><span data-stu-id="4541d-106">Scope</span></span>|<span data-ttu-id="4541d-107">Hlavní</span><span class="sxs-lookup"><span data-stu-id="4541d-107">Major</span></span>|
|<span data-ttu-id="4541d-108">Version</span><span class="sxs-lookup"><span data-stu-id="4541d-108">Version</span></span>|<span data-ttu-id="4541d-109">4.5</span><span class="sxs-lookup"><span data-stu-id="4541d-109">4.5</span></span>|
|<span data-ttu-id="4541d-110">type</span><span class="sxs-lookup"><span data-stu-id="4541d-110">Type</span></span>|<span data-ttu-id="4541d-111">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="4541d-111">Retargeting</span></span>|
|<span data-ttu-id="4541d-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4541d-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

