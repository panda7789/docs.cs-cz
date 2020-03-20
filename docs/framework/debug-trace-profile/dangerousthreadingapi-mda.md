---
title: dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174768"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
Spravovaný `dangerousThreadingAPI` pomocník pro ladění (MDA) <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> je aktivován, když je metoda volána v jiném vlákně než aktuálnívlákno.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace neodpovídá nebo přestane reagovat neomezeně dlouho. Data systému nebo aplikace mohou být dočasně ponechána v nepředvídatelném stavu nebo dokonce i po vypnutí aplikace. Některé operace nejsou dokončeny podle očekávání.  
  
 Příznaky se mohou značně lišit v důsledku náhodnosti vlastní problému.  
  
## <a name="cause"></a>Příčina  
 Podproces je asynchronně pozastavena jiným vláknem <xref:System.Threading.Thread.Suspend%2A> pomocí metody. Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace. Pozastavení podprocesu může mít za následek poškození dat nebo přerušení invariants. Pokud podproces být umístěn do pozastaveného stavu <xref:System.Threading.Thread.Resume%2A> a nikdy obnovena pomocí metody, aplikace může zavěsit neomezeně dlouho a případně poškodit data aplikace. Tyto metody byly označeny jako zastaralé.  
  
 Pokud synchronizační primitiva jsou drženy cílovým vláknem, zůstávají drženy během pozastavení. To může vést k zablokování by měl jiný podproces, například vlákno provádějící <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivní. V této situaci problém projevuje jako zablokování.  
  
## <a name="resolution"></a>Řešení  
 Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A>. Pro spolupráci mezi vlákny použijte synchronizační <xref:System.Threading.ReaderWriterLock> <xref:System.Threading.Mutex>primitiva, například <xref:System.Threading.Monitor>, , nebo c# `lock` příkaz. Pokud je nutné použít tyto metody, snížit časové okno a minimalizovat množství kódu, který se spustí, zatímco vlákno je v pozastaveném stavu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o nebezpečných operacích podprocesu.  
  
## <a name="output"></a>Výstup  
 MDA identifikuje nebezpečnou metodu threadingu, která způsobila jeho aktivaci.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metody, která způsobuje `dangerousThreadingAPI`aktivaci .  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
