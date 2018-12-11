---
title: invalidApartmentStateChange – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f96ea8cf215c1392857635e85556f530784397
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147649"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange – pomocník spravovaného ladění (MDA)
`invalidApartmentStateChange` Pomocníka spravovaného ladění (MDS) je aktivován některý z dva problémy:  
  
-   Chcete-li změnit stavu apartment modelu COM, který již byl inicializován pomocí modelu COM do stavu různých apartment vlákna je proveden pokus o.  
  
-   Neočekávaně se změní stav objektu apartment modelu COM vlákna.  
  
## <a name="symptoms"></a>Příznaky  
  
-   Stav objektu apartment modelu COM vlákna je co nebyl požadován. To může způsobit proxy má být použit pro komponenty modelu COM, které mají jiný než aktuální model vlákna. Pak může dojít <xref:System.InvalidCastException> vyvolání při volání objektu COM prostřednictvím rozhraní, které nejsou nastaveny pro zařazování mezi objektu apartment.  
  
-   Stav objektu apartment modelu COM vlákna je jiný, než se očekávalo. To může způsobit <xref:System.Runtime.InteropServices.COMException> s HRESULT RPC_E_WRONG_THREAD a také <xref:System.InvalidCastException> při provádění volání na [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW). To může způsobit také některé komponenty modelu COM s jedním vláknem přístup více vláken ve stejnou dobu, což může vést k poškození nebo ztrátě dat k.  
  
## <a name="cause"></a>příčina  
  
-   K jiným stavem objektu apartment modelu COM byl dřív inicializovaný vlákna. Všimněte si, že stav oddílu vlákna lze nastavit explicitně nebo implicitně. Explicitní operace zahrnují <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Threading.Thread.SetApartmentState%2A> a <xref:System.Threading.Thread.TrySetApartmentState%2A> metody. Vlákna vytvořeného <xref:System.Threading.Thread.Start%2A> metoda je implicitně nastavena na <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.Threading.Thread.SetApartmentState%2A> je volána před spuštěním podprocesu. Hlavního vlákna aplikace je také implicitně inicializován na <xref:System.Threading.ApartmentState.MTA> není-li <xref:System.STAThreadAttribute> je zadán atribut v hlavní metodě.  
  
-   `CoUninitialize` – Metoda (nebo `CoInitializeEx` metoda) s jinou souběžnosti se nazývá modelu ve vlákně.  
  
## <a name="resolution"></a>Rozlišení  
 Před zahájením provádění se nastavit stav objektu apartment vlákna, nebo použít buď <xref:System.STAThreadAttribute> atribut nebo <xref:System.MTAThreadAttribute> atribut do metody main aplikace.  
  
 Pro druhý příčinu v ideálním případě by kód, který volá `CoUninitialize` metoda by měla upravit tak, aby zpoždění volání, dokud vlákno se chystá ukončit a neexistují žádné RCW a jejich základní komponenty modelu COM stále používá v vlákna. Ale pokud to není možné upravovat kód, který volá `CoUninitialize` metoda pak žádné RCW by měla sloužit z vláken, které jsou neinicializované tímto způsobem.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Stavu apartment modelu COM aktuálního vlákna a stav, který byl pokus o přidání kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situaci, která může aktivovat toto MDA.  
  
```csharp
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
