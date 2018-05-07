---
title: Možnosti sloučení v PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7df080185db9631e47bb7a886f6e0db894974a6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="merge-options-in-plinq"></a>Možnosti sloučení v PLINQ
Při provádění dotazu jako paralelní, oddíly PLINQ zdrojové sekvence více vláken mohli pracovat na různé části souběžně, obvykle v samostatných vláknech. Pokud výsledky mají být využívány na jedno vlákno, například v `foreach` (`For Each` v jazyce Visual Basic) smyčce, pak je potřeba sloučit výsledky z každého vlákno zpět do jedné sekvence. Druh sloučení, který provádí PLINQ závisí na operátory, které se nacházejí v dotazu. Operátory, které zavádí nové pořadí ve výsledcích například musí vyrovnávací paměti všechny elementy z všechna vlákna. Z hlediska využívání vlákno (což je také u uživatelů aplikace) může plně ve vyrovnávací paměti dotaz spustit znatelné dobu před tím, než vyvolá první výsledek. Jiné operátory ve výchozím nastavení, jsou částečně do vyrovnávací paměti; dávají výsledky v dávkách. Jeden operátor <xref:System.Linq.ParallelEnumerable.ForAll%2A> není ve výchozím nastavení do vyrovnávací paměti. Dává všechny elementy ze všech vláken okamžitě.  
  
 Pomocí <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metoda, jak je znázorněno v následujícím příkladu, můžete zadat nápovědu pro PLINQ, která určuje, jaký druh sloučení provést.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Úplný příklad najdete v tématu [postupy: určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Pokud některé dotazy nepodporují požadovanou možnost, pak možnost bude ignorována. Ve většině případů nemáte zadejte možnost sloučení pro PLINQ dotazu. Ale v některých případech můžete zjistit pomocí testování a měření, které dotazu nejlépe provádí v jiné než výchozí režim. Běžné použití této možnosti je vynutit operátor sloučení bloků dat do datového proudu s cílem poskytnout rychleji reagující uživatelské rozhraní.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> Výčet obsahuje následující možnosti, které určují pro podporované tvary dotazu, jak je získán finální výstup dotazu, když je výsledek zpracován na jedno vlákno:  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> Možnost způsobí, že každý zpracovávaný element má být vrácen z každé vlákno, jakmile se vytvářejí. Toto chování je obdobou "vysílání" výstupu. Pokud <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor se nachází v dotazu, `NotBuffered` pořadí zdrojové elementy se zachovají. I když `NotBuffered` spustí vracet výsledky, jakmile jsou k dispozici,, celkový čas k vytvoření všechny výsledky, může stále dojít být delší než pomocí jedné z dalších možností sloučení.  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Možnost způsobí, že dotaz pro shromažďování elementy do vyrovnávací paměti a pravidelně všechny najednou vláknu obsah vyrovnávací paměti. Toto je analogická k vracení zdrojová data v "bloky" místo "streamování" chování `NotBuffered`. `AutoBuffered` může trvat déle než `NotBuffered` chcete zpřístupnit první prvek spotřebitelské vlákno. Velikost vyrovnávací paměti a přesné chování vracení výsledku se nedají konfigurovat a může lišit v závislosti na různé faktory, které se týkají dotazu.  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Možnost způsobí, že výstup celého uložená do vyrovnávací paměti, před vrácením libovolné prvku výsledků dotazu. Pokud použijete tuto možnost, může trvat delší než první prvek je dostupná na vláknu, ale může být vytvořen výsledků rychleji než pomocí jiné možnosti.  
  
## <a name="query-operators-that-support-merge-options"></a>Operátory dotazu, které podporují možnosti sloučení  
 Následující tabulka uvádí operátory, které podporují všechny režimy nastavení, může zadané omezení.  
  
|Operátor|Omezení|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Řazení podle jiného typu dotazy, které mají pole nebo seznam jako zdroj.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Řazení podle jiného typu dotazy, které mají pole nebo seznam jako zdroj.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Žádné|  
  
 Všechny ostatní operátory dotazu PLINQ může ignorovat možností sloučení zadaný uživatelem. Některé operátory dotazů, například <xref:System.Linq.ParallelEnumerable.Reverse%2A> a <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, nemůžou vracet prvky, dokud všechny vytváří a přeuspořádány. Proto když <xref:System.Linq.ParallelMergeOptions> se používá v dotazu, který také obsahuje nepodporovaný operátor <xref:System.Linq.ParallelEnumerable.Reverse%2A>, sloučení chování se neprojeví v dotazu, dokud po tento operátor má vytváří své výsledky.  
  
 Schopnost některý operátorů zpracovat možnosti sloučení závisí na typu zdrojové sekvence a jestli <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor byl použit dříve v dotazu. <xref:System.Linq.ParallelEnumerable.ForAll%2A> je vždy <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; vrací elementy okamžitě. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> je vždy <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; předtím, než bude vrácen, je nutné seřadit celý seznam.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Postupy: Určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
