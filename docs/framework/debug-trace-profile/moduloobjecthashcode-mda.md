---
title: moduloObjectHashcode – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b1223839be3747b04810d6b5bd131733c41631f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614379"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode – pomocník spravovaného ladění (MDA)
`moduloObjectHashcode` Pomocníka spravovaného ladění (MDA) změní chování <xref:System.Object> pro provádění modulo operace na vrátil kód hash <xref:System.Object.GetHashCode%2A> metoda. Výchozí modul pro toto MDA je 1, což způsobí, že <xref:System.Object.GetHashCode%2A> vrátit 0 pro všechny objekty.  
  
## <a name="symptoms"></a>Příznaky  
 Po přesunutí na novou verzi modulu common language runtime (CLR), program už správně provede:  
  
- Program je stále nesprávný objekt z <xref:System.Collections.Hashtable>.  
  
- Pořadí výčtu ze <xref:System.Collections.Hashtable> má změnu, která program přestane fungovat.  
  
- Dva objekty, které používají musí rovnat už nejsou stejné.  
  
- Nyní jsou objekty, které používají nebude stejný jako rovnocenné.  
  
## <a name="cause"></a>Příčina  
 Váš program může zobrazovat v objektu nesprávného z <xref:System.Collections.Hashtable> protože provádění <xref:System.Object.Equals%2A> metody ve třídě pro klíč do <xref:System.Collections.Hashtable> testy pro rovnost objektů porovnáním výsledky volání <xref:System.Object.GetHashCode%2A> – metoda . Kódů hash by neměl použije k testování rovnosti objektu, protože dva objekty mohou mít stejnou hodnotu hash, i když jejich příslušných polí mají různé hodnoty. Tyto kolize hodnot hash kód, i když je vzácné v praxi, dojde k. To má vliv <xref:System.Collections.Hashtable> vyhledávání je, že dva klíče, které nejsou shodné se zdají být stejné, a špatný objekt je vrácen z <xref:System.Collections.Hashtable>. Z důvodů výkonu provádění <xref:System.Object.GetHashCode%2A> verze modulu runtime, takže kolize, které nemusí být na jednu verzi můžou probíhat v budoucích verzích se může změnit. Povolte toto MDA k otestování, jestli váš kód obsahuje chyby, když dojde ke kolizi těchto kódů hash. Když je povoleno, toto MDA způsobí, že <xref:System.Object.GetHashCode%2A> metoda vrátí 0, výsledkem všech kódů hash kolize. Pouze účinku povolení, které toto MDA by měl mít v programu je, že váš program spouští pomaleji.  
  
 Pořadí výčtu ze <xref:System.Collections.Hashtable> může změnit z jedné verze modulu runtime, pokud jiný algoritmus používaný k výpočtu hodnoty hash kódy pro změnu klíče. K otestování, jestli váš program přijal závislost na pořadí výčtu klíče nebo hodnoty z tabulky hash, můžete povolit toto MDA.  
  
## <a name="resolution"></a>Řešení  
 Nikdy nepoužívejte kódů hash jako náhradu identity objektu. Implementace přepsané <xref:System.Object.Equals%2A?displayProperty=nameWithType> metoda není výsledkem porovnání kódů hash.  
  
 Nevytvářejte závislosti v řádu výčty klíče nebo hodnoty ve zatřiďovacích tabulek.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Aplikace poběží pomaleji, pokud je povolené toto MDA. Toto MDA jednoduše převezme, která by byla vrácena hodnota hash a místo toho vrátí zbytek po vydělení zbytku.  
  
## <a name="output"></a>Výstup  
 Neexistuje žádný výstup pro toto MDA.  
  
## <a name="configuration"></a>Konfigurace  
 `modulus` Atribut určuje modul používá na hodnotu hash. Výchozí hodnota je 1.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
