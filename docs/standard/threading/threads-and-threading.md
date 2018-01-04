---
title: "Vlákna a dělení na vlákna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 91db5cf75053f7a9b343036345a97d8084ae38fb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="threads-and-threading"></a>Vlákna a dělení na vlákna
Operační systémy pomocí procesů k oddělení různých aplikací, které jsou spuštěny. Vláken je základní jednotkou, které operační systém přiděluje čas procesoru a víc než jedno vlákno může provádění kódu uvnitř tohoto procesu. Každé vlákno udržuje obslužné rutiny výjimek, plánování prioritu a sadu struktury, které používá systém uložit kontext přístup z více vláken, dokud je naplánována. Kontext vlákno obsahuje všechny informace, které vlákno je potřeba bezproblémově pokračovat v provádění, včetně vlákna sadu registrů CPU a zásobník v adresním prostoru procesu hostitele vlákna.  
  
 Rozhraní .NET Framework další rozděluje procesu operačního systému do lightweight spravované podprocesů, které, názvem domény aplikace reprezentována <xref:System.AppDomain?displayProperty=nameWithType>. Jeden nebo více spravovaných vláknech (reprezentována <xref:System.Threading.Thread?displayProperty=nameWithType>) můžete spustit v jedné nebo více domén aplikací v rámci stejné spravovaného procesu. Přestože každé domény aplikace spustí s jedním vláknem, kód v této doméně vytvořit další domény aplikace a další vlákna. Výsledkem je, že spravované vlákno můžete volně přesouvat mezi doménami aplikací uvnitř stejné spravovaného procesu; Můžete mít pouze jedno vlákno přesun mezi několik domén aplikace.  
  
 Operační systém, který podporuje preemptivní multitasking vytvoří z několika procesů účinku současné spouštění více vláken. Dělá to pomocí dělení dostupné procesorového času mezi vláken, která ho potřebovat, přidělování řez času procesoru pro každé vlákno, jedna po druhé. Aktuálně prováděné vlákno je pozastaveno, po dobu jeho uplynutí řez a další vlákna obnoví systémem. Pokud systém přepínat mezi jednotlivými vlákny na jiný, uloží kontextu vláken preempted vlákno a znovu načte uložené vlákno kontextu další vlákno ve frontě přístup z více vláken.  
  
 Délka časového intervalu závisí na operační systém a procesoru. Protože každý řez čas je malá, více vláken pravděpodobně provedl ve stejnou dobu, i když je pouze jeden procesor. Toto je ve skutečnosti případu v systémech s více procesory, kde jsou spustitelné vláken distribuovány mezi dostupných procesorů.  
  
