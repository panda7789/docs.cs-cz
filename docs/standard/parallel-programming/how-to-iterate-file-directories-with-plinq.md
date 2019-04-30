---
title: 'Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d48f6df1e0e7680d2706c73c33dc817e1feaf1d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781196"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ
Tento příklad ukazuje dvě jednoduché způsoby paralelní operace na adresářů se soubory. První dotaz používá <xref:System.IO.Directory.GetFiles%2A> metoda k vyplnění pole názvů souboru v adresáři a všech podadresářích. Tato metoda nevrací až celého pole se vyplní, a proto ji můžete zavést latenci na začátku této operace. Ale po naplnění pole PLINQ může zpracovat ho paralelně velmi rychle.  
  
 Druhý dotaz používá statickou <xref:System.IO.Directory.EnumerateDirectories%2A> a <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody, které začít vracet výsledky okamžitě. Tento přístup může být rychlejší při jsou iterace stromy velké adresáře, i když čas zpracování ve srovnání s prvním příkladu může záviset na mnoha faktorech.  
  
> [!WARNING]
>  Tyto příklady jsou určeny k předvedení využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k iteraci přes adresářů se soubory v jednoduché scénáře, když máte přístup ke všem adresářům ve stromové struktuře, velikosti souborů nejsou velmi velké a čas přístupu nejsou důležité. Tento přístup zahrnuje určitou latenci na začátku, zatímco pole názvy souborů se vytváří.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k iteraci přes adresářů se soubory v jednoduché scénáře, když máte přístup ke všem adresářům ve stromové struktuře, velikosti souborů nejsou velmi velké a čas přístupu nejsou důležité. Tento přístup zahájí vytváření výsledky rychleji než v předchozím příkladu.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Při použití <xref:System.IO.Directory.GetFiles%2A>, ujistěte se, že máte dostatečná oprávnění ke všem adresářům ve stromové struktuře. Jinak bude vyvolána výjimka a nevrátí se žádné výsledky. Při použití <xref:System.IO.Directory.EnumerateDirectories%2A> v PLINQ dotazu je problematické pro zpracování výjimek vstupně-výstupních operací řádné tak, aby vám pokračujte iterace. Pokud váš kód musí zpracovat vstup/výstup nebo výjimky neoprávněného přístupu, měli byste uvažovat o postupu popsaného v [jak: Procházení adresářů se soubory pomocí paralelní třídy](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Pokud je latence vstupně-výstupní operace problém, se souborem vstupně-výstupní operace přes síť, Představme si třeba pomocí jedné z asynchronní vstupně-výstupní techniky popsané v [TPL a tradiční rozhraní .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) a v tomto [blogový příspěvek ](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
