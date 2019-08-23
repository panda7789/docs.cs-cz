---
title: Mutex – třídy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2edf1f06873796bd63fceaca9a4bb99e509589
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910346"
---
# <a name="mutexes"></a>Mutex – třídy
K poskytnutí výhradního <xref:System.Threading.Mutex> přístupu k prostředku můžete použít objekt. Třída používá více systémových prostředků <xref:System.Threading.Monitor> než třída, ale lze ji zařadit napříč hranicemi domény aplikace, lze ji použít s více čekacími procesy a lze ji použít k synchronizaci vláken v různých procesech. <xref:System.Threading.Mutex> Porovnání mechanismů spravované synchronizace najdete v tématu [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Příklady kódu naleznete v referenční dokumentaci pro <xref:System.Threading.Mutex.%23ctor%2A> konstruktory.  
  
## <a name="using-mutexes"></a>Použití mutexů  
 Vlákno volá <xref:System.Threading.WaitHandle.WaitOne%2A> metodu mutex pro vyžádání vlastnictví. Bloky volání, dokud není objekt mutex k dispozici, nebo dokud neuplyne časový interval volitelného časového limitu. Stav mutex je signalizována, pokud není vlastníkem vlákna.  
  
 Vlákno uvolňuje mutex voláním jeho <xref:System.Threading.Mutex.ReleaseMutex%2A> metody. Mutexy mají spřažení vlákna; To znamená, že mutex může být uvolněn pouze vláknem, které je vlastníkem. Pokud vlákno uvolní mutex, který nevlastní, <xref:System.ApplicationException> je vyvolána ve vlákně.  
  
 <xref:System.Threading.WaitHandle> <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle> <xref:System.Threading.Mutex> Vzhledem k tomu, že <xref:System.Threading.WaitHandle.WaitAny%2A> třída je odvozena z, můžete také volat statické metody nebo metody pro vyžádání vlastnictví v kombinaci s jinými obslužnými rutinami čekání. <xref:System.Threading.Mutex>  
  
 Pokud vlákno vlastní a <xref:System.Threading.Mutex>, může toto vlákno určit stejné <xref:System.Threading.Mutex> v opakovaných voláních Wait-Request bez blokování jeho spuštění, ale musí vydávat <xref:System.Threading.Mutex> tolik, kolikrát se má uvolnit vlastnictví.  
  
## <a name="abandoned-mutexes"></a>Opuštěné mutexy  
 Pokud se vlákno ukončí bez uvolnění a <xref:System.Threading.Mutex>, je tento mutex označován jako opuštěno. To často znamená závažnou chybu při programování, protože prostředek, který zámek mutex chrání, může být ponechán v nekonzistentním stavu. V .NET Framework verze 2,0 <xref:System.Threading.AbandonedMutexException> je vyvolána v dalším vlákně, která získá mutex.  
  
> [!NOTE]
> V .NET Framework verzích 1,0 a 1,1 je opuštění <xref:System.Threading.Mutex> nastavené na signálový stav a další čekající vlákno získá vlastnictví. Pokud žádné vlákno nečeká, <xref:System.Threading.Mutex> zůstane ve stavu signalizace. Není vyvolána žádná výjimka.  
  
 V případě mutexu v rámci systému může opuštěný mutex indikovat, že aplikace byla náhle ukončena (například pomocí Správce úloh systému Windows).  
  
## <a name="local-and-system-mutexes"></a>Místní a systémové mutexy  
 Mutexy mají dva typy: místní mutexy a pojmenované mutexy systému. Vytvoříte-li <xref:System.Threading.Mutex> objekt pomocí konstruktoru, který přijímá název, je spojen s objektem operačního systému daného názvu. Pojmenované mutexy systému jsou viditelné v celém operačním systému a lze je použít k synchronizaci aktivit procesů. Můžete vytvořit více <xref:System.Threading.Mutex> objektů, které reprezentují stejný pojmenovaný mutex systému, a můžete <xref:System.Threading.Mutex.OpenExisting%2A> použít metodu k otevření existujícího pojmenovaného mutex systému.  
  
 Místní mutex existuje jenom v rámci vašeho procesu. Dá se použít v jakémkoli vlákně v procesu, který má odkaz na místní <xref:System.Threading.Mutex> objekt. Každý <xref:System.Threading.Mutex> objekt je samostatný místní mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Access Control zabezpečení pro mutexy systému  
 .NET Framework verze 2,0 poskytuje možnost dotazování a nastavení zabezpečení řízení přístupu systému Windows pro pojmenované systémové objekty. Doporučuje se chránit mutexy systému před vytvořením, protože systémové objekty jsou globální a proto je lze uzamknout jiným kódem než vlastním.  
  
 Informace o zabezpečení řízení přístupu pro <xref:System.Security.AccessControl.MutexSecurity> mutexy naleznete v tématech třídy a <xref:System.Security.AccessControl.MutexAccessRule> <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Security.AccessControl.MutexRights> výčet <xref:System.Threading.Mutex> ,, <xref:System.Threading.Mutex.SetAccessControl%2A>a <xref:System.Threading.Mutex.OpenExisting%2A> metody třídy a <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Dělení objektů a funkcí](threading-objects-and-features.md)
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Dělení na vlákna](index.md)
