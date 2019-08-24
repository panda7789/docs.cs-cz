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
ms.openlocfilehash: edf519621c2113843b89d96948243e9c095d2a57
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988865"
---
# <a name="garbage-collection-notifications"></a>Oznámení pro kolekci paměti
Existují situace, kdy úplné uvolňování paměti (tj. generace 2) modulem CLR (Common Language Runtime) může negativně ovlivnit výkon. To může být problém zejména u serverů, které zpracovávají velké objemy požadavků. v takovém případě může dlouhý uvolňování paměti způsobit časový limit požadavku. Aby se zabránilo úplnému výskytu celé kolekce v průběhu kritického období, můžete být upozorněni na přístup k úplnému uvolňování paměti a pak provést akci přesměrování úlohy na jinou instanci serveru. Kolekci můžete také vyvolat sami a za předpokladu, že aktuální instance serveru nemusí zpracovávat požadavky.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda zaregistruje oznámení, které se vygeneruje v případě, že je k disjetí kompletní uvolňování paměti. Toto oznámení obsahuje dvě části: při přístupu k úplnému uvolňování paměti a po dokončení úplného uvolňování paměti.  
  
> [!WARNING]
> Pouze blokování uvolňování paměti vyvolává oznámení. Pokud je povolen prvek konfigurace [ \<> gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) , nebudou uvolňování paměti na pozadí vyvolávat oznámení.  
  
 Chcete-li zjistit, kdy bylo oznámení vyvoláno <xref:System.GC.WaitForFullGCApproach%2A> , <xref:System.GC.WaitForFullGCComplete%2A> použijte metody a. Obvykle tyto metody použijete ve `while` smyčce k průběžnému <xref:System.GCNotificationStatus> získávání výčtu, který zobrazuje stav oznámení. Pokud je <xref:System.GCNotificationStatus.Succeeded>tato hodnota, můžete provést následující akce:  
  
- V reakci na oznámení získané s <xref:System.GC.WaitForFullGCApproach%2A> metodou můžete přesměrovat úlohu a případně vyvolávat kolekci sami.  
  
- V reakci na oznámení získané s <xref:System.GC.WaitForFullGCComplete%2A> metodou můžete nastavit, aby byla aktuální instance serveru k dispozici pro opětovné zpracování požadavků. Můžete také shromažďovat informace. Například můžete použít <xref:System.GC.CollectionCount%2A> metodu k zaznamenání počtu kolekcí.  
  
 Metody<xref:System.GC.WaitForFullGCComplete%2A>ajsou navržené tak, aby společně <xref:System.GC.WaitForFullGCApproach%2A> spolupracovaly. Použití jednoho bez druhého může způsobit neurčité výsledky.  
  
## <a name="full-garbage-collection"></a>Úplné uvolňování paměti  
 Modul runtime způsobuje úplné uvolňování paměti v případě, kdy platí kterýkoli z následujících scénářů:  
  
- Dostatek paměti bylo povýšeno na generaci 2 a způsobilo novou kolekci 2. generace.  
  
- Do haldy velkých objektů bylo povýšeno dostatečné množství paměti, které způsobí novou kolekci 2. generace.  
  
- Kolekce 1. generace je eskalace z kolekce 2. generace z důvodu jiných faktorů.  
  
 Prahové hodnoty, které zadáte v <xref:System.GC.RegisterForFullGCNotification%2A> metodě, se vztahují na první dva scénáře. V prvním scénáři ale nebudete vždy dostávat oznámení v čase, který je úměrný prahovým hodnotám, které zadáte, ze dvou důvodů:  
  
- Modul runtime nekontroluje každé přidělení malých objektů (z důvodů výkonu).  
  
- Pouze kolekce 1. generace přivýší paměť do generace 2.  
  
 Třetí scénář také přispívá k nejistotě, kdy obdržíte oznámení. I když se nejedná o záruku, ukáže se to jako užitečný způsob, jak zmírnit důsledky neoprávněného uvolňování paměti tím, že se žádosti v této době přesměrují, nebo když kolekci vyvoláte sami, když se dá lépe přizpůsobit.  
  
