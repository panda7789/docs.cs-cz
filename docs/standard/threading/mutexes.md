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
ms.openlocfilehash: 874f879697db0b47c73626350eeb05a01b38e1bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127557"
---
# <a name="mutexes"></a>Mutex – třídy
K poskytnutí exkluzivního přístupu k prostředku můžete použít objekt <xref:System.Threading.Mutex>. Třída <xref:System.Threading.Mutex> používá více systémových prostředků než <xref:System.Threading.Monitor> třídy, ale lze ji zařadit napříč hranicemi domény aplikace, lze ji použít s více čekacími procesy a lze ji použít k synchronizaci vláken v různých procesech. Porovnání mechanismů spravované synchronizace najdete v tématu [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Příklady kódu naleznete v referenční dokumentaci pro konstruktory <xref:System.Threading.Mutex.%23ctor%2A>.  
  
## <a name="using-mutexes"></a>Použití mutexů  
 Vlákno volá metodu <xref:System.Threading.WaitHandle.WaitOne%2A> mutex pro vyžádání vlastnictví. Bloky volání, dokud není objekt mutex k dispozici, nebo dokud neuplyne časový interval volitelného časového limitu. Stav mutex je signalizována, pokud není vlastníkem vlákna.  
  
 Vlákno uvolňuje mutex voláním jeho metody <xref:System.Threading.Mutex.ReleaseMutex%2A>. Mutexy mají spřažení vlákna; To znamená, že mutex může být uvolněn pouze vláknem, které je vlastníkem. Pokud vlákno uvolní mutex, který nevlastní, je vyvolána <xref:System.ApplicationException> ve vlákně.  
  
 Vzhledem k tomu, že třída <xref:System.Threading.Mutex> je odvozena z <xref:System.Threading.WaitHandle>, můžete také volat statické <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> metody <xref:System.Threading.WaitHandle> pro vyžádání vlastnictví <xref:System.Threading.Mutex> v kombinaci s jinými obslužnými rutinami.  
  
 Pokud vlákno vlastní <xref:System.Threading.Mutex>, může toto vlákno určit stejný <xref:System.Threading.Mutex> v opakovaných voláních Wait-Request bez blokování jeho provádění; ale musí vydávat <xref:System.Threading.Mutex> tolikrát, kolikrát vydává vlastnictví.  
  
## <a name="abandoned-mutexes"></a>Opuštěné mutexy  
 Pokud se vlákno ukončí bez uvolnění <xref:System.Threading.Mutex>, odmutex se říká, že má být opuštěn. To často znamená závažnou chybu při programování, protože prostředek, který zámek mutex chrání, může být ponechán v nekonzistentním stavu. V .NET Framework verze 2,0 se <xref:System.Threading.AbandonedMutexException> vyvolal v dalším vlákně, které získá mutex.  
  
> [!NOTE]
> V .NET Framework verzích 1,0 a 1,1 je opuštěná <xref:System.Threading.Mutex> nastavena na signálový stav a další čekající vlákno získá vlastnictví. Pokud žádné vlákno nečeká, <xref:System.Threading.Mutex> zůstane v signalizačním stavu. Není vyvolána žádná výjimka.  
  
 V případě mutexu v rámci systému může opuštěný mutex indikovat, že aplikace byla náhle ukončena (například pomocí Správce úloh systému Windows).  
  
## <a name="local-and-system-mutexes"></a>Místní a systémové mutexy  
 Mutexy mají dva typy: místní mutexy a pojmenované mutexy systému. Vytvoříte-li objekt <xref:System.Threading.Mutex> pomocí konstruktoru, který přijímá název, je spojen s objektem operačního systému daného názvu. Pojmenované mutexy systému jsou viditelné v celém operačním systému a lze je použít k synchronizaci aktivit procesů. Můžete vytvořit více objektů <xref:System.Threading.Mutex>, které reprezentují stejný pojmenovaný mutex systému, a můžete použít metodu <xref:System.Threading.Mutex.OpenExisting%2A> k otevření existujícího pojmenovaného mutex systému.  
  
 Místní mutex existuje jenom v rámci vašeho procesu. Dá se použít v jakémkoli vlákně v procesu, který má odkaz na místní objekt <xref:System.Threading.Mutex>. Každý objekt <xref:System.Threading.Mutex> je samostatný místní mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Access Control zabezpečení pro mutexy systému  
 .NET Framework verze 2,0 poskytuje možnost dotazování a nastavení zabezpečení řízení přístupu systému Windows pro pojmenované systémové objekty. Doporučuje se chránit mutexy systému před vytvořením, protože systémové objekty jsou globální a proto je lze uzamknout jiným kódem než vlastním.  
  
 Informace o zabezpečení řízení přístupu pro mutexy naleznete v tématu třídy <xref:System.Security.AccessControl.MutexSecurity> a <xref:System.Security.AccessControl.MutexAccessRule>, <xref:System.Security.AccessControl.MutexRights> výčet, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>a <xref:System.Threading.Mutex.OpenExisting%2A>ch metod třídy <xref:System.Threading.Mutex> a konstruktoru <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Dělení objektů a funkcí](threading-objects-and-features.md)
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Dělení na vlákna](index.md)
