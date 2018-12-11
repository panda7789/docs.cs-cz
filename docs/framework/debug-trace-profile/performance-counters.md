---
title: Čítače výkonu v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39472662cd26799e9adbbbd199129e2c83dd0d93
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155363"
---
# <a name="performance-counters-in-the-net-framework"></a>Čítače výkonu v rozhraní .NET Framework
Toto téma obsahuje seznam čítačů výkonu najdete v [Windows Performance Monitor](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  
  
-   [Čítače výkonu výjimky](#exception)  
  
-   [Interoperabilita – čítače výkonu](#interop)  
  
-   [JIT – čítače výkonu](#jit)  
  
-   [Načtení čítačů výkonu](#loading)  
  
-   [Uzamčení a vlákna čítače výkonu](#lockthread)  
  
-   [Čítače výkonu paměti](#memory)  
  
-   [Čítače výkonu sítě](#networking)  
  
-   [Čítače výkonu zabezpečení](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>Čítače výkonu výjimky  
 Kategorii Performance konzoly výjimky .NET CLR obsahuje čítače, které obsahují informace o výjimky vyvolané aplikací. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet vyvolaných výjimek**|Zobrazí celkový počet výjimek vyvolaných od spuštění aplikace. Jedná se o výjimky .NET a nespravovaných výjimek převedených na výjimky .NET. Například HRESULT vrácená z nespravovaného kódu je převedena na výjimku ve spravovaném kódu.<br /><br /> Tento čítač zahrnuje zpracovaných a nezpracovaných výjimek. Výjimky, které jsou znovu vyvolány se počítají znovu.|  
|**počet výjimek vyvolaných za sekundu**|Zobrazí počet výjimek vyvolaných za sekundu. Jedná se o výjimky .NET a nespravovaných výjimek převedených na výjimky .NET. Například HRESULT vrácená z nespravovaného kódu je převedena na výjimku ve spravovaném kódu.<br /><br /> Tento čítač zahrnuje zpracovaných a nezpracovaných výjimek. To nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování. Tento čítač je indikátor potenciální problémy s výkonem, pokud velké (> 100s) počet výjimek jsou vyvolány.|  
|**počet filtrů za sekundu**|Zobrazuje počet filtrů výjimek .NET spuštěných za sekundu. Filtr výjimek vyhodnocuje, bez ohledu na to, zda výjimka je ošetřena.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**počet bezpodmínečných bloků za sekundu**|Zobrazí počet bloky finally za sekundu. A nakonec je zaručeno bloku, který se spustí bez ohledu na to, jak byl ukončen bloku try.  Jenom počítají se nakonec bloky, které jsou spouštěny pro výjimku. Nakonec se nepočítají bloků na cestách normální kódu tímto čítačem.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Vyvolání-zachycení za sekundu**|Zobrazí počet rámců zásobníku procházet z rámce, ve kterém došlo k výjimce na rámec, který zpracovává výjimku, za sekundu. Tento čítač resetuje na nulu, při zadání obslužné rutiny výjimek se proto vnořené výjimky zobrazit hloubka zásobníku obslužnou rutinu.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Interoperabilita – čítače výkonu  
 Kategorii Performance konzoly spolupráce .NET CLR obsahuje čítače, které poskytují informace o interakci aplikace s komponenty modelu COM, služby COM + a externí knihovny typů. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**počet obálek CCW**|Zobrazuje aktuální počet obálek volatelných aplikacemi COM (CCW). Obálka CCW. je proxy server pro spravovaný objekt, na kterou se odkazuje z nespravovaného COM klienta. Tento čítač indikuje počet spravovaných objektů, které odkazuje nespravovaný kód com.|  
|**počet zařazování**|Zobrazí celkový počet pokusů o argumentů a vrácené hodnoty návratových ze spravovaného do nespravovaného kódu a naopak od spuštění aplikace. Hodnota tohoto čítače se zvýší, pokud jsou zástupné procedury vloženy. (Zástupné procedury zodpovídají za zařazování argumentů a vrácených hodnot). Zástupné procedury jsou zpravidla vloženy Pokud je režie zařazování malá.|  
|**počet objektů stub**|Zobrazuje aktuální počet zástupných procedur vytvořených platformou CLR. Zástupné procedury zodpovídají za zařazování argumentů a vrácených hodnot ze spravovaného do nespravovaného kódu a naopak, během volání interop modelu COM nebo platformu vyvolání volání.|  
|**počet exportů TLB za sekundu**|Vyhrazeno pro budoucí použití.|  
|**počet importů TLB za sekundu**|Vyhrazeno pro budoucí použití.|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>JIT – čítače výkonu  
 Kategorii Performance konzoly .NET CLR JIT zahrnuje čítače, které obsahují informace o kódu, který byl zkompilován JIT Kompilátorem. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**počet bajtů IL zpracovaných kompilátorem JIT**|Zobrazí celkový počet bajtů Microsoft intermediate language (MSIL) zkompilovány kompilátorem just-in-time (JIT) od spuštění aplikace. Tento čítač je ekvivalentní **celkový počet bajtů IL zpracovaných kompilátorem JIT** čítače.|  
|**Počet metod zpracovaných kompilátorem JIT**|Zobrazí celkový počet metod zkompilovaný pomocí kompilátoru JIT od aplikace spuštěna. Tento čítač nezahrnuje metody zkompilované JIT předem.|  
|**% Času v překladu za běhu**|Zobrazuje procento času stráveného při kompilaci JIT od poslední fáze kompilace JIT. Tento čítač je aktualizován na konci každé kompilační fáze JIT. Kompilační fáze JIT vyvolá se v případě metody a jeho závislosti jsou zkompilovány.|  
|**Počet bajtů IL zpracovaných kompilátorem JIT za sekundu**|Zobrazuje počet bajtů jazyka MSIL, které jsou zkompilovány JIT za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Standardní selhání kompilátoru Jit**|Zobrazuje nejvyšší počet metod, které se kompilátoru JIT nepodařilo zkompilovat od spuštění aplikace. Takovým selháním může dojít, pokud nemůže být ověřen jazyk MSIL nebo pokud dojde k vnitřní chybě v kompilátoru JIT.|  
|**Celkový počet bajtů IL zpracovaných kompilátorem JIT**|Zobrazí celkový počet bajtů MSIL zkompilovaný pomocí kompilátoru JIT od aplikace spuštěna. Tento čítač je ekvivalentní **počet bajtů IL zpracovaných kompilátorem JIT** čítače.|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>Načtení čítačů výkonu  
 Výkon konzoly .NET CLR načítání kategorie zahrnuje čítače, které obsahují informace o sestavení, třídy a aplikačních doménách, které jsou načteny. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**% Času načítání**|Vyhrazeno pro budoucí použití.|  
|**Délka hledání sestavení**|Vyhrazeno pro budoucí použití.|  
|**Počet bajtů v haldě zaváděcího programu**|Zobrazí aktuální velikost v bajtech paměti potvrzené zaváděcím programem tříd ve všech doménách aplikace. Potvrzená paměť je fyzického místa vyhrazeného ve stránkovacím souboru na disku.|  
|**Aktuální objekty třídy AppDomain**|Zobrazuje aktuální počet domén aplikace načíst v této aplikaci.|  
|**Aktuální sestavení**|Zobrazuje aktuální počet načtených sestavení ve všech doménách aplikace v aktuálně spuštěné aplikaci. Pokud je sestavení zavedeno jako doménově neutrální z více domén aplikace, tento čítač se zvyšuje pouze jednou.|  
|**Aktuálně zavedené třídy**|Zobrazuje aktuální počet tříd, které jsou načteny ve všech sestaveních.|  
|**Frekvence objektů třídy AppDomain**|Zobrazí počet domén aplikace zavedených za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Počet objektů třídy appdomains uvolněných**|Zobrazí počet domén aplikace uvolněných za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Frekvence sestavení**|Zobrazí počet sestavení zavedených za sekundu ve všech doménách aplikace. Pokud je sestavení zavedeno jako doménově neutrální z více domén aplikace, tento čítač se zvyšuje pouze jednou.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Frekvence zavádění tříd**|Zobrazuje počet tříd zavedených za sekundu ve všech sestaveních. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Frekvence zavádění**|Zobrazuje počet tříd, které se nepodařilo načíst za sekundu. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.<br /><br /> Zavádění může dojít z mnoha důvodů, například neodpovídající zabezpečení nebo neplatný formát. Podrobnosti najdete v tématu nápovědy profilování služby.|  
|**Celkový počet selhání při načítání**|Zobrazuje nejvyšší počet tříd, které se nepovedlo načíst od spuštění aplikace.<br /><br /> Zavádění může dojít z mnoha důvodů, například neodpovídající zabezpečení nebo neplatný formát. Podrobnosti najdete v tématu nápovědy profilování služby.|  
|**Celkový počet objektů třídy AppDomain**|Zobrazuje nejvyšší počet domén aplikace zavedených od spuštění aplikace.|  
|**Celkový počet objektů třídy appdomains uvolněných**|Zobrazí celkový počet uvolněných od spuštění aplikace domény aplikace. Pokud domény aplikace je načteny nebo uvolněny více než jednou, zvýší čítač pokaždé, když je doména aplikace uvolněna.|  
|**Celkový počet sestavení**|Zobrazí celkový počet sestavení načtených od spuštění aplikace. Pokud je sestavení zavedeno jako doménově neutrální z více domén aplikace, tento čítač se zvyšuje pouze jednou.|  
|**Celkový počet zavedených tříd**|Zobrazuje kumulativní počet tříd, které jsou načteny ve všech sestaveních od spuštění aplikace.|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>Uzamčení a vlákna čítače výkonu  
 Kategorii Performance konzoly uzamčení a vlákna .NET CLR obsahuje čítače, které obsahují informace o spravované uzamčení a vlákna, které aplikace používá. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet aktuálních logických podprocesů**|Zobrazuje počet objektů pro aktuální spravované vlákno v aplikaci. Tento čítač udržuje počet spuštěných a zastavení vlákna. Hodnota čítače nepředstavuje průměr v čase; Zobrazí se pouze o poslední zjištěnou hodnotu.|  
|**Počet aktuálních fyzických vláken**|Zobrazuje počet vláken nativní operačního systému vytvořených a vlastněných platformou CLR tak, aby fungoval jako základní vlákna pro objekty spravované vlákna. Hodnota tohoto čítače nezahrnuje vlákna používaná platformou modulu runtime v rámci vnitřních operací; je podmnožinou vlákna v procesu operačního systému.|  
|**Počet aktuálních rozpoznaných vláken**|Zobrazuje počet vláken, které jsou aktuálně rozpoznána platformou modulu runtime. Tato vlákna jsou spojeny s odpovídající objekt spravované vlákno. Modul runtime nevytvoří tato vlákna, ale které byly provedeny uvnitř modulu runtime alespoň jednou.<br /><br /> Jsou sledována pouze jedinečná vlákna; vlákna se stejným ID vlákna, znovu zadejte modul runtime nebo jsou znovu vytvořena po ukončení vlákna, nejsou počítána dvakrát.|  
|**počet celkový počet rozpoznaných vláken**|Zobrazí celkový počet vláken, které byly rozpoznány modulem runtime od spuštění aplikace. Tato vlákna jsou spojeny s odpovídající objekt spravované vlákno. Modul runtime nevytvoří tato vlákna, ale které byly provedeny uvnitř modulu runtime alespoň jednou.<br /><br /> Jsou sledována pouze jedinečná vlákna; vlákna se stejným ID vlákna, znovu zadejte modul runtime nebo jsou znovu vytvořena po ukončení vlákna, nejsou počítána dvakrát.|  
|**Počet sporů za sekundu**|Zobrazí rychlost, jakou pokouší získat spravované uzamčení neúspěšně vlákna v modulu runtime.|  
|**Aktuální délka fronty**|Zobrazí celkový počet vláken, které jsou aktuálně čekají na získání spravovaného uzamčení v aplikaci. Hodnota čítače nepředstavuje průměr v čase; Zobrazí naposledy zjištěnou hodnotu.|  
|**Délka fronty za sekundu**|Zobrazuje počet vláken za sekundu, které čekají na získání uzamčení v aplikaci. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Nejvyšší délka fronty**|Zobrazí celkový počet vláken, která čekala na získání spravovaného uzamčení od spuštění aplikace.|  
|**rozpoznaná vlákna za sekundu**|Zobrazuje počet vláken za sekundu, které byly rozpoznány modulem runtime. Tato vlákna jsou spojeny s odpovídající objekt spravované vlákno. Modul runtime nevytvoří tato vlákna, ale které byly provedeny uvnitř modulu runtime alespoň jednou.<br /><br /> Jsou sledována pouze jedinečná vlákna; vlákna se stejným ID vlákna, znovu zadejte modul runtime nebo jsou znovu vytvořena po ukončení vlákna, nejsou počítána dvakrát.<br /><br /> Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Celkový počet sporů**|Zobrazí celkový počet případů, kdy se vlákna v modulu runtime jste se pokusili získat spravované uzamčení nebylo úspěšné.|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>Čítače výkonu paměti  
 Kategorii Performance konzoly .NET CLR paměti zahrnuje čítače, které obsahují informace o systému uvolňování paměti. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet bajtů ve všech haldách**|Součet **velikost haldy 1 Obecné**, **velikost haldy 2. generace**, a **velikost haldy velkých objektů** čítače. Tento čítač označuje velikost aktuální paměti přidělených bajtů na uvolnění paměti haldy.|  
|**Počet popisovačů GC**|Zobrazí aktuální počet popisovačů kolekce uvolnění paměti. Obslužné rutiny uvolnění paměti jsou popisovače k prostředkům, které jsou externí vzhledem k common language runtime a spravované prostředí.|  
|**Počet úklidů 0**|Zobrazí počet pokusů, které objekty generace 0 (to znamená, nejmladší, naposledy přidělené objekty) uklizeny od spuštění aplikace.<br /><br /> Pokud není dostatečná pro uspokojení požadavku na přidělení dostupné paměti v generaci 0, dojde k uvolnění paměti generace 0. Tento čítač se zvyšuje na konci uvolnění 0. generace. Vyšší generace uvolňování pamětí zahrnout všechny nižší generace kolekce. Tento čítač je explicitně zvýší, když dojde větší uvolnění paměti generace (generace 1 nebo 2).<br /><br /> Tento čítač zobrazí naposledy zjištěnou hodnotu. **_Global\_**  hodnota čítače není přesná a je třeba ji ignorovat.|  
|**Počet úklidů 1**|Zobrazí počet pokusů, které objekty 1. generace uklizeny od spuštění aplikace.<br /><br /> Hodnota čítače je zvýšena na konci 1 uvolnění paměti generace. Vyšší generace uvolňování pamětí zahrnout všechny nižší generace kolekce. Tento čítač je explicitně zvýší, když dojde k uvolnění vyšší generaci (2. generace).<br /><br /> Tento čítač zobrazí naposledy zjištěnou hodnotu. **_Global\_**  hodnota čítače není přesná a je třeba ji ignorovat.|  
|**Počet úklidů 2**|Zobrazí počet pokusů, které objekty 2. generace uklizeny od spuštění aplikace. Hodnota čítače je zvýšena na konci 2 uvolnění paměti generace (také nazývané úplného uvolňování paměti kolekce).<br /><br /> Tento čítač zobrazí naposledy zjištěnou hodnotu. **_Global\_**  hodnota čítače není přesná a je třeba ji ignorovat.|  
|**Počet vyvolání GC**|Zobrazí maximální počet, kolikrát se provedlo uvolňování kvůli explicitní volání konstruktoru <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Je dobrým zvykem umožňuje systému uvolňování paměti, frekvence jeho kolekcích.|  
|**počet nepřesunutelných objektů**|Zobrazí počet připojených objektů v posledním uvolnění paměti. Připojený objekt je objekt, který systému uvolňování paměti nelze přesunout v paměti. Čítač zaznamenává připojené objekty pouze v haldách, které jsou uvolněna z paměti. Například uvolnění paměti generace 0 způsobí, že nepřesunutelné pouze v haldě 0. generace.|  
|**Počet používaných bloků jímek**|Zobrazí aktuální počet bloků synchronizace. Synchronizační bloky jsou datové struktury jednotlivé objekty přidělené pro ukládání informací o synchronizaci. Drží slabé odkazy na spravované objekty a musí být kontrolována uvolnění paměti. Synchronizace bloků nejsou omezeny na ukládání informací o synchronizaci; můžete ukládat také COM interop metadat. Tento čítač označuje problémy s výkonem se hojně používají synchronizací primitiv.|  
|**Celkový počet svěřených bajtů**|Zobrazuje velikost virtuální paměti v bajtech, aktuálně potvrzené systémem uvolňování paměti. Potvrzená paměť je fyzická paměť, pro kterou bylo vyhrazeno místo ve stránkovacím souboru na disku.|  
|**Počet celkový vyhrazených bajtů**|Zobrazuje velikost virtuální paměti v bajtech, která je aktuálně vyhrazena systémem uvolňování paměti. Vyhrazenou pamětí je virtuální paměťový prostor vyhrazený pro aplikaci, když se používají bez použití disku nebo stránek hlavní paměti.|  
|**% Času v uvolňování paměti**|Zobrazuje procentuální hodnotu uplynulého času, který byl vynaložen provádění úklidu modulem od posledního cyklu uvolňování paměti kolekce. Tento čítač obvykle označuje práci provádí uvolňování paměti shromažďování a compact jménem aplikace. Tento čítač je aktualizován pouze na konci každé uvolňování paměti. Hodnota čítače nepředstavuje průměr; odráží její hodnotu o poslední zjištěnou hodnotu.|  
|**Přidělené bajty za sekundu**|Zobrazí počet bajtů za sekundu přidělený k haldě uvolňování paměti kolekce. Tento čítač je aktualizován na konci každé uvolňování paměti, ne při každém přidělení. Hodnota čítače nepředstavuje průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Zachované objekty finalizace**|Zobrazí počet uvolňování objektů, které byly zachovány při kolekce z důvodu čekání na jejich dokončení. Pokud tyto objekty obsahovat odkazy na jiné objekty, tyto objekty také překonání ale nejsou tímto čítačem počítány. **Povýšen finalizační paměť z 0. generace** čítač představuje paměti zůstat naživu kvůli dokončení.<br /><br /> Hodnota čítače nepředstavuje kumulativní; během této konkrétní kolekce je aktualizován na konci každé uvolňování paměti s počtem zachované objekty. Tento čítač označuje další režii, které aplikace se můžou účtovat kvůli dokončení.|  
|**Velikost haldy 0. generace**|Zobrazí maximální počet bajtů, které mohou být přiděleny v generaci 0; Aktuální počet bajtů alokovaných v generaci 0 neznamená.<br /><br /> Při přidělení od posledního shromažďování dat přesahují tuto velikost, dojde k uvolnění paměti generace 0. Velikost 0. generace je vyladěný uvolnění paměti a může změnit při spuštění aplikace. Na konci generace 0. generace kolekce velikost haldy 0 je 0 bajtů. Tento čítač zobrazuje velikost v bajtech, přidělení, která volá dalšího uvolnění paměti generace 0.<br /><br /> Tento čítač je aktualizován na konci uvolnění, ne při každém přidělení.|  
|**Přesunuté z 0. generace bajty/s**|Zobrazuje počet bajtů za sekundu, které jsou přesunuty z 0. generace do 1. generace. Paměť povýšen při odolává uvolňování paměti. Tento čítač je indikátor objektů jsou uložena relativně dlouhodobá vytváří za sekundu.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Velikost haldy 1. generace**|Zobrazuje aktuální počet bajtů v generaci 1; Tento čítač nezobrazuje maximální velikost 1. generace. Objekty se nebudou přidělovat přímo v této generaci; ale jsou přesouvány z předchozí generace 0 uvolňování paměti kolekce. Tento čítač je aktualizován na konci uvolnění, ne při každém přidělení.|  
|**Přesunuté z 1. generace bajty/s**|Zobrazuje počet bajtů za sekundu, které jsou přesunuty z 1. generace do 2. generace. Tento čítač nezahrnuje objekty, které jsou přesunuty pouze z důvodu čekání na jejich dokončení.<br /><br /> Paměť povýšen při odolává uvolňování paměti. Nic se přesunuty z 2. generace, protože se jedná o nejstarší generování. Tento čítač je indikátor objektů s velmi dlouhým poločasem rozpadu vytváří za sekundu.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Velikost haldy 2. generace**|Zobrazuje aktuální počet bajtů v 2. generace. Objekty se nebudou přidělovat přímo v této generaci; ale jsou přesouvány z 1. generace během uvolnění paměti předchozí generace 1. Tento čítač je aktualizován na konci uvolnění, ne při každém přidělení.|  
|**Velikost velkých objektových haldách**|Zobrazí aktuální velikost v bajtech haldy pro velké objekty. Objekty, které jsou větší než přibližně o velikosti 85 000 bajtů jsou považovány za velké objekty uvolnění paměti a přidělují přímo ze zvláštní haldy; ale nejsou přesouvány prostřednictvím těchto generacích. Tento čítač je aktualizován na konci uvolnění, ne při každém přidělení.|  
|**ID procesu**|Zobrazuje ID instance procesu CLR, která je monitorována.|  
|**Finalizační paměť přesunutá z 0. generace**|Zobrazí počet bajtů paměti, které jsou přesunuty z 0. generace do 1. generace pouze z důvodu čekání na jejich dokončení. Hodnota čítače nepředstavuje kumulativní; Zobrazuje hodnotu zjištěnou na konci posledního uvolnění paměti.|  
|**Přesunutá paměť z 0. generace**|Zobrazí počet bajtů paměti, které byly zachovány při uvolnění paměti a jsou přesunuty z 0. generace do 1. generace. Tento čítač nezahrnuje objekty, které jsou přesunuty pouze z důvodu čekání na jejich dokončení. Hodnota čítače nepředstavuje kumulativní; Zobrazuje hodnotu zjištěnou na konci posledního uvolnění paměti.|  
|**Přesunutá paměť z 1. generace**|Zobrazí počet bajtů paměti, které byly zachovány při uvolnění paměti a jsou přesunuty z 1. generace do 2. generace. Tento čítač nezahrnuje objekty, které jsou přesunuty pouze z důvodu čekání na jejich dokončení. Hodnota čítače nepředstavuje kumulativní; Zobrazuje hodnotu zjištěnou na konci posledního uvolnění paměti. Tento čítač nastaven na hodnotu 0, pokud poslední uvolnění paměti bylo pouze 0. generace kolekce.|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>Čítače výkonu sítě  
 Výkon konzoly .NET CLR sítě kategorie zahrnuje čítače, které poskytují informace o datech, která aplikace odesílá a přijímá přes síť. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Přijaté bajty**|Kumulativní celkový počet bajtů přijatých všechny <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu. Toto číslo zahrnuje data a všechny informace o protokolu, který není definován protokolu TCP/IP.|  
|**Odeslané bajty**|Kumulativní počet bajtů odeslaných všechny <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu. Toto číslo zahrnuje data a všechny informace o protokolu, který není definován protokolu TCP/IP.|  
|**Připojení**|Kumulativní počet <xref:System.Net.Sockets.Socket> objekty pro sokety datového proudu, které byly neustále připojené v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**Přijaté datagramy**|Celkový počet kumulativní počet všech přijatých paketů datagram <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**Odeslané datagramy**|Kumulativní celkový počet datagramů odeslaných paketů za sekundu ve všech <xref:System.Net.Sockets.Socket> objekty v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**Doba života HttpWebRequest průměr**|Průměrný čas na dokončení všech <xref:System.Net.HttpWebRequest> objekty, které skončila v posledního intervalu v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**HttpWebRequest průměrný čas fronty**|Průměrný čas na fronty pro všechny <xref:System.Net.HttpWebRequest> objekty, které left fronty v posledního intervalu v rámci <xref:System.AppDomain> od spuštění procesu.|  
|**HttpWebRequests vytvořené za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty vytvořené za sekundu v rámci <xref:System.AppDomain>.|  
|**HttpWebRequests zařazených do fronty za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty, které byly přidány do fronty za sekundu v rámci <xref:System.AppDomain>.|  
|**Přerušeno HttpWebRequests za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty, které aplikace volá <xref:System.Net.HttpWebRequest.Abort%2A> metoda za sekundu v rámci <xref:System.AppDomain>.|  
|**Nepovedlo HttpWebRequests za sekundu**|Počet <xref:System.Net.HttpWebRequest> objekty, které přijaly neúspěšné stavový kód ze serveru za sekundu v rámci <xref:System.AppDomain>.|  
  
 Existuje několik tříd síťových čítače výkonu, které jsou podporovány:  
  
-   Události čítačů, které měří počet pokusů, které došlo k nějaké události.  
  
-   Data čítačů, které měří množství dat odeslat ani přijmout.  
  
-   Doba trvání čítačů, které měří jak dlouho různé procesy trvat. Čas se měří na objektech v každém intervalu (obvykle v sekundách) po pocházejí z různých stavů.  
  
-   Za Interval čítačů, které měří počet objektů, které využívají konkrétní přechod na interval (obvykle za sekundu).  
  
 Sítě čítače výkonu pro událostí patří:  
  
-   **Připojení**  
  
-   **Přijaté datagramy**  
  
-   **Odeslané datagramy**  
  
 Tyto čítače výkonu poskytují počty od spuštění procesu. Počet <xref:System.Net.Sockets.Socket> připojení obsahuje explicitní <xref:System.Net.Sockets.Socket> metoda volá aplikací pro připojení soketu datového proudu, který byl zřízený stejně jako vnitřní volání uskutečněných tímto jiné třídy (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>, a <xref:System.Net.Sockets.TcpClient>, například) k <xref:System.Net.Sockets.Socket> třídy  
  
 Počty pro **přijatých datagramů** a **datagramy odeslané** zahrnuje datagram pakety odeslány nebo přijaty pomocí explicitní <xref:System.Net.Sockets.Socket> metoda volá jako dobře vnitřní volání uskutečněných tímto jiné aplikace třídy (<xref:System.Net.Sockets.UdpClient>, například) k <xref:System.Net.Sockets.Socket>. Třída. Počty **přijatých datagramů** a **datagramy odeslané** slouží také k poskytují velmi hrubých měřítko kolik bajtů byly odeslány nebo přijaty pomocí datagramy podle za předpokladu, že průměrná velikost pro datagram.  
  
 Čítače výkonu sítě pro data, patří:  
  
-   **Přijaté bajty**  
  
-   **Odeslané bajty**  
  
 Výše uvedené čítače poskytují počet bajtů od spuštění procesu.  
  
 Existují dva čítače doby trvání, které měří jak dlouho trvalo <xref:System.Net.HttpWebRequest> objekty předávání buď jejich celý životní cyklus nebo právě součástí je:  
  
-   **Doba života HttpWebRequest průměr**  
  
-   **HttpWebRequest průměrný čas fronty**  
  
 Pro **Průměrná životnost HttpWebRequest** čítače, dobu života většinu <xref:System.Net.HttpWebRequest> objekty s časem, který je vytvořen objekt až po dobu, po kterou datového proudu odpovědi je ukončená aplikace vždycky spustí. Existují dva běžné případy:  
  
-   Pokud aplikace se nikdy nevolá <xref:System.Net.HttpWebRequest.GetResponse%2A> nebo <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> metody a pak životnosti <xref:System.Net.HttpWebRequest> objekt se ignoruje.  
  
-   Pokud <xref:System.Net.HttpWebRequest> objektu vyvolá výjimku <xref:System.Net.WebException> při volání <xref:System.Net.HttpWebRequest.GetResponse%2A> nebo <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metody, dobu života končí, když je vyvolána výjimka. Technicky vzato základního datového proudu odpovědi také zavření od tohoto okamžiku (datového proudu odpovědi vrátí uživateli je ve skutečnosti paměťový proud, který obsahuje kopii datového proudu odpovědi).  
  
 Existují čtyři čítače, které sledují určité <xref:System.Net.HttpWebRequest> objektu problémy za interval. Tyto čítače výkonu může pomoci vývojáři aplikací, správci, a pracovníkům podpory lépe pochopit, co <xref:System.Net.HttpWebRequest> dělají objekty. Čítače zahrnují následující:  
  
-   **HttpWebRequests vytvořené za sekundu**  
  
-   **HttpWebRequests zařazených do fronty za sekundu**  
  
-   **Přerušeno HttpWebRequests za sekundu**  
  
-   **Nepovedlo HttpWebRequests za sekundu**  
  
 Pro **HttpWebRequests přerušených za sekundu** čítač, vnitřní volání <xref:System.Net.HttpWebRequest.Abort%2A> se také počítají. Tyto interní volání jsou obvykle způsobeno časové limity, které aplikace může být vhodné k měření.  
  
 **HttpWebRequests. nezdařilo se za sekundu** čítače obsahuje počet <xref:System.Net.HttpWebRequest> objekty, které přijaly stav selhání kódu ze serveru za sekundu. To znamená, že se stavovým kódem přijatou ze serveru Http na konci požadavku nebyla v rozsahu 200 k 299. Stavové kódy, které jsou zpracovány a mít za následek novou žádost o (řadu kódy 401 Unauthorized status například) se nezdaří nebo není odmítnuti v závislosti na výsledku opakování. Pokud aplikace by se zobrazit chyba založené na nový pokus, tento čítač se zvyšuje.  
  
 Čítače výkonu sítě je přístupný a spravují s použitím <xref:System.Diagnostics.PerformanceCounter> a související třídy v <xref:System.Diagnostics> oboru názvů. Čítače výkonu sítě je možné zobrazit i v konzole Windows Performance Monitor.  
  
 Čítače výkonu sítě musí být povolené v konfiguračním souboru, který se má použít. Všechny čítače výkonu sítě jsou povolené nebo zakázané s jedno nastavení v konfiguračním souboru. Jednotlivé čítače výkonu sítě nemůže být povolena nebo zakázána. Další informace najdete v tématu [ \<performanceCounter > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Pokud jsou povolené sítě – čítače, se vytvářet a aktualizovat na úrovni AppDomain a globální čítače výkonu. Pokud je zakázané, aplikace nebude poskytovat žádné síťové data čítače výkonu.  
  
 Čítače výkonu jsou seskupené do kategorií. Aplikace můžete zobrazit seznam všech kategorií pomocí následujícího ukázkového kódu:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Čítače výkonu sítě patří do dvou kategorií:  
  
-   ".NET CLR síťové služby" – původní čítače výkonu zavedeno v rozhraní .NET Framework verze 2 a podporuje se v rozhraní .NET Framework verze 2 nebo novější.  
  
-   ".NET CLR sítě 4.0.0.0" - všechny výše uvedené soketu čítače plus nové čítače výkonu, podporuje se v rozhraní .NET Framework verze 4 a novější. Tyto nové čítače poskytují informace o výkonu na <xref:System.Net.HttpWebRequest> objekty.  
  
 Další informace o přístupu a správě čítače výkonu v aplikaci najdete v tématu [čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>Čítače výkonu zabezpečení  
 Kategorii Performance konzoly zabezpečení .NET CLR obsahuje čítače, které poskytují informace o zabezpečení kontroly, které provádí modul common language runtime pro aplikace. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet kontrol během propojování**|Zobrazí celkový počet zabezpečení přístupu kódu při propojování kontroluje od spuštění aplikace. Kontroly zabezpečení přístupu kódu při propojování jsou prováděny, pokud volající požaduje konkrétní oprávnění v době kompilace just-in-time (JIT). Propojování kontrola se provádí jednou za volajícího. Čítač není indikátorem závažných problémů s výkonem; je pouze informativní aktivity zabezpečení systému.|  
|**% Času při kontrolách**|Od posledního vzorku o určitý zobrazuje procento času stráveného provádí runtime kontroly zabezpečení přístupu kódu. Tento čítač je aktualizován na konci kontroly zabezpečení rozhraní .NET Framework. Nejedná se o průměr; představuje poslední zjištěnou hodnotu.|  
|**% Času Sig ověřování**|Vyhrazeno pro budoucí použití.|  
|**Hloubka procházení zásobníku**|Zobrazuje hloubku zásobníku během poslední kontroly zabezpečení kód přístup k modulu runtime. Kontroly zabezpečení přístupu kódu za běhu jsou prováděny procházení zásobníku. Hodnota čítače nepředstavuje průměr; Zobrazí se pouze o poslední zjištěnou hodnotu.|  
|**Celková doba běhu kontroly**|Zobrazí celkový počet kód modulu runtime přístup k zabezpečení provedených od spuštění aplikace. Modul runtime kód získat přístup k zabezpečení, které jsou provedeny kontroly, když volající požaduje konkrétní oprávnění. Kontroly za běhu se provádí při každém volání volajícího a zkoumá aktuálního zásobníku vláken volajícího. Při použití s **hloubka procházení zásobníku** čítače, tento čítač označuje snížení výkonu, ke které dochází ke kontrolám zabezpečení.|  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 [Běhová profilace](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
