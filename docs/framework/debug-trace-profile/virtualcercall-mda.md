---
title: "virtualCERCall – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3f0c06eef7524c18e252ade9122d8c9cb3c2f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="virtualcercall-mda"></a>virtualCERCall – pomocník spravovaného ladění (MDA)
`virtualCERCall` Pomocník spravovaného ladění (MDA) je aktivován jako upozornění označující, že volání lokalitě v rámci graf volání (CER) oblasti omezeného provádění odkazuje na virtuální cíl, který je virtuální volání metody virtuální jiný koncový nebo volání pomocí rozhraní. Modul CLR (CLR) nelze předvídání metodu cílové těchto volání z mezilehlých jazyk a metadata analýzy samostatně. V důsledku toho stromu volání nelze připravit jako součást CER grafu a přerušení přístup z více vláken v tomto podstrom, nejde blokovat automaticky. Tato MDA upozorňuje na případy, kdy je CER může být potřeba rozšířit pomocí explicitního volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda po další informace požadované pro výpočetní cíl volání se označuje za běhu.  
  
## <a name="symptoms"></a>Příznaky  
 Je odpojen CERs, které se nespustí, pokud byl přerušen vlákna nebo domény aplikace.  
  
## <a name="cause"></a>příčina  
 CER obsahuje volání virtuální metodu, která nelze připravit automaticky.  
  
## <a name="resolution"></a>Rozlišení  
 Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> virtuální metody.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
  
```  
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
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
  
```  
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
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
