---
title: Vytváření vláken a předávání dat při spuštění
description: Naučte se vytvářet vlákna a předávat data v počátečním čase procesu operačního systému v .NET.
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
ms.openlocfilehash: 811028d3c853441ff3a61d3628a44e5c65ba7059
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661911"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Vytváření vláken a předávání dat při spuštění

Při vytvoření procesu operačního systému vloží operační systém vlákno a spustí kód v tomto procesu, včetně jakékoli původní domény aplikace. Od tohoto okamžiku je možné vytvořit a zničit domény aplikace, aniž by bylo nutné vytvořit nebo zničit žádná vlákna operačního systému. Pokud je spuštěný kód spravovaný, <xref:System.Threading.Thread> lze získat objekt pro vlákno spuštěné v aktuální doméně aplikace načtením statické <xref:System.Threading.Thread.CurrentThread%2A> vlastnosti typu <xref:System.Threading.Thread> . Toto téma popisuje vytvoření vlákna a popisuje alternativy k předávání dat proceduře vlákna.  
  
## <a name="creating-a-thread"></a>Vytvoření vlákna

 Vytvořením nového <xref:System.Threading.Thread> objektu se vytvoří nové spravované vlákno. <xref:System.Threading.Thread>Třída má konstruktory, které přijímají <xref:System.Threading.ThreadStart> delegáta nebo <xref:System.Threading.ParameterizedThreadStart> delegáta. Tento delegát zabalí metodu, která je vyvolána novým vláknem při volání <xref:System.Threading.Thread.Start%2A> metody. Volání <xref:System.Threading.Thread.Start%2A> více než jednou způsobí, že <xref:System.Threading.ThreadStateException> bude vyvolána výjimka.  
  
 <xref:System.Threading.Thread.Start%2A>Metoda se vrátí hned, často před samotným spuštěním nového vlákna. Pomocí <xref:System.Threading.Thread.ThreadState%2A> vlastností a můžete <xref:System.Threading.Thread.IsAlive%2A> určit stav vlákna v jednom okamžiku, ale tyto vlastnosti by nikdy neměly být použity pro synchronizaci aktivit vláken.  
  
> [!NOTE]
> Po spuštění vlákna není nutné uchovávat odkaz na <xref:System.Threading.Thread> objekt. Vlákno pokračuje v provádění až do ukončení procedury vlákna.  
  
 Následující příklad kódu vytvoří dvě nová vlákna pro volání instance a statické metody pro jiný objekt.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Předávání dat do vláken

 V .NET Framework verze 2,0 <xref:System.Threading.ParameterizedThreadStart> poskytuje delegát snadný způsob, jak předat objekt obsahující data do vlákna při volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody. Příklad kódu naleznete v tématu <xref:System.Threading.ParameterizedThreadStart> .  
  
 Použití <xref:System.Threading.ParameterizedThreadStart> delegáta není typově bezpečný způsob, jak předat data, protože <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody přijímá libovolný objekt. Alternativou je zapouzdřit proceduru vlákna a data v pomocné třídě a použít <xref:System.Threading.ThreadStart> delegáta k provedení procedury vlákna. Následující příklad znázorňuje tuto techniku:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ani <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> delegát nemá návratovou hodnotu, protože k dispozici není žádné místo pro návrat dat z asynchronního volání. Chcete-li načíst výsledky metody vlákna, můžete použít metodu zpětného volání, jak je znázorněno v následující části.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Načítání dat z vláken pomocí metod zpětného volání

 Následující příklad ukazuje metodu zpětného volání, která načítá data z vlákna. Konstruktor pro třídu, která obsahuje data a metodu vlákna, přijímá také delegáta představující metodu zpětného volání; před ukončením metody vlákna vyvolá delegát zpětného volání.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [Dělení na vlákna](index.md)
- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
