---
ms.openlocfilehash: d6c658f306dd4792e3cb5dbdc9471043ca95a071
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859195"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="bca20-101">HttpRuntime.AppDomainAppPath vyvolá NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="bca20-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bca20-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bca20-102">Details</span></span>|<span data-ttu-id="bca20-103">V rozhraní .NET Framework 4.6.2, modul runtime vyvolá <code>T:System.NullReferenceException</code> při načítání <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> hodnotu, která obsahuje znaky s hodnotou null. V rozhraní .NET Framework 4.6.1 a starší verze, modul runtime vyvolá <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="bca20-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="bca20-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="bca20-104">Suggestion</span></span>|<span data-ttu-id="bca20-105">Můžete provést jeden z těchto kroků reagovat na tuto změnu:</span><span class="sxs-lookup"><span data-stu-id="bca20-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="bca20-106">Zpracování <code>T:System.NullReferenceException</code> Pokud aplikace běží na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="bca20-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="bca20-107">Upgrade na rozhraní .NET Framework 4.7, který obnoví předchozí chování a vyvolá <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="bca20-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="bca20-108">Scope</span><span class="sxs-lookup"><span data-stu-id="bca20-108">Scope</span></span>|<span data-ttu-id="bca20-109">Edge</span><span class="sxs-lookup"><span data-stu-id="bca20-109">Edge</span></span>|
|<span data-ttu-id="bca20-110">Version</span><span class="sxs-lookup"><span data-stu-id="bca20-110">Version</span></span>|<span data-ttu-id="bca20-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="bca20-111">4.6.2</span></span>|
|<span data-ttu-id="bca20-112">type</span><span class="sxs-lookup"><span data-stu-id="bca20-112">Type</span></span>|<span data-ttu-id="bca20-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="bca20-113">Retargeting</span></span>|
|<span data-ttu-id="bca20-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bca20-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