## <a name="when-to-use-multiple-threads"></a>Kdy použít více vláken  
 Software, který vyžaduje zásah uživatele musí reagovat na aktivity uživatele co nejrychleji a poskytuje bohaté uživatelské prostředí. Ve stejnou dobu ale musíte postupovat výpočty potřebné pro zobrazení dat tak rychlé nejblíže uživatele. Pokud vaše aplikace používá pouze jedno vlákno provádění, můžete kombinovat [asynchronní programování](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) s[vzdálené komunikace rozhraní .NET Framework](http://msdn.microsoft.com/en-us/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) nebo [webové služby XML](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c) vytvořený ASP .NET pomocí bude čas zpracování dalších počítačů kromě u vlastního zvýšit rychlost odezvy pro uživatele a snižte dobu zpracování dat aplikace. Pokud provádíte náročné práce vstupu a výstupu, můžete taky vstupně-výstupních operací dokončení porty zvýšit rychlost reakce aplikace.  
  
### <a name="advantages-of-multiple-threads"></a>Výhody více vláken  
 Použití více než jedno vlákno, je však nejúčinnějších technik, které jsou k dispozici pro zvýšení rychlosti reakce na uživatele a zpracovat data potřebná k provedení úlohy téměř stejnou dobu. Na počítači s jeden procesor můžete vytvořit více vláken tento platit, využívat výhod malé období mezi uživatelem události ke zpracování dat na pozadí. Uživatel například můžete upravit tabulkou, zatímco jiné vlákno je přepočítání dalších částí tabulky v rámci stejné aplikaci.  
  
 Bez úprav stejná aplikace by výrazně zvýšit spokojenost uživatelů při spuštění v počítači s více než jeden procesor. Doménu jednu aplikaci použít více vláken k provádění následujících úloh:  
  
-   Komunikují přes síť, na webový server a k databázi.  
  
-   Proveďte operace, které trvat velké množství času.  
  
-   Rozlišení úlohy různých priority. Například s vysokou prioritou vlákna spravuje kritický pro čas úlohy a nízkou prioritu vlákna provede další úlohy.  
  
-   Povolit uživatelské rozhraní zůstanou reakce, při přidělování čas úlohy na pozadí.  
  
### <a name="disadvantages-of-multiple-threads"></a>Nevýhody více vláken  
 Doporučuje se používat jako několik vláken jako možný, a současně minimalizujete její použití operačního systému prostředků a zlepšení výkonu. Dělení na vlákna má také požadavky na prostředky a potenciální konflikty, aby byla považována za při navrhování vaší aplikace. Požadavky na prostředky jsou následující:  
  
-   Systém vyžaduje paměť pro informace o kontextu, které vyžadují procesy, **AppDomain** objekty a vláken. Proto je počet procesů, **AppDomain** objekty a vláken, které lze vytvořit, je omezen dostupné paměti.  
  
-   Udržování přehledu o velký počet vláken spotřebovává významný využití procesoru. Pokud jsou moc velký počet vláken, většina z nich nebudou dosáhnout výrazné pokroku. Pokud je většina aktuální vláken v jednom procesu, jsou naplánovány méně často vláken v jiné procesy.  
  
-   Řízení provádění kódu s mnoha vláken je složitý a může být zdrojem celou řadu chyb.  
  
-   Zničení vláken vyžaduje zároveň budete vědět, co může nastat a zpracování těchto problémů.  
  
 Poskytuje sdílený přístup k prostředkům, mohou vytvářet konflikty. Aby nedocházelo ke konfliktům, musíte synchronizovat nebo řízení přístupu ke sdíleným prostředkům. Selhání synchronizace přístupu správně (ve stejné nebo jiné aplikace domény) může vést k problémům, třeba blokování (v které dvěma vlákny přestane reagovat při každé čeká na dokončení dalších) soupeření podmínky (Pokud je výsledek neobvyklé dochází z důvodu neočekávané kritické závislost na načasování dvě události). Systém poskytuje synchronizačními objekty, které slouží ke koordinaci prostředků sdílení mezi více vláken. Snižuje počet vláken, usnadňuje synchronizovat prostředky.  
  
 Prostředky, které vyžadují synchronizaci patří:  
  
-   Systémové prostředky (třeba portů komunikace).  
  
-   Prostředky sdílené více procesy (například obslužných rutin souborů).  
  
-   Prostředky domény jednu aplikaci (například globální, statické a instanci pole) přistupovat pomocí více vláken.  
  
### <a name="threading-and-application-design"></a>Návrh vláken a aplikace  
 Obecně platí, pomocí <xref:System.Threading.ThreadPool> třída je nejjednodušší způsob, jak zpracovat více vláken pro poměrně krátké úlohy, která se nebude blokovat jiná vlákna a pokud neočekáváte konkrétní plánování úloh. Existují však několik důvodů, proč vytvořit vlastní vláken:  
  
-   Pokud potřebujete úlohu tak, aby měl s konkrétní prioritou.  
  
-   Pokud máte úlohu, která může spustit po dlouhou dobu (a proto blokovat další úkoly).  
  
-   Pokud je třeba umístit do single-threaded apartment vláken (všechny **zachovalo** vláken jsou ve více vláken typu apartment).  
  
-   Pokud potřebujete stabilní identita spojená s vlákno. Například by měl použít vyhrazený vlákno zrušení daném vláknu, pozastavit je nebo vyhledat podle názvu.  
  
-   Pokud potřebujete spustit vlákna na pozadí, které zajišťují interakci s uživatelským rozhraním, poskytuje rozhraní .NET Framework verze 2.0 <xref:System.ComponentModel.BackgroundWorker> komponenty, která komunikuje pomocí události, mezi vlákny zařazování do vlákna uživatelského rozhraní.  
  
### <a name="threading-and-exceptions"></a>Zřetězení a výjimek  
 Zpracování výjimek v vláken. Nezpracované výjimky v vláken vlákna na pozadí i, obecně ukončit proces. Existují tři výjimky pro toto pravidlo:  
  
-   A <xref:System.Threading.ThreadAbortException> je vyvolána v vlákno, protože <xref:System.Threading.Thread.Abort%2A> byla volána.  
  
-   <xref:System.AppDomainUnloadedException> Je vyvolána v vlákno, protože odpojení domény aplikace.  
  
-   Modul common language runtime nebo hostitelský proces se ukončuje vlákno.  
  
 Další informace najdete v tématu [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1 modul common language runtime bezobslužně traps některé výjimky, například v podprocesy z fondu podprocesů. To může poškodit stav aplikace a nakonec způsobit, že aplikace přestane reagovat, což může být velmi obtížné ladění.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Spravovaný fond vláken](../../../docs/standard/threading/the-managed-thread-pool.md)
