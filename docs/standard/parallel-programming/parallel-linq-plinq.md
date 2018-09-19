---
title: Paralelní LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fe7edffd53023cba6dac1454e620d6e0d7e9513
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007424"
---
# <a name="parallel-linq-plinq"></a>Paralelní LINQ (PLINQ)
Paralelní LINQ (PLINQ) je implementace LINQ to Objects. PLINQ implementuje úplnou sadu operátorů standardního dotazu LINQ jako rozšiřující metody pro <xref:System.Linq> obor názvů a má další operátoři pro paralelních operací. PLINQ kombinuje jednoduchosti a přehlednosti syntaxi LINQ s výkonným paralelním programování. Stejně jako kód, který cílí Task Parallel Library, dotazy PLINQ horizontálně stupeň souběžnosti na základě možností hostitelského počítače.  
  
 V mnoha případech můžete PLINQ významně zvyšuje rychlost LINQ to Objects dotazů s použitím všech dostupných jader v hostitelském počítači efektivněji. Toto zvýšení výkonu přináší vysoce výkonné výpočetní výkon na pracovní plochu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>  
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
- [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
