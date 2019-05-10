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
ms.openlocfilehash: 7255ef11bfdf74afa6ae2032b0c86c8c44dbfe7d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647729"
---
# <a name="merge-options-in-plinq"></a>Možnosti sloučení v PLINQ
Při provádění dotazu jako paralelně, PLINQ rozdělí zdrojovou sekvenci tak, aby více vláken může pracovat na různých částech souběžně, obvykle v samostatných vláknech. Výsledky jsou-li využívat v jednom vlákně, například v `foreach` (`For Each` v jazyce Visual Basic) smyčce, pak výsledky z každé vlákno musí být sloučeny zpět do jedné sekvence. Druh sloučení, který provádí PLINQ závisí na subjekty, které se nacházejí v dotazu. Například operátory, které zavádí novou objednávku na výsledcích musí uložit do vyrovnávací paměti všechny prvky ze všech vláken. Z pohledu konzumním vlákně (která je také, že uživatel aplikace) může plně ve vyrovnávací paměti dotaz spusťte znatelný dobu vypršení vytváří výsledek první. Ostatní operátory ve výchozím nastavení, se částečně uložená do vyrovnávací paměti; dávají výsledky v dávkách. Jeden operátor <xref:System.Linq.ParallelEnumerable.ForAll%2A> nemá vyrovnávací paměť ve výchozím nastavení. Bude vrácen všechny prvky ze všech vláken okamžitě.  
  
 S použitím <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> způsob, jak je znázorněno v následujícím příkladu, můžete poskytnout nápovědu PLINQ, který označuje, jaký druh sloučení provést.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Kompletní příklad naleznete v tématu [jak: Určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Pokud konkrétní dotaz nepodporuje požadované možnosti, klikněte možnost bude ignorována. Ve většině případů není nutné zadat možnost sloučení pro PLINQ dotazu. Nicméně v některých případech může být pro vás z testování a měření, které dotaz provádí nejlépe v jiné než výchozí režim. Běžné použití této možnosti je vynutit operátor sloučení bloků dat do datového proudu negace rychleji reagující uživatelské rozhraní.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> Výčet zahrnuje následující možnosti, které určují pro podporované tvary dotazu, jak je získán finální výstup z dotazu, když v jednom vlákně se spotřebuje výsledky:  
  
- `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> Možnost způsobí, že každý zpracovaných prvek má být vrácena z každé vlákno, jakmile je vytvořen. Toto chování je obdobou "streaming" výstup. Pokud <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor je k dispozici v dotazu `NotBuffered` zachovává pořadí prvků zdroje. I když `NotBuffered` začne vracet výsledky, jako jsou k dispozici, celková doba nutná k vytvoření všechny výsledky, může stále dojít být delší než jedním z dalších možností sloučení.  
  
- `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Možnost způsobí, že dotaz, který shromáždí prvky do vyrovnávací paměti a pravidelně všechny najednou konzumním vlákně obsah vyrovnávací paměti. To je obdobou získávání zdrojová data v "bloky" místo "streaming" chování `NotBuffered`. `AutoBuffered` může trvat déle než `NotBuffered` zpřístupnit první prvek v konzumním vlákně. Velikost vyrovnávací paměti a přesné získávání chování se nedají konfigurovat a může lišit v závislosti na různých faktorech, které se vztahují k dotazu.  
  
- `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Možnost způsobí, že výstupní celého ukládány do vyrovnávací paměti, než všechny prvky jsou výsledkem dotazu. Když použijete tuto možnost, může trvat delší dobu před prvním prvkem je k dispozici v konzumním vlákně, ale může být stále vytváří úplné výsledky rychleji pomocí dalších možností.  
  
## <a name="query-operators-that-support-merge-options"></a>Operátory dotazů, které podporují možnosti sloučení  
 V následující tabulce jsou uvedeny operátory, které podporují všechny režimy možnost sloučení, zadané omezení.  
  
|Operátor|Omezení|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Seřazené bez dotazy, které mají seznamu nebo pole pouze zdroj.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Seřazené bez dotazy, které mají seznamu nebo pole pouze zdroj.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Žádný|  
  
 Všechny ostatní operátory dotazu PLINQ může ignorovat zadané uživatelské možnosti sloučení. Některé operátory dotazů, třeba <xref:System.Linq.ParallelEnumerable.Reverse%2A> a <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, žádné elementy nelze pozastavit, dokud všechny vytvořené a přeuspořádány. Proto když <xref:System.Linq.ParallelMergeOptions> se používá v dotazu, který také obsahuje operátor <xref:System.Linq.ParallelEnumerable.Reverse%2A>, sloučení chování se neprojeví v dotazu, dokud po operátor vytvořil jeho výsledky.  
  
 Schopnost některé operátory zpracování možností sloučení závisí na typu zdrojové sekvence a určuje, zda <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> dříve v dotazu byla použita operátor. <xref:System.Linq.ParallelEnumerable.ForAll%2A> je vždy <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; okamžitě vrací elementy. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> je vždy <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; je nutné seřadit celý seznam předtím, než bude vrácen.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Postupy: Určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
