---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616240"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="7e92f-101">Kontrolní součty souborů XOML pracovního postupu se změnily z MD5 na SHA256</span><span class="sxs-lookup"><span data-stu-id="7e92f-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="7e92f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7e92f-102">Details</span></span>

<span data-ttu-id="7e92f-103">Aby bylo možné podporovat ladění pracovních postupů na základě souborů XOML pomocí sady Visual Studio, jsou při vytváření projektů pracovních postupů obsahujících soubory XOML kontrolní součet obsahu souboru XOML obsažen v kódu generovaném jako <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> hodnota.</span><span class="sxs-lookup"><span data-stu-id="7e92f-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="7e92f-104">V .NET Framework 4.7.2 a dřívějších verzích tato kontrolní hodnota hash použila algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS.</span><span class="sxs-lookup"><span data-stu-id="7e92f-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="7e92f-105">Počínaje .NET Framework 4,8 se používá algoritmus SHA256.</span><span class="sxs-lookup"><span data-stu-id="7e92f-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="7e92f-106">Aby bylo možné compatibile pomocí WorkflowMarkupSourceAttribute. MD5Digest, jsou použity pouze prvních 16 bajtů vygenerovaného kontrolního součtu. To může způsobit problémy při ladění.</span><span class="sxs-lookup"><span data-stu-id="7e92f-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="7e92f-107">Možná budete muset projekt znovu sestavit.</span><span class="sxs-lookup"><span data-stu-id="7e92f-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7e92f-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="7e92f-108">Suggestion</span></span>

<span data-ttu-id="7e92f-109">Pokud znovu sestavíte projekt, zkuste nastavit `AppContext` přepínač &quot;Switch.System. Workflow. ComponentModel. UseLegacyHashForXomlFileChecksum &quot; na hodnotu true. V kódu:</span><span class="sxs-lookup"><span data-stu-id="7e92f-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="7e92f-110">Nebo v konfiguračním souboru (musí být MSBuild.exe.config pro MSBuild.exe, které používáte):</span><span class="sxs-lookup"><span data-stu-id="7e92f-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7e92f-111">Name</span><span class="sxs-lookup"><span data-stu-id="7e92f-111">Name</span></span>    | <span data-ttu-id="7e92f-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7e92f-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7e92f-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7e92f-113">Scope</span></span>   | <span data-ttu-id="7e92f-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="7e92f-114">Minor</span></span>       |
| <span data-ttu-id="7e92f-115">Verze</span><span class="sxs-lookup"><span data-stu-id="7e92f-115">Version</span></span> | <span data-ttu-id="7e92f-116">4,8</span><span class="sxs-lookup"><span data-stu-id="7e92f-116">4.8</span></span>         |
| <span data-ttu-id="7e92f-117">Typ</span><span class="sxs-lookup"><span data-stu-id="7e92f-117">Type</span></span>    | <span data-ttu-id="7e92f-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="7e92f-118">Retargeting</span></span> |
