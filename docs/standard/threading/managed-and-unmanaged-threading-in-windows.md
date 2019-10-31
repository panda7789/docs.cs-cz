---
title: Spravovaná a nespravovaná vlákna ve Windows
ms.date: 10/24/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- threading [.NET], managed
- threads and fibers [.NET]
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
ms.openlocfilehash: 6ab0cc7c1ec2f7bbc633ac966dd18ab3ea7a395b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127546"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Spravovaná a nespravovaná vlákna ve Windows

Správa všech vláken se provádí prostřednictvím <xref:System.Threading.Thread> třídy, včetně vláken vytvořených modulem CLR (Common Language Runtime) a vytvořených mimo modul runtime, který do spravovaného prostředí zahájí kód. Modul runtime monitoruje všechna vlákna ve svém procesu, který ve spravovaném prostředí pro spuštění někdy spustil kód. Nesleduje žádné další podprocesy. Vlákna mohou pomocí zprostředkovatele komunikace s objekty COM vstoupit do prostředí spravovaného spuštění (protože modul runtime zveřejňuje spravované objekty jako objekty COM na nespravovaný svět), funkci [DLLGETCLASSOBJECT](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) com a vyvolání platformy.  
  
 Když nespravované vlákno vstoupí do modulu runtime prostřednictvím, například obálka s podporou modelu COM, systém zkontroluje místní úložiště vlákna daného vlákna, aby vyhledal interní spravovaný objekt <xref:System.Threading.Thread>. Pokud je některý z nich nalezen, modul runtime je již o tomto vláknu vědom. Pokud ale nemůže nějaký najít, modul runtime vytvoří nový objekt <xref:System.Threading.Thread> a nainstaluje ho do úložiště místního vlákna tohoto vlákna.  
  
 Ve spravovaném vlákně je <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> stabilním identifikátorem spravovaného vlákna. Po celou dobu životnosti vlákna se nebude kolidovat s hodnotou z žádného jiného vlákna bez ohledu na doménu aplikace, ze které tuto hodnotu získáváte.  
  
> [!NOTE]
> **IDvlákna** operačního systému nemá žádný pevný vztah ke spravovanému vláknu, protože nespravovaný hostitel může řídit vztah mezi spravovanými a nespravovanými vlákny. Konkrétně propracované hostitel může použít rozhraní Fiber API k naplánování mnoha spravovaných vláken proti stejnému vláknu operačního systému nebo k přesunutí spravovaného vlákna mezi různými vlákny operačního systému.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapování z vlákna Win32 do spravovaného vlákna

 Následující tabulka mapuje prvky vláken Win32 na jejich přibližný ekvivalent za běhu. Všimněte si, že toto mapování nepředstavuje stejné funkce. **TerminateThread** například neprovede klauzule **finally** nebo uvolní prostředky a nelze je zabránit. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ale spustí celý kód pro vrácení zpět, vrátí deklarace všech prostředků a dá se pomocí <xref:System.Threading.Thread.ResetAbort%2A>odepřít. Nezapomeňte si před tím, než začnete vytvářet předpoklady o funkcích, pečlivě si přečtěte dokumentaci.  
  
|V systému Win32|V modulu CLR (Common Language Runtime)|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinace **vlákna** a <xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Spat**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** v popisovači vlákna|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread –**|Bez ekvivalentu|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Bez ekvivalentu|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Bez ekvivalentu|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Blízko **funkce CoInitializeEx** (Ole32. DLL|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Spravovaná vlákna a COM Apartment

Spravované vlákno může být označeno k označení toho, že bude hostovat [jeden vlákn](/windows/desktop/com/single-threaded-apartments) [nebo vícevláknový objekt Apartment.](/windows/desktop/com/multithreaded-apartments) (Další informace o architektuře vláken COM naleznete v tématu [procesy, vlákna a objekty Apartment](/windows/desktop/com/processes--threads--and-apartments).) Metody <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>a <xref:System.Threading.Thread.TrySetApartmentState%2A> třídy <xref:System.Threading.Thread> vracejí a přiřazují stav objektu apartment vlákna. Pokud stav nebyl nastaven, <xref:System.Threading.Thread.GetApartmentState%2A> vrátí <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Vlastnost lze nastavit pouze v případě, že je vlákno ve stavu <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType>; dá se pro vlákno nastavit jenom jednou.  
  
 Pokud stav objektu Apartment není nastaven před spuštěním vlákna, vlákno je inicializováno jako vícevláknové prostředí (MTA). Finalizační vlákno a všechna vlákna řízená <xref:System.Threading.ThreadPool> jsou MTA.  
  
> [!IMPORTANT]
> V případě spouštěcího kódu aplikace jediným způsobem, jak řídit stav objektu apartment, je použít <xref:System.MTAThreadAttribute> nebo <xref:System.STAThreadAttribute> na proceduru vstupního bodu. V .NET Framework 1,0 a 1,1 lze vlastnost <xref:System.Threading.Thread.ApartmentState%2A> nastavit jako první řádek kódu. Tato není povolená v .NET Framework 2,0.  
  
 Spravované objekty, které jsou vystaveny modelu COM, se chovají, jako kdyby obsahovaly agregované zařazování vláken s volnými vlákny. Jinými slovy, mohou být volány z libovolného objektu COM v rámci libovolného typu s více vlákny. Jedinými spravovanými objekty, které se nezobrazují toto chování s volnou vláknem, jsou objekty, které jsou odvozeny z <xref:System.EnterpriseServices.ServicedComponent> nebo <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 Ve spravovaném světě není dostupná žádná podpora pro <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>, pokud nepoužíváte kontexty a spravované instance závislé na kontextu. Pokud používáte služby Enterprise Services, musí být objekt odvozen od <xref:System.EnterpriseServices.ServicedComponent> (která je sama o sobě odvozena z <xref:System.ContextBoundObject>).  
  
 Pokud spravovaný kód volá objekty modelu COM, vždy se řídí pravidly modelu COM. Jinými slovy volá proxy objekty COM Apartment a obálky kontextu COM+ 1,0, jak jsou vyvolány pomocí OLE32.  
  
## <a name="blocking-issues"></a>Blokování problémů  

Pokud vlákno provede nespravované volání do operačního systému, který zablokovalo vlákno v nespravovaném kódu, modul runtime nevezme kontrolu nad <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. V případě <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>modul runtime označí vlákno k **přerušení** a při opětovném vložení spravovaného kódu ho převezme pod kontrolou. Doporučujeme místo nespravovaného blokování použít spravované blokování. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>a tak dále, reagují na <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Pokud je vlákno v izolovaném vláknu, všechny tyto spravované operace blokování budou správně pumpovat zprávy ve vašem vlákně, zatímco vaše vlákno je blokováno.  

## <a name="threads-and-fibers"></a>Vlákna a vlákna

Model vláken .NET nepodporuje [vlákna](/windows/desktop/procthread/fibers). Neměli byste volat do žádné nespravované funkce, která je implementována pomocí vláken. Taková volání můžou způsobit zhroucení prostředí .NET Runtime.

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
