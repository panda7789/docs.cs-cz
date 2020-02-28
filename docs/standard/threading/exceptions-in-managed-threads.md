---
title: Výjimky ve spravovaných vláknech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 6c14c60b30f8f70aa5e888ed45d6f867154e18d8
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159647"
---
# <a name="exceptions-in-managed-threads"></a>Výjimky ve spravovaných vláknech
Počínaje verzí 2,0 .NET Framework modul CLR (Common Language Runtime) umožňuje většině neošetřených výjimek v vláknech pokračovat přirozeně. Ve většině případů to znamená, že Neošetřená výjimka způsobí ukončení aplikace.  
  
> [!NOTE]
> Jedná se o významnou změnu z .NET Framework verzí 1,0 a 1,1, která poskytuje zastavení pro mnoho neošetřených výjimek, například neošetřené výjimky v vláknech fondu vláken. Viz [změnit z předchozích verzí](#ChangeFromPreviousVersions) dále v tomto tématu.  
  
 Modul CLR (Common Language Runtime) poskytuje zastavení pro určité neošetřené výjimky, které se používají pro řízení toku programu:  
  
- Ve vlákně je vyvolána <xref:System.Threading.ThreadAbortException>, protože byla volána <xref:System.Threading.Thread.Abort%2A>.  
  
- Ve vlákně je vyvolána <xref:System.AppDomainUnloadedException>, protože doména aplikace, ve které je vlákno prováděno, je odpojena.  
  
- Modul CLR (Common Language Runtime) nebo hostitelský proces ukončí vlákno vyvoláním vnitřní výjimky.  
  
 Pokud některá z těchto výjimek není ošetřena v vláknech vytvořených modulem CLR (Common Language Runtime), výjimka ukončí vlákno, ale modul CLR (Common Language Runtime) nedovoluje, aby výjimka pokračovala dále.  
  
 Pokud jsou tyto výjimky v hlavním vlákně neošetřené nebo v vláknech, které vstoupily do modulu runtime z nespravovaného kódu, fungují normálně, což vede k ukončení aplikace.  
  
> [!NOTE]
> Je možné, aby modul runtime vyvolal neošetřenou výjimku předtím, než jakýkoli spravovaný kód měl možnost nainstalovat obslužnou rutinu výjimky. I když spravovaný kód neměl žádnou možnost zpracovat takovou výjimku, může výjimka pokračovat přirozeně.  
  
## <a name="exposing-threading-problems-during-development"></a>Odhalení problémů s vlákny během vývoje  
 Když můžou vlákna selhat bez problémů bez ukončení aplikace, může se stát, že se nedetekuje vážné programové problémy. Toto je konkrétní problém pro služby a další aplikace, které běží po delší dobu. Když dojde k selhání vláken, stav programu se postupně bude poškodit. Výkon aplikace může být degradován nebo aplikace přestane reagovat.  
  
 Povolení neošetřených výjimek v vláknech pro pokračování v přirozeném prostředí, dokud operační systém neukončí program, zveřejňuje tyto problémy při vývoji a testování. Zprávy o chybách pro ukončení programu podporují ladění.  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a>Změnit z předchozích verzí  
 Nejvýznamnější změna se týká spravovaných vláken. V .NET Framework verzích 1,0 a 1,1 poskytuje modul CLR (Common Language Runtime) pro neošetřené výjimky v následujících situacích příkaz restop:  
  
- Ve vlákně fondu vláken neexistuje žádná taková věc jako Neošetřená výjimka. Když úloha vyvolá výjimku, kterou nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a potom vrátí vlákno do fondu vláken.  
  
- Neexistuje žádná taková věc jako Neošetřená výjimka ve vlákně vytvořeném pomocí metody <xref:System.Threading.Thread.Start%2A> třídy <xref:System.Threading.Thread>. Když kód spuštěný v takovém vlákně vyvolá výjimku, kterou nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a poté řádně ukončí vlákno.  
  
- Neexistuje žádná taková věc jako Neošetřená výjimka ve vlákně finalizační metody. Když finalizační metoda vyvolá výjimku, kterou nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a poté umožňuje finalizačnímu vláknu obnovit spuštěné finalizační metody.  
  
 Stav popředí nebo pozadí spravovaného vlákna nemá vliv na toto chování.  
  
 V případě neošetřených výjimek na vláknech, které pocházejí z nespravovaného kódu, je rozdíl malý. Dialogové okno runtime JIT – připojit přesměruje dialog operačního systému na spravované výjimky nebo nativní výjimky na vláknech, které prošly nativním kódem. Proces se ukončí ve všech případech.  
  
### <a name="migrating-code"></a>Migrace kódu  
 Obecně platí, že změna bude zveřejnit dříve nerozpoznané programové problémy, aby bylo možné je opravit. V některých případech však programátoři mohli využít výhod běhového prostředí za běhu, například pro ukončení vláken. V závislosti na situaci by měly vzít v úvahu jednu z následujících strategií migrace:  
  
- Přestrukturuje kód, aby se vlákno po obdržení signálu řádně ukončilo.  
  
- K přerušení vlákna použijte metodu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
- Pokud vlákno musí být zastaveno, aby bylo možné pokračovat v ukončení procesu, nastavte vlákno vlákno na pozadí tak, aby bylo při ukončení procesu automaticky ukončeno.  
  
 Ve všech případech by strategie měla postupovat podle pokynů pro návrh pro výjimky. Výjimky najdete v tématu [pokyny pro návrh](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Příznak kompatibility aplikace  
 Jako dočasná míra kompatibility můžou správci umístit příznak kompatibility do oddílu `<runtime>` konfiguračního souboru aplikace. To způsobí, že se modul CLR (Common Language Runtime) vrátí k chování verzí 1,0 a 1,1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Přepsání hostitele  
 V .NET Framework verze 2,0 může nespravovaný hostitel používat rozhraní [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) v rozhraní API pro hostování k přepsání výchozích neošetřených zásad pro modul CLR (Common Language Runtime). Funkce [ICLRPolicyManager:: SetUnhandledExceptionPolicy –](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) slouží k nastavení zásad pro neošetřené výjimky.  
  
## <a name="see-also"></a>Viz také

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
