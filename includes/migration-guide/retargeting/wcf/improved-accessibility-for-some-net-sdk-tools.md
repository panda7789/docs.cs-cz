---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614549"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Vylepšené usnadnění pro některé nástroje .NET SDK

#### <a name="details"></a>Podrobnosti

V sadě .NET Framework SDK 4.7.1 byly vylepšené nástroje SvcConfigEditor.exe a SvcTraceViewer.exe tím, že opravuje různé problémy s přístupností. Většina z nich byla malé problémy, jako je název, který není definován, nebo některé vzorce automatizace uživatelského rozhraní nejsou správně implementovány. I když mnoho uživatelů by si tyto nesprávné hodnoty nedozvěděli, zákazníci, kteří používají asistenční technologie, jako jsou čtečky obrazovky, budou tyto nástroje sady SDK k dispozici podrobněji. V některých případech tyto opravy mění předchozí chování, jako je například pořadí fokusu klávesnice. Chcete-li získat všechny opravy usnadnění v těchto nástrojích, můžete do souboru app.config následující:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.1       |
| Typ    | Změna cílení |
