---
ms.openlocfilehash: 5a45d616001be5a2a2bdf2c654c10526125d7d86
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802588"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Změna vysoký kontrast – pole se seznamem svcTraceViewer

|   |   |
|---|---|
|Podrobnosti|V [nástroje prohlížeče trasování služeb Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox – ovládací prvky se zobrazí v správná barva v určitých vysokokontrastních motivech. Problém byl vyřešen v rozhraní .NET Framework 4.7.2. Ale z důvodu zpětné kompatibility požadavky rozhraní .NET Framework SDK, opravy nebyla pro zákazníky ve výchozím nastavení viditelné. .NET 4.8 poskytuje informace o této změně přidáním následujícího kódu [konfigurace přepínačů AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) svcTraceViewer.exe.config souboru:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Doporučení|<ul><li>Jak se pokud chcete odhlásit změny, pokud už nechcete mít vysoký kontrast chování změnit, můžete jej zakázat tak, že odeberete ze souboru svcTraceViewer.exe.config v následující části:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.8|
|type|Modul runtime|

