---
title: 'Zmírnění: snímky PNG v objektech ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 1a4ae0c069a4cd6d53bce77e64822ebf3fbb5361
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457879"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Zmírnění: snímky PNG v objektech ikon
Počínaje .NET Framework 4,6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převádí ikony s snímky PNG do objektů <xref:System.Drawing.Bitmap>.  
  
 V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, vyvolá metoda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> výjimku <xref:System.ArgumentOutOfRangeException>, pokud objekt <xref:System.Drawing.Icon> obsahuje snímky PNG.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují speciální zpracování pro <xref:System.ArgumentOutOfRangeException>, která je vyvolána, když objekt <xref:System.Drawing.Icon> obsahuje snímky PNG. Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.  
  
### <a name="mitigation"></a>Zmírnění  
 Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do oddílu [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Pokud soubor App. config již obsahuje prvek `AppContextSwitchOverrides`, nová hodnota by měla být sloučena s atributem `value` takto:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
