---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621100"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="6cd6c-101">Pracovní postup teď vygeneruje původní výjimku místo NullReferenceException v některých případech.</span><span class="sxs-lookup"><span data-stu-id="6cd6c-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="6cd6c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6cd6c-102">Details</span></span>

<span data-ttu-id="6cd6c-103">V .NET Framework 4.6.2 a starších verzích, když metoda Execute aktivity pracovního postupu vyvolá výjimku s <code>null</code> hodnotou <xref:System.Exception.Message> vlastnosti, modul runtime pracovního postupu System. Activities vyvolá a <xref:System.NullReferenceException?displayProperty=fullName> maskuje původní výjimku. V .NET Framework 4,7 je vyvolána dříve maskovaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="6cd6c-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6cd6c-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="6cd6c-104">Suggestion</span></span>

<span data-ttu-id="6cd6c-105">Pokud váš kód spoléhá na zpracování <xref:System.NullReferenceException?displayProperty=fullName> , změňte ho na zachytit výjimky, které by mohly být vyvolány z vašich vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="6cd6c-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="6cd6c-106">Name</span><span class="sxs-lookup"><span data-stu-id="6cd6c-106">Name</span></span>    | <span data-ttu-id="6cd6c-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6cd6c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6cd6c-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6cd6c-108">Scope</span></span>   |<span data-ttu-id="6cd6c-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="6cd6c-109">Minor</span></span>|
|<span data-ttu-id="6cd6c-110">Verze</span><span class="sxs-lookup"><span data-stu-id="6cd6c-110">Version</span></span>|<span data-ttu-id="6cd6c-111">4,7</span><span class="sxs-lookup"><span data-stu-id="6cd6c-111">4.7</span></span>|
|<span data-ttu-id="6cd6c-112">Typ</span><span class="sxs-lookup"><span data-stu-id="6cd6c-112">Type</span></span>|<span data-ttu-id="6cd6c-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="6cd6c-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cd6c-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6cd6c-114">Affected APIs</span></span>

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
