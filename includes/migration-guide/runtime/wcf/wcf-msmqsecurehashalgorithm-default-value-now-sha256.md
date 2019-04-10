---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236195"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="122a8-101">WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256</span><span class="sxs-lookup"><span data-stu-id="122a8-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="122a8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="122a8-102">Details</span></span>|<span data-ttu-id="122a8-103">Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve službě WCF pro zprávy služby Msmq je SHA256.</span><span class="sxs-lookup"><span data-stu-id="122a8-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="122a8-104">V rozhraní .NET Framework 4.7 a dřívějších verzích je výchozí zprávu podpisový algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="122a8-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="122a8-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="122a8-105">Suggestion</span></span>|<span data-ttu-id="122a8-106">Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit změny tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code>části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="122a8-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="122a8-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="122a8-107">Scope</span></span>|<span data-ttu-id="122a8-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="122a8-108">Minor</span></span>|
|<span data-ttu-id="122a8-109">Version</span><span class="sxs-lookup"><span data-stu-id="122a8-109">Version</span></span>|<span data-ttu-id="122a8-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="122a8-110">4.7.1</span></span>|
|<span data-ttu-id="122a8-111">Type</span><span class="sxs-lookup"><span data-stu-id="122a8-111">Type</span></span>|<span data-ttu-id="122a8-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="122a8-112">Runtime</span></span>|
