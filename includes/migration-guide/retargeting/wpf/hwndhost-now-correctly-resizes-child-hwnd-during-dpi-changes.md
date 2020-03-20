---
ms.openlocfilehash: b92086c8ccf7592ce70b75bd31d4ea255c35b543
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803484"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost nyní správně mění velikost child-HWND během změn DPI

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a starších verzích, kdy byl wpf <xref:System.Windows.Interop.HwndHost> spuštěn v režimu podporujícího monitorování, nebyly ovládací prvky hostované v rámci správně dimenzovány po změnách DPI, například při přesouvání aplikací z jednoho monitoru na druhý. Tato oprava zajišťuje, že hostované ovládací prvky jsou odpovídajícím způsobem dimenzovány.|
|Návrh|Aby aplikace mohla těžit z těchto změn, musí být spuštěna v rozhraní .NET Framework 4.7.2 nebo novějším a musí <code>&lt;runtime&gt;</code> se k tomuto <code>false</code>chování přihlásit nastavením následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) v části konfiguračního souboru aplikace na , jak ukazuje následující příklad.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Hlavní|
|Version|4.8|
|Typ|Změna cílení|
