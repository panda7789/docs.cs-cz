---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617247"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="15226-101">Typy WorkFlow 3.0 jsou zastaralé</span><span class="sxs-lookup"><span data-stu-id="15226-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="15226-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="15226-102">Details</span></span>

<span data-ttu-id="15226-103">Rozhraní API modelu Windows Workflow Foundation (WWF) 3.0 (tj. rozhraní z oboru názvů System.Workflow) jsou už zastaralá.</span><span class="sxs-lookup"><span data-stu-id="15226-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="15226-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="15226-104">Suggestion</span></span>

<span data-ttu-id="15226-105">Je vhodné místo nich používat nová rozhraní API WWF 4.0 (z oboru názvů System.Activities).</span><span class="sxs-lookup"><span data-stu-id="15226-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="15226-106">Příklad použití nových rozhraní API najdete [tady](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) a další pokyny jsou k dispozici [tady](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span><span class="sxs-lookup"><span data-stu-id="15226-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="15226-107">Rozhraní API WWF 3.0 se stále podporují, můžete je tedy případně použít. Upozornění na čas sestavení se vyhnete tím, že ho potlačíte nebo použijete starší kompilátor.</span><span class="sxs-lookup"><span data-stu-id="15226-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="15226-108">Name</span><span class="sxs-lookup"><span data-stu-id="15226-108">Name</span></span>    | <span data-ttu-id="15226-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="15226-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="15226-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="15226-110">Scope</span></span>   | <span data-ttu-id="15226-111">Hlavní</span><span class="sxs-lookup"><span data-stu-id="15226-111">Major</span></span>       |
| <span data-ttu-id="15226-112">Verze</span><span class="sxs-lookup"><span data-stu-id="15226-112">Version</span></span> | <span data-ttu-id="15226-113">4.5</span><span class="sxs-lookup"><span data-stu-id="15226-113">4.5</span></span>         |
| <span data-ttu-id="15226-114">Typ</span><span class="sxs-lookup"><span data-stu-id="15226-114">Type</span></span>    | <span data-ttu-id="15226-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="15226-115">Retargeting</span></span> |
