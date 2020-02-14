---
title: virtualCERCall – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: 49ba4e7ca0b8ed2e433053130bc9ca2742c72ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217194"
---
# <a name="virtualcercall-mda"></a>virtualCERCall – pomocník spravovaného ladění (MDA)
Pomocník s nástrojem `virtualCERCall` Managed Debugging Assistant (MDA) je aktivován jako upozornění indikující, že web volání v rámci grafu volání v oblasti s omezením (CER) odkazuje na virtuální cíl, který je virtuálním voláním k nekonečné virtuální metodě nebo volání pomocí rozhraní. Modul CLR (Common Language Runtime) nemůže předpovědět cílovou metodu těchto volání ze samotného mezilehlého jazyka a analýzy metadat. V důsledku toho nelze strom volání připravit jako součást grafu CER a přerušení vlákna v tomto podstromu nelze automaticky blokovat. Tento MDA upozorňuje na případy, kdy může být nutné rozšíření CER pomocí explicitního volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>, jakmile jsou další informace požadované pro výpočet cíle volání známy v době běhu.  
  
## <a name="symptoms"></a>Příznaky  
 CERs, které neběží, když je vlákno přerušeno nebo je doména aplikace uvolněna.  
  
## <a name="cause"></a>Příčina  
 CER obsahuje volání virtuální metody, která se nedá automaticky připravit.  
  
## <a name="resolution"></a>Řešení  
 Pro virtuální metodu zavolejte <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
