---
title: "Spravovaná a nespravovaná vlákna ve Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ce17ef15a5b582a9df0f16d7e0ac82df626579d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Spravovaná a nespravovaná vlákna ve Windows
Správa všechna vlákna se provádí prostřednictvím <xref:System.Threading.Thread> třídy, včetně vláken vytvořený modul common language runtime a ty mimo modul runtime, který zadejte spravované prostředí ke spouštění kódu. Modul runtime monitoruje všechna vlákna zpracování, které někdy provedli kódu v rámci spravovaného spouštění prostředí. Žádné další podprocesy sledovat. Vláken můžete zadat spravovaného spouštění prostředí pomocí zprostředkovatele komunikace s objekty COM (protože modul runtime zpřístupní spravované objekty jako objekty COM nespravované World), modelu COM [DllGetClassObject](https://msdn.microsoft.com/library/ms680760.aspx) funkce a vyvolání platformy.  
  
 Nespravovaná vlákna zadá runtime prostřednictvím, například obálka volatelná aplikacemi COM, systém kontroluje, zda místní úložiště daném vláknu se podívat interní spravované <xref:System.Threading.Thread> objektu. Pokud je takový nalezen, je již vědět tohoto podprocesu modulu runtime. Pokud nelze najít jednu, vytvoří novou však modulu runtime <xref:System.Threading.Thread> objektu a nainstaluje v místním úložišti tento přístup z více vláken.  
  
 V dělení na spravovaná vlákna, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> je identifikace stabilní spravovaných vláken. Po dobu jeho existence váš přístup z více vláken nebude kolidují s hodnotou z jiné vlákno, bez ohledu na doménu aplikace, ze kterého můžete získat tuto hodnotu.  
  
> [!NOTE]
>  Spouštění operačního systému **ID podprocesu** nemá žádný pevné vztah k spravované vlákno, protože nespravované hostitele můžete řídit vztah mezi spravovanými a nespravovanými vláken. Konkrétně sofistikované hostitele můžete použít rozhraní API Fiber, naplánovat mnoho spravovaných vláknech na stejném vlákně, v operačním systému nebo přesunout spravované vlákno mezi vláken jiného operačního systému.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapování z vlákna Win32 pro dělení na spravovaná vlákna  
 Následující tabulka mapuje vláken elementy Win32 jejich přibližnou runtime ekvivalentní. Všimněte si, že toto mapování nepředstavuje identické funkce. Například **TerminateThread** nepracuje **nakonec** klauzule nebo uvolní prostředky a nelze zabránit. Ale <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> provede všech vašich kódech vrácení zpět, získá všechny prostředky a může být odepřen pomocí <xref:System.Threading.Thread.ResetAbort%2A>. Nezapomeňte si přečíst v dokumentaci těsně před odhad funkce.  
  
|V systému Win32|V modulu common language runtime|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinace **vláken** a<xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Přejít do režimu spánku**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** na popisovač podprocesu|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Žádný ekvivalent|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Žádný ekvivalent|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Žádný ekvivalent|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Zavřete na **CoInitializeEx** (OLE32. KNIHOVNY DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Spravovaných vláknech a Apartment COM  
 Spravované vlákno, může být označen k označení, že bude hostitelem [jednovláknové](http://msdn.microsoft.com/library/windows/desktop/ms680112.aspx) nebo [vícevláknové](http://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) typu apartment. (Další informace o modelu COM dělení na vlákna architektuře, najdete v části [procesy, vláken a Apartment](http://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>, A <xref:System.Threading.Thread.TrySetApartmentState%2A> metody <xref:System.Threading.Thread> třídy vrátit a přiřaďte stav objektu apartment vlákna. Pokud stav není nastaven, <xref:System.Threading.Thread.GetApartmentState%2A> vrátí <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Vlastnost lze nastavit pouze v případě, že se <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> stavu; ho lze nastavit pouze jednou vlákna.  
  
 Pokud stav objektu apartment není nastavena, před zahájením vlákno, vlákno je inicializován jako více vláken typu apartment (MTA). Vlákno finalizační metodu a všechna vlákna řízené <xref:System.Threading.ThreadPool> jsou modelu MTA.  
  
> [!IMPORTANT]
>  Pro spuštění kódu aplikace, je jediným způsobem, jak řídit stav objektu apartment použít <xref:System.MTAThreadAttribute> nebo <xref:System.STAThreadAttribute> položek bodu postupu. V rozhraní .NET Framework 1.0 a 1.1 <xref:System.Threading.Thread.ApartmentState%2A> vlastnost lze nastavit jako první řádek kódu. To není povoleno v rozhraní .NET Framework 2.0.  
  
 Spravované objekty, které jsou zpřístupněny COM chovat, jako by se měl agregovat volné zařazování vláken. Jinými slovy bylo možné volat z jakékoli COM apartment způsobem podprocesy. Jenom spravované objekty, které nedojde toto chování podprocesy jsou tyto objekty, které jsou odvozeny od <xref:System.EnterpriseServices.ServicedComponent> nebo <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 Ve spravovaném světě, neexistuje žádná podpora pro <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> Pokud nechcete použít kontexty a spravované instance kontextu vazby. Pokud používáte podnikové služby, pak objektu musí být odvozeny od <xref:System.EnterpriseServices.ServicedComponent> (který je sám odvozen z <xref:System.ContextBoundObject>).  
  
 Když spravovaný kód zavolá objekty modelu COM, vždy následuje COM pravidla. Jinými slovy zavolá prostřednictvím proxy apartment COM a kontext obálky COM + 1.0 stanovená OLE32.  
  
## <a name="blocking-issues"></a>Problémy s blokováním  
 Pokud vlákno provede volání nespravovaného do operačního systému, který má blokovaný vlákno v nespravovaném kódu, modul runtime nebude převzít kontrolu nad pro <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. U <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, modul runtime označí vlákno pro **Abort** a provede kontrolu nad ho, když ho znovu vstupuje do spravovaného kódu. Je vhodnější pro použití spravovaných blokování místo nespravované blokování. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>a tak dále jsou všechny reaguje na <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Navíc pokud váš přístup z více vláken ve single-threaded apartment, všechny tyto spravované blokování operace bude správně čerpadla zprávy ve vašem apartment při vaší vlákno je blokované.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
 <xref:System.Threading.ThreadState>  
 <xref:System.EnterpriseServices.ServicedComponent>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Monitor>
