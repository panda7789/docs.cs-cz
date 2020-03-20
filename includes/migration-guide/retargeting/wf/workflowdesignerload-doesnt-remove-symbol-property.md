---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804655"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="71ee5-101">WorkflowDesigner.Load neodstraní vlastnost symbolu</span><span class="sxs-lookup"><span data-stu-id="71ee5-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71ee5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="71ee5-102">Details</span></span>|<span data-ttu-id="71ee5-103">Při cílení rozhraní .NET Framework 4.5 v návrháři pracovního postupu a <xref:System.Activities.Presentation.WorkflowDesigner.Load> načítání re-hostované 3.5 workflow s metodou, je vyvolána <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> při ukládání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="71ee5-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="71ee5-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="71ee5-104">Suggestion</span></span>|<span data-ttu-id="71ee5-105">Tato chyba se projevuje pouze při cílení rozhraní .NET Framework 4.5 v <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> návrháři pracovního postupu, takže ji lze obejít nastavením rozhraní 4.0 .NET Framework.Alternativně se může vyhnout problému pomocí <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody k načtení pracovního postupu namísto <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="71ee5-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="71ee5-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="71ee5-106">Scope</span></span>|<span data-ttu-id="71ee5-107">Hlavní</span><span class="sxs-lookup"><span data-stu-id="71ee5-107">Major</span></span>|
|<span data-ttu-id="71ee5-108">Version</span><span class="sxs-lookup"><span data-stu-id="71ee5-108">Version</span></span>|<span data-ttu-id="71ee5-109">4.5</span><span class="sxs-lookup"><span data-stu-id="71ee5-109">4.5</span></span>|
|<span data-ttu-id="71ee5-110">Typ</span><span class="sxs-lookup"><span data-stu-id="71ee5-110">Type</span></span>|<span data-ttu-id="71ee5-111">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="71ee5-111">Retargeting</span></span>|
|<span data-ttu-id="71ee5-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="71ee5-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
