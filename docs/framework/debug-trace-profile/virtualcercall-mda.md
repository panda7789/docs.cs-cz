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
ms.openlocfilehash: a2112baed863b1035cbee4e956c1b6e271ff6e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181712"
---
# <a name="virtualcercall-mda"></a>virtualCERCall – pomocník spravovaného ladění (MDA)
Spravovaný `virtualCERCall` ladicí asistent (MDA) je aktivován jako upozornění označující, že lokalita volání v rámci grafu volání v rámci grafu volání omezené ho spuštění (CER) odkazuje na virtuální cíl, to znamená virtuální volání nefinal virtual metody nebo volání pomocí rozhraní. Modul CLR (COMMON Language runtime) nemůže předpovědět cílovou metodu těchto volání z mezilehlého jazyka a analýzy metadat samostatně. V důsledku toho nelze připravit strom volání jako součást grafu CER a přerušení podprocesu v tomto podstromu nelze automaticky blokovat. Tento MDA varuje před případy, kdy cer může být <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> nutné rozšířit pomocí explicitní volání metody, jakmile další informace potřebné k výpočtu cíle volání je známa v době běhu.  
  
## <a name="symptoms"></a>Příznaky  
 CER, které nejsou spuštěny při přerušení podprocesu nebo je uvolněna doména aplikace.  
  
## <a name="cause"></a>Příčina  
 Cer obsahuje volání virtuální metody, která nemůže být připravena automaticky.  
  
## <a name="resolution"></a>Řešení  
 Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> virtuální metody.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
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
