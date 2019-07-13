---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858992"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Vylepšení přístupnosti pro některé nástroje sady .NET SDK

|   |   |
|---|---|
|Podrobnosti|V SDK rozhraní .NET Framework 4.7.1 byly vylepšeny nástroje SvcConfigEditor.exe a SvcTraceViewer.exe opravou různých usnadnění. Většina z nich byly malé problémy, jako je název nedefinují nebo určité vzory pro automatizaci uživatelského rozhraní nebyl správně implementována. Při nesprávné hodnoty si nevšimnou mnoho uživatelů, zákazníci, kteří používají podpůrnou technologií, jako je čtečky obrazovky najdete tyto sady SDK nástroje přístupnější. Tyto opravy jistě, změňte některá předchozí chování, stejně jako pořadí fokus klávesnice. Zajistí všechno, co přístupnost opravy v těchto nástrojů můžete do souboru app.config následující:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7.1|
|type|Změna cílení|

