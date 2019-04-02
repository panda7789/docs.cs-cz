---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760439"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="7c876-101">Pracovní postup vyvolá nyní původní výjimku namísto NullReferenceException v některých případech</span><span class="sxs-lookup"><span data-stu-id="7c876-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7c876-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7c876-102">Details</span></span>|<span data-ttu-id="7c876-103">V rozhraní .NET Framework 4.6.2 a předchozími verzemi, pokud metodu Execute aktivita pracovního postupu vyvolá výjimku <code>null</code> hodnota <xref:System.Exception.Message> vlastnost, modul runtime pracovního postupu System.Activities vyvolá výjimku <xref:System.NullReferenceException?displayProperty=name>, maskování původní výjimka. V rozhraní .NET Framework 4.7 je vyvolána výjimka dříve maskované.</span><span class="sxs-lookup"><span data-stu-id="7c876-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="7c876-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="7c876-104">Suggestion</span></span>|<span data-ttu-id="7c876-105">Pokud váš kód závisí na zpracování <xref:System.NullReferenceException?displayProperty=name>, změňte ho na zachytit výjimky, které mohou být vyvolány z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="7c876-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="7c876-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7c876-106">Scope</span></span>|<span data-ttu-id="7c876-107">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="7c876-107">Minor</span></span>|
|<span data-ttu-id="7c876-108">Version</span><span class="sxs-lookup"><span data-stu-id="7c876-108">Version</span></span>|<span data-ttu-id="7c876-109">4.7</span><span class="sxs-lookup"><span data-stu-id="7c876-109">4.7</span></span>|
|<span data-ttu-id="7c876-110">Type</span><span class="sxs-lookup"><span data-stu-id="7c876-110">Type</span></span>|<span data-ttu-id="7c876-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="7c876-111">Runtime</span></span>|
|<span data-ttu-id="7c876-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7c876-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

