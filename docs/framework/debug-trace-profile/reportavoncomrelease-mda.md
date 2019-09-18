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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bea73a30cb103f0e72caf73a633229a0719dc6c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052318"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease – pomocník spravovaného ladění (MDA)
Pomocník `reportAvOnComRelease` spravovaného ladění (MDA) je aktivován, pokud jsou výjimky vyvolány z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace <xref:System.Runtime.InteropServices.Marshal.Release%2A> s <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> objekty COM a pomocí metody nebo kombinované s nezpracovanými voláními modelu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu a poškození paměti.  
  
## <a name="cause"></a>příčina  
 V některých případech je výjimka vyvolána z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM <xref:System.Runtime.InteropServices.Marshal.Release%2A> a <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> použití metody nebo kombinované s nezpracovanými voláními com. V normálním případě je tato výjimka zahozena, protože to nedělá, by způsobilo narušení přístupu v modulu CLR, takže by to mělo za následek. Když je tento asistent povolený, můžou se tyto výjimky detekovat a nahlásit místo pouhého zahození.  
  
## <a name="resolution"></a>Řešení  
 Prozkoumejte kód pro počítání odkazů a vyhledejte chyby a také prozkoumání nativních klientů vašeho objektu pro chyby počítání odkazů.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 K dispozici jsou dva režimy. Pokud je `allowAv` `true`atribut, asistent zabraňuje modulu runtime v zahození porušení přístupu. Pokud `allowAv` je`false`, což je výchozí hodnota, modul runtime zruší porušení přístupu, ale uživateli je hlášena zpráva s upozorněním, že byla vyvolána výjimka a byla zahozena.  
  
## <a name="output"></a>Výstup  
 Pokud je to možné, výstup obsahuje původní tabulku vtable ukazatele rozhraní modelu COM. V opačném případě se zobrazí informační zpráva.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
