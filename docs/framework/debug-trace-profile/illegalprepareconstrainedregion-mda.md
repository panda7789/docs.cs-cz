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
ms.openlocfilehash: b80d6160876834b22e8d9d1eb7112b8b67c15fcc
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216463"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
Pokud volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> přímo nepředchází příkaz `try` obslužné rutiny výjimky, je aktivována aplikace `illegalPrepareConstrainedRegion` Managed Debugging Assistant (MDA). Toto omezení je na úrovni jazyka MSIL, takže je povoleno mít zdroj negenerující kód mezi voláním a `try`, jako jsou například komentáře.  
  
## <a name="symptoms"></a>Příznaky  
 Omezená oblast provádění (CER), která se nikdy nepovažuje za takovou, ale jako jednoduchý blok zpracování výjimek (`finally` nebo `catch`). V důsledku toho se oblast nespustí v případě stavu mimo paměti nebo přerušení vlákna.  
  
## <a name="cause"></a>Příčina  
 Vzor přípravy pro CER se nedodržuje správně.  Toto je chybná událost. Volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> používané k označení obslužných rutin výjimek v `catch`/`finally`/`fault`/`filter` bloky musí být použity těsně před příkazem `try`.  
  
## <a name="resolution"></a>Řešení  
 Zajistěte, aby volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> následovalo těsně před příkazem `try`.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazuje název metody, která volá metodu <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, posun MSIL a zprávu indikující volání bezprostředně před začátkem bloku try.  
  
## <a name="configuration"></a>Konfigurace  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
