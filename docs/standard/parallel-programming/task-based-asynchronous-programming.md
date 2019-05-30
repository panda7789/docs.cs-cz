---
title: Úkolově orientovanou asynchronní programování – .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad13a5771adbfbd389feeccd3e8c833c4c2f778a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300639"
---
# <a name="task-based-asynchronous-programming"></a>Asynchronní programování založené na úlohách

Task Parallel Library (TPL) je založena na konceptu *úloh*, což představuje asynchronní operaci. V některých ohledech úkol podobá vláknu nebo <xref:System.Threading.ThreadPool> pracovní položky, ale na vyšší úrovni abstrakce. Termín *paralelismus úloh* odkazuje na jeden nebo více nezávislých úloh, které jsou spuštěny souběžně. Úlohy poskytují dvě hlavní výhody:

- Větší škálovatelnost a efektivnější využívání systémových prostředků.

     Na pozadí jsou úlohy řazeny do <xref:System.Threading.ThreadPool>, který byl vylepšen o algoritmy, které naleznou a upravují počet vláken, a vyrovnávají zatížení maximalizuje propustnost. Díky tomu jsou úlohy relativně lehké a lze jich vytvořit mnoho, takže lze dosáhnout jemně odstupňovaného paralelismu.

- Více programového ovládání než je k dispozici s vláknem nebo pracovní položkou.

     Úlohy a architektura kolem nich vytvořená poskytují bohatou sadu rozhraní (API), která podporují čekání, zrušení, pokračování, robustní zpracování výjimek, podrobný stav, vlastní plánování a další.

Pro oba z těchto důvodů je v rozhraní .NET Framework TPL upřednostňovaným rozhraním API pro psaní vícevláknového, asynchronního a paralelního kódu.

## <a name="creating-and-running-tasks-implicitly"></a>Vytváření a spouštění úloh implicitně

<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> Metoda poskytuje pohodlný způsob, jak souběžně spustit libovolný počet různých příkazů. Stačí pouze předat <xref:System.Action> delegáta pro každou položku práce. Nejsnadnější způsob, jak vytvořit tyto delegáty, je použití lambda výrazů. Lambda výraz může buďto volat pojmenovanou metodu, nebo poskytnout vložený kód. Následující příklad ukazuje základní <xref:System.Threading.Tasks.Parallel.Invoke%2A> volání, které vytvoří a spustí dvě úlohy, které běží souběžně. První úloha je reprezentována výrazem lambda, který volá metodu s názvem `DoSomeWork`, a druhý úkol představuje výraz lambda, který volá metodu s názvem `DoSomeOtherWork`.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Počet <xref:System.Threading.Tasks.Task> instancí, které jsou vytvořeny na pozadí pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> není nutně roven počtu zadaných delegátů. Knihovna TPL může využít různé optimalizace, zejména s velkým počtem delegátů.

