---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621070"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="63114-101">Podporuje zápis zvláštního relativního identifikátoru URI, pokud je k dispozici Unicode</span><span class="sxs-lookup"><span data-stu-id="63114-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="63114-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="63114-102">Details</span></span>

<span data-ttu-id="63114-103"><xref:System.Uri>již nebude <xref:System.NullReferenceException> při volání <xref:System.Uri.TryCreate%2A> na určité relativní identifikátory URI obsahující kódování Unicode vyvolána.</span><span class="sxs-lookup"><span data-stu-id="63114-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="63114-104">Nejjednodušší reprodukce <xref:System.NullReferenceException> je níže, přičemž dva příkazy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="63114-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="63114-105">Aby bylo možné reprodukování <xref:System.NullReferenceException> , musí být splněny následující položky:</span><span class="sxs-lookup"><span data-stu-id="63114-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="63114-106">Identifikátor URI musí být zadaný jako relativní k tomu, aby byl s http: a za ním nenásleduje znakem//.</span><span class="sxs-lookup"><span data-stu-id="63114-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="63114-107">Identifikátor URI musí obsahovat znaky Unicode nebo nevyhrazené symboly zakódované v procentech.</span><span class="sxs-lookup"><span data-stu-id="63114-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="63114-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="63114-108">Suggestion</span></span>

<span data-ttu-id="63114-109">Uživatelé by měli v závislosti na tomto chování zakázat relativní identifikátory URI místo toho zadat <xref:System.UriKind.Absolute?displayProperty=nameWithType> při vytváření identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="63114-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="63114-110">Name</span><span class="sxs-lookup"><span data-stu-id="63114-110">Name</span></span>    | <span data-ttu-id="63114-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="63114-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="63114-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="63114-112">Scope</span></span>   |<span data-ttu-id="63114-113">Edge</span><span class="sxs-lookup"><span data-stu-id="63114-113">Edge</span></span>|
|<span data-ttu-id="63114-114">Verze</span><span class="sxs-lookup"><span data-stu-id="63114-114">Version</span></span>|<span data-ttu-id="63114-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="63114-115">4.7.2</span></span>|
|<span data-ttu-id="63114-116">Typ</span><span class="sxs-lookup"><span data-stu-id="63114-116">Type</span></span>|<span data-ttu-id="63114-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="63114-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63114-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63114-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
