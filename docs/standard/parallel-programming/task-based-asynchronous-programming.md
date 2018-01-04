---
title: "Asynchronní programování založené na úlohách"
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
helpviewer_keywords: parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
caps.latest.revision: "51"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8e5367c8a786d720cdf3394922527020f8d4d47a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="task-based-asynchronous-programming"></a>Asynchronní programování založené na úlohách
Task Parallel Library (TPL) je založena na konceptu *úloh*, která představuje asynchronní operaci. V některých způsobech úlohu podobá vlákna nebo <xref:System.Threading.ThreadPool> pracovních položek, ale na vyšší úrovni abstrakce. Termín *úkolů paralelismus* odkazuje na jeden nebo více nezávislých úkoly, které jsou spuštěné současně. Úlohy poskytují dvě hlavní výhody:  
  
-   Větší škálovatelnost a efektivnější využívání systémových prostředků.  
  
     Na pozadí jsou úlohy zařazené do <xref:System.Threading.ThreadPool>, které se rozšířily o algoritmy, zjistit a upravte počet vláken, a které poskytují, Maximalizovat propustnost Vyrovnávání zatížení. Díky tomu jsou úlohy relativně lehké a lze jich vytvořit mnoho, takže lze dosáhnout jemně odstupňovaného paralelismu.  
  
-   Více programového ovládání než je k dispozici s vláknem nebo pracovní položkou.  
  
     Úlohy a architektura kolem nich vytvořená poskytují bohatou sadu rozhraní (API), která podporují čekání, zrušení, pokračování, robustní zpracování výjimek, podrobný stav, vlastní plánování a další.  
  
 Pro oba z těchto důvodů je v rozhraní .NET Framework TPL upřednostňovaným rozhraním API pro psaní vícevláknového, asynchronního a paralelního kódu.  
  
## <a name="creating-and-running-tasks-implicitly"></a>Vytvoření a spuštění úloh implicitně  
 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> Metoda představuje pohodlný způsob pro souběžnou libovolný počet různých příkazů. Stačí pouze předat <xref:System.Action> delegáta pro každou položku práce. Nejsnadnější způsob, jak vytvořit tyto delegáty, je použití lambda výrazů. Lambda výraz může buďto volat pojmenovanou metodu, nebo poskytnout vložený kód. Následující příklad ukazuje základní <xref:System.Threading.Tasks.Parallel.Invoke%2A> volání, které se vytvoří a spustí dvě úlohy, které běží souběžně. První úlohou je reprezentována výrazu lambda, která volá metodu s názvem `DoSomeWork`, a v druhé úloze je reprezentována výrazem lambda, která volá metodu s názvem `DoSomeOtherWork`.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
 [!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]  
  
> [!NOTE]
>  Počet <xref:System.Threading.Tasks.Task> instancí, které jsou vytvořeny na pozadí pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> není nutně roven počtu zadaných delegátů, které jsou k dispozici. Knihovna TPL může využít různé optimalizace, zejména s velkým počtem delegátů.  
  
 Další informace najdete v tématu [postupy: použití Parallel.Invoke k provádění paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).  
  
 Pro větší kontrolu nad spuštění úkolu nebo na vrácení hodnoty z úlohy, budete muset pracovat s <xref:System.Threading.Tasks.Task> více explicitně objekty.  
  
