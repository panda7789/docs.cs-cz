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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138106"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Vytváření vláken a předávání dat při spuštění

Při vytvoření procesu operačního systému, operační systém vloží vlákno ke spuštění kódu v tomto procesu, včetně jakékoli původní domény aplikace. Od tohoto okamžiku mohou být domény aplikací vytvořeny a zničeny bez nutnosti vytváření nebo zničení vláken operačního systému. Pokud je spouštěný kód spravován, <xref:System.Threading.Thread> lze získat objekt pro vlákno prováděné v aktuální doméně <xref:System.Threading.Thread.CurrentThread%2A> aplikace <xref:System.Threading.Thread>načtením statické vlastnosti typu . Toto téma popisuje vytváření vláken a popisuje alternativy pro předávání dat do postupu podprocesu.  
  
## <a name="creating-a-thread"></a>Vytvoření vlákna

 Vytvořenínového <xref:System.Threading.Thread> objektu vytvoří nové spravované vlákno. Třída <xref:System.Threading.Thread> má konstruktory, <xref:System.Threading.ThreadStart> které mají <xref:System.Threading.ParameterizedThreadStart> delegáta nebo delegáta; delegát zabalí metodu, která je vyvolána novým <xref:System.Threading.Thread.Start%2A> vláknem při volání metody. Volání <xref:System.Threading.Thread.Start%2A> více než <xref:System.Threading.ThreadStateException> jednou způsobí, že být vyvolána.  
  
 Metoda <xref:System.Threading.Thread.Start%2A> vrátí okamžitě, často před skutečně spuštěna nové vlákno. Vlastnosti <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> můžete použít k určení stavu vlákna v jednom okamžiku, ale tyto vlastnosti by nikdy neměly být použity pro synchronizaci aktivit podprocesů.  
  
> [!NOTE]
> Po spuštění vlákna není nutné zachovat odkaz na <xref:System.Threading.Thread> objekt. Vlákno pokračuje v provádění, dokud procedura podprocesu neskončí.  
  
 Následující příklad kódu vytvoří dvě nová vlákna pro volání instance a statické metody na jiném objektu.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Předávání dat vláknům

 V rozhraní .NET Framework verze <xref:System.Threading.ParameterizedThreadStart> 2.0 delegát poskytuje snadný způsob, jak předat objekt <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> obsahující data do vlákna při volání přetížení metody. Viz <xref:System.Threading.ParameterizedThreadStart> příklad kódu.  
  
 Použití <xref:System.Threading.ParameterizedThreadStart> delegáta není typově bezpečný způsob předání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> dat, protože přetížení metody přijímá libovolný objekt. Alternativou je zapouzdřit proceduru podprocesu a data <xref:System.Threading.ThreadStart> v pomocné třídě a použít delegáta k provedení postupu podprocesu. Následující příklad ukazuje tuto techniku:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ani <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> delegát nemá vrácenou hodnotu, protože neexistuje žádné místo pro vrácení dat z asynchronního volání. Chcete-li načíst výsledky metody podprocesu, můžete použít metodu zpětného volání, jak je znázorněno v další části.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Načítání dat z vláken pomocí metod zpětného volání

 Následující příklad ukazuje metodu zpětného volání, která načítá data z vlákna. Konstruktor pro třídu, která obsahuje data a metodu podprocesu, také přijímá delegáta představujícímetodu zpětného volání; před ukončením metody podprocesu vyvolá delegáta zpětného volání.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [Threading](index.md)
- [Použití vláken a zřetězení](using-threads-and-threading.md)
