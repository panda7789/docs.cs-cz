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
ms.openlocfilehash: dededed9bcd4558296323532c0ecbfb60bf5b311
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015092"
---
# <a name="mutexes"></a>Mutex – třídy
Můžete použít <xref:System.Threading.Mutex> objektu pro výhradní přístup k prostředku. <xref:System.Threading.Mutex> Třída používá více systémových prostředků, než <xref:System.Threading.Monitor> třídy, ale může být zařazována přes hranice aplikační domény, je možné s více čeká a je možné k synchronizaci vláken v různých procesů. Porovnání mechanismy spravované synchronizace najdete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Příklady kódu naleznete v tématu v referenční dokumentaci <xref:System.Threading.Mutex.%23ctor%2A> konstruktory.  
  
## <a name="using-mutexes"></a>Pomocí mutexů  
 Vlákno volá <xref:System.Threading.WaitHandle.WaitOne%2A> metoda mutex vlastnictví požadavku. Bloky volání dokud mutex je k dispozici, nebo dokud volitelný časový interval uplyne. Stav objektu mutex je signál, pokud žádné vlákno jeho vlastníkem.  
  
 Vlákno uvolní objekt mutex voláním jeho <xref:System.Threading.Mutex.ReleaseMutex%2A> metoda. Mutexů mít spřažení vláken; To znamená mohou být vydány mutex pouze ve vlákně, které jej vlastní. Pokud vlákno uvolní objekt mutex nevlastní, <xref:System.ApplicationException> je vyvolána výjimka ve vlákně.  
  
 Protože <xref:System.Threading.Mutex> třída odvozena z <xref:System.Threading.WaitHandle>, můžete také volat statickou <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> metody <xref:System.Threading.WaitHandle> požadavek vlastnictví <xref:System.Threading.Mutex> ve spojení s jinými obslužné rutiny čekání.  
  
 Pokud vlastní vlákno <xref:System.Threading.Mutex>, vlákno může zadat stejné <xref:System.Threading.Mutex> ve voláních opakovaný požadavek čekání bez blokování jeho spuštění, ale je nutné uvolnit <xref:System.Threading.Mutex> jako tolikrát, kolikrát k uvolnění vlastnictví.  
  
## <a name="abandoned-mutexes"></a>Opuštěné mutexů  
 Pokud se vlákno ukončí bez uvolnění <xref:System.Threading.Mutex>, mutex se říká, že se opuštěna. To často určuje vážné programovací chyba, protože prostředek, který chrání mutex může být v nekonzistentním stavu. V rozhraní .NET Framework verze 2.0 <xref:System.Threading.AbandonedMutexException> je vyvolána v další vlákna, která se získá mutex.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1, opuštěné <xref:System.Threading.Mutex> čeká sady do signalizovaného stavu a další vlákno získává vlastnictví. Pokud žádné vlákno čeká <xref:System.Threading.Mutex> zůstane v signalizovaného stavu. Není vyvolána žádná výjimka.  
  
 V případě systémová mutex zrušenému objektu mutex může znamenat, že aplikace byla ukončena náhle (například pomocí Správce úloh Windows).  
  
## <a name="local-and-system-mutexes"></a>Místní a vzájemně vyloučené přístupy systému  
 Vzájemně vyloučené přístupy jsou dvou typů: místní mutexů a pojmenovaných systému mutexů. Pokud jste vytvořili <xref:System.Threading.Mutex> pomocí konstruktoru, který přijímá název, je přidružen k objektu operačního systému s tímto názvem. Název systému vzájemně vyloučené přístupy jsou viditelné v celém operačním systému a slouží k synchronizaci činností procesy. Můžete vytvořit více <xref:System.Threading.Mutex> objekty, které představují stejné pojmenovaný vzájemně vyloučený přístup systému, můžete si <xref:System.Threading.Mutex.OpenExisting%2A> metoda otevřít existující pojmenovaný vzájemně vyloučený přístup systému.  
  
 Místní objekt mutex existuje pouze v rámci procesu. Je možné z žádného vlákna v procesu, který obsahuje odkaz na místní <xref:System.Threading.Mutex> objektu. Každý <xref:System.Threading.Mutex> objekt je samostatný místní vzájemně vyloučený přístup.  
  
### <a name="access-control-security-for-system-mutexes"></a>Zabezpečení řízení přístupu pro mutexů systému  
 Rozhraní .NET Framework verze 2.0 umožňuje dotazování a nastavování Windows zabezpečení řízení přístupu pro pojmenované systémové objekty. Ochrana systému mutexů od okamžiku vytvoření se doporučuje, protože systémové objekty jsou globální a proto může být uzamčen jiný kód uzamknout.  
  
 Informace o zabezpečení řízení přístupu pro vzájemně vyloučené přístupy, najdete v článku <xref:System.Security.AccessControl.MutexSecurity> a <xref:System.Security.AccessControl.MutexAccessRule> třídy, <xref:System.Security.AccessControl.MutexRights> výčet, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, a <xref:System.Threading.Mutex.OpenExisting%2A> metody <xref:System.Threading.Mutex> třídy a <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktoru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Dělení na vlákna](index.md)
