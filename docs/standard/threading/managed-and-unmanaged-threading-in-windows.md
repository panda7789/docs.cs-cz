---
title: Spravovaná a nespravovaná vlákna ve Windows
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7834df6c987e94e59357c7c60db2627d107bffc3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864547"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Spravovaná a nespravovaná vlákna ve Windows
Správa všech vláken se provádí prostřednictvím <xref:System.Threading.Thread> třídy, včetně vlákna vytvořená modulem common language runtime a ty mimo modul runtime, které zadat spravované prostředí ke spuštění kódu. Modul runtime monitoruje všechna vlákna v procesu, které jste dříve spustili kódu ve spravovaném spouštěcím prostředí. Sledovat ostatní vlákna. Vlákna můžete zadat spravovaném spouštěcím prostředí pomocí zprostředkovatele komunikace s objekty COM (protože modul runtime poskytuje spravované objekty jako objekty modelu COM pro nespravované celý svět), COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) funkce a vyvolání platformy.  
  
 Když nespravovaného vlákna do modulu runtime prostřednictvím, například obálku volatelnou modelem COM systém kontroluje, zda úložiště thread local bylo vlákno k vyhledání interní spravované <xref:System.Threading.Thread> objektu. Pokud ho najde, modul runtime je již vědět toto vlákno. Pokud nelze najít jeden, ale modul runtime vytvoří novou <xref:System.Threading.Thread> objektu a nainstaluje ho v úložišti thread local toto vlákno.  
  
 V dělení na spravovaná vlákna, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> je identifikace stabilní spravované vlákno. Po dobu životnosti vašeho vlákna nebudou kolidovat s hodnotu z jiných vláken, bez ohledu na doménu aplikace, ze kterého můžete získat tuto hodnotu.  
  
> [!NOTE]
>  Spouštění operačního systému **Idvlákna** nemá žádný pevné vztah spravovaná vlákna, protože nespravovaný hostitel může určit vztah mezi spravovanými a nespravovanými vlákna. Sofistikované hostitele můžete konkrétně byste měli použít rozhraní API Fiber naplánování mnoho spravovaná vlákna na stejném vlákně operačního systému, nebo přesunout spravované vlákno mezi vlákny jiný operační systém.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapování z Win32 dělení na vlákna pro dělení na spravovaná vlákna  
 Následující tabulka mapuje dělení na vlákna prvky Win32 k jejich přibližné runtime ekvivalentní. Všimněte si, že toto mapování nepředstavuje identické funkce. Například **TerminateThread** nespustí **nakonec** klauzule nebo uvolněte prostředky a nelze zabránit. Ale <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> spustí váš kód vrácení zpět, uvolní všechny prostředky a může být odepřen pomocí <xref:System.Threading.Thread.ResetAbort%2A>. Nezapomeňte si přečíst dokumentaci těsně před vyvozování předpokladů o funkce.  
  
|V systému Win32|V modulu common language runtime|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinace **vlákna** a <xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Přejít do režimu spánku**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**Funkce WaitForSingleObject** na popisovač podprocesu|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Žádný ekvivalent|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Žádný ekvivalent|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Žádný ekvivalent|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Zavřít **CoInitializeEx** (OLE32. KNIHOVNY DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Spravovaná vlákna a objekty apartment modelu COM  
 Spravované vlákno může být označený k označení, že bude hostovat [s jedním vláknem](/windows/desktop/com/single-threaded-apartments) nebo [s více vlákny](/windows/desktop/com/multithreaded-apartments) objektu apartment. (Další informace o modelu COM dělení na vlákna architektury, najdete v článku [procesy, vlákna a objekty apartment](https://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>, A <xref:System.Threading.Thread.TrySetApartmentState%2A> metody <xref:System.Threading.Thread> třídy vrátit a přiřadit stav apartment vlákna. Pokud stav není nastavený, <xref:System.Threading.Thread.GetApartmentState%2A> vrátí <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Vlastnost lze nastavit pouze v případě, že vlákno je v <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> stavu, lze ji nastavit pouze jednou pro vlákno.  
  
 Pokud stav objektu apartment není nastavena, před spuštěním vlákno, vlákno je inicializován jako s více vlákny typu apartment (MTA). Vlákno finalizační metody a dokud všechna vlákna, které řídí <xref:System.Threading.ThreadPool> jsou MTA.  
  
> [!IMPORTANT]
>  Pro spuštění kódu aplikace, je jediný způsob, jak řídit stav objektu apartment použít <xref:System.MTAThreadAttribute> nebo <xref:System.STAThreadAttribute> položku bodu postup. V rozhraní .NET Framework 1.0 a 1.1 <xref:System.Threading.Thread.ApartmentState%2A> vlastnost lze nastavit jako první řádek kódu. To není povolené v rozhraní .NET Framework 2.0.  
  
 Spravované objekty, které jsou vystaveny rozhraní COM se chovají, jako by se měl agregují volným zařazováním vláken. Jinými slovy že lze volat z jakékoli objektu apartment modelu COM způsobem volných vláken. Pouze spravované objekty, které nejsou tímto způsobem chovat volných vláken jsou tyto objekty, které jsou odvozeny z <xref:System.EnterpriseServices.ServicedComponent> nebo <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 Ve spravovaném světě, neexistuje žádná podpora pro <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> Pokud nepoužíváte spravované instance vázané na kontext a kontexty. Pokud používáte podnikové služby, pak objekt musí být odvozen od <xref:System.EnterpriseServices.ServicedComponent> (což je samotný odvozen z <xref:System.ContextBoundObject>).  
  
 Když spravovaný kód volá navýšení kapacity pro objekty modelu COM, vždy následuje COM pravidla. Jinými slovy volá prostřednictvím proxy modelu COM typu apartment a obálky kontext modelu COM + 1.0 určený OLE32.  
  
## <a name="blocking-issues"></a>Problémy s blokováním  
 Pokud vlákno provede nespravovaného volání do operačního systému, který se zablokoval vlákna v nespravovaném kódu, modulu runtime nebude převzít kontrolu nad pro <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. V případě třídy <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, modul runtime označí vlákno pro **přerušit** a provede kontrolu, když ho znovu přejde do spravovaného kódu. Je vhodné k použití spravované blokování namísto nespravovaného blokování. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>, a tak dále všechny interaktivní <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Navíc pokud vaše vlákno je v jednovláknovém objektu apartment, všechny tyto spravované blokující operace bude správně pump zprávy v vašeho objektu apartment zatímco vaše vlákno blokované.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
- <xref:System.Threading.ThreadState>  
- <xref:System.EnterpriseServices.ServicedComponent>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.Monitor>
