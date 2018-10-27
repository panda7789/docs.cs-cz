---
title: Vlákna a dělení na vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5049ed1b44155f3c21c53bef24a13006fe97a3fa
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452583"
---
# <a name="threads-and-threading"></a>Vlákna a dělení na vlákna
Operační systémy používat procesů k oddělení různých aplikací, které jsou spuštěny. Vlákna jsou základní jednotka, na který operační systém přiděluje čas procesoru a víc než jedno vlákno může být provádění kódu uvnitř tohoto procesu. Každé vlákno udržuje obslužné rutiny výjimek, prioritu plánování a sadu struktury, které systém používá k uložení kontext vlákna, dokud je naplánována. Kontext vlákna obsahuje všechny informace, které vlákno je potřeba bez problémů pokračovat v provádění, včetně vlákna sadu registrů CPU a zásobníku, v adresním prostoru vlákna hostitelského procesu.  
  
 Další rozhraní .NET Framework rozděluje proces operačního systému do zjednodušené spravované podprocesy, názvem domény aplikace, reprezentovaný <xref:System.AppDomain?displayProperty=nameWithType>. Jeden nebo více spravovaných vláken (představované <xref:System.Threading.Thread?displayProperty=nameWithType>) můžete spustit v jedné nebo více počet domén aplikace v rámci stejné spravovaného procesu. I když každá aplikační doména je spuštěn s jedním vláknem, kód v této doméně aplikace můžete vytvořit další domény aplikace a další vlákna. Výsledkem je, že spravovaná vlákna, můžou volně přesouvat mezi doménami aplikace uvnitř stejné spravovaného procesu; může mít pouze jedno vlákno přecházení mezi několik domén aplikace.  
  
 Operační systém, který podporuje preemptivní multitasking vytvoří efekt souběžné provádění více vláken z více procesů. Dělá to tak, že dělení dostupné procesorového času mezi vlákny, které ho potřebují, přidělení řez času procesoru pro každé vlákno jeden po druhém. Aktuálně spuštěné vlákno je pozastaveno, když uplyne řez času a další vlákno obnoví spuštění. Když systém přepínat z jednoho vlákna do druhého, uloží kontext vlákna preempted vlákna a znovu načte kontext uložený vlákna další vlákna ve frontě vlákna.  
  
 Délka časového intervalu závisí na operační systém a procesoru. Protože každém časovém řezu je malá, více vláken se spouští ve stejnou dobu, i v případě, že existuje pouze jeden procesor. To platí ve skutečnosti více procesorů systémech, kde jsou spustitelné vlákna distribuovat mezi dostupné procesory.  
  
## <a name="when-to-use-multiple-threads"></a>Použití více vláken  
 Software, který vyžaduje zásah uživatele musí reagovat na činnost uživatele co nejrychleji k poskytování bohaté uživatelské prostředí. Ve stejnou dobu ale je třeba postupovat výpočty potřebné k prezentaci dat pro uživatele co nejrychleji. Pokud vaše aplikace používá pouze jedno vlákno provádění, můžete kombinovat [asynchronní programování](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) s [vzdálené komunikace rozhraní .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100)) nebo [webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100)) vytvořené pomocí ASP .NET pomocí doba zpracování jiných počítačů, kromě toho, který vlastní zvýšit rychlost odezvy pro uživatele a zkrácení doby zpracování dat vaší aplikace. Pokud provádíte náročné na vstupně výstupní práce, také vám pomůže portů dokončení vstupně-výstupních operací jim zrychlit odezvu vaší aplikace.  
  
### <a name="advantages-of-multiple-threads"></a>Výhody více vláken  
 Pomocí více než jedno vlákno, ale je možné zvýšit rychlost odezvy pro uživatele a zpracovat data potřebná k dosažení téměř současně procesorově nejvýkonnější postup. Na počítači s jedním procesorem můžete vytvořit více vláken tohoto efektu výhod malé tečky času mezi uživatelem události ke zpracování dat na pozadí. Například uživatel může upravovat tabulky, zatímco jiné vlákno je přepočítání dalších součástí tabulky v rámci stejné aplikace.  
  
 Bez jakýchkoli úprav by tu samou aplikaci výrazně zvýšit spokojenost uživatelů při spuštění v počítači s více než jeden procesor. Jedné aplikační domény použít více vláken k provádění následujících úloh:  
  
-   Komunikovat přes síť, na webový server a k databázi.  
  
-   Provádění operací, které provést velké množství času.  
  
-   Rozlišení úlohy různé priority. Například vlákno s vysokou prioritou spravuje náročné úlohy a vlákno s nízkou prioritou provede další úlohy.  
  
-   Povolte uživatelské rozhraní pro zpřístupněním, při přidělování čas úlohy na pozadí.  
  
