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
ms.openlocfilehash: f0ecb05dba70dc9c8aba7f04928fd0ab49c900c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125577"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease – pomocník spravovaného ladění (MDA)
`reportAvOnComRelease` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud jsou výjimky vyvolány z důvodu chyby při provádění COM interop a používá počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu a poškození paměti.  
  
## <a name="cause"></a>Příčina  
 V některých případech je vyvolána výjimka z důvodu chyby při provádění COM interop a používá počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM. Za normálních okolností se tato výjimka je zahozena, protože pokud to neuděláte by způsobila porušení přístupu v prostředí CLR, Probíhá ukončování. Pokud tohoto Pomocníka s nastavením je povoleno, možné takové výjimky zjištěna a předávat místo jednoduše zahozeny.  
  
## <a name="resolution"></a>Řešení  
 Zkontrolujte vaši informaci, počítací kódu a vyhledejte chyby, stejně jako zkoumání nativní klienty objektu pro chyby při počítání referencí.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 K dispozici jsou dva režimy. Pokud `allowAv` atribut je `true`, pomocníka zabraňuje modulu runtime zahazuje se narušení přístupu. Pokud `allowAv` je `false`, což je výchozí, modul runtime odstraní narušení přístupu, ale upozornění se oznamuje službě uživatele k označení, že výjimka byla vyvolána a zahodí.  
  
## <a name="output"></a>Výstup  
 Pokud je to možné výstup obsahuje původní ukazatel rozhraní modelu COM vtable. V opačném případě se zobrazí informační zpráva.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
