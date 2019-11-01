---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198392"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="6b23d-101">Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.</span><span class="sxs-lookup"><span data-stu-id="6b23d-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="6b23d-102">Výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> se změnila z 2,0 na 1,1.</span><span class="sxs-lookup"><span data-stu-id="6b23d-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b23d-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6b23d-103">Version introduced</span></span>

<span data-ttu-id="6b23d-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6b23d-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="6b23d-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="6b23d-105">Change description</span></span>

<span data-ttu-id="6b23d-106">V .NET Core 1,0 až 2,0 je výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 1,1.</span><span class="sxs-lookup"><span data-stu-id="6b23d-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="6b23d-107">Počínaje .NET Core 2,1 se změnilo na 2,1.</span><span class="sxs-lookup"><span data-stu-id="6b23d-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="6b23d-108">Počínaje rozhraním .NET Core 3,0 je výchozí číslo verze vrácené vlastností <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> jednou znovu 1,1.</span><span class="sxs-lookup"><span data-stu-id="6b23d-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b23d-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6b23d-109">Recommended action</span></span>

<span data-ttu-id="6b23d-110">Aktualizujte kód, pokud závisí na vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> vracející výchozí hodnotu 2,0.</span><span class="sxs-lookup"><span data-stu-id="6b23d-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="6b23d-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6b23d-111">Category</span></span>

<span data-ttu-id="6b23d-112">Síťové služby</span><span class="sxs-lookup"><span data-stu-id="6b23d-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b23d-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6b23d-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

