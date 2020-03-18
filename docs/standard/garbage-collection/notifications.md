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
ms.openlocfilehash: d5646c4969c95350ab4cd63b16f6f99ffba3a4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131538"
---
# <a name="garbage-collection-notifications"></a>Oznámení pro kolekci paměti
Existují situace, ve kterých úplné uvolnění paměti (to znamená generace 2 kolekce) podle prostředí common language runtime může nepříznivě ovlivnit výkon. To může být problém zejména se servery, které zpracovávají velké objemy požadavků; v tomto případě dlouhé uvolňování paměti může způsobit časový čas požadavku. Chcete-li zabránit úplné kolekce dochází během kritického období, můžete být upozorněni, že úplné uvolnění paměti se blíží a pak provést akci k přesměrování úlohy do jiné instance serveru. Můžete také vyvolat kolekce sami, za předpokladu, že aktuální instance serveru není nutné zpracovávat požadavky.  
  
 Metoda <xref:System.GC.RegisterForFullGCNotification%2A> registruje pro oznámení, které mají být vyvolány, když za běhu cítí, že úplné uvolnění paměti se blíží. Existují dvě části tohoto oznámení: při úplné uvolňování paměti se blíží a po dokončení úplné uvolňování paměti.  
  
> [!WARNING]
> Pouze blokování uvolňování paměti vyvolat oznámení. Pokud je povolen [ \<prvek gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurace, uvolnění paměti na pozadí nevyvolá oznámení.  
  
 Chcete-li zjistit, kdy bylo <xref:System.GC.WaitForFullGCApproach%2A> vyvoláno oznámení, použijte metody a. <xref:System.GC.WaitForFullGCComplete%2A> Obvykle použijete tyto metody `while` ve smyčce neustále <xref:System.GCNotificationStatus> získat výčet, který zobrazuje stav oznámení. Pokud je <xref:System.GCNotificationStatus.Succeeded>tato hodnota , můžete provést následující kroky:  
  
- V reakci na oznámení <xref:System.GC.WaitForFullGCApproach%2A> získané pomocí metody můžete přesměrovat úlohy a případně vyvolat kolekce sami.  
  
- V reakci na oznámení <xref:System.GC.WaitForFullGCComplete%2A> získané metodou můžete zpřístupnit aktuální instanci serveru pro zpracování požadavků znovu. Můžete také shromažďovat informace. Metodu <xref:System.GC.CollectionCount%2A> můžete například použít k zaznamenání počtu kolekcí.  
  
 A <xref:System.GC.WaitForFullGCApproach%2A> metody <xref:System.GC.WaitForFullGCComplete%2A> jsou navrženy tak, aby spolupracovaly. Použití jednoho bez druhého může vést k neurčitým výsledkům.  
  
## <a name="full-garbage-collection"></a>Úplné uvolnění paměti  
 Za běhu způsobí úplné uvolnění paměti, pokud jsou splněny některé z následujících scénářů:  
  
- Dostatek paměti byla povýšena do generace 2 způsobit další generace 2 kolekce.  
  
- Dostatek paměti byla povýšena do haldy velkého objektu způsobit další generace 2 kolekce.  
  
- Kolekce generace 1 je eskalována na kolekci generace 2 kvůli jiným faktorům.  
  
 Prahové hodnoty zadané <xref:System.GC.RegisterForFullGCNotification%2A> v metodě platí pro první dva scénáře. V prvním scénáři však ne vždy obdržíte oznámení v době úměrné prahové hodnotě, kterou zadáte, ze dvou důvodů:  
  
- Runtime nekontroluje každé přidělení malých objektů (z důvodů výkonu).  
  
- Pouze generace 1 kolekce podporovat paměť do generace 2.  
  
 Třetí scénář také přispívá k nejistotě, kdy obdržíte oznámení. I když to není záruka, se ukáže jako užitečný způsob, jak zmírnit účinky nevhodnou úplné uvolnění paměti přesměrováním požadavky během této doby nebo vyvolání kolekce sami, když může být lépe přizpůsobena.  
  
## <a name="notification-threshold-parameters"></a>Parametry prahové hodnoty oznámení  
 Metoda <xref:System.GC.RegisterForFullGCNotification%2A> má dva parametry k určení prahové hodnoty generace 2 objektů a haldy velkého objektu. Pokud jsou tyto hodnoty splněny, by měla být vyvolána oznámení o uvolnění paměti. Následující tabulka popisuje tyto parametry.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Číslo mezi 1 a 99, který určuje, kdy by měla být zvýšena oznámení na základě objektů povýšen v generaci 2.|  
|`largeObjectHeapThreshold`|Číslo mezi 1 a 99, který určuje, kdy by měla být zvýšena oznámení na základě objektů, které jsou přiděleny v haldě velkého objektu.|  
  
 Pokud zadáte hodnotu, která je příliš vysoká, je vysoká pravděpodobnost, že obdržíte oznámení, ale může být příliš dlouhá doba čekání, než za běhu způsobí kolekci. Pokud vyvoláte kolekce sami, můžete získat více objektů, než by být vyvolána, pokud runtime způsobí kolekce.  
  
 Pokud zadáte hodnotu, která je příliš nízká, může za běhu způsobit kolekce dříve, než jste měli dostatek času na oznámení.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu skupina serverů obsluhuje příchozí webové požadavky. Chcete-li simulovat zatížení zpracování požadavků, bajtová <xref:System.Collections.Generic.List%601> pole jsou přidány do kolekce. Každý server registruje pro oznámení uvolnění paměti a `WaitForFullGCProc` potom spustí vlákno <xref:System.GCNotificationStatus> na metodu uživatele <xref:System.GC.WaitForFullGCApproach%2A> průběžně <xref:System.GC.WaitForFullGCComplete%2A> sledovat výčet, který je vrácen a metody.  
  
 A <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> metody volání jejich příslušné metody zpracování událostí uživatele při oznámení je aktivována:  
  
- `OnFullGCApproachNotify`  
  
     Tato metoda `RedirectRequests` volá metodu uživatele, která instruuje server služby řízení front požadavků, aby pozastavil odesílání požadavků na server. To je simulováno nastavením `bAllocate` `false` proměnné na úrovni třídy tak, aby nebyly přiděleny žádné další objekty.  
  
     Dále je `FinishExistingRequests` volána metoda uživatele k dokončení zpracování čekajících požadavků serveru. To je simulováno vymazáním <xref:System.Collections.Generic.List%601> kolekce.  
  
     Nakonec uvolňování paměti je vyvolána, protože zatížení je lehký.  
  
- `OnFullGCCompleteNotify`  
  
     Tato metoda volá `AcceptRequests` metodu uživatele k obnovení přijímání požadavků, protože server již není náchylný k úplnému uvolnění paměti. Tato akce je simulována nastavením `bAllocate` proměnné tak, aby `true` objekty mohou pokračovat v přidávání do <xref:System.Collections.Generic.List%601> kolekce.  
  
 Následující kód obsahuje `Main` metodu příkladu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Následující kód obsahuje `WaitForFullGCProc` metodu uživatele, která obsahuje nepřetržitou smyčku while pro kontrolu oznámení o uvolnění paměti.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Následující kód obsahuje `OnFullGCApproachNotify` metodu, jak je volána z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Následující kód obsahuje `OnFullGCApproachComplete` metodu, jak je volána z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Následující kód obsahuje uživatelské metody, které `OnFullGCApproachNotify` `OnFullGCCompleteNotify` jsou volány z metody a. Uživatelské metody přesměrovat požadavky, dokončit existující požadavky a potom obnovit požadavky po úplné uvolnění paměti došlo.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Celý ukázkový kód je následující:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Kolekce paměti](../../../docs/standard/garbage-collection/index.md)
