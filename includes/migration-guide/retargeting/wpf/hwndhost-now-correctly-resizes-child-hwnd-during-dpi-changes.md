---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616243"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="76886-101">HwndHost nyní správně mění velikost podřízeného-HWND během změny v DPI</span><span class="sxs-lookup"><span data-stu-id="76886-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="76886-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="76886-102">Details</span></span>

<span data-ttu-id="76886-103">V .NET Framework 4.7.2 a starších verzích, když byl WPF spuštěn v režimu podporujícím monitorování, nejsou ovládací prvky hostované v této <xref:System.Windows.Interop.HwndHost> velikosti správně po změnách dpi, například při přesunu aplikací z jednoho monitorování na jiný.</span><span class="sxs-lookup"><span data-stu-id="76886-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="76886-104">Tato oprava zajišťuje správné velikosti hostovaných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="76886-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="76886-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="76886-105">Suggestion</span></span>

<span data-ttu-id="76886-106">Aby aplikace mohla tyto změny využít, musí běžet na .NET Framework 4.7.2 nebo novějším a musí se k tomuto chování vyjádřit nastavením následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) v `<runtime>` části konfiguračního souboru aplikace na `false` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="76886-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="76886-107">Name</span><span class="sxs-lookup"><span data-stu-id="76886-107">Name</span></span>    | <span data-ttu-id="76886-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="76886-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="76886-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="76886-109">Scope</span></span>   | <span data-ttu-id="76886-110">Hlavní</span><span class="sxs-lookup"><span data-stu-id="76886-110">Major</span></span>       |
| <span data-ttu-id="76886-111">Verze</span><span class="sxs-lookup"><span data-stu-id="76886-111">Version</span></span> | <span data-ttu-id="76886-112">4,8</span><span class="sxs-lookup"><span data-stu-id="76886-112">4.8</span></span>         |
| <span data-ttu-id="76886-113">Typ</span><span class="sxs-lookup"><span data-stu-id="76886-113">Type</span></span>    | <span data-ttu-id="76886-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="76886-114">Retargeting</span></span> |
