---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803728"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="4abde-101">WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256</span><span class="sxs-lookup"><span data-stu-id="4abde-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4abde-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4abde-102">Details</span></span>|<span data-ttu-id="4abde-103">Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve službě WCF pro zprávy služby Msmq je SHA256.</span><span class="sxs-lookup"><span data-stu-id="4abde-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="4abde-104">V rozhraní .NET Framework 4.7 a dřívějších verzích je výchozí zprávu podpisový algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="4abde-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="4abde-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="4abde-105">Suggestion</span></span>|<span data-ttu-id="4abde-106">Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit změny tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code>části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="4abde-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="4abde-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4abde-107">Scope</span></span>|<span data-ttu-id="4abde-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="4abde-108">Minor</span></span>|
|<span data-ttu-id="4abde-109">Version</span><span class="sxs-lookup"><span data-stu-id="4abde-109">Version</span></span>|<span data-ttu-id="4abde-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4abde-110">4.7.1</span></span>|
|<span data-ttu-id="4abde-111">Type</span><span class="sxs-lookup"><span data-stu-id="4abde-111">Type</span></span>|<span data-ttu-id="4abde-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4abde-112">Runtime</span></span>|
