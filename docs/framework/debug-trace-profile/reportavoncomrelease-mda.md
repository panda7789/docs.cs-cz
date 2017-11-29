---
title: "reportAvOnComRelease – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de48fca818f8456627c9507756cc2d8a200c50e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease – pomocník spravovaného ladění (MDA)
`reportAvOnComRelease` Pomocník spravovaného ladění (MDA) se aktivuje, pokud jsou výjimky vyvolány z důvodu chyby při provádění COM spolupráce a pomocí počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu a poškození paměti.  
  
## <a name="cause"></a>příčina  
 V některých případech je vyvolána výjimka z důvodu chyby při provádění COM spolupráce a pomocí počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM. Za normálních okolností se tato výjimka je zahozena, protože není tak by způsobit narušení přístupu v prostředí CLR, bude mimo provoz. Pokud tohoto pomocníka je povoleno, můžete tyto výjimky zjistil a hlášené místo jednoduše budou odstraněny.  
  
## <a name="resolution"></a>Rozlišení  
 Zkontrolujte vaši informaci, kód a vyhledejte chyby při počítání a také zkoumání nativních klientů objektu pro chyby při počítání referencí.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 K dispozici jsou dva režimy. Pokud `allowAv` atribut je `true`, pomocníka brání modulu runtime zahození porušení přístupu. Pokud `allowAv` je `false`, který je výchozí, modul runtime zahodí narušení přístupu, ale upozornění údajně uživateli znamenat, že byla vyvolána a zahodí výjimku.  
  
## <a name="output"></a>Výstup  
 Pokud je to možné výstup obsahuje původní vtable ukazatel rozhraní COM. Jinak se zobrazí informační zpráva.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
