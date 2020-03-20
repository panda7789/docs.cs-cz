---
title: openGenericCERCall – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181778"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall – pomocník spravovaného ladění (MDA)

Spravovaný `openGenericCERCall` ladicí asistent je aktivován, aby varoval, že graf oblasti omezeného spuštění (CER) s obecnými proměnnými typu v kořenové metodě je zpracováván v době kompilace JIT nebo nativnígenerace bitové kopie a alespoň jedna z proměnných obecného typu je typ odkazu na objekt.

## <a name="symptoms"></a>Příznaky

Kód CER se nespustí, pokud je vlákno přerušeno nebo když je uvolněna doména aplikace.

## <a name="cause"></a>Příčina

V době kompilace JIT je instance obsahující typ odkazu na objekt pouze reprezentativní, protože výsledný kód je sdílen a každá z proměnných typu odkazu na objekt může být libovolný typ odkazu na objekt. To může zabránit přípravě některých prostředků run-time předem.

Zejména metody s proměnnými typu obecného typu mohou líně přidělit prostředky na pozadí. Tyto položky jsou označovány jako položky obecného slovníku. Například pro `List<T> list = new List<T>();` příkaz, `T` kde je obecná proměnná typu, musí runtime vyhledat a případně vytvořit `List<Object>, List<String>`přesnou inkaso za běhu, například , a tak dále. To může selhat z různých důvodů mimo kontrolu vývojáře, jako je například nedostatek paměti.

Tento MDA by měl být aktivován pouze v době kompilace JIT, nikoli v případě, že existuje přesná instance.

Když je aktivován tento MDA, pravděpodobné příznaky jsou, že CER nejsou funkční pro špatné konkresace. Ve skutečnosti se runtime nepokusil implementovat CER za okolností, které způsobily aktivaci MDA. Takže pokud vývojář používá sdílenou instanci CER, pak jit kompilace chyby, obecné typy typu načítání chyby nebo podproces přeruší v rámci oblasti zamýšlené CER nejsou zachyceny.

## <a name="resolution"></a>Řešení

Nepoužívejte obecné proměnné typu, které jsou typu odkazu na objekt pro metody, které mohou obsahovat CER.

## <a name="effect-on-the-runtime"></a>Vliv na běhový čas

Tento MDA nemá žádný vliv na CLR.

## <a name="output"></a>Výstup

Následuje ukázka výstupu z tohoto MDA:
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a>Příklad

Kód CER není spuštěn.

```csharp
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

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
