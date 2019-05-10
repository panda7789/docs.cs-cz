---
title: Oznámení pro kolekci paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc4850ff87d9ea827e86a16ee6b3a6953c1e3552
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622711"
---
# <a name="garbage-collection-notifications"></a>Oznámení pro kolekci paměti
Existují situace, ve kterých může úplného uvolňování paměti kolekce (to znamená, že kolekce generace 2) modulem common language runtime nepříznivě ovlivnit výkon. To může být problém zvláště u serverů, které zpracovávají velký objem požadavků. v takovém případě dlouhé uvolnění paměti může způsobit vypršení časového limitu požadavku. Pokud chcete zabránit celé kolekce, ze které se vyskytují během kritických období, můžete být upozorněni, že úplné uvolnění paměti se blíží a pak provedete akce vedoucí k přesměrování zatížení k jiné instanci serveru. Můžete také zahájit kolekce sami, za předpokladu, že není potřeba zpracovávat požadavky na aktuální instanci serveru.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda registruje pro oznámení, chcete-li být vyvolána, když modul runtime detekuje, že se blíží úplného uvolňování paměti kolekce. Existují dvě části pro toto oznámení: když se blíží úplného uvolňování paměti kolekce a po dokončení úplného uvolňování paměti kolekce.  
  
> [!WARNING]
>  Blokování uvolnění paměti pouze zvýšit oznámení. Když [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurační element je povolen, nevyvolá uvolnění paměti na pozadí, oznámení.  
  
 Chcete-li zjistit, kdy bylo vyvoláno upozornění, použijte <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody. Obvykle se používají tyto metody v `while` smyčky průběžně získat <xref:System.GCNotificationStatus> výčet, který se zobrazuje stav oznámení. Pokud je tato hodnota <xref:System.GCNotificationStatus.Succeeded>, abyste udělali toto:  
  
- V reakci na oznámení získali díky <xref:System.GC.WaitForFullGCApproach%2A> metodu, můžete přesměrovat úlohy a potenciálně způsobit kolekce sami.  
  
- V reakci na oznámení získali díky <xref:System.GC.WaitForFullGCComplete%2A> metodu, můžete provést aktuální instance serveru k dispozici pro zpracování požadavků znovu. Může také shromažďovat informace. Například můžete použít <xref:System.GC.CollectionCount%2A> metoda k zaznamenání počtu kolekcí.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody jsou navrženy pro práci společně. Pomocí jednoho bez nich můžete výsledky neurčitý.  
  
## <a name="full-garbage-collection"></a>Úplné uvolňování paměti  
 Modul runtime způsobuje úplného uvolňování paměti kolekce, když je splněna některá z následujících scénářů:  
  
- Dostatek paměti má byla povýšeny do generace 2 způsobit další generaci 2 kolekce.  
  
- Dostatek paměti byl povýšen na velkých objektových haldách způsobit další generaci 2 kolekce.  
  
- Sběr generace 1 je eskalován jej kolekce generace 2 z důvodu dalších faktorů.  
  
 Prahové hodnoty, které zadáte <xref:System.GC.RegisterForFullGCNotification%2A> metoda platí pro první dva scénáře. První scénář, nebude však vždycky dostat oznámení v době úměrná prahové hodnoty, kterou zadáte pro dva důvody:  
  
- Modul runtime nekontroluje každý přidělení malých objektů (z důvodů výkonu).  
  
- Pouze generace 1 kolekce propagace paměti do 2. generace.  
  
 Třetí scénář také přispívá ke nejistota když bude oznámení zasláno. I když to není zárukou, že bude užitečný způsob, jak zmírnit efekty nevhodnou úplného uvolňování přesměrování požadavků během této doby nebo nevyvolá kolekci, sami když ho může lépe vyhovovat.  
  
## <a name="notification-threshold-parameters"></a>Parametry prahová hodnota oznámení  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda má dva parametry k určení prahové hodnoty 2. generace objektů a haldy pro velké objekty. Pokud jsou splněny tyto hodnoty, by měla být zvýšena oznámení uvolnění paměti. Následující tabulka popisuje tyto parametry.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Číslo mezi 1 a 99, která určuje, kdy by měla být zvýšena oznámení založené na objektech, které jsou povýšeny do generace 2.|  
|`largeObjectHeapThreshold`|Číslo mezi 1 a 99, která určuje, kdy by měla být zvýšena oznámení založené na objektech, které jsou přiděleny do haldy pro velké objekty.|  
  
 Pokud zadáte hodnotu, která je příliš vysoká, je vysoká pravděpodobnost, že bude zasláno oznámení, ale může být příliš dlouhou dobou čekat, než modul runtime způsobí, že kolekce. Pokud jste zahájit kolekce sami, může uvolnit více objektů, než by uvolnit, pokud modul runtime způsobí, že kolekce.  
  
 Pokud zadáte hodnotu, která je příliš nízká, modul runtime může způsobit kolekci předtím, než máte dostatek času na upozornění.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu skupiny serverů služby příchozích webových požadavků. Pro simulaci zatížení zpracování požadavků, bajtová pole se přidají do <xref:System.Collections.Generic.List%601> kolekce. Každý server zaregistruje pro oznámení uvolnění paměti a poté spustí vlákno na `WaitForFullGCProc` metody uživatele k nepřetržitému monitorování <xref:System.GCNotificationStatus> výčet, který je vrácený <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody volání svých metod uživatele zpracování událostí při vyvolání oznámení:  
  
- `OnFullGCApproachNotify`  
  
     Tato metoda volá `RedirectRequests` metody uživatele, který nastaví server služby Řízení front žádost o pozastavení odesílání požadavku na server. To se simuluje nastavením proměnné úrovni třídy `bAllocate` k `false` tak, aby se přidělují žádné další objekty.  
  
     Dále `FinishExistingRequests` uživatele metoda je volána na dokončení zpracování žádosti čekající na vyřízení serveru. To se simuluje zrušením <xref:System.Collections.Generic.List%601> kolekce.  
  
     Uvolňování paměti je vyvolaných finally, protože je zatížení světla.  
  
- `OnFullGCCompleteNotify`  
  
     Tato metoda volá metodu uživatele `AcceptRequests` obnovit přijímá žádosti, protože na serveru už není náchylné k úplné uvolnění paměti. Tato akce se simuluje tak, že nastavíte `bAllocate` proměnnou `true` tak, aby objekty může pokračovat se přidávají do <xref:System.Collections.Generic.List%601> kolekce.  
  
 Následující kód obsahuje `Main` metoda v příkladu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Následující kód obsahuje `WaitForFullGCProc` metody uživatele, obsahující průběžné ke kontrole oznámení pro kolekci paměti smyčku while.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Následující kód obsahuje `OnFullGCApproachNotify` způsob, jak volat z  
  
 `WaitForFullGCProc` Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Následující kód obsahuje `OnFullGCApproachComplete` způsob, jak volat z  
  
 `WaitForFullGCProc` Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Následující kód obsahuje metody uživatele, které se volají z `OnFullGCApproachNotify` a `OnFullGCCompleteNotify` metody. Metody uživatele přesměrování požadavků, Dokončit existující žádosti o a poté obnovit požadavky po úplné uvolnění paměti došlo k chybě.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Vzorový kód celé vypadá takto:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
