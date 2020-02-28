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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159387"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizace dat pro Multithreading

Pokud více vláken může volat vlastnosti a metody jednoho objektu, je důležité, aby tato volání byla synchronizovaná. Jinak může jedno vlákno přerušit činnost jiného vlákna a objekt může být ponechán v neplatném stavu. Třída, jejíž členové jsou chráněni před těmito přerušeními, se nazývají bezpečné pro přístup z více vláken.  
  
.NET poskytuje několik strategií pro synchronizaci přístupu k instanci a statickým členům:  
  
- Synchronizované oblasti kódu. Můžete použít třídu <xref:System.Threading.Monitor> nebo podporu kompilátoru pro tuto třídu k synchronizaci pouze bloku kódu, který ji potřebuje, a zlepšení výkonu.  
  
- Ruční synchronizace. Můžete použít synchronizační objekty poskytované knihovnou tříd .NET. Viz [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md), které obsahují diskuzi o <xref:System.Threading.Monitor> třídy.  
  
- Synchronizované kontexty. Pro aplikace .NET Framework a Xamarin můžete pomocí <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> povolit jednoduchou automatickou synchronizaci objektů <xref:System.ContextBoundObject>.  
  
- Třídy kolekce v oboru názvů <xref:System.Collections.Concurrent?displayProperty=nameWithType>. Tyto třídy poskytují předdefinované synchronizované operace přidání a odebrání. Další informace najdete v tématu [kolekce bezpečné](../../../docs/standard/collections/thread-safe/index.md)pro přístup z více vláken.  
  
 Modul CLR (Common Language Runtime) poskytuje model vláken, ve kterém třídy spadají do řady kategorií, které mohou být synchronizovány různými způsoby v závislosti na požadavcích. Následující tabulka uvádí, která podpora synchronizace je k dispozici pro pole a metody s danou kategorií synchronizace.  
  
|Kategorie|Globální pole|Statická pole|Statické metody|Pole instance|Metody instance|Konkrétní bloky kódu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Žádná synchronizace|Ne|Ne|Ne|Ne|Ne|Ne|  
|Synchronizovaný kontext|Ne|Ne|Ne|Ano|Ano|Ne|  
|Synchronizované oblasti kódu|Ne|Ne|Pouze v případě označení|Ne|Pouze v případě označení|Pouze v případě označení|  
|Ruční synchronizace|Ručně|Ručně|Ručně|Ručně|Ručně|Ručně|  
  
## <a name="no-synchronization"></a>Žádná synchronizace  
 Toto je výchozí nastavení pro objekty. Jakékoli vlákno může kdykoli přistupovat k libovolné metodě nebo poli. Přístup k těmto objektům má pouze jedno vlákno v čase.  
  
## <a name="manual-synchronization"></a>Ruční synchronizace  
 Knihovna tříd .NET poskytuje řadu tříd pro synchronizaci vláken. Viz [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Synchronizované oblasti kódu  
 Můžete použít třídu <xref:System.Threading.Monitor> nebo klíčové slovo kompilátoru pro synchronizaci bloků kódu, metody instance a statických metod. U synchronizovaných statických polí není podporována žádná podpora.  
  
 Visual Basic a C# podporují označení bloků kódu pomocí konkrétního klíčového slova jazyka, příkazu `lock` v C# nebo v příkazu `SyncLock` v Visual Basic. Když je kód spuštěn vláknem, je proveden pokus o získání zámku. Pokud zámek již byl získán jiným vláknem, vlákno zablokuje, dokud zámek nebude k dispozici. Když vlákno ukončí synchronizovaný blok kódu, je zámek uvolněn bez ohledu na to, jak vlákno ukončí blok.  
  
> [!NOTE]
> Příkazy `lock` a `SyncLock` jsou implementovány pomocí <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, takže lze použít jiné metody <xref:System.Threading.Monitor> ve spojení s nimi v rámci synchronizované oblasti.  
  
 Metodu můžete také vyřadit pomocí <xref:System.Runtime.CompilerServices.MethodImplAttribute> s hodnotou <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>, která má stejný účinek jako použití <xref:System.Threading.Monitor> nebo jedno z klíčových slov kompilátoru pro uzamknutí celého těla metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> lze použít k přerušení vlákna z blokujících operací, jako je například čekání na přístup k synchronizované oblasti kódu. **Vlákno. Interrupt** slouží také k přerušení podprocesů mimo operace, jako je <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Nezamkněte typ – to znamená, `typeof(MyType)` v C#, `GetType(MyType)` v Visual Basic nebo `MyType::typeid` v C++ , aby se chránily `static` metody (`Shared` metody v Visual Basic). Místo toho použijte privátní statický objekt. Podobně nepoužívejte `this` v C# (`Me` v Visual Basic) k uzamknutí metod instancí. Místo toho použijte privátní objekt. Třída nebo instance může být uzamčena jiným kódem než vaší vlastní, což může způsobit zablokování nebo problémy s výkonem.  
  
### <a name="compiler-support"></a>Podpora kompilátoru  
 Visual Basic a C# podporují klíčové slovo jazyka, které používá <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> k uzamknutí objektu. Visual Basic podporuje příkaz [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ; C# podporuje příkaz [Lock](../../csharp/language-reference/keywords/lock-statement.md) .  
  
 V obou případech, pokud je vyvolána výjimka v bloku kódu, zámek získaný **zámkem** nebo **SyncLock** je automaticky uvolněn. Kompilátory C# a Visual Basic emitují blok **Try**/**finally** s **monitorováním. Zadejte** na začátku příkazu try a **Sledujte. Exit** v bloku **finally** . Pokud je vyvolána výjimka uvnitř bloku **Lock** nebo **SyncLock** , spustí se obslužná rutina **finally** , která vám umožní provést jakoukoli čistou práci.  
  
## <a name="synchronized-context"></a>Synchronizovaný kontext  

Pouze v aplikacích .NET Framework a Xamarin můžete použít <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> na jakémkoli <xref:System.ContextBoundObject> k synchronizaci všech metod instancí a polí. Všechny objekty ve stejné kontextu domény sdílejí stejný zámek. Více vláknům má povolen přístup k metodám a polím, ale v jednom okamžiku je povoleno pouze jedno vlákno.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)
- [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [Příkaz SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
