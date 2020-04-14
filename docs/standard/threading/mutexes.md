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
ms.openlocfilehash: 3f020db49bcdcbf6ce3d573348a93b06e87db199
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242722"
---
# <a name="mutexes"></a>Mutex – třídy
Objekt můžete <xref:System.Threading.Mutex> použít k poskytnutí výhradnípřístup k prostředku. Třída <xref:System.Threading.Mutex> používá více systémových <xref:System.Threading.Monitor> prostředků než třída, ale může být zařazena přes hranice domény aplikace, může být použita s více čeká a lze ji použít k synchronizaci podprocesů v různých procesech. Porovnání mechanismů spravované synchronizace naleznete v [tématu Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Příklady kódu naleznete v referenční <xref:System.Threading.Mutex.%23ctor%2A> dokumentaci pro konstruktory.  
  
## <a name="using-mutexes"></a>Použití mutexů  
 Vlákno volá <xref:System.Threading.WaitHandle.WaitOne%2A> metodu mutex požadovat vlastnictví. Volání blokuje, dokud mutex je k dispozici, nebo dokud neuplyne volitelný časový limit intervalu. Stav mutex je signalizován, pokud žádné vlákno vlastní.  
  
 Podproces uvolní mutex voláním <xref:System.Threading.Mutex.ReleaseMutex%2A> jeho metody. Objekty Mutex mají spřažení vláken; to znamená, že objekt mutex může být uvolněn pouze podprocesem, který jej vlastní. Pokud vlákno uvolní mutex, který nevlastní, <xref:System.ApplicationException> je vyvolána ve vlákně.  
  
 Vzhledem <xref:System.Threading.Mutex> k tomu, že třída je <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle.WaitAny%2A> odvozena <xref:System.Threading.WaitHandle> z <xref:System.Threading.WaitHandle>, <xref:System.Threading.Mutex> můžete také volat statické nebo metody požadovat vlastnictví v kombinaci s jinými popisovače čekání.  
  
 Pokud vlákno vlastní <xref:System.Threading.Mutex>, toto vlákno <xref:System.Threading.Mutex> můžete zadat stejné v opakovaných volání čekání požadavku bez blokování jeho spuštění; však musí uvolnit <xref:System.Threading.Mutex> tolikrát uvolnit vlastnictví.  
  
## <a name="abandoned-mutexes"></a>Opuštěné mutexes  
 Pokud vlákno ukončí bez <xref:System.Threading.Mutex>uvolnění , mutex se říká, že je opuštěn. To často označuje závažnou chybu programování, protože prostředek, který objekt mutex chrání, může být ponechán v nekonzistentním stavu. V rozhraní .NET Framework verze <xref:System.Threading.AbandonedMutexException> 2.0 je vyvolána v dalším vlákně, která získá mutex.  
  
> [!NOTE]
> V rozhraní .NET Framework verze 1.0 a 1.1 je opuštěné nastaveno <xref:System.Threading.Mutex> na signalizovaný stav a další čekající vlákno získá vlastnictví. Pokud žádné vlákno čeká, zůstane <xref:System.Threading.Mutex> v signalizovaném stavu. Žádná výjimka se nevyvolá.  
  
 V případě mutex celého systému, opuštěné mutex může znamenat, že aplikace byla ukončena náhle (například pomocí Správce úloh systému Windows).  
  
## <a name="local-and-system-mutexes"></a>Místní a systémové objekty Mutexes  
 Objekty mutex jsou dvou typů: místní objekty mutex a pojmenované objekty mutex systému. Pokud vytvoříte <xref:System.Threading.Mutex> objekt pomocí konstruktoru, který přijímá název, je přidružen k objektu operačního systému tohoto názvu. Pojmenované systémové objekty mutex jsou viditelné v celém operačním systému a lze je použít k synchronizaci aktivit procesů. Můžete vytvořit <xref:System.Threading.Mutex> více objektů, které představují stejný pojmenovaný systémmu <xref:System.Threading.Mutex.OpenExisting%2A> mutex a můžete použít metodu k otevření existujícího pojmenovaného objektu mutex systému.  
  
 Místní objekt mutex existuje pouze v rámci procesu. Může být použit libovolným vláknem v procesu, <xref:System.Threading.Mutex> který má odkaz na místní objekt. Každý <xref:System.Threading.Mutex> objekt je samostatný místní objekt mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Zabezpečení řízení přístupu pro objekty Mutexes systému  
 Rozhraní .NET Framework verze 2.0 poskytuje možnost dotazovat a nastavovat zabezpečení řízení přístupu systému Windows pro pojmenované systémové objekty. Ochrana objekty mutex systému od okamžiku vytvoření se doporučuje, protože systémové objekty jsou globální a proto lze uzamknout jiným kódem než vlastní.  
  
 Informace o zabezpečení řízení přístupu pro objekty mutex naleznete v <xref:System.Threading.Mutex.GetAccessControl%2A> <xref:System.Threading.Mutex.SetAccessControl%2A>tématu <xref:System.Threading.Mutex.OpenExisting%2A> <xref:System.Threading.Mutex> <xref:System.Security.AccessControl.MutexSecurity> <xref:System.Security.AccessControl.MutexAccessRule> <xref:System.Security.AccessControl.MutexRights> a třídy, <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> výčet, , a metody třídy a konstruktoru.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
- [Závity a závity](threads-and-threading.md)
- [Dělení na vlákna](index.md)
