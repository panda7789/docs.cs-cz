---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802588"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox vysoká změna kontrastu

|   |   |
|---|---|
|Podrobnosti|V [nástroji Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)nebyly ovládací prvky combobox zobrazeny ve správné barvě v určitých motivech s vysokým kontrastem. Problém byl vyřešen v rozhraní .NET Framework 4.7.2. Z důvodu požadavků na zpětnou kompatibilitu sady .NET Framework SDK však oprava nebyla ve výchozím nastavení pro zákazníky viditelná. .NET 4.8 zobrazí tuto změnu přidáním následujících [přepínačů konfigurace AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do souboru svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Návrh|<ul><li>Jak se odhlásit ze změny Pokud nechcete mít vysoký kontrast změny chování, můžete zakázat odebráním následující části ze souboru svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.8|
|Typ|Modul runtime|
