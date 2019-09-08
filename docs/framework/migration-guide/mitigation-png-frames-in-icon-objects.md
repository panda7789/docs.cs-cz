---
title: Zmírnění Snímky PNG v objektech ikon
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a76681cf6efd649fe366a68d956246334975fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789971"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Zmírnění Snímky PNG v objektech ikon
Počínaje .NET Framework 4,6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede ikony s snímky PNG do <xref:System.Drawing.Bitmap> objektů.  
  
 V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> vyvolá metoda výjimku, pokud <xref:System.Drawing.Icon> objekt obsahuje snímky PNG.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují <xref:System.ArgumentOutOfRangeException> speciální zpracování pro výjimku <xref:System.Drawing.Icon> , která je vyvolána, když objekt má snímky PNG. Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.  
  
### <a name="mitigation"></a>Zmírnění  
 Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do [ \<oddílu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Pokud soubor App. config již obsahuje `AppContextSwitchOverrides` element, nová hodnota by měla být sloučena `value` s atributem takto:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6.md)
