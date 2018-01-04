---
title: "Postupy: Zpracování výjimek v dotazu PLINQ"
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
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3e09bc2b285d014a7d3a6ed6fc4e50f85b537d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Postupy: Zpracování výjimek v dotazu PLINQ
V prvním příkladu v tomto tématu ukazuje způsob zpracování <xref:System.AggregateException?displayProperty=nameWithType> , může být vyvolána z PLINQ dotazu, jakmile je spuštěn. Druhý příklad ukazuje, jak se umístí bloků try-catch v rámci delegátů, co nejblíže k kde bude vyvolána výjimka. Tímto způsobem můžete zachytit je Jakmile k nim dojde a případně pokračovat v provádění dotazu. Pokud je výjimky umožněno vyvolat zpět do spojovacího vlákna, je možné, že dotaz může pokračovat ve zpracování některé položky po je vyvolána výjimka.  
  
 V některých případech když PLINQ přejde zpět k sekvenční provádění, a dojde k výjimce, výjimka může být rozšířen přímo a není uzavřen do <xref:System.AggregateException>. Navíc <xref:System.Threading.ThreadAbortException>s rozšířeny vždy přímo.  
  
> [!NOTE]
>  Pokud je povoleno "Pouze můj kód", Visual Studio se rozdělit na řádku, která vyvolala výjimku a zobrazí chybovou zprávu, která říká "výjimka není zpracována uživatelského kódu." Tato chyba je neškodná. Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech. Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
>   
>  Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak umístit bloky try-catch – okolo kód, který provede daný dotaz k zachycení všech <xref:System.AggregateException?displayProperty=nameWithType>vyvolaných.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 V tomto příkladu dotaz nemůže pokračovat po vyvolání výjimky. Podle času kód aplikace zachytí výjimky PLINQ již zastavil dotaz na všechna vlákna.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak se umístí blok try-catch – delegáta, aby bylo možné zachytit výjimku a pokračovat v provádění dotazu.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování a spuštění těchto příkladech, zkopírujte je do příklad ukázková Data pro PLINQ a volat metodu z hlavní.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud víte, jak ji zpracovat tak, aby nedošlo k poškození stavu vašeho programu není zachycení výjimek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
