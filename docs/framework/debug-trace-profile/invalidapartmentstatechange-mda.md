---
title: "invalidApartmentStateChange – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71634018e42ad66fdd2d03d0b0d496394cde801e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange – pomocník spravovaného ladění (MDA)
`invalidApartmentStateChange` Pomocník spravovaného ladění (MDS) je aktivován buď dva problémy:  
  
-   Chcete-li změnit stav objektu apartment COM podproces, který již byl inicializován nástrojem COM do stavu různých apartment je proveden pokus o.  
  
-   Neočekávaně se změní stav objektu apartment COM vlákna.  
  
## <a name="symptoms"></a>Příznaky  
  
-   Stav objektu apartment COM vlákno je co nebyl požadován. To může způsobit proxy, který se má použít pro komponenty modelu COM, které mají model vláken liší od aktuální verze. Pak může dojít <xref:System.InvalidCastException> vyvolání při volání objektu COM prostřednictvím rozhraní, které nejsou nastaveny pro zařazování mezi apartment.  
  
-   Stav objektu apartment COM vlákno je jiné, než se očekávalo. To může způsobit <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD a také <xref:System.InvalidCastException> při provádění volání na [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW). To může způsobit také některé jednovláknové součásti COM přístup více vláken ve stejnou dobu, což může vést k poškození nebo ztrátě dat.  
  
## <a name="cause"></a>příčina  
  
-   Vlákno byl dříve na jiný stav objektu apartment COM inicializován. Všimněte si, že stav objektu apartment vlákna lze nastavit explicitně nebo implicitně. Explicitní operace zahrnují <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Threading.Thread.SetApartmentState%2A> a <xref:System.Threading.Thread.TrySetApartmentState%2A> metody. Vlákno vytvořené pomocí <xref:System.Threading.Thread.Start%2A> je implicitně nastavena metoda <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.Threading.Thread.SetApartmentState%2A> je volat před zahájením vlákno. Hlavní vlákno aplikace je také implicitně inicializována tak, aby <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.STAThreadAttribute> atribut je zadaný na hlavní metodu.  
  
-   `CoUninitialize` – Metoda (nebo `CoInitializeEx` metoda) s jinou souběžnosti se nazývá model na vlákno.  
  
## <a name="resolution"></a>Rozlišení  
 Nastavit stav objektu apartment vlákna, než začne provádění nebo použít buď <xref:System.STAThreadAttribute> atribut nebo <xref:System.MTAThreadAttribute> atribut hlavní metodu aplikace.  
  
 Pro druhý příčina v ideálním případě kód, který volá `CoUninitialize` by měl být upraven metoda k volání počkat, až budou vlákno se chystá ukončit a neexistují žádné RCWs a jejich základní komponenty modelu COM stále používá vlákno. Ale pokud není možné změnit kód, který volá `CoUninitialize` metoda pak žádné RCWs slouží z vláken, které jsou tímto způsobem Neinicializovaný.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Stav objektu apartment COM aktuální vlákno a stav, který kód při pokusu o použití.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situace, které můžou aktivovat tuto (mda).  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
