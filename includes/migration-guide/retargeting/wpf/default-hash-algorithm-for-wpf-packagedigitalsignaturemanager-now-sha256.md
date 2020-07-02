---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614588"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="46572-101">Výchozí algoritmus hash pro WPF PackageDigitalSignatureManager je teď SHA256.</span><span class="sxs-lookup"><span data-stu-id="46572-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="46572-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="46572-102">Details</span></span>

<span data-ttu-id="46572-103">`System.IO.Packaging.PackageDigitalSignatureManager`Poskytuje funkce pro digitální podpisy ve vztahu k balíčkům WPF.</span><span class="sxs-lookup"><span data-stu-id="46572-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="46572-104">V .NET Framework 4,7 a starších verzích byl jako algoritmus SHA1 použit výchozí algoritmus ( <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType> ) použitý k podepisování částí balíčku.</span><span class="sxs-lookup"><span data-stu-id="46572-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="46572-105">Vzhledem k nedávnému vlivu zabezpečení na SHA1 se tato výchozí hodnota změnila na SHA256 počínaje 4.7.1em .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46572-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="46572-106">Tato změna má vliv na všechna podepisování balíčků, včetně dokumentů XPS.</span><span class="sxs-lookup"><span data-stu-id="46572-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="46572-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="46572-107">Suggestion</span></span>

<span data-ttu-id="46572-108">Vývojář, který chce tuto změnu využít při cílení na verzi architektury, .NET Framework 4.7.1 nebo vývojář, který vyžaduje předchozí funkce při cílení na .NET Framework 4.7.1 nebo vyšší, může správně nastavit následující příznak AppContext.</span><span class="sxs-lookup"><span data-stu-id="46572-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="46572-109">Hodnota true způsobí, že se jako výchozí algoritmus používá SHA1. Výsledkem nepravdivého výsledku v SHA256.</span><span class="sxs-lookup"><span data-stu-id="46572-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="46572-110">Name</span><span class="sxs-lookup"><span data-stu-id="46572-110">Name</span></span>    | <span data-ttu-id="46572-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="46572-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="46572-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="46572-112">Scope</span></span>   | <span data-ttu-id="46572-113">Edge</span><span class="sxs-lookup"><span data-stu-id="46572-113">Edge</span></span>        |
| <span data-ttu-id="46572-114">Verze</span><span class="sxs-lookup"><span data-stu-id="46572-114">Version</span></span> | <span data-ttu-id="46572-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="46572-115">4.7.1</span></span>       |
| <span data-ttu-id="46572-116">Typ</span><span class="sxs-lookup"><span data-stu-id="46572-116">Type</span></span>    | <span data-ttu-id="46572-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="46572-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="46572-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="46572-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
