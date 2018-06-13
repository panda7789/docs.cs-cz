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
ms.openlocfilehash: 998e159cceded6da2e9c3068680c45bc1c9345a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591528"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizace dat pro vícevláknové zpracování
Když více vláken můžete volat vlastnosti a metody jednoho objektu, je velmi důležité synchronizovat těchto volání. V opačném případě může být jedno vlákno přerušení činnosti jiné vlákno a objekt může být ponecháno v neplatném stavu. Třídu, jejíž členové jsou chráněny před přerušení práce se nazývá bezpečné pro přístup z více vláken.  
  
 Common Language Infrastructure poskytuje několik strategií, které synchronizovat přístup k instanci a statické členy:  
  
-   Synchronizované kód oblasti. Můžete použít <xref:System.Threading.Monitor> třídu nebo kompilátoru podpory pro tuto třídu synchronizovat pouze blokovat kód, který potřebuje, zvýšení výkonu.  
  
-   Ruční synchronizace. Můžete použít objekty synchronizace poskytované knihovně tříd rozhraní .NET Framework. V tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md), což zahrnuje diskuzi o <xref:System.Threading.Monitor> třídy.  
  
-   Kontexty synchronizované. Můžete použít <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> povolení jednoduchý, automatické synchronizace pro <xref:System.ContextBoundObject> objekty.  
  
-   Třídy kolekcí v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů. Tyto třídy poskytují předdefinované synchronizované přidávat a odebírat operace. Další informace najdete v tématu [kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md).  
  
 Modul CLR poskytuje model vláken, ve kterém třídy lze rozdělit do několika kategorií, které je možné synchronizovat mnoha různými způsoby v závislosti na požadavcích na. Následující tabulka uvádí, jaké synchronizace podpora je k dispozici pro pole a metody s danou synchronizace kategorie.  
  
|Kategorie|Globální pole|Statická pole|Statické metody|Pole instance|Instance metody|Bloky konkrétní kódu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Žádná synchronizace|Ne|Ne|Ne|Ne|Ne|Ne|  
|Synchronizované kontextu|Ne|Ne|Ne|Ano|Ano|Ne|  
|Synchronizované kód oblasti|Ne|Ne|Pouze v případě označeny|Ne|Pouze v případě označeny|Pouze v případě označeny|  
|Ruční synchronizace|Ruční|Ruční|Ruční|Ruční|Ruční|Ruční|  
  
## <a name="no-synchronization"></a>Žádná synchronizace  
 Toto je výchozí hodnota pro objekty. Jakékoli vlákno můžete kdykoli přístup metoda a pole. Tyto objekty by měla přístup pouze jedno vlákno současně.  
  
## <a name="manual-synchronization"></a>Ruční synchronizace  
 Knihovna tříd rozhraní .NET Framework poskytuje několik tříd pro synchronizaci vláken. V tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Synchronizované kód oblasti  
 Můžete použít <xref:System.Threading.Monitor> třídu nebo – klíčové slovo kompilátoru, aby synchronizoval bloky kódu, instanci metody a statické metody. Neexistuje žádná podpora pro synchronizované statických polí.  
  
 Visual Basic a C# podpora značení bloky kódu s použitím klíčového slova konkrétní jazyk, `lock` příkaz v jazyce C# nebo `SyncLock` příkaz v jazyce Visual Basic. Pokud kód je provedený vlákno, je proveden pokus o získat zámek. Pokud již byla získal zámek jiné vlákno, vlákno bloky, dokud nebude k dispozici zámek. Při ukončení synchronizované blok kódu vlákno zámek vydání, bez ohledu na to, jak vlákno ukončí bloku.  
  
> [!NOTE]
>  `lock` a `SyncLock` příkazy jsou implementované pomocí <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, další metody <xref:System.Threading.Monitor> lze použít ve spojení s nimi do oblasti synchronizované.  
  
 Můžete také uspořádání metodu s **MethodImplAttribute** a **MethodImplOptions.Synchronized**, který má stejný účinek jako použití **monitorování** nebo jeden z kompilátoru klíčová slova se uzamknout celého obsahu metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> slouží k přerušení vlákno blokování operace, jako je například čekání na přístup do synchronizované oblasti kódu mimo. **Thread.Interrupt** slouží také k přerušení vláken mimo operací, jako je <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Zamknout typ – to znamená, `typeof(MyType)` v jazyce C#, `GetType(MyType)` v jazyce Visual Basic nebo `MyType::typeid` v jazyce C++ – Pokud chcete chránit `static` metody (`Shared` metody v jazyce Visual Basic). Místo toho použijte objekt privátní statické. Podobně, nepoužívejte `this` v jazyce C# (`Me` v jazyce Visual Basic) zámku metod, které. Místo toho použijte soukromý objekt. Třídy nebo instance může být uzamčen kódu než vlastní, potenciálně způsobuje zablokování nebo problémy s výkonem.  
  
### <a name="compiler-support"></a>Podpora kompilátoru  
 Visual Basic a C# podpora klíčové slovo jazyka, který používá <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> zamknout objekt. Podporuje jazyka Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) příkaz; C# podporuje [zámku](~/docs/csharp/language-reference/keywords/lock-statement.md) příkaz.  
  
 V obou případech, pokud je vyvolána výjimka v kódu blok zámek získaný pomocí **zámku** nebo **SyncLock** vydání automaticky. Emitování kompilátory jazyka C# a Visual Basic **zkuste**/**nakonec** blokovat s **Monitor.Enter** na začátku try, a **Monitor.Exit**  v **nakonec** bloku. Pokud je vyvolána výjimka uvnitř **zámku** nebo **SyncLock –** bloku **nakonec** spustí obslužnou rutinu umožňují práci žádné čištění.  
  
## <a name="synchronized-context"></a>Synchronizované kontextu  
 Můžete použít **SynchronizationAttribute** na žádném **ContextBoundObject** synchronizovat všechny instance metody a pole. Všechny objekty ve stejné doméně kontextu sdílet stejnou zámek. Více vláken je povolen přístup metody a pole, ale v jednom okamžiku je povoleno pouze jedno vlákno.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [Příkaz SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md)
