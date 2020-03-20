---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857209"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="ab55c-101">WCF PipeConnection.GetHashAlgorithm nyní používá SHA256</span><span class="sxs-lookup"><span data-stu-id="ab55c-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ab55c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ab55c-102">Details</span></span>|<span data-ttu-id="ab55c-103">Počínaje rozhraním .NET Framework 4.7.1 používá nadace Windows Communication Foundation k generování náhodných názvů pojmenovaných kanálů hash SHA256.</span><span class="sxs-lookup"><span data-stu-id="ab55c-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="ab55c-104">V rozhraní .NET Framework 4.7 a starších verzích používala hašiš SHA1.</span><span class="sxs-lookup"><span data-stu-id="ab55c-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="ab55c-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="ab55c-105">Suggestion</span></span>|<span data-ttu-id="ab55c-106">Pokud s touto změnou narazíte na problém s kompatibilitou v rozhraní .NET Framework 4.7.1 <code>&lt;runtime&gt;</code> nebo novějším, můžete ji odhlásit přidáním následujícího řádku do části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="ab55c-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="ab55c-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ab55c-107">Scope</span></span>|<span data-ttu-id="ab55c-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="ab55c-108">Minor</span></span>|
|<span data-ttu-id="ab55c-109">Version</span><span class="sxs-lookup"><span data-stu-id="ab55c-109">Version</span></span>|<span data-ttu-id="ab55c-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ab55c-110">4.7.1</span></span>|
|<span data-ttu-id="ab55c-111">Typ</span><span class="sxs-lookup"><span data-stu-id="ab55c-111">Type</span></span>|<span data-ttu-id="ab55c-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="ab55c-112">Runtime</span></span>|
