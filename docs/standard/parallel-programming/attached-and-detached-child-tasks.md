---
title: "Připojené a odpojené podřízené úlohy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1a0c664dffc2986d4d6985fd2b71cd8055bf2c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attached-and-detached-child-tasks"></a>Připojené a odpojené podřízené úlohy
A *podřízené úlohy* (nebo *vnořené úlohy*) je <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> instance, který je vytvořen v jiné úlohy, která se označuje jako delegát uživatele *nadřazené úlohy*. Podřízené úlohy můžete odpojit nebo připojen. A *odpojené podřízené úlohy* je úkol, který provádí nezávisle na jeho nadřazený objekt. *Podřízené úlohy připojený* vnořené úloha, která je vytvořena s <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost, jehož nadřazeným prvkem není explicitně nebo ve výchozím nastavení zakazují ho připojovaný. Úkol může vytvořit libovolný počet připojené a odpojené podřízené úlohy, omezena pouze systémové prostředky.  
  
 Následující tabulka uvádí základní rozdíly mezi dva druhy podřízené úlohy.  
  
|Kategorie|Odpojené podřízené úlohy|Připojené podřízené úlohy|  
|--------------|--------------------------|--------------------------|  
|Nadřazené čeká na dokončení úloh podřízené.|Ne|Ano|  
|Nadřazené rozšíří výjimky vyvolané podřízené úlohy.|Ne|Ano|  
|Stav nadřazeného závisí na stavu podřízené.|Ne|Ano|  
  
 Ve většině scénářů doporučujeme použít odpojené podřízené úlohy, protože jejich vztahů s ostatními úkoly jsou méně složitých. To znamená, proč jsou ve výchozím nastavení odpojené úkoly vytvořené v nadřazené úlohy, a je nutné explicitně zadat <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvořit připojené podřízené úlohy.  
  
## <a name="detached-child-tasks"></a>Odpojené podřízené úlohy  
 I podřízené úlohy je vytvořený nadřazené úlohy, ve výchozím nastavení je nezávislé na nadřazené úlohy. V následujícím příkladu se vytvoří úlohu nadřazené jeden jednoduché podřízené úlohy. Pokud spustíte příklad kódu několikrát, může dojít k výstupu z příkladu se liší od zobrazená, a také že výstup může změnit pokaždé, když provedete spuštění kódu. K tomu dochází, protože úloha nadřazené a podřízené úlohy spustit nezávisle na sobě navzájem; podřízená je odpojit úloha. V příkladu pouze čeká na dokončení, úlohy nadřazené a podřízené úlohy nemusí spustit nebo dokončení před konzolovou aplikaci ukončí.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Pokud je reprezentována podřízené úlohy <xref:System.Threading.Tasks.Task%601> objekt ne <xref:System.Threading.Tasks.Task> objekt, můžete zajistit, že nadřazené úlohy počká na podřízené k dokončení přístup k <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost podřízeného i v případě, že je odpojené podřízené úlohy. <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnost blokuje až do dokončení úkolu, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Připojené podřízené úlohy  
 Na rozdíl od odpojené podřízené úlohy jsou synchronizovány s nadřazenou úzce připojené podřízené úlohy. Odpojené podřízené úlohy v předchozím příkladu na připojené podřízené úlohy můžete změnit pomocí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost v příkazu vytvoření úlohy, jak je znázorněno v následujícím příkladu. V tomto kódu připojené podřízené úlohy dokončení před jeho nadřazený objekt. V důsledku toho výstup z příkladu je stejný pokaždé, když spustíte kód.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Připojené podřízené úlohy můžete použít k vytvoření úzce synchronizovaných grafů asynchronních operací.  
  
 Podřízené úlohy však můžete připojit ke své nadřazené úloze pouze v případě, že jeho nadřazený objekt není zakázat připojené podřízené úlohy. Nadřazené úlohy můžete explicitně zabránění podřízené úlohy připojení k nim zadáním <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost v konstruktoru třídy nadřazené úlohy nebo <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda. Nadřazené úlohy implicitně zabránit podřízené úlohy připojení k nim, pokud jsou vytvořené pomocí volání <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda. Toto dokládá následující příklad. Je stejný jako předchozí příklad, s tím rozdílem, že vytvoření úlohy nadřazené voláním <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> metoda místo <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> metoda. Protože podřízené úlohy není připojit ke své nadřazené úloze, nepředvídatelným výstup z příkladu. Vzhledem k tomu, že vytváření úlohy výchozí možnosti pro <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> zahrnují přetížení <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, v tomto příkladu je funkčně srovnatelný v prvním příkladu v části "Odpojené podřízené úlohy".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Výjimky v podřízené úlohy  
 Pokud odpojené podřízené úlohy vyvolá výjimku, musí být dodržen této výjimky nebo přímo v nadřazené úloze zpracovává stejně jako v jakékoli úlohy,-nested. Pokud připojená úloha vyvolá výjimku, výjimka je automaticky rozšířena do nadřazené úlohy a zpět na vlákno, které čeká nebo se pokusí o přístup k úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost. Proto může pomocí připojené podřízené úlohy zpracovat všechny výjimky v jednom místě ve volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> na volající vlákno. Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Zrušení a podřízené úlohy  
 Zrušení úlohy je spolupráci. To znamená aby bylo možné zrušit, musí každý připojené nebo odpojené podřízené úlohy sledování stavu token zrušení. Pokud chcete zrušit nadřazený a všechny její podřízené položky pomocí jedné žádosti, můžete předat stejný token jako argument všechny úlohy, které poskytují v každé úloze logiku reagovat na žádosti v každé úloze. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Pokud nadřazená zruší  
 Pokud nadřazený se zruší, před zahájením jeho podřízené úlohy, spustí se nikdy podřízený objekt. Pokud nadřazený se zruší, po jeho podřízené úlohy je již spuštěn, spustí podřízené k dokončení, pouze pokud má svou vlastní logiky zrušení. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Při zrušení odpojené podřízené úlohy  
 Pokud odpojené podřízené úlohy se zruší, pomocí stejný token, který byl předán do nadřazené a nadřazeného nečeká podřízené úlohy, žádná výjimka šíří, protože výjimka je považován za neškodné spolupráce zrušení. Toto chování je stejné jako u jakékoli úlohy, nejvyšší úrovně.  
  
