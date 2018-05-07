---
title: 'Omezení rizik: PNG rámce v ikona objektů'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3ee5cc03f684acf103c96ecd14387f119bf0bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Omezení rizik: PNG rámce v ikona objektů
Od verze rozhraní .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda převede úspěšně ikony s PNG rámce do <xref:System.Drawing.Bitmap> objekty.  
  
 V aplikacích, které cílí na rozhraní .NET Framework 4.5.2 a dřívějších verzích <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vrátí <xref:System.ArgumentOutOfRangeException> výjimka pokud <xref:System.Drawing.Icon> objekt má rámce PNG.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivňuje aplikace, která jsou překompilovat, jehož cílem je rozhraní .NET Framework 4.6 a které implementují zvláštní zpracování pro <xref:System.ArgumentOutOfRangeException> , když dojde <xref:System.Drawing.Icon> objekt má rámce PNG. Při spuštění v rozhraní .NET Framework 4.6, převod proběhne úspěšně, <xref:System.ArgumentOutOfRangeException> je už ne vyvolána, a proto už volána obslužná rutina výjimky.  
  
### <a name="mitigation"></a>Zmírnění  
 Pokud je toto chování žádoucí, můžete zachovat předchozí chování přidáním následující elementu, který chcete [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Pokud již obsahuje soubor app.config `AppContextSwitchOverrides` elementu, nová hodnota má být sloučena s `value` atribut takto:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
