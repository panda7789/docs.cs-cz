---
title: 'Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5da70cdca16c83b33e525aea588c02c696702ac7
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929158"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ
Tento příklad ukazuje dva jednoduché způsoby paralelizovat operací v adresářích souborů. První dotaz používá <xref:System.IO.Directory.GetFiles%2A> metodu k naplnění pole názvů souborů v adresáři a všech podadresářích. Tato metoda nevrátí hodnotu, dokud se nezaplní celé pole, a proto může zavádět latenci na začátku operace. Nicméně po naplnění pole je PLINQ schopen ho zpracovat paralelně velmi rychle.  
  
 Druhý dotaz používá statické <xref:System.IO.Directory.EnumerateDirectories%2A> metody a <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , které okamžitě zahájí návrat výsledků. Tento přístup může být rychlejší, když provádíte iteraci v rámci rozsáhlých stromů adresářů, i když doba zpracování ve srovnání s prvním příkladem může záviset na mnoha faktorech.  
  
> [!WARNING]
> Tyto příklady jsou určeny k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak iterovat soubory adresáře v jednoduchých scénářích, když máte přístup ke všem adresářům stromu, velikosti souborů nejsou velmi velké a časy přístupu nejsou významné. Tento přístup zahrnuje dobu latence na začátku při seřazování pole názvů souborů.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak iterovat soubory adresáře v jednoduchých scénářích, když máte přístup ke všem adresářům stromu, velikosti souborů nejsou velmi velké a časy přístupu nejsou významné. Tento přístup začíná vytvářet výsledky rychleji než v předchozím příkladu.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Při použití <xref:System.IO.Directory.GetFiles%2A>nástroje se ujistěte, že máte dostatečná oprávnění ke všem adresářům ve stromové struktuře. V opačném případě bude vyvolána výjimka a nebudou vráceny žádné výsledky. Při použití <xref:System.IO.Directory.EnumerateDirectories%2A> v PLINQ dotazu je problematické zpracovávat výjimky vstupu a výstupu plynule tak, aby bylo možné pokračovat v iteraci. Pokud váš kód musí zpracovat výjimky vstupu/výstupu nebo neoprávněný přístup, měli byste zvážit přístup popsaný [v tématu How to: Iterujte adresáře souborů s paralelní třídou](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Pokud je latence vstupně-výstupních operací, například při vstupně-výstupních operacích se soubory přes síť, zvažte použití jedné z asynchronních vstupně-výstupních metod popsaných v tématu [TPL a tradičního .NET Framework asynchronního programování](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) a v tomto [blogovém příspěvku](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
