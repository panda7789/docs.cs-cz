---
title: 'Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 208076cb9b7b56ab13458fa0dd4d92f2023106b9
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635834"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ

Tento článek ukazuje dva způsoby, jak paralelizovat operace v adresářích souborů. První dotaz používá <xref:System.IO.Directory.GetFiles%2A> metodu k naplnění pole názvů souborů v adresáři a všech podadresářích. Tato metoda může zavést latence na začátku operace, protože nevrátí, dokud je naplněncelé pole. Však po naplnění pole, PLINQ můžete zpracovat paralelně rychle.  
  
Druhý dotaz používá <xref:System.IO.Directory.EnumerateDirectories%2A> statické <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> a metody, které začnou vracet výsledky okamžitě. Tento přístup může být rychlejší, když iterace přes velké adresářové stromy, ale doba zpracování ve srovnání s prvním příkladem závisí na mnoha faktorech.  
  
> [!NOTE]
> Tyto příklady jsou určeny k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>Příklad GetFiles

 Tento příklad ukazuje, jak itetovat přes adresáře souborů v jednoduchých scénářích, když máte přístup ke všem adresářům ve stromu, velikosti souborů nejsou velké a časy přístupu nejsou významné. Tento přístup zahrnuje období latence na začátku při vytváření pole názvů souborů.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>Příklad výčtu souborů

 Tento příklad ukazuje, jak itetovat přes adresáře souborů v jednoduchých scénářích, když máte přístup ke všem adresářům ve stromu, velikosti souborů nejsou velké a časy přístupu nejsou významné. Tento přístup začíná produkovat výsledky rychleji než v předchozím příkladu.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Při <xref:System.IO.Directory.GetFiles%2A>použití se ujistěte, že máte dostatečná oprávnění pro všechny adresáře ve stromu. V opačném případě bude vyvolána výjimka a nebudou vráceny žádné výsledky. Při použití <xref:System.IO.Directory.EnumerateDirectories%2A> v plinq dotazu je problematické zpracovat výjimky vstupně-v a to v elegantním způsobem, který umožňuje pokračovat v iterace. Pokud váš kód musí zpracovat výjimky vstupně-neoprávněný přístup, pak byste měli zvážit přístup popsaný v [How to: Iterate File Directories with the Parallel Class](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Pokud je vstupně-výstupní latence problém, například se vstupně-výstupními vstupně-výstupními programy v síti, zvažte použití jedné z asynchronních technik vstupně-výstupních služeb popsaných v [tpl a tradiční asynchronní programování rozhraní .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) a v tomto [příspěvku blogu](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
