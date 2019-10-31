---
title: Vytváření vláken a předávání dat při spuštění
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138106"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Vytváření vláken a předávání dat při spuštění

Při vytvoření procesu operačního systému vloží operační systém vlákno a spustí kód v tomto procesu, včetně jakékoli původní domény aplikace. Od tohoto okamžiku je možné vytvořit a zničit domény aplikace, aniž by bylo nutné vytvořit nebo zničit žádná vlákna operačního systému. Pokud je spuštěný kód spravovaný, lze získat <xref:System.Threading.Thread> objekt pro vlákno spuštěné v aktuální doméně aplikace načtením vlastnosti static <xref:System.Threading.Thread.CurrentThread%2A> typu <xref:System.Threading.Thread>. Toto téma popisuje vytvoření vlákna a popisuje alternativy k předávání dat proceduře vlákna.  
  
## <a name="creating-a-thread"></a>Vytvoření vlákna

 Vytvořením nového objektu <xref:System.Threading.Thread> se vytvoří nové spravované vlákno. Třída <xref:System.Threading.Thread> má konstruktory, které přijímají delegáta <xref:System.Threading.ThreadStart> nebo delegáta <xref:System.Threading.ParameterizedThreadStart>; delegát zabalí metodu, která je vyvolána novým vláknem při volání metody <xref:System.Threading.Thread.Start%2A>. Volání <xref:System.Threading.Thread.Start%2A> více než jednou způsobí vyvolání <xref:System.Threading.ThreadStateException>.  
  
 Metoda <xref:System.Threading.Thread.Start%2A> vrátí hodnotu okamžitě, často před tím, než se nové vlákno skutečně spustí. Pomocí vlastností <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> můžete určit stav vlákna v jednom okamžiku, ale tyto vlastnosti by nikdy neměly být použity pro synchronizaci aktivit vláken.  
  
> [!NOTE]
> Po spuštění vlákna není nutné uchovávat odkaz na objekt <xref:System.Threading.Thread>. Vlákno pokračuje v provádění až do ukončení procedury vlákna.  
  
 Následující příklad kódu vytvoří dvě nová vlákna pro volání instance a statické metody pro jiný objekt.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Předávání dat do vláken

 V .NET Framework verze 2,0 <xref:System.Threading.ParameterizedThreadStart> delegát poskytuje snadný způsob, jak předat objekt obsahující data do vlákna při volání přetížení metody <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Příklad kódu naleznete v tématu <xref:System.Threading.ParameterizedThreadStart>.  
  
 Použití delegáta <xref:System.Threading.ParameterizedThreadStart> není typově bezpečný způsob, jak předat data, protože přetížení metody <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přijímá libovolný objekt. Alternativou je zapouzdřit proceduru vlákna a data v pomocné třídě a použít delegáta <xref:System.Threading.ThreadStart> k provedení procedury vlákna. Následující příklad znázorňuje tuto techniku:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Žádná z delegátů <xref:System.Threading.ThreadStart> ani <xref:System.Threading.ParameterizedThreadStart> nemá návratovou hodnotu, protože neexistuje místo pro návrat dat z asynchronního volání. Chcete-li načíst výsledky metody vlákna, můžete použít metodu zpětného volání, jak je znázorněno v následující části.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Načítání dat z vláken pomocí metod zpětného volání

 Následující příklad ukazuje metodu zpětného volání, která načítá data z vlákna. Konstruktor pro třídu, která obsahuje data a metodu vlákna, přijímá také delegáta představující metodu zpětného volání; před ukončením metody vlákna vyvolá delegát zpětného volání.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [Dělení na vlákna](index.md)
- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
