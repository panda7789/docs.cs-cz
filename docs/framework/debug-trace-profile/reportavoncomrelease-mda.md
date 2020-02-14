---
title: reportAvOnComRelease – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
ms.openlocfilehash: fca6b209e6432678a264f10762adb3871e3596ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217226"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease – pomocník spravovaného ladění (MDA)
Pokud jsou výjimky vyvolány z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM a použitím metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> kombinované s nezpracovanými voláními modelu COM, je aktivována aplikace `reportAvOnComRelease` Managed Debugging Assistant (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu a poškození paměti.  
  
## <a name="cause"></a>Příčina  
 V některých případech je výjimka vyvolána z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM a použití metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> kombinované s nezpracovanými voláními COM. V normálním případě je tato výjimka zahozena, protože to nedělá, by způsobilo narušení přístupu v modulu CLR, takže by to mělo za následek. Když je tento asistent povolený, můžou se tyto výjimky detekovat a nahlásit místo pouhého zahození.  
  
## <a name="resolution"></a>Řešení  
 Prozkoumejte kód pro počítání odkazů a vyhledejte chyby a také prozkoumání nativních klientů vašeho objektu pro chyby počítání odkazů.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 K dispozici jsou dva režimy. Pokud je atribut `allowAv` `true`, asistent zabraňuje modulu runtime v zahození porušení přístupu. Je-li `allowAv` `false`, což je výchozí hodnota, modul runtime zruší porušení přístupu, ale uživateli je hlášena zpráva s upozorněním, že byla vyvolána výjimka a zahozena.  
  
## <a name="output"></a>Výstup  
 Pokud je to možné, výstup obsahuje původní tabulku vtable ukazatele rozhraní modelu COM. V opačném případě se zobrazí informační zpráva.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
