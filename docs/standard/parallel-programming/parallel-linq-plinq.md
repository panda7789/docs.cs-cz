---
title: "Paralelní LINQ (PLINQ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 94eeeda4666a4e6c1cb8729d6563ffcc4aa479c4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="parallel-linq-plinq"></a>Paralelní LINQ (PLINQ)
Paralelní LINQ (PLINQ) je paralelní provádění LINQ na objekty. PLINQ implementuje kompletní LINQ standardní operátory dotazu jako rozšiřující metody pro <xref:System.Linq> obor názvů a má další operátory paralelních operací. PLINQ kombinuje jednoduchosti a přehlednosti syntaxe LINQ s možností paralelní programování. Stejně jako kód s cílem Task Parallel Library dotazy PLINQ škálovat v stupeň souběžnosti na základě schopností hostitelského počítače.  
  
 V mnoha scénářích PLINQ výrazně zvýšit rychlost LINQ na objekty dotazy pomocí všechny dostupné jader na hostitelském počítači efektivněji. Toto zvýšení výkonu přináší vysoký výkon výpočetní výkon na pracovní plochu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úvod do PLINQ](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [Zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [Možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [Postupy: Řazení ovládacích prvků v dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [Postupy: Kombinování paralelních a sekvenčních dotazů LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [Postupy: Zpracování výjimek v dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [Postupy: Zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [Postupy: Psaní vlastní agregační funkce pro PLINQ](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [Postupy: Určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [Postupy: Určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [Postupy: Měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [Ukázková data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
