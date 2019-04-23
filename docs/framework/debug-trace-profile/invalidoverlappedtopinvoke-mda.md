---
title: invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4bdb2035906b9383342201017b58d1d0050113b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084554"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)
`invalidOverlappedToPinvoke` Pomocníka spravovaného ladění (MDA) se aktivuje, když překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti je předán konkrétním funkcím Win32.  
  
> [!NOTE]
>  Ve výchozím nastavení toto MDA aktivováno, pouze pokud platforma volání je definováno v kódu a ladicí program hlásí stav JustMyCode každé metody. Ladicí program, který nerozumí JustMyCode (například MDbg.exe bez přípon), neaktivuje toto MDA. Tento MDA lze povolit pro ty ladící programy pomocí konfiguračního souboru a explicitně nastavit `justMyCode="false"` v. mda.config souboru `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Příznaky  
 Selhání nebo nevysvětlitelné poškození haldy.  
  
## <a name="cause"></a>Příčina  
 Překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti je předán konkrétním funkcím operačního systému.  
  
 V následující tabulce jsou uvedeny funkce, že toto MDA sleduje.  
  
|Modul|Funkce|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|kernel32.dll|`ReadFile`|  
|kernel32.dll|`ReadFileEx`|  
|kernel32.dll|`WriteFile`|  
|kernel32.dll|`WriteFileEx`|  
|kernel32.dll|`ReadDirectoryChangesW`|  
|kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Potenciál pro poškození haldy je vysoký pro tuto podmínku, protože <xref:System.AppDomain> provádění volání se může uvolnit. Pokud <xref:System.AppDomain> uvolní, kód aplikace uvolní paměť pro překrývající ukazatel, což způsobí poškození při dokončení operace nebo kód způsobí přetečení paměti, což povede k potížím později.  
  
## <a name="resolution"></a>Řešení  
 Použití <xref:System.Threading.Overlapped> objektu, volání <xref:System.Threading.Overlapped.Pack%2A> metodu k získání <xref:System.Threading.NativeOverlapped> struktura, která může být předán funkci. Pokud <xref:System.AppDomain> uvolní, CLR čeká na dokončení asynchronní operace před uvolněním ukazatele.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemělo žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Následuje příklad výstupu z tohoto MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
