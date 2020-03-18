---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451879"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="b87ef-101">Výchozí hodnota HttpRequestMessage.Version změněna na 1.1</span><span class="sxs-lookup"><span data-stu-id="b87ef-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="b87ef-102">Výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> se změnila z 2.0 na 1.1.</span><span class="sxs-lookup"><span data-stu-id="b87ef-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b87ef-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b87ef-103">Version introduced</span></span>

<span data-ttu-id="b87ef-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b87ef-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b87ef-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b87ef-105">Change description</span></span>

<span data-ttu-id="b87ef-106">V rozhraní .NET Core 1.0 až 2.0 je výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 1.1.</span><span class="sxs-lookup"><span data-stu-id="b87ef-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="b87ef-107">Počínaje rozhraním .NET Core 2.1 byl změněn na 2.1.</span><span class="sxs-lookup"><span data-stu-id="b87ef-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="b87ef-108">Počínaje rozhraním .NET Core 3.0 je <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> výchozí číslo verze vrácené vlastností opět 1.1.</span><span class="sxs-lookup"><span data-stu-id="b87ef-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b87ef-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b87ef-109">Recommended action</span></span>

<span data-ttu-id="b87ef-110">Aktualizujte kód, pokud <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> závisí na vlastnost vrácení výchozí hodnotu 2.0.</span><span class="sxs-lookup"><span data-stu-id="b87ef-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="b87ef-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b87ef-111">Category</span></span>

<span data-ttu-id="b87ef-112">Sítě</span><span class="sxs-lookup"><span data-stu-id="b87ef-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b87ef-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b87ef-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
