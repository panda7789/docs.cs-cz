---
title: 'Zmírnění: Png snímky v objektech ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248892"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Zmírnění: Png snímky v objektech ikon
Počínaje rozhraním .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede <xref:System.Drawing.Bitmap> ikony s rámečky PNG na objekty.  
  
 V aplikacích, které cílí na rozhraní .NET Framework <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 4.5.2 a starší verze, metoda vyvolá výjimku, <xref:System.ArgumentOutOfRangeException> pokud <xref:System.Drawing.Icon> objekt má png rámce.  
  
## <a name="impact"></a>Dopad  
 Tato změna má vliv na aplikace, které jsou překompilovány na cíl <xref:System.ArgumentOutOfRangeException> .NET Framework <xref:System.Drawing.Icon> 4.6 a které implementují speciální zpracování pro to, který je vyvolán, když má objekt png rámce. Při spuštění v rámci rozhraní .NET Framework 4.6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolána a proto obslužná rutina výjimky již není vyvolána.  
  
### <a name="mitigation"></a>Omezení rizik  
 Pokud je toto chování nežádoucí, můžete zachovat předchozí chování přidáním následujícího prvku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Pokud soubor app.config již `AppContextSwitchOverrides` prvek obsahuje, měla by `value` být nová hodnota sloučena s atributem takto:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
