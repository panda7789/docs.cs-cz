---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982163"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Změna vysoký kontrast – pole se seznamem svcTraceViewer

|   |   |
|---|---|
|Podrobnosti|V [nástroje prohlížeče trasování služeb Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox – ovládací prvky se zobrazí v správná barva v určitých vysokokontrastních motivech. Problém byl vyřešen v rozhraní .NET Framework 4.7.2. Ale z důvodu zpětné kompatibility požadavky rozhraní .NET Framework SDK, opravy nebyla pro zákazníky ve výchozím nastavení viditelné. .NET 4.8 poskytuje informace o této změně přidáním následujícího kódu [konfigurace přepínačů AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) svcTraceViewer.exe.config souboru:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Doporučení|<ul><li>Jak se pokud chcete odhlásit změny, pokud už nechcete mít vysoký kontrast chování změnit, můžete jej zakázat tak, že odeberete ze souboru svcTraceViewer.exe.config v následující části:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.8|
|Type|Modul runtime|
