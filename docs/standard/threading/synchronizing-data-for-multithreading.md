---
title: Synchronizace dat pro vícevláknové zpracování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a7561a09b1b47827b3476b5525863503765064f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45526938"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizace dat pro vícevláknové zpracování
Při více vláken mohl provádět volání k vlastnostem a metodám jednoho objektu, je důležité, že tato volání synchronizovat. V opačném případě jedno vlákno může dojít k přerušení činnosti jiné vlákno a objekt může zůstat v neplatném stavu. Třídy, jejíž členové jsou chráněny i před přerušení práce se nazývá bezpečné pro vlákna.  
  
 Common Language Infrastructure poskytuje několik strategií k synchronizaci přístupu k instanci a statické členy:  
  
-   Oblasti synchronizované kódu. Můžete použít <xref:System.Threading.Monitor> třídy nebo kompilátoru podpora pro tuto třídu synchronizovat pouze kód bloku, která potřebuje, zvýšení výkonu.  
  
-   Ruční synchronizace. Můžete používat synchronizaci objektů v knihovně tříd rozhraní .NET Framework poskytuje. Naleznete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md), která obsahuje diskusi o <xref:System.Threading.Monitor> třídy.  
  
-   Synchronizované kontexty. Můžete použít <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> umožňující jednoduchý, automatické synchronizace pro <xref:System.ContextBoundObject> objekty.  
  
-   Třídy kolekcí v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů. Tyto třídy poskytují integrovanou synchronizované přidávat a odebírat operace. Další informace najdete v tématu [kolekce bezpečné pro vlákna](../../../docs/standard/collections/thread-safe/index.md).  
  
 Modul common language runtime poskytuje model vláken ve kterém třídy spadají do několika kategorií, které lze synchronizovat v různých různými způsoby v závislosti na požadavky. Následující tabulka uvádí, jaké synchronizace podpora se poskytuje pro pole a metody synchronizace dané kategorie.  
  
|Kategorie|Globální pole|Statická pole|Statické metody|Pole instance|Instance metody|Bloky kódu konkrétní|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Žádná synchronizace|Ne|Ne|Ne|Ne|Ne|Ne|  
|Synchronizované kontextu|Ne|Ne|Ne|Ano|Ano|Ne|  
|Oblasti synchronizované kódu|Ne|Ne|Pouze v případě označeny|Ne|Pouze v případě označeny|Pouze v případě označeny|  
|Ruční synchronizace|Ruční|Ruční|Ruční|Ruční|Ruční|Ruční|  
  
## <a name="no-synchronization"></a>Žádná synchronizace  
 Toto je výchozí nastavení pro objekty. Jakékoli vlákno může přístup k žádné metody nebo pole v každém okamžiku. Pouze jedno vlákno vždy měli přístup k těmto objektům.  
  
## <a name="manual-synchronization"></a>Ruční synchronizace  
 Knihovna tříd rozhraní .NET Framework poskytuje několik tříd pro synchronizaci vláken. Zobrazit [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Oblasti synchronizované kódu  
 Můžete použít <xref:System.Threading.Monitor> třídu nebo klíčové slovo kompilátoru synchronizovat bloky kódu, metody instance a statické metody. Není dostupná podpora pro synchronizované statická pole.  
  
 Visual Basic a C# podporují označování bloků kódu s klíčovým slovem konkrétní jazyk, `lock` příkaz v jazyce C# nebo `SyncLock` v sadě Visual Studio. Když je kód spuštěn podproces, je proveden pokus o získání zámku. Pokud zámek už získala společnost jiné vlákno, vlákno blokováno, dokud nebude k dispozici zámek. Při ukončení vlákna synchronizovaného bloku kódu, zámek je uvolněn, bez ohledu na to, jak vlákno opustí blok.  
  
> [!NOTE]
>  `lock` a `SyncLock` příkazy jsou implementovány pomocí <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, takže jiné metody <xref:System.Threading.Monitor> lze použít ve spojení s nimi v rámci oblasti synchronizované.  
  
 Můžete také uspořádání metodu s **MethodImplAttribute** a **MethodImplOptions.Synchronized**, který má stejný účinek jako použití **monitorování** nebo jeden z kompilátoru klíčová slova k uzamčení celý tělo metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> je možné přerušit vlákno mimo blokující operace, jako je čekání na přístup do synchronizované oblasti kódu. **Thread.Interrupt** slouží také k přerušení vlákna z operací, jako je <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Nepoužívejte zámky typ – to znamená, `typeof(MyType)` v jazyce C#, `GetType(MyType)` v jazyce Visual Basic nebo `MyType::typeid` v jazyce C++ – aby chránil `static` metody (`Shared` metody v jazyce Visual Basic). Místo toho použijte privátní statický objekt. Podobně, nepoužívejte `this` v jazyce C# (`Me` v jazyce Visual Basic) k uzamčení instanci metody. Místo toho použijte privátní objekt. Třídy nebo instance může být uzamčen kódu než vlastní a potenciálně nezpůsobil zablokování nebo problémy s výkonem.  
  
### <a name="compiler-support"></a>Podpora kompilátoru  
 Visual Basic a C# – klíčové slovo jazyka, který používá podporují <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> zamknout objekt. Visual Basic podporuje [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) příkaz C# podporuje [Zámek](~/docs/csharp/language-reference/keywords/lock-statement.md) příkazu.  
  
 V obou případech platí, pokud dojde k výjimce v kódu bloku zámek získaný **Zámek** nebo **SyncLock** se automaticky uvolní. Kompilátory C# a Visual Basic **zkuste**/**nakonec** blokovat s **Monitor.Enter** na začátku try, a **Monitor.Exit**  v **nakonec** bloku. Pokud dojde k výjimce uvnitř **Zámek** nebo **SyncLock** bloku **nakonec** spustí obslužnou rutinu, aby bylo možné provést žádnou práci čištění.  
  
## <a name="synchronized-context"></a>Synchronizované kontextu  
 Můžete použít **SynchronizationAttribute** na žádném **ContextBoundObject** k synchronizaci všech instanci metody a pole. Všechny objekty ve stejné doméně kontextu sdílet stejnou zámku. Více vláken je povolen přístup k metody a pole, ale v daný okamžik je povoleno pouze jedno vlákno.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
- [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
- [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
- [Příkaz SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
- [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md)
