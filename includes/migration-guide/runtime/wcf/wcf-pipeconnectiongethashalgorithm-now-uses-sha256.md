---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621094"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="23070-101">WCF připojení PipeConnection bylo. GetHashAlgorithm teď používá SHA256.</span><span class="sxs-lookup"><span data-stu-id="23070-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="23070-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="23070-102">Details</span></span>

<span data-ttu-id="23070-103">Počínaje .NET Framework 4.7.1 Windows Communication Foundation používá SHA256 hash k vygenerování náhodných názvů pro pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="23070-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="23070-104">V .NET Framework 4,7 a starších verzích používala hodnotu hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="23070-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="23070-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="23070-105">Suggestion</span></span>

<span data-ttu-id="23070-106">Pokud narazíte na problém s kompatibilitou s touto změnou v .NET Framework 4.7.1 nebo novějším, můžete ji odhlásit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="23070-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="23070-107">Name</span><span class="sxs-lookup"><span data-stu-id="23070-107">Name</span></span>    | <span data-ttu-id="23070-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="23070-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="23070-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="23070-109">Scope</span></span>   |<span data-ttu-id="23070-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="23070-110">Minor</span></span>|
|<span data-ttu-id="23070-111">Verze</span><span class="sxs-lookup"><span data-stu-id="23070-111">Version</span></span>|<span data-ttu-id="23070-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="23070-112">4.7.1</span></span>|
|<span data-ttu-id="23070-113">Typ</span><span class="sxs-lookup"><span data-stu-id="23070-113">Type</span></span>|<span data-ttu-id="23070-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="23070-114">Runtime</span></span>|
