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
ms.openlocfilehash: 670a32b4d198d2762e0bb51e41297836e471e05b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052847"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext – pomocník spravovaného ladění (MDA)
Pomocník `disconnectedContext` spravovaného ladění (MDA) se aktivuje, když se modul CLR pokusí přejít do odpojeného izolovaného modelu nebo kontextu a přitom obsluhuje požadavek týkající se objektu com.  
  
## <a name="symptoms"></a>Příznaky  
 Volání na obálku s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) se doručí do základní komponenty modelu COM v aktuálním objektu Apartment nebo kontextu, nikoli v takovém případě, ve kterém existují. To může způsobit poškození nebo ztrátu dat, pokud komponenta modelu COM není Vícevláknová, jako v případě komponent typu STA (Single-threaded Apartment). Alternativně, pokud je RCW samotný proxy, volání může způsobit vyvolání a <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT z RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>příčina  
 Objekt Apartment nebo kontext OLE byl vypnut, když se modul CLR pokusí přejít do něj. To je nejčastěji způsobeno tím, že se neukončí všechny komponenty modelu COM vlastněné objektem Apartment. Tato situace může nastat jako výsledek explicitního volání z uživatelského kódu na RCW nebo v případě, že samotný CLR pracuje s komponentou COM. , například když modul CLR uvolňuje komponentu COM, když je přidružený RCW uvolněn z paměti.  
  
## <a name="resolution"></a>Řešení  
 Chcete-li se tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA, neukončilo před dokončením aplikace všemi objekty, které jsou v objektu Apartment v provozu. Totéž platí pro kontexty; Ujistěte se, že kontexty nejsou vypnuté předtím, než se aplikace kompletně dokončí všemi komponentami modelu COM, které jsou v daném kontextu aktivní.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o odpojeném kontextu.  
  
## <a name="output"></a>Výstup  
 Oznamuje kontextový soubor cookie odpojeného objektu Apartment nebo kontextu.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
