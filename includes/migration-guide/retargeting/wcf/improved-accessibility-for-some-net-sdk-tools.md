---
ms.openlocfilehash: 0b087fca59d60a086a9ea8b2bb19c09f646c3dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858992"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Vylepšená přístupnost pro některé nástroje sady .NET SDK

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework SDK 4.7.1 byly nástroje SvcConfigEditor.exe a SvcTraceViewer.exe vylepšeny opravou různých problémů s usnadněním přístupu. Většina z nich byly malé problémy, jako je název není definován nebo některé vzory automatizace uživatelského rozhraní není implementována správně. Zatímco mnoho uživatelů by si nebyli vědomi těchto nesprávných hodnot, zákazníci, kteří používají asistenční technologie, jako jsou programy pro čtení z obrazovky, najdou tyto nástroje sady SDK přístupnější. Jistě, tyto opravy změnit některé předchozí chování, jako je pořadí fokusu klávesnice. Chcete-li získat všechny opravy usnadnění v těchto nástrojích, můžete do souboru app.config získat následující:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Změna cílení|
