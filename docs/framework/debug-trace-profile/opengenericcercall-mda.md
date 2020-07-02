---
title: openGenericCERCall – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění openGenericCERCall, který se může aktivovat, když se kód CER nespustí, když se vlákno přeruší nebo když se doména aplikace uvolní.
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
ms.openlocfilehash: 4df33b0cdf9759edec47f02b3feb671d03284ec8
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803934"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall – pomocník spravovaného ladění (MDA)

`openGenericCERCall`Pomocník spravovaného ladění je aktivován, aby upozornil na to, že graf s omezeným výkonem (CER) s proměnnými obecného typu v kořenové metodě je zpracováván při KOMPILACI JIT nebo v době generování nativní bitové kopie a nejméně jedna z obecných typů proměnných je typ odkazu na objekt.

## <a name="symptoms"></a>Příznaky

Kód CER se nespustí, pokud je vlákno přerušeno nebo pokud je doména aplikace uvolněna.

## <a name="cause"></a>Příčina

V době kompilace JIT je vytváření instancí obsahující typ odkazu na objekt pouze zástupce, protože výsledný kód je sdílen a každá proměnná typu odkazu na objekt může být libovolný typ odkazu na objekt. To může předem zabránit přípravě některých prostředků za běhu.

Konkrétně metody s proměnnými obecného typu mohou laxně vytvářená přidělit prostředky na pozadí. Ty jsou označovány jako položky obecného slovníku. Například pro příkaz, `List<T> list = new List<T>();` kde `T` je proměnná obecného typu, musí modul runtime vyhledat a případně vytvořit přesnou instanci v době běhu, například, `List<Object>, List<String>` a tak dále. To může selhat z nejrůznějších důvodů mimo řízení vývojáře, jako je například nedostatek paměti.

Tato položka MDA by měla být aktivována pouze v době kompilace JIT, nikoli v případě přesného vytvoření instance.

Když je tento MDA aktivovaný, je pravděpodobným symptomem, že CERs nejsou funkční pro špatné vytváření instancí. Ve skutečnosti se modul runtime nepokusil implementovat CER za okolností, které způsobily aktivaci modulu MDA. Takže pokud vývojář používá sdílené vytváření instancí CER, chyby kompilace JIT, chyby načítání obecných typů nebo přerušení vlákna v rámci oblasti zamýšleného CER se nezachycují.

## <a name="resolution"></a>Řešení

Nepoužívejte proměnné obecného typu, které jsou typu odkazu na objekt pro metody, které mohou obsahovat CER.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime

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

Kód CER není proveden.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
