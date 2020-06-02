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
ms.openlocfilehash: a2c238cb66c5018cd1dd4085c6541ef3c9371beb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290639"
---
# <a name="merge-options-in-plinq"></a>Možnosti sloučení v PLINQ
Když je dotaz spuštěn paralelně, PLINQ rozdělí zdrojové sekvence tak, aby více vláken mohlo pracovat souběžně na různých částech, obvykle v samostatných vláknech. Pokud mají být výsledky spotřebovány v jednom vlákně, například ve `foreach` `For Each` smyčce (ve Visual Basic), pak se výsledky z každého vlákna musí sloučit zpátky do jedné sekvence. Typ sloučení, který PLINQ provede, závisí na operátorech, které jsou k dispozici v dotazu. Například operátory, které mají novou objednávku pro výsledky, musí ukládat do vyrovnávací paměti všechny prvky ze všech vláken. Z perspektivy nenáročného vlákna (což je také uživatel aplikace) může být spuštěný dotaz s úplnými vyrovnávacími pamětmi, který je možné určit včas před tím, než vytvoří svůj první výsledek. Jiné operátory jsou ve výchozím nastavení částečně uloženy do vyrovnávací paměti. poskytují své výsledky v dávkách. Jeden operátor není <xref:System.Linq.ParallelEnumerable.ForAll%2A> ve výchozím nastavení ukládán do vyrovnávací paměti. Poskytuje všechny prvky ze všech vláken okamžitě.  
  
 Pomocí <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody, jak je znázorněno v následujícím příkladu, můžete poskytnout nápovědu pro PLINQ, který označuje, jaký typ sloučení provést.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Úplný příklad naleznete v tématu [How to: Zadejte možnosti sloučení v PLINQ](how-to-specify-merge-options-in-plinq.md).  
  
 Pokud konkrétní dotaz nepodporuje požadovanou možnost, bude možnost pouze ignorována. Ve většině případů není nutné zadávat možnost sloučení pro dotaz PLINQ. V některých případech však můžete zjistit testováním a měřením, že se dotaz vykoná nejlépe v režimu, který není výchozí. Běžnou možností použití této možnosti je vynutit operátor sloučení bloků dat pro streamování výsledků, aby bylo možné zajistit lépe reagující uživatelské rozhraní.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions>Výčet obsahuje následující možnosti, které určují, jak se mají u podporovaných tvarů dotazů vydávat konečný výstup dotazu, když se výsledky spotřebují v jednom vlákně:  
  
- `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered>Možnost způsobí, že každý zpracovávaný prvek bude vrácen z každého vlákna, jakmile je vytvořen. Toto chování je podobné jako výstup "streamování". Pokud se <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor nachází v dotazu, `NotBuffered` zachovává pořadí zdrojových elementů. I když `NotBuffered` začne vracet výsledky, jakmile jsou k dispozici, celková doba pro vyprodukování všech výsledků může být stále delší než použití jedné z dalších možností sloučení.  
  
- `Auto Buffered`  
  
     Tato <xref:System.Linq.ParallelMergeOptions.AutoBuffered> možnost způsobí, že dotaz shromáždí prvky do vyrovnávací paměti a poté pravidelně vyhodnotí obsah vyrovnávací paměti na náročné vlákno. Jedná se o podobnou funkci pro zpracování zdrojových dat v blocích "místo použití" streamování " `NotBuffered` . `AutoBuffered`může trvat déle než, `NotBuffered` aby byl první prvek k dispozici na náročném vlákně. Velikost vyrovnávací paměti a přesné chování při vracení není konfigurovatelné a může se lišit v závislosti na různých faktorech, které se vztahují k dotazu.  
  
- `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered>Možnost způsobí, že výstup celého dotazu bude uložen do vyrovnávací paměti před tím, než budou získány jakékoli prvky. Použijete-li tuto možnost, může trvat déle, než bude první prvek k dispozici ve vybírající vlákně, ale kompletní výsledky mohou být stále vytvořeny rychleji než pomocí dalších možností.  
  
## <a name="query-operators-that-support-merge-options"></a>Operátory dotazů, které podporují možnosti sloučení  
 V následující tabulce jsou uvedeny operátory, které podporují všechny režimy možností sloučení, v souladu se zadanými omezeními.  
  
|Operátor|Omezení|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Neseřazené dotazy, které mají pouze zdroj pole nebo seznamu.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Neseřazené dotazy, které mají pouze zdroj pole nebo seznamu.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Žádné|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Žádné|  
  
 Všechny ostatní operátory dotazů PLINQ mohou ignorovat možnosti sloučení poskytované uživatelem. Některé operátory dotazů, například <xref:System.Linq.ParallelEnumerable.Reverse%2A> a <xref:System.Linq.ParallelEnumerable.OrderBy%2A> , nemohou vracet žádné prvky, dokud nebudou všechny vyprodukovány a přeobjednány. Proto při <xref:System.Linq.ParallelMergeOptions> použití v dotazu, který obsahuje také operátor, jako je <xref:System.Linq.ParallelEnumerable.Reverse%2A> , chování sloučení nebude v dotazu použito, dokud tento operátor nevyrobí své výsledky.  
  
 Schopnost některých operátorů zpracovat možnosti sloučení závisí na typu zdrojové sekvence a na tom, zda <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> byl operátor použit dříve v dotazu. <xref:System.Linq.ParallelEnumerable.ForAll%2A>je vždy <xref:System.Linq.ParallelMergeOptions.NotBuffered> , vrátí své prvky hned. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>je vždycky <xref:System.Linq.ParallelMergeOptions.FullyBuffered> ; před tím, než to bude mít, musí seřadit celý seznam.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
- [Postupy: Určení možností sloučení v PLINQ](how-to-specify-merge-options-in-plinq.md)
