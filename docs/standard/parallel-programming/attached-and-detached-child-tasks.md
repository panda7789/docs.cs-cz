---
title: Připojené a odpojené podřízené úlohy
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
ms.openlocfilehash: 8f15ee4f136e3e2df1a4e1c7683467f2a4bc9bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123189"
---
# <a name="attached-and-detached-child-tasks"></a>Připojené a odpojené podřízené úlohy
Podřízený *úkol* (nebo *vnořený úkol*) je <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> instance, která je vytvořena v delegátovi uživatele jiné úlohy, která se označuje jako *nadřazená úloha*. Podřízený úkol může být odpojen nebo připojen. *Odpojená podřízená úloha* je úloha, která se provádí nezávisle na nadřazené úloze. Připojený *podřízený úkol* je vnořený úkol, který je vytvořen s <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možností, jejíž nadřazený není explicitně nebo ve výchozím nastavení zakázat připojení. Úkol může vytvořit libovolný počet připojených a odpojených podřízených úloh, omezených pouze systémovými prostředky.  
  
 V následující tabulce jsou uvedeny základní rozdíly mezi dvěma druhy podřízených úkolů.  
  
|Kategorie|Odpojené podřízené úkoly|Připojené podřízené úkoly|  
|--------------|--------------------------|--------------------------|  
|Nadřazený čeká na dokončení podřízených úkolů.|Ne|Ano|  
|Nadřazený šíří výjimky vyzývané podřízenými úkoly.|Ne|Ano|  
|Stav rodiče závisí na stavu dítěte.|Ne|Ano|  
  
 Ve většině případů doporučujeme použít odpojené podřízené úkoly, protože jejich vztahy s jinými úkoly jsou méně složité. To je důvod, proč jsou úkoly vytvořené uvnitř nadřazených úkolů ve výchozím nastavení odpojeny a je nutné explicitně zadat <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvoření připojené podřízené úlohy.  
  
