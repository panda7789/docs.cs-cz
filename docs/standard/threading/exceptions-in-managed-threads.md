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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159647"
---
# <a name="exceptions-in-managed-threads"></a>Výjimky ve spravovaných vláknech
Počínaje rozhraním .NET Framework verze 2.0 umožňuje běžný jazyk runtime většinu neošetřených výjimek ve vláknech přirozeně pokračovat. Ve většině případů to znamená, že neošetřená výjimka způsobí ukončení aplikace.  
  
> [!NOTE]
> Jedná se o významnou změnu oproti rozhraní .NET Framework verze 1.0 a 1.1, které poskytují backstop pro mnoho neošetřených výjimek , například neošetřené výjimky ve vláknech fondu vláken. Viz [Změna z předchozích verzí](#ChangeFromPreviousVersions) dále v tomto tématu.  
  
 Běžný jazyk runtime poskytuje backstop pro některé neošetřené výjimky, které se používají pro řízení toku programu:  
  
- A <xref:System.Threading.ThreadAbortException> je vyvolána ve <xref:System.Threading.Thread.Abort%2A> vlákně, protože byl volán.  
  
- Je <xref:System.AppDomainUnloadedException> vyvolána ve vlákně, protože doména aplikace, ve kterém je vlákno provádění je uvolněna.  
  
- Běžný jazyk runtime nebo hostitelský proces ukončí vlákno vyvoláním vnitřní výjimky.  
  
 Pokud některá z těchto výjimek nejsou zpracovány ve vláknech vytvořených běžným jazykem runtime, výjimka ukončí vlákno, ale běžný jazyk runtime neumožňuje výjimku pokračovat dále.  
  
 Pokud tyto výjimky nejsou zpracovány v hlavním vlákně nebo ve vláknech, která zadala runtime z nespravovaného kódu, postupují normálně, což vede k ukončení aplikace.  
  
> [!NOTE]
> Je možné, že za běhu vyvolat neošetřenou výjimku před libovolný spravovaný kód měl možnost nainstalovat obslužnou rutinu výjimky. I když spravovaný kód neměl šanci zpracovat takovou výjimku, výjimka může postupovat přirozeně.  
  
## <a name="exposing-threading-problems-during-development"></a>Odhalení problémů s vlákny během vývoje  
 Pokud vlákna mohou selhat tiše, bez ukončení aplikace, vážné problémy s programováním může přejít nezjištěný. To je zvláštní problém pro služby a další aplikace, které běží po delší dobu. Při selhání vláken se stav programu postupně poškodí. Výkon aplikace může snížit nebo aplikace přestane odpovídat.  
  
 Povolení neošetřené výjimky ve vláknech postupovat přirozeně, dokud operační systém ukončí program, zpřístupňuje tyto problémy během vývoje a testování. Zprávy o chybách při ukončení programu podporují ladění.  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a>Změna z předchozích verzí  
 Nejvýznamnější změna se vměšuje do spravovaných vláken. V rozhraní .NET Framework verze 1.0 a 1.1, common language runtime poskytuje backstop pro neošetřené výjimky v následujících situacích:  
  
- Neexistuje žádná taková věc jako neošetřené výjimky ve vlákně fondu vláken. Když úloha vyvolá výjimku, kterou nezpracovává, vytiskne runtime trasování zásobníku výjimek do konzoly a potom vrátí vlákno do fondu vláken.  
  
- Neexistuje žádná taková věc jako neošetřené výjimky <xref:System.Threading.Thread.Start%2A> na <xref:System.Threading.Thread> vlákno vytvořené metodou třídy. Když kód spuštěný v takovém vlákně vyvolá výjimku, kterou nezpracovává, vytiskne runtime trasování zásobníku výjimek do konzoly a potom řádně ukončí vlákno.  
  
- Neexistuje žádná taková věc jako neošetřené výjimky ve vlákně finalizační metody. Když finalizační metoda vyvolá výjimku, kterou nezpracovává, vytiskne za běhu trasování zásobníku výjimek do konzoly a pak povolí finalizační podproces pokračovat ve spuštění finalizačních metod.  
  
 Stav popředí nebo pozadí spravovaného vlákna nemá vliv na toto chování.  
  
 Pro neošetřené výjimky na vláknech pocházejících z nespravovaného kódu je rozdíl jemnější. Dialogové okno připojit jit za běhu předcvrzuje dialogové okno operačního systému pro spravované výjimky nebo nativní výjimky ve vláknech, které prošly nativním kódem. Proces bude ukončen ve všech případech.  
  
### <a name="migrating-code"></a>Migrace kódu  
 Obecně platí, že změna bude vystavit dříve nerozpoznané problémy s programováním tak, aby mohly být opraveny. V některých případech však programátoři mohli využít backstop runtime, například ukončit podprocesy. V závislosti na situaci by měli zvážit jednu z následujících strategií migrace:  
  
- Restrukturalizovat kód tak, aby vlákno ukončí řádně při přijetí signálu.  
  
- Pomocí <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody přerušte vlákno.  
  
- Pokud podproces musí být zastaven, aby ukončení procesu může pokračovat, aby vlákno podproces podproces na pozadí tak, aby je automaticky ukončena při ukončení procesu.  
  
 Ve všech případech by se strategie měla řídit pokyny pro návrh výjimek. Viz [Pokyny pro návrh výjimek](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Příznak kompatibility aplikací  
 Jako dočasné opatření kompatibility mohou správci umístit `<runtime>` příznak kompatibility do části konfiguračního souboru aplikace. To způsobí, že běžný jazyk runtime vrátit k chování verze 1.0 a 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Přepsání hostitele  
 V rozhraní .NET Framework verze 2.0 může nespravovaný hostitel použít rozhraní [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) v hostitelském rozhraní API k přepsání výchozí zásady neošetřené výjimky modulu COMMON Language runtime. Funkce [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) se používá k nastavení zásad pro neošetřené výjimky.  
  
## <a name="see-also"></a>Viz také

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
