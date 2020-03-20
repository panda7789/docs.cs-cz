---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859195"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="ecf57-101">HttpRuntime.AppDomainAppPath vyvolá výjimku NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="ecf57-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ecf57-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ecf57-102">Details</span></span>|<span data-ttu-id="ecf57-103">V rozhraní .NET Framework 4.6.2 za <code>T:System.NullReferenceException</code> běhu vyvolá <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> při načítání hodnoty, která obsahuje znaky null. V rozhraní .NET Framework 4.6.1 a starších verzích za běhu vyvolá . <code>T:System.ArgumentNullException</code></span><span class="sxs-lookup"><span data-stu-id="ecf57-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="ecf57-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="ecf57-104">Suggestion</span></span>|<span data-ttu-id="ecf57-105">Můžete provést některou z následujících reagovat na tuto změnu:</span><span class="sxs-lookup"><span data-stu-id="ecf57-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="ecf57-106"><code>T:System.NullReferenceException</code> Zpracování, pokud je aplikace spuštěna v rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="ecf57-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="ecf57-107">Upgrade na rozhraní .NET Framework 4.7, který obnoví <code>T:System.ArgumentNullException</code>předchozí chování a vyvolá .</span><span class="sxs-lookup"><span data-stu-id="ecf57-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="ecf57-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ecf57-108">Scope</span></span>|<span data-ttu-id="ecf57-109">Edge</span><span class="sxs-lookup"><span data-stu-id="ecf57-109">Edge</span></span>|
|<span data-ttu-id="ecf57-110">Version</span><span class="sxs-lookup"><span data-stu-id="ecf57-110">Version</span></span>|<span data-ttu-id="ecf57-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ecf57-111">4.6.2</span></span>|
|<span data-ttu-id="ecf57-112">Typ</span><span class="sxs-lookup"><span data-stu-id="ecf57-112">Type</span></span>|<span data-ttu-id="ecf57-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="ecf57-113">Retargeting</span></span>|
|<span data-ttu-id="ecf57-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ecf57-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
