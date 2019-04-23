---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981444"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="1b14e-101">HttpRuntime.AppDomainAppPath vyvolá NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="1b14e-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1b14e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1b14e-102">Details</span></span>|<span data-ttu-id="1b14e-103">V rozhraní .NET Framework 4.6.2, modul runtime vyvolá <code>T:System.NullReferenceException</code> při načítání <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> hodnotu, která obsahuje znaky s hodnotou null. V rozhraní .NET Framework 4.6.1 a starší verze, modul runtime vyvolá <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="1b14e-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="1b14e-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="1b14e-104">Suggestion</span></span>|<span data-ttu-id="1b14e-105">Můžete provést jeden z těchto kroků reagovat na tuto změnu:</span><span class="sxs-lookup"><span data-stu-id="1b14e-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="1b14e-106">Zpracování <code>T:System.NullReferenceException</code> Pokud aplikace běží na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="1b14e-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="1b14e-107">Upgrade na rozhraní .NET Framework 4.7, který obnoví předchozí chování a vyvolá <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="1b14e-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="1b14e-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1b14e-108">Scope</span></span>|<span data-ttu-id="1b14e-109">Edge</span><span class="sxs-lookup"><span data-stu-id="1b14e-109">Edge</span></span>|
|<span data-ttu-id="1b14e-110">Version</span><span class="sxs-lookup"><span data-stu-id="1b14e-110">Version</span></span>|<span data-ttu-id="1b14e-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="1b14e-111">4.6.2</span></span>|
|<span data-ttu-id="1b14e-112">Type</span><span class="sxs-lookup"><span data-stu-id="1b14e-112">Type</span></span>|<span data-ttu-id="1b14e-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="1b14e-113">Retargeting</span></span>|
|<span data-ttu-id="1b14e-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1b14e-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
