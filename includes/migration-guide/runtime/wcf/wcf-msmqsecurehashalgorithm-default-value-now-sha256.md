---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760431"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="8cbac-101">WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256</span><span class="sxs-lookup"><span data-stu-id="8cbac-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8cbac-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8cbac-102">Details</span></span>|<span data-ttu-id="8cbac-103">Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve službě WCF pro zprávy služby Msmq je SHA256.</span><span class="sxs-lookup"><span data-stu-id="8cbac-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="8cbac-104">V rozhraní .NET Framework 4.7 a dřívějších verzích je výchozí zprávu podpisový algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="8cbac-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="8cbac-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="8cbac-105">Suggestion</span></span>|<span data-ttu-id="8cbac-106">Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit změny tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code>části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="8cbac-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8cbac-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8cbac-107">Scope</span></span>|<span data-ttu-id="8cbac-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="8cbac-108">Minor</span></span>|
|<span data-ttu-id="8cbac-109">Version</span><span class="sxs-lookup"><span data-stu-id="8cbac-109">Version</span></span>|<span data-ttu-id="8cbac-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="8cbac-110">4.7.1</span></span>|
|<span data-ttu-id="8cbac-111">Type</span><span class="sxs-lookup"><span data-stu-id="8cbac-111">Type</span></span>|<span data-ttu-id="8cbac-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8cbac-112">Runtime</span></span>|

