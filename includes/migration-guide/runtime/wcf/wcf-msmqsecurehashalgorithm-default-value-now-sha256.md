---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857203"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="fba4c-101">WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256</span><span class="sxs-lookup"><span data-stu-id="fba4c-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fba4c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fba4c-102">Details</span></span>|<span data-ttu-id="fba4c-103">Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve službě WCF pro zprávy služby Msmq je SHA256.</span><span class="sxs-lookup"><span data-stu-id="fba4c-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="fba4c-104">V rozhraní .NET Framework 4.7 a dřívějších verzích je výchozí zprávu podpisový algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="fba4c-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="fba4c-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="fba4c-105">Suggestion</span></span>|<span data-ttu-id="fba4c-106">Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit změny tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code>části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="fba4c-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="fba4c-107">Scope</span><span class="sxs-lookup"><span data-stu-id="fba4c-107">Scope</span></span>|<span data-ttu-id="fba4c-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="fba4c-108">Minor</span></span>|
|<span data-ttu-id="fba4c-109">Version</span><span class="sxs-lookup"><span data-stu-id="fba4c-109">Version</span></span>|<span data-ttu-id="fba4c-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="fba4c-110">4.7.1</span></span>|
|<span data-ttu-id="fba4c-111">type</span><span class="sxs-lookup"><span data-stu-id="fba4c-111">Type</span></span>|<span data-ttu-id="fba4c-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="fba4c-112">Runtime</span></span>|

