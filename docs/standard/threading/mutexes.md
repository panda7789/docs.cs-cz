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
ms.openlocfilehash: f9267bdd19a14995851f2689651c001815812912
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291172"
---
# <a name="mutexes"></a>Mutex – třídy
K <xref:System.Threading.Mutex> Poskytnutí výhradního přístupu k prostředku můžete použít objekt. <xref:System.Threading.Mutex>Třída používá více systémových prostředků než <xref:System.Threading.Monitor> třída, ale lze ji zařadit napříč hranicemi domény aplikace, lze ji použít s více čekacími procesy a lze ji použít k synchronizaci vláken v různých procesech. Porovnání mechanismů spravované synchronizace najdete v tématu [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md).  
  
 Příklady kódu naleznete v referenční dokumentaci pro <xref:System.Threading.Mutex.%23ctor%2A> konstruktory.  
  
## <a name="using-mutexes"></a>Použití mutexů  
 Vlákno volá <xref:System.Threading.WaitHandle.WaitOne%2A> metodu mutex pro vyžádání vlastnictví. Bloky volání, dokud není objekt mutex k dispozici, nebo dokud neuplyne časový interval volitelného časového limitu. Stav mutex je signalizována, pokud není vlastníkem vlákna.  
  
 Vlákno uvolňuje mutex voláním jeho <xref:System.Threading.Mutex.ReleaseMutex%2A> metody. Mutexy mají spřažení vlákna; To znamená, že mutex může být uvolněn pouze vláknem, které je vlastníkem. Pokud vlákno uvolní mutex, který nevlastní, <xref:System.ApplicationException> je vyvolána ve vlákně.  
  
 Vzhledem k tomu <xref:System.Threading.Mutex> , že třída je odvozena z <xref:System.Threading.WaitHandle> , můžete také volat statické <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle.WaitAny%2A> metody nebo metody <xref:System.Threading.WaitHandle> pro vyžádání vlastnictví <xref:System.Threading.Mutex> v kombinaci s jinými obslužnými rutinami čekání.  
  
 Pokud vlákno vlastní a <xref:System.Threading.Mutex> , může toto vlákno určit stejné <xref:System.Threading.Mutex> v opakovaných voláních Wait-Request bez blokování jeho spuštění, ale musí vydávat tolik, <xref:System.Threading.Mutex> kolikrát se má uvolnit vlastnictví.  
  
## <a name="abandoned-mutexes"></a>Opuštěné mutexy  
 Pokud se vlákno ukončí bez uvolnění a <xref:System.Threading.Mutex> , je tento mutex označován jako opuštěno. To často znamená závažnou chybu při programování, protože prostředek, který zámek mutex chrání, může být ponechán v nekonzistentním stavu. V .NET Framework verze 2,0 <xref:System.Threading.AbandonedMutexException> je vyvolána v dalším vlákně, která získá mutex.  
  
> [!NOTE]
> V .NET Framework verzích 1,0 a 1,1 je opuštění <xref:System.Threading.Mutex> nastavené na signálový stav a další čekající vlákno získá vlastnictví. Pokud žádné vlákno nečeká, <xref:System.Threading.Mutex> zůstane ve stavu signalizace. Žádná výjimka se nevyvolá.  
  
 V případě mutexu v rámci systému může opuštěný mutex indikovat, že aplikace byla náhle ukončena (například pomocí Správce úloh systému Windows).  
  
## <a name="local-and-system-mutexes"></a>Místní a systémové mutexy  
 Mutexy mají dva typy: místní mutexy a pojmenované mutexy systému. Vytvoříte <xref:System.Threading.Mutex> -li objekt pomocí konstruktoru, který přijímá název, je spojen s objektem operačního systému daného názvu. Pojmenované mutexy systému jsou viditelné v celém operačním systému a lze je použít k synchronizaci aktivit procesů. Můžete vytvořit více <xref:System.Threading.Mutex> objektů, které reprezentují stejný pojmenovaný mutex systému, a můžete použít <xref:System.Threading.Mutex.OpenExisting%2A> metodu k otevření existujícího pojmenovaného mutex systému.  
  
 Místní mutex existuje jenom v rámci vašeho procesu. Dá se použít v jakémkoli vlákně v procesu, který má odkaz na místní <xref:System.Threading.Mutex> objekt. Každý <xref:System.Threading.Mutex> objekt je samostatný místní mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Access Control zabezpečení pro mutexy systému  
 .NET Framework verze 2,0 poskytuje možnost dotazování a nastavení zabezpečení řízení přístupu systému Windows pro pojmenované systémové objekty. Doporučuje se chránit mutexy systému před vytvořením, protože systémové objekty jsou globální a proto je lze uzamknout jiným kódem než vlastním.  
  
 Informace o zabezpečení řízení přístupu pro mutexy naleznete v tématech <xref:System.Security.AccessControl.MutexSecurity> třídy a <xref:System.Security.AccessControl.MutexAccessRule> , <xref:System.Security.AccessControl.MutexRights> výčet, <xref:System.Threading.Mutex.GetAccessControl%2A> , <xref:System.Threading.Mutex.SetAccessControl%2A> a <xref:System.Threading.Mutex.OpenExisting%2A> metody <xref:System.Threading.Mutex> třídy a <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktoru.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Dělení na vlákna](index.md)
