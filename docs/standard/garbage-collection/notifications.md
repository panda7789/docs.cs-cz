---
title: "Oznámení pro kolekci paměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41a2ed9c5d239f1570955e87bb5b749e29830bc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-notifications"></a>Oznámení pro kolekci paměti
Existují situace, ve kterých může kolekci úplného uvolňování paměti (který je kolekcí generace 2) podle modul common language runtime nepříznivě ovlivnit výkon. To může být problém zvláště u serverů, které zpracovávají velké objemy požadavků. v takovém případě dlouho uvolňování může způsobit časový limit požadavku. Pokud chcete zabránit úplnou kolekci z výskytu kritické období, můžete být upozorněni, kolekci úplného uvolňování paměti se blíží a pak proveďte akce přesměrování zatížení k jiné instanci serveru. Můžete může také způsobit kolekci sami, za předpokladu, že aktuální instance serveru nemusí zpracovávat žádosti.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda registruje pro oznámení se vyvolá, když modul runtime detekuje, že se blíží úplné uvolnění paměti. Toto oznámení, skládá ze dvou částí: když se blíží kolekci úplného uvolňování paměti a po dokončení úplné uvolnění paměti.  
  
> [!WARNING]
>  Pouze blokující kolekce paměti vyvolat oznámení. Když [ \<gcconcurrent – >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurační prvek je povoleno, pozadí kolekce nevydá oznámení.  
  
 Chcete-li zjistit, kdy bylo vyvoláno upozornění, použijte <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody. Obvykle se používá tyto metody v `while` opakování ve smyčce bude průběžně získat <xref:System.GCNotificationStatus> výčet, který se zobrazí stav oznámení. Pokud je tato hodnota <xref:System.GCNotificationStatus.Succeeded>, můžete provést následující:  
  
-   V reakci na oznámení, které byly získány <xref:System.GC.WaitForFullGCApproach%2A> metodu, můžete přesměrovat zatížení a případně vyvolat kolekci sami.  
  
-   V reakci na oznámení, které byly získány <xref:System.GC.WaitForFullGCComplete%2A> metodu, můžete provést aktuální instanci serveru, která je k dispozici pro zpracování požadavků zopakovat. Může také shromažďovat informace. Například můžete použít <xref:System.GC.CollectionCount%2A> metoda zaznamenání počet kolekcí.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody se nedají používat společně. Pomocí jednoho bez dalších může vytvářet neurčitém výsledky.  
  
## <a name="full-garbage-collection"></a>Úplné uvolňování paměti  
 Modul runtime způsobí kolekce úplného uvolňování paměti, když některá z následujících scénářů:  
  
-   Dostatek paměti, se použije do 2 způsobí další kolekce generace 2. generace.  
  
-   Dostatek paměti, se použije do velkého objektu haldy způsobí další kolekce 2. generace.  
  
-   Kolekce generace 1 je Eskalovat do kolekce generace 2 z důvodu dalších faktorů.  
  
 Prahové hodnoty v zadáte <xref:System.GC.RegisterForFullGCNotification%2A> metoda platí pro první dva scénáře. První scénář, nebude však vždycky dostat oznámení v době úměrná prahové hodnoty, které zadáte dvou důvodů:  
  
-   Modul runtime nekontroluje každý přidělení malé objektu (z důvodů výkonu).  
  
-   Pouze generace 1 kolekce povýšení paměti do 2. generace.  
  
 Třetí scénář také přispívá k nejistoty z když obdržíte oznámení. I když to není záruku, ukáže jako vhodný způsob, jak pomocí přesměrování požadavků během této doby nebo zcizení kolekce, sami při můžete se lépe shromáždit, a minimalizoval vliv kolekci nevhodnou úplného uvolňování paměti.  
  
## <a name="notification-threshold-parameters"></a>Oznámení prahové hodnoty parametrů  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda má dva parametry k určení prahové hodnoty objekty 2. generace a haldě velkého objektu. Pokud jsou splněny tyto hodnoty, má se vrhnout oznámení kolekce paměti. Následující tabulka popisuje tyto parametry.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Číslo mezi 1 a 99, která určuje, kdy by měl vyvolána oznámení založené na objektech podporována ve 2. generace.|  
|`largeObjectHeapThreshold`|Číslo mezi 1 a 99, která určuje, kdy by měl vyvolána oznámení založené na objekty, které mají při přidělování v haldě velkého objektu.|  
  
 Pokud zadáte hodnotu, která je příliš vysoká, je vysoká pravděpodobnost, že dostanete oznámení, ale může být příliš dlouhou dobou čekání před modulu runtime způsobí, že kolekce. Pokud jste vyvolat kolekci sami, může získat více objektů, než by uvolnit, pokud modul runtime, způsobí kolekce.  
  
 Pokud zadáte hodnotu, která je příliš nízká, modul runtime může způsobit kolekce předtím, než jste předtím dostatek času na upozorněni.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu skupiny serverů služby příchozích webových požadavků. Pro simulaci zatížení zpracování žádostí, bajtová pole jsou přidány do <xref:System.Collections.Generic.List%601> kolekce. Každý server zaregistruje pro oznámení kolekce paměti a pak spustí vlákna na `WaitForFullGCProc` uživatele metoda neustále monitorovat <xref:System.GCNotificationStatus> výčet, který je vrácený <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody volání svých uživatelů metod zpracování událostí po vyvolání oznámení:  
  
-   `OnFullGCApproachNotify`  
  
     Tato metoda volá `RedirectRequests` uživatele metoda, která nastaví server služby Řízení front žádost o pozastavení odesílání požadavků na server. To se simuluje nastavení proměnné úrovni třídy `bAllocate` k `false` tak, že jsou přiděleny žádné další objekty.  
  
     Dále `FinishExistingRequests` uživatele metoda je volána k dokončení zpracování žádosti čekající na serveru. To se simuluje zrušením <xref:System.Collections.Generic.List%601> kolekce.  
  
     Kolekce paměti je nakonec vyvolané, protože zatížení je light.  
  
-   `OnFullGCCompleteNotify`  
  
     Tato metoda volá metodu uživatele `AcceptRequests` obnovit přijímá žádosti, protože server už je ohrožena útoky založenými na kolekci úplného uvolňování paměti. Tato akce se simuluje nastavení `bAllocate` proměnnou `true` tak, aby objekty může pokračovat, který se přidává do <xref:System.Collections.Generic.List%601> kolekce.  
  
 Obsahuje následující kód `Main` metoda v příkladu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Obsahuje následující kód `WaitForFullGCProc` metoda uživatele, který obsahuje nepřetržitou při opakování ve smyčce bude kontrolovat oznámení pro uvolňování paměti.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Obsahuje následující kód `OnFullGCApproachNotify` metoda, jak volat z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Obsahuje následující kód `OnFullGCApproachComplete` metoda, jak volat z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Následující kód obsahuje metody uživatele, které se nazývají z `OnFullGCApproachNotify` a `OnFullGCCompleteNotify` metody. Metody uživatele přesměrovat požadavky, existující žádosti o dokončení a poté obnovit požadavky po úplné uvolnění paměti došlo k chybě.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Ukázka celý kódu vypadá takto:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