## <a name="detached-child-tasks"></a>Odpojené podřízené úkoly  
 Přestože je podřízená úloha vytvořena nadřazeným úkolem, je ve výchozím nastavení nezávislá na nadřazené úloze. V následujícím příkladu nadřazený úkol vytvoří jednu jednoduchou podřízenou úlohu. Pokud spustíte ukázkový kód vícekrát, můžete si všimnout, že výstup z příkladu se liší od zobrazené a také, že výstup může změnit při každém spuštění kódu. K tomu dochází, protože nadřazené úlohy a podřízené úkoly provádět nezávisle na sobě; dítě je samostatný úkol. Příklad čeká pouze na dokončení nadřazené úlohy a podřízená úloha se nemusí spustit nebo dokončit před ukončením konzolové aplikace.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Pokud je podřízená <xref:System.Threading.Tasks.Task%601> úloha reprezentována objektem, nikoli objektem, <xref:System.Threading.Tasks.Task> můžete zajistit, že <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> nadřazená úloha bude čekat na dokončení podřízené ho dokončení přístupem k vlastnosti podřízeného i v případě, že se jedná o odpojenou podřízenou úlohu. Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje, dokud jeho úkol dokončí, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Připojené podřízené úkoly  
 Na rozdíl od odpojených podřízených úkolů jsou připojené podřízené úkoly úzce synchronizovány s nadřazenou úlohou. Odpojenou podřízenou úlohu v předchozím příkladu můžete změnit <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> na připojenou podřízenou úlohu pomocí možnosti v příkazu vytvoření úkolu, jak je znázorněno v následujícím příkladu. V tomto kódu musí být připojená podřízená úloha dokončena před nadřazenou úlohou. V důsledku toho výstup z příkladu je stejný při každém spuštění kódu.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Připojené podřízené úlohy můžete použít k vytvoření úzce synchronizovaných grafů asynchronních operací.  
  
 Podřízený úkol se však může připojit k nadřazenému úkolu pouze v případě, že její nadřazený úkol nezakazuje připojené podřízené úkoly. Nadřazené úkoly mohou explicitně zabránit <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> tomu, aby se k nim podřízené úkoly připojily zadáním možnosti v konstruktoru třídy nadřazeného úkolu nebo v metodě. <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> Nadřazené úkoly implicitně zabránit podřízené úkoly <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> z jejich připojení, pokud jsou vytvořeny voláním metody. Toto dokládá následující příklad. Je totožný s předchozím příkladem, s tím <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> rozdílem, <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> že nadřazený úkol je vytvořen voláním metody spíše než metody. Vzhledem k tomu, že podřízený úkol není schopen připojit k nadřazené, výstup z příkladu je nepředvídatelné. Vzhledem k tomu, <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> že výchozí <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>možnosti vytváření úloh pro přetížení zahrnují , tento příklad je funkčně ekvivalentní prvnímu příkladu v části "Odpojené podřízené úkoly".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Výjimky v podřízených úkolech  
 Pokud odpojená podřízená úloha vyvolá výjimku, musí být tato výjimka pozorována nebo zpracována přímo v nadřazené úloze stejně jako u všech nevnořených úloh. Pokud připojená podřízená úloha vyvolá výjimku, výjimka se automaticky rozšíří do nadřazené úlohy a <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> zpět do vlákna, které čeká nebo se pokusí o přístup k vlastnosti úlohy. Proto pomocí připojené podřízené úkoly, můžete zpracovat všechny výjimky <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pouze v jednom bodě volání na volající vlákno. Další informace naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Zrušení a podřízené úkoly  
 Zrušení úkolu je kooperativní. To znamená, že chcete-li zrušit, musí každá připojená nebo odpojená podřízená úloha sledovat stav tokenu zrušení. Pokud chcete zrušit nadřazenou položku a všechny jeho podřízené položky pomocí jednoho požadavku na zrušení, předáte stejný token jako argument všem úkolům a v každém úkolu poskytnete logiku pro odpověď na požadavek v jednotlivých úkolech. Další informace naleznete v [tématu Zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md) a [postup: Zrušení úkolu a jeho podřízených úloh](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Když rodič zruší  
 Pokud nadřazený zruší sám před spuštěním podřízené úlohy, podřízený nikdy nespustí. Pokud nadřazený zruší sám po jeho podřízené úlohy již byla zahájena, podřízený spustí k dokončení, pokud má vlastní logiku zrušení. Další informace naleznete v [tématu Zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Když se odpojená podřízená úloha zruší  
 Pokud odpojené podřízené úlohy zruší sám pomocí stejného tokenu, který byl předán nadřazený a nadřazený nečeká na podřízenou úlohu, žádná výjimka je rozšířena, protože výjimka je považována za neškodné zrušení spolupráce. Toto chování je stejné jako u všech úkolů nejvyšší úrovně.  
  
### <a name="when-an-attached-child-task-cancels"></a>Když se připojený podřízený úkol zruší  
 Když připojené podřízené úlohy zruší sám pomocí stejného tokenu, <xref:System.Threading.Tasks.TaskCanceledException> který byl předán jeho nadřazené úlohy, a je rozšířena do spojovacího vlákna uvnitř <xref:System.AggregateException>. Musíte počkat na nadřazenou úlohu, abyste mohli zpracovávat všechny neškodné výjimky kromě všech chybných výjimek, které jsou šířeny prostřednictvím grafu připojených podřízených úloh.  
  
 Další informace naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Zabránění připojení podřízené úlohy k nadřazené úloze  
 Neošetřená výjimka, která je vyvolána podřízenou úlohou, je rozšířena na nadřazenou úlohu. Toto chování můžete použít k pozorování všech výjimek podřízených úloh z jedné kořenové úlohy namísto procházení stromu úkolů. Šíření výjimek však může být problematické, pokud nadřazená úloha neočekává přílohu z jiného kódu. Zvažte například aplikaci, která volá komponentu <xref:System.Threading.Tasks.Task> knihovny jiného výrobce z objektu. Pokud součást knihovny jiného <xref:System.Threading.Tasks.Task> výrobce také <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> vytvoří objekt a určuje jeho připojení k nadřazené úloze, všechny neošetřené výjimky, ke kterým dochází v podřízené úloze, se rozšíří na nadřazenou úlohu. To může vést k neočekávanému chování v hlavní aplikaci.  
  
 Chcete-li zabránit připojení podřízené úlohy k <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> nadřazené <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> úloze, zadejte tuto možnost při vytváření nadřazeného nebo objektu. Když se úloha pokusí připojit k nadřazené a nadřazená určuje <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, podřízená <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> úloha se nebude moci připojit k nadřazené úloze a provede se stejně, jako by tato možnost nebyla zadána.  
  
 Můžete také zabránit podřízené úloze v připojení k nadřazené úlohě, když podřízená úloha není dokončena včas. Vzhledem k tomu, že nadřazená úloha se nedokončí, dokud nebudou dokončeny všechny podřízené úlohy, může dlouho běžící podřízená úloha způsobit, že celková aplikace bude fungovat špatně. Příklad, který ukazuje, jak zlepšit výkon aplikace tím, že brání úkolu v připojení k nadřazenému úkolu, najdete v [tématu Jak: Zabránit podřízené úloze v připojení k nadřazené úloze](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