Další informace najdete v tématu [jak: Použití algoritmu Parallel.Invoke k vykonávání paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Pro větší kontrolu nad spouštěním úloh nebo pro navrácení hodnoty z úlohy je nutné pracovat s <xref:System.Threading.Tasks.Task> objekty více explicitně.

## <a name="creating-and-running-tasks-explicitly"></a>Vytváření a spouštění úloh explicitně

Úloha, která nevrací hodnotu je reprezentována <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy. Úloha, která navrací hodnotu je reprezentována <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> třída, která dědí z <xref:System.Threading.Tasks.Task>. Objekt úlohy zpracovává podrobnosti infrastruktury a poskytuje metody a vlastnosti, které jsou přístupné z volajícího vlákna po celou dobu trvání úlohy. Například můžete získat přístup <xref:System.Threading.Tasks.Task.Status%2A> vlastnosti úlohy v každém okamžiku k určení, zda byla spuštěna, dokončena, byla zrušena nebo byla vyvolána výjimka. Stav je reprezentován <xref:System.Threading.Tasks.TaskStatus> výčtu.

Když je vytvořena úloha, je jí zadán uživatelský delegát, jenž provádí zapouzdření kódu, který úloha provede. Tento delegát může být vyjádřen jako pojmenovaný delegát, anonymní metoda nebo lambda výraz. Lambda výrazy mohou obsahovat volání pojmenované metody, jak ukazuje následující příklad. Všimněte si, že příklad obsahuje volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodou, jak zajistit, že dokončení úkolu před ukončením aplikace v režimu konzoly.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Můžete také použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody pro vytvoření a spuštění úlohy v rámci jedné operace. Chcete-li spravovat úlohu, <xref:System.Threading.Tasks.Task.Run%2A> metody používají výchozí Plánovač úloh bez ohledu na to, jaké úlohy scheduleru souvisí s aktuálním vláknem. <xref:System.Threading.Tasks.Task.Run%2A> Metody jsou preferovaným způsobem, jak vytvářet a spouštět úlohy, když není potřeba větší kontrolu nad vytváření a plánování úloh.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Můžete také použít <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodu pro vytvoření a spuštění úlohy v rámci jedné operace. Tuto metodu použijte, když vytváření a plánování nemusí být odděleno a vyžadujete další možnosti vytvoření úkolu nebo použití určitého plánovače nebo pokud potřebujete předat další stav do úkolu, který můžete načíst pomocí jeho <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastnost, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> vystavují statickou <xref:System.Threading.Tasks.Task.Factory%2A> vlastnost, která vrátí výchozí instanci <xref:System.Threading.Tasks.TaskFactory>, takže můžete volat metodu jako `Task.Factory.StartNew()`. Také v následujícím příkladu jelikož úlohy jsou typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, každá má veřejnou <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost, která obsahuje výsledek výpočtu. Úlohy běží asynchronně a mohou být dokončeny v libovolném pořadí. Pokud <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost je přístupná před dokončením výpočtu, vlastnost blokuje volající vlákno, dokud hodnota není k dispozici.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Další informace najdete v tématu [jak: Vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Při použití lambda výrazu k vytvoření delegáta máte přístup ke všem proměnným, které jsou v daném okamžiku viditelné ve zdrojovém kódu. V některých případech, zejména v rámci smyčky, však lambda nezachytí proměnnou podle očekávání. Pouze zachycuje konečnou hodnotu, nikoli mutaci hodnoty po každé iteraci. Následující příklad ukazuje tento problém. Předává smyčky pro lambda výraz, který instancuje čítač `CustomData` objektu a používá čítače smyčky jako identifikátoru objektu. Jak výstup z příkladu ukazuje, každý `CustomData` objektu má stejný identifikátor.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

K hodnotě v každé iteraci můžete přistupovat zadáním objektu stavu úlohy pomocí jeho konstruktoru. Následující příklad upravuje předchozí příklad pomocí čítače smyčky při vytváření `CustomData` objektu, který je poté předán výrazu lambda.  Jak výstup z příkladu ukazuje, každý `CustomData` objekt obsahuje nyní jedinečný identifikátor na základě hodnoty čítače cyklů v době byla vytvořena instance objektu.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Tento stav je předán jako argument delegátovi úlohy a je možné přistupovat z objektu úlohy pomocí <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastnost.  Následující příklad je podobný předchozímu příkladu. Používá <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost pro zobrazení informací o `CustomData` objekty předán lambda výrazu.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>ID úlohy

Každá úloha obdrží celočíselný identifikátor ID, který ji jednoznačně identifikuje v doméně aplikace a je přístupný pomocí <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> vlastnost. ID je užitečné při prohlížení informace o úkolu v ladicím programu sady Visual Studio **paralelní zásobníky** a **úlohy** systému windows. ID využívá líné vytváření, což znamená, že není vytvořeno, dokud se o něj nepožádá, proto může mít úloha při každém spuštění programu jiné ID. Další informace o tom, jak zobrazení ID úlohy v ladicím programu naleznete v tématu [Using the Tasks Window](/visualstudio/debugger/using-the-tasks-window) a [použití okna paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Možnosti vytvoření úlohy

Většina rozhraní API, která vytváří úlohy, poskytuje přetížení <xref:System.Threading.Tasks.TaskCreationOptions> parametru. Zadáním jedné z těchto možností lze dát pokyn plánovači úloh, jak naplánovat úlohy ve fondu vláken. V následující tabulce jsou uvedeny různé možnosti pro vytváření úloh.

|<xref:System.Threading.Tasks.TaskCreationOptions> Hodnota parametru|Popis|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Výchozí hodnota, pokud není zadána jiná. Plánovač používá k plánování úlohy své výchozí heuristické metody.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Určuje, že úlohy by měly být naplánovány tak, aby se úlohy vytvořené dříve pravděpodobně prováděly dříve a později vytvořené úlohy aby se s větší pravděpodobností prováděly později.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Určuje, že úloha představuje dlouhotrvající operaci.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Určuje, že úloha by měla být vytvořena jako připojená podřízená úloha aktuální úlohy, pokud existuje. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Určuje, že pokud vnitřní úloha Určuje `AttachedToParent` možnost, že úloha se stává připojenou podřízenou úlohu.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Určuje, že Plánovač úloh vytvořených voláním metody, jako je <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> v rámci určitého úkolu, je výchozím plánovačem namísto plánovače, na kterém je tato úloha spuštěna.|

Možnosti lze kombinovat pomocí logické bitové **nebo** operace. Následující příklad zobrazuje úlohu, který má <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> možnost.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Úkoly, vlákna a jazykovou verzi

Každé vlákno má přidružená jazyková verze a jazykové verze uživatelského rozhraní, který je definovaný <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti, v uvedeném pořadí. Jazyková verze vlákna se používá v těchto operací formátování, analýza, řazení a porovnání řetězců. Jazyková verze vlákna uživatelského rozhraní se používá ve vyhledávání prostředků. Obvykle Pokud nezadáte výchozí jazykovou verzi pro všechna vlákna v doméně aplikace s použitím <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> jazyková verze systému je definován vlastností, výchozí jazykovou verzi a jazykové verze uživatelského rozhraní vlákna. Pokud explicitně nastavit jazykovou verzi vlákna a spustit nové vlákno, nové vlákno nedědí jazykovou verzi, volajícího vlákna; Místo toho jeho jazyková verze je výchozí jazykovou verzi systému. Pro tento postup se proto zavázala založené na úlohách programovací model pro aplikace, které cílové verze rozhraní .NET Framework před rozhraní .NET Framework 4.6.

> [!IMPORTANT]
> Všimněte si, že volající vlákno jazykovou verzi jako součást úkolu kontextu se vztahuje na aplikace, která *cílové* rozhraní .NET Framework 4.6, ne aplikace, která *běžet pod* rozhraní .NET Framework 4.6. Při vytváření projektu v sadě Visual Studio tak, že vyberete danou verzi z rozevíracího seznamu v horní části můžete cílit na konkrétní verzi rozhraní .NET Framework **nový projekt** dialogové okno, nebo mimo sadu Visual Studio můžete použít <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut. Pro aplikace, že cílová verze rozhraní .NET Framework před rozhraní .NET Framework 4.6 nebo, který sdělení nebudete cílit na konkrétní verzi rozhraní .NET Framework, jazykovou verzi úkolu i nadále určuje jazykovou verzi vlákna, na kterém běží.

Počínaje aplikací využívajících rozhraní .NET Framework 4.6, jazyková verze volajícího vlákna zdědí každý úkol, i v případě, že se úloha spouští asynchronně ve vláknu fondu vláken.

Následující příklad uvádí jednoduchý obrázek. Používá <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut cílit na rozhraní .NET Framework 4.6 a změní aktuální jazykovou verzi aplikace na buď francouzština (Francie) nebo pokud francouzština (Francie) už je aktuální jazyková verze Angličtina (Spojené státy). Potom se vyvolá delegáta s názvem `formatDelegate` , která vrací některá čísla naformátovaná jako hodnoty měny v nové jazykové verze. Všimněte si, zda delegáta jako úlohu synchronně nebo asynchronně, vrátí očekávaný výsledek protože jazyková verze volajícího vlákna je zděděno asynchronní úloha.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Pokud používáte Visual Studio, můžete vynechat <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut a místo toho vyberte rozhraní .NET Framework 4.6 jako cíl, při vytváření projektu v **nový projekt** dialogového okna.

Pro výstup, který odráží chování aplikací cílová verze rozhraní .NET Framework před rozhraní .NET Framework 4.6, odeberte <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut ze zdrojového kódu. Výstup bude odrážet konvencí formátování je výchozí jazyková verze systému, ne jazyková verze volajícího vlákna.

Další informace o asynchronních úloh a jazykovou verzi, naleznete v části "Jazyková verze a asynchronních operací podle úloh" v <xref:System.Globalization.CultureInfo> tématu.

## <a name="creating-task-continuations"></a>Vytváření pokračování úlohy

<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> metody umožňují zadat úlohu, kterou chcete spustit po *předchozí úloha* dokončí. Delegátovi pokračujícího úkol je předán odkaz na předchozí úlohu tak, aby mohl zkontrolovat stav předchozí úlohy a načtením hodnoty <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> mohl použít výstup předchůdce jako vstup pro pokračování.

V následujícím příkladu `getData` úloha je spuštěna voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> metody. `processData` Úloha je spuštěna automaticky při `getData` dokončí, a `displayData` se spustí po `processData` dokončí. `getData` Vytvoří celočíselné pole, které je přístupné `processData` úloh prostřednictvím `getData` úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost. `processData` Úkolů zpracuje toto pole a vrátí výsledek, jehož typ je odvozen z návratového typu výrazu lambda, který je předán <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> metody. `displayData` Provede automaticky při `processData` dokončí a <xref:System.Tuple%603> objekt vrácený `processData` výraz lambda je přístupný `displayData` úloh prostřednictvím `processData` úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Vlastnost. `displayData` Přebírá výsledek úlohy `processData` úloh a vytváří výsledek, jehož typ je odvozen podobným způsobem a který je k dispozici v programu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Protože <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> je metoda instance, můžete vytvořit řetězové volání metody společně namísto vytvoření instance <xref:System.Threading.Tasks.Task%601> objekt u každé předchozí úlohy. Následující příklad je funkčně stejný jako předchozí příklad, s tím rozdílem, že zřetězí společně volání <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Všimněte si, <xref:System.Threading.Tasks.Task%601> vrácený řetězcem volání metody je konečnou pokračující úlohou.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody umožňují pokračovat z více úloh.

Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Vytváření odpojených podřízených úloh

Když uživatelský kód, který běží v rámci úlohy vytvoří novou úlohu a neurčí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost, je nová úloha není synchronizována s nadřízenou úlohou žádným zvláštním způsobem. Tento typ nesynchronizovaného úkolu se nazývá *odpojená vnořená úloha* nebo *odpojenou podřízenou úlohu*. Následující příklad zobrazuje úlohu, která vytváří jednu odpojenou podřízenou úlohu.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Nadřazená úloha nečeká na dokončení odpojené podřízené úlohy.

## <a name="creating-child-tasks"></a>Vytváření podřízených úloh

Když uživatelský kód, který běží v rámci úlohy, vytvoří úlohu s <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost Nová úloha známá jako *připojená podřízená úloha* nadřazeného úkolu. Můžete použít <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost strukturovaného paralelismu úloh, protože nadřazená úloha implicitně čeká na dokončení všech připojených podřízených úloh. Následující příklad zobrazuje nadřazenou úlohu, která vytvoří deset připojených podřízených úloh. Všimněte si, že ačkoli v příkladu volána <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda čekat na dokončení nadřazených úloh nemusí explicitně čekat na dokončení připojených podřízených úloh.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Nadřazené úlohy mohou používat <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost zabránit připojení k nadřazené úloze jiných úloh. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Čekání na dokončení úloh

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy poskytují několik přetížení <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, které umožňují čekat na dokončení úlohy. Kromě toho přetížení statických <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody umožňují čekat některých nebo všech úloh na dokončení v poli.

Obvykle se na úlohu čeká z některého z těchto důvodů:

- Hlavní vlákno závisí na konečném výsledku vypočítaném úlohou.

- Je potřeba zpracovat výjimky, které mohou být vyvolány z úlohy.

- Aplikace se může ukončit předtím, než se dokončí všechny úlohy. Například konzolové aplikace budou ukončeny co nejdříve veškerého synchronního kódu v `Main` po provedení (vstupní bod aplikace).

Následující příklad zobrazuje základní vzor, který nezahrnuje zpracování výjimek.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Příklad zobrazující zpracování výjimek, naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Některá přetížení umožňují určit časový limit a jiná přijímají další <xref:System.Threading.CancellationToken> jako vstupní parametr, aby mohlo být samotné čekání zrušeno buď programově, nebo jako odpověď na uživatelský vstup.

Při čekání na úlohu se implicitně čeká všechny podřízené dané úlohy, které byly vytvořeny pomocí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> Vrátí hodnotu okamžitě, pokud úloha již byla dokončena. Jakékoli výjimky způsobené úlohou budou vyvolány metodou <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> , i když <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda byla volána po dokončení úlohy.

## <a name="composing-tasks"></a>Skládání úloh

<xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> třídy poskytují několik metod, které vám pomohou vytvořit více úkolů k implementaci běžných vzorů a pro lepší využití asynchronních jazykových funkcí, které jsou poskytovány C#, Visual Basic a F#. Tato část popisuje <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, a <xref:System.Threading.Tasks.Task.FromResult%2A> metody.

### <a name="taskwhenall"></a>Task.WhenAll

<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Metoda asynchronně čeká na více <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekty na dokončení. Poskytuje přetížené verze, které umožňují čekání na nerovnoměrné sady úloh. Například může čekat pro více <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objektů k dokončení z jedné metody volání.

### <a name="taskwhenany"></a>Task.WhenAny

<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Metoda asynchronně čeká na jednu z více <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekty na dokončení. Stejně jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodu, tato metoda poskytuje přetížené verze, které umožňují čekat na nerovnoměrné sady úloh. <xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda je užitečná v následujících scénářích.

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu pro výběr operace, která skončí jako první a pak zrušení zbývajících operací.

- Prokládané operace. Můžete spustit více operací, které musíte dokončit všechny a použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metody k rozšíření předchozího scénáře tím, že omezíte počet souběžných operací.

- Operace, jejichž platnost vypršela. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> pro výběr jedné nebo více úloh a úlohy, která skončí za určitou dobu, například úkol, který je vrácený <xref:System.Threading.Tasks.Task.Delay%2A> metody. <xref:System.Threading.Tasks.Task.Delay%2A> Metoda je popsaná v následující části.

### <a name="taskdelay"></a>Task.Delay

<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.Task> , který je dokončen po určeném čase. Tuto metodu můžete použít k vytvoření cyklů, které občas provádějí dotazování na data, zavedení limitů, zpracování vstupu uživatele na předem stanovenou dobu zpoždění a tak dále.

### <a name="tasktfromresult"></a>Task(T).FromResult

S použitím <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metodu, můžete vytvořit <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje předem vypočítaný výsledek. Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán. Příklad, který používá <xref:System.Threading.Tasks.Task.FromResult%2A> k načtení výsledků asynchronní operací stažení, které jsou uloženy v mezipaměti, naleznete v tématu [jak: Vytváření Předvypočítaných úloh](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Zpracování výjimek v úlohách

Pokud úloha vyvolá jednu nebo více výjimek, výjimky jsou obaleny do <xref:System.AggregateException> výjimky. Tato výjimka se šíří zpět k vláknu spojenému s úlohou, které je obvykle vláknem čekajícím na dokončení úloh nebo vláknem, které přistupuje k <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost. Toto chování slouží k vynucení, aby při všech neošetřených výjimkách ve výchozím nastavení zásady rozhraní .NET Framework ukončily proces. Volající kód může zpracovávat výjimky pomocí některého z následujících postupů v `try` / `catch` blok:

- <xref:System.Threading.Tasks.Task.Wait%2A> – Metoda

- <xref:System.Threading.Tasks.Task.WaitAll%2A> – Metoda

- <xref:System.Threading.Tasks.Task.WaitAny%2A> – Metoda

- <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnost

Spojovací vlákno může také výjimky zpracovávat přístupem k <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost předtím, než je úkol uklizena modulem. Přístupem k této vlastnosti nebude nezpracovaná výjimka spouštět chování šíření výjimky, které ukončí proces, když je objekt finalizován.

Další informace o výjimkách a úlohách naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Zrušení úloh

<xref:System.Threading.Tasks.Task> Třídy podporuje kooperativní zrušení a je plně integrováno <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> třídy, které byly zavedeny v rozhraní .NET Framework 4. Mnoho konstruktorů ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídě <xref:System.Threading.CancellationToken> jako vstupní parametr objekt. Mnoho <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> a <xref:System.Threading.Tasks.Task.Run%2A> také zahrnovat přetížení <xref:System.Threading.CancellationToken> parametru.

Můžete vytvořit token a vyslat žádost zrušení později, s použitím <xref:System.Threading.CancellationTokenSource> třídy. Předat token, který má <xref:System.Threading.Tasks.Task> jako argument a také odkazovat stejný token v uživatelském delegátu, který provádí reakci na žádost o zrušení.

Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [jak: Zrušení úlohy a jejích potomků](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Třída TaskFactory

<xref:System.Threading.Tasks.TaskFactory> Třída poskytuje statické metody, které provádí zapouzdření některých běžný schémat pro vytváření a spouštění úloh a pokračujících úloh.

- Nejběžnější vzor <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, který vytvoří a spustí úlohu v jednom příkazu.

- Při vytváření úlohy pokračování z více předchůdců použijte <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metoda nebo <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> nebo jejich ekvivalenty v <xref:System.Threading.Tasks.Task%601> třídy. Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- K zapouzdření modelu asynchronního programování `BeginX` a `EndX` metody v <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> použijte <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Další informace najdete v tématu [TPL a tradiční rozhraní .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Výchozí hodnota <xref:System.Threading.Tasks.TaskFactory> je přístupná jako statická vlastnost ve <xref:System.Threading.Tasks.Task> třídy nebo <xref:System.Threading.Tasks.Task%601> třídy. Můžete také vytvořit instanci <xref:System.Threading.Tasks.TaskFactory> přímo a určit různé možnosti, které zahrnují <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> možnost, <xref:System.Threading.Tasks.TaskContinuationOptions> možnost, nebo <xref:System.Threading.Tasks.TaskScheduler>. Jakékoli možnosti jsou zadány při vytváření továrny úloh se použijí na všechny úlohy, které vytvoří, pokud <xref:System.Threading.Tasks.Task> je vytvořená pomocí <xref:System.Threading.Tasks.TaskCreationOptions> výčtu, ve kterém továrna úkolu možnosti jsou továrny úloh.

## <a name="tasks-without-delegates"></a>Úlohy bez delegátů

V některých případech můžete chtít použít <xref:System.Threading.Tasks.Task> k zapouzdření některé asynchronní operace, kterou provádí externí komponenta namísto uživatelského delegáta. Pokud je operace založena na vzoru Begin/End modelu asynchronního programování, můžete použít <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Pokud to není tento případ, můžete použít <xref:System.Threading.Tasks.TaskCompletionSource%601> objekt obalí operaci do úlohy a tím získáte některé výhody <xref:System.Threading.Tasks.Task> programování, například podporu šíření výjimek a pokračování. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Vlastní plánovače

Většině vývojářů aplikací a knihoven nezáleží na kterém procesoru je úloha spuštěna, jak synchronizuje svou práci s ostatními úlohami nebo jak je naplánována na <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Vyžadují pouze to, aby byly tyto úkony v hostitelském počítači prováděny tak efektivně, jak je to možné. Pokud požadujete jemněji odstupňovanou kontrolu nad podrobnostmi plánování, Task Parallel Library umožňuje konfigurovat některá nastavení výchozího plánovače úloh a dokonce umožňuje zadat vlastní plánovač. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Související datové struktury

TPL má několik nových veřejných typů, které jsou použitelné jak v situacích paralelního, tak i sekvenčního vykonávání. Zahrnují několik bezpečným pro vlákno, rychlých a škálovatelných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a několik nových typů synchronizace, například <xref:System.Threading.Semaphore?displayProperty=nameWithType> a <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, které jsou efektivnější než jejich předchůdci pro konkrétní druhy úloh. Další nové typy v rozhraní .NET Framework 4, například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.SpinLock?displayProperty=nameWithType>, poskytují funkce, které v dřívějších verzích nebyly k dispozici. Další informace najdete v tématu [datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Vlastní typy úloh

Doporučujeme vám, že není odvozena od <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Namísto toho doporučujeme použít <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost pro přidružení dalších dat nebo stavu k <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objektu. Můžete také použít rozšiřující metody k rozšíření funkčnosti <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> třídy. Další informace o metodách rozšíření naleznete v tématu [rozšiřující metody](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md) a [rozšiřující metody](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Pokud musí dědit z <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, nemůžete použít <xref:System.Threading.Tasks.Task.Run%2A>, <xref:System.Threading.Tasks.Task.Run%2A>, nebo <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, nebo <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> typ třídy pro vytvoření instancí vlastního úkolu, protože tyto mechanismy vytvářejí pouze <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty. Kromě toho nelze použít mechanismy pokračování úloh, které jsou poskytovány <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, a <xref:System.Threading.Tasks.TaskFactory%601> k vytvoření instance vlastního typu úlohy, protože tyto mechanismy také vytvářejí pouze <xref:System.Threading.Tasks.Task> a  <xref:System.Threading.Tasks.Task%601> objekty.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-|-|
|[Řetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Popisuje, jak fungují pokračování.|
|[Připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Popisuje rozdíl mezi připojenými a odpojenými podřízenými úlohami.|
|[Zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md)|Popisuje podporu zrušení, která je integrovaná <xref:System.Threading.Tasks.Task> objektu.|
|[Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Popisuje způsob zpracování výjimek v souběžných vláknech.|
|[Postupy: Použití algoritmu Parallel.Invoke k vykonávání paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Postupy: Vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Popisuje, jak z úloh vracet hodnoty.|
|[Postupy: Zrušení úlohy a jejích potomků](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Popisuje, jak zrušit úlohy.|
|[Postupy: Vytváření Předvypočítaných úloh](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody k načtení výsledků asynchronní operací stažení, které jsou uloženy v mezipaměti.|
|[Postupy: Procházení binárního stromu s paralelními úlohami](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Popisuje, jak použít úlohy k procházení binárního stromu.|
|[Postupy: Rozbalení vnořené úlohy](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Popisuje způsob použití <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> – metoda rozšíření.|
|[Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Parallel.For%2A> a <xref:System.Threading.Tasks.Parallel.ForEach%2A> pro vytvoření paralelních cyklů nad daty.|
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Uzel nejvyšší úrovně pro paralelní programování rozhraní .NET Framework.|

## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Ukázky pro paralelní programování s rozhraním .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