## <a name="notification-threshold-parameters"></a>Parametry prahové hodnoty oznámení  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda má dva parametry pro určení prahových hodnot objektů generace 2 a haldy velkých objektů. Po splnění těchto hodnot by se mělo vyvolat oznámení o uvolňování paměti. Tyto parametry jsou popsány v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Číslo mezi 1 a 99, které určuje, kdy má být oznámení vyvoláno na základě objektů povýšených v generaci 2.|  
|`largeObjectHeapThreshold`|Číslo mezi 1 a 99, které určuje, kdy má být oznámení vyvoláno v závislosti na objektech, které jsou přiděleny v haldě velkých objektů.|  
  
 Pokud zadáte hodnotu, která je příliš vysoká, dojde k vysoké pravděpodobnosti, že obdržíte oznámení, ale může být příliš dlouhé období, než modul runtime vyvolá kolekci. Pokud kolekci vyvoláte sami, můžete získat více objektů, než by byla uvolněna v případě, že modul runtime vyvolá kolekci.  
  
 Pokud zadáte hodnotu, která je příliš nízká, modul runtime může tuto kolekci způsobit předtím, než bude dostatek času na oznámení.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu skupina serverů obsluhuje příchozí webové požadavky. Chcete-li simulovat úlohy zpracování požadavků, Bajtová pole jsou přidána do <xref:System.Collections.Generic.List%601> kolekce. Každý server zaregistruje oznámení pro uvolňování paměti a potom spustí vlákno v `WaitForFullGCProc` metodě uživatele, aby nepřetržitě <xref:System.GCNotificationStatus> sledovalo výčet <xref:System.GC.WaitForFullGCApproach%2A> , který je <xref:System.GC.WaitForFullGCComplete%2A> vrácen metodou a metodou.  
  
 Metody<xref:System.GC.WaitForFullGCComplete%2A>avolají při vyvolání oznámení příslušné metody pro zpracování událostí: <xref:System.GC.WaitForFullGCApproach%2A>  
  
- `OnFullGCApproachNotify`  
  
     Tato metoda volá `RedirectRequests` metodu uživatele, která dává pokyn serveru služby Řízení front zpráv k pozastavení odesílání požadavků na server. To je simulované nastavením proměnné `bAllocate` `false` na úrovni třídy tak, aby nebyly přiděleny žádné další objekty.  
  
     Dále je volána metoda uživatelekdokončenízpracovánípožadavkůnaserver,kteréčekajínavyřízení.`FinishExistingRequests` To se simuluje vymazáním <xref:System.Collections.Generic.List%601> kolekce.  
  
     Nakonec je vyvolaný uvolňování paměti, protože zatížení je lehké.  
  
- `OnFullGCCompleteNotify`  
  
     Tato metoda volá metodu `AcceptRequests` uživatele, aby obnovila přijímání požadavků, protože server již není náchylný k úplnému uvolňování paměti. Tato akce je simulována nastavením `bAllocate` `true` proměnné tak, aby bylo možné <xref:System.Collections.Generic.List%601> obnovit objekty do kolekce.  
  
 Následující kód obsahuje `Main` metodu příkladu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Následující kód obsahuje `WaitForFullGCProc` metodu uživatele, která obsahuje nepřetržitou smyčku while ke kontrole oznámení o uvolňování paměti.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Následující kód obsahuje `OnFullGCApproachNotify` metodu volanou z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Následující kód obsahuje `OnFullGCApproachComplete` metodu volanou z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Následující kód obsahuje uživatelské metody, které jsou volány z `OnFullGCApproachNotify` metod a. `OnFullGCCompleteNotify` Metody uživatele přesměrují požadavky, dokončí stávající žádosti a pak obnoví požadavky po úplném uvolnění paměti.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Celá ukázka kódu je následující:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
