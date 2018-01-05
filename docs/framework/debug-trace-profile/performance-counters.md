---
title: "Čítače výkonu v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15486a55fc15ba2cc3cc64db50f317b39dfd77bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="performance-counters-in-the-net-framework"></a>Čítače výkonu v rozhraní .NET Framework
Toto téma obsahuje seznam čítačů výkonu, které vás zavedou [sledování výkonu](http://technet.microsoft.com/library/cc749249.aspx).  
  
-   [Čítače výkonu výjimky](#exception)  
  
-   [Čítače výkonu interoperability](#interop)  
  
-   [Čítače výkonu JIT](#jit)  
  
-   [Načítání čítače výkonu](#loading)  
  
-   [Čítače výkonu uzamčení a přístup z více vláken](#lockthread)  
  
-   [Čítače výkonu paměti](#memory)  
  
-   [Čítače výkonu sítě](#networking)  
  
-   [Čítače výkonu zabezpečení](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>Čítače výkonu výjimky  
 Kategorie .NET CLR – výjimky výkonu konzole obsahuje čítače, které obsahují informace o výjimky vyvolané aplikace. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**vyvolané výjimky**|Zobrazí celkový počet výjimek vyvolaných od spuštění aplikace. Jedná se o výjimky .NET a nespravované výjimky, které jsou převedeny na výjimky .NET. Například HRESULT vrácená z nespravovaného kódu jsou převedeny na výjimky ve spravovaném kódu.<br /><br /> Tento čítač zahrnuje zpracovávaný i neošetřené výjimky. Výjimky, které jsou znovu vyvolány, se počítají znovu.|  
|**počet výjimek / s**|Zobrazí počet výjimek vyvolaných za sekundu. Jedná se o výjimky .NET a nespravované výjimky, které jsou převedeny na výjimky .NET. Například HRESULT vrácená z nespravovaného kódu jsou převedeny na výjimky ve spravovaném kódu.<br /><br /> Tento čítač zahrnuje zpracovávaný i neošetřené výjimky. Není v průměru v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování. Tento čítač je ukazatelem potenciální problémy s výkonem, pokud velké (> 100s) jsou vyvolány počet výjimek.|  
|**počet filtrů za sekundu**|Zobrazí počet filtry výjimek .NET provedených za sekundu. Bez ohledu na to, jestli výjimka je ošetřena vyhodnotí filtr výjimek.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**počet Finallys za sekundu**|Zobrazí počet finally – bloky provedených za sekundu. A nakonec bloku záruku, že se má provádět bez ohledu na to, jak byl bloku try byl ukončen.  Pouze počítají se nakonec bloky provést pro výjimku. Nakonec se tento čítač nezapočítávají bloky na normální kód cesty.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Throw k zachycení hloubka za sekundu**|Zobrazí počet rámce zásobníku provázán ze snímku, která vyvolala výjimku rámce, který zpracovává výjimky, za sekundu. Tento čítač se obnoví na nulu při zadání se obslužnou rutinu výjimky, takže vnořené výjimky zobrazit hloubka zásobníku obslužné rutiny pro obslužnou rutinu.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Čítače výkonu interoperability  
 Zprostředkovatel komunikace s objekty .NET CLR kategorie výkonu konzole zahrnuje čítače, které obsahují informace o interakci aplikace s komponenty modelu COM, služby COM + a externí typ knihoven. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**počet CCWs**|Zobrazí aktuální počet COM – obálky s možností (CCWs). DOLEVA je proxy server pro spravovaného objektu se na ně odkazovat z nespravované modelu COM klienta. Tento čítač udává počet spravovaných objektů, které odkazuje nespravovaného kódu COM.|  
|**# zařazování**|Zobrazí celkový počet nezdařených pokusů o argumentů a návratové hodnoty mají byl zařazen ze spravovaného na nespravovaný kód a naopak a od spuštění aplikace. Tento čítač není zvýší, pokud jsou zástupných procedury vložená. (Zástupných procedur jsou zodpovědní za zařazování argumenty a návratové hodnoty). Zástupných procedur jsou obvykle vložená, pokud zařazování režie je malá.|  
|**počet zástupných procedur**|Zobrazí aktuální počet zástupných procedur vytvořený modul common language runtime. Zástupných procedur jsou zodpovědní za zařazování argumenty a návratové hodnoty ze spravovaných do nespravovaných kódu a naopak a během volání zprostředkovatele komunikace s objekty COM nebo platformu vyvolat volání.|  
|**počet TLB exportuje za sekundu**|Vyhrazeno pro budoucí použití.|  
|**počet TLB importy za sekundu**|Vyhrazeno pro budoucí použití.|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>JIT – čítače výkonu  
 Výkon konzoly .NET CLR JIT kategorie zahrnuje čítače, které poskytují informace o kódu, které bylo kompilováno za běhu. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**počet bajtů JITted IL**|Zobrazí celkový počet bajtů (MSIL intermediate language) Microsoft zkompilují kompilátoru v běhu (JIT) od spuštění aplikace. Tento čítač je ekvivalentní **celkový počet bajtů Jitted IL** čítače.|  
|**počet JITted metody**|Zobrazí celkový počet metody kompilována od aplikace spuštěna. Tento čítač nezahrnuje pre kompilována metody.|  
|**% Času v Jit**|Zobrazuje procentuální hodnotu uplynulého času stráví v JIT – kompilace od poslední fáze JIT kompilace. Toto počítadlo je aktualizováno na konci každé fáze JIT kompilace. Fázi kompilace JIT dojde, pokud metoda a jeho závislosti jsou zkompilovat.|  
|**Jitted IL bajtů / s**|Zobrazí počet bajtů MSIL, které jsou kompilována za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Selhání standardní Jit**|Zobrazí počet ve špičce metody, které JIT kompilátoru se nezdařilo zkompilovat od spuštění aplikace. Této chybě může dojít, pokud nelze ověřit MSIL nebo pokud dojde k vnitřní chybě v kompilátoru za běhu.|  
|**Celkový počet bajtů Jitted IL**|Zobrazí celkový počet bajtů MSIL kompilována od aplikace spuštěna. Tento čítač je ekvivalentní **počet bajtů Jitted IL** čítače.|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>Načítání čítače výkonu  
 Výkon konzoly .NET CLR načítání kategorie zahrnuje čítače, které obsahují informace o sestavení, třídy a aplikační domény, které jsou načteny. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**% Času načítání**|Vyhrazeno pro budoucí použití.|  
|**Délka hledání sestavení**|Vyhrazeno pro budoucí použití.|  
|**Bajtů v haldě zavaděče**|Zobrazí aktuální velikost v bajtech paměť poskytnutá zavaděčem třída všechny domény aplikace. Potvrzená paměť je fyzického místa vyhrazeného ve stránkovacím souboru disku.|  
|**Aktuální domén**|Zobrazí aktuální počet načtených v této aplikaci aplikační domény.|  
|**Aktuální sestavení**|Zobrazí aktuální počet načtených sestavení ve všech doménách aplikací v aktuálně běžící aplikaci. Pokud je sestavení načten z několika domén aplikace jako domény jazykově neutrální, tento čítač se navyšuje pouze jednou.|  
|**Načíst aktuální třídy**|Zobrazí aktuální počet načtených ve všech sestaveních třídy.|  
|**Počet domén**|Zobrazí počet domén aplikací načíst za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Počet domén odpojeno**|Zobrazí počet domén aplikací uvolněna za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Počet sestavení**|Zobrazí počet sestavení načíst za sekundu ve všech doménách aplikací. Pokud je sestavení načten z několika domén aplikace jako domény jazykově neutrální, tento čítač se navyšuje pouze jednou.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Načíst počet třídy**|Zobrazí počet třídy načíst za sekundu ve všech sestaveních. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Počet selhání načtení**|Zobrazí počet třídy, které se nepodařilo načíst za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.<br /><br /> Selhání načtení může dojít z mnoha důvodů, například nedostatečné zabezpečení nebo neplatný formát. Podrobnosti najdete v tématu, že že profilace služeb nápovědy.|  
|**Celkový počet selhání načtení**|Zobrazí počet ve špičce tříd, které se nepodařilo načíst od spuštění aplikace.<br /><br /> Selhání načtení může dojít z mnoha důvodů, například nedostatečné zabezpečení nebo neplatný formát. Podrobnosti najdete v tématu, že že profilace služeb nápovědy.|  
|**Celkový počet domén**|Zobrazí počet ve špičce aplikační domény načíst od spuštění aplikace.|  
|**Celkový počet domén odpojeno**|Zobrazí celkový počet domén aplikací odpojení od spuštění aplikace. Pokud domény aplikace je načítání a uvolňování vícekrát, tento čítač zvýší pokaždé, když je odpojen domény aplikace.|  
|**Celkový počet sestavení**|Zobrazí celkový počet načtených sestavení od spuštění aplikace. Pokud je sestavení načten z několika domén aplikace jako domény jazykově neutrální, tento čítač se navyšuje pouze jednou.|  
|**Celkový počet třídy načíst**|Zobrazí kumulativní počet načíst ve všech sestaveních tříd od spuštění aplikace.|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>Čítače výkonu uzamčení a přístup z více vláken  
 Kategorie výkonu konzoly .NET CLR LocksAndThreads zahrnuje čítače, které obsahují informace o spravovaných zámky a vláken, které aplikace používá. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**počet aktuální logické vláken**|Zobrazuje počet aktuální vlákno spravovaných objektů, které v aplikaci. Tento čítač udržuje počet obou spuštěna a zastavena vláken. Hodnota čítače nepředstavuje průměr v čase; Zobrazuje jenom poslední zjištěnou hodnotu.|  
|**počet aktuální fyzické vláken**|Zobrazí počet vláken nativní operačního systému vytvořit a vlastní modul common language runtime tak, aby fungoval jako základní vláken pro objekty spravovaných vláken. Hodnota tohoto čítače nezahrnuje vlákna používaná modulem runtime v jeho interní operace; je podmnožinou vláken v procesu operačního systému.|  
|**počet aktuální rozpoznaný vláken**|Zobrazí počet vláken, které jsou aktuálně rozpoznány modulem runtime. Tyto vlákna jsou přidružená ke odpovídající spravovaných vláken objektu. Modul runtime nevytváří tyto vláken, ale budou mít alespoň jednou spustit uvnitř modulu runtime.<br /><br /> Pouze jedinečné vláken jsou sledovány; vláken se stejným ID přístup z více vláken, která znovu modulu runtime nebo jsou vytvořeny po ukončení vlákno se nezapočítávají dvakrát.|  
|**počet celkový rozpoznaný vláken**|Zobrazí celkový počet vláken, která byla rozpoznána modulem runtime od spuštění aplikace. Tyto vlákna jsou přidružená ke odpovídající spravovaných vláken objektu. Modul runtime nevytváří tyto vláken, ale budou mít alespoň jednou spustit uvnitř modulu runtime.<br /><br /> Pouze jedinečné vláken jsou sledovány; vláken se stejným ID přístup z více vláken, která znovu modulu runtime nebo jsou vytvořeny po ukončení vlákno se nezapočítávají dvakrát.|  
|**Míra kolizí za sekundu**|Zobrazí rychlost, jakou pokusí získat spravovaný zámek neúspěšně vláken v modulu runtime.|  
|**Aktuální délka fronty**|Zobrazí celkový počet vláken, které aktuálně čekají na získání zámku spravovaných v aplikaci. Hodnota čítače nepředstavuje průměr v čase; Zobrazí naposledy zjištěnou hodnotu.|  
|**Délka fronty za sekundu**|Zobrazí počet vláken za sekundu, které čekají na získání zámku v aplikaci. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Délka fronty ve špičce**|Zobrazí celkový počet vláken, která čekali získat spravovaný zámek od spuštění aplikace.|  
|**Počet vláken rozpoznaný za sekundu**|Zobrazí počet vláken za sekundu, které byly rozpoznány modulem runtime. Tyto vlákna jsou přidružená ke odpovídající spravovaných vláken objektu. Modul runtime nevytváří tyto vláken, ale budou mít alespoň jednou spustit uvnitř modulu runtime.<br /><br /> Pouze jedinečné vláken jsou sledovány; vláken se stejným ID přístup z více vláken, která znovu modulu runtime nebo jsou vytvořeny po ukončení vlákno se nezapočítávají dvakrát.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Celkový počet kolizí**|Zobrazí celkový počet pokusů, které vláken v modulu runtime Pokusili jste se neúspěšně získat spravovaný zámek.|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>Čítače výkonu paměti  
 Výkon konzoly využívání paměti rozhraním .NET CLR kategorie zahrnuje čítače, které obsahují informace o systému uvolňování paměti. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet bajtů ve všech haldách**|Zobrazí součet **velikost haldy 1. generace**, **velikost haldy 2**, a **velikost haldy velkého objektu** čítače. Tento čítač označuje velikost aktuální paměti přidělené v bajtech na uvolnění paměti haldách.|  
|**# Zpracovává uvolňování paměti**|Zobrazí aktuální počet popisovačů kolekce paměti používá. Kolekce popisovačů paměti jsou popisovače k prostředkům externí modul common language runtime a spravované prostředí.|  
|**Počet úklidů 0**|Zobrazí počet časy, kdy objekty 0. generace (který nejmladší, objekty naposledy přidělené) uklizeny od spuštění aplikace.<br /><br /> Uvolňování paměti generace 0 nastane, když není dostatečná pro uspokojení požadavku na přidělení dostupné paměti v 0. generace. Tento čítač je zvýšena na konci uvolňování 0. generace. Vyšší generace uvolnění obsahuje všechny nižší generace kolekce. Tento čítač je explicitně zvýší, když dojde k uvolnění paměti vyšší generace (generace 1 nebo 2).<br /><br /> Čítač zobrazí naposledy zjištěnou hodnotu. **_Global\_**  hodnota čítače není přesná a je třeba ji ignorovat.|  
|**# 1. generace kolekce**|Zobrazí počet časy, kdy objekty 1. generace uklizeny od spuštění aplikace.<br /><br /> Hodnota čítače je zvýšena na konci generace 1 uvolňování. Vyšší generace uvolnění obsahuje všechny nižší generace kolekce. Tento čítač je explicitně zvýší, když dojde k uvolnění paměti vyšší generaci (2. generace).<br /><br /> Čítač zobrazí naposledy zjištěnou hodnotu. **_Global\_**  hodnota čítače není přesná a je třeba ji ignorovat.|  
|**# Úklidů 2. generace**|Zobrazí počet časy, kdy objekty 2. generace uklizeny od spuštění aplikace. Čítače je zvýšena na konci generace 2 uvolňování paměti (také nazývané úplný uvolnění paměti).<br /><br /> Čítač zobrazí naposledy zjištěnou hodnotu. **_Global\_**  hodnota čítače není přesná a je třeba ji ignorovat.|  
|**# Vyvolané uvolňování paměti**|Zobrazí počet ve špičce počet probíhalo uvolňování paměti z důvodu explicitní volání <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Je dobrým zvykem umožníte uvolňování ladit četnost jeho kolekce.|  
|**počet připojených objektů**|Zobrazí počet definovaného objektů v poslední uvolnění paměti. Vázaný objekt je objekt, který má systém uvolňování nelze přesunout do paměti. Tento čítač sleduje definovaného objekty pouze v haldách, které jsou uvolnění z paměti. Například uvolnění paměti generace 0 způsobí, že výčet definovaného objekty pouze v haldy 0. generace.|  
|**Počet bloků jímky používá**|Zobrazí aktuální počet bloků s synchronizace používá. Bloky synchronizace jsou jednotlivé objekty datové struktury přidělené pro ukládání informací o synchronizaci. Drží slabé odkazy na spravované objekty a musí být kontrolována modulem garbage collector. Bloky synchronizace nejsou omezeny na ukládání informací o synchronizaci; také můžete uložit metadata zprostředkovatele komunikace s objekty COM. Tento čítač označuje problémy s výkonem se výrazně využívá primitiv synchronizace.|  
|**# Celkový počet potvrzených bajtů**|Zobrazí velikost virtuální paměti, v bajtech, aktuálně potvrzeno modulem garbage collector. Potvrzená paměť je fyzická paměť, pro který bylo vyhrazeno místo ve stránkovacím souboru disku.|  
|**# Celkový počet vyhrazené bajtů**|Zobrazí velikost virtuální paměti, v bajtech aktuálně rezervován uvolňování paměti. Rezervovaná paměť je vyhrazena pro aplikaci virtuální paměti místa, pokud již byly použity žádné disku nebo stránek hlavní paměti.|  
|**Čas**|Zobrazuje procentuální hodnotu uplynulého času stráveného provádění úklidu od posledního cyklu shromažďování uvolňování paměti. Tento čítač udává obvykle práci systémem uvolňování paměti shromažďování a compact jménem aplikace. Toto počítadlo je aktualizováno pouze na konci každé uvolňování paměti. Hodnota čítače nepředstavuje průměr; jeho hodnota odpovídá poslední zjištěné hodnotě.|  
|**Přidělené bajtů za sekundu**|Zobrazí počet bajtů přidělených v haldě kolekce paměti za sekundu. Toto počítadlo je aktualizováno na konci každé uvolňování paměti, ne v každém přidělení. Hodnota čítače nepředstavuje průměr v čase; zobrazí rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Přesun finalizace**|Zobrazí počet objektů uvolňování paměti, které zůstanou platné i po kolekci, protože čekají na Dokončit. Pokud tyto objekty mají odkazy na další objekty, tyto objekty také zachována i po ukončení, ale nejsou zjištěné službou tento čítač. **Povýší finalizace paměti z 0. generace** čítač představuje všechny paměti, která zůstal naživu kvůli dokončení.<br /><br /> Tento čítač není kumulativní; na konci každé uvolňování paměti s počtem přesun se aktualizuje během této konkrétní kolekce. Tento čítač udává zvýšené režii, které aplikace může dojít z důvodu finalizace.|  
|**Velikost haldy 0. generace**|Zobrazí maximální počet bajtů, které mohou být přiděleny v generace 0; Aktuální počet bajtů přidělených v generace 0 neuvádí.<br /><br /> Uvolňování paměti 0. generace dojde, když přidělení od posledního shromažďování přesahují tuto velikost. Velikost generace 0 je přizpůsobená modulem garbage collector a můžou změnit při spuštění aplikace. Na konci 0. generace kolekce generování velikost haldy 0 je 0 bajtů. Tento čítač zobrazuje velikost v bajtech přidělení, které vyvolá další kolekce generace 0 paměti.<br /><br /> Toto počítadlo je aktualizováno na konci uvolňování, ne v každém přidělení.|  
|**0. generace povýší bajty/s**|Zobrazí počet bajtů za sekundu, které povýšené z generace 0 na 1. generace. Paměť se vyzval při jeho odolává uvolnění paměti. Tento čítač je poměrně dlohotrvající objektů vytváří za sekundu, které slouží jako ukazatel.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Velikost haldy 1. generace**|Zobrazí aktuální počet bajtů v generace 1; Tento čítač nezobrazuje maximální velikost 1. generace. Objekty jsou přiděleny přímo v generování; že jsou povýší z předchozí generace 0 kolekce. Toto počítadlo je aktualizováno na konci uvolňování, ne v každém přidělení.|  
|**1. generace povýší bajty/s**|Zobrazí počet bajtů za sekundu, které povýšené z generace 1 na 2. generace. Nejsou v tomto čítači zahrnuté objekty, které jsou povýšit, protože se čeká na Dokončit.<br /><br /> Paměť se vyzval při jeho odolává uvolnění paměti. Nic je povýší z generace 2, protože je nejstarší generování. Tento čítač je velmi dlohotrvající objektů vytváří za sekundu, které slouží jako ukazatel.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Velikost haldy 2. generace**|Zobrazí aktuální počet bajtů v 2. generace. Objekty jsou přiděleny přímo v generování; že jsou povýší z generace 1 během předchozí generace 1 kolekce. Toto počítadlo je aktualizováno na konci uvolňování, ne v každém přidělení.|  
|**Velká velikost objektu haldy**|Zobrazí aktuální velikost v bajtech haldě velký objekt. Objekty, které jsou větší než přibližně 85,000 bajtů, se považují za rozsáhlé objekty modulem garbage collector a jsou přímo přidělené v speciální haldy; jejich nejsou podporovány prostřednictvím generace. Toto počítadlo je aktualizováno na konci uvolňování, ne v každém přidělení.|  
|**ID procesu**|Zobrazí ID procesu instance procesu CLR, která je monitorována.|  
|**Propagovaných finalizace paměti z 0. generace**|Zobrazí počet bajtů paměti, které jsou povýší z generace 0 na 1. generace, protože se čeká na Dokončit. Tento čítač není kumulativní; Zobrazí hodnotu zjištěnými na konci posledního uvolnění paměti.|  
|**Propagovaných paměti od 0. generace**|Zobrazí počet bajtů paměti, které zůstanou platné i po uvolnění paměti a povýšené z generace 0 na 1. generace. Nejsou v tomto čítači zahrnuté objekty, které jsou povýšit, protože se čeká na Dokončit. Tento čítač není kumulativní; Zobrazí hodnotu zjištěnými na konci posledního uvolnění paměti.|  
|**Propagovaných paměti od 1. generace**|Zobrazí počet bajtů paměti, které zůstanou platné i po uvolnění paměti a povýšené z generace 1 na 2. generace. Nejsou v tomto čítači zahrnuté objekty, které jsou povýšit, protože se čeká na Dokončit. Tento čítač není kumulativní; Zobrazí hodnotu zjištěnými na konci posledního uvolnění paměti. Tento čítač nastaven na hodnotu 0, pokud byl poslední uvolňování kolekci generace 0.|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>Čítače výkonu sítě  
 Výkon konzoly .NET CLR sítě kategorie zahrnuje čítače, které obsahují informace o datech, která aplikace odesílá a přijímá přes síť. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**Přijaté bajty**|Kumulativní celkový počet bajtů přijatých všechny <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu. Tato hodnota zahrnuje data a informace protokolu, které není definováno protokolem TCP/IP.|  
|**Odeslané bajty**|Kumulativní počet bajtů odeslaných všechny <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu. Tato hodnota zahrnuje data a informace protokolu, které není definováno protokolem TCP/IP.|  
|**Vytvořeno připojení**|Kumulativní počet <xref:System.Net.Sockets.Socket> objekty pro sokety datového proudu, které byly někdy připojené v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**Přijaté datagramy**|Kumulativní celkový počet přijatých všechny pakety datagram <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**Odeslané datagramy**|Kumulativní celkový počet odeslaných všechny paketů datagram <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**HttpWebRequest – Průměrná doba platnosti**|Průměrný čas na dokončení všech <xref:System.Net.HttpWebRequest> objekty, které skončila v posledního intervalu v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**HttpWebRequest – Průměrná doba fronty**|Průměrná doba na fronty pro všechny <xref:System.Net.HttpWebRequest> objekty, které left fronty v posledního intervalu v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**Vytvořit HttpWebRequests za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty vytvořené za sekundu v rámci <xref:System.AppDomain>.|  
|**HttpWebRequests zařazených do fronty za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty, které byly přidány do fronty za sekundu v rámci <xref:System.AppDomain>.|  
|**Byl zrušen HttpWebRequests za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty, kde aplikace volán <xref:System.Net.HttpWebRequest.Abort%2A> metoda za sekundu v rámci <xref:System.AppDomain>.|  
|**HttpWebRequests se nezdařilo za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty, které přijatý kód stav selhání ze serveru za sekundu v rámci <xref:System.AppDomain>.|  
  
 Existuje několik tříd síťových čítače výkonu, které jsou podporovány:  
  
-   Čítače událostí, které určovat počet časy, kdy došlo k některé události.  
  
-   Data čítače, které měří objem dat. odesílané nebo přijímané.  
  
-   Doba trvání čítače, které měří jak dlouho různé procesy trvat. Časy jsou hodnoceny na objektech v každém intervalu (obvykle v sekundách) po pocházejí z různých stavů.  
  
-   -Interval čítačů, které měří počet objektů, které přijímání konkrétní přechod intervalu (obvykle za sekundu).  
  
 Síťové čítače výkonu pro události zahrnují následující:  
  
-   **Vytvořeno připojení**  
  
-   **Přijaté datagramy**  
  
-   **Odeslané datagramy**  
  
 Tyto čítače výkonu zadejte počty od spuštění procesu. Počty z <xref:System.Net.Sockets.Socket> připojení obsahuje explicitní <xref:System.Net.Sockets.Socket> metoda volá pomocí aplikace pro navázat připojení soketu datového proudu, který byl taky jako vnitřní volání jiné třídy, (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>, a <xref:System.Net.Sockets.TcpClient>, například) k <xref:System.Net.Sockets.Socket> – třída  
  
 Počty pro **přijatých datagramů** a **Odeslané datagramy** zahrnuje datagram pakety odesílané nebo přijímané pomocí explicitní <xref:System.Net.Sockets.Socket> metoda volá aplikací jako dobře interní volání jiná třídy (<xref:System.Net.Sockets.UdpClient>, například) k <xref:System.Net.Sockets.Socket>. Třída. Počty **přijatých datagramů** a **Odeslané datagramy** mohou být využity také k poskytování velmi hrubý míru kolik bajtů byly odesílané nebo přijímané pomocí za předpokladu, že průměrná velikost pro datagram datagramy.  
  
 Síťové čítače výkonu pro data zahrnují následující:  
  
-   **Přijaté bajty**  
  
-   **Odeslané bajty**  
  
 Výše uvedené čítače zadejte počet bajtů od spuštění procesu.  
  
 Existují dva trvání čítače, které měří, jak dlouho trvalo <xref:System.Net.HttpWebRequest> objektů na předání buď jejich celý životní cyklus nebo právě součástí je:  
  
-   **HttpWebRequest – Průměrná doba platnosti**  
  
-   **HttpWebRequest – Průměrná doba fronty**  
  
 Pro **HttpWebRequest – Průměrná životnost** čítače, doba platnosti pro většinu <xref:System.Net.HttpWebRequest> objekty vždy začíná ve chvíli, objekt je vytvořena do okamžiku odpovědi datový proud je uzavřen aplikací. Existují dvě běžné případy:  
  
-   Aplikace nikdy volá-li <xref:System.Net.HttpWebRequest.GetResponse%2A> nebo <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> metody a po dobu životnosti <xref:System.Net.HttpWebRequest> objektu je ignorována.  
  
-   Pokud <xref:System.Net.HttpWebRequest> objektu vyvolává <xref:System.Net.WebException> při volání metody <xref:System.Net.HttpWebRequest.GetResponse%2A> nebo <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metody, životnost skončí, když je vyvolána výjimka. Technicky základního datového proudu odpovědi také zavření v tomto bodě (datového proudu odpovědi vrátil uživateli je ve skutečnosti obsahující kopii datového proudu odpovědi datový proud paměti).  
  
 Existují čtyři čítače, které sledují určité <xref:System.Net.HttpWebRequest> objektu problémy intervalu. Tyto čítače výkonu může pomoci vývojářům aplikací, správce, a až lépe porozumíte pracovníky technické podpory, co <xref:System.Net.HttpWebRequest> objekty dělají. Čítače zahrnují následující:  
  
-   **Vytvořit HttpWebRequests za sekundu**  
  
-   **HttpWebRequests zařazených do fronty za sekundu**  
  
-   **Byl zrušen HttpWebRequests za sekundu**  
  
-   **HttpWebRequests se nezdařilo za sekundu**  
  
 Pro **HttpWebRequests přerušených za sekundu** čítač, interní volání <xref:System.Net.HttpWebRequest.Abort%2A> také počítají. Tyto interní volání jsou obvykle způsobeno vypršení časových limitů, které aplikace může být vhodné měření.  
  
 **HttpWebRequests se nezdařilo za sekundu** čítač obsahuje počet <xref:System.Net.HttpWebRequest> objekty, které přijaly stav selhání kódu ze serveru za sekundu. To znamená, že kód stavu přijatých ze serveru Http na konci požadavku nebyl v rozsahu 200 k 299. Stavové kódy, které jsou zpracovávány a mít za následek novou žádost o (řadu kódy 401 Unauthorized status např.) bude selhat nebo není odmítnuti v závislosti na výsledku opakovaném. Pokud aplikace se zobrazí chybu na základě při opakovaném, tohoto čítače se zvýší.  
  
 Čítače výkonu sítě lze přistupovat a spravovat pomocí <xref:System.Diagnostics.PerformanceCounter> a související třídy v <xref:System.Diagnostics> obor názvů. Síťové čítače výkonu lze také zobrazit s konzolou sledování výkonu systému Windows.  
  
 Čítače výkonu sítě je nutné povolit v konfiguračním souboru má být použit. Všechny síťové čítače výkonu jsou zapnutá nebo vypnutá s jedním nastavením v konfiguračním souboru. Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě. Další informace najdete v tématu [ \<performanceCounter > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Pokud jsou povolené sítě čítače, tato akce vytvoří a aktualizovat na AppDomain a globální čítače výkonu. Pokud je zakázaná, aplikace nebude poskytovat žádné sítě data čítače výkonu.  
  
 Čítače výkonu jsou seskupené do kategorií. Aplikace můžete seznam všech kategorií s následující příklad kódu:  
  
```  
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Síťové čítače výkonu jsou uvedené ve dvou kategoriích:  
  
-   "Modulu .NET CLR sítě" - původní čítače výkonu přináší na rozhraní .NET Framework verze 2 a podporována v rozhraní .NET Framework verze 2 nebo novější.  
  
-   ".NET CLR sítě 4.0.0.0" - všechny výše uvedené soketu čítače plus nové čítače výkonu podporována v rozhraní .NET Framework verze 4 nebo novější. Poskytují tyto nové čítače výkonu informace na <xref:System.Net.HttpWebRequest> objekty.  
  
 Další informace o přístupu k a správy čítače výkonu v aplikaci najdete v tématu [čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>Čítače výkonu zabezpečení  
 Výkon konzoly .NET CLR zabezpečení kategorie zahrnuje čítače, které poskytují informace o zabezpečení kontrol prováděných modul common language runtime pro aplikace. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|**# Odkaz kontroly runtime**|Zobrazí celkový počet zabezpečení přístupu kódu v době propojování kontroluje od spuštění aplikace. Kontroly zabezpečení přístupu kódu v době propojování provede, když volající vyžaduje konkrétní oprávnění v době kompilace za běhu (JIT). Propojování kontrola se provádí jednou za volajícího. Tento počet není určující pro problémy s výkonem závažné; je jenom informativní aktivity zabezpečení systému.|  
|**% Času v RT kontroly**|Zobrazuje procentuální hodnotu uplynulého času stráví provádění runtime kontroly zabezpečení přístupu kódu od posledního vzorku. Toto počítadlo je aktualizováno na konci kontrolu zabezpečení rozhraní .NET Framework. Není v průměru; reprezentuje naposledy zjištěnou hodnotu.|  
|**% Času Sig ověřování**|Vyhrazeno pro budoucí použití.|  
|**Hloubka zásobníku procházení**|Hloubka zásobníku zobrazí během kontroly zabezpečení přístupu kódu poslední modulu runtime. Kontroly zabezpečení přístupu kódu runtime provádí procházení zásobníku. Hodnota čítače nepředstavuje průměr; Zobrazuje jenom poslední zjištěnou hodnotu.|  
|**Kontroluje celkové doby běhu**|Zobrazí celkový počet kód při spuštění přístup kontroly zabezpečení provést od spuštění aplikace. Modul runtime kódu přístup k zabezpečení, které budou provedeny kontroly, když volající požaduje konkrétní oprávnění. Kontrolu běhového prostředí je proveden při každém volání volajícího a prověří aktuální vlákno zásobníku volajícího. Při použití s **provede hloubka zásobníku** čítač, tento čítač označuje snížení výkonu, které dochází v kontrol zabezpečení.|  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 [Běhová profilace](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