### <a name="disadvantages-of-multiple-threads"></a>Nevýhody více vláken  
 Doporučuje se použít jako několik vláken jako možné, a tím minimalizovat použití operačního systému prostředků a zlepšení výkonu. Práce s vlákny má také požadavky na prostředky a potenciální konflikty vzít v úvahu při navrhování vaší aplikace. Požadavky na prostředky jsou následující:  
  
-   Systém vyžaduje paměť pro informace o kontextu požadované procesy, **AppDomain** objekty a vlákna. Proto se počet procesů, **AppDomain** dostupné paměti je omezená objekty a vlákna, které je možné vytvořit.  
  
-   Udržování přehledu o velkém počtu vláken spotřebovává významný čas procesoru. Pokud existuje příliš mnoho vláken, většina z nich nebude pokroku významné. Pokud je většina aktuálních vláken v jednom procesu, vlákna v jiné procesy jsou naplánovány méně často.  
  
-   Řízení provádění kódu s několika vlákny je složitá a může být zdrojem je mnoho chyb.  
  
-   Zničení vláken vyžaduje vědět, co se může stát a zpracování těchto problémů.  
  
 Poskytuje sdílený přístup k prostředkům, mohou vytvářet konflikty. Aby nedocházelo ke konfliktům, musíte synchronizovat nebo řízení přístupu ke sdíleným prostředkům. Selhání pro synchronizaci přístupu správně (v jednom nebo několika aplikačních doménách) může vést k problémům, například (v které dvěma vlákny přestane reagovat při každé čeká na dokončení jiné) zablokování a konflikty časování (když výsledek neobvyklé dochází z důvodu neočekávané důležitým obchodním časování dvě události). Poskytuje tento systém synchronizaci objektů, které slouží ke koordinaci mezi více vlákny sdílení prostředků. Snížení počtu vláken usnadňuje synchronizovat prostředky.  
  
 Prostředky, které vyžadují synchronizaci patří:  
  
-   Systémové prostředky (například komunikační porty).  
  
-   Prostředky sdílena několika procesy (jako jsou popisovače souborů).  
  
-   Prostředky z jedné aplikace domény aplikace (jako je například globální, statická a instance pole) přístup prostřednictvím více vláken.  
  
### <a name="threading-and-application-design"></a>Návrh pro dělení na vlákna a aplikace  
 Obecně platí, pomocí <xref:System.Threading.ThreadPool> třída je nejjednodušší způsob, jak zpracovávat více vláken poměrně krátké úlohy, která nebude blokovat ostatní vlákna a pokud neočekáváte konkrétní plánování úloh. Existují však několik důvodů k vytváření vlastních vláken:  
  
-   Pokud potřebujete úlohu s konkrétní prioritou.  
  
-   Pokud máte úlohu, která může být dlouhý čas spuštění (a blokovat další úlohy).  
  
-   Pokud potřebujete umístit vlákna do jednovláknový apartment (všechny **fondu vláken** jsou vlákna v s více vlákny typu apartment).  
  
-   Pokud potřebujete stabilní identitu přidruženou k vláknu. Například by měl použít vyhrazené vlákno přerušit bylo vlákno, jej pozastavit nebo vyhledat podle názvu.  
  
-   Pokud je potřeba spustit vláken na pozadí, které pracují s uživatelským rozhraním, poskytuje rozhraní .NET Framework verze 2.0 <xref:System.ComponentModel.BackgroundWorker> komponenta, která komunikuje pomocí události, zařazování mezi vlákny vlákno uživatelského rozhraní.  
  
### <a name="threading-and-exceptions"></a>Zřetězení a výjimky  
 Zpracování výjimek ve vláknech. Neošetřené výjimky ve vláknech, dokonce i na pozadí podprocesů, obecně ukončit proces. Existují tři výjimkou tohoto pravidla:  
  
-   A <xref:System.Threading.ThreadAbortException> je vyvolána ve vlákně, protože <xref:System.Threading.Thread.Abort%2A> byla volána.  
  
-   <xref:System.AppDomainUnloadedException> Je vyvolána ve vlákně, protože probíhá uvolnění domény aplikace.  
  
-   Modul common language runtime nebo hostitelský proces ukončí vlákno.  
  
 Další informace najdete v tématu [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1 modul common language runtime bezobslužně traps některé výjimky, například v vláken fondu vláken. Toto může poškodit stav aplikace a nakonec způsobit, že aplikace přestane reagovat, které může být velmi obtížné ladit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadPool>  
- <xref:System.ComponentModel.BackgroundWorker>  
- [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [Spravovaný fond vláken](../../../docs/standard/threading/the-managed-thread-pool.md)
