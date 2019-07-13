---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859116"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="c9658-101">Zabezpečení zpráv WCF je teď možné použít TLS1.1 a TLS1.2</span><span class="sxs-lookup"><span data-stu-id="c9658-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c9658-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c9658-102">Details</span></span>|<span data-ttu-id="c9658-103">Spuštění v rozhraní .NET Framework 4.7, zákazníci můžou nakonfigurovat TLS1.1 nebo TLS1.2 v zabezpečení zpráv WCF kromě SSL3.0 a protokol TLS 1.0 prostřednictvím nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9658-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="c9658-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c9658-104">Suggestion</span></span>|<span data-ttu-id="c9658-105">V rozhraní .NET Framework 4.7 je ve výchozím nastavení zakázána podpora TLS1.1 a TLS1.2 v zabezpečení zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="c9658-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="c9658-106">Můžete ji povolit tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="c9658-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="c9658-107">Scope</span><span class="sxs-lookup"><span data-stu-id="c9658-107">Scope</span></span>|<span data-ttu-id="c9658-108">Edge</span><span class="sxs-lookup"><span data-stu-id="c9658-108">Edge</span></span>|
|<span data-ttu-id="c9658-109">Version</span><span class="sxs-lookup"><span data-stu-id="c9658-109">Version</span></span>|<span data-ttu-id="c9658-110">4.7</span><span class="sxs-lookup"><span data-stu-id="c9658-110">4.7</span></span>|
|<span data-ttu-id="c9658-111">type</span><span class="sxs-lookup"><span data-stu-id="c9658-111">Type</span></span>|<span data-ttu-id="c9658-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="c9658-112">Retargeting</span></span>|

