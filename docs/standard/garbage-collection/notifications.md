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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131538"
---
# <a name="garbage-collection-notifications"></a>Oznámení pro kolekci paměti
Existují situace, kdy úplné uvolňování paměti (tj. generace 2) modulem CLR (Common Language Runtime) může negativně ovlivnit výkon. To může být problém zejména u serverů, které zpracovávají velké objemy požadavků. v takovém případě může dlouhý uvolňování paměti způsobit časový limit požadavku. Aby se zabránilo úplnému výskytu celé kolekce v průběhu kritického období, můžete být upozorněni na přístup k úplnému uvolňování paměti a pak provést akci přesměrování úlohy na jinou instanci serveru. Kolekci můžete také vyvolat sami a za předpokladu, že aktuální instance serveru nemusí zpracovávat požadavky.  
  
 Metoda <xref:System.GC.RegisterForFullGCNotification%2A> zaregistruje oznámení, aby se vyvolalo v případě, že se blíží modul runtime, který se blíží k celému uvolňování paměti. Toto oznámení obsahuje dvě části: při přístupu k úplnému uvolňování paměti a po dokončení úplného uvolňování paměti.  
  
> [!WARNING]
> Pouze blokování uvolňování paměti vyvolává oznámení. Když je povolený prvek konfigurace [\<gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) , nebudou uvolňování paměti na pozadí vyvolávat oznámení.  
  
 Chcete-li zjistit, kdy bylo oznámení vyvoláno, použijte metody <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A>. Obvykle tyto metody použijete ve smyčce `while` k průběžnému získávání <xref:System.GCNotificationStatus> výčtu, který zobrazuje stav oznámení. Pokud je tato hodnota <xref:System.GCNotificationStatus.Succeeded>, můžete provést následující akce:  
  
- V reakci na oznámení získané pomocí metody <xref:System.GC.WaitForFullGCApproach%2A> můžete přesměrovat úlohu a případně vyvolávat kolekci sami.  
  
- V reakci na oznámení získané pomocí metody <xref:System.GC.WaitForFullGCComplete%2A> můžete nastavit, aby byla aktuální instance serveru k dispozici pro opětovné zpracování požadavků. Můžete také shromažďovat informace. Například můžete použít metodu <xref:System.GC.CollectionCount%2A> k zaznamenání počtu kolekcí.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody jsou navržené tak, aby společně fungovaly. Použití jednoho bez druhého může způsobit neurčité výsledky.  
  
## <a name="full-garbage-collection"></a>Úplné uvolňování paměti  
 Modul runtime způsobuje úplné uvolňování paměti v případě, kdy platí kterýkoli z následujících scénářů:  
  
- Dostatek paměti bylo povýšeno na generaci 2 a způsobilo novou kolekci 2. generace.  
  
- Do haldy velkých objektů bylo povýšeno dostatečné množství paměti, které způsobí novou kolekci 2. generace.  
  
- Kolekce 1. generace je eskalace z kolekce 2. generace z důvodu jiných faktorů.  
  
 Prahové hodnoty, které zadáte v metodě <xref:System.GC.RegisterForFullGCNotification%2A>, se vztahují na první dva scénáře. V prvním scénáři ale nebudete vždy dostávat oznámení v čase, který je úměrný prahovým hodnotám, které zadáte, ze dvou důvodů:  
  
- Modul runtime nekontroluje každé přidělení malých objektů (z důvodů výkonu).  
  
- Pouze kolekce 1. generace přivýší paměť do generace 2.  
  
 Třetí scénář také přispívá k nejistotě, kdy obdržíte oznámení. I když se nejedná o záruku, ukáže se to jako užitečný způsob, jak zmírnit důsledky neoprávněného uvolňování paměti tím, že se žádosti v této době přesměrují, nebo když kolekci vyvoláte sami, když se dá lépe přizpůsobit.  
  
## <a name="notification-threshold-parameters"></a>Parametry prahové hodnoty oznámení  
 Metoda <xref:System.GC.RegisterForFullGCNotification%2A> má dva parametry, které určují mezní hodnoty objektů generace 2 a haldy velkých objektů. Po splnění těchto hodnot by se mělo vyvolat oznámení o uvolňování paměti. Tyto parametry jsou popsány v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Číslo mezi 1 a 99, které určuje, kdy má být oznámení vyvoláno na základě objektů povýšených v generaci 2.|  
|`largeObjectHeapThreshold`|Číslo mezi 1 a 99, které určuje, kdy má být oznámení vyvoláno v závislosti na objektech, které jsou přiděleny v haldě velkých objektů.|  
  
 Pokud zadáte hodnotu, která je příliš vysoká, dojde k vysoké pravděpodobnosti, že obdržíte oznámení, ale může být příliš dlouhé období, než modul runtime vyvolá kolekci. Pokud kolekci vyvoláte sami, můžete získat více objektů, než by byla uvolněna v případě, že modul runtime vyvolá kolekci.  
  
 Pokud zadáte hodnotu, která je příliš nízká, modul runtime může tuto kolekci způsobit předtím, než bude dostatek času na oznámení.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu skupina serverů obsluhuje příchozí webové požadavky. Chcete-li simulovat úlohy zpracování požadavků, Bajtová pole jsou přidána do kolekce <xref:System.Collections.Generic.List%601>. Každý server se registruje pro oznámení o uvolňování paměti a potom spustí vlákno na metodě `WaitForFullGCProc` User pro nepřetržité monitorování výčtu <xref:System.GCNotificationStatus>, který vrací <xref:System.GC.WaitForFullGCApproach%2A> a metody <xref:System.GC.WaitForFullGCComplete%2A>.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> a metody <xref:System.GC.WaitForFullGCComplete%2A> volají při vyvolání oznámení příslušné metody pro zpracování událostí:  
  
- `OnFullGCApproachNotify`  
  
     Tato metoda volá metodu `RedirectRequests` uživatele, která dává pokyn serveru služby Řízení front zpráv k pozastavení odesílání požadavků na server. To se simuluje nastavením proměnné na úrovni třídy `bAllocate` tak, aby `false` tak, že nejsou přiděleny žádné další objekty.  
  
     Dále je volána metoda uživatele `FinishExistingRequests` k dokončení zpracování požadavků na server, které čekají na vyřízení. To se simuluje vymazáním kolekce <xref:System.Collections.Generic.List%601>.  
  
     Nakonec je vyvolaný uvolňování paměti, protože zatížení je lehké.  
  
- `OnFullGCCompleteNotify`  
  
     Tato metoda volá metodu uživatele `AcceptRequests`, aby obnovila přijímání požadavků, protože server již není náchylný k úplnému uvolňování paměti. Tato akce se simuluje nastavením proměnné `bAllocate` na `true`, aby se objekty mohly do kolekce <xref:System.Collections.Generic.List%601> přidat.  
  
 Následující kód obsahuje metodu `Main` v příkladu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Následující kód obsahuje metodu `WaitForFullGCProc` uživatele, která obsahuje průběžnou smyčku while ke kontrole oznámení o uvolňování paměti.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Následující kód obsahuje metodu `OnFullGCApproachNotify`, jak je volána z  
  
 Metoda `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Následující kód obsahuje metodu `OnFullGCApproachComplete`, jak je volána z  
  
 Metoda `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Následující kód obsahuje uživatelské metody, které jsou volány z metod `OnFullGCApproachNotify` a `OnFullGCCompleteNotify`. Metody uživatele přesměrují požadavky, dokončí stávající žádosti a pak obnoví požadavky po úplném uvolnění paměti.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Celá ukázka kódu je následující:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
