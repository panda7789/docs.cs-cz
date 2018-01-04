---
title: "Vytváření vláken a předávání dat při spuštění"
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
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d17ef8a199061f56f00e39fa887e2e64f64427ec
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Vytváření vláken a předávání dat při spuštění
Když je vytvořen procesu operačního systému, operační systém vloží vlákna ke spouštění kódu v procesu, včetně všech původní domény aplikace. Od tohoto okamžiku se lze vytvořit a zničen bez žádné podprocesy operačního systému nutně vytvořením nebo zničení aplikační domény. Pokud je spravovaný kód spouštěna kód, pak <xref:System.Threading.Thread> objektu pro přístup z více vláken provádění v aktuální doméně aplikace je možné získat načítání statických <xref:System.Threading.Thread.CurrentThread%2A> vlastnost typu <xref:System.Threading.Thread>. Toto téma popisuje vytváření vláken a alternativami pro předávání dat na postup přístup z více vláken.  
  
## <a name="creating-a-thread"></a>Vytváření vlákna  
 Vytvoření nové <xref:System.Threading.Thread> objekt vytvoří nové spravované vlákno. <xref:System.Threading.Thread> Třída obsahuje konstruktory, které nepřijímají <xref:System.Threading.ThreadStart> delegovat nebo <xref:System.Threading.ParameterizedThreadStart> delegovat; delegát zabalí metody, která je volána nové vlákno při volání <xref:System.Threading.Thread.Start%2A> metoda. Volání metody <xref:System.Threading.Thread.Start%2A> více než jednou způsobí, že <xref:System.Threading.ThreadStateException> vyvolání.  
  
 <xref:System.Threading.Thread.Start%2A> Metoda vrátí okamžitě, často předtím, než má ve skutečnosti spustit nové vlákno. Můžete použít <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> vlastnosti k určení stavu vlákno daném okamžiku, ale tyto vlastnosti musí být nikdy použit pro synchronizaci aktivity vláken.  
  
> [!NOTE]
>  Jakmile začne vlákno, není nutné zachovat odkaz na <xref:System.Threading.Thread> objektu. Vlákno bude pokračovat v provádění až do ukončení procesu přístup z více vláken.  
  
 Následující příklad kódu vytvoří dva nové vláken pro volání instance a statické metody na jiný objekt.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>Předání dat do vláken a načtení dat z vláken  
 V rozhraní .NET Framework verze 2.0 <xref:System.Threading.ParameterizedThreadStart> delegáta poskytuje snadný způsob, jak předat objekt obsahující data na vlákno při volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody. V tématu <xref:System.Threading.ParameterizedThreadStart> příklad kódu.  
  
 Pomocí <xref:System.Threading.ParameterizedThreadStart> delegát není bezpečný způsob k předávání dat, protože <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody přijímá libovolného objektu. Alternativou je zapouzdření vlákno postup a data v pomocnou třídu a použijte <xref:System.Threading.ThreadStart> delegáta ke spuštění procedury přístup z více vláken. Tento postup je uveden v příklady dvě kódu, které následují.  
  
 Ani jeden z těchto delegáti má návratovou hodnotu, protože není k dispozici žádné místní vrátit data z asynchronního volání. Pokud chcete načíst výsledky metody přístup z více vláken, můžete použít metody zpětného volání, jak je předvedeno v druhém příkladu kódu.  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>Načítání dat pomocí metody zpětného volání  
 Následující příklad ukazuje metodu zpětného volání, která načte data z vlákna. Konstruktor pro třídu, která obsahuje data a metodu přístup z více vláken také přijímá delegáta představující metoda zpětného volání; předtím, než skončí metodu přístup z více vláken, vyvolá delegáta zpětného volání.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
