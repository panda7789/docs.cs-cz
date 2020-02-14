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
ms.openlocfilehash: 8acafcc2fba9a7d30cc77f25f06adaca7c79db32
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217419"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange – pomocník spravovaného ladění (MDA)
Pomocníka spravovaného ladění `invalidApartmentStateChange` (MDS) se aktivuje jedním z těchto dvou problémů:  
  
- Došlo k pokusu o změnu stavu objektu COM apartment vlákna, které již bylo inicializováno modelem COM, do jiného stavu objektu apartment.  
  
- Stav objektu COM Apartment v vlákně se neočekávaně mění.  
  
## <a name="symptoms"></a>Příznaky  
  
- Stav objektu COM v vlákně vlákna není to, co bylo vyžádáno. To může způsobit, že se proxy budou používat pro komponenty modelu COM, které mají model podprocesů odlišný od aktuálního typu. To může způsobit, že <xref:System.InvalidCastException> vyvolána při volání objektu COM prostřednictvím rozhraní, která nejsou nastavena pro zařazování mezi platformami.  
  
- Stav objektu COM apartment vlákna je jiný, než se očekávalo. To může způsobit <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD a <xref:System.InvalidCastException> při volání obálky s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW). To může také způsobit, že některé komponenty modelu COM s jedním vláknem mají přístup více vlákny ve stejnou dobu, což může vést k poškození nebo ztrátě dat.  
  
## <a name="cause"></a>Příčina  
  
- Vlákno bylo dříve inicializováno do jiného stavu apartment modelu COM. Všimněte si, že stav objektu apartment vlákna lze nastavit buď explicitně, nebo implicitně. Mezi explicitní operace patří vlastnost <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> a metody <xref:System.Threading.Thread.SetApartmentState%2A> a <xref:System.Threading.Thread.TrySetApartmentState%2A>. Vlákno vytvořené pomocí metody <xref:System.Threading.Thread.Start%2A> je implicitně nastaveno na <xref:System.Threading.ApartmentState.MTA>, pokud <xref:System.Threading.Thread.SetApartmentState%2A> není voláno před spuštěním vlákna. Hlavní vlákno aplikace je také implicitně inicializováno na <xref:System.Threading.ApartmentState.MTA>, pokud není atribut <xref:System.STAThreadAttribute> zadán v metodě Main.  
  
- Metoda `CoUninitialize` (nebo metoda `CoInitializeEx`) s jiným modelem souběžnosti je volána ve vlákně.  
  
## <a name="resolution"></a>Řešení  
 Nastavte stav objektu apartment vlákna předtím, než se spustí jeho spuštění, nebo použijte atribut <xref:System.STAThreadAttribute> nebo atribut <xref:System.MTAThreadAttribute> na metodu Main aplikace.  
  
 V případě druhé příčiny by v ideálním případě měl být kód, který volá metodu `CoUninitialize`, změněn tak, aby zpozdil volání, dokud vlákno nekončí a neexistují žádné RCW a jejich podkladové komponenty COM jsou stále používány vláknem. Nicméně pokud není možné upravit kód, který volá metodu `CoUninitialize`, pak by neměl být použit žádný RCW z vláken, která jsou tímto způsobem neinicializována.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Stav objektu COM Apartment aktuálního vlákna a stav, který byl proveden pokus o použití kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA.  
  
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
