---
title: "Výjimky ve spravovaných vláknech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f68a7aebdb1625b149287d70fd91c2108a658b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-in-managed-threads"></a>Výjimky ve spravovaných vláknech
Od verze rozhraní .NET Framework verze 2.0, modul common language runtime umožňuje nejvíce neošetřených výjimek v vláken přirozeně pokračovat. Ve většině případů to znamená, že neošetřené výjimce způsobí, že je aplikace ukončena.  
  
> [!NOTE]
>  Toto je významné změny z rozhraní .NET Framework verze 1.0 a 1.1, které přinášejí mnoho neošetřených výjimek backstop – například neošetřené výjimky v podprocesy z fondu podprocesů. V tématu [změnit z předchozích verzí](#ChangeFromPreviousVersions) dál v tomto tématu.  
  
 Modul common language runtime poskytuje backstop určité neošetřené výjimky, které se používají pro řízení toku programu:  
  
-   A <xref:System.Threading.ThreadAbortException> je vyvolána v vlákno, protože <xref:System.Threading.Thread.Abort%2A> byla volána.  
  
-   <xref:System.AppDomainUnloadedException> Je vyvolána v vlákno, protože odpojení doménu aplikace, ve kterém je prováděna vlákno.  
  
-   Modul common language runtime nebo hostitelský proces se ukončuje vlákno podle došlo k vnitřní výjimce.  
  
 Pokud jsou tyto výjimky neošetřené v vláken vytvořený modul common language runtime, výjimka ukončí vlákno, ale modul common language runtime neumožňuje výjimka, která má pokračovat.  
  
 Pokud jsou tyto výjimky neošetřené do hlavního vlákna nebo vláken, které zadali modulu runtime z nespravovaného kódu, budou pokračovat vést k ukončení aplikace za normálních okolností.  
  
> [!NOTE]
>  Je možné pro modul runtime má být vyvolána k neošetřené výjimce před spravovaný kód dostal příležitost k instalaci obslužnou rutinu výjimky. I když spravovaného kódu dříve žádné šanci na zpracování takové výjimky, může pokračovat přirozeně výjimku.  
  
## <a name="exposing-threading-problems-during-development"></a>Vystavení vlákna problémy během vývoje  
 Pokud vláken mají povoleno selhání tiše, bez ukončení aplikace, může pokračovat nezjištěné programovací vážným problémům. Toto je konkrétního problému služeb a dalších aplikací, které se spustit po delší dobu. Jako vláken nezdaří, je poškozena postupně stav programu. Může snížit výkon aplikace nebo aplikace může přestat reagovat.  
  
 Povolení neošetřených výjimek v vláken samozřejmě pokračovat, dokud operační systém ukončuje programu, zpřístupní takovým problémům během vývoje a testování. Zprávy o chybách na program ukončení podpory ladění.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Změnit z předchozích verzí  
 Nejdůležitější změny se vztahují na spravovaná vlákna. V rozhraní .NET Framework verze 1.0 a 1.1 poskytuje modul common language runtime backstop neošetřené výjimky v následujících situacích:  
  
-   Neexistuje žádný takový akci jako k neošetřené výjimce v podprocesu fondu vláken. Pokud úloha vyvolá výjimku, který nezpracovává, modul runtime vytiskne trasování zásobníku výjimky ke konzole a vrátí do fondu vláken vlákno.  
  
-   Neexistuje žádná taková věc k neošetřené výjimce v podprocesu vytvořeného s <xref:System.Threading.Thread.Start%2A> metodu <xref:System.Threading.Thread> třídy. Pokud kód spuštěný na takové vlákno vyvolá výjimku, který nezpracovává, modul runtime vytiskne trasování zásobníku výjimky ke konzole a řádně ukončí vlákno.  
  
-   Neexistuje žádná taková věc jako neošetřená výjimka ve vláknu finalizační metodu. Pokud finalizační metody vyvolá výjimku, který nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a pak umožňuje vlákno finalizační metodu obnovit systémem finalizační metody.  
  
 Stav popředí nebo pozadí spravované vlákno toto chování neovlivňuje.  
  
 Pro neošetřených výjimek na vláken z nespravovaného kódu je další menší rozdíl. JIT – připojené dialogu runtime brání dialogu operačního systému pro spravované výjimky nebo nativní výjimky na vláken, které uplynuly prostřednictvím nativního kódu. Proces se ukončuje ve všech případech.  
  
### <a name="migrating-code"></a>Migrace kódu  
 Obecně platí změna zveřejní dříve nerozpoznané programovací problémy tak, aby odstraněny. V některých případech ale programátory může využili backstop modulu runtime, např. Chcete-li ukončit vláken. V závislosti na situaci že měli zvážit jednu z následujících strategií migrace:  
  
-   Změnit strukturu kód, aby vlákno ukončí řádně, když je obdržena signál.  
  
-   Použití <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda k přerušení vlákno.  
  
-   Pokud vlákno musí být zastaven, ukončení procesu mohli pokračovat, ujistěte se, vlákno vlákna na pozadí tak, aby je automaticky ukončen na ukončení procesu.  
  
 Ve všech případech strategie postupujte podle pokynů pro návrh pro výjimky. V tématu [návrh pokyny pro výjimky](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Příznak kompatibility aplikace  
 Z důvodu dočasného kompatibility správci můžete umístit příznak kompatibility ve `<runtime>` oddílu konfiguračního souboru aplikace. To způsobí, že modul common language runtime se vrátit k chování verze 1.0 a 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Přepsání hostitele  
 V rozhraní .NET Framework verze 2.0, můžete použít nespravované hostitele [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní v rozhraní API hostování přepsat výchozí nastavení neošetřená výjimka zásady modul common language runtime. [Iclrpolicymanager::setunhandledexceptionpolicy –](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) funkce slouží k nastavení zásad pro neošetřených výjimek.  
  
## <a name="see-also"></a>Viz také  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
