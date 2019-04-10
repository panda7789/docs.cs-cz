---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234674"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="71da9-101">WorkflowDesigner.Load neodebere vlastnost symbol</span><span class="sxs-lookup"><span data-stu-id="71da9-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71da9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="71da9-102">Details</span></span>|<span data-ttu-id="71da9-103">Při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů a načítání 3.5 a znovu hostovaných pracovních postupů s <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> je vyvolána při ukládání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="71da9-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="71da9-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="71da9-104">Suggestion</span></span>|<span data-ttu-id="71da9-105">Tato chyba projevuje pouze při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů, takže je možné pracovat kolem tak, že nastavíte <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> na 4.0 .NET Framework.Alternatively může být problém vyhnout použitím <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodu načtení pracovního postupu, místo <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="71da9-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="71da9-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="71da9-106">Scope</span></span>|<span data-ttu-id="71da9-107">Hlavní</span><span class="sxs-lookup"><span data-stu-id="71da9-107">Major</span></span>|
|<span data-ttu-id="71da9-108">Version</span><span class="sxs-lookup"><span data-stu-id="71da9-108">Version</span></span>|<span data-ttu-id="71da9-109">4.5</span><span class="sxs-lookup"><span data-stu-id="71da9-109">4.5</span></span>|
|<span data-ttu-id="71da9-110">Type</span><span class="sxs-lookup"><span data-stu-id="71da9-110">Type</span></span>|<span data-ttu-id="71da9-111">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="71da9-111">Retargeting</span></span>|
|<span data-ttu-id="71da9-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="71da9-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
