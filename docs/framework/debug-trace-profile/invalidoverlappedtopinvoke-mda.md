---
title: invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Invalidoverlappedtopinvoke – (MDA) v rozhraní .NET, který se může aktivovat během havárie nebo nejasná poškození haldy.
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 162efd55bf636cf2e8698706bd011379f2f6f11f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051698"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)
`invalidOverlappedToPinvoke`Pokud překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti, je předán konkrétním funkcím Win32, je aktivován pomocník spravovaného ladění (MDA).  
  
> [!NOTE]
> Ve výchozím nastavení je tento MDA aktivován pouze v případě, že je ve vašem kódu definováno volání metody Invoke a ladicí program ohlásí stav JustMyCode pro každou metodu. Ladicí program, který nerozumí JustMyCode (například MDbg.exe bez rozšíření), neaktivuje Tento MDA. Tento MDA lze povolit pro tyto ladicí programy pomocí konfiguračního souboru a explicitně nastavit `justMyCode="false"` v souboru .mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>` ).  
  
## <a name="symptoms"></a>Příznaky  
 Selhání nebo nejasná poškození haldy.  
  
## <a name="cause"></a>Příčina  
 Překrývající ukazatel, který nebyl vytvořen na haldě uvolňování paměti, je předán konkrétním funkcím operačního systému.  
  
 V následující tabulce jsou uvedeny funkce, které tento MDA sleduje.  
  
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
  
 Potenciál pro poškození haldy je pro tento stav vysoký, protože <xref:System.AppDomain> volání může být uvolněno. Pokud se uvolní <xref:System.AppDomain> , kód aplikace buď uvolní paměť pro překrývající ukazatel, což způsobí poškození po dokončení operace, nebo kód nevrátí paměť, což způsobí obtíže později.  
  
## <a name="resolution"></a>Řešení  
 Použijte <xref:System.Threading.Overlapped> objekt, voláním <xref:System.Threading.Overlapped.Pack%2A> metody pro získání <xref:System.Threading.NativeOverlapped> struktury, která může být předána funkci. Pokud se uvolní <xref:System.AppDomain> , modul CLR počká, dokud se asynchronní operace nedokončí před uvolněním ukazatele.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA neměl žádný vliv na CLR.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
