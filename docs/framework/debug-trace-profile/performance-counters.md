---
title: Čítače výkonu v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: 44a5d1cb70d294d720290a4754bb5f5cb47f79a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400020"
---
# <a name="performance-counters-in-the-net-framework"></a>Čítače výkonu v rozhraní .NET Framework

Toto téma obsahuje seznam čítačů výkonu, které naleznete v [programu Sledování výkonu systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  

## <a name="exception-performance-counters"></a>Čítače výkonu výjimek  
 Kategorie výjimek performance console .NET CLR zahrnuje čítače, které poskytují informace o výjimkách vyvolaným aplikací. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**# exceps hozený**|Zobrazuje celkový počet výjimek vyběhl od spuštění aplikace. To zahrnuje výjimky .NET i nespravované výjimky, které jsou převedeny na výjimky rozhraní .NET. Například HRESULT vrácený z nespravovaného kódu je převeden na výjimku ve spravovaném kódu.<br /><br /> Tento čítač obsahuje zpracované i neošetřené výjimky. Výjimky, které jsou znovu vyvolány se počítají znovu.|  
|**Počet Exceps Hozeno / Sec**|Zobrazuje počet výjimek vyvržených za sekundu. To zahrnuje výjimky .NET i nespravované výjimky, které jsou převedeny na výjimky rozhraní .NET. Například HRESULT vrácený z nespravovaného kódu je převeden na výjimku ve spravovaném kódu.<br /><br /> Tento čítač obsahuje zpracované i neošetřené výjimky. Není to průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku. Tento čítač je indikátorem potenciální problémy s výkonem, pokud jsou vyvolány velké (>100s) počet výjimek.|  
|**Počet filtrů / s**|Zobrazí počet filtrů výjimek rozhraní .NET provedených za sekundu. Filtr výjimek vyhodnocuje bez ohledu na to, zda je výjimka zpracována.<br /><br /> Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Počet finallys / Sec**|Zobrazuje počet spouštěných bloků finally za sekundu. Finally blok je zaručeno, že bude proveden bez ohledu na to, jak byl ukončen blok try.  Počítají se pouze bloky finally provedené pro výjimku; finally bloky na normální cesty kódu nejsou počítány do tohoto čítače.<br /><br /> Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Hod na hloubku úlovku / s**|Zobrazuje počet projetých rámců zásobníku z rámce, který vyvolal výjimku, do rámce, který výjimku zpracoval, za sekundu. Tento čítač se při zadání obslužné rutiny výjimky resetuje na nulu, takže vnořené výjimky zobrazují hloubku zásobníku obslužné rutiny obslužné rutiny.<br /><br /> Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  

## <a name="interop-performance-counters"></a>Čítače výkonu Interop  
 Kategorie Performance console .NET CLR Interop obsahuje čítače, které poskytují informace o interakci aplikace s komponentami modelu COM, službami modelu COM+ a externími knihovnami typů. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet CCWs**|Zobrazí aktuální počet výtažků s voláním COM (CCWs). CCW je proxy server pro spravovaný objekt odkazovaný z nespravovaného klienta COM. Tento čítač označuje počet spravovaných objektů, na které odkazuje nespravovaný kód COM.|  
|**Počet zařazování**|Zobrazuje celkový počet argumentů a vrácených hodnot, které byly od spuštění aplikace zařazeny ze spravovaného na nespravovaný kód a naopak. Tento čítač není inkremented, pokud jsou vloženy. (Zástupné procedury jsou zodpovědné za zařazování argumenty a vrácené hodnoty). Zástupné procedury jsou obvykle vloženy, pokud je režie zařazování malá.|  
|**Počet Útržků**|Zobrazuje aktuální počet zástupných procedur vytvořených běžným jazykem. Zástupné procedury jsou zodpovědné za zařazování argumentů a návratové hodnoty ze spravovaného do nespravovaného kódu a naopak během volání interop com nebo volání platformy vyvolat.|  
|**Počet exportů TLB / sec**|Vyhrazeno pro budoucí použití.|  
|**Počet importů TLB / sec**|Vyhrazeno pro budoucí použití.|  

## <a name="jit-performance-counters"></a>JIT – čítače výkonu  
 Kategorie Performance console .NET CLR JIT obsahuje čítače, které poskytují informace o kódu, který byl kompilován JIT. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet IL Bytes JITted**|Zobrazuje celkový počet bajtů středního jazyka Microsoft (MSIL) zkompilovaných kompilátorem just-in-time (JIT) od spuštění aplikace. Tento čítač je ekvivalentní **celkové # čítače JITTED bajty IL.**|  
|**Počet metod JITted**|Zobrazí celkový počet metod, které jit zkompiloval od spuštění aplikace. Tento čítač neobsahuje metody zkompilované předem JIT.|  
|**% Čas v Jit**|Zobrazuje procento uplynulého času stráveného v kompilaci JIT od poslední fáze kompilace JIT. Tento čítač je aktualizován na konci každé fáze kompilace JIT. Fáze kompilace JIT dochází při zkompilování metody a její závislosti.|  
|**IL Bajty Jitted / s**|Zobrazuje počet bajtů MSIL, které jsou kompilovány JIT za sekundu. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Standardní selhání Jit**|Zobrazuje maximální počet metod, které kompilátor JIT nezkompiluje od spuštění aplikace. K této chybě může dojít, pokud msil nelze ověřit nebo pokud je vnitřní chyba v kompilátoru JIT.|  
|**Celkový počet počet JItted ů IL bajtů**|Zobrazí celkový počet bajtů MSIL JIT zkompilovaných od spuštění aplikace. Tento čítač je ekvivalentní **# čítače JITted bajtů IL.**|  

## <a name="loading-performance-counters"></a>Čítače výkonu načítání  
 Kategorie načítání performance console .NET CLR zahrnuje čítače, které poskytují informace o načítaných sestaveních, třídách a aplikačních doménách. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**% načítání času**|Vyhrazeno pro budoucí použití.|  
|**Délka hledání sestavení**|Vyhrazeno pro budoucí použití.|  
|**Bajty v haldě zavaděče**|Zobrazuje aktuální velikost paměti potvrzené zavaděčem třídy ve všech aplikačních doménách v bajtech. Potvrzená paměť je fyzické místo vyhrazené v stránkovacím souboru disku.|  
|**Aktuální domény aplikací**|Zobrazí aktuální počet aplikačních domén načtených v této aplikaci.|  
|**Aktuální sestavení**|Zobrazuje aktuální počet sestavení načtených ve všech aplikačních doménách v aktuálně spuštěné aplikaci. Pokud je sestavení načteno jako neutrální z domény z více aplikačních domén, bude tento čítač rozšířen pouze jednou.|  
|**Aktuální načtené třídy**|Zobrazí aktuální počet tříd načtených ve všech sestaveních.|  
|**Rychlost doméně aplikací**|Zobrazuje počet načtených aplikačních domén za sekundu. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Rychlost uvolněných doméně aplikací**|Zobrazuje počet aplikačních domén uvolněných za sekundu. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Rychlost sestavení**|Zobrazuje počet sestavení načtených za sekundu ve všech aplikačních doménách. Pokud je sestavení načteno jako neutrální z domény z více aplikačních domén, bude tento čítač rozšířen pouze jednou.<br /><br /> Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Míra načtených tříd**|Zobrazuje počet tříd načtených za sekundu ve všech sestaveních. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Míra selhání zatížení**|Zobrazuje počet tříd, které se nepodařilo načíst za sekundu. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.<br /><br /> K selhání zatížení může dojít z mnoha důvodů, například nedostatečné zabezpečení nebo neplatný formát. Podrobnosti naleznete v nápovědě ke službám profilování.|  
|**Celkový počet selhání zatížení**|Zobrazuje maximální počet tříd, které se od spuštění aplikace nepodařilo načíst.<br /><br /> K selhání zatížení může dojít z mnoha důvodů, například nedostatečné zabezpečení nebo neplatný formát. Podrobnosti naleznete v nápovědě ke službám profilování.|  
|**Celkový počet domén aplikace**|Zobrazuje maximální počet aplikačních domén načtených od spuštění aplikace.|  
|**Celkový počet uvolněných doméně aplikací**|Zobrazuje celkový počet aplikačních domén uvolněných od spuštění aplikace. Pokud je doména aplikace načtena a uvolněna vícekrát, tento čítač se zvětší při každém uvolnění domény aplikace.|  
|**Celkový počet sestavení**|Zobrazí celkový počet sestavení načtených od spuštění aplikace. Pokud je sestavení načteno jako neutrální z domény z více aplikačních domén, bude tento čítač rozšířen pouze jednou.|  
|**Celkový počet načtených tříd**|Zobrazí kumulativní počet tříd načtených ve všech sestaveních od spuštění aplikace.|  

## <a name="lock-and-thread-performance-counters"></a>Čítače výkonu zámku a vlákna  
 Výkon konzoly .NET CLR ZámkyAndThreads kategorie obsahuje čítače, které poskytují informace o spravované zámky a podprocesy, které používá aplikace. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet aktuálních logických vláken**|Zobrazuje počet aktuálních objektů spravovaného podprocesu v aplikaci. Tento čítač udržuje počet spuštěných i zastavených vláken. Tento čítač není průměr v průběhu času; zobrazí pouze poslední zjištěnou hodnotu.|  
|**Počet aktuálních fyzických vláken**|Zobrazuje počet nativních podprocesů operačního systému vytvořených a vlastněných běžným jazykem, které mají sloužit jako základní vlákna pro objekty spravovaných vláken. Hodnota tohoto čítače nezahrnuje vlákna používaná za běhu v jeho vnitřníoperace; jedná se o podmnožinu vláken v procesu operačního systému.|  
|**Počet aktuálních rozpoznaných vláken**|Zobrazuje počet podprocesů, které jsou aktuálně rozpoznány za běhu. Tato vlákna jsou přidružena k odpovídajícímu objektu spravovaného vlákna. Runtime nevytváří tato vlákna, ale mají spustit uvnitř runtime alespoň jednou.<br /><br /> Jsou sledovány pouze jedinečné vlákna; vlákna se stejným ID vlákna, které znovu zadejte runtime nebo jsou znovu vytvořeny po ukončení podprocesu se nepočítají dvakrát.|  
|**Počet celkových rozpoznaných vláken**|Zobrazuje celkový počet podprocesů, které byly rozpoznány za běhu od spuštění aplikace. Tato vlákna jsou přidružena k odpovídajícímu objektu spravovaného vlákna. Runtime nevytváří tato vlákna, ale mají spustit uvnitř runtime alespoň jednou.<br /><br /> Jsou sledovány pouze jedinečné vlákna; vlákna se stejným ID vlákna, které znovu zadejte runtime nebo jsou znovu vytvořeny po ukončení podprocesu se nepočítají dvakrát.|  
|**Míra tvrzení / s**|Zobrazuje rychlost, jakou se vlákna v běhu pokoušejí neúspěšně získat spravovaný zámek.|  
|**Aktuální délka fronty**|Zobrazuje celkový počet podprocesů, které aktuálně čekají na získání spravovaného zámku v aplikaci. Tento čítač není průměr v průběhu času; zobrazí poslední pozorovanou hodnotu.|  
|**Délka fronty / s**|Zobrazuje počet podprocesů za sekundu, které čekají na získání zámku v aplikaci. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Špička délky fronty**|Zobrazuje celkový počet podprocesů, které čekaly na získání spravovaného zámku od spuštění aplikace.|  
|**rychlost rozpoznaných vláken / sec**|Zobrazuje počet vláken za sekundu, které byly rozpoznány za běhu. Tato vlákna jsou přidružena k odpovídajícímu objektu spravovaného vlákna. Runtime nevytváří tato vlákna, ale mají spustit uvnitř runtime alespoň jednou.<br /><br /> Jsou sledovány pouze jedinečné vlákna; vlákna se stejným ID vlákna, které znovu zadejte runtime nebo jsou znovu vytvořeny po ukončení podprocesu se nepočítají dvakrát.<br /><br /> Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Celkový počet tvrzení**|Zobrazuje celkový počet pokusů vláken v běhu o neúspěšně získat spravovaný zámek.|  

## <a name="memory-performance-counters"></a>Čítače výkonu paměti  
 Kategorie paměti Performance console .NET CLR obsahuje čítače, které poskytují informace o systému uvolňování paměti. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**# Bytes ve všech hromadách**|Zobrazí součet **čítačů Gen 1 Haldy**, **Gen 2 Haldy**a Velikost **haldy velkého objektu.** Tento čítač označuje aktuální paměť přidělenou v bajtů na hromadách uvolňování paměti.|  
|**# Gc úchyty**|Zobrazí aktuální počet popisovačů uvolňování paměti, které jsou používány. Popisovače uvolňování paměti jsou popisovače pro prostředky mimo běžný jazyk runtime a spravované prostředí.|  
|**# Gen 0 Sbírky**|Zobrazuje počet, kolikrát jsou objekty generace 0 (tj. nejmladší, naposledy přidělené objekty) uvolněny od spuštění aplikace.<br /><br /> Uvolnění paměti generace 0 dochází, když dostupná paměť v generaci 0 není dostatečná pro splnění požadavku na přidělení. Tento čítač je přírůstek na konci generace 0 uvolňování paměti. Vyšší generace uvolňování paměti zahrnují všechny kolekce nižší generace. Tento čítač je explicitně zvýší, když dojde k vyšší generace (generace 1 nebo 2) uvolňování paměti.<br /><br /> Tento čítač zobrazuje poslední pozorovanou hodnotu. Hodnota **\_ _Global** čítače není přesná a měla by být ignorována.|  
|**# Gen 1 Sbírky**|Zobrazuje počet, kolikrát jsou objekty generace 1 uvolněny od spuštění aplikace.<br /><br /> Čítač se zintáčí na konci uvolnění paměti generace 1. Vyšší generace uvolňování paměti zahrnují všechny kolekce nižší generace. Tento čítač je explicitně zvýší, když dojde k uvolnění paměti vyšší generace (generace 2).<br /><br /> Tento čítač zobrazuje poslední pozorovanou hodnotu. Hodnota **\_ _Global** čítače není přesná a měla by být ignorována.|  
|**# Gen 2 Sbírky**|Zobrazuje počet, kolikrát jsou objekty generace 2 uvolněny od spuštění aplikace. Čítač se zintádne na konci uvolnění paměti generace 2 (také se nazývá úplné uvolnění paměti).<br /><br /> Tento čítač zobrazuje poslední pozorovanou hodnotu. Hodnota **\_ _Global** čítače není přesná a měla by být ignorována.|  
|**# Indukované GC**|Zobrazuje maximální počet případů, kdy bylo provedeno uvolnění <xref:System.GC.Collect%2A?displayProperty=nameWithType>paměti z důvodu explicitního volání aplikace . Je vhodné nechat uvolňování naladit frekvenci jeho kolekcí.|  
|**Počet připnutých objektů**|Zobrazuje počet připnutých objektů, ke kterým došlo v posledním uvolnění paměti. Připnutý objekt je objekt, který systém uvolňování paměti nelze přesunout v paměti. Tento čítač sleduje připnuté objekty pouze v hromadách, které jsou uvolněné. Například uvolnění paměti generace 0 způsobí výčet připnutých objektů pouze v haldě generace 0.|  
|**Počet dřezových bloků v provozu**|Zobrazí aktuální počet použitelných synchronizačních bloků. Bloky synchronizace jsou datové struktury pro jeden objekt přidělené pro ukládání informací o synchronizaci. Uchovávají slabé odkazy na spravované objekty a musí být zkontrolovány systémem uvolňování paměti. Synchronizační bloky nejsou omezeny na ukládání informací o synchronizaci; mohou také ukládat metadata interop com. Tento čítač označuje problémy s výkonem s intenzivní použití synchronizace primitiv.|  
|**# Celkem potvrzených bajtů**|Zobrazuje velikost virtuální paměti v bajtech aktuálně potvrzených systémem uvolňování paměti. Potvrzená paměť je fyzická paměť, pro kterou bylo v stránkovacím souboru disku vyhrazeno místo.|  
|**# Celkem rezervované bajty**|Zobrazuje velikost virtuální paměti v bajtech, aktuálně rezervované systémem uvolňování paměti. Vyhrazená paměť je místo virtuální paměti vyhrazené pro aplikaci, pokud nebyly použity žádné diskové nebo hlavní paměti.|  
|**% času v GC**|Zobrazuje procento uplynulého času stráveného prováděním uvolňování paměti od posledního cyklu uvolňování paměti. Tento čítač obvykle označuje práci provedenou systémem uvolňování paměti shromažďovat a kompaktní paměti jménem aplikace. Tento čítač je aktualizován pouze na konci každé uvolnění paměti. Tento čítač není průměr; jeho hodnota odráží poslední zjištěnou hodnotu.|  
|**Přidělené bajty za sekundu**|Zobrazuje počet bajtů za sekundu přidělených na haldě uvolňování paměti. Tento čítač je aktualizován na konci každé uvolnění paměti, nikoli při každém přidělení. Tento čítač není průměr v průběhu času; zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorku.|  
|**Dokončení Survivors**|Zobrazí počet objektů uvolňování paměti, které přežijí kolekci, protože čekají na dokončení. Pokud tyto objekty obsahovat odkazy na jiné objekty, tyto objekty také přežít, ale nejsou počítány tímto čítač. **Povýšenfinalizace paměti z Gen 0** čítač představuje všechny paměti, které přežily z důvodu dokončení.<br /><br /> Tento čítač není kumulativní; je aktualizován na konci každé uvolňování paměti s počtem přeživších během této konkrétní kolekce pouze. Tento čítač označuje dodatečné režie, které může aplikace vzniknout z důvodu dokončení.|  
|**Velikost haldy Gen 0**|Zobrazí maximální počet bajtů, které mohou být přiděleny v generaci 0; neoznačuje aktuální počet bajtů přidělených v generaci 0.<br /><br /> Uvolnění paměti generace 0 dochází, když přidělení od poslední kolekce překročit tuto velikost. Velikost generace 0 je naladěn a systém uvolňování paměti se může během provádění aplikace změnit. Na konci generace 0 kolekce velikost generace 0 haldy je 0 bajtů. Tento čítač zobrazuje velikost v bajtů přidělení, která vyvolá další generace 0 uvolňování paměti.<br /><br /> Tento čítač je aktualizován na konci uvolňování paměti, nikoli při každém přidělení.|  
|**Gen 0 Povýšenbajtů/s**|Zobrazí bajty za sekundu, které jsou povýšeny z generace 0 na generaci 1. Paměť je povýšen, když přežije uvolnění paměti. Tento čítač je indikátorem relativně dlouho trvající objekty vytvářené za sekundu.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorkování.|  
|**Velikost haldy Gen 1**|Zobrazuje aktuální počet bajtů v generaci 1; tento čítač nezobrazuje maximální velikost generace 1. Objekty nejsou přímo přiděleny v této generaci; jsou povýšeni z předchozí generace 0 uvolnění paměti. Tento čítač je aktualizován na konci uvolňování paměti, nikoli při každém přidělení.|  
|**Gen 1 Povýšenbajtů/s**|Zobrazí bajty za sekundu, které jsou povýšeny z generace 1 na generaci 2. Objekty, které jsou povýšenpouze proto, že čekají na dokončení nejsou zahrnuty v tomto čítači.<br /><br /> Paměť je povýšen, když přežije uvolnění paměti. Nic není podporováno z generace 2, protože se jedná o nejstarší generaci. Tento čítač je indikátorem velmi dlouho trvající objekty vytvářeny za sekundu.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami pozorovanými v posledních dvou vzorcích děleno dobou trvání intervalu vzorkování.|  
|**Velikost haldy Gen 2**|Zobrazuje aktuální počet bajtů v generaci 2. Objekty nejsou přímo přiděleny v této generaci; jsou povýšenz generace 1 během předchozí generace 1 uvolnění paměti. Tento čítač je aktualizován na konci uvolňování paměti, nikoli při každém přidělení.|  
|**Velikost haldy velkých objektů**|Zobrazí aktuální velikost haldy velkého objektu v bajtech. Objekty, které jsou větší než přibližně 85 000 bajtů jsou považovány za velké objekty systémem uvolňování paměti a jsou přímo přiděleny ve zvláštní haldě. Nejsou podporovány po generace. Tento čítač je aktualizován na konci uvolňování paměti, nikoli při každém přidělení.|  
|**ID procesu**|Zobrazí ID procesu instance procesu CLR, která je monitorována.|  
|**Povýšen finalizace-Paměť z Gen 0**|Zobrazí bajty paměti, které jsou povýšeny z generace 0 na generaci 1 pouze proto, že čekají na dokončení. Tento čítač není kumulativní; zobrazí hodnotu zjištěnou na konci poslední ho shromažďování paměti.|  
|**Povýšenpaměť z Gen 0**|Zobrazí bajty paměti, které přežijí uvolňování paměti a jsou povýšeny z generace 0 na generaci 1. Objekty, které jsou povýšenpouze proto, že čekají na dokončení nejsou zahrnuty v tomto čítači. Tento čítač není kumulativní; zobrazí hodnotu zjištěnou na konci poslední ho shromažďování paměti.|  
|**Povýšenpaměť z Gen 1**|Zobrazí bajty paměti, které přežijí uvolňování paměti a jsou povýšeny z generace 1 na generaci 2. Objekty, které jsou povýšenpouze proto, že čekají na dokončení nejsou zahrnuty v tomto čítači. Tento čítač není kumulativní; zobrazí hodnotu zjištěnou na konci poslední ho shromažďování paměti. Tento čítač je obnovena na 0, pokud poslední uvolnění paměti byla pouze generace 0 kolekce.|  

## <a name="networking-performance-counters"></a>Čítače výkonu sítě  

Kategorie Performance console .NET CLR Networking obsahuje čítače, které poskytují informace o datech, která aplikace odesílá a přijímá v síti. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Přijaté bajty**|Kumulativní celkový počet bajtů přijatých všemi <xref:System.Net.Sockets.Socket> objekty od <xref:System.AppDomain> zahájení procesu. Toto číslo zahrnuje data a všechny informace protokolu, které nejsou definovány protokolem TCP/IP.|  
|**Odeslané bajty**|Kumulativní počet bajtů odeslaných <xref:System.Net.Sockets.Socket> všemi <xref:System.AppDomain> objekty od zahájení procesu. Toto číslo zahrnuje data a všechny informace protokolu, které nejsou definovány protokolem TCP/IP.|  
|**Navázáná připojení**|Kumulativní celkový počet <xref:System.Net.Sockets.Socket> objektů pro sokety datového <xref:System.AppDomain> proudu, které byly někdy připojeny v rámci od spuštění procesu.|  
|**Přijaté datagramy**|Kumulativní celkový počet paketů datagramu <xref:System.Net.Sockets.Socket> přijatých <xref:System.AppDomain> všemi objekty od zahájení procesu.|  
|**Odeslané datagramy**|Kumulativní celkový počet paketů datagramu <xref:System.Net.Sockets.Socket> odeslaných <xref:System.AppDomain> všemi objekty od zahájení procesu.|  
|**Průměrná životnost httpwebrequest**|Průměrná doba do <xref:System.Net.HttpWebRequest> dokončení pro všechny objekty, <xref:System.AppDomain> které skončily v posledním intervalu od zahájení procesu.|  
|**Průměrná doba čekání httpWebRequest**|Průměrná doba čekání na <xref:System.Net.HttpWebRequest> frontě pro všechny objekty, <xref:System.AppDomain> které opustily frontu v posledním intervalu od spuštění procesu.|  
|**HttpWebRequests Vytvořeno/s**|Počet objektů <xref:System.Net.HttpWebRequest> vytvořených za <xref:System.AppDomain>sekundu v rámci .|  
|**HttpWebRequests ve frontě/s**|Počet <xref:System.Net.HttpWebRequest> objektů, které byly přidány do fronty <xref:System.AppDomain>za sekundu v rámci .|  
|**HttpWebRequests přerušeno/s**|Počet <xref:System.Net.HttpWebRequest> objektů, kde aplikace <xref:System.Net.HttpWebRequest.Abort%2A> volala metodu <xref:System.AppDomain>za sekundu v rámci .|  
|**HttpWebRequests se nezdařilo/s**|Počet <xref:System.Net.HttpWebRequest> objektů, které obdržely neúspěšný stavový kód <xref:System.AppDomain>ze serveru za sekundu v rámci .|  
  
 Existuje několik tříd čítačů výkonu sítě podporovány:  
  
- Čítače událostí, které měří počet, kolikrát došlo k určité události.  
  
- Čítače dat, které měří množství odeslaných nebo přijatých dat.  
  
- Čítače doby trvání, které měří, jak dlouho trvá různé procesy. Časy jsou měřeny na objekty každý interval (obvykle v sekundách) poté, co pocházejí z různých stavů.  
  
- Čítače intervalů, které měří počet objektů, které provádějí určitý přechod za interval (obvykle za sekundu).  
  
Čítače výkonu sítě pro události zahrnují následující:  
  
- **Navázáná připojení**  
  
- **Přijaté datagramy**  
  
- **Odeslané datagramy**  
  
 Tyto čítače výkonu poskytují počty od spuštění procesu. Počty <xref:System.Net.Sockets.Socket> navázání připojení <xref:System.Net.Sockets.Socket> zahrnují explicitní volání metod aplikací pro připojení soketu datového proudu,<xref:System.Net.HttpWebRequest> <xref:System.Net.FtpWebRequest>které <xref:System.Net.WebClient>bylo <xref:System.Net.Sockets.TcpClient>vytvořeno, a <xref:System.Net.Sockets.Socket> interní volání provedená jinými třídami ( , , a , například) do třídy.  
  
 Počty **přijatých datagramů** a **odeslaných datagramů** zahrnují pakety datagramu odeslané nebo přijaté pomocí explicitních <xref:System.Net.Sockets.Socket> volání metod aplikací a interní volání jiných tříd (<xref:System.Net.Sockets.UdpClient>například) do <xref:System.Net.Sockets.Socket>. Třída. Počty **přijatých datagramů** a **odeslaných datagramů** mohou být také použity k poskytnutí velmi hrubé míry toho, kolik bajtů bylo odesláno nebo přijato pomocí datagramů za předpokladu, že je pro datagram průměrná velikost.  
  
 Čítače výkonu sítě pro data zahrnují následující:  
  
- **Přijaté bajty**  
  
- **Odeslané bajty**  
  
 Výše uvedené čítače poskytují počty bajtů od zahájení procesu.  
  
 Existují dva čítače doby trvání, <xref:System.Net.HttpWebRequest> které měří, jak dlouho trvalo, než objekty prošly celým jejich životním cyklem nebo jen jeho částí:  
  
- **Průměrná životnost httpwebrequest**  
  
- **Průměrná doba čekání httpWebRequest**  
  
 Pro **čítač Průměrná životnost httpwebrequest** životnost životnost většiny <xref:System.Net.HttpWebRequest> objektů vždy začíná čas, který je vytvořen objekt až do doby, kdy je datový proud odezvy uzavřen aplikací. Existují dva neobvyklé případy:  
  
- Pokud aplikace nikdy <xref:System.Net.HttpWebRequest.GetResponse%2A> volá <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> metody or, je <xref:System.Net.HttpWebRequest> životnost objektu ignorována.  
  
- Pokud <xref:System.Net.HttpWebRequest> objekt vyvolá <xref:System.Net.WebException> při volání <xref:System.Net.HttpWebRequest.GetResponse%2A> <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metody nebo, životnost končí při vyvolání výjimky. Technicky je základní datový proud odpovědi také uzavřen v tomto okamžiku (datový proud odpovědi vrácený uživateli je skutečně datový proud paměti obsahující kopii datového proudu odpovědí).  
  
 Existují čtyři čítače, které sledují určité <xref:System.Net.HttpWebRequest> problémy s objekty za interval. Tyto čítače výkonu mohou pomoci vývojářům aplikací, <xref:System.Net.HttpWebRequest> správcům a pracovníkům podpory lépe pochopit, co objekty dělají. Čítače zahrnují následující:  
  
- **HttpWebRequests Vytvořeno/s**  
  
- **HttpWebRequests ve frontě/s**  
  
- **HttpWebRequests přerušeno/s**  
  
- **HttpWebRequests se nezdařilo/s**  
  
 Pro **čítač HttpWebRequests Aborted/sec** se <xref:System.Net.HttpWebRequest.Abort%2A> také počítají interní volání. Tato interní volání jsou obvykle způsobena časovými časy, které aplikace může chtít měřit.  
  
 Čítač **HttpWebRequests Failed/sec** obsahuje počet <xref:System.Net.HttpWebRequest> objektů, které obdržely neúspěšný stavový kód ze serveru za sekundu. To znamená, že stavový kód přijatý ze serveru Http na konci požadavku nebyl v rozsahu mezi 200 a 299. Stavové kódy, které jsou zpracovány a výsledkem nový požadavek (mnoho z 401 Neoprávněných stavových kódů, například) se nezdaří nebo neselže na základě výsledku opakování. Pokud aplikace by vidět chybu na základě opakování, pak tento čítač je přírůstek.  
  
 Čítače výkonu sítě lze přistupovat a spravovat pomocí <xref:System.Diagnostics.PerformanceCounter> a související třídy v oboru <xref:System.Diagnostics> názvů. Čítače výkonu sítě lze také zobrazit pomocí konzoly sledování výkonu systému Windows.  
  
 Čítače výkonu sítě je třeba povolit v konfiguračním souboru, který má být použit. Všechny čítače výkonu sítě jsou povoleny nebo zakázány s jediným nastavením v konfiguračním souboru. Jednotlivé čítače výkonu sítě nelze povolit ani zakázat. Další informace naleznete v [ \<tématu performanceCounter> Element (Nastavení sítě)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Pokud jsou povoleny čítače sítě, vytvoří se a aktualizuje čítače výkonu pro vlastní i globální. Pokud je zakázáno, aplikace nebude poskytovat žádné sítě výkon čítač dat.  
  
 Čítače výkonu jsou seskupeny do kategorií. Aplikace může vypsat všechny kategorie s následujícím ukázkovým kódem:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Čítače výkonu sítě jsou uvedeny ve dvou kategoriích:  
  
- ".NET CLR Networking" - původní čítače výkonu zavedené v rozhraní .NET Framework verze 2 a podporované v rozhraní .NET Framework verze 2 a novější.  
  
- ".NET CLR Networking 4.0.0.0" - Všechny výše uvedené čítače soketů plus nové čítače výkonu podporované v rozhraní .NET Framework verze 4 a novější. Tyto nové čítače <xref:System.Net.HttpWebRequest> poskytují informace o výkonu objektů.  
  
 Další informace o přístupu a správě čítačů výkonu v aplikaci naleznete v tématu [Čítače výkonu](performance-counters.md).  

## <a name="security-performance-counters"></a>Čítače výkonu zabezpečení  
 Kategorie zabezpečení Performance console .NET CLR obsahuje čítače, které poskytují informace o kontrolách zabezpečení, které provádí běžný jazyk runtime pro aplikaci. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**# Kontrola času spojení**|Zobrazuje celkový počet kontrol zabezpečení přístupu k kódu v době propojení od spuštění aplikace. Kontroly zabezpečení přístupu k kódu v době propojení jsou prováděny, když volající požaduje konkrétní oprávnění v době kompilace za čase (JIT). Kontrola doby propojení se provádí jednou na volajícího. Tento počet nesvědčí o závažných problémech s výkonem. pouze svědčí o činnosti bezpečnostního systému.|  
|**% času v kontrolách RT**|Zobrazuje procento uplynulého času stráveného prováděním kontrol zabezpečení přístupu kódu runtime od poslední ukázky. Tento čítač je aktualizován na konci kontroly zabezpečení rozhraní .NET Framework. Není to průměr; představuje poslední pozorovanou hodnotu.|  
|**% čas sig ověřování**|Vyhrazeno pro budoucí použití.|  
|**Hloubka procházení zásobníku**|Zobrazí hloubku zásobníku během poslední kontroly zabezpečení přístupu kódu runtime. Kontroly zabezpečení přístupu kódu runtime jsou prováděny procházením zásobníku. Tento čítač není průměr; zobrazí pouze poslední zjištěnou hodnotu.|  
|**Celkové kontroly za běhu**|Zobrazuje celkový počet kontrol zabezpečení přístupu kódu runtime provedených od spuštění aplikace. Kontroly zabezpečení přístupu kódu runtime jsou prováděny, když volající vyžaduje konkrétní oprávnění. Kontrola za běhu se provádí při každém volání volajícím a zkontroluje aktuální zásobník vlákna volajícího. Při použití s **čítač hloubka procházení zásobníku** tento čítač označuje snížení výkonu, ke kterému dochází pro kontroly zabezpečení.|  
  
## <a name="see-also"></a>Viz také

- [Čítače výkonu](performance-counters.md)
- [Běhová profilace](runtime-profiling.md)
