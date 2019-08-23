---
title: Synchronizace dat pro vícevláknové zpracování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc8381f8059e37c6c520c2402289124a506188e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968416"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizace dat pro Multithreading

Pokud více vláken může volat vlastnosti a metody jednoho objektu, je důležité, aby tato volání byla synchronizovaná. Jinak může jedno vlákno přerušit činnost jiného vlákna a objekt může být ponechán v neplatném stavu. Třída, jejíž členové jsou chráněni před těmito přerušeními, se nazývají bezpečné pro přístup z více vláken.  
  
.NET poskytuje několik strategií pro synchronizaci přístupu k instanci a statickým členům:  
  
- Synchronizované oblasti kódu. Můžete použít <xref:System.Threading.Monitor> podporu třídy nebo kompilátoru pro tuto třídu k synchronizaci pouze bloku kódu, který ji potřebuje, a zlepšení výkonu.  
  
- Ruční synchronizace. Můžete použít synchronizační objekty poskytované knihovnou tříd .NET. Viz [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md), které obsahují diskuzi o <xref:System.Threading.Monitor> třídě.  
  
- Synchronizované kontexty. Pro aplikace .NET Framework a Xamarin můžete použít <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> k povolení jednoduché automatické <xref:System.ContextBoundObject> synchronizace objektů.  
  
- Třídy kolekce v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů. Tyto třídy poskytují předdefinované synchronizované operace přidání a odebrání. Další informace najdete v tématu [kolekce bezpečné](../../../docs/standard/collections/thread-safe/index.md)pro přístup z více vláken.  
  
 Modul CLR (Common Language Runtime) poskytuje model vláken, ve kterém třídy spadají do řady kategorií, které mohou být synchronizovány různými způsoby v závislosti na požadavcích. Následující tabulka uvádí, která podpora synchronizace je k dispozici pro pole a metody s danou kategorií synchronizace.  
  
|Kategorie|Globální pole|Statická pole|Statické metody|Pole instance|Metody instance|Konkrétní bloky kódu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Žádná synchronizace|Ne|Ne|Ne|Ne|Ne|Ne|  
|Synchronizovaný kontext|Ne|Ne|Ne|Ano|Ano|Ne|  
|Synchronizované oblasti kódu|Ne|Ne|Pouze v případě označení|Ne|Pouze v případě označení|Pouze v případě označení|  
|Ruční synchronizace|Zásah|Zásah|Zásah|Zásah|Zásah|Zásah|  
  
## <a name="no-synchronization"></a>Žádná synchronizace  
 Toto je výchozí nastavení pro objekty. Jakékoli vlákno může kdykoli přistupovat k libovolné metodě nebo poli. Přístup k těmto objektům má pouze jedno vlákno v čase.  
  
## <a name="manual-synchronization"></a>Ruční synchronizace  
 Knihovna tříd .NET poskytuje řadu tříd pro synchronizaci vláken. Viz [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Synchronizované oblasti kódu  
 Můžete použít <xref:System.Threading.Monitor> klíčové slovo class nebo Compiler pro synchronizaci bloků kódu, metody instance a statických metod. U synchronizovaných statických polí není podporována žádná podpora.  
  
 Visual Basic a C# podporují označení bloků kódu pomocí konkrétního klíčového slova jazyka, `lock` C# `SyncLock` příkazu v nebo příkazu v Visual Basic. Když je kód spuštěn vláknem, je proveden pokus o získání zámku. Pokud zámek již byl získán jiným vláknem, vlákno zablokuje, dokud zámek nebude k dispozici. Když vlákno ukončí synchronizovaný blok kódu, je zámek uvolněn bez ohledu na to, jak vlákno ukončí blok.  
  
> [!NOTE]
> <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor> Příkazy a jsou`SyncLock` implementovány pomocí a, takže lze použít jiné metody v kombinaci s nimi v rámci synchronizované oblasti. `lock`  
  
 Můžete také vyřadit metodu <xref:System.Runtime.CompilerServices.MethodImplAttribute> s <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>hodnotou, která má stejný účinek jako použití <xref:System.Threading.Monitor> nebo jedno z klíčových slov kompilátoru pro uzamknutí celého těla metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>dá se použít k přerušení vlákna z blokujících operací, jako je například čekání na přístup k synchronizované oblasti kódu. **Vlákno. Interrupt** slouží také k přerušení podprocesů mimo operace, <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>jako je.  
  
> [!IMPORTANT]
> Nezamkněte `typeof(MyType)` typ – to znamená v C#, `GetType(MyType)` v Visual Basic nebo `MyType::typeid` v C++ , aby se chránily `static` metody (`Shared` metody v Visual Basic). Místo toho použijte privátní statický objekt. Podobně nepoužívejte `this` v C# (`Me` v Visual Basic) k uzamknutí metod instancí. Místo toho použijte privátní objekt. Třída nebo instance může být uzamčena jiným kódem než vaší vlastní, což může způsobit zablokování nebo problémy s výkonem.  
  
### <a name="compiler-support"></a>Podpora kompilátoru  
 Visual Basic a C# podporují klíčové slovo jazyka, které používá <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> k uzamknutí objektu. Visual Basic podporuje příkaz [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ; C# podporuje příkaz [Lock](../../csharp/language-reference/keywords/lock-statement.md) .  
  
 V obou případech, pokud je vyvolána výjimka v bloku kódu, zámek získaný zámkem nebo **SyncLock** je automaticky uvolněn. Kompilátory C# a Visual Basic generují blok **Try**/**finally** s monitorováním **. Zadejte** na začátku příkazu try a **Sledujte. Exit** v bloku **finally** . Pokud je vyvolána výjimka uvnitř bloku **Lock** nebo **SyncLock** , spustí se obslužná rutina **finally** , která vám umožní provést jakoukoli čistou práci.  
  
## <a name="synchronized-context"></a>Synchronizovaný kontext  
 
Pouze v aplikacích .NET Framework a Xamarin můžete <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> <xref:System.ContextBoundObject> k synchronizaci všech metod a polí instance použít příkaz on. Všechny objekty ve stejné kontextu domény sdílejí stejný zámek. Více vláknům má povolen přístup k metodám a polím, ale v jednom okamžiku je povoleno pouze jedno vlákno.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)
- [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [Příkaz SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
