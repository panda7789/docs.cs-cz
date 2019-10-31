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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123189"
---
# <a name="attached-and-detached-child-tasks"></a>Připojené a odpojené podřízené úlohy
*Podřízená úloha* (neboli *vnořená úloha*) je instance <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> vytvořená v uživatelském delegátu jiné úlohy, která se označuje jako *nadřazená úloha*. Podřízená úloha může být buď odpojená, nebo připojená. *Odpojená podřízená úloha* je úkol, který se spouští nezávisle na jeho nadřazeném prvku. *Připojená podřízená úloha* je vnořená úloha vytvořená s možností <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>, jejíž nadřazená položka není explicitně nebo ve výchozím nastavení zakazuje připojení. Úkol může vytvořit libovolný počet připojených a odpojených podřízených úloh, které jsou omezeny pouze systémovými prostředky.  
  
 V následující tabulce jsou uvedeny základní rozdíly mezi dvěma druhy podřízených úloh.  
  
|Kategorie|Odpojené podřízené úlohy|Připojené podřízené úlohy|  
|--------------|--------------------------|--------------------------|  
|Nadřazený objekt čeká na dokončení podřízených úloh.|Ne|Ano|  
|Nadřazený objekt šíří výjimky vyvolané podřízenými úlohami.|Ne|Ano|  
|Stav nadřazeného objektu závisí na stavu podřízeného.|Ne|Ano|  
  
 Ve většině scénářů doporučujeme používat odpojené podřízené úlohy, protože jejich vztahy s ostatními úkoly jsou méně složité. To je důvod, proč jsou úlohy vytvořené uvnitř nadřazených úloh odpojeny ve výchozím nastavení a je nutné explicitně zadat možnost <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> pro vytvoření připojené podřízené úlohy.  
  
