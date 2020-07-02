---
ms.openlocfilehash: c557f1cb65a675446bc77c57ef91972df92712bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617149"
---
### <a name="iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a><span data-ttu-id="6ef1e-101">Vlastnost IAsyncResult. CompletedSynchronously musí být správná, aby se výsledný úkol dokončil.</span><span class="sxs-lookup"><span data-stu-id="6ef1e-101">IAsyncResult.CompletedSynchronously property must be correct for the resulting task to complete</span></span>

#### <a name="details"></a><span data-ttu-id="6ef1e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6ef1e-102">Details</span></span>

<span data-ttu-id="6ef1e-103">Při volání TaskFactory. FromAsync <xref:System.IAsyncResult.CompletedSynchronously> musí být implementace vlastnosti správná, aby se výsledný úkol dokončil.</span><span class="sxs-lookup"><span data-stu-id="6ef1e-103">When calling TaskFactory.FromAsync, the implementation of the <xref:System.IAsyncResult.CompletedSynchronously> property must be correct for the resulting task to complete.</span></span> <span data-ttu-id="6ef1e-104">To znamená, že vlastnost musí vracet hodnotu true, pokud a pouze v případě, že implementace byla dokončena synchronně.</span><span class="sxs-lookup"><span data-stu-id="6ef1e-104">That is, the property must return true if, and only if, the implementation completed synchronously.</span></span> <span data-ttu-id="6ef1e-105">Dříve nebyla tato vlastnost zaškrtnuta.</span><span class="sxs-lookup"><span data-stu-id="6ef1e-105">Previously, the property was not checked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6ef1e-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="6ef1e-106">Suggestion</span></span>

<span data-ttu-id="6ef1e-107">Pokud <xref:System.IAsyncResult?displayProperty=fullName> implementace správně vrátí hodnotu true pro <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> vlastnost pouze v případě, že je úloha dokončena synchronně, nebude zaznamenáno žádné přerušení.</span><span class="sxs-lookup"><span data-stu-id="6ef1e-107">If <xref:System.IAsyncResult?displayProperty=fullName> implementations correctly return true for the <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> property only when a task completed synchronously, then no break will be observed.</span></span> <span data-ttu-id="6ef1e-108">Uživatelé by měli zkontrolovat implementace, které <xref:System.IAsyncResult?displayProperty=fullName> vlastní (pokud existují), aby se zajistilo, že správně vyhodnotí, jestli je úloha dokončená synchronně nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6ef1e-108">Users should review <xref:System.IAsyncResult?displayProperty=fullName> implementations they own (if any) to ensure that they correctly evaluate whether a task completed synchronously or not.</span></span>

| <span data-ttu-id="6ef1e-109">Name</span><span class="sxs-lookup"><span data-stu-id="6ef1e-109">Name</span></span>    | <span data-ttu-id="6ef1e-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ef1e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ef1e-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6ef1e-111">Scope</span></span>   | <span data-ttu-id="6ef1e-112">Edge</span><span class="sxs-lookup"><span data-stu-id="6ef1e-112">Edge</span></span>        |
| <span data-ttu-id="6ef1e-113">Verze</span><span class="sxs-lookup"><span data-stu-id="6ef1e-113">Version</span></span> | <span data-ttu-id="6ef1e-114">4.5</span><span class="sxs-lookup"><span data-stu-id="6ef1e-114">4.5</span></span>         |
| <span data-ttu-id="6ef1e-115">Typ</span><span class="sxs-lookup"><span data-stu-id="6ef1e-115">Type</span></span>    | <span data-ttu-id="6ef1e-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="6ef1e-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6ef1e-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6ef1e-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
