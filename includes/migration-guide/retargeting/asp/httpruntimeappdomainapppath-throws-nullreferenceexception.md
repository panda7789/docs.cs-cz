---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617526"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="37381-101">HttpRuntime. AppDomainAppPath vyvolá NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="37381-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="37381-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="37381-102">Details</span></span>

<span data-ttu-id="37381-103">V .NET Framework 4.6.2 vyvolá modul runtime `T:System.NullReferenceException` při načítání `P:System.Web.HttpRuntime.AppDomainAppPath` hodnoty, která obsahuje znaky null. V .NET Framework 4.6.1 a dřívějších verzích vyvolá modul runtime `T:System.ArgumentNullException` .</span><span class="sxs-lookup"><span data-stu-id="37381-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="37381-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="37381-104">Suggestion</span></span>

<span data-ttu-id="37381-105">Na tuto změnu můžete reagovat jedním z těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="37381-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="37381-106">Zpracujte, `T:System.NullReferenceException` Pokud je aplikace spuštěná na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="37381-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="37381-107">Upgradujte na .NET Framework 4,7, který obnoví předchozí chování a vyvolá `T:System.ArgumentNullException` .</span><span class="sxs-lookup"><span data-stu-id="37381-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="37381-108">Name</span><span class="sxs-lookup"><span data-stu-id="37381-108">Name</span></span>    | <span data-ttu-id="37381-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37381-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="37381-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="37381-110">Scope</span></span>   | <span data-ttu-id="37381-111">Edge</span><span class="sxs-lookup"><span data-stu-id="37381-111">Edge</span></span>        |
| <span data-ttu-id="37381-112">Verze</span><span class="sxs-lookup"><span data-stu-id="37381-112">Version</span></span> | <span data-ttu-id="37381-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="37381-113">4.6.2</span></span>       |
| <span data-ttu-id="37381-114">Typ</span><span class="sxs-lookup"><span data-stu-id="37381-114">Type</span></span>    | <span data-ttu-id="37381-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="37381-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="37381-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="37381-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
