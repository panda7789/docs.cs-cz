---
title: "openGenericCERCall – pomocník spravovaného ladění (MDA)"
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
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f82760eaeb051f2006a8baf11ac77c485d007758
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall – pomocník spravovaného ladění (MDA)
`openGenericCERCall` Upozornit, že graf omezeného provádění oblast (CER) s proměnné obecného typu v kořenové metoda je zpracovávaný v JIT – kompilace nebo nativních bitových kopií časem vygenerování a alespoň jeden z obecná se aktivuje Pomocník spravovaného ladění Typ proměnné je odkaz na typ objektu.  
  
## <a name="symptoms"></a>Příznaky  
 CER kód není spuštěn, když byl přerušen vlákna nebo když je odpojen domény aplikace.  
  
## <a name="cause"></a>příčina  
 Během JIT – kompilace vytvoření instance obsahující odkaz na typ objektu, který je pouze zástupce, protože výsledná kód jsou sdílena a každý typ proměnné objektových referencí mohou být jakéhokoli typu odkaz na objekt. To může zabránit přípravy některé prostředky běhu předem.  
  
 Metody s proměnné obecného typu můžete konkrétně líné přidělení prostředků na pozadí. Tyto jsou označovány jako položky obecné slovníku. Například pro příkaz `List<T> list = new List<T>();` kde `T` je proměnná obecného typu modulu runtime musí vyhledat a případně vytvořit přesný instance za běhu, například `List<Object>, List<String>`, a tak dále. To může selhat z různých důvodů mimo kontrolu vývojáře, například spuštění nedostatek paměti.  
  
 Tato MDA by měl být aktivován pouze během JIT – kompilace, ne při přesné vytváření instancí.  
  
 Po aktivaci tato MDA pravděpodobně příznaky jsou, že CERs nejsou funkční pro chybný konkretizací. Modul runtime nebyla ve skutečnosti se pokusil implementovat CER okolností, které způsobily MDA chcete aktivovat. Takže pokud vývojář používá sdílené vytváření instancí z CER, pak JIT – kompilace chyby, Obecné zadejte chyby při načítání nebo zrušení vláken v rámci oblasti určený CER nejsou zachycena.  
  
## <a name="resolution"></a>Rozlišení  
 Nepoužívejte proměnné obecného typu, které jsou typu odkaz objektu pro metody, které mohou obsahovat CER.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Zde je ukázkový výstup z této (mda).  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 CER kód není spuštěn.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
