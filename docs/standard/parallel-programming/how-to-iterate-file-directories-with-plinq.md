---
title: 'Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 523db9d356954a4a397b63d836018070effa9e5b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ
Tento příklad ukazuje dva způsoby jednoduché učinit paralelní operací na souborové adresáře. První dotaz používá <xref:System.IO.Directory.GetFiles%2A> metoda k vyplnění pole názvy souborů v adresáři a všechny podadresáře. Tato metoda nevrátí, dokud se vyplní celé pole, a proto ho můžou představovat latence na začátku operaci. Ale po naplnění pole PLINQ může zpracovat paralelní velmi rychle.  
  
 Druhý dotaz používá statickou <xref:System.IO.Directory.EnumerateDirectories%2A> a <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody, které začít vracet výsledky okamžitě. Tento přístup může být rychlejší při jsou iterování přes stromy velké adresáře, i když bude čas zpracování ve srovnání s prvním příkladu může záviset na mnoha faktorech.  
  
> [!WARNING]
>  Tyto příklady jsou určeny k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak Iterujte přes souborové adresáře v jednoduchého scénáře, když máte přístup do všech adresářů ve stromu, velikosti souborů nejsou velmi velké a čas přístupu nejsou důležité. Tento postup zahrnuje období latence na začátku při je vytvářen pole názvy souborů.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak Iterujte přes souborové adresáře v jednoduchého scénáře, když máte přístup do všech adresářů ve stromu, velikosti souborů nejsou velmi velké a čas přístupu nejsou důležité. Tento přístup začne generovala výsledky rychleji než předchozí příklad.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Při použití <xref:System.IO.Directory.GetFiles%2A>, ujistěte se, zda máte dostatečná oprávnění na všechny adresáře ve stromové struktuře. V opačném případě bude vyvolána výjimka, které budou vráceny žádné výsledky. Při použití <xref:System.IO.Directory.EnumerateDirectories%2A> v PLINQ dotazu, je problematické zpracování výjimek vstupně-výstupních operací řádně způsobem, který umožňuje pokračovat iterace. Pokud váš kód musí zpracovat vstupně-výstupních operací nebo výjimky neoprávněného přístupu, pak byste měli zvážit postupuje podle [postupy: procházení adresářů se soubory pomocí paralelní třídy](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Pokud je latence vstupně-výstupních operací problém, například souborem vstupně-výstupní operace přes síť, zvažte použití mezi asynchronní vstupně-výstupních operací technik popsaných v [TPL a tradiční rozhraní .NET Framework asynchronní programování](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) a v tomto [příspěvku na blogu ](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
