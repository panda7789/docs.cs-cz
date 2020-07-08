---
title: moduloObjectHashcode – pomocník spravovaného ladění (MDA)
description: Projděte si pomocníka spravovaného ladění moduloObjectHashcode (MDA), který změní třídu objektu tak, aby získala zbývající hodnotu ve výsledku metody GetHashCode.
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
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052062"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode – pomocník spravovaného ladění (MDA)
`moduloObjectHashcode`Pomocník spravovaného ladění (MDA) změní chování <xref:System.Object> třídy a provede operaci modulo u kódu hash vráceného <xref:System.Object.GetHashCode%2A> metodou. Výchozí modul pro tento MDA je 1, což způsobí, že <xref:System.Object.GetHashCode%2A> vrátí 0 pro všechny objekty.  
  
## <a name="symptoms"></a>Příznaky  
 Po přesunu na novou verzi modulu CLR (Common Language Runtime) se program již neprovádí správně:  
  
- Program získává špatný objekt z <xref:System.Collections.Hashtable> .  
  
- Pořadí výčtu z a <xref:System.Collections.Hashtable> má změnu, která program přerušuje.  
  
- Dva objekty, které mají být rovny, se již neshodují.  
  
- Jsou nyní stejné dva objekty, které se neshodují.  
  
## <a name="cause"></a>Příčina  
 Váš program může získat špatný objekt z objektu, <xref:System.Collections.Hashtable> protože implementace <xref:System.Object.Equals%2A> metody třídy pro klíč do <xref:System.Collections.Hashtable> testů pro rovnost objektů porovnáním výsledků volání <xref:System.Object.GetHashCode%2A> metody. Kódy hash by se neměly používat k testování rovnosti objektů, protože dva objekty mohou mít stejný kód hash, a to i v případě, že jejich příslušná pole mají jiné hodnoty. Tyto kolizí kódů hash, i když jsou v praxi zřídka, proběhnou. Efekt, který je výsledkem <xref:System.Collections.Hashtable> vyhledávání, je, že dva klíče, které nejsou stejné, se zdají být stejné a chybný objekt je vrácen z <xref:System.Collections.Hashtable> . Z důvodů výkonu může implementace nástroje <xref:System.Object.GetHashCode%2A> změnit mezi verzemi modulu runtime, takže kolize, ke kterým může dojít v jedné verzi, se mohou vyskytnout v následujících verzích. Povolte Tento MDA k otestování, jestli váš kód obsahuje chyby, když dojde ke kolizi kódů hash. Je-li tato možnost povolena, způsobí to, že <xref:System.Object.GetHashCode%2A> Metoda vrátí hodnotu 0, což vede ke konfliktu všech kódů hash. Jediným účinkem, který umožňuje této službě MDA, by měl mít program v programu, že váš program běží pomaleji.  
  
 Pořadí výčtu ze se <xref:System.Collections.Hashtable> může změnit z jedné verze modulu runtime na jiný, pokud algoritmus používaný k výpočtu kódů hash pro změnu klíče. Chcete-li otestovat, zda program provedl závislost na pořadí výčtu klíčů nebo hodnot z zatřiďovací tabulky, můžete povolit Tento MDA.  
  
## <a name="resolution"></a>Řešení  
 Nikdy nepoužívejte kódy hash jako náhradu identity objektu. Implementujte přepsání <xref:System.Object.Equals%2A?displayProperty=nameWithType> metody pro neporovnání kódů hash.  
  
 Nevytvářejte závislosti na pořadí výčtů klíčů nebo hodnot v zatřiďovacích tabulkách.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Pokud je tento MDA povolený, aplikace běží pomaleji. Tento MDA jednoduše převezme kód hash, který by byl vrácen, a místo toho vrátí zbytek, pokud je dělen modulem.  
  
## <a name="output"></a>Výstup  
 Pro tento MDA není k dispozici žádný výstup.  
  
## <a name="configuration"></a>Konfigurace  
 `modulus`Atribut určuje zbytky používané v kódu hash. Výchozí hodnota je 1.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
