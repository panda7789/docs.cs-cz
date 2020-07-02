---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616043"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="e5aad-101">WorkflowDesigner. Load neodebere vlastnost symbol.</span><span class="sxs-lookup"><span data-stu-id="e5aad-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

#### <a name="details"></a><span data-ttu-id="e5aad-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e5aad-102">Details</span></span>

<span data-ttu-id="e5aad-103">Při cílení na .NET Framework 4,5 v Návrháři pracovních postupů a načítají se znovu hostovaný pracovní postup 3,5 s <xref:System.Activities.Presentation.WorkflowDesigner.Load> metodou, <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> je při ukládání pracovního postupu vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e5aad-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> is thrown while saving the workflow.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e5aad-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="e5aad-104">Suggestion</span></span>

<span data-ttu-id="e5aad-105">Tato chyba se manifestuje pouze v případě, že je v Návrháři pracovních postupů cílen .NET Framework 4,5, takže je možné ji vyřešit nastavením na `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` 4,0 .NET Framework. Alternativně lze problému zabránit pomocí <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody pro načtení pracovního postupu namísto <xref:System.Activities.Presentation.WorkflowDesigner.Load> .</span><span class="sxs-lookup"><span data-stu-id="e5aad-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>

| <span data-ttu-id="e5aad-106">Name</span><span class="sxs-lookup"><span data-stu-id="e5aad-106">Name</span></span>    | <span data-ttu-id="e5aad-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e5aad-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e5aad-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e5aad-108">Scope</span></span>   | <span data-ttu-id="e5aad-109">Hlavní</span><span class="sxs-lookup"><span data-stu-id="e5aad-109">Major</span></span>       |
| <span data-ttu-id="e5aad-110">Verze</span><span class="sxs-lookup"><span data-stu-id="e5aad-110">Version</span></span> | <span data-ttu-id="e5aad-111">4.5</span><span class="sxs-lookup"><span data-stu-id="e5aad-111">4.5</span></span>         |
| <span data-ttu-id="e5aad-112">Typ</span><span class="sxs-lookup"><span data-stu-id="e5aad-112">Type</span></span>    | <span data-ttu-id="e5aad-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e5aad-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e5aad-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e5aad-114">Affected APIs</span></span>

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
