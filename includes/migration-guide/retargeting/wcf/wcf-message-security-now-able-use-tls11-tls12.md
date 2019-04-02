---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760200"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="8e999-101">Zabezpečení zpráv WCF je teď možné použít TLS1.1 a TLS1.2</span><span class="sxs-lookup"><span data-stu-id="8e999-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8e999-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8e999-102">Details</span></span>|<span data-ttu-id="8e999-103">Spuštění v rozhraní .NET Framework 4.7, zákazníci můžou nakonfigurovat TLS1.1 nebo TLS1.2 v zabezpečení zpráv WCF kromě SSL3.0 a protokol TLS 1.0 prostřednictvím nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e999-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="8e999-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="8e999-104">Suggestion</span></span>|<span data-ttu-id="8e999-105">V rozhraní .NET Framework 4.7 je ve výchozím nastavení zakázána podpora TLS1.1 a TLS1.2 v zabezpečení zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="8e999-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="8e999-106">Můžete ji povolit tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="8e999-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8e999-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8e999-107">Scope</span></span>|<span data-ttu-id="8e999-108">Edge</span><span class="sxs-lookup"><span data-stu-id="8e999-108">Edge</span></span>|
|<span data-ttu-id="8e999-109">Version</span><span class="sxs-lookup"><span data-stu-id="8e999-109">Version</span></span>|<span data-ttu-id="8e999-110">4.7</span><span class="sxs-lookup"><span data-stu-id="8e999-110">4.7</span></span>|
|<span data-ttu-id="8e999-111">Type</span><span class="sxs-lookup"><span data-stu-id="8e999-111">Type</span></span>|<span data-ttu-id="8e999-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="8e999-112">Retargeting</span></span>|

