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
ms.openlocfilehash: 623466e0e960ea991ae92e5de432171b70bad1d2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588623"
---
# <a name="merge-options-in-plinq"></a>Možnosti sloučení v PLINQ
Při provádění dotazu jako paralelní, PLINQ rozdělí zdrojovou sekvenci tak, aby více vláken může pracovat na různých částech současně, obvykle v samostatných vláknech. Pokud mají být výsledky spotřebovány v jednom `foreach` vlákně, například ve smyčce (v`For Each` jazyce Visual Basic), musí být výsledky z každého vlákna sloučeny zpět do jedné sekvence. Druh sloučení, který provádí PLINQ závisí na operátory, které jsou k dispozici v dotazu. Například operátory, které ukládají nové pořadí na výsledky musí vyrovnávací paměti všechny prvky ze všech vláken. Z hlediska náročné vlákno (což je také uživatel aplikace) plně do vyrovnávací paměti dotaz může spustit znatelnou dobu před tím, než vytvoří svůj první výsledek. Ostatní operátory jsou ve výchozím nastavení částečně uloženy do vyrovnávací paměti; přinášejí své výsledky v dávkách. Jeden operátor, <xref:System.Linq.ParallelEnumerable.ForAll%2A> není ve výchozím nastavení do vyrovnávací paměti. Poskytuje všechny prvky ze všech vláken okamžitě.  
  
 Pomocí <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody, jak je znázorněno v následujícím příkladu, můžete poskytnout nápovědu plinq, která označuje, jaký druh sloučení provést.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Úplný příklad najdete v [tématu Jak: Zadat možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Pokud konkrétní dotaz nemůže podporovat požadovanou možnost, bude tato možnost ignorována. Ve většině případů není nutné zadat možnost sloučení pro dotaz PLINQ. V některých případech však můžete zjistit testováním a měřením, že dotaz se provádí nejlépe v režimu mimo výchozí. Běžné použití této možnosti je vynutit operátor slučování bloků dat k streamování jeho výsledky s cílem poskytnout více reagovat uživatelské rozhraní.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 Výčet <xref:System.Linq.ParallelMergeOptions> obsahuje následující možnosti, které určují pro podporované obrazce dotazu způsob, jakým je konečný výstup dotazu při spotřebě výsledků v jednom vlákně:  
  
- `Not Buffered`  
  
     Možnost <xref:System.Linq.ParallelMergeOptions.NotBuffered> způsobí, že každý zpracovaný prvek, který má být vrácen z každého vlákna, jakmile je vyroben. Toto chování je analogické jako "streamování" výstupu. Pokud <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor je k dispozici `NotBuffered` v dotazu, zachová pořadí zdrojových prvků. Přestože `NotBuffered` začne dávat výsledky, jakmile jsou k dispozici, celková doba pro vytvoření všech výsledků může být stále delší než použití jedné z dalších možností sloučení.  
  
- `Auto Buffered`  
  
     Možnost <xref:System.Linq.ParallelMergeOptions.AutoBuffered> způsobí, že dotaz shromažďovat prvky do vyrovnávací paměti a pak pravidelně výtěžek obsahu vyrovnávací paměti najednou náročné vlákno. To je analogické s získávání zdrojových dat v "bloky" namísto `NotBuffered`použití "streamování" chování . `AutoBuffered`může trvat `NotBuffered` déle, než aby byl první prvek k dispozici na náročnévlákno. Velikost vyrovnávací paměti a přesné chování výtěžnosti nejsou konfigurovatelné a mohou se lišit v závislosti na různých faktorech, které se vztahují k dotazu.  
  
- `FullyBuffered`  
  
     Možnost <xref:System.Linq.ParallelMergeOptions.FullyBuffered> způsobí, že výstup celého dotazu do vyrovnávací paměti před některé z prvků jsou výnosy. Při použití této možnosti může trvat déle, než první prvek je k dispozici na náročné vlákno, ale úplné výsledky může být stále vytvářeny rychleji než pomocí jiných možností.  
  
## <a name="query-operators-that-support-merge-options"></a>Operátory dotazů, které podporují možnosti sloučení  
 V následující tabulce jsou uvedeny operátory, které podporují všechny režimy možností sloučení, s výhradou zadaných omezení.  
  
|Operátor|Omezení|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Neobjednané dotazy, které mají pouze zdroj array nebo list.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Neobjednané dotazy, které mají pouze zdroj array nebo list.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Žádný|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Žádný|  
  
 Všechny ostatní operátory dotazů PLINQ mohou ignorovat možnosti sloučení poskytované uživatelem. Některé operátory dotazu, například <xref:System.Linq.ParallelEnumerable.Reverse%2A> a <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, nemůže přinést žádné prvky, dokud všechny byly vytvořeny a reordered. Proto při <xref:System.Linq.ParallelMergeOptions> použití v dotazu, který také <xref:System.Linq.ParallelEnumerable.Reverse%2A>obsahuje operátor, jako je například , chování sloučení nebude použita v dotazu, dokud tento operátor vytvořil jeho výsledky.  
  
 Schopnost některých operátorů zpracovat možnosti sloučení závisí na typu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> zdrojové sekvence a na tom, zda byl operátor použit dříve v dotazu. <xref:System.Linq.ParallelEnumerable.ForAll%2A>je <xref:System.Linq.ParallelMergeOptions.NotBuffered> vždy ; okamžitě dává své prvky. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>je <xref:System.Linq.ParallelMergeOptions.FullyBuffered>vždy ; musí seřadit celý seznam dříve, než se zobrazí jeho výnosy.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Postupy: Určení možností sloučení v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
