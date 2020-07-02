---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614596"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="cae73-101">Výchozí algoritmus hash pro kompilátor značek WPF je nyní SHA256</span><span class="sxs-lookup"><span data-stu-id="cae73-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="cae73-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cae73-102">Details</span></span>

<span data-ttu-id="cae73-103">WPF MarkupCompiler poskytuje kompilační služby pro soubory značek XAML.</span><span class="sxs-lookup"><span data-stu-id="cae73-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="cae73-104">V .NET Framework 4.7.1 a starších verzích byl výchozí algoritmus hash použitý pro kontrolní součty SHA1.</span><span class="sxs-lookup"><span data-stu-id="cae73-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="cae73-105">Vzhledem k nedávnému vlivu zabezpečení na SHA1 se tato výchozí hodnota změnila na SHA256 počínaje 4.7.2em .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cae73-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="cae73-106">Tato změna má vliv na veškerou generaci kontrolního součtu pro soubory značek během kompilace.</span><span class="sxs-lookup"><span data-stu-id="cae73-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cae73-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="cae73-107">Suggestion</span></span>

<span data-ttu-id="cae73-108">Vývojář, který cílí na .NET Framework 4.7.2 nebo větší a chce se vrátit k chování algoritmu hash SHA1, musí nastavit následující příznak AppContext.</span><span class="sxs-lookup"><span data-stu-id="cae73-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="cae73-109">Vývojář, který chce využít SHA256 hash při cílení na verzi architektury nižší než .NET 4.7.2, musí nastavit níže uvedený příznak AppContext.</span><span class="sxs-lookup"><span data-stu-id="cae73-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="cae73-110">Všimněte si, že nainstalovaná verze .NET Framework musí být 4.7.2 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="cae73-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="cae73-111">Name</span><span class="sxs-lookup"><span data-stu-id="cae73-111">Name</span></span>    | <span data-ttu-id="cae73-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cae73-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cae73-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="cae73-113">Scope</span></span>   | <span data-ttu-id="cae73-114">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="cae73-114">Transparent</span></span> |
| <span data-ttu-id="cae73-115">Verze</span><span class="sxs-lookup"><span data-stu-id="cae73-115">Version</span></span> | <span data-ttu-id="cae73-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="cae73-116">4.7.2</span></span>       |
| <span data-ttu-id="cae73-117">Typ</span><span class="sxs-lookup"><span data-stu-id="cae73-117">Type</span></span>    | <span data-ttu-id="cae73-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="cae73-118">Retargeting</span></span> |
