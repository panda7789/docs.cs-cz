---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614492"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="a4575-101">Vazba WCF s režimem zabezpečení TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a4575-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="a4575-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a4575-102">Details</span></span>

<span data-ttu-id="a4575-103">Počínaje .NET Framework 4.6.1 může být vazba WCF, která používá režim zabezpečení TransportWithMessageCredential, nastavená tak, aby přijímala zprávy s nepodepsanými &quot; &quot; hlavičkami pro asymetrické zabezpečovací klíče. Ve výchozím nastavení &quot; &quot; budou v .NET Framework 4.6.1 nadále odmítány nepodepsané do hlaviček.</span><span class="sxs-lookup"><span data-stu-id="a4575-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="a4575-104">Budou přijaty pouze v případě, že se aplikace výslovný do tohoto nového režimu provozu pomocí Switch.System. AllowUnsignedToHeader konfigurační přepínač ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a4575-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a4575-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="a4575-105">Suggestion</span></span>

<span data-ttu-id="a4575-106">Vzhledem k tomu, že se jedná o funkci výslovného souhlasu, nemělo by to mít vliv na chování stávajících aplikací.</span><span class="sxs-lookup"><span data-stu-id="a4575-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="a4575-107">Chcete-li určit, zda je použito nové chování, nebo ne, použijte následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a4575-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="a4575-108">Name</span><span class="sxs-lookup"><span data-stu-id="a4575-108">Name</span></span>    | <span data-ttu-id="a4575-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a4575-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a4575-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a4575-110">Scope</span></span>   | <span data-ttu-id="a4575-111">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="a4575-111">Transparent</span></span> |
| <span data-ttu-id="a4575-112">Verze</span><span class="sxs-lookup"><span data-stu-id="a4575-112">Version</span></span> | <span data-ttu-id="a4575-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="a4575-113">4.6.1</span></span>       |
| <span data-ttu-id="a4575-114">Typ</span><span class="sxs-lookup"><span data-stu-id="a4575-114">Type</span></span>    | <span data-ttu-id="a4575-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="a4575-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a4575-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a4575-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
