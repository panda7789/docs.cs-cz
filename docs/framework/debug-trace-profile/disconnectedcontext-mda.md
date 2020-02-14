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
ms.openlocfilehash: 3d04e304a6b30fe6fd4deeda5a97007f11ee7b13
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216535"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext – pomocník spravovaného ladění (MDA)
Pokud se modul CLR pokusí přejít do odpojeného izolovaného modelu nebo kontextu a současně obsluhuje požadavek týkající se objektu COM, aktivuje se Pomocník s `disconnectedContext` Managed Debugging Assistant (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Volání na obálku s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) se doručí do základní komponenty modelu COM v aktuálním objektu Apartment nebo kontextu, nikoli v takovém případě, ve kterém existují. To může způsobit poškození nebo ztrátu dat, pokud komponenta modelu COM není Vícevláknová, jako v případě komponent typu STA (Single-threaded Apartment). Alternativně, pokud je RCW samotný proxy, volání může způsobit vyvolání <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>Příčina  
 Objekt Apartment nebo kontext OLE byl vypnut, když se modul CLR pokusí přejít do něj. To je nejčastěji způsobeno tím, že se neukončí všechny komponenty modelu COM vlastněné objektem Apartment. Tato situace může nastat jako výsledek explicitního volání z uživatelského kódu na RCW nebo v případě, že samotný CLR pracuje s komponentou COM. , například když modul CLR uvolňuje komponentu COM, když je přidružený RCW uvolněn z paměti.  
  
## <a name="resolution"></a>Řešení  
 Chcete-li se tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA, neukončilo před dokončením aplikace všemi objekty, které jsou v objektu Apartment v provozu. Totéž platí pro kontexty; Ujistěte se, že kontexty nejsou vypnuté předtím, než se aplikace kompletně dokončí všemi komponentami modelu COM, které jsou v daném kontextu aktivní.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o odpojeném kontextu.  
  
## <a name="output"></a>Výstup  
 Oznamuje kontextový soubor cookie odpojeného objektu Apartment nebo kontextu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
