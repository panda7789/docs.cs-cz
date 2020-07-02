---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614537"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="b7fd6-101">Zabezpečení zpráv WCF teď může používat protokol TLS 1.1 a TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="b7fd6-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

#### <a name="details"></a><span data-ttu-id="b7fd6-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b7fd6-102">Details</span></span>

<span data-ttu-id="b7fd6-103">Počínaje .NET Framework 4,7 můžou zákazníci kromě nastavení konfigurace aplikace nakonfigurovat protokol TLS 1.1 nebo TLS 1.2 v zabezpečení zpráv WCF i na zabezpečení SSL 3.0 a TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="b7fd6-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b7fd6-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="b7fd6-104">Suggestion</span></span>

<span data-ttu-id="b7fd6-105">Ve výchozím nastavení je v .NET Framework 4,7 podporovaná podpora TLS 1.1 a TLS 1.2 v zabezpečení zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="b7fd6-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="b7fd6-106">Můžete ji povolit přidáním následujícího řádku do `<runtime>` oddílu app.config nebo web.config souboru:</span><span class="sxs-lookup"><span data-stu-id="b7fd6-106">You can enable it by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| <span data-ttu-id="b7fd6-107">Name</span><span class="sxs-lookup"><span data-stu-id="b7fd6-107">Name</span></span>    | <span data-ttu-id="b7fd6-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b7fd6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b7fd6-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b7fd6-109">Scope</span></span>   | <span data-ttu-id="b7fd6-110">Edge</span><span class="sxs-lookup"><span data-stu-id="b7fd6-110">Edge</span></span>        |
| <span data-ttu-id="b7fd6-111">Verze</span><span class="sxs-lookup"><span data-stu-id="b7fd6-111">Version</span></span> | <span data-ttu-id="b7fd6-112">4,7</span><span class="sxs-lookup"><span data-stu-id="b7fd6-112">4.7</span></span>         |
| <span data-ttu-id="b7fd6-113">Typ</span><span class="sxs-lookup"><span data-stu-id="b7fd6-113">Type</span></span>    | <span data-ttu-id="b7fd6-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b7fd6-114">Retargeting</span></span> |
