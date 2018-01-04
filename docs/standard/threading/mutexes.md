---
title: "Mutex – třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2804d0c60657623b558d86386c5e1043422b648c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="mutexes"></a>Mutex – třídy
Můžete použít <xref:System.Threading.Mutex> objekt zajistit výhradní přístup k prostředku. <xref:System.Threading.Mutex> Třída používá více systémových prostředků, než <xref:System.Threading.Monitor> třídy, ale může být zařazeno napříč hranicemi domény aplikace, dá použít s více počká a může sloužit k synchronizaci vláken v jiné procesy. Porovnání mechanismů spravované synchronizace najdete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Příklady kódu v tématu referenční dokumentaci k nástroji pro <xref:System.Threading.Mutex.%23ctor%2A> konstruktory.  
  
## <a name="using-mutexes"></a>Pomocí mutex – třídy  
 Volá vlákna <xref:System.Threading.WaitHandle.WaitOne%2A> metoda mutex vlastnictví požadavku. Bloky volání dokud mutex je k dispozici, nebo dokud volitelné časový limit uplyne. Stav mutex je signál, pokud žádný přístup z více vláken je jeho vlastníkem.  
  
 Vlákno uvolní mutex voláním jeho <xref:System.Threading.Mutex.ReleaseMutex%2A> metoda. Mutex – třídy mají spřažení podprocesu; To znamená mohou být vydány mutex pouze pomocí podproces, který je jeho vlastníkem. Pokud vlákno uvolní mutex nevlastní, <xref:System.ApplicationException> je vyvolána v vlákno.  
  
 Protože <xref:System.Threading.Mutex> třída odvozená z <xref:System.Threading.WaitHandle>, byste také zavolat statických <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> metody <xref:System.Threading.WaitHandle> z požadavku vlastnictví <xref:System.Threading.Mutex> ve spojení s jinými obslužné rutiny čekání.  
  
 Pokud vlastní vlákna <xref:System.Threading.Mutex>, vlákno můžete zadat stejný <xref:System.Threading.Mutex> ve voláních opakovaný požadavek čekání bez blokování jeho provádění; však je nutné uvolnit <xref:System.Threading.Mutex> jako tolikrát, kolikrát chcete-li uvolnit vlastnictví.  
  
## <a name="abandoned-mutexes"></a>Opuštěného mutex – třídy  
 Pokud vlákno ukončí bez uvolnění <xref:System.Threading.Mutex>, mutex říká, že je možné opuštění. Protože je v nekonzistentním stavu může být ponecháno na prostředek, který chrání mutex často označuje závažné chybě programování. V rozhraní .NET Framework verze 2.0 <xref:System.Threading.AbandonedMutexException> je vyvolána v další vlákno, které získá mutex.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1, opuštěného <xref:System.Threading.Mutex> je nastaven na signalizovaného stav a další čekání na vlákno získá vlastnictví. Pokud žádné podproces čeká <xref:System.Threading.Mutex> zůstane v signalizovaného stavu. Nedojde k výjimce.  
  
 V případě mutex systémové opuštěného mutex může znamenat, že aplikace byla ukončena náhle (například pomocí Správce úloh systému Windows).  
  
## <a name="local-and-system-mutexes"></a>Místní a systému mutex – třídy  
 Mutex – třídy jsou dvou typů: místní mutex – třídy a mutex – třídy s názvem systému. Pokud vytvoříte <xref:System.Threading.Mutex> pomocí konstruktor, který přijímá název, je přidružen objektu operačního systému s tímto názvem. S názvem systém mutex – třídy jsou viditelné v rámci operačního systému a slouží k synchronizaci aktivity procesy. Můžete vytvořit několik <xref:System.Threading.Mutex> objekty, které představují stejné pojmenovaný vzájemně vyloučený přístup systému, a můžete <xref:System.Threading.Mutex.OpenExisting%2A> metoda otevřete existující pojmenovaný vzájemně vyloučený přístup systému.  
  
 Místní mutex existuje pouze v rámci procesu. Mohou být využívána libovolného vlákna procesu, který obsahuje odkaz na místní <xref:System.Threading.Mutex> objektu. Každý <xref:System.Threading.Mutex> objekt není samostatný objekt mutex místní.  
  
### <a name="access-control-security-for-system-mutexes"></a>Zabezpečení řízení přístupu pro systém mutex – třídy  
 Rozhraní .NET Framework verze 2.0 poskytuje možnost pro dotazování a nastavit zabezpečení řízení přístupu Windows objektů s názvem systému. Ochrana systému mutex – třídy v okamžiku vytvoření se doporučuje, protože systémové objekty jsou globální a proto může být uzamčen kódu než vlastní.  
  
 Informace o zabezpečení řízení přístupu pro mutex – třídy, v tématu <xref:System.Security.AccessControl.MutexSecurity> a <xref:System.Security.AccessControl.MutexAccessRule> třídy, <xref:System.Security.AccessControl.MutexRights> výčtu <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, a <xref:System.Threading.Mutex.OpenExisting%2A> metody <xref:System.Threading.Mutex> třídy a <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktor.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)
