---
title: illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění illegalPrepareConstrainedRegion, který je vyvolán, pokud volání PrepareConstrainedRegions není následováno příkazem try.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051282"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
`illegalPrepareConstrainedRegion`Pomocník spravovaného ladění (MDA) je aktivován, pokud <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> volání metody přímo nepředchází `try` příkaz obslužné rutiny výjimky. Toto omezení je na úrovni MSIL, takže je povoleno mít zdroj negenerující kód mezi voláním a `try` , jako jsou komentáře.  
  
## <a name="symptoms"></a>Příznaky  
 Omezená oblast provádění (CER), která se nikdy nepovažuje za takovou, ale jako jednoduchý blok zpracování výjimek ( `finally` nebo `catch` ). V důsledku toho se oblast nespustí v případě stavu mimo paměti nebo přerušení vlákna.  
  
## <a name="cause"></a>Příčina  
 Vzor přípravy pro CER se nedodržuje správně.  Toto je chybná událost. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Volání metody použité k označení obslužných rutin výjimek, protože zavedete-li CER do jejich `catch` / `finally` / `fault` / `filter` bloků, je nutné použít těsně před `try` příkazem.  
  
## <a name="resolution"></a>Řešení  
 Zajistěte, aby volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> následovalo těsně před `try` příkazem.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazuje název metody, která volá <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun MSIL a zprávu indikující volání bezprostředně před začátkem bloku try.  
  
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
