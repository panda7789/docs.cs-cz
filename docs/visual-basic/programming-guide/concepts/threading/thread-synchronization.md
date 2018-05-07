---
title: Synchronizace vláken (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
ms.openlocfilehash: 9922230e1c7f2bd30c575bd66387feb4850a298b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="thread-synchronization-visual-basic"></a>Synchronizace vláken (Visual Basic)
Následující části popisují funkce a třídy, které slouží k synchronizaci přístup k prostředkům v vícevláknové aplikace.  
  
 Jednou z výhod používání více vláken v aplikaci je asynchronně provádí každé vlákno. Pro aplikace systému Windows to umožňuje časově náročné úlohy, které mají být provedeny na pozadí při okna aplikace a ovládací prvky zůstanou reaguje. Aplikace, více vláken pro server poskytuje možnost pro zpracování jednotlivých příchozích požadavků s jiném podprocesu. Každý nový požadavek, jinak hodnota nebude získat servis dokud předchozí požadavek je plně splněna.  
  
 Ale musí být koordinované asynchronní povaha vláken znamená, že přístup k prostředkům, jako jsou popisovače souborů, připojení k síti a paměti. Dvě nebo více vláken, jinak hodnota přístup stejného zdroje ve stejnou dobu, každý dál, bez ohledu druhé strany akcí. Výsledkem je poškození dat nepředvídatelné.  
  
 Pro jednoduché operace na integrální číselné datové typy synchronizace vláken lze provést pomocí členy <xref:System.Threading.Interlocked> třídy. Pro všechna ostatní data typy a prostředky nejsou bezpečné pro přístup z více vláken, multithreading můžete bezpečně provést pouze pomocí konstrukce v tomto tématu.  
  
 Základní informace o vícevláknové programování naleznete v tématu:  
  
-   [Základy dělení na spravovaná vlákna](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Použití vláken a dělení na vlákna](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Doporučené postupy dělení na spravovaná vlákna](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-and-synclock-keywords"></a>Uzamčení a SyncLock – klíčová slova  
 Visual Basic `SyncLock` příkaz lze použít k zajištění, že blok kódu zcela dokončena bez přerušení jiná vlákna. To lze provést po dobu trvání blok kódu získávání zámku vzájemné vyloučení pro daný objekt.  
  
 A `SyncLock` příkaz je zadaný objekt jako argument a následuje blok kódu, který se má provádět pouze jedním vláknem současně. Příklad:  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 Argument poskytnuté `SyncLock` – klíčové slovo musí být založený na typu odkaz na objekt a slouží k definování oboru zámku. V předchozím příkladu obor zámků je omezena na tuto funkci, protože žádné odkazy na objekt `lockThis` existovat mimo funkci. Pokud odkazu, by tento objekt rozšířit obor zámků. Zadaný objekt přesněji řečeno, slouží výhradně k jednoznačné identifikaci sdílený mezi více vláken, aby ho bylo možné instance třídy libovolný prostředek. V praxi ale tento objekt obvykle reprezentuje prostředků, pro které vlákno synchronizace je nezbytné. Například pokud objektu kontejneru se má používat více vláken, předána kontejneru k uzamčení a synchronizované kód bloku následující zámek by přístup kontejneru. Tak dlouho, dokud jiná vlákna zamkne ve stejném obsahuje před přístupem k, pak je přístup k objektu bezpečně synchronizován.  
  
 Obecně je vyhýbat se na zamykání `public` typ, nebo na instancí objektů mimo kontrolu vaší aplikace. Například `lockThis` může být problematické, pokud instance je přístupná veřejně, protože kód mimo vaši kontrolu může zamknout na objekt i. To může vytvořit zablokování situacích, kde dva nebo více podprocesů čeká na uvolnění výskyty stejného objektu. Uzamčení na veřejné datového typu, na rozdíl od objektu, může způsobit problémy ze stejného důvodu. Uzamčení na řetězcové literály je obzvláště rizikové, protože řetězcové literály *interned* modulem common language runtime (CLR). To znamená, že jednu instanci libovolný daný řetězec je literál pro celý program, přesně stejný objekt představuje literál ve všech systémem všechna vlákna aplikační domény. V důsledku toho uzamknout řetězec se stejným obsahem, kdekoli v procesu uzamčení aplikace všechny instance tento řetězec v aplikaci. V důsledku toho je vhodné zamknout privátní nebo chráněného člena, který není interned. Některé třídy poskytují členy, konkrétně k uzamčení. <xref:System.Array> Typu, například poskytuje <xref:System.Array.SyncRoot%2A>. Zadejte mnoho typů kolekce `SyncRoot` také člen.  
  
 Další informace o `SyncLock` příkaz, naleznete v následujících tématech:  
  
-   [Příkaz SyncLock](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>Sledování  
 Podobně jako `SyncLock` – klíčové slovo, monitorování zabránit bloky kódu ze současné spuštění více vláken. <xref:System.Threading.Monitor.Enter%2A> Metoda umožňuje pouze jednu vlákno pokračujte do následující příkazy; jiná vlákna jsou blokována až provádění vlákna volání <xref:System.Threading.Monitor.Exit%2A>. Toto je stejně jako pomocí `SyncLock` – klíčové slovo. Příklad:  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 Jde o ekvivalent:  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 Pomocí `SyncLock` – klíčové slovo je obecně upřednostňované oproti použití <xref:System.Threading.Monitor> přímo třídu, jak protože `SyncLock` je přesnější a protože `SyncLock` zajistí, že základní monitorování vydání, i když chráněný kód vyvolá došlo k výjimce. To je provedeno pomocí `Finally` – klíčové slovo, které se provádí jeho přidružený kód bloku bez ohledu na to, jestli je vyvolána výjimka.  
  
## <a name="synchronization-events-and-wait-handles"></a>Synchronizace události a obslužné rutiny čekání  
 Pomocí uzamčení nebo monitorování jsou užitečné pro zabránění souběžné spouštění citlivé na vlákno bloky kódu, ale tyto konstrukce neumožňují jedno vlákno pro komunikaci událost do jiného. To vyžaduje *synchronizace události*, které jsou objekty, které mají mezi dvěma stavy, signalizovaného a zrušení signalizovaného, který lze použít k aktivaci a pozastavení vláken. Vlákna pozastavil prováděné pro čekání na událost synchronizace, která je unsignaled a může být aktivováno změnou stavu událostí na signál. Pokud pro čekání na událost, která již signalizace pokusů o vlákno, vlákno pokračuje bez nutnosti zpoždění.  
  
 Existují dva typy událostí synchronizace: <xref:System.Threading.AutoResetEvent>, a <xref:System.Threading.ManualResetEvent>. Liší se pouze v tom, že <xref:System.Threading.AutoResetEvent> změny z signál na unsignaled automaticky vždycky, když se aktivuje vlákna. Naopak <xref:System.Threading.ManualResetEvent> umožňuje libovolný počet vláken, které chcete aktivovat podle jeho signalizovaného stavu a obnoví jenom se unsignaled stavu při jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána.  
  
 Vláken můžete provedeny pro čekání na události ve volání jedné z metod čekání, jako například <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, nebo <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> způsobí, že podproces Počkejte, dokud se změní na signál, jedna událost, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blokuje vlákno, dokud jeden nebo více událostí uvedené stát signál, a <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blokuje vlákno, dokud všechny uvedené události stane signál. Událost se změní na signál, když jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda je volána.  
  
 V následujícím příkladu se vytvoří a spustí vlákna `Main` funkce. Nové vlákno čeká na k událost pomocí <xref:System.Threading.WaitHandle.WaitOne%2A> metoda. Vlákno je pozastaveno, dokud se změní na událost signál primární podprocesem, který spouští `Main` funkce. Jakmile bude signál události, vrátí pomocného vlákno. V takovém případě protože události se používá pouze pro jedno vlákno aktivace buď <xref:System.Threading.AutoResetEvent> nebo <xref:System.Threading.ManualResetEvent> třídy by bylo možné použít.  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
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
 [Vícevláknové aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Příkaz SyncLock](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
 [Mutex – třídy](../../../../standard/threading/mutexes.md)  
 [Propojené operace](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [Synchronizace dat pro vícevláknové zpracování](../../../../standard/threading/synchronizing-data-for-multithreading.md)
