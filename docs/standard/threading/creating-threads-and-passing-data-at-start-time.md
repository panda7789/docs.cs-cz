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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c231c946897772a6f02cce6eb2d3c4936b72a35e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716036"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Vytváření vláken a předávání dat při spuštění

Když se procesu operačního systému, operační systém vloží vlákna ke spouštění kódu v tomto procesu, včetně domén původní aplikace. Od této chvíle lze vytvořit a zničit bez žádného vlákna operačního systému, nemusí být vytváření nebo zničení aplikačních doménách. Pokud jde o spravovaného kódu při provádění kódu, o <xref:System.Threading.Thread> objektu pro vlákno provádění v aktuální doméně aplikace, můžete získat výčtem načítání statické <xref:System.Threading.Thread.CurrentThread%2A> vlastnost typu <xref:System.Threading.Thread>. Toto téma popisuje vytvoření vlákna a alternativy k předávání dat procedura vlákna.  
  
## <a name="creating-a-thread"></a>Vytvořením vlákna

 Vytvoření nového <xref:System.Threading.Thread> objekt vytvoří nové spravované vlákno. <xref:System.Threading.Thread> Třída nemá konstruktor <xref:System.Threading.ThreadStart> delegáta nebo <xref:System.Threading.ParameterizedThreadStart> delegovat; zabalí delegát metody, která je volána při volání nové vlákno <xref:System.Threading.Thread.Start%2A> – metoda. Volání <xref:System.Threading.Thread.Start%2A> více než jednou způsobí, že <xref:System.Threading.ThreadStateException> vyvolání.  
  
 <xref:System.Threading.Thread.Start%2A> Metoda vrátí okamžitě, často před zahájením nové vlákno je ve skutečnosti. Můžete použít <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> vlastnosti k určení stavu vlákna v daném okamžiku provádějí jednu, ale tyto vlastnosti by měla být nikdy použit pro synchronizaci činností vlákna.  
  
> [!NOTE]
> Po zahájení vlákno není nutné zachovat odkaz na <xref:System.Threading.Thread> objektu. Vlákno pokračuje v běhu až do ukončení procedura vlákna.  
  
 Následující příklad kódu vytvoří dva nové vláken pro volání instance a statické metody na jiný objekt.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Předání dat do vláken

 V rozhraní .NET Framework verze 2.0 <xref:System.Threading.ParameterizedThreadStart> delegáta poskytuje snadný způsob, jak předat objekt, který obsahuje data na vlákno při volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody. Zobrazit <xref:System.Threading.ParameterizedThreadStart> příklad kódu.  
  
 Použití <xref:System.Threading.ParameterizedThreadStart> delegáta není typově bezpečný způsob, jak předávat data, protože <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody přijímá libovolný objekt. Alternativou je k zapouzdření procedura vlákna a data v pomocnou třídu a použít <xref:System.Threading.ThreadStart> delegát k provádění procedura vlákna. Následující příklad ukazuje tento postup:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ani <xref:System.Threading.ThreadStart> ani <xref:System.Threading.ParameterizedThreadStart> delegát má návratovou hodnotu, protože neexistuje žádný místo pro vrácení dat z asynchronní volání. K načtení výsledků metody vlákno, můžete použít metodu zpětného volání, jak je znázorněno v následující části.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Načtení dat z vláken pomocí metody zpětného volání

 Následující příklad ukazuje metodu zpětného volání, která načte data z vlákna. Konstruktor pro třídu, která obsahuje data a metoda vlákna také přijímá delegát představující metodu zpětného volání; předtím, než metoda vlákno ukončí, vyvolá delegáta zpětného volání.  
  
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
