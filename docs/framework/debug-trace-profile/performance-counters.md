---
title: Čítače výkonu v rozhraní .NET Framework
description: Přečtěte si o čítačích výkonu v rozhraní .NET. Existují čítače výkonu pro výjimky, zprostředkovatele komunikace, kompilátory JIT, načítání, paměť, sítě, zabezpečení a další.
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: 3702e9d2e0a369f5391c16088202caf5d7ced7ea
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803700"
---
# <a name="performance-counters-in-the-net-framework"></a>Čítače výkonu v .NET Framework

V tomto tématu najdete seznam čítačů výkonu, které můžete najít v [nástroji Sledování výkonu systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  

## <a name="exception-performance-counters"></a>Čítače výkonu výjimek  
 Kategorie výjimky modulu .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o výjimkách vyvolaných aplikací. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet vyvolaných # z počet vyvolaných**|Zobrazuje celkový počet výjimek vyvolaných od spuštění aplikace. To zahrnuje výjimky rozhraní .NET i nespravované výjimky, které jsou převedeny na výjimky rozhraní .NET. Například hodnota HRESULT vrácená z nespravovaného kódu je převedena na výjimku ve spravovaném kódu.<br /><br /> Tento čítač zahrnuje jak zpracované, tak neošetřené výjimky. Výjimky, které jsou znovu vyvolány, se počítají znovu.|  
|**Počet vyvolaných počet vyvolaných za sekundu**|Zobrazuje počet výjimek vyvolaných za sekundu. To zahrnuje výjimky rozhraní .NET i nespravované výjimky, které jsou převedeny na výjimky rozhraní .NET. Například hodnota HRESULT vrácená z nespravovaného kódu je převedena na výjimku ve spravovaném kódu.<br /><br /> Tento čítač zahrnuje jak zpracované, tak neošetřené výjimky. Nejedná se o průměr v čase; zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování. Tento čítač je indikátorem potenciálních problémů s výkonem, pokud je vyvolán velký (>) počet výjimek.|  
|**počet filtrů za sekundu**|Zobrazuje počet zpracovaných filtrů výjimek .NET za sekundu. Filtr výjimek vyhodnocuje bez ohledu na to, zda je výjimka zpracována.<br /><br /> Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**počet finally za sekundu**|Zobrazuje počet bloků finally spuštěných za sekundu. Je zaručeno provedení bloku finally bez ohledu na to, jak byl blok try ukončen.  Počítají se pouze bloky finally provedené pro výjimku. v tomto čítači se nepočítají bloky finally k běžným cestám kódu.<br /><br /> Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Zahodit na hloubku zachycení za sekundu**|Zobrazuje počet prodaných rámců zásobníku z rámce, který vyvolal výjimku do rámce, který zpracovává výjimku, za sekundu. Tento čítač je nastaven na hodnotu nula, pokud je zadána obslužná rutina výjimky, takže vnořené výjimky znázorňují hloubku zásobníku obslužných rutin.<br /><br /> Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  

## <a name="interop-performance-counters"></a>Čítače výkonu spolupráce  
 Kategorie interoperability .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o interakci aplikace s komponentami modelu COM, službami COM+ a externími knihovnami typů. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**počet obálek CCW**|Zobrazuje aktuální počet obálk s vydaných v modelu COM (obálek CCW). DOLEVA je proxy pro spravovaný objekt, na který se odkazuje z nespravovaného klienta modelu COM. Tento čítač označuje počet spravovaných objektů, na které odkazuje nespravovaný kód COM.|  
|**počet zařazování**|Zobrazuje celkový počet argumentů a vrácených hodnot, které byly zařazeny ze spravovaného do nespravovaného kódu, a naopak, od spuštění aplikace. Tento čítač není zvýšen, pokud jsou zástupné procedury vloženy. (Zástupné procedury jsou zodpovědné za zařazování argumentů a vrácených hodnot). Zástupné procedury jsou obvykle vloženy, pokud je zařazování na malá.|  
|**počet zástupných procedur**|Zobrazuje aktuální počet zástupných procedur vytvořených modulem CLR (Common Language Runtime). Zástupné procedury jsou zodpovědné za zařazování argumentů a návratové hodnoty ze spravovaného do nespravovaného kódu a naopak, během volání Interop modelu COM nebo volání vyvolání platformy.|  
|**počet exportů TLB za sekundu**|Vyhrazeno pro budoucí použití.|  
|**počet importů TLB za sekundu**|Vyhrazeno pro budoucí použití.|  

## <a name="jit-performance-counters"></a>JIT – čítače výkonu  
 Kategorie JIT konzoly Performance .NET CLR obsahuje čítače, které poskytují informace o kódu, který byl zkompilován JIT. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**počet bajtů IL zpracovaných kompilátorem JIT**|Zobrazuje celkový počet bajtů jazyka MSIL (Microsoft Intermediate Language) zkompilovaných kompilátorem JIT (just-in-time) od spuštění aplikace. Tento čítač je ekvivalentní k **celkovému počtu čítačů zpracovaných kompilátorem JIT bajtů Il** .|  
|**počet metod zpracovaných kompilátorem JIT**|Zobrazuje celkový počet metod, které byly kompilovány JIT od spuštění aplikace. Tento čítač neobsahuje metody zkompilované před kompilátorem JIT.|  
|**% Času v JIT**|Zobrazuje procento uplynulého času stráveného kompilací JIT od poslední fáze kompilace JIT. Tento čítač se aktualizuje na konci každé kompilační fáze JIT. Fáze kompilace JIT nastane, když je zkompilována metoda a její závislosti.|  
|**IL – bajty zpracovaných kompilátorem JIT/s**|Zobrazuje počet bajtů jazyka MSIL, které jsou kompilovány JIT za sekundu. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Standardní chyby JIT**|Zobrazuje nejvyšší počet metod, které kompilátor JIT nedokázal zkompilovat od spuštění aplikace. K této chybě může dojít, pokud jazyk MSIL nelze ověřit nebo pokud došlo k vnitřní chybě v kompilátoru JIT.|  
|**Celkový počet bajtů zpracovaných kompilátorem JIT úrovně důvěryhodnosti**|Zobrazuje celkový počet bajtů jazyka MSIL spouštěných JIT od spuštění aplikace. Tento čítač je ekvivalentem čítače **# zpracovaných kompilátorem JIT bajtů úrovně Il** .|  

## <a name="loading-performance-counters"></a>Načítají se čítače výkonu.  
 Kategorie načítání modulu .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o sestaveních, třídách a doménách aplikace, které jsou načteny. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**% Času načítání**|Vyhrazeno pro budoucí použití.|  
|**Délka hledání sestavení**|Vyhrazeno pro budoucí použití.|  
|**Počet bajtů v haldě zavaděče**|Zobrazuje aktuální velikost paměti potvrzené zavaděčem tříd napříč všemi doménami aplikace v bajtech. Potvrzená paměť je fyzické místo rezervované ve stránkovacím souboru na disku.|  
|**Aktuální třídy AppDomains**|Zobrazuje aktuální počet aplikačních domén načtených v této aplikaci.|  
|**Aktuální sestavení**|Zobrazuje aktuální počet sestavení načtených napříč všemi aplikačními doménami v aktuálně spuštěné aplikaci. Pokud je sestavení načteno jako doménově neutrální z více domén aplikace, tento čítač se zvyšuje pouze jednou.|  
|**Aktuální načtené třídy**|Zobrazuje aktuální počet tříd zavedených ve všech sestaveních.|  
|**Frekvence objektů třídy AppDomain**|Zobrazuje počet načtených aplikačních domén za sekundu. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Frekvence uvolňování objektů třídy AppDomain**|Zobrazí počet uvolněných aplikačních domén za sekundu. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Frekvence sestavení**|Zobrazuje počet sestavení načtených za sekundu napříč doménami aplikace. Pokud je sestavení načteno jako doménově neutrální z více domén aplikace, tento čítač se zvyšuje pouze jednou.<br /><br /> Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Počet načtených tříd**|Zobrazuje počet tříd načtených za sekundu ve všech sestaveních. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Frekvence selhání načítání**|Zobrazí počet tříd, které se nepodařilo načíst za sekundu. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.<br /><br /> Selhání načítání může nastat z mnoha důvodů, jako je nedostatečné zabezpečení nebo neplatný formát. Podrobnosti najdete v nápovědě ke službě profilace.|  
|**Celkový počet selhání načtení**|Zobrazuje nejvyšší počet tříd, které se nepodařilo načíst od spuštění aplikace.<br /><br /> Selhání načítání může nastat z mnoha důvodů, jako je nedostatečné zabezpečení nebo neplatný formát. Podrobnosti najdete v nápovědě ke službě profilace.|  
|**Celkový počet objektů třídy AppDomain**|Zobrazuje nejvyšší počet aplikačních domén načtených od spuštění aplikace.|  
|**Celkový počet nenačtených objektů AppDomain**|Zobrazuje celkový počet aplikačních domén uvolněných od spuštění aplikace. Pokud je doména aplikace načtena a uvolněna několikrát, tento čítač se zvýší pokaždé, když se doména aplikace uvolní.|  
|**Celkem sestavení**|Zobrazuje celkový počet sestavení načtených od spuštění aplikace. Pokud je sestavení načteno jako doménově neutrální z více domén aplikace, tento čítač se zvyšuje pouze jednou.|  
|**Celkový počet načtených tříd**|Zobrazuje kumulativní počet tříd zavedených ve všech sestaveních od spuštění aplikace.|  

## <a name="lock-and-thread-performance-counters"></a>Čítače výkonu zámků a vláken  
 Kategorie LocksAndThreads modulu .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o spravovaných zámkech a vláknech, které aplikace používá. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet aktuálních logických vláken**|Zobrazí počet aktuálních objektů spravovaného vlákna v aplikaci. Tento čítač udržuje počet spuštěných i zastavených vláken. Tento čítač nepředstavuje průměr v čase. zobrazuje jenom poslední zjištěnou hodnotu.|  
|**Počet aktuálních fyzických vláken**|Zobrazí počet nativních vláken operačního systému vytvořených a vlastněných modulem CLR (Common Language Runtime), aby fungoval jako podkladová vlákna pro objekty spravovaného vlákna. Hodnota tohoto čítače nezahrnuje vlákna používaná modulem runtime v rámci svých interních operací. Jedná se o podmnožinu vláken v procesu operačního systému.|  
|**Počet aktuálních rozpoznaných vláken**|Zobrazí počet vláken, která jsou aktuálně rozpoznána modulem runtime. Tato vlákna jsou přidružena k odpovídajícímu objektu spravovaného vlákna. Modul runtime nevytváří Tato vlákna, ale byly spuštěny v modulu runtime alespoň jednou.<br /><br /> Jsou sledována pouze jedinečná vlákna; vlákna se stejným ID vlákna, která znovu vstupují modul runtime nebo se znovu vytvoří po ukončení vlákna, se nepočítají dvakrát.|  
|**Celkový počet rozpoznaných vláken**|Zobrazuje celkový počet vláken rozpoznávaných modulem runtime od spuštění aplikace. Tato vlákna jsou přidružena k odpovídajícímu objektu spravovaného vlákna. Modul runtime nevytváří Tato vlákna, ale byly spuštěny v modulu runtime alespoň jednou.<br /><br /> Jsou sledována pouze jedinečná vlákna; vlákna se stejným ID vlákna, která znovu vstupují modul runtime nebo se znovu vytvoří po ukončení vlákna, se nepočítají dvakrát.|  
|**Počet sporů za sekundu**|Zobrazuje rychlost, s jakou se vlákna v modulu runtime pokoušejí neúspěšně získat spravovaný zámek.|  
|**Aktuální délka fronty**|Zobrazuje celkový počet vláken, která aktuálně čekají na získání spravovaného zámku v aplikaci. Tento čítač nepředstavuje průměr v čase. zobrazuje poslední zjištěnou hodnotu.|  
|**Délka fronty/s**|Zobrazí počet vláken za sekundu, které čekají na získání zámku v aplikaci. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Maximální délka fronty**|Zobrazuje celkový počet vláken, která od spuštění aplikace čekala na získání spravovaného zámku.|  
|**frekvence rozpoznaných vláken za sekundu**|Zobrazí počet vláken za sekundu, které byly rozpoznány modulem runtime. Tato vlákna jsou přidružena k odpovídajícímu objektu spravovaného vlákna. Modul runtime nevytváří Tato vlákna, ale byly spuštěny v modulu runtime alespoň jednou.<br /><br /> Jsou sledována pouze jedinečná vlákna; vlákna se stejným ID vlákna, která znovu vstupují modul runtime nebo se znovu vytvoří po ukončení vlákna, se nepočítají dvakrát.<br /><br /> Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Celkový počet sporů**|Zobrazuje celkový počet pokusů, kolikrát se vlákna v modulu runtime pokusila získat spravovaný zámek neúspěšně.|  

## <a name="memory-performance-counters"></a>Čítače výkonu paměti  
 Kategorie paměti modulu .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o uvolňování paměti. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet bajtů ve všech haldách**|Zobrazuje součet čítače velikosti haldy **1**. generace, **velikosti haldy 2. generace**a **large object čítačů velikosti haldy** . Tento čítač označuje aktuální paměť přidělenou v bajtech pro haldy uvolňování paměti.|  
|**Počet popisovačů GC**|Zobrazuje aktuální počet používaných obslužných rutin uvolňování paměti. Popisovače uvolňování paměti jsou popisovače pro prostředky externě pro modul CLR (Common Language Runtime) a spravované prostředí.|  
|**Počet kolekcí 0. generace**|Zobrazuje počet uvolnění objektů generace 0 (tj. nejmladšího sourozence, naposledy přidělených objektů) od spuštění aplikace.<br /><br /> K uvolňování paměti generace 0 dochází, když volná paměť v generaci 0 nestačí pro splnění žádosti o přidělení. Tento čítač se zvyšuje na konci uvolňování paměti generace 0. Generace paměti vyšší úrovně zahrnuje všechny kolekce nižší generace. Tento čítač se explicitně zvýší, když dojde k uvolnění paměti generace vyšší (generace 1 nebo 2).<br /><br /> Tento čítač zobrazuje poslední zjištěnou hodnotu. Hodnota **čítače \_ _global** není přesná a měla by být ignorována.|  
|**Počet kolekcí 1. generace**|Zobrazuje počet uvolnění paměti objektů generace 1 od spuštění aplikace.<br /><br /> Čítač se zvyšuje na konci uvolňování paměti 1. generace. Generace paměti vyšší úrovně zahrnuje všechny kolekce nižší generace. Tento čítač se explicitně zvýší, když dojde k uvolnění paměti vyšší generace (generace 2).<br /><br /> Tento čítač zobrazuje poslední zjištěnou hodnotu. Hodnota **čítače \_ _global** není přesná a měla by být ignorována.|  
|**Počet kolekcí generace 2**|Zobrazuje počet uvolnění paměti objektů generace 2 od spuštění aplikace. Čítač se zvyšuje na konci uvolňování paměti 2. generace (označuje se také jako úplné uvolňování paměti).<br /><br /> Tento čítač zobrazuje poslední zjištěnou hodnotu. Hodnota **čítače \_ _global** není přesná a měla by být ignorována.|  
|**Počet vyvolaných GC**|Zobrazuje nejvyšší počet, kolikrát bylo uvolňování paměti provedeno z důvodu explicitního volání <xref:System.GC.Collect%2A?displayProperty=nameWithType> . Je vhodné nechat systém uvolňování paměti, aby vypravil četnost jeho kolekcí.|  
|**počet připnutých objektů**|Zobrazuje počet připnutých objektů zjištěných při posledním uvolňování paměti. Připnutý objekt je objekt, který systém uvolňování paměti nemůže přesunout do paměti. Tento čítač sleduje připnuté objekty pouze v haldách, které jsou shromažďovány z paměti. Například uvolňování paměti generace 0 způsobuje vyčíslení připnuté objekty pouze v haldě generace 0.|  
|**Počet používaných bloků jímky**|Zobrazuje aktuální počet používaných synchronizačních bloků. Bloky synchronizace jsou datové struktury pro jednotlivé objekty přidělené pro ukládání informací o synchronizaci. Obsahují slabé odkazy na spravované objekty a musí být prohledávány systémem uvolňování paměti. Synchronizační bloky nejsou omezeny na ukládání informací o synchronizaci; můžou také ukládat definiční metadata COM. Tento čítač indikuje problémy s výkonem při velkém použití primitiv synchronizace.|  
|**Celkový počet potvrzených bajtů**|Zobrazuje velikost virtuální paměti (v bajtech), která je aktuálně potvrzena systémem uvolňování paměti. Potvrzená paměť je fyzická paměť, pro kterou bylo vyhrazeno místo ve stránkovacím souboru na disku.|  
|**Celkový počet rezervovaných bajtů**|Zobrazuje velikost virtuální paměti (v bajtech), která je aktuálně vyhrazena systémem uvolňování paměti. Rezervovaná paměť je virtuální prostor, který je vyhrazený pro aplikaci, když se nepoužily žádné diskové nebo hlavní paměťové stránky.|  
|**% Času v GC**|Zobrazuje procento uplynulého času stráveného prováděním uvolňování paměti od posledního cyklu uvolňování paměti. Tento čítač obvykle označuje práci prováděnou systémem uvolňování paměti pro shromažďování a komprimaci paměti jménem aplikace. Tento čítač se aktualizuje jenom na konci každého uvolňování paměti. Tento čítač nepředstavuje průměr. jeho hodnota odráží poslední zjištěnou hodnotu.|  
|**Přidělené bajty za sekundu**|Zobrazuje počet bajtů za sekundu, které jsou přiděleny haldě uvolňování paměti. Tento čítač se aktualizuje na konci každého uvolňování paměti, ne při každém přidělení. Tento čítač nepředstavuje průměr v čase. zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Zbývající objekty pro finalizaci**|Zobrazí počet uvolněných paměťových objektů, které zachytí kolekci, protože čekají na dokončení. Pokud tyto objekty uchovávají odkazy na jiné objekty, jsou tyto objekty zachovány, ale nejsou počítány tímto čítačem. **Povýšená finalizace paměti z čítače gen 0** představuje veškerou paměť, která se zadržela v důsledku dokončení.<br /><br /> Tento čítač není kumulativní; aktualizuje se na konci každého uvolňování paměti s počtem pozůstalých v této konkrétní kolekci. Tento čítač označuje dodatečnou režii, kterou může aplikace vzniknout z důvodu finalizace.|  
|**Velikost haldy 0. generace**|Zobrazí maximální počet bajtů, které mohou být přiděleny v generaci 0; neoznačuje aktuální počet bajtů přidělených v generaci 0.<br /><br /> Uvolňování paměti generace 0 nastane, pokud přidělení od poslední kolekce překročí tuto velikost. Velikost generace 0 je vyladěna systémem uvolňování paměti a může se změnit během provádění aplikace. Na konci kolekce 0. generace je velikost haldy generace 0 0 bajtů. Tento čítač zobrazuje velikost přidělení (v bajtech), která vyvolá nové uvolňování paměti generace 0.<br /><br /> Tento čítač se aktualizuje na konci uvolňování paměti, ne při každém přidělení.|  
|**Bajty úrovně gen 0 (KB/s)**|Zobrazuje počet bajtů za sekundu, které jsou povýšeny z generace 0 na generaci 1. V případě, že se zachová uvolňování paměti, je podporována paměť. Tento čítač je indikátorem poměrně dlouhých objektů, které jsou vytvářeny za sekundu.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Velikost haldy 1. generace**|Zobrazuje aktuální počet bajtů v generaci 1; Tento čítač nezobrazuje maximální velikost 1. generace. Objekty nejsou v této generaci přímo přiděleny; jsou povýšeny z předchozích generací paměti generace 0. Tento čítač se aktualizuje na konci uvolňování paměti, ne při každém přidělení.|  
|**Bajty úrovně 1. generace (KB/s)**|Zobrazuje počet bajtů za sekundu, které jsou povýšeny z generace 1 na generaci 2. Objekty, které jsou povýšeny pouze proto, že čekají na finalizaci, nejsou zahrnuty do tohoto čítače.<br /><br /> V případě, že se zachová uvolňování paměti, je podporována paměť. Z generace 2 se nic nezvyšuje, protože se jedná o nejstarší generaci. Tento čítač je indikátorem velmi dlouhých objektů, které jsou vytvářeny za sekundu.<br /><br /> Tento čítač zobrazuje rozdíl mezi hodnotami zjištěnými v posledních dvou vzorcích dělený délkou intervalu vzorkování.|  
|**Velikost haldy 2. generace**|Zobrazí aktuální počet bajtů v generaci 2. Objekty nejsou v této generaci přímo přiděleny; jsou povýšeny z generace 1 v předchozích kolekcích uvolnění paměti 1. generace. Tento čítač se aktualizuje na konci uvolňování paměti, ne při každém přidělení.|  
|**Velikost haldy Large Object**|Zobrazí aktuální velikost haldy velkých objektů v bajtech. Objekty, které jsou větší než přibližně 85 000 bajtů, jsou považovány za velké objekty uvolňováním paměti a jsou přímo přiděleny ve speciální haldě. Nejsou povýšené prostřednictvím generací. Tento čítač se aktualizuje na konci uvolňování paměti, ne při každém přidělení.|  
|**ID procesu**|Zobrazuje ID procesu monitorované instance procesu CLR.|  
|**Povýšená finalizace – paměť z 0. generace**|Zobrazí bajty paměti, které jsou povýšeny z 0. generace do 1. generace, protože čekají na dokončení. Tento čítač není kumulativní; zobrazuje hodnotu zjištěnou na konci posledního uvolňování paměti.|  
|**Propagovaná paměť z gen 0**|Zobrazí bajty paměti, které zadržely uvolňování paměti a jsou povýšeny z generace 0 na generaci 1. Objekty, které jsou povýšeny pouze proto, že čekají na finalizaci, nejsou zahrnuty do tohoto čítače. Tento čítač není kumulativní; zobrazuje hodnotu zjištěnou na konci posledního uvolňování paměti.|  
|**Propagace paměti z 1. generace**|Zobrazuje počet bajtů paměti, které zadržely uvolňování paměti a jsou povýšeny z generace 1 na generaci 2. Objekty, které jsou povýšeny pouze proto, že čekají na finalizaci, nejsou zahrnuty do tohoto čítače. Tento čítač není kumulativní; zobrazuje hodnotu zjištěnou na konci posledního uvolňování paměti. Hodnota tohoto čítače je nastavena na hodnotu 0, pokud poslední uvolňování paměti bylo pouze kolekcí generace 0.|  

## <a name="networking-performance-counters"></a>Čítače výkonu sítě  

Kategorie sítě .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o datech, která aplikace odesílá a přijímá přes síť. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Přijaté bajty**|Kumulativní celkový počet bajtů přijatých všemi <xref:System.Net.Sockets.Socket> objekty v době, kdy byl <xref:System.AppDomain> proces spuštěn. Toto číslo zahrnuje data a všechny informace o protokolu, které nejsou definovány protokolem TCP/IP.|  
|**Odeslané bajty**|Kumulativní počet bajtů odeslaných všemi <xref:System.Net.Sockets.Socket> objekty v době, kdy byl <xref:System.AppDomain> proces spuštěn. Toto číslo zahrnuje data a všechny informace o protokolu, které nejsou definovány protokolem TCP/IP.|  
|**Navázaná připojení**|Kumulativní celkový počet <xref:System.Net.Sockets.Socket> objektů pro sokety streamů, které byly někdy připojeny v <xref:System.AppDomain> době od spuštění procesu.|  
|**Přijaté datagramy**|Kumulativní celkový počet paketů datagramů přijatých všemi <xref:System.Net.Sockets.Socket> objekty v době, kdy byl <xref:System.AppDomain> proces spuštěn.|  
|**Odeslané datagramy**|Kumulativní celkový počet paketů datagramů odeslaných všemi <xref:System.Net.Sockets.Socket> objekty v době, kdy byl <xref:System.AppDomain> proces spuštěn.|  
|**Průměrná doba života HttpWebRequest**|Průměrná doba dokončení všech <xref:System.Net.HttpWebRequest> objektů, které skončily v posledním intervalu v <xref:System.AppDomain> době od spuštění procesu.|  
|**Průměrná doba čekání HttpWebRequest**|Průměrná doba čekání pro všechny <xref:System.Net.HttpWebRequest> objekty, které opustily frontu v posledním intervalu <xref:System.AppDomain> od spuštění procesu.|  
|**HttpWebRequests vytvořená za sekundu**|Počet <xref:System.Net.HttpWebRequest> objektů vytvořených za sekundu v rámci <xref:System.AppDomain> .|  
|**HttpWebRequests ve frontě za sekundu**|Počet <xref:System.Net.HttpWebRequest> objektů přidaných do fronty za sekundu v rámci <xref:System.AppDomain> .|  
|**HttpWebRequests přerušeno za sekundu**|Počet <xref:System.Net.HttpWebRequest> objektů, ve kterých aplikace volala <xref:System.Net.HttpWebRequest.Abort%2A> metodu za sekundu v rámci <xref:System.AppDomain> .|  
|**Neúspěšné HttpWebRequests/s**|Počet <xref:System.Net.HttpWebRequest> objektů, které přijaly stavový kód neúspěšné ze serveru za sekundu v rámci <xref:System.AppDomain> .|  
  
 Podporuje se několik tříd čítačů výkonu sítě:  
  
- Čítače události, které měří počet výskytů určité události.  
  
- Čítače dat, které měří množství odeslaných nebo přijímaných dat.  
  
- Čítače doby trvání, které měří, jak dlouho různé procesy trvají. Časy se měří na objektech každého intervalu (obvykle v sekundách) po tom, co se nacházejí v různých stavech.  
  
- Čítače podle intervalu, které měří počet objektů, které provádějí určitý přechod na interval (obvykle za sekundu).  
  
Mezi čítače výkonu sítě pro události patří následující:  
  
- **Navázaná připojení**  
  
- **Přijaté datagramy**  
  
- **Odeslané datagramy**  
  
 Tyto čítače výkonu poskytují počty od spuštění procesu. Počty <xref:System.Net.Sockets.Socket> navázaných připojení zahrnují explicitní <xref:System.Net.Sockets.Socket> volání metody v rámci aplikace pro připojení soketu streamu, které bylo navázáno, a také interní volání prováděná jinými třídami ( <xref:System.Net.HttpWebRequest> , <xref:System.Net.FtpWebRequest> , <xref:System.Net.WebClient> a <xref:System.Net.Sockets.TcpClient> , například) do <xref:System.Net.Sockets.Socket> třídy.  
  
 Počty **přijatých datagramů** a **odeslaných datagramů** zahrnují pakety datagramů odeslané nebo přijímané pomocí explicitní <xref:System.Net.Sockets.Socket> volání metody v rámci aplikace, stejně jako interní volání prováděná jinými třídami ( <xref:System.Net.Sockets.UdpClient> například) na <xref:System.Net.Sockets.Socket> . Deník. Počty **přijatých datagramů** a **Odeslané datagramy** mohou být také použity k zajištění velmi hrubé míry, kolik bajtů bylo odesláno nebo přijato pomocí datagramů, za předpokladu, že je pro datagram k dispozici Průměrná velikost.  
  
 Mezi čítače výkonu sítě pro data patří následující:  
  
- **Přijaté bajty**  
  
- **Odeslané bajty**  
  
 Výše uvedené čítače poskytují počty bajtů od spuštění procesu.  
  
 Existují dvě počítadla doby trvání, která měří, jak dlouho trvalo, <xref:System.Net.HttpWebRequest> aby objekty prošly celým životním cyklem nebo pouze jeho součástí:  
  
- **Průměrná doba života HttpWebRequest**  
  
- **Průměrná doba čekání HttpWebRequest**  
  
 V případě čítače **HttpWebRequest Average** = doba života většiny <xref:System.Net.HttpWebRequest> objektů vždy začíná časem, kdy je objekt vytvořen, až do doby, kdy je datový proud odpovědí uzavřen aplikací. Existují dva Neběžné případy:  
  
- Pokud aplikace nikdy nevolá <xref:System.Net.HttpWebRequest.GetResponse%2A> metody nebo <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> , pak je doba života <xref:System.Net.HttpWebRequest> objektu ignorována.  
  
- Pokud <xref:System.Net.HttpWebRequest> objekt vyvolá <xref:System.Net.WebException> při volání <xref:System.Net.HttpWebRequest.GetResponse%2A> <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metody nebo, životnost končí, když je vyvolána výjimka. Technicky, podkladový datový proud odpovědí je také uzavřen v tomto okamžiku (datový proud odpovědi vrácený uživateli je ve skutečnosti datový proud obsahující kopii datového proudu odpovědí).  
  
 Existují čtyři čítače, které sledují určité <xref:System.Net.HttpWebRequest> problémy s objekty za interval. Tyto čítače výkonu mohou pomoci vývojářům aplikací, správcům a pracovníkům podpory lépe pochopit, co <xref:System.Net.HttpWebRequest> dělají objekty. Mezi tyto čítače patří:  
  
- **HttpWebRequests vytvořená za sekundu**  
  
- **HttpWebRequests ve frontě za sekundu**  
  
- **HttpWebRequests přerušeno za sekundu**  
  
- **Neúspěšné HttpWebRequests/s**  
  
 U čítače **HttpWebRequests Aborted/s** se <xref:System.Net.HttpWebRequest.Abort%2A> také počítají interní volání. Tato interní volání jsou obvykle způsobena vypršením časového limitu, který aplikace může chtít změřit.  
  
 Čítač **neúspěšných HttpWebRequests/s** obsahuje počet <xref:System.Net.HttpWebRequest> objektů, které přijaly stavový kód neúspěšné ze serveru za sekundu. To znamená, že stavový kód přijatý ze serveru HTTP na konci požadavku nebyl v rozsahu od 200 do 299. Stavové kódy, které jsou zpracovávány a mají za následek novou žádost (například řada stavových kódů 401 neautorizovaných, například), selže nebo selže v závislosti na výsledku opakování. Pokud se v aplikaci při pokusu o opakování zobrazí chyba, tento čítač se zvýší.  
  
 K čítačům výkonu sítě lze přistupovat a spravovat pomocí <xref:System.Diagnostics.PerformanceCounter> tříd a souvisejících v <xref:System.Diagnostics> oboru názvů. Čítače výkonu sítě lze také zobrazit pomocí konzoly Sledování výkonu systému Windows.  
  
 V konfiguračním souboru musí být povolené čítače výkonu sítě, které se mají použít. Všechny čítače výkonu sítě jsou povoleny nebo zakázány v jednom nastavení konfiguračního souboru. Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě. Další informace naleznete v tématu [ \<performanceCounter> element (nastavení sítě)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Pokud jsou povolené síťové čítače, vytvoří a aktualizují se i globální čítače výkonu pro každou doménu. V případě zakázání aplikace nebude poskytovat žádná data čítače výkonu sítě.  
  
 Čítače výkonu jsou seskupeny do kategorií. Aplikace může zobrazit seznam všech kategorií s následujícím příkladem kódu:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Čítače výkonu sítě jsou uvedené ve dvou kategoriích:  
  
- "Sítě .NET CLR" – původní čítače výkonu zavedené ve verzi .NET Framework 2 a podporované v .NET Framework verze 2 a novější.  
  
- ".NET CLR Networking 4.0.0.0" – všechny výše uvedené čítače soketu a nové čítače výkonu podporované ve verzi .NET Framework 4 a novější. Tyto nové čítače poskytují informace o výkonu pro <xref:System.Net.HttpWebRequest> objekty.  
  
 Další informace o přístupu k čítačům výkonu a jejich správě v aplikaci najdete v tématu [čítače výkonu](performance-counters.md).  

## <a name="security-performance-counters"></a>Čítače výkonu zabezpečení  
 Kategorie zabezpečení modulu .NET CLR konzoly Performance obsahuje čítače, které poskytují informace o kontrolách zabezpečení, které modul CLR (Common Language Runtime) provádí pro aplikaci. Následující tabulka popisuje tyto čítače výkonu.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|**Počet kontrol času propojení**|Zobrazí celkový počet kontrol zabezpečení přístupu kódu při propojování od spuštění aplikace. Kontroly zabezpečení přístupu kódu při propojování se provádějí, když volající požaduje určité oprávnění v době kompilace JIT (just-in-time). Pro jednotlivého volajícího se provádí kontroly za běhu. Tento počet není informativní pro závažné problémy s výkonem. je pouze informativní aktivita systému zabezpečení.|  
|**% Času v kontrolách RT**|Zobrazuje procentuální hodnotu uplynulého času stráveného prováděním kontrol zabezpečení přístupu ke kódu za běhu od posledního vzorku. Tento čítač se aktualizuje na konci .NET Framework kontroly zabezpečení. Nejedná se o průměrnou hodnotu; představuje poslední zjištěnou hodnotu.|  
|**% Času ověřování SIG**|Vyhrazeno pro budoucí použití.|  
|**Hloubka procházení zásobníku**|Zobrazuje hloubku zásobníku během poslední kontroly zabezpečení přístupu kódu za běhu. Kontroly zabezpečení přístupu kódu za běhu se provádí procházením zásobníku. Tento čítač nepředstavuje průměr. zobrazuje jenom poslední zjištěnou hodnotu.|  
|**Celkový počet kontrol za běhu**|Zobrazuje celkový počet kontrol zabezpečení přístupu kódu za běhu, které byly provedeny od spuštění aplikace. Kontroly zabezpečení přístupu kódu za běhu se provádějí, když volající požaduje určité oprávnění. Kontrola za běhu se provádí při každém volání volajícího a prověřuje aktuální zásobník vlákna volajícího. Při použití s čítačem **hloubky procházení zásobníku** označuje tento čítač snížení výkonu, ke kterému dochází při kontrolách zabezpečení.|  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](performance-counters.md)
- [Běhová profilace](runtime-profiling.md)
