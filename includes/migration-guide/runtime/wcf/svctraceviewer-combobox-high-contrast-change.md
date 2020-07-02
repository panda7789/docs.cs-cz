---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621988"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="79445-101">Změna vysokého kontrastu svcTraceViewer pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="79445-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="79445-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="79445-102">Details</span></span>

<span data-ttu-id="79445-103">V [nástroji Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)se ovládací prvky ComboBox nezobrazovaly ve správné barvě v určitých motivech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="79445-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="79445-104">Problém byl vyřešen .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="79445-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="79445-105">V důsledku .NET Framework požadavků na zpětnou kompatibilitu sady SDK ale není tato oprava pro zákazníky ve výchozím nastavení viditelná.</span><span class="sxs-lookup"><span data-stu-id="79445-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="79445-106">.NET 4,8 přidá tuto změnu přidáním následujících [AppContext konfigurace](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do souboru svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="79445-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a><span data-ttu-id="79445-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="79445-107">Suggestion</span></span>

<ul><li><span data-ttu-id="79445-108">Pokud nechcete, aby se změna chování vysokého kontrastu nezměnila, můžete ji zakázat odebráním následující části ze souboru svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="79445-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="79445-109">Name</span><span class="sxs-lookup"><span data-stu-id="79445-109">Name</span></span>    | <span data-ttu-id="79445-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="79445-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="79445-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="79445-111">Scope</span></span>   |<span data-ttu-id="79445-112">Edge</span><span class="sxs-lookup"><span data-stu-id="79445-112">Edge</span></span>|
|<span data-ttu-id="79445-113">Verze</span><span class="sxs-lookup"><span data-stu-id="79445-113">Version</span></span>|<span data-ttu-id="79445-114">4,8</span><span class="sxs-lookup"><span data-stu-id="79445-114">4.8</span></span>|
|<span data-ttu-id="79445-115">Typ</span><span class="sxs-lookup"><span data-stu-id="79445-115">Type</span></span>|<span data-ttu-id="79445-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="79445-116">Runtime</span></span>|
