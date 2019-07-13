---
ms.openlocfilehash: 71f61f23a8b17459610d253766a99e594f09428e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857209"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="5e6c1-101">Nyní používá SHA256 WCF PipeConnection.GetHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="5e6c1-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5e6c1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5e6c1-102">Details</span></span>|<span data-ttu-id="5e6c1-103">Od verze rozhraní .NET Framework 4.7.1, Windows Communication Foundation používá hodnotu hash SHA256 pro generování náhodných názvů u pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="5e6c1-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="5e6c1-104">V rozhraní .NET Framework 4.7 a dřívějších verzích používá hodnotu hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="5e6c1-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="5e6c1-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="5e6c1-105">Suggestion</span></span>|<span data-ttu-id="5e6c1-106">Pokud narazíte na potíže s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit ho tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="5e6c1-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="5e6c1-107">Scope</span><span class="sxs-lookup"><span data-stu-id="5e6c1-107">Scope</span></span>|<span data-ttu-id="5e6c1-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="5e6c1-108">Minor</span></span>|
|<span data-ttu-id="5e6c1-109">Version</span><span class="sxs-lookup"><span data-stu-id="5e6c1-109">Version</span></span>|<span data-ttu-id="5e6c1-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="5e6c1-110">4.7.1</span></span>|
|<span data-ttu-id="5e6c1-111">type</span><span class="sxs-lookup"><span data-stu-id="5e6c1-111">Type</span></span>|<span data-ttu-id="5e6c1-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5e6c1-112">Runtime</span></span>|

