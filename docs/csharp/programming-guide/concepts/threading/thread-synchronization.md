---
title: Synchronizace vláken (C#)
ms.date: 07/20/2015
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
ms.openlocfilehash: 6f0fe42c06b27369612cf586c7a93ce098822162
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509383"
---
# <a name="thread-synchronization-c"></a>Synchronizace vláken (C#)
Následující části popisují funkce a třídy, které slouží k synchronizaci přístupu k prostředkům ve vícevláknových aplikacích.  
  
 Jednou z výhod používání více vláken v aplikaci je, že se každý podproces spustí asynchronně. Pro aplikace Windows díky tomu časově náročné úlohy provádět na pozadí při okna aplikace a ovládací prvky stále reagovat. Pro server aplikace multithreading poskytuje možnost pro zpracování jednotlivých příchozích požadavků s jiném vlákně. V opačném případě nebude získat každému novému požadavku Údržba až do předchozí požadavek nebyl plně spokojeni.  
  
 Ale musí být koordinované asynchronní povaze vlákna znamená, že přístup k prostředkům, jako jsou popisovače souborů, připojení k síti a paměti. V opačném případě dvě či více vláken může přistupovat k stejný prostředek ve stejnou dobu, každý vědět o druhé strany akce. Výsledkem je poškození dat nepředvídatelné.  
  
 Pro jednoduché operace na integrální číselné datové typy, synchronizaci vláken můžete docílit, když se členy <xref:System.Threading.Interlocked> třídy. Pro všechna ostatní data typů a prostředků, není bezpečná pro vlákno, multithreading lze bezpečně provést pouze pomocí konstrukce v tomto tématu.  
  
 Základní informace o programování s více vlákny naleznete v tématu:  
  
-   [Základy dělení na spravovaná vlákna](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Použití vláken a dělení na vlákna](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Doporučené postupy dělení na spravovaná vlákna](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>Lock – klíčové slovo  
 C# `lock` příkaz lze použít k zajištění, že blok kódu úloha poběží do konce bez přerušení jiných vláken. Toho lze dosáhnout získání zámku vzájemné vyloučení pro daný objekt po dobu trvání bloku kódu.  
  
 A `lock` příkaz je zadaný objekt jako argument a následuje blok kódu, který je provádět najednou pouze jedno vlákno. Příklad:  
  
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
  
 Argument uvedený pro `lock` – klíčové slovo musí být objekt podle typu odkazu a slouží k definování oboru zámek. V předchozím příkladu zámek rozsah je omezen na tuto funkci, protože žádné odkazy na objekt `lockThis` existují mimo funkci. Pokud takový odkaz, obor zámků i na tento objekt. Přesněji řečeno zadaný objekt slouží pouze k jednoznačné identifikaci sdílený mezi více vlákny, pak se instance libovolné třídy bude prostředek. V praxi, ale tento objekt obvykle představuje prostředek, pro které vlákno je nezbytné synchronizace. Pokud objekt kontejneru se použije ve víc vláknech, potom kontejner může být předán Zamknout a blok synchronizované kódu po uzamčení bude přístup ke kontejneru. Tak dlouho, dokud jiná vlákna uzamkne na stejném obsahuje před přístupem k jeho, pak se bezpečně synchronizuje přístup k objektu.  
  
 Obecně je vhodné vyhnout zamykání `public` typ, nebo na instance objektů mimo kontrolu vaší aplikace. Například `lock(this)` může být problematické, pokud instance je přístupná veřejně, protože mohou na objekt i uzamknout kódu mimo vaši kontrolu. To může vytvořit zablokování situací, ve kterém dvě či více vláken čeká na uvolnění na stejný objekt. Uzamčení na veřejné datový typ, na rozdíl od objektu, může způsobit problémy ze stejného důvodu. Uzamčení na literál řetězce je zejména riskantní, protože řetězcové literály jsou *internovány* modulem common language runtime (CLR). To znamená, že jednu instanci libovolné daný řetězec je literál celého programu, přesně stejný objekt představuje literál ve všech spuštění aplikační domény, na všech vláknech. V důsledku toho uzamknout řetězec s použitím stejného obsahu kdekoli v procesu uzamčení aplikace všechny výskyty tohoto řetězce do aplikace. V důsledku toho je nejlepší soukromé nebo chráněné člena, který není internovány zamknout. Některé třídy poskytovaly členy speciálně pro uzamčení. <xref:System.Array> Typ, například poskytuje <xref:System.Array.SyncRoot%2A>. Poskytuje mnoho typů kolekce `SyncRoot` také člena.  
  
 Další informace o `lock` příkaz, naleznete v následujících tématech:  
  
-   [lock – příkaz](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>Sledování  
 Podobně jako `lock` – klíčové slovo, monitorování předcházet bloky kódu z souběžné provádění více vláken. <xref:System.Threading.Monitor.Enter%2A> Metoda umožňuje jeden a pouze jeden vláknu pokračovat na následující příkazy – všechny ostatní vlákna jsou zablokována až do spuštěné vlákno vyvolá <xref:System.Threading.Monitor.Exit%2A>. Toto je stejně jako kdybyste službu `lock` – klíčové slovo. Příklad:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 To je ekvivalentní:  
  
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
  
 Pomocí `lock` – klíčové slovo je obecně upřednostňované nad pomocí <xref:System.Threading.Monitor> přímo třídu, obě protože `lock` je stručnější a protože `lock` zajistí, že základní monitorování vydání, i v případě chráněných kód vyvolá výjimku došlo k výjimce. Toho se dosahuje pomocí `finally` – klíčové slovo, která spustí bloku přidružený kód bez ohledu na to, zda je vyvolána výjimka.  
  
## <a name="synchronization-events-and-wait-handles"></a>Synchronizace události a obslužné rutiny čekání  
 Použití uzamčení nebo monitorování je k zamezení souběžné provádění vlákna zohledňující bloky kódu, ale tyto konstrukce neumožňují jedno vlákno pro komunikaci událost do jiného. To vyžaduje, aby *synchronizace události*, které jsou objekty, které mají jednu ze dvou stavů, signalizovaného a zrušení signalizovaného, který slouží k aktivaci a pozastavení vlákna. Vlákna pozastaví pomocí provádí čekání na událost synchronizace, která je unsignaled a je možné aktivovat tak, že změníte stav událostí na signál. Pokud vlákno se pokusí čekání na událost, která je již signalizována, vlákno pokračuje k provedení bez zpoždění.  
  
 Existují dva typy událostí synchronizace: <xref:System.Threading.AutoResetEvent>, a <xref:System.Threading.ManualResetEvent>. Se liší pouze v dané <xref:System.Threading.AutoResetEvent> změny z signalizován na unsignaled automaticky pokaždé, když se aktivuje vlákno. Naopak <xref:System.Threading.ManualResetEvent> umožňuje libovolný počet vláken aktivováno signalizovaného stavu a bude pouze používat unsignaled stav, kdy jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána.  
  
 Vlákna můžete provést pro čekání na události ve volání jedné z metod čekání, jako například <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, nebo <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> způsobí, že vlákno počkat, až bude signál, jedna událost, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blokuje vlákno, dokud jeden nebo více uvedené události stát signalizovanými, a <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blokuje vlákno, dokud všechny uvedené události signálování. Událost se stane signál, když jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda je volána.  
  
 V následujícím příkladu se vytvoří a tím, že vlákno `Main` funkce. Nové vlákno čeká na událost pomocí <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Vlákno je pozastaveno, dokud události stane primární vlákno, které provádí signál, `Main` funkce. Jakmile bude signál události, vrátí pomocné vlákno. V tomto případě protože událost se používá jenom pro jedno vlákno aktivace, buď <xref:System.Threading.AutoResetEvent> nebo <xref:System.Threading.ManualResetEvent> třídy může používat.  
  
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
 A *mutex* se podobá monitorování, zabrání současné spuštění bloku kódu ve více než jedno vlákno v čase. Název "mutex" se ve skutečnosti zkráceným tvarem termín "vzájemně se vylučuje." Na rozdíl od monitorování ale objekt mutex slouží k synchronizaci vláken napříč procesy. Objekt mutex je reprezentována <xref:System.Threading.Mutex> třídy.  
  
 Když se použije pro synchronizaci mezi procesy, se nazývá mutex *pojmenovaný vzájemně vyloučený přístup* vzhledem k tomu je možné použít v jiné aplikaci, a proto není možné sdílet prostřednictvím globální nebo statická proměnná. To se musí předávat název, aby obě aplikace přístup na stejný objekt mutex.  
  
 Objekt mutex lze pro synchronizaci vláken uvnitř procesu, ale pomocí <xref:System.Threading.Monitor> je obecně upřednostňované, protože monitorování byly navrženy specificky pro rozhraní .NET Framework a proto lépe využívat zdroje. Naproti tomu <xref:System.Threading.Mutex> třídy tvoří obálku pro konstrukci Win32. I když je výkonnější než monitorování, mutex vyžaduje vzájemné spolupráce přechody, která jsou než ty, které vyžadují více výpočetně náročné <xref:System.Threading.Monitor> třídy. Příklad použití objektu mutex, naleznete v tématu [mutexů](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Interlocked – třída  
 Můžete použít metody <xref:System.Threading.Interlocked> třídy, aby se zabránilo problémům, které může dojít, pokud více vláken pokusí zároveň aktualizovat nebo porovnání stejnou hodnotu. Metody této třídy umožňují bezpečně přírůstek, snížení, exchange a porovnat hodnoty z libovolného vlákna.  
  
## <a name="readerwriter-locks"></a>Zámky ReaderWriter  
 V některých případech můžete uzamknout prostředek pouze v případě, že se zápisem dat a povolit víc klientů současně číst data, když se aktualizuje data. <xref:System.Threading.ReaderWriterLock> Třídě vynucuje exkluzivní přístup k prostředku vlákno upravuje prostředek, ale umožní přístup neexkluzivní při čtení prostředku. Zámky ReaderWriter jsou užitečnou alternativou pro výhradní zámek, které způsobují ostatní vlákna čekat, i když tato vlákna není potřeba aktualizovat data.  
  
## <a name="deadlocks"></a>Zablokování  
 Synchronizace vláken je neocenitelný při řízení aplikací s více vlákny, ale je vždy nebezpečí vytvoření `deadlock`, kde více vláken čekají na sebe navzájem a aplikace jde o zastavení. Zablokování je podobná situace, ve kterém auta se zastaví na zarážku čtyř směrů a každý uživatel, který čeká na další přechod. Předcházení zablokování je důležité. klíč je pečlivé plánování. Často můžete předpovídat situace zablokování pomocí diagramů vícevláknové aplikace před spuštěním kódu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>  
- <xref:System.Threading.WaitHandle.WaitOne%2A>  
- <xref:System.Threading.WaitHandle.WaitAny%2A>  
- <xref:System.Threading.WaitHandle.WaitAll%2A>  
- <xref:System.Threading.Thread.Join%2A>  
- <xref:System.Threading.Thread.Start%2A>  
- <xref:System.Threading.Thread.Sleep%2A>  
- <xref:System.Threading.Monitor>  
- <xref:System.Threading.Mutex>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Interlocked>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading>  
- <xref:System.Threading.EventWaitHandle.Set%2A>  
- <xref:System.Threading.Monitor>  
- [lock – příkaz](../../../../csharp/language-reference/keywords/lock-statement.md)  
- [Mutex – třídy](../../../../standard/threading/mutexes.md)  
- [Propojené operace](../../../../standard/threading/interlocked-operations.md)  
- [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
- [Synchronizace dat pro vícevláknové zpracování](../../../../standard/threading/synchronizing-data-for-multithreading.md)