## <a name="creating-and-running-tasks-explicitly"></a>Vytvoření a spuštění úloh explicitně  
 Úloha, která nevrátí hodnotu je reprezentována <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy. Úloha, která vrátí hodnotu, je reprezentována <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> třídy, která dědí z <xref:System.Threading.Tasks.Task>. Objekt úlohy zpracovává podrobnosti infrastruktury a poskytuje metody a vlastnosti, které jsou přístupné z volajícího vlákna po celou dobu trvání úlohy. Například můžete získat přístup <xref:System.Threading.Tasks.Task.Status%2A> vlastnosti úlohy kdykoli k určení, zda byla spuštěna, byl dokončen, byla zrušena nebo došlo k výjimce. Stav je reprezentována <xref:System.Threading.Tasks.TaskStatus> výčtu.  
  
 Když je vytvořena úloha, je jí zadán uživatelský delegát, jenž provádí zapouzdření kódu, který úloha provede. Tento delegát může být vyjádřen jako pojmenovaný delegát, anonymní metoda nebo lambda výraz. Lambda výrazy mohou obsahovat volání pojmenované metody, jak ukazuje následující příklad. Všimněte si, že v příkladu obsahuje volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodou, jak zajistit, že úloha dokončí provádění před ukončením aplikace režimu konzoly.  
  
 [!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
 [!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]  
  
 Můžete také <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody pro vytvoření a spuštění úlohy v rámci jedné operace. Ke správě úlohy, <xref:System.Threading.Tasks.Task.Run%2A> metody použití výchozího plánovače úloh, bez ohledu na to, jaké úlohu plánovače souvisí s aktuální vlákno. <xref:System.Threading.Tasks.Task.Run%2A> Metody jsou upřednostňovaný způsob, jak vytvořit a spustit úlohy v případě, že není potřeba větší kontrolu nad vytvoření a plánování úloh.  
  
 [!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
 [!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]  
  
 Můžete také <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodu pro vytvoření a spuštění úlohy v rámci jedné operace. Tuto metodu použijte, když vytvoření a plánování nemusí být oddělené a chcete, aby možnosti vytvoření další úlohy nebo použijte konkrétní scheduleru, nebo když potřebujete předat další stav do úlohy prostřednictvím jeho <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost, jak je znázorněno Následující příklad.  
  
 [!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/startnew1.cs#3)]
 [!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/startnew1.vb#3)]  
  
 <xref:System.Threading.Tasks.Task>a <xref:System.Threading.Tasks.Task%601> každý vystavit statického <xref:System.Threading.Tasks.Task.Factory%2A> vlastnost, která vrací výchozí instanci <xref:System.Threading.Tasks.TaskFactory>, takže můžete volat metodu jako `Task.Factory.StartNew()`. Také v následujícím příkladu protože úlohy jsou typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, každá má veřejné <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost, která obsahuje výsledek výpočet. Úlohy běží asynchronně a mohou být dokončeny v libovolném pořadí. Pokud <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost přistupuje předtím, než se dokončí výpočet, vlastnost blokuje volající vlákno, dokud nebude k dispozici hodnota.  
  
 [!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
 [!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]  
  
 Další informace najdete v tématu [postupy: vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 Při použití lambda výrazu k vytvoření delegáta máte přístup ke všem proměnným, které jsou v daném okamžiku viditelné ve zdrojovém kódu. V některých případech, zejména v rámci smyčky, však lambda nezachytí proměnnou podle očekávání. Pouze zachycuje konečnou hodnotu, nikoli mutaci hodnoty po každé iteraci. Následující příklad ukazuje tento problém. Pak předá smyčku čítač výrazu lambda, která vytvoří `CustomData` objektu a používá čítač smyčky jako identifikátor objektu. Jako výstup z příkladu znázorňuje všechny `CustomData` objekt má stejné identifikátor.  
  
 [!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
 [!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]  
  
 K hodnotě v každé iteraci můžete přistupovat zadáním objektu stavu úlohy pomocí jeho konstruktoru. Následující příklad změní předchozí příklad pomocí čítač smyčky při vytváření `CustomData` objekt, který je pak předaný výrazu lambda.  Jako výstup z příkladu znázorňuje všechny `CustomData` objekt teď má jedinečný identifikátor na základě hodnoty čítače smyčky v době byla vytvořena instance objektu.  
  
 [!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
 [!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]  
  
 Tento stav je předán jako argument delegáta úlohy a byla přístupná z objektu úlohy pomocí <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastnost.  Následující příklad je podobný předchozímu příkladu. Použije <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost pro zobrazení informací o `CustomData` objekty předaný výrazu lambda.  
  
 [!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
 [!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]  
  
## <a name="task-id"></a>ID úlohy  
 Každá úloha obdrží ID celé číslo, které jednoznačně identifikuje v doméně aplikace a je přístupný pomocí <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> vlastnost. ID je užitečné pro zobrazení informací o úkolu v ladicím programu sady Visual Studio **paralelní zásobníky** a **úlohy** systému windows. ID využívá líné vytváření, což znamená, že není vytvořeno, dokud se o něj nepožádá, proto může mít úloha při každém spuštění programu jiné ID. Další informace o tom, jak zobrazit ID úkolu v ladicím programu najdete v tématu [používání okna úloh](/visualstudio/debugger/using-the-tasks-window) a [použití okna paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
## <a name="task-creation-options"></a>Možnosti vytvoření úlohy  
 Většina rozhraní API, které vytvářejí úlohy poskytují přetížení, které přijímají <xref:System.Threading.Tasks.TaskCreationOptions> parametr. Zadáním jedné z těchto možností lze dát pokyn plánovači úloh, jak naplánovat úlohy ve fondu vláken. V následující tabulce jsou uvedeny různé možnosti pro vytváření úloh.  
  
|<xref:System.Threading.Tasks.TaskCreationOptions>Hodnota parametru|Popis|  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|  
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Výchozí hodnota, pokud není zadána jiná. Plánovač používá k plánování úlohy své výchozí heuristické metody.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Určuje, že úlohy by měly být naplánovány tak, aby se úlohy vytvořené dříve pravděpodobně prováděly dříve a později vytvořené úlohy aby se s větší pravděpodobností prováděly později.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Určuje, že úloha představuje dlouhotrvající operaci.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Určuje, že úloha by měla být vytvořena jako připojená podřízená úloha aktuální úlohy, pokud existuje. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|  
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Určuje, že pokud určuje vnitřní úloh `AttachedToParent` možnost této úlohy se stává připojené podřízené úlohy.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Určuje, že Plánovač úloh pro úlohy vytvořen při volání metody, třeba <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> uvnitř určitý úkol je scheduler výchozí místo scheduler, na kterém je tato úloha spuštěna.|  
  
 Možnosti mohou být kombinovány s použitím bitové **nebo** operaci. Následující příklad ukazuje úkol, který má <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> možnost.  
  
 [!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
 [!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]  
  
## <a name="tasks-threads-and-culture"></a>Úlohy, vláken a kultury  
 Každé vlákno má přidružené jazykovou verzi a jazyková verze uživatelského rozhraní, který je definovaný <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti, v uvedeném pořadí. Jazykovou verzi vlákna se používá v těchto operací jako formátování, analýza, řazení a porovnání řetězců. Jazyková verze uživatelského rozhraní vlákno se používá v vyhledávání prostředků. Normálně Pokud nezadáte výchozí jazykovou verzi pro všechna vlákna v doméně aplikace pomocí <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> vlastnosti, výchozí jazykovou verzi a jazyková verze uživatelského rozhraní vlákna je definována systémovou kulturu. Pokud explicitně nastavit jazykovou verzi vlákna a spustit nové vlákno, nové vlákno nedědí jazykovou verzi volající vlákno; Místo toho jeho jazyková verze je výchozí jazykovou verzi systému. Programovací model pro aplikace, které cílové verze rozhraní .NET Framework před založený na úlohách [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] řídit tento postup.  
  
> [!IMPORTANT]
>  Všimněte si, že volající vlákno jazykové verzi v rámci úkolu kontextu se vztahují na aplikace, *cíl* [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], není aplikace, *běh* [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Při vytváření projektu v sadě Visual Studio vyberte z rozevíracího seznamu v horní části této verze, můžete vybrat konkrétní verzi rozhraní .NET Framework **nový projekt** dialogové okno, nebo mimo ni Visual Studio můžete použít <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut. Pro aplikace, které cílové verze rozhraní .NET Framework před verzí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], nebo který cílit na konkrétní verzi rozhraní .NET Framework, bude určen jazykovou verzi vlákna, ve kterém běží pokračuje úkolu jazykovou verzi.  
  
 Počínaje aplikací cílených [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], zdědí jazykovou verzi volající vlákno každý úkol, i když tato úloha se spustí asynchronně na vlákno fondu vláken.  
  
 Následující příklad uvádí jednoduchý obrázek. Použije <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut target [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a mění aktuální jazykovou verzi aplikace buď francouzština (Francie), nebo pokud francouzština (Francie) je již aktuální jazykové verze Angličtina (Spojené státy). Poté vyvolá delegáta s názvem `formatDelegate` , který vrací čísla formátovaná jako hodnoty měny v nové jazykové verze. Všimněte si, že zda delegát jako úlohu synchronně nebo asynchronně, vrátí očekávaný výsledek protože jazykovou verzi volající vlákno je zdědí asynchronní úlohu.  
  
 [!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
 [!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]  
  
 Pokud používáte Visual Studio, můžete vynechat <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut a místo toho vyberte rozhraní .NET Framework 4.6 jako cíl, když vytvoříte projekt v **nový projekt** dialogové okno.  
  
 Pro výstup, která odráží chování aplikací cílové verze rozhraní .NET Framework před [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], odeberte <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut ze zdrojového kódu. Výstup bude odrážet konvencí formátování výchozí systémovou kulturu, není jazyková verze volající vlákno.  
  
 Další informace o asynchronních úloh a jazykovou verzi, najdete v části "Jazyková verze a asynchronní operace založené na úlohách" v <xref:System.Globalization.CultureInfo> tématu.  
  
## <a name="creating-task-continuations"></a>Vytváření pokračování úlohy  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> metody umožňují zadat při spuštění úlohy *předchozí úlohou* dokončí. Delegát úkolů pokračování je předán odkaz na předchozí úlohou tak, aby mohl zkontrolovat stav předchozí úlohou a při získávání hodnoty <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost, můžete použít výstup předchůdce jako vstup pro pokračování.  
  
 V následujícím příkladu `getData` úloha je spuštěna voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> metoda. `processData` Úloha je spuštěna automaticky při `getData` dokončí, a `displayData` při spuštění `processData` dokončí. `getData`Vytvoří celočíselné pole, která je přístupná `processData` úkolů prostřednictvím `getData` úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost. `processData` Úloh zpracovává tohoto pole a vrátí výsledek, jehož typ je odvozen z návratový typ výrazu lambda předaný <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> metoda. `displayData` Úloha se spustí automaticky při `processData` dokončí a <xref:System.Tuple%603> objekt vrácený `processData` výrazu lambda je přístupné `displayData` úlohy prostřednictvím `processData` úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Vlastnost. `displayData` Úloh trvá výsledek `processData` úkolů a vytváří výsledek, jejichž typ je odvozen podobným způsobem a který je k dispozici v programu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.  
  
 [!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
 [!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]  
  
 Protože <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> je metoda instance, můžete řetězu volání metod společně, namísto vytváření instancí <xref:System.Threading.Tasks.Task%601> objekt pro každý předchozí úlohou. Následující příklad je funkčně stejný jako předchozí příklad, s tím rozdílem, že zřetězený společně volání <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metoda. Všimněte si, že <xref:System.Threading.Tasks.Task%601> objekt vrácený řetězec volání metod je úloha konečné pokračování.  
  
 [!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
 [!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]  
  
 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody umožňují pokračovat z více úloh.  
  
 Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování pomocí](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="creating-detached-child-tasks"></a>Vytváření odpojené podřízené úlohy  
 Když uživatelský kód, který běží v úloze vytvoří novou úlohu a neurčuje <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost, Nová úloha není synchronizován s nadřazené úlohy žádným zvláštním způsobem. Tento typ úlohy není synchronizována se nazývá *odpojit vnořené úlohy* nebo *odpojené podřízené úlohy*. Následující příklad zobrazuje úlohu, která vytváří jednu odpojenou podřízenou úlohu.  
  
 [!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
 [!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]  
  
 Nadřazená úloha nečeká na dokončení odpojené podřízené úlohy.  
  
## <a name="creating-child-tasks"></a>Vytvoření podřízené úlohy  
 Když uživatelský kód, který běží v úloze vytvoří úlohu s <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost Nová úloha se označuje jako *podřízené úlohy připojený* nadřazeného úkolu. Můžete použít <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost k strukturovaného paralelismu úloh, protože nadřazená úloha implicitně čeká na dokončení všech úloh připojené podřízené. Následující příklad zobrazuje nadřazenou úlohu, která vytvoří deset připojených podřízených úloh. Všimněte si, že i když se volá v příkladu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda čekání na dokončení úlohy nadřazené nemá explicitně čekat na dokončení úlohy připojený podřízené.  
  
 [!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
 [!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]  
  
 Nadřazené úloh můžete použít <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost zabránění připojení do nadřazené úlohy další úlohy. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="waiting-for-tasks-to-finish"></a>Čekání na dokončení úkolů  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy poskytují několik přetížení <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> a <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>--> `System.Threading.Tasks.Task.Wait` metody, které vám umožní počkejte na dokončení úlohy. Kromě toho přetížení statické <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody umožňují čekat některá nebo všechna pole na dokončení úkolů.  
  
 Obvykle se na úlohu čeká z některého z těchto důvodů:  
  
-   Hlavní vlákno závisí na konečném výsledku vypočítaném úlohou.  
  
-   Je potřeba zpracovat výjimky, které mohou být vyvolány z úlohy.  
  
-   Aplikace se může ukončit předtím, než se dokončí všechny úlohy. Například konzolové aplikace se ukončí co nejdříve veškerých synchronních kód v `Main` provedlo (vstupní bod aplikace).  
  
 Následující příklad zobrazuje základní vzor, který nezahrnuje zpracování výjimek.  
  
 [!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
 [!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]  
  
 Příklad, který ukazuje výjimek, naleznete v části [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
 Některé přetížení umožňují zadat časový limit a jiné přijímají další <xref:System.Threading.CancellationToken> jako vstupní parametr, tak, aby mohlo být samotné čekání zrušeno buď programově, nebo jako odpověď na uživatelský vstup.  
  
 Když čekat úlohy je implicitně počkat všechny podřízené dané úlohy, které byly vytvořeny pomocí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Vrátí okamžitě, pokud je úloha je dokončeno. Jakékoli výjimky vyvolané úloha bude vyvolané <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda, i když <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda byla volána po dokončení úlohy.  
  
## <a name="composing-tasks"></a>Skládání úlohy  
 <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> tříd poskytuje několik metod, které vám mohou pomoci vytvořit více úloh k implementaci běžných vzorů a lepší využití asynchronní jazykové funkce, které jsou k dispozici v jazyce C#, [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]a F #. Tato část popisuje <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, a <xref:System.Threading.Tasks.Task.FromResult%2A> metody.  
  
### <a name="taskwhenall"></a>Task.WhenAll  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Metoda asynchronně čeká více <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekty, které chcete dokončit. Poskytuje přetížené verze, které umožňují čekání na nerovnoměrné sady úloh. Například můžete počkat několik <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty k dokončení z volání jednu metodu.  
  
### <a name="taskwhenany"></a>Task.WhenAny  
 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Metoda asynchronně čeká na jednu více <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekty, které chcete dokončit. Stejně jako na <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metoda, tato metoda poskytuje přetížené verze, které vám umožní počkejte neuniformní sady úlohy. <xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda je užitečná zejména v následujících scénářích.  
  
-   Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda vyberte operaci, nejprve dokončí a poté zrušte zbývajících operací.  
  
-   Prokládané operace. Můžete spustit více operací, které musíte dokončit všechny a použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda zpracovat výsledky, protože dokončení jednotlivých operací. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.  
  
-   Omezené operace. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu pro předchozí scénář rozšířit tak, že omezí počet souběžných operací.  
  
-   Operace, jejichž platnost vypršela. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda můžete vybrat, jestli jeden nebo více úloh a úlohu, která se dokončí po určitý čas, jako je například úlohu, která je vrácena <xref:System.Threading.Tasks.Task.Delay%2A> metoda. <xref:System.Threading.Tasks.Task.Delay%2A> Metoda je popsaná v následující části.  
  
### <a name="taskdelay"></a>Task.Delay  
 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda vytváří <xref:System.Threading.Tasks.Task> objekt, který končí po zadanou dobu. Tuto metodu můžete použít k vytvoření cyklů, které občas provádějí dotazování na data, zavedení limitů, zpracování vstupu uživatele na předem stanovenou dobu zpoždění a tak dále.  
  
### <a name="tasktfromresult"></a>Task(T).FromResult  
 Pomocí <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metodu, můžete vytvořit <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje předvypočítaných výsledek. Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek této <xref:System.Threading.Tasks.Task%601> objektu již je počítaný. Pro příklad, který používá <xref:System.Threading.Tasks.Task.FromResult%2A> načíst výsledky stahování asynchronní operace, které jsou uložené v mezipaměti, najdete v části [postupy: vytvoření úlohy Pre-Computed](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).  
  
## <a name="handling-exceptions-in-tasks"></a>Zpracování výjimek v úlohách  
 Pokud úloha vyvolá jednu nebo více výjimek, výjimky jsou uzavřen do <xref:System.AggregateException> výjimka. Že výjimka rozšířena zpět na vlákno, které spojí s úkolu, který je obvykle vláken, která čeká na dokončení úlohy nebo podproces, který přistupuje <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost. Toto chování slouží k vynucení, aby při všech neošetřených výjimkách ve výchozím nastavení zásady rozhraní .NET Framework ukončily proces. Volání kódu můžete zpracování výjimky pomocí některé z těchto v `try` / `catch` bloku:  
  
-   <xref:System.Threading.Tasks.Task.Wait%2A> – Metoda  
  
-   <xref:System.Threading.Tasks.Task.WaitAll%2A> – Metoda  
  
-   <xref:System.Threading.Tasks.Task.WaitAny%2A> – Metoda  
  
-   <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnost  
  
 Spojovací vlákno může také zpracování výjimek přímým přístupem <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost před úlohu uvolňování paměti. Přístupem k této vlastnosti nebude nezpracovaná výjimka spouštět chování šíření výjimky, které ukončí proces, když je objekt finalizován.  
  
 Další informace o výjimkách a úlohách najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="canceling-tasks"></a>Zrušení úloh  
 `Task` Třída podporuje spolupráci zrušení a jsou plně integrované s <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> třídy, které byly představeny v rozhraní .NET Framework 4. Mnoho z konstruktorů v <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> proveďte třídy <xref:System.Threading.CancellationToken> objektu jako vstupní parametr. Řadu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> a <xref:System.Threading.Tasks.Task.Run%2A> přetížení také zahrnovat <xref:System.Threading.CancellationToken> parametr.  
  
 Můžete vytvořit token a vydat žádost o zrušení některých později pomocí <xref:System.Threading.CancellationTokenSource> třídy. Předejte token, který má <xref:System.Threading.Tasks.Task> jako argument a také odkaz na stejný token v uživatelském delegátovi, který provádí reakci na žádost o zrušení.  
  
 Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
## <a name="the-taskfactory-class"></a>Třída TaskFactory  
 <xref:System.Threading.Tasks.TaskFactory> Třída poskytuje statické metody, které zapouzdřují některé obecné vzory pro vytváření a spouštění úloh a úloh pokračování.  
  
-   Nejběžnější vzor <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, která vytvoří a spustí úlohu v jednom příkazu.  
  
-   Při vytváření úloh pokračování z více předchůdců, použijte <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metoda nebo <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metoda nebo jejich ekvivalenty v <xref:System.Threading.Tasks.Task%601> třídy. Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování pomocí](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
-   K zapouzdření asynchronní programovací Model `BeginX` a `EndX` metody v <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> instance, použijte <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Další informace najdete v tématu [TPL a tradiční rozhraní .NET Framework asynchronní programování](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Výchozí <xref:System.Threading.Tasks.TaskFactory> můžou mít přístup pomocí statické vlastnosti na <xref:System.Threading.Tasks.Task> třídy nebo <xref:System.Threading.Tasks.Task%601> třídy. Můžete také vytvořit instanci <xref:System.Threading.Tasks.TaskFactory> přímo a určit různé možnosti, které zahrnují <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> možnost, <xref:System.Threading.Tasks.TaskContinuationOptions> možnost, nebo <xref:System.Threading.Tasks.TaskScheduler>. Jakékoliv možnosti jsou zadány při vytváření úloh se použijí na všechny úlohy, které vytvoří, pokud <xref:System.Threading.Tasks.Task> je vytvořená pomocí <xref:System.Threading.Tasks.TaskCreationOptions> výčtu, ve kterém případ úkolu možnosti přepsání u objektu pro vytváření úloh.  
  
## <a name="tasks-without-delegates"></a>Úlohy bez delegátů  
 V některých případech můžete chtít použít <xref:System.Threading.Tasks.Task> k zapouzdření některé asynchronní operace, které se provádí pomocí externí komponenta namísto uživatelského delegáta. Pokud operace je založená na vzoru Begin/End Model asynchronního programování, můžete použít <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Pokud není tento případ, můžete použít <xref:System.Threading.Tasks.TaskCompletionSource%601> objekt, který chcete zalomení operaci v úloze a získat tak některé z výhod <xref:System.Threading.Tasks.Task> programovatelnosti, například podporu pro šíření výjimek a pokračování. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="custom-schedulers"></a>Vlastní plánovače  
 Většina vývojářů aplikace nebo knihovna nezáleží na kterém procesoru úloha spuštěna, jak synchronizuje svou práci s ostatními úkoly nebo jak je naplánována na <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Vyžadují pouze to, aby byly tyto úkony v hostitelském počítači prováděny tak efektivně, jak je to možné. Pokud požadujete jemněji odstupňovanou kontrolu nad podrobnostmi plánování, Task Parallel Library umožňuje konfigurovat některá nastavení výchozího plánovače úloh a dokonce umožňuje zadat vlastní plánovač. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskScheduler>.  
  
## <a name="related-data-structures"></a>Související datové struktury  
 TPL má několik nových veřejných typů, které jsou použitelné jak v situacích paralelního, tak i sekvenčního vykonávání. Patří mezi ně několik třídy bezpečné pro přístup z více vláken, rychlá a škálovatelná kolekce v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a synchronizace několik nových typů například <xref:System.Threading.Semaphore?displayProperty=nameWithType> a <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, které jsou efektivnější než jejich předchůdci pro konkrétní druhy zátěží. Další nové typy v rozhraní .NET Framework 4, například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.SpinLock?displayProperty=nameWithType>, poskytovat funkce, které nebyly k dispozici ve starších verzích. Další informace najdete v tématu [datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).  
  
## <a name="custom-task-types"></a>Typy úloh  
 Doporučujeme vám, že není dědit z <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Místo toho doporučujeme používat <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost pro přidružení dalších dat nebo stavu s <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objektu. Můžete taky rozšiřující metody pro rozšíření funkcí <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> třídy. Další informace o metodách rozšíření najdete v tématu [rozšiřující metody](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md) a [rozšiřující metody](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Pokud musí dědit z <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, nemůžete použít <xref:System.Threading.Tasks.Task.Run%2A>, <xref:System.Threading.Tasks.Task.Run%2A>, nebo <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, nebo <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> třídy pro vytvoření instance vlastní úlohu zadat, protože tyto mechanismy vytvořit pouze <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty. Kromě toho nelze použít na úkolů pokračování mechanismy, které jsou poskytovány <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, a <xref:System.Threading.Tasks.TaskFactory%601> vytvořit instance typu vaše vlastní úlohu, protože tyto mechanismy také vytvořit pouze <xref:System.Threading.Tasks.Task> a  <xref:System.Threading.Tasks.Task%601> objekty.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-|-|  
|[Řetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Popisuje, jak fungují pokračování.|  
|[Připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Popisuje rozdíl mezi připojenými a odpojenými podřízenými úlohami.|  
|[Zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md)|Popisuje podporu zrušení, který je součástí <xref:System.Threading.Tasks.Task> objektu.|  
|[Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Popisuje způsob zpracování výjimek v souběžných vláknech.|  
|[Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|  
|[Postupy: Vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Popisuje, jak z úloh vracet hodnoty.|  
|[Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Popisuje, jak zrušit úlohy.|  
|[Postupy: Vytváření předvypočítaných úloh](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Popisuje postup použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metoda načíst výsledky stahování asynchronní operace, které jsou uložené v mezipaměti.|  
|[Postupy: Procházení binárního stromu s paralelními úlohami](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Popisuje, jak použít úlohy k procházení binárního stromu.|  
|[Postupy: Rozbalení vnořené úlohy](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Ukazuje, jak používat <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metoda rozšíření.|  
|[Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Parallel.For%2A> a <xref:System.Threading.Tasks.Parallel.ForEach%2A> pro vytvoření paralelní smyčky nad daty.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Uzel nejvyšší úrovně pro paralelní programování rozhraní .NET Framework.|  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [Ukázky pro paralelní programování s rozhraním .NET Framework](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
