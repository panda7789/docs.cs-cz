---
title: illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052674"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
Pomocník `illegalPrepareConstrainedRegion` spravovaného ladění (MDA) je aktivován, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> Pokud volání metody přímo nepředchází `try` příkaz obslužné rutiny výjimky. Toto omezení je na úrovni MSIL, takže je povoleno mít zdroj negenerující kód mezi voláním a `try`, jako jsou komentáře.  
  
## <a name="symptoms"></a>Příznaky  
 Omezená oblast provádění (CER), která se nikdy nepovažuje za takovou, ale jako jednoduchý blok zpracování výjimek (`finally` nebo `catch`). V důsledku toho se oblast nespustí v případě stavu mimo paměti nebo přerušení vlákna.  
  
## <a name="cause"></a>příčina  
 Vzor přípravy pro CER se nedodržuje správně.  Toto je chybná událost. / / `catch` `fault` Volánímetodypoužité`filter` k označení obslužných rutin výjimek, `finally` protože/ zavedete-li CER do bloků, je nutné použít bezprostředně před <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> `try` příkaz.  
  
## <a name="resolution"></a>Řešení  
 Zajistěte, aby <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> volání následovalo těsně `try` před příkazem.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazuje název metody, která volá <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun MSIL a zprávu indikující volání bezprostředně před začátkem bloku try.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje vzor, který způsobuje, že je tento MDA aktivován.  
  
```csharp
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
