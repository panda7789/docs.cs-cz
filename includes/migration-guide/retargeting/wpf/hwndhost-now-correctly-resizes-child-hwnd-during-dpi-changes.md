---
ms.openlocfilehash: d374ded6a29ce815beeb26505010563a26d978e8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803484"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost nyní správně změní velikost podřízeného prvku HWND během změny DPI

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a starších verzí při spuštění v režimu přehledu o za monitorování, WPF ovládací prvky hostované v rámci <xref:System.Windows.Interop.HwndHost> nebyly správnou velikost po změně DPI, například při přesunutí aplikací z jednoho monitoru do druhého. Tato oprava zajistí, že hostované ovládací prvky jsou správnou velikost.|
|Doporučení|Aby aplikace využívat tyto změny, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější, a to musí vyjádřit výslovný souhlas pro toto chování tak, že nastavíte následující [přepínač AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) v <code>&lt;runtime&gt;</code> část konfigurace aplikace do souboru <code>false</code>, jak ukazuje následující příklad.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Hlavní|
|Version|4.8|
|type|Změna cílení|

