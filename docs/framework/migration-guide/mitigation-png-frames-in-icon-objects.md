---
title: 'Omezení rizik: PNG rámce v objektech ikonu'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 575d77524e567ba55f7cd9222d690fcee25d3f20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102866"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Omezení rizik: PNG rámce v objektech ikonu
Od verze rozhraní .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede ikony PNG snímky do <xref:System.Drawing.Bitmap> objekty.  
  
 V aplikacích, které jsou cíleny na rozhraní .NET Framework 4.5.2 a starší verze <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda výjimku <xref:System.ArgumentOutOfRangeException> výjimka pokud <xref:System.Drawing.Icon> objekt má snímky PNG.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní aplikace, které jsou rekompilovány cílit na rozhraní .NET Framework 4.6 a které implementují zvláštní zacházení <xref:System.ArgumentOutOfRangeException> , která je vyvolána, když <xref:System.Drawing.Icon> objekt má snímky PNG. Při spuštění v rozhraní .NET Framework 4.6, převod je úspěšný, <xref:System.ArgumentOutOfRangeException> je už ne vyvolána, a proto je již vyvolána obslužná rutina výjimky.  
  
### <a name="mitigation"></a>Zmírnění  
 Pokud toto chování nežádoucí, můžete zachovat předchozí chování tak, že přidáte následující element na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Pokud již obsahuje soubor app.config `AppContextSwitchOverrides` elementu, nová hodnota mají sloučit s `value` atribut následujícím způsobem:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
