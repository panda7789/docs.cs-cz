---
title: "moduloObjectHashcode – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 618196473e8e947e84b0506771bce84ee71a1c2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode – pomocník spravovaného ladění (MDA)
`moduloObjectHashcode` Pomocník spravovaného ladění (MDA) změní chování <xref:System.Object> třída k provedení modulo operace na vrátil kód hash <xref:System.Object.GetHashCode%2A> metoda. Modulus výchozí pro tento MDA je 1, což způsobí, že <xref:System.Object.GetHashCode%2A> vrátit 0 pro všechny objekty.  
  
## <a name="symptoms"></a>Příznaky  
 Po přesunutí na novou verzi common language runtime (CLR), program již provede správně:  
  
-   Tento program je získávání nesprávný objektu z <xref:System.Collections.Hashtable>.  
  
-   Pořadí výčtu z <xref:System.Collections.Hashtable> obsahuje změny, která dělí program.  
  
-   Dva objekty, které používá k rovná již nejsou stejné.  
  
-   Nyní jsou stejné dva objekty, které používají k nesmí být stejné.  
  
## <a name="cause"></a>příčina  
 Váš program může být získávání nesprávný objektu z <xref:System.Collections.Hashtable> protože provádění <xref:System.Object.Equals%2A> metody pro třídu pro klíč do <xref:System.Collections.Hashtable> testy rovnosti objektů srovnáním výsledků volání <xref:System.Object.GetHashCode%2A> – metoda . Hash – kódy nepoužívejte k testování rovnosti objekt, protože dva objekty může mít stejnou hodnotu hash, i když je jejich odpovídající pole mají různé hodnoty. Tyto kód kolize hodnot hash, i když je taková situace vzácná, v praxi, dojít. To má na účinek <xref:System.Collections.Hashtable> vyhledávání je, že dva klíče, které se neshodují se zdají být rovna a nesprávný objekt je vrácen z <xref:System.Collections.Hashtable>. Z důvodů výkonu implementace <xref:System.Object.GetHashCode%2A> runtime verze, takže kolize, které nemusí být na jednu verzi může dojít v budoucích verzích se může změnit. Povolte tento MDA k ověření, zda má váš kód chyby při konfliktu kódů hash. Pokud povolena, budou tato MDA <xref:System.Object.GetHashCode%2A> metoda vrátí 0, což vede k všech kódů hash kolize. Pouze účinku povolení, které na váš program by měl mít tato MDA je váš program probíhá pomaleji.  
  
 Pořadí výčtu z <xref:System.Collections.Hashtable> může změnit z jedné verze modulu runtime, když se jiný algoritmus používaný k výpočtu kódů hash pro změny klíče. K ověření, zda váš program trvá závislostí v řádu výčet klíče nebo hodnoty mimo zatřiďovací tabulku, můžete povolit tuto (mda).  
  
## <a name="resolution"></a>Rozlišení  
 Hash – kódy nikdy nepoužívejte jako náhrada za identity objektu. Implementace přepis metody <xref:System.Object.Equals%2A?displayProperty=nameWithType> metoda není porovnat kódů hash.  
  
 Nevytvářejte závislosti v řádu výčty klíče nebo hodnoty hash – tabulky.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Aplikace pracovat pomaleji, pokud je povolena tato (mda). Tato MDA jednoduše trvá hash, která by byly vráceny a místo toho vrátí zbytek po dělený numerického zbytku.  
  
## <a name="output"></a>Výstup  
 Neexistuje žádný výstup pro tento (mda).  
  
## <a name="configuration"></a>Konfigurace  
 `modulus` Atribut určuje numerického zbytku použít na hodnotu hash. Výchozí hodnota je 1.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
