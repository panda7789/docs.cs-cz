---
title: disconnectedContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181972"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext – pomocník spravovaného ladění (MDA)
`disconnectedContext` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR se pokusí o přechod do odpojeného oddílu nebo kontextu během obsluhy žádost o objekt modelu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Volání [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) se doručí nadřazená komponenta modelu COM v aktuálním oddílu nebo kontextu místo ten, ve kterém existují. To může způsobit poškození a nebo ztrátu nejsou-li komponenta modelu COM s více vlákny, stejně jako v případě komponenty jednovláknový apartment (STA). Případně, pokud Obálka RCW je samotný proxy serveru, volání může vést vyvolání sady <xref:System.Runtime.InteropServices.COMException> s HRESULT RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>Příčina  
 OLE oddílu nebo kontextu má byla ukončena, když modul CLR se pokusí přejít do něj. To je nejčastěji způsobeno objekty apartment STA vypíná před všechny komponenty modelu COM typu apartment vlastněné byly zcela to může nastat v důsledku explicitního volání z uživatelského kódu na obálky RCW, nebo když samotný modul CLR je manipulace s komponenty modelu COM , třeba když CLR vydává komponenty modelu COM při přidružené RCW byla uvolněna z paměti.  
  
## <a name="resolution"></a>Řešení  
 K tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA nebyl ukončen před dokončením příkazu se u všech objektů, kteří žijí v typu apartment aplikace. Totéž platí i pro kontexty; Zajistěte, aby kontexty nevypnou, než se aplikace úplně dokončená všechny komponenty modelu COM, kteří žijí v kontextu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o odpojený kontext.  
  
## <a name="output"></a>Výstup  
 Sestavy soubor cookie kontextu odpojeného oddílu nebo kontextu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
