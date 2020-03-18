---
title: Synchronizace dat pro vícevláknové zpracování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
ms.openlocfilehash: a70bd3070d8b1dcd06e55d330a01d29071293f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159387"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizace dat pro vícevláknové

Pokud více vláken může volat vlastnosti a metody jednoho objektu, je důležité, aby tato volání byla synchronizována. V opačném případě jedno vlákno může přerušit to, co dělá jiné vlákno, a objekt může být ponechán v neplatném stavu. Třída, jejíž členy jsou chráněny před těmito přerušeními se nazývá bezpečné pro přístup z více vláken.  
  
Rozhraní .NET poskytuje několik strategií pro synchronizaci přístupu k instancí a statickým členům:  
  
- Oblasti synchronizovaných kódů. Podporu třídy <xref:System.Threading.Monitor> nebo kompilátoru pro tuto třídu můžete použít k synchronizaci pouze bloku kódu, který ji potřebuje, a zlepšení výkonu.  
  
- Ruční synchronizace. Můžete použít synchronizační objekty poskytované knihovnou tříd .NET. Viz [Přehled základních synchronizačních zařízení](../../../docs/standard/threading/overview-of-synchronization-primitives.md), <xref:System.Threading.Monitor> který zahrnuje diskusi o třídě.  
  
- Synchronizované kontexty. Pro aplikace .NET Framework a Xamarin <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> můžete použít k povolení <xref:System.ContextBoundObject> jednoduché, automatické synchronizace pro objekty.  
  
- Třídy kolekce <xref:System.Collections.Concurrent?displayProperty=nameWithType> v oboru názvů. Tyto třídy poskytují integrované synchronizované operace přidání a odebrání. Další informace naleznete v [tématu Thread-Safe Collections](../../../docs/standard/collections/thread-safe/index.md).  
  
 Běžný jazyk runtime poskytuje model podprocesu, ve kterém třídy spadají do několika kategorií, které lze synchronizovat různými způsoby v závislosti na požadavcích. V následující tabulce je uvedena podpora synchronizace pro pole a metody s danou kategorií synchronizace.  
  
|Kategorie|Globální pole|Statická pole|Statické metody|Pole instance|Metody instance|Specifické bloky kódu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Žádná synchronizace|Ne|Ne|Ne|Ne|Ne|Ne|  
|Synchronizovaný kontext|Ne|Ne|Ne|Ano|Ano|Ne|  
|Synchronizované oblasti kódu|Ne|Ne|Pouze v případě, že je označen|Ne|Pouze v případě, že je označen|Pouze v případě, že je označen|  
|Ruční synchronizace|Ruční|Ruční|Ruční|Ruční|Ruční|Ruční|  
  
## <a name="no-synchronization"></a>Žádná synchronizace  
 Toto je výchozí nastavení pro objekty. Jakékoli vlákno může kdykoli přistupovat k libovolné metodě nebo poli. Pouze jedno vlákno najednou by měl přístup k těmto objektům.  
  
## <a name="manual-synchronization"></a>Ruční synchronizace  
 Knihovna tříd .NET poskytuje řadu tříd pro synchronizaci vláken. Viz [Přehled základních synchronizačních zařízení](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Oblasti synchronizovaných kódů  
 Můžete použít <xref:System.Threading.Monitor> třídu nebo klíčové slovo kompilátoru k synchronizaci bloků kódu, metod instance a statických metod. Neexistuje žádná podpora pro synchronizovaná statická pole.  
  
 Visual Basic a C# podporují označování bloků kódu s klíčovým `lock` slovem určitého `SyncLock` jazyka, příkaz v jazyce C# nebo příkaz v jazyce Visual Basic. Při spuštění kódu podprocesem, je proveden pokus o získání zámku. Pokud zámek již byla získána jiným vláknem, vlákno blokuje, dokud zámek k dispozici. Když vlákno ukončí synchronizovaný blok kódu, zámek je uvolněn, bez ohledu na to, jak vlákno ukončí blok.  
  
> [!NOTE]
> `lock` Příkazy `SyncLock` a jsou <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>implementovány pomocí <xref:System.Threading.Monitor> a , takže jiné metody lze použít ve spojení s nimi v rámci synchronizované oblasti.  
  
 Můžete také ozdobit metodu <xref:System.Runtime.CompilerServices.MethodImplAttribute> s <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>hodnotou , která má <xref:System.Threading.Monitor> stejný účinek jako použití nebo jedno z klíčových slov kompilátoru k uzamčení celého těla metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>lze přerušit vlákno z blokování operací, jako je například čekání na přístup k synchronizované oblasti kódu. **Thread.Interrupt** se také používá k přerušení <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>podprocesů z operací, jako je .  
  
> [!IMPORTANT]
> Neuzamknout typ – `typeof(MyType)` to je `GetType(MyType)` v jazyce `MyType::typeid` C#, v jazyce `static` Visual`Shared` Basic nebo v jazyce C++ – k ochraně metod (metody v jazyce Visual Basic). Místo toho použijte soukromý statický objekt. Podobně nepoužívejte `this` v jazyce`Me` C# ( v jazyce Visual Basic) k uzamčení metod instance. Místo toho použijte soukromý objekt. Třídu nebo instanci lze uzamknout jiným kódem než vlastním, což může způsobit zablokování nebo problémy s výkonem.  
  
### <a name="compiler-support"></a>Podpora kompilátoru  
 Visual Basic a C# podporují klíčové <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> slovo jazyka, který používá a uzamkne objekt. Visual Basic podporuje [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) prohlášení; C# podporuje příkaz [lock.](../../csharp/language-reference/keywords/lock-statement.md)  
  
 V obou případech, pokud je vyvolána výjimka v bloku kódu, zámek získané **zámek** nebo **SyncLock** je uvolněna automaticky. C# a Visual Basic kompilátory vyzařují **try**/**finally** bloku s **Monitor.Enter** na začátku try a **Monitor.Exit** v **finally** bloku. Pokud je vyvolána výjimka uvnitř **zámku** nebo **SyncLock** bloku, **finally** obslužná rutina spustí, aby vám umožní provést všechny vyčištění práce.  
  
## <a name="synchronized-context"></a>Synchronizovaný kontext  

Pouze v rozhraní .NET Framework a Xamarin můžete použít <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> na libovolné <xref:System.ContextBoundObject> synchronizovat všechny metody instance a pole. Všechny objekty ve stejné kontextové doméně sdílejí stejný zámek. Více vláken je povoleno přístup k metodám a polím, ale pouze jedno vlákno je povoleno v jednom okamžiku.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)
- [Přehled základních synchronizačních zařízení](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock – příkaz](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
