---
title: 'Zmírnění: snímky PNG v objektech ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248892"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Zmírnění: snímky PNG v objektech ikon
Počínaje .NET Framework 4,6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda úspěšně převede ikony s snímky PNG do <xref:System.Drawing.Bitmap> objektů.  
  
 V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda <xref:System.ArgumentOutOfRangeException> výjimku, pokud <xref:System.Drawing.Icon> objekt obsahuje snímky PNG.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují speciální zpracování pro <xref:System.ArgumentOutOfRangeException> výjimku, která je vyvolána, když <xref:System.Drawing.Icon> objekt má snímky PNG. Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.  
  
### <a name="mitigation"></a>Omezení rizik  
 Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do oddílu [ \< runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Pokud soubor App. config již obsahuje `AppContextSwitchOverrides` element, nová hodnota by měla být sloučena s `value` atributem takto:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
