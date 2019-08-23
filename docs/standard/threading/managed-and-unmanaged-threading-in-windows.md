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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da32d514b19424487cebc1d113388cfa9a2dbdf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913231"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Spravovaná a nespravovaná vlákna ve Windows

Správa všech vláken je prováděna prostřednictvím <xref:System.Threading.Thread> třídy, včetně vláken vytvořených modulem CLR (Common Language Runtime) a vytvořených mimo modul runtime, který do spravovaného prostředí zadává kód. Modul runtime monitoruje všechna vlákna ve svém procesu, který ve spravovaném prostředí pro spuštění někdy spustil kód. Nesleduje žádné další podprocesy. Vlákna mohou pomocí zprostředkovatele komunikace s objekty COM vstoupit do prostředí spravovaného spuštění (protože modul runtime zveřejňuje spravované objekty jako objekty COM na nespravovaný svět), funkci [DLLGETCLASSOBJECT](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) com a vyvolání platformy.  
  
 Když nespravované vlákno vstoupí do modulu runtime prostřednictvím, například obálka s podporou modelu COM, systém zkontroluje místní úložiště vlákna daného vlákna, aby hledal interní spravovaný <xref:System.Threading.Thread> objekt. Pokud je některý z nich nalezen, modul runtime je již o tomto vláknu vědom. Pokud ale nemůže nějaký najít, modul runtime vytvoří nový <xref:System.Threading.Thread> objekt a nainstaluje ho do úložiště místního vlákna tohoto vlákna.  
  
 Ve spravovaném vlákně <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> je stabilním identifikátorem spravovaného vlákna. Po celou dobu životnosti vlákna se nebude kolidovat s hodnotou z žádného jiného vlákna bez ohledu na doménu aplikace, ze které tuto hodnotu získáváte.  
  
> [!NOTE]
> **IDvlákna** operačního systému nemá žádný pevný vztah ke spravovanému vláknu, protože nespravovaný hostitel může řídit vztah mezi spravovanými a nespravovanými vlákny. Konkrétně propracované hostitel může použít rozhraní Fiber API k naplánování mnoha spravovaných vláken proti stejnému vláknu operačního systému nebo k přesunutí spravovaného vlákna mezi různými vlákny operačního systému.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapování z vlákna Win32 do spravovaného vlákna

 Následující tabulka mapuje prvky vláken Win32 na jejich přibližný ekvivalent za běhu. Všimněte si, že toto mapování nepředstavuje stejné funkce. **TerminateThread** například neprovede klauzule **finally** nebo uvolní prostředky a nelze je zabránit. Spustí se ale veškerý váš kód vrácení zpět, uvolní všechny prostředky a může být odepřen pomocí <xref:System.Threading.Thread.ResetAbort%2A>. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Nezapomeňte si před tím, než začnete vytvářet předpoklady o funkcích, pečlivě si přečtěte dokumentaci.  
  
|V systému Win32|V modulu CLR (Common Language Runtime)|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinace **vlákna** a<xref:System.Threading.ThreadStart>|  
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

Spravované vlákno může být označeno k označení toho, že bude hostovat [jeden vlákn](/windows/desktop/com/single-threaded-apartments) nebo vícevláknový [](/windows/desktop/com/multithreaded-apartments) objekt Apartment. (Další informace o architektuře vláken COM naleznete v tématu [procesy, vlákna a objekty Apartment](/windows/desktop/com/processes--threads--and-apartments).) Metody <xref:System.Threading.Thread.GetApartmentState%2A> ,<xref:System.Threading.Thread.SetApartmentState%2A> a<xref:System.Threading.Thread.TrySetApartmentState%2A>třídyvrací a přiřazují stav objektu apartment vlákna. <xref:System.Threading.Thread> Pokud stav nebyl nastaven, <xref:System.Threading.Thread.GetApartmentState%2A> vrátí. <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>  
  
 Vlastnost lze nastavit pouze v případě, že vlákno je ve <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> stavu, lze pro vlákno nastavit pouze jednou.  
  
 Pokud stav objektu Apartment není nastaven před spuštěním vlákna, vlákno je inicializováno jako vícevláknové prostředí (MTA). Finalizační vlákno a všechna vlákna řízená nástrojem <xref:System.Threading.ThreadPool> jsou typu MTA.  
  
> [!IMPORTANT]
> V případě spouštěcího kódu aplikace jediným způsobem, jak řídit stav objektu apartment, je <xref:System.MTAThreadAttribute> použít <xref:System.STAThreadAttribute> nebo na proceduru vstupního bodu. V .NET Framework 1,0 a 1,1 <xref:System.Threading.Thread.ApartmentState%2A> lze vlastnost nastavit jako první řádek kódu. Tato není povolená v .NET Framework 2,0.  
  
 Spravované objekty, které jsou vystaveny modelu COM, se chovají, jako kdyby obsahovaly agregované zařazování vláken s volnými vlákny. Jinými slovy, mohou být volány z libovolného objektu COM v rámci libovolného typu s více vlákny. Jediné spravované objekty, které se nezobrazují toto chování s volnou vláknem, jsou objekty, <xref:System.EnterpriseServices.ServicedComponent> které <xref:System.Runtime.InteropServices.StandardOleMarshalObject>jsou odvozeny z nebo.  
  
 Ve spravovaném světě není podporována podpora pro, pokud nepoužíváte kontexty a spravované instance závislé na <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> kontextu. Pokud používáte služby Enterprise Services, musí být objekt odvozen od <xref:System.EnterpriseServices.ServicedComponent> (který je sám odvozen z <xref:System.ContextBoundObject>).  
  
 Pokud spravovaný kód volá objekty modelu COM, vždy se řídí pravidly modelu COM. Jinými slovy volá proxy objekty COM Apartment a obálky kontextu COM+ 1,0, jak jsou vyvolány pomocí OLE32.  
  
## <a name="blocking-issues"></a>Blokování problémů  

Pokud vlákno vytvoří nespravované volání do operačního systému, který zablokoval vlákno v nespravovaném kódu, modul runtime je nevezme pod kontrolou pro <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nebo. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> V případě <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>je modul runtime označen vláknem pro **přerušení** a při opětovném vložení spravovaného kódu ho převezme pod kontrolou. Doporučujeme místo nespravovaného blokování použít spravované blokování. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ,<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>,, ,<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, atak<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> je vše reagovat na a .<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> Pokud je vlákno v izolovaném vláknu, všechny tyto spravované operace blokování budou správně pumpovat zprávy ve vašem vlákně, zatímco vaše vlákno je blokováno.  

## <a name="threads-and-fibers"></a>Vlákna a vlákna

Model vláken .NET nepodporuje [vlákna](/windows/desktop/procthread/fibers). Neměli byste volat do žádné nespravované funkce, která je implementována pomocí vláken. Taková volání můžou způsobit zhroucení prostředí .NET Runtime.

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