## <a name="detached-child-tasks"></a>Odpojené podřízené úlohy  
 I když je podřízená úloha vytvořena nadřazenou úlohou, ve výchozím nastavení je nezávislá na nadřazené úloze. V následujícím příkladu vytvoří nadřazená úloha jednu jednoduchou podřízenou úlohu. Pokud spustíte ukázkový kód několikrát, můžete si všimnout, že výstup z příkladu se liší od zobrazeného a také když se výstup může změnit při každém spuštění kódu. K tomu dochází, protože nadřazená úloha a podřízené úlohy se spouštějí nezávisle na sobě. podřízená úloha je odpojená úloha. Příklad čeká pouze na dokončení nadřazené úlohy a podřízená úloha se nemusí spustit nebo dokončit před ukončením aplikace konzoly.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Pokud je podřízená úloha reprezentována objektem <xref:System.Threading.Tasks.Task%601>, nikoli objektem <xref:System.Threading.Tasks.Task>, můžete zajistit, že nadřazená úloha bude čekat na dokončení podřízeného objektu, a to tak, že přejde k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> podřízeného objektu, i když se jedná o odpojenou podřízenou úlohu. Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje až do dokončení jeho úlohy, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Připojené podřízené úlohy  
 Na rozdíl od odpojených podřízených úloh jsou připojené podřízené úlohy úzce synchronizovány s nadřazenou položkou. Odpojenou podřízenou úlohu v předchozím příkladu můžete změnit na připojenou podřízenou úlohu pomocí možnosti <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> v příkazu pro vytvoření úlohy, jak je znázorněno v následujícím příkladu. V tomto kódu se připojená podřízená úloha dokončí před svým nadřazeným prvkem. Výsledkem je, že výstup z příkladu je stejný při každém spuštění kódu.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Připojené podřízené úlohy můžete použít k vytvoření úzce synchronizovaných grafů asynchronních operací.  
  
 Podřízená úloha se ale může připojit k nadřazenému objektu pouze v případě, že jeho nadřazený objekt nezakáže připojené podřízené úlohy. Nadřazené úlohy mohou explicitně zabránit tomu, aby se k nim podřízené úlohy připojily zadáním možnosti <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> v konstruktoru třídy nadřazené úlohy nebo v metodě <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Nadřazené úlohy implicitně zabraňují podřízeným úkolům v připojení, pokud jsou vytvořeny voláním metody <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>. Toto dokládá následující příklad. Je stejný jako předchozí příklad s tím rozdílem, že nadřazená úloha je vytvořena voláním metody <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType>, nikoli metodou <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType>. Vzhledem k tomu, že se podřízená úloha nemůže připojit ke své nadřazené položce, není možné předpovědět výstup z tohoto příkladu. Vzhledem k tomu, že výchozí možnosti vytváření úloh pro <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> přetížení zahrnují <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, je tento příklad funkčně ekvivalentní prvnímu příkladu v části "odpojené podřízené úlohy".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Výjimky v podřízených úlohách  
 Pokud odpojená podřízená úloha vyvolá výjimku, musí být tato výjimka pozorována nebo zpracována přímo v nadřazené úloze stejně jako u libovolné nevnořené úlohy. Pokud připojená podřízená úloha vyvolá výjimku, výjimka je automaticky šířena do nadřazené úlohy a zpět do vlákna, které čeká nebo se pokouší o přístup k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> úkolu. Proto pomocí připojených podřízených úloh můžete zpracovat všechny výjimky pouze v jednom bodě volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> v volajícím vlákně. Další informace naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Zrušení a podřízené úlohy  
 Zrušení úlohy je kooperativní. To znamená, že aby bylo možné je zrušit, každá připojená nebo odpojená podřízená úloha musí monitorovat stav tokenu zrušení. Pokud chcete zrušit nadřazenou položku a všechny její podřízené položky pomocí jedné žádosti o zrušení, předáte stejný token jako argument všem úkolům a v každém úkolu poskytnete logiku reagovat na požadavek v jednotlivých úkolech. Další informace naleznete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [Postup: zrušení úlohy a jejích podřízených objektů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Při zrušení nadřazené položky  
 Pokud nadřazený objekt zruší sám sebe před spuštěním podřízené úlohy, podřízené položky se nikdy nespustí. Pokud nadřazený objekt zruší sám sebe poté, co již byla podřízená úloha spuštěna, bude podřízená tabulka dokončena, pokud nemá svou vlastní logiku zrušení. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Když se zruší odpojená podřízená úloha  
 Pokud odpojená podřízená úloha zruší sebe sama pomocí stejného tokenu, který byl předán nadřazenému objektu, a nadřazený objekt nečeká na podřízenou úlohu, není šířena žádná výjimka, protože výjimka je považována za zrušení neškodné spolupráce. Toto chování je stejné jako u všech úloh nejvyšší úrovně.  
  
### <a name="when-an-attached-child-task-cancels"></a>Když se zruší připojená podřízená úloha  
 Pokud připojená podřízená úloha zruší sebe sama pomocí stejného tokenu, který byl předán své nadřazené úloze, <xref:System.Threading.Tasks.TaskCanceledException> je šířena do spojovacího vlákna v rámci <xref:System.AggregateException>. Je nutné počkat na nadřazenou úlohu, aby bylo možné zpracovat všechny neškodné výjimky kromě všech výjimek, které jsou šířeny pomocí grafu připojených podřízených úloh.  
  
 Další informace naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Zabránění tomu, aby se podřízená úloha připojila k nadřazenému objektu  
 Neošetřená výjimka, která je vyvolána podřízenou úlohou, je šířena do nadřazené úlohy. Toto chování můžete použít ke sledování všech výjimek podřízených úloh z jedné kořenové úlohy namísto procházení stromu úkolů. Šíření výjimky však může být problematické, Pokud nadřazená úloha neočekává přílohu z jiného kódu. Zvažte například aplikaci, která volá komponentu knihovny třetí strany z objektu <xref:System.Threading.Tasks.Task>. Pokud komponenta knihovny třetí strany vytvoří objekt <xref:System.Threading.Tasks.Task> a určí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>, aby ho připojil k nadřazené úloze, všechny neošetřené výjimky, ke kterým dojde v podřízené úloze, se šíří do nadřazeného objektu. To může vést k neočekávanému chování v hlavní aplikaci.  
  
 Chcete-li zabránit tomu, aby se podřízená úloha připojila k nadřazené úloze, určete možnost <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> při vytváření nadřazeného objektu <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Když se úloha pokusí připojit k nadřazené položce a Nadřazená položka určuje možnost <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, podřízená úloha se nebude moci připojit k nadřazenému objektu a provede se stejným způsobem, jako kdyby nebyla zadána možnost <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>.  
  
 V případě, že se podřízená úloha nedokončuje včas, můžete také zabránit tomu, aby se podřízená úloha připojila k nadřazené úloze. Vzhledem k tomu, že nadřazená úloha není dokončena, dokud nebudou dokončeny všechny podřízené úlohy, může dlouhodobě spuštěná podřízená úloha způsobit, že celková aplikace nebude fungovat špatně. Příklad, který ukazuje, jak zlepšit výkon aplikace tím, že zabráníte tomu, aby se úloha připojila k nadřazené úloze, najdete v tématu [How to: Inpomoci při připojení podřízené úlohy ke své nadřazené položce](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
