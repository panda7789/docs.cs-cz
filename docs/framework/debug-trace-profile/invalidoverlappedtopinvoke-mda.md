---
title: "invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 395601c6aaff39bf2acb01ae36d306e57566aa4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)
`invalidOverlappedToPinvoke` Pomocník spravovaného ladění (MDA) se aktivuje, když překrytý ukazatel, jež nebyla vytvořena v haldě kolekce paměti předána ke konkrétním funkcím Win32.  
  
> [!NOTE]
>  Ve výchozím nastavení tento MDA je aktivována, jenom Pokud platformou vyvolat volání je definována v kódu a ladicí program hlásí stav JustMyCode každé metody. Ladicí program, který nerozumí JustMyCode (například MDbg.exe bez přípony) nebudou aktivovat tuto (mda). Tento MDA lze povolit pro tyto ladicí programy pomocí konfiguračního souboru a explicitně settting `justMyCode="false"` v. soubor mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Příznaky  
 Poškození haldy unexplainable nebo dojde k chybě.  
  
## <a name="cause"></a>příčina  
 Překryté ukazatele, jež nebyla vytvořena v haldě kolekce paměti se předají funkcím konkrétní operační systém.  
  
 Následující tabulka uvádí funkce, že tento MDA sleduje.  
  
|Modul|Funkce|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|Kernel32.dll|`ReadFile`|  
|Kernel32.dll|`ReadFileEx`|  
|Kernel32.dll|`WriteFile`|  
|Kernel32.dll|`WriteFileEx`|  
|Kernel32.dll|`ReadDirectoryChangesW`|  
|Kernel32.dll|`PostQueuedCompletionStatus`|  
|Mswsock.dll –|`ConnectEx`|  
|Ws2_32.dll|`WSASend`|  
|Ws2_32.dll|`WSASendTo`|  
|Ws2_32.dll|`WSARecv`|  
|Ws2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Tato podmínka, protože je vysoká potenciální poškození haldy <xref:System.AppDomain> provádění volání může mít za následek uvolnění. Pokud <xref:System.AppDomain> uvolní, kódu aplikace bude buď volné paměti pro překrytý ukazatel způsobuje poškození při dokončení operace nebo kód bude úniku paměť, způsobuje problémy později.  
  
## <a name="resolution"></a>Rozlišení  
 Použijte <xref:System.Threading.Overlapped> objektu, volání <xref:System.Threading.Overlapped.Pack%2A> metodu za účelem získání <xref:System.Threading.NativeOverlapped> struktura, která může být předaný funkci. Pokud <xref:System.AppDomain> uvolní, modul CLR čeká na dokončení asynchronní operace před uvolnění ukazatele.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemělo žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Následuje příklad výstupu z této (mda).  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
