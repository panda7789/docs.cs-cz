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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2cb99a1bda8223ddece4b4aff4a87d95357d90e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153693"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall – pomocník spravovaného ladění (MDA)
`openGenericCERCall` Upozornit, oblast (CER) graf omezeného provádění s proměnnými obecného typu v metodě kořenové je zpracovávána v kompilaci JIT nebo nativní bitové kopie generování a alespoň jeden z obecného se aktivuje pomocníka spravovaného ladění Typ proměnné je odkaz na typ objektu.  
  
## <a name="symptoms"></a>Příznaky  
 CER kód nejde spustit, když je přerušeno vlákno nebo když je doména aplikace uvolněna.  
  
## <a name="cause"></a>příčina  
 V době kompilace JIT je instance obsahující odkaz na typ objektu, který pouze zástupce, protože výsledný kód je sdílet, a každý typ proměnné odkazu na objekt může být libovolný typ objektu odkaz. To může zabránit přípravy několik zdrojů informací za běhu, předem.  
  
 Zejména metody s proměnnými obecného typu laxně přidělení prostředků na pozadí. Tyto jsou označovány jako položky generický slovník. Například pro příkaz `List<T> list = new List<T>();` kde `T` je obecný typem proměnné modul runtime musí vyhledat a případně také mohli vytvářet přesné vytváření instancí v době běhu, třeba `List<Object>, List<String>`a tak dále. To může selhat z různých důvodů mimo kontrolu vývojáře, jako je například spuštění nedostatek paměti.  
  
 Toto MDA by měl být aktivována pouze v době kompilace JIT, ne po přesné vytváření instancí.  
  
 Když je toto MDA aktivováno, pravděpodobně příznaky jsou, že CERs nejsou funkční pro chybný instancí. Ve skutečnosti modul runtime nezačaly k implementaci CER za okolností, které způsobily MDA aktivaci. Pokud vývojář používá sdílené instance CER, pak chyby kompilace JIT, obecných typů zadejte chyby při načítání nebo zrušení vláken v oblasti určené CER proto nejsou zachyceny.  
  
## <a name="resolution"></a>Rozlišení  
 Nepoužívejte proměnné obecného typu, které jsou objekt odkazového typu pro metody, které mohou obsahovat CER.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Následuje ukázkový výstup z tohoto MDA.  
  
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
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