### <a name="when-an-attached-child-task-cancels"></a>Při zrušení připojené podřízené úlohy  
 Pokud připojená úloha se zruší, pomocí stejný token, který byl předán nadřazené úkolu, <xref:System.Threading.Tasks.TaskCanceledException> rozšířena do spojovacího vlákna uvnitř <xref:System.AggregateException>. Je nutné počkat nadřazené úlohy tak, aby bylo možné zpracovat všechny neškodné výjimky kromě všech neškodné výjimky, které rozšířeny nahoru prostřednictvím graf připojené podřízené úlohy.  
  
 Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Brání připojení k nadřazené podřízené úlohy  
 Neošetřená výjimka, která je vyvolané podřízené úlohy se rozšíří do nadřazené úlohy. Toto chování můžete sledovat všechny podřízené úlohy výjimky z úlohy jeden kořenový místo procházení stromu úloh. Výjimka šíření však může být problematické, pokud úloha nadřazené neočekává přílohy z jiných kódu. Představte si třeba aplikaci, která volá komponentu z knihovny třetích stran <xref:System.Threading.Tasks.Task> objektu. Pokud komponentu knihovny třetí strany vytvoří také <xref:System.Threading.Tasks.Task> objektu a určuje <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> připojení k nadřazené úlohy, všechny neošetřených výjimek, které se vyskytují v podřízené úlohy rozšíří do nadřazené. To může vést k neočekávanému chování v hlavní aplikaci.  
  
 Abyste zabránili se připojuje k úkolu nadřazené podřízené úlohy, zadejte <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> při vytvoření nadřazeného <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objektu. Když úloha pokusí připojit ke své nadřazené úloze a Určuje nadřazený <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, nebudou moci připojit k nadřazenému podřízené úlohy a spustí jenom jako kdyby <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> nebyla zadána možnost.  
  
 Také můžete chtít podřízené úlohy zabránit v připojení k nadřazené při podřízené úlohy nebyl dokončen v časovém limitu. Protože úloha nadřazené nedokončí, dokud nedokončí všechny podřízené úlohy, dlouhodobé podřízené úlohy může způsobit celkové aplikaci nízký výkon. Příklad, který ukazuje, jak zlepšit výkon aplikace tak, že zabrání připojení k nadřazené úkolu úlohu, naleznete v části [postupy: zabránění Attaching podřízené úlohy ke své nadřazené úloze](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
