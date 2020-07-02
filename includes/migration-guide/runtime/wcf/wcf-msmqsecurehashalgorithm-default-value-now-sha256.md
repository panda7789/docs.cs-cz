---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621088"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="919dc-101">Výchozí hodnota MsmqSecureHashAlgorithm WCF je teď SHA256.</span><span class="sxs-lookup"><span data-stu-id="919dc-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="919dc-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="919dc-102">Details</span></span>

<span data-ttu-id="919dc-103">Počínaje .NET Framework 4.7.1 je výchozí algoritmus podepisování zprávy ve službě WCF pro zprávy MSMQ SHA256.</span><span class="sxs-lookup"><span data-stu-id="919dc-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="919dc-104">V .NET Framework 4,7 a starších verzích je výchozí algoritmus podepisování zprávy SHA1.</span><span class="sxs-lookup"><span data-stu-id="919dc-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="919dc-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="919dc-105">Suggestion</span></span>

<span data-ttu-id="919dc-106">Pokud narazíte na problémy s kompatibilitou s touto změnou .NET Framework 4.7.1 nebo novějším, můžete tuto změnu zrušit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="919dc-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="919dc-107">Name</span><span class="sxs-lookup"><span data-stu-id="919dc-107">Name</span></span>    | <span data-ttu-id="919dc-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="919dc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="919dc-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="919dc-109">Scope</span></span>   |<span data-ttu-id="919dc-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="919dc-110">Minor</span></span>|
|<span data-ttu-id="919dc-111">Verze</span><span class="sxs-lookup"><span data-stu-id="919dc-111">Version</span></span>|<span data-ttu-id="919dc-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="919dc-112">4.7.1</span></span>|
|<span data-ttu-id="919dc-113">Typ</span><span class="sxs-lookup"><span data-stu-id="919dc-113">Type</span></span>|<span data-ttu-id="919dc-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="919dc-114">Runtime</span></span>|
