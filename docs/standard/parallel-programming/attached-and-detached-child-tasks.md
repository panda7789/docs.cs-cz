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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83451af25006e9da396a3e6618cbecee036e9fe2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003760"
---
# <a name="attached-and-detached-child-tasks"></a>Připojené a odpojené podřízené úlohy
A *podřízená úloha* (nebo *vnořená úloha*) je <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> instanci, která je vytvořena v uživatelském delegátu jiného úkolu, který se označuje jako *nadřazená úloha*. Podřízená úloha může odpojit nebo připojen. A *odpojenou podřízenou úlohu* je úkol, který se spustí bez ohledu na jejich svého nadřazeného objektu. *Připojená podřízená úloha* je vnořená úloha, která se vytvoří s <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost, jejíž nadřazený prvek není explicitně nebo implicitně zakazují, aby ho z přímého připojení. Úkol může vytvořit libovolný počet připojené a odpojené podřízené úlohy, omezen pouze systémovými prostředky.  
  
 V následující tabulce jsou uvedeny základní rozdíly mezi dvěma druhy podřízených úkolů.  
  
|Kategorie|Odpojených podřízených úloh|Připojené podřízené úlohy|  
|--------------|--------------------------|--------------------------|  
|Nadřazený prvek čeká na dokončení podřízených úloh.|Ne|Ano|  
|Nadřazená úloha šíří výjimek vyvolaných podřízenými úlohami.|Ne|Ano|  
|Stav nadřazeného objektu závisí na stavu objektu podřízeného.|Ne|Ano|  
  
 Ve většině scénářů doporučujeme použití odpojených podřízených úloh, protože mají méně složité jejich vztahy s ostatními úlohami. To znamená, proč jsou úlohy vytvářené uvnitř nadřízených úloh odpojeny ve výchozím nastavení, a je nutné explicitně zadat <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvořit připojenou podřízenou úlohu.  
  
## <a name="detached-child-tasks"></a>Odpojených podřízených úloh  
 I když podřízená úloha vytvořena nadřazenou úlohou, ve výchozím nastavení je nezávislá na nadřazené úloze. V následujícím příkladu nadřazená úloha vytvoří jednoduchou podřízenou úlohu. Pokud ukázkový kód spustíte vícekrát, můžete si všimnout, že výstup z příkladu se liší od zobrazení a také, že výstup se může změnit pokaždé, když spustíte kód. K tomu dojde, protože nadřazené a podřízené úlohy se provádějí nezávisle na sobě navzájem; podřízená je odpojená úloha. V příkladu pouze čeká na dokončení nadřazených úloh a podřízená úloha pravděpodobně nebude spuštěna nebo dokončena před konzolovou aplikaci ukončí.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Pokud podřízená úloha je reprezentována <xref:System.Threading.Tasks.Task%601> objekt spíše než <xref:System.Threading.Tasks.Task> objektu, můžete zajistit, že nadřazená úloha bude čekat na podřízenou k dokončení přístupu k <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost podřízené, i pokud se jedná odpojená podřízená úloha. <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnost blokuje až do dokončení svých úkolů, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Připojené podřízené úlohy  
 Na rozdíl od odpojených podřízených úloh jsou připojené podřízené úlohy úzce synchronizovány s nadřazenými. Odpojenou podřízenou úlohu z předchozího příkladu na připojenou podřízenou úlohu můžete změnit pomocí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost v příkazu vytvoření úlohy, jak je znázorněno v následujícím příkladu. V tomto kódu se připojené podřízené úlohy dokončí před nadřazenými. V důsledku toho výstup z příkladu je stejný při každém spuštění kódu.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Připojené podřízené úlohy můžete použít k vytvoření úzce synchronizovaných grafů asynchronních operací.  
  
 Podřízená úloha však můžete připojit k nadřazené úloze pouze v případě, že jeho nadřazený objekt nevylučuje připojených podřízených úloh. Nadřízené úlohy můžete explicitně zabránění podřízené úkoly připojení k nim zadáním <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost v konstruktoru třídy nadřazené úloze nebo <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody. Nadřazené úlohy implicitně zabránit podřízené úlohy k nim připojí, když jsou vytvořeny pomocí volání <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody. Toto dokládá následující příklad. Je stejný jako předchozí příklad, s tím rozdílem, že nadřazená úloha je vytvořen zavoláním <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> metoda místo <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> metody. Vzhledem k tomu, že podřízená úloha není možné se připojit k nadřazené úloze, výstup z příkladu nepředvídatelné. Protože úloha vytváření výchozí možnosti pro <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> zahrnout přetížení <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, tento příklad je funkčně srovnatelný s první příklad v části "Odpojené podřízené úlohy".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Výjimky v podřízených úkolech  
 Pokud odpojená podřízená úloha vyvolá výjimku, musí být tato výjimka zjištěnými nebo zpracovávána přímo v nadřazené úloze, stejně jako u jakékoli úlohy bez vnoření. Pokud připojená podřízená úloha vyvolá výjimku, výjimka se automaticky šíří do nadřazené úlohy a zpět k vláknu, které čeká nebo se pokusí o přístup k úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost. Proto pomocí připojené podřízené úlohy můžete zpracovávat všechny výjimky v jednom místě ve volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> na volajícím vlákně. Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Zrušení a podřízené úlohy  
 Zrušení úlohy je kooperativní. To znamená aby se úloha zrušila, každá připojená nebo odpojená podřízená úloha musí sledovat stav token zrušení. Pokud chcete zrušit nadřazenou položku a všechny jeho podřízené objekty s použitím pouze jedné žádosti, předejte stejný token jako argument pro všechny úlohy a poskytují v jednotlivých úkolech logiku odpovědi na žádost v každé úloze. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Při zrušení nadřazeného  
 Pokud nadřazená úloha zruší sama sebe, před spuštěním jeho podřízené úloze, nikdy spouštěna. Pokud nadřazená úloha zruší sama sebe, po její podřízená úloha je již spuštěna, podřízená úloha poběží do konce ledaže má svojí vlastní logiku zrušení. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Při zrušení odpojené podřízené úlohy  
 Pokud odpojená podřízená úloha zruší sama pomocí stejného tokenu, který byl předán nadřazenému prvku a nadřazeného nečeká podřízenou úlohu, nejsou šířeny žádné výjimky, protože všechny výjimky jsou považovány za neškodné kooperativní zrušení. Toto chování je stejné jako u libovolných úloh nejvyšší úrovně.  
  
