---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621988"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Změna vysokého kontrastu svcTraceViewer pole se seznamem

#### <a name="details"></a>Podrobnosti

V [nástroji Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)se ovládací prvky ComboBox nezobrazovaly ve správné barvě v určitých motivech s vysokým kontrastem. Problém byl vyřešen .NET Framework 4.7.2. V důsledku .NET Framework požadavků na zpětnou kompatibilitu sady SDK ale není tato oprava pro zákazníky ve výchozím nastavení viditelná. .NET 4,8 přidá tuto změnu přidáním následujících [AppContext konfigurace](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do souboru svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a>Návrh

<ul><li>Pokud nechcete, aby se změna chování vysokého kontrastu nezměnila, můžete ji zakázat odebráním následující části ze souboru svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4,8|
|Typ|Modul runtime|
