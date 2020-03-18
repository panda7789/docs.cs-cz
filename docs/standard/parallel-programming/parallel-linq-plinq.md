---
title: Paralelní LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140033"
---
# <a name="parallel-linq-plinq"></a>Paralelní LINQ (PLINQ)
Paralelní LINQ (PLINQ) je paralelní implementace LINQ na objekty. PLINQ implementuje úplnou sadu linq standardní operátory dotazů jako metody rozšíření pro obor <xref:System.Linq> názvů a má další operátory pro paralelní operace. PLINQ kombinuje jednoduchost a čitelnost syntaxe LINQ s výkonem paralelního programování. Stejně jako kód, který cílí na paralelní knihovnu úloh, se dotazy PLINQ škálují v stupni souběžnosti na základě možností hostitelského počítače.  
  
 V mnoha scénářích může PLINQ výrazně zvýšit rychlost dotazů LINQ na objekty efektivnějším použitím všech dostupných jader v hostitelském počítači. Tento zvýšený výkon přináší na plochu vysoký výpočetní výkon.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úvod do PLINQ](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [Zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [Možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [Postupy: Řazení ovládacích prvků v PLINQ dotazu](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [Postupy: Kombinování paralelních a sekvenčních LINQ dotazů](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [Postupy: Zpracování výjimek v dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [Postupy: Zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [Postupy: Psaní vlastní agregační funkce pro PLINQ](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [Postupy: Určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [Postupy: Určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [Postupy: Měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [Ukázková data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Dotaz integrovaný jazykem (LINQ) – C #](../../csharp/programming-guide/concepts/linq/index.md)  
- [Dotaz integrovaný jazykem (LINQ) – visual basic](../../visual-basic/programming-guide/concepts/linq/index.md)  
