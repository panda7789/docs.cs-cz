---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857203"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="3305e-101">WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256</span><span class="sxs-lookup"><span data-stu-id="3305e-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3305e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3305e-102">Details</span></span>|<span data-ttu-id="3305e-103">Počínaje rozhraním .NET Framework 4.7.1 je výchozím algoritmem podepisování zpráv v wcf pro zprávy Msmq SHA256.</span><span class="sxs-lookup"><span data-stu-id="3305e-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="3305e-104">V rozhraní .NET Framework 4.7 a starších verzích je výchozí algoritmus podepisování zpráv SHA1.</span><span class="sxs-lookup"><span data-stu-id="3305e-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="3305e-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="3305e-105">Suggestion</span></span>|<span data-ttu-id="3305e-106">Pokud s touto změnou narazíte na problémy s kompatibilitou v rozhraní .NET Framework 4.7.1 <code>&lt;runtime&gt;</code>nebo novějším, můžete změnu odhlásit přidáním následujícího řádku do části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="3305e-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="3305e-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3305e-107">Scope</span></span>|<span data-ttu-id="3305e-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="3305e-108">Minor</span></span>|
|<span data-ttu-id="3305e-109">Version</span><span class="sxs-lookup"><span data-stu-id="3305e-109">Version</span></span>|<span data-ttu-id="3305e-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3305e-110">4.7.1</span></span>|
|<span data-ttu-id="3305e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3305e-111">Type</span></span>|<span data-ttu-id="3305e-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3305e-112">Runtime</span></span>|
