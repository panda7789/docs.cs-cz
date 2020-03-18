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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127546"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Spravované a nespravované podprocesy v systému Windows

Správa všech vláken se provádí <xref:System.Threading.Thread> prostřednictvím třídy, včetně podprocesů vytvořených běžným jazykem runtime a těch vytvořených mimo runtime, které vstupují do spravovaného prostředí ke spuštění kódu. Runtime monitoruje všechna vlákna v jeho procesu, které někdy spouštěné kód v rámci prostředí spravovaného spuštění. Nesleduje žádná jiná vlákna. Vlákna můžete zadat prostředí spravovaného spuštění prostřednictvím interop modelu COM (protože runtime zveřejňuje spravované objekty jako objekty COM do nespravovaného světa), funkce COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) a vyvolání platformy.  
  
 Když nespravované vlákno zadá za běhu prostřednictvím, například com volatelné obálky, systém zkontroluje místní úložiště <xref:System.Threading.Thread> vlákna tohoto vlákna hledat vnitřní spravovaný objekt. Pokud je nalezen, runtime je již vědom tohoto vlákna. Pokud jej nelze najít, ale za běhu <xref:System.Threading.Thread> vytvoří nový objekt a nainstaluje jej do místního úložiště podprocesu tohoto vlákna.  
  
 Ve spravovaném <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> podprocesu je stabilní identifikace spravovaného podprocesu. Po dobu životnosti podprocesu nebude kolidovat s hodnotou z jiného vlákna, bez ohledu na doménu aplikace, ze které získáte tuto hodnotu.  
  
> [!NOTE]
> Operační systém **ThreadId** nemá žádný pevný vztah ke spravovanému vláknu, protože nespravovaný hostitel může řídit vztah mezi spravovanými a nespravovanými vlákny. Konkrétně sofistikovaný hostitel může použít rozhraní FIBER API k naplánování mnoha spravovaných vláken proti stejnému vláknu operačního systému nebo k přesunutí spravovaného vlákna mezi různými vlákny operačního systému.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapování z vláken Win32 na spravované podprocesy

 Následující tabulka mapuje prvky vláken Win32 na jejich přibližný ekvivalent běhu. Všimněte si, že toto mapování nepředstavuje identické funkce. Například **TerminateThread** neprovede **finally** klauzule nebo uvolnit prostředky a nelze zabránit. Však <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> provede všechny vaše vrácení kódu, uvolní všechny prostředky a <xref:System.Threading.Thread.ResetAbort%2A>může být odepřen pomocí . Ujistěte se, že si pozorně přečíst dokumentaci před provedením předpoklady o funkčnosti.  
  
|V Win32|V běžném jazykovém běhu|  
|--------------|------------------------------------|  
|**Vytvořit vlákno**|Kombinace **závitu** a<xref:System.Threading.ThreadStart>|  
|**Ukončit vlákno**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**Pozastavit vlákno**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**Pokračovat v vlákně**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Režim spánku**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** na popisovači vlákna|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**Ukončit vlákno**|Žádný ekvivalent|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**Nastavit prioritu vlákna**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Žádný ekvivalent|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Žádný ekvivalent|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|V blízkosti **CoInitializeEx** (OLE32. DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Spravovaná vlákna a komoby COM

Spravované vlákno může být označeno jako označení, že bude hostitelem apartment [s jedním podprocesem](/windows/desktop/com/single-threaded-apartments) nebo [s více vlákny.](/windows/desktop/com/multithreaded-apartments) (Další informace o architektuře vláken COM naleznete v [tématu Procesy, vlákna a byty](/windows/desktop/com/processes--threads--and-apartments).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>a <xref:System.Threading.Thread.TrySetApartmentState%2A> metody <xref:System.Threading.Thread> třídy vrátit a přiřadit stav apartment podprocesu. Pokud stav nebyl nastaven, <xref:System.Threading.Thread.GetApartmentState%2A> <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>vrátí .  
  
 Vlastnost lze nastavit pouze v případě, <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> že vlákno je ve stavu; lze nastavit pouze jednou pro vlákno.  
  
 Pokud stav apartment není nastaven před spuštěním vlákna, vlákno je inicializováno jako vícevláknový byt (MTA). Finalizační podproces a všechna <xref:System.Threading.ThreadPool> vlákna řízená jsou MTA.  
  
> [!IMPORTANT]
> Pro spouštěcí kód aplikace je jediným způsobem, jak <xref:System.MTAThreadAttribute> řídit <xref:System.STAThreadAttribute> stav apartment, použít proceduru nebo do vstupního bodu. V rozhraní .NET Framework 1.0 a <xref:System.Threading.Thread.ApartmentState%2A> 1.1 lze vlastnost nastavit jako první řádek kódu. To není povoleno v rozhraní .NET Framework 2.0.  
  
 Spravované objekty, které jsou vystaveny com chovat, jako kdyby agregované zařazovací hostoru s volným vláknem. Jinými slovy, mohou být volány z libovolného bytu COM způsobem s volným závitem. Pouze spravované objekty, které nevykazují toto chování s <xref:System.EnterpriseServices.ServicedComponent> volným závitem jsou objekty, které jsou odvozeny od nebo <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 Ve spravovaném světě neexistuje žádná <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> podpora pro pokud používáte kontexty a kontextové spravované instance. Pokud používáte služby Enterprise Services, <xref:System.EnterpriseServices.ServicedComponent> musí váš objekt být <xref:System.ContextBoundObject>odvozen z (který je sám odvozen z).  
  
 Při volání spravovaného kódu na objekty MODELU COM vždy dodržuje pravidla modelu COM. Jinými slovy volá prostřednictvím proxy komanda a obálky kontextu COM + 1.0 podle OLE32.  
  
## <a name="blocking-issues"></a>Blokování problémů  

Pokud vlákno provede nespravované volání do operačního systému, který zablokoval vlákno v nespravovaném <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> kódu, runtime nebude převzít kontrolu nad ním pro nebo <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. V případě <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, runtime označí vlákno pro **Abort** a převezme kontrolu nad ním, když znovu zadá spravovaný kód. Je vhodnější použít spravované blokování spíše než nespravované blokování. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>, , , a <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> tak <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>dále, jsou všechny citlivé na a na . Také pokud vaše vlákno je v bytě s jedním podprocesem, všechny tyto operace spravované blokování bude správně pumpovat zprávy ve vašem bytě, zatímco vaše vlákno je blokován.  

## <a name="threads-and-fibers"></a>Vlákna a vlákna

Model podprocesů .NET nepodporuje [vlákna](/windows/desktop/procthread/fibers). Neměli byste volat do žádné nespravované funkce, která je implementována pomocí vláken. Tato volání může mít za následek selhání běhu .NET.

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