### <a name="when-an-attached-child-task-cancels"></a>Při zrušení připojené podřízené úlohy  
 Pokud připojená podřízená úloha zruší sama pomocí stejného tokenu, který byl předán nadřízené úloze, <xref:System.Threading.Tasks.TaskCanceledException> je postoupena do spojovacího vlákna uvnitř <xref:System.AggregateException>. Je nutné počkat nadřazené úloze, aby bylo možné zpracovat všechny neškodné výjimky kromě všechny neškodné výjimky, které byly postoupeny nahoru grafem připojených podřízených úloh.  
  
 Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Zabránění podřízené úloze, mohla připojit k nadřazené  
 Neošetřená výjimka, která je vyvolána podřízenou úlohou se šíří do nadřazené úlohy. Toto chování můžete sledovat všech výjimek podřízené úlohy z jednoho kořene místo procházení stromu úloh. Šíření výjimek však může být problematické, pokud nadřazená úloha neočekává přílohu z jiného kódu. Představte si třeba aplikaci, která volá komponenty knihovny třetí strany z <xref:System.Threading.Tasks.Task> objektu. Pokud součást knihovny třetích stran také vytvoří <xref:System.Threading.Tasks.Task> objektu a určuje <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> připojit k nadřazené úloze, všechny neošetřené výjimky, ke kterým dochází v podřízené úloze se promítnou do nadřazené. To může vést k neočekávanému chování v hlavní aplikaci.  
  
 Chcete-li zabránit podřízené úloze v připojení k nadřazené úloze, zadejte <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> při vytváření nadřazeného možnost <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objektu. Při pokusí připojit k nadřazenému úkolu a ten specifikuje <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, podřízená úloha nebude možné se připojit k nadřazené a spustí stejně jako <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> nebyla zadána možnost.  
  
 Můžete také chtít zabránit podřízené úloze v připojení k nadřazené úloze, pokud podřízená úloha neskončí v časovém limitu. Protože nadřazenou úlohu nedokončí až do dokončení všech podřízených úloh, může způsobit dlouhotrvající podřízená úloha celkový nízký výkon aplikace. Příklad, který ukazuje, jak zlepšit výkon aplikace zabráněním úlohu se připojuje k nadřazené úloze, naleznete v tématu [postupy: zabránění připojení podřízené úlohy ke své nadřazené úloze](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
