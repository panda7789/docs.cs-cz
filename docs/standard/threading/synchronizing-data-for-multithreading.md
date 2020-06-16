---
title: Synchronizace dat pro vícevláknové zpracování
description: Naučte se synchronizovat data pro multithreading v .NET. Výběr strategií, například synchronizovaných oblastí kódu, ruční synchronizace nebo synchronizovaných kontextů.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
ms.openlocfilehash: 4d528c54816961caa251ce054abf2c6cf07e9d01
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769103"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizace dat pro Multithreading

Pokud více vláken může volat vlastnosti a metody jednoho objektu, je důležité, aby tato volání byla synchronizovaná. Jinak může jedno vlákno přerušit činnost jiného vlákna a objekt může být ponechán v neplatném stavu. Třída, jejíž členové jsou chráněni před těmito přerušeními, se nazývají bezpečné pro přístup z více vláken.  
  
.NET poskytuje několik strategií pro synchronizaci přístupu k instanci a statickým členům:  
  
- Synchronizované oblasti kódu. Můžete použít <xref:System.Threading.Monitor> podporu třídy nebo kompilátoru pro tuto třídu k synchronizaci pouze bloku kódu, který ji potřebuje, a zlepšení výkonu.  
  
- Ruční synchronizace. Můžete použít synchronizační objekty poskytované knihovnou tříd .NET. Viz [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md), které obsahují diskuzi o <xref:System.Threading.Monitor> třídě.  
  
- Synchronizované kontexty. Pro aplikace .NET Framework a Xamarin můžete použít <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> k povolení jednoduché automatické synchronizace <xref:System.ContextBoundObject> objektů.  
  
- Třídy kolekce v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů. Tyto třídy poskytují předdefinované synchronizované operace přidání a odebrání. Další informace najdete v tématu [kolekce bezpečné](../collections/thread-safe/index.md)pro přístup z více vláken.  
  
 Modul CLR (Common Language Runtime) poskytuje model vláken, ve kterém třídy spadají do řady kategorií, které mohou být synchronizovány různými způsoby v závislosti na požadavcích. Následující tabulka uvádí, která podpora synchronizace je k dispozici pro pole a metody s danou kategorií synchronizace.  
  
|Kategorie|Globální pole|Statická pole|Statické metody|Pole instance|Metody instance|Konkrétní bloky kódu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Žádná synchronizace|Ne|Ne|Ne|Ne|Ne|Ne|  
|Synchronizovaný kontext|Ne|Ne|Ne|Ano|Ano|Ne|  
|Synchronizované oblasti kódu|Ne|Ne|Pouze v případě označení|Ne|Pouze v případě označení|Pouze v případě označení|  
|Ruční synchronizace|Ruční|Ruční|Ruční|Ruční|Ruční|Ruční|  
  
## <a name="no-synchronization"></a>Žádná synchronizace  
 Toto je výchozí nastavení pro objekty. Jakékoli vlákno může kdykoli přistupovat k libovolné metodě nebo poli. Přístup k těmto objektům má pouze jedno vlákno v čase.  
  
## <a name="manual-synchronization"></a>Ruční synchronizace  
 Knihovna tříd .NET poskytuje řadu tříd pro synchronizaci vláken. Viz [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Synchronizované oblasti kódu  
 Můžete použít <xref:System.Threading.Monitor> klíčové slovo class nebo Compiler pro synchronizaci bloků kódu, metody instance a statických metod. U synchronizovaných statických polí není podporována žádná podpora.  
  
 Visual Basic i C# podporují označení bloků kódu pomocí klíčového slova konkrétního jazyka, `lock` příkazu v jazyce C# nebo `SyncLock` příkazu v Visual Basic. Když je kód spuštěn vláknem, je proveden pokus o získání zámku. Pokud zámek již byl získán jiným vláknem, vlákno zablokuje, dokud zámek nebude k dispozici. Když vlákno ukončí synchronizovaný blok kódu, je zámek uvolněn bez ohledu na to, jak vlákno ukončí blok.  
  
> [!NOTE]
> `lock`Příkazy a `SyncLock` jsou implementovány pomocí <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> , takže <xref:System.Threading.Monitor> lze použít jiné metody v kombinaci s nimi v rámci synchronizované oblasti.  
  
 Můžete také vyřadit metodu s <xref:System.Runtime.CompilerServices.MethodImplAttribute> hodnotou <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType> , která má stejný účinek jako použití <xref:System.Threading.Monitor> nebo jedno z klíčových slov kompilátoru pro uzamknutí celého těla metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>dá se použít k přerušení vlákna z blokujících operací, jako je například čekání na přístup k synchronizované oblasti kódu. **Vlákno. Interrupt** slouží také k přerušení podprocesů mimo operace, jako je <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> Nezamkněte typ – to je `typeof(MyType)` v jazyce C#, `GetType(MyType)` v Visual Basic nebo `MyType::typeid` v jazyce C++, aby bylo možné chránit `static` metody ( `Shared` metody v Visual Basic). Místo toho použijte privátní statický objekt. Podobně nepoužívejte `this` v jazyce C# ( `Me` v Visual Basic) k uzamknutí metod instancí. Místo toho použijte privátní objekt. Třída nebo instance může být uzamčena jiným kódem než vaší vlastní, což může způsobit zablokování nebo problémy s výkonem.  
  
### <a name="compiler-support"></a>Podpora kompilátoru  
 Visual Basic i C# podporují klíčové slovo jazyka, které používá <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> k uzamknutí objektu. Visual Basic podporuje příkaz [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ; Jazyk C# podporuje příkaz [Lock](../../csharp/language-reference/keywords/lock-statement.md) .  
  
 V obou případech, pokud je vyvolána výjimka v bloku kódu, zámek získaný **zámkem** nebo **SyncLock** je automaticky uvolněn. Kompilátory jazyka C# a Visual Basic generují blok **Try** / **finally** s **monitorováním. Zadejte** na začátku příkazu try a **Sledujte. Exit** v bloku **finally** . Pokud je vyvolána výjimka uvnitř bloku **Lock** nebo **SyncLock** , spustí se obslužná rutina **finally** , která vám umožní provést jakoukoli čistou práci.  
  
## <a name="synchronized-context"></a>Synchronizovaný kontext  

Pouze v aplikacích .NET Framework a Xamarin můžete <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> <xref:System.ContextBoundObject> k synchronizaci všech metod a polí instance použít příkaz on. Všechny objekty ve stejné kontextu domény sdílejí stejný zámek. Více vláknům má povolen přístup k metodám a polím, ale v jednom okamžiku je povoleno pouze jedno vlákno.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)
- [SyncLock – příkaz](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
