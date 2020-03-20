---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859116"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="16f9c-101">Zabezpečení zpráv WCF je nyní schopno používat TLS1.1 a TLS1.2</span><span class="sxs-lookup"><span data-stu-id="16f9c-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="16f9c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="16f9c-102">Details</span></span>|<span data-ttu-id="16f9c-103">Počínaje rozhraním .NET Framework 4.7 mohou zákazníci konfigurovat tls1.1 nebo TLS1.2 v zabezpečení zpráv WCF kromě SSL3.0 a TLS1.0 prostřednictvím nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="16f9c-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="16f9c-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="16f9c-104">Suggestion</span></span>|<span data-ttu-id="16f9c-105">V rozhraní .NET Framework 4.7 je ve výchozím nastavení zakázána podpora tls1.1 a TLS1.2 v zabezpečení zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="16f9c-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="16f9c-106">Můžete ji povolit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> oddílu souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="16f9c-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="16f9c-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="16f9c-107">Scope</span></span>|<span data-ttu-id="16f9c-108">Edge</span><span class="sxs-lookup"><span data-stu-id="16f9c-108">Edge</span></span>|
|<span data-ttu-id="16f9c-109">Version</span><span class="sxs-lookup"><span data-stu-id="16f9c-109">Version</span></span>|<span data-ttu-id="16f9c-110">4.7</span><span class="sxs-lookup"><span data-stu-id="16f9c-110">4.7</span></span>|
|<span data-ttu-id="16f9c-111">Typ</span><span class="sxs-lookup"><span data-stu-id="16f9c-111">Type</span></span>|<span data-ttu-id="16f9c-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="16f9c-112">Retargeting</span></span>|
