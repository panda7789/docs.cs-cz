---
title: 'Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: abf31ea69af6a85140efb783959a9a586ef6a59e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277996"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ

Tento článek ukazuje dva způsoby, jak paralelizovat operace v adresářích souborů. První dotaz používá <xref:System.IO.Directory.GetFiles%2A> metodu k naplnění pole názvů souborů v adresáři a všech podadresářích. Tato metoda může zavádět latenci na začátku operace, protože nevrátí hodnotu, dokud se naplní celé pole. Nicméně po naplnění pole je PLINQ schopen ho zpracovat paralelně.  
  
Druhý dotaz používá statické <xref:System.IO.Directory.EnumerateDirectories%2A> <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody a, které začínají okamžitě vracet výsledky. Tento přístup může být rychlejší, když provádíte iteraci v rámci rozsáhlých stromů adresářů, ale doba zpracování v porovnání s prvním příkladem závisí na mnoha faktorech.  
  
> [!NOTE]
> Tyto příklady jsou určeny k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>Příklad GetFiles

 Tento příklad ukazuje, jak iterovat soubory adresáře v jednoduchých scénářích, když máte přístup ke všem adresářům stromu, velikost souborů není velká a časy přístupu nejsou významné. Tento přístup zahrnuje dobu latence na začátku při seřazování pole názvů souborů.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>Příklad EnumerateFiles

 Tento příklad ukazuje, jak iterovat soubory adresáře v jednoduchých scénářích, když máte přístup ke všem adresářům stromu, velikost souborů není velká a časy přístupu nejsou významné. Tento přístup začíná vytvářet výsledky rychleji než v předchozím příkladu.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Při použití nástroje <xref:System.IO.Directory.GetFiles%2A> se ujistěte, že máte dostatečná oprávnění ke všem adresářům ve stromové struktuře. V opačném případě bude vyvolána výjimka a nebudou vráceny žádné výsledky. Při použití <xref:System.IO.Directory.EnumerateDirectories%2A> v PLINQ dotazu je problematické zpracovávat výjimky vstupu a výstupu plynule tak, aby bylo možné pokračovat v iteraci. Pokud váš kód musí zpracovat výjimky vstupně-výstupních operací nebo neoprávněného přístupu, měli byste zvážit přístup popsaný v tématu [Postupy: iterování souborů adresáře s paralelní třídou](how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Pokud je latence vstupně-výstupních operací, například při vstupně-výstupních operacích se soubory přes síť, zvažte použití jedné z asynchronních vstupně-výstupních metod popsaných v tématu [TPL a tradičního .NET Framework asynchronního programování](tpl-and-traditional-async-programming.md) a v tomto [blogovém příspěvku](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
