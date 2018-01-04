---
title: "illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b739cb76827a12a9928e0268e5e2cb8be686479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
`illegalPrepareConstrainedRegion` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> volání metody nepředchází okamžitě `try` prohlášení o obslužná rutina výjimky. Toto omezení je na MSIL úroveň, tak, aby byl povolený mít jiný kód generování zdroj mezi volání a `try`, jako je například komentáře.  
  
## <a name="symptoms"></a>Příznaky  
 Oblasti omezeného provádění (CER), která se nikdy považuje jako takový, ale jako jednoduchý výjimka zpracování blok (`finally` nebo `catch`). V důsledku toho oblasti nespouští v události podmínku nedostatku paměti nebo přerušení přístup z více vláken.  
  
## <a name="cause"></a>příčina  
 Tento vzor přípravy CER nedodržíte správně.  Toto je událost chyby. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Volání metody, které používá se k označení obslužné rutiny výjimek jako představení CER v jejich `catch` / `finally` / `fault` / `filter` bloky se musí použít bezprostředně před `try` příkaz.  
  
## <a name="resolution"></a>Rozlišení  
 Ujistěte se, že volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se stane bezprostředně před `try` příkaz.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazí název volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun MSIL a zprávu s upozorněním, volání nepředchází okamžitě začátku bloku try.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje vzor, který způsobuje, že tento MDA chcete aktivovat.  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
