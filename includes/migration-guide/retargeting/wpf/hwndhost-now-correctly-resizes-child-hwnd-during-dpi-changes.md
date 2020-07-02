---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616243"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost nyní správně mění velikost podřízeného-HWND během změny v DPI

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.2 a starších verzích, když byl WPF spuštěn v režimu podporujícím monitorování, nejsou ovládací prvky hostované v této <xref:System.Windows.Interop.HwndHost> velikosti správně po změnách dpi, například při přesunu aplikací z jednoho monitorování na jiný. Tato oprava zajišťuje správné velikosti hostovaných ovládacích prvků.

#### <a name="suggestion"></a>Návrh

Aby aplikace mohla tyto změny využít, musí běžet na .NET Framework 4.7.2 nebo novějším a musí se k tomuto chování vyjádřit nastavením následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) v `<runtime>` části konfiguračního souboru aplikace na `false` , jak ukazuje následující příklad.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4,8         |
| Typ    | Změna cílení |
