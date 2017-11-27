---
title: "Synchronizace vláken (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b51775eac5221ec8c723d89323d1f4f542d2453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="thread-synchronization-c"></a>Synchronizace vláken (C#)
Následující části popisují funkce a třídy, které slouží k synchronizaci přístup k prostředkům v vícevláknové aplikace.  
  
 Jednou z výhod používání více vláken v aplikaci je asynchronně provádí každé vlákno. Pro aplikace systému Windows to umožňuje časově náročné úlohy, které mají být provedeny na pozadí při okna aplikace a ovládací prvky zůstanou reaguje. Aplikace, více vláken pro server poskytuje možnost pro zpracování jednotlivých příchozích požadavků s jiném podprocesu. Každý nový požadavek, jinak hodnota nebude získat servis dokud předchozí požadavek je plně splněna.  
  
 Ale musí být koordinované asynchronní povaha vláken znamená, že přístup k prostředkům, jako jsou popisovače souborů, připojení k síti a paměti. Dvě nebo více vláken, jinak hodnota přístup stejného zdroje ve stejnou dobu, každý dál, bez ohledu druhé strany akcí. Výsledkem je poškození dat nepředvídatelné.  
  
 Pro jednoduché operace na integrální číselné datové typy synchronizace vláken lze provést pomocí členy <xref:System.Threading.Interlocked> třídy. Pro všechna ostatní data typy a prostředky nejsou bezpečné pro přístup z více vláken, multithreading můžete bezpečně provést pouze pomocí konstrukce v tomto tématu.  
  
 Základní informace o vícevláknové programování naleznete v tématu:  
  
