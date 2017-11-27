---
title: "disconnectedContext – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1bbcd4a1058c4202a3de7b8eecb05caad7730ce5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext – pomocník spravovaného ladění (MDA)
`disconnectedContext` Pomocník spravovaného ladění (MDA) se aktivuje, když se modul CLR pokusí o přechod do odpojeného oddílu nebo kontextu během obsluhy žádost týkající se objektu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Volání na [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) budou doručeny do základní komponenty modelu COM v aktuálním oddílu nebo kontextu místo jeden, ve které existují. To může způsobit poškození a nebo ztráty dat, pokud není součást COM s více vlákny, jako v případě součásti single-threaded apartment (STA). Případně, pokud RCW se proxy server, volání může dojít k vyvolání z <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>příčina  
 OLE oddílu nebo kontextu byla vypnuta při modulu CLR pokusí o přechod do ní. To je nejčastěji způsobeno STA bytů, které právě vypíná před všechny komponenty modelu COM, které vlastní typu apartment úplně byly vydané to může nastat v důsledku explicitní volání z uživatelského kódu RCW nebo při CLR samotné je manipulace s komponenty modelu COM , například když modulu CLR vydává komponenty modelu COM při přidružené RCW byl uvolnění z paměti.  
  
## <a name="resolution"></a>Rozlišení  
 K tomuto problému nedošlo, zajistěte, aby vlákno, které vlastní STA nezavře aplikaci ještě před ukončením se všemi objekty, které existují v typu apartment. Totéž platí i pro kontexty; Zkontrolujte, zda nejsou kontexty vypne, než je zcela dokončení všech součástí modelu COM, které za provozu v rámci aplikace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR. Pouze sestavy data o odpojený kontext.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