-   [Dělení na spravovaná vlákna základy](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Použití vláken a dělení na vlákna](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Dělení na spravovaná vlákna osvědčené postupy](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>Lock – klíčové slovo  
 C# `lock` příkaz lze použít k zajištění, že blok kódu zcela dokončena bez přerušení jiná vlákna. To lze provést po dobu trvání blok kódu získávání zámku vzájemné vyloučení pro daný objekt.  
  
 A `lock` příkaz je zadaný objekt jako argument a následuje blok kódu, který se má provádět pouze jedním vláknem současně. Příklad:  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 Argument poskytnuté `lock` – klíčové slovo musí být založený na typu odkaz na objekt a slouží k definování oboru zámku. V předchozím příkladu obor zámků je omezena na tuto funkci, protože žádné odkazy na objekt `lockThis` existovat mimo funkci. Pokud odkazu, by tento objekt rozšířit obor zámků. Zadaný objekt přesněji řečeno, slouží výhradně k jednoznačné identifikaci sdílený mezi více vláken, aby ho bylo možné instance třídy libovolný prostředek. V praxi ale tento objekt obvykle reprezentuje prostředků, pro které vlákno synchronizace je nezbytné. Například pokud objektu kontejneru se má používat více vláken, předána kontejneru k uzamčení a synchronizované kód bloku následující zámek by přístup kontejneru. Tak dlouho, dokud jiná vlákna zamkne ve stejném obsahuje před přístupem k, pak je přístup k objektu bezpečně synchronizován.  
  
 Obecně je vyhýbat se na zamykání `public` typ, nebo na instancí objektů mimo kontrolu vaší aplikace. Například `lock(this)` může být problematické, pokud instance je přístupná veřejně, protože kód mimo vaši kontrolu může zamknout na objekt i. To může vytvořit zablokování situacích, kde dva nebo více podprocesů čeká na uvolnění výskyty stejného objektu. Uzamčení na veřejné datového typu, na rozdíl od objektu, může způsobit problémy ze stejného důvodu. Uzamčení na řetězcové literály je obzvláště rizikové, protože řetězcové literály *interned* modulem common language runtime (CLR). To znamená, že jednu instanci libovolný daný řetězec je literál pro celý program, přesně stejný objekt představuje literál ve všech systémem všechna vlákna aplikační domény. V důsledku toho uzamknout řetězec se stejným obsahem, kdekoli v procesu uzamčení aplikace všechny instance tento řetězec v aplikaci. V důsledku toho je vhodné zamknout privátní nebo chráněného člena, který není interned. Některé třídy poskytují členy, konkrétně k uzamčení. <xref:System.Array> Typu, například poskytuje <xref:System.Array.SyncRoot%2A>. Zadejte mnoho typů kolekce `SyncRoot` také člen.  
  
 Další informace o `lock` příkaz, naleznete v následujících tématech:  
  
-   [Lock – příkaz](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>Sledování  
 Podobně jako `lock` – klíčové slovo, monitorování zabránit bloky kódu ze současné spuštění více vláken. <xref:System.Threading.Monitor.Enter%2A> Metoda umožňuje pouze jednu vlákno pokračujte do následující příkazy; jiná vlákna jsou blokována až provádění vlákna volání <xref:System.Threading.Monitor.Exit%2A>. Toto je stejně jako pomocí `lock` – klíčové slovo. Příklad:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Jde o ekvivalent:  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 Pomocí `lock` – klíčové slovo je obecně upřednostňované oproti použití <xref:System.Threading.Monitor> přímo třídu, jak protože `lock` je přesnější a protože `lock` zajistí, že základní monitorování vydání, i když chráněný kód vyvolá došlo k výjimce. To je provedeno pomocí `finally` – klíčové slovo, které se provádí jeho přidružený kód bloku bez ohledu na to, jestli je vyvolána výjimka.  
  
## <a name="synchronization-events-and-wait-handles"></a>Synchronizace události a obslužné rutiny čekání  
 Pomocí uzamčení nebo monitorování jsou užitečné pro zabránění souběžné spouštění citlivé na vlákno bloky kódu, ale tyto konstrukce neumožňují jedno vlákno pro komunikaci událost do jiného. To vyžaduje *synchronizace události*, které jsou objekty, které mají mezi dvěma stavy, signalizovaného a zrušení signalizovaného, který lze použít k aktivaci a pozastavení vláken. Vlákna pozastavil prováděné pro čekání na událost synchronizace, která je unsignaled a může být aktivováno změnou stavu událostí na signál. Pokud pro čekání na událost, která již signalizace pokusů o vlákno, vlákno pokračuje bez nutnosti zpoždění.  
  
 Existují dva typy událostí synchronizace: <xref:System.Threading.AutoResetEvent>, a <xref:System.Threading.ManualResetEvent>. Liší se pouze v tom, že <xref:System.Threading.AutoResetEvent> změny z signál na unsignaled automaticky vždycky, když se aktivuje vlákna. Naopak <xref:System.Threading.ManualResetEvent> umožňuje libovolný počet vláken, které chcete aktivovat podle jeho signalizovaného stavu a obnoví jenom se unsignaled stavu při jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána.  
  
 Vláken můžete provedeny pro čekání na události ve volání jedné z metod čekání, jako například <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, nebo <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>způsobí, že podproces Počkejte, dokud se změní na signál, jedna událost, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blokuje vlákno, dokud jeden nebo více událostí uvedené stát signál, a <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blokuje vlákno, dokud všechny uvedené události stane signál. Událost se změní na signál, když jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda je volána.  
  
 V následujícím příkladu se vytvoří a spustí vlákna `Main` funkce. Nové vlákno čeká na k událost pomocí <xref:System.Threading.WaitHandle.WaitOne%2A> metoda. Vlákno je pozastaveno, dokud se změní na událost signál primární podprocesem, který spouští `Main` funkce. Jakmile bude signál události, vrátí pomocného vlákno. V takovém případě protože události se používá pouze pro jedno vlákno aktivace buď <xref:System.Threading.AutoResetEvent> nebo <xref:System.Threading.ManualResetEvent> třídy by bylo možné použít.  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>Objekt mutex  
 A *mutex* je podobná monitorování; zabraňuje souběžných spuštění bloku kódu ve více než jedno vlákno najednou. Ve skutečnosti název "mutex" je zkrácený tvar termín "vzájemně vylučují." Na rozdíl od monitorování ale mutex slouží k synchronizaci vláken napříč procesy. Mutex je reprezentována <xref:System.Threading.Mutex> třídy.  
  
 Pokud se použije pro synchronizace mezi procesy, se nazývá mutex *pojmenovaný vzájemně vyloučený přístup* vzhledem k tomu, že je pro použití v jiné aplikaci, a proto nemohou být sdíleny prostřednictvím globální nebo statické proměnné. Je nutné mít název, aby obě aplikace přístup na stejný objekt mutex.  
  
 Mutex lze pro synchronizace uvnitř zpracování vláken, ale pomocí <xref:System.Threading.Monitor> je obecně upřednostňované, protože monitorování byly navrženy speciálně pro rozhraní .NET Framework a proto lépe využívat zdroje. Naopak <xref:System.Threading.Mutex> třída je obálka pro Win32 konstrukce. I když je mnohem snazší než monitorování, mutex vyžaduje spolupráce přechody, které jsou výpočetně nákladné než ty, které vyžadují <xref:System.Threading.Monitor> třídy. Příklad použití mutex, naleznete v části [mutex – třídy](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Interlocked – třída  
 Můžete použít metody <xref:System.Threading.Interlocked> třídy, aby problémy, ke kterým dochází při pokusu o několik vláken současně aktualizovat nebo porovnat stejnou hodnotu. Metody této třídy vám umožní bezpečně přírůstek, snížení, exchange a porovnání hodnot z libovolného vlákna.  
  
## <a name="readerwriter-locks"></a>Zámky ReaderWriter  
 V některých případech můžete chtít uzamknout prostředek jenom v případě, že zapisuje data a povolit více klientů současně číst data, je-li data není aktualizován. <xref:System.Threading.ReaderWriterLock> Třída vynucuje výhradní přístup k prostředku vlákno upravuje prostředek, ale nikoli výhradní přístup umožňuje při čtení prostředku. Zámky ReaderWriter jsou užitečné alternativou k výhradní zámek, které způsobují jiná vlákna počkat, i když tyto vláken není potřeba aktualizovat data.  
  
## <a name="deadlocks"></a>Zablokování  
 Synchronizace vláken je velice užitečné v vícevláknové aplikace, ale je vždy nebezpečí vytváření `deadlock`, kde více vláken, které čekají na sebe navzájem a aplikace se dodává zastavení. Zablokování se podobá k situaci, ve kterém jsou zastaveny automobilů na čtyři způsob zastavení a každá osoba čekání na další přejdete. Zamezení zablokování je důležité. klíč je pečlivé plánování. Zablokování situacích můžete často předvídání podle diagramů vícevláknové aplikace před zahájením kódování.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [Vícevláknové aplikace (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Lock – příkaz](../../../../csharp/language-reference/keywords/lock-statement.md)  
 [Mutex – třídy](../../../../standard/threading/mutexes.md)  
 [Propojené operace](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [Synchronizace dat pro Multithreading](../../../../standard/threading/synchronizing-data-for-multithreading.md)
