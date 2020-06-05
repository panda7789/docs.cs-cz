---
title: Asynchronní programování založené na úlohách – .NET
description: V tomto článku se dozvíte o asynchronním programování založeném na úlohách prostřednictvím TAsk Parallel Library (TPL) v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: f7cb42c8982cb6a704b39730a4f7aa0ce781d506
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446376"
---
# <a name="task-based-asynchronous-programming"></a>Asynchronní programování založené na úlohách

Task Parallel Library (TPL) je založen na konceptu *úlohy*, která představuje asynchronní operaci. V některých způsobech se úkol podobá vláknu nebo <xref:System.Threading.ThreadPool> pracovní položce, ale na vyšší úrovni abstrakce. Pojem *úkol paralelismus* odkazuje na jednu nebo více nezávislých úloh, které jsou spuštěny souběžně. Úlohy poskytují dvě hlavní výhody:

- Větší škálovatelnost a efektivnější využívání systémových prostředků.

     Na pozadí jsou úlohy zařazené do fronty, která se rozšířila <xref:System.Threading.ThreadPool> o algoritmy, které určují a upravují počet vláken, která poskytují vyrovnávání zatížení pro maximalizaci propustnosti. Díky tomu jsou úlohy relativně lehké a lze jich vytvořit mnoho, takže lze dosáhnout jemně odstupňovaného paralelismu.

- Více programového ovládání než je k dispozici s vláknem nebo pracovní položkou.

     Úlohy a architektura kolem nich vytvořená poskytují bohatou sadu rozhraní (API), která podporují čekání, zrušení, pokračování, robustní zpracování výjimek, podrobný stav, vlastní plánování a další.

Pro oba z těchto důvodů je v rozhraní .NET Framework TPL upřednostňovaným rozhraním API pro psaní vícevláknového, asynchronního a paralelního kódu.

## <a name="creating-and-running-tasks-implicitly"></a>Implicitní vytváření a spouštění úloh

<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>Metoda poskytuje pohodlný způsob, jak souběžně spustit libovolný počet libovolných příkazů. Stačí předat <xref:System.Action> delegáta pro každou položku práce. Nejsnadnější způsob, jak vytvořit tyto delegáty, je použití lambda výrazů. Lambda výraz může buďto volat pojmenovanou metodu, nebo poskytnout vložený kód. Následující příklad ukazuje základní <xref:System.Threading.Tasks.Parallel.Invoke%2A> volání, které vytvoří a spustí dvě úlohy, které jsou spuštěny souběžně. První úloha je reprezentována výrazem lambda, který volá metodu s názvem `DoSomeWork` a druhá úloha je reprezentována výrazem lambda, který volá metodu s názvem `DoSomeOtherWork` .

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Počet <xref:System.Threading.Tasks.Task> instancí, které jsou vytvořeny na pozadí podle, <xref:System.Threading.Tasks.Parallel.Invoke%2A> není nutně roven počtu poskytnutých delegátů. Knihovna TPL může využít různé optimalizace, zejména s velkým počtem delegátů.

Další informace naleznete v tématu [How to: use Parallel. Invoke pro provádění paralelních operací](how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Chcete-li získat větší kontrolu nad prováděním úloh nebo vrátit hodnotu z úkolu, je nutné pracovat s <xref:System.Threading.Tasks.Task> objekty lépe.

## <a name="creating-and-running-tasks-explicitly"></a>Explicitní vytváření a spouštění úloh

Úloha, která nevrací hodnotu, je reprezentována <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídou. Úloha, která vrací hodnotu, je reprezentována <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> třídou, která dědí z <xref:System.Threading.Tasks.Task> . Objekt úlohy zpracovává podrobnosti infrastruktury a poskytuje metody a vlastnosti, které jsou přístupné z volajícího vlákna po celou dobu trvání úlohy. Můžete například kdykoli přistupovat k <xref:System.Threading.Tasks.Task.Status%2A> Vlastnosti úlohy a zjistit, zda byla spuštěna, dokončena, zrušena, nebo byla vyvolána výjimka. Stav je reprezentován <xref:System.Threading.Tasks.TaskStatus> výčtem.

Když je vytvořena úloha, je jí zadán uživatelský delegát, jenž provádí zapouzdření kódu, který úloha provede. Tento delegát může být vyjádřen jako pojmenovaný delegát, anonymní metoda nebo lambda výraz. Lambda výrazy mohou obsahovat volání pojmenované metody, jak ukazuje následující příklad. Všimněte si, že příklad obsahuje volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, aby bylo zajištěno, že úloha dokončí provádění před ukončením aplikace v režimu konzoly.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Můžete také použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody k vytvoření a spuštění úlohy v jedné operaci. Pro správu úlohy <xref:System.Threading.Tasks.Task.Run%2A> používají metody výchozí Plánovač úloh bez ohledu na to, který Plánovač úloh je přidružený k aktuálnímu vláknu. <xref:System.Threading.Tasks.Task.Run%2A>Metody jsou preferovaným způsobem, jak vytvářet a spouštět úlohy, když není potřeba větší kontrola nad vytvořením a plánováním úkolu.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Tuto metodu můžete také použít <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> k vytvoření a spuštění úlohy v jedné operaci. Tuto metodu použijte, když vytváření a plánování nemusí být odděleno a vyžadujete další možnosti vytvoření úlohy nebo použití konkrétního plánovače, nebo pokud potřebujete předat další stav do úlohy, kterou můžete načíst prostřednictvím její <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastnosti, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task>a <xref:System.Threading.Tasks.Task%601> každá z nich zveřejňuje statickou <xref:System.Threading.Tasks.Task.Factory%2A> vlastnost, která vrátí výchozí instanci <xref:System.Threading.Tasks.TaskFactory> , aby bylo možné volat metodu jako `Task.Factory.StartNew()` . V následujícím příkladu, protože jsou úkoly typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , mají každý z nich veřejnou <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost, která obsahuje výsledek výpočtu. Úlohy běží asynchronně a mohou být dokončeny v libovolném pořadí. <xref:System.Threading.Tasks.Task%601.Result%2A>Je-li vlastnost přístupná před dokončením výpočtu, vlastnost zablokuje volající vlákno, dokud není k dispozici hodnota.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Další informace najdete v tématu [Postupy: vrácení hodnoty z úkolu](how-to-return-a-value-from-a-task.md).

Při použití lambda výrazu k vytvoření delegáta máte přístup ke všem proměnným, které jsou v daném okamžiku viditelné ve zdrojovém kódu. V některých případech, zejména v rámci smyčky, však lambda nezachytí proměnnou podle očekávání. Pouze zachycuje konečnou hodnotu, nikoli mutaci hodnoty po každé iteraci. Následující příklad ukazuje tento problém. Předá počítadlo výrazu lambda, který vytvoří instanci `CustomData` objektu, a použije čítač smyčky jako identifikátoru objektu. Jak výstup z příkladu ukazuje, každý `CustomData` objekt má stejný identifikátor.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

K hodnotě v každé iteraci můžete přistupovat zadáním objektu stavu úlohy pomocí jeho konstruktoru. Následující příklad upravuje předchozí příklad pomocí čítače smyčky při vytváření `CustomData` objektu, který je zase předán výrazu lambda.  Jak výstup z příkladu ukazuje, každý `CustomData` objekt má nyní jedinečný identifikátor na základě hodnoty čítače smyčky v době, kdy byla vytvořena instance objektu.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Tento stav je předán jako argument delegátu úlohy a lze k němu přistupovat z objektu úlohy pomocí <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> Vlastnosti.  Následující příklad je podobný předchozímu příkladu. Používá <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost k zobrazení informací o `CustomData` objektech předaných do výrazu lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>ID úlohy

Každý úkol obdrží celočíselný identifikátor ID, který ji jednoznačně identifikuje v doméně aplikace a je k němu možné přistupovat pomocí <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> Vlastnosti. ID je užitečné pro zobrazení informací o úloze v oknech **paralelní zásobníky** a **úlohy** ladicího programu sady Visual Studio. ID využívá líné vytváření, což znamená, že není vytvořeno, dokud se o něj nepožádá, proto může mít úloha při každém spuštění programu jiné ID. Další informace o tom, jak zobrazit ID úloh v ladicím programu, najdete v tématu [použití okna úlohy](/visualstudio/debugger/using-the-tasks-window) a [použití okna Paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Možnosti vytvoření úlohy

Většina rozhraní API, které vytváří úlohy, poskytuje přetížení, která přijímají <xref:System.Threading.Tasks.TaskCreationOptions> parametr. Zadáním jedné z těchto možností lze dát pokyn plánovači úloh, jak naplánovat úlohy ve fondu vláken. V následující tabulce jsou uvedeny různé možnosti pro vytváření úloh.

|<xref:System.Threading.Tasks.TaskCreationOptions>hodnota parametru|Description|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Výchozí hodnota, pokud není zadána jiná. Plánovač používá k plánování úlohy své výchozí heuristické metody.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Určuje, že úlohy by měly být naplánovány tak, aby se úlohy vytvořené dříve pravděpodobně prováděly dříve a později vytvořené úlohy aby se s větší pravděpodobností prováděly později.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Určuje, že úloha představuje dlouhotrvající operaci.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Určuje, že úloha by měla být vytvořena jako připojená podřízená úloha aktuální úlohy, pokud existuje. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Určuje, že pokud vnitřní úloha Určuje `AttachedToParent` možnost, tato úloha se nestane připojenou podřízenou úlohou.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Určuje, že Plánovač úloh pro úlohy vytvořené voláním metod, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> jako <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> je nebo z určitého úkolu, je výchozím plánovačem namísto plánovače, na kterém je tato úloha spuštěná.|

Možnosti lze kombinovat pomocí bitové operace **nebo** . Následující příklad ukazuje úlohu s <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> možností a.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Úlohy, vlákna a jazyková verze

Každé vlákno má přidruženou jazykovou verzi a jazykovou verzi uživatelského rozhraní, které jsou definovány <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnostmi a v <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> uvedeném pořadí. Jazyková verze vlákna se v takových operacích používá jako formátování, analýza, řazení a porovnávání řetězců. Jazyková verze uživatelského rozhraní vlákna se používá při vyhledávání prostředků. Pokud neurčíte výchozí jazykovou verzi pro všechna vlákna v doméně aplikace pomocí <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> vlastností a, výchozí jazyková verze a jazyková verze uživatelského rozhraní vlákna jsou definovány systémovou jazykovou verzí. Pokud jste explicitně nastavili jazykovou verzi vlákna a spustili nové vlákno, nové vlákno nedědí jazykovou verzi volajícího vlákna; místo toho je jeho jazyková verze výchozí jazyková verze systému. Programovací model založený na úlohách pro aplikace, které cílí na verze .NET Framework před .NET Framework 4,6 v souladu s tímto postupem.

> [!IMPORTANT]
> Všimněte si, že jazyková verze volajícího vlákna je v rámci kontextu úlohy platná pro aplikace, které *cílí* na .NET Framework 4,6, ne aplikace, které *běží pod* .NET Framework 4,6. Můžete cílit na konkrétní verzi .NET Framework při vytváření projektu v aplikaci Visual Studio výběrem této verze z rozevíracího seznamu v horní části dialogového okna **Nový projekt** nebo mimo sadu Visual Studio můžete použít <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut. Pro aplikace, které cílí na verze .NET Framework před .NET Framework 4,6 nebo které necílí na konkrétní verzi .NET Framework, je jazyková verze úlohy i nadále určena kulturou vlákna, na které běží.

Počínaje aplikacemi, které cílí na .NET Framework 4,6, je jazyková verze volajícího vlákna zděděna každou úlohou, a to i v případě, že se úloha spouští asynchronně ve vlákně fondu vláken.

Následující příklad poskytuje jednoduchý obrázek. Používá <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut k cílení na .NET Framework 4,6 a změní aktuální jazykovou verzi aplikace na francouzštinu (Francie) nebo, pokud francouzština (Francie) již aktuální jazykovou verzi, angličtinu (USA). Poté vyvolá delegáta s názvem `formatDelegate` , který vrátí čísla formátovaná jako hodnoty měny v nové jazykové verzi. Všimněte si, zda delegát jako úkol buď synchronně, nebo asynchronně, vrátí očekávaný výsledek, protože jazyková verze volajícího vlákna je zděděna asynchronním úkolem.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Pokud používáte aplikaci Visual Studio, můžete <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut vynechat a místo toho vybrat .NET Framework 4,6 jako cíl při vytváření projektu v dialogovém okně **Nový projekt** .

Pro výstup, který odráží chování aplikací cílové verze .NET Framework před .NET Framework 4,6, odeberte <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut ze zdrojového kódu. Výstup bude odpovídat konvencím formátování výchozí jazykové verze systému, nikoli jazykové verzi volajícího vlákna.

Další informace o asynchronních úlohách a jazykové verzi naleznete v části "jazyková verze a asynchronní operace založené na úlohách" v <xref:System.Globalization.CultureInfo> tématu.

## <a name="creating-task-continuations"></a>Vytváření pokračování úlohy

<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>Metody a <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> umožňují zadat úlohu, která se spustí po dokončení *předchozí úlohy* . Delegátem úlohy pokračování je předán odkaz na předchozí úlohu, aby mohl prověřit stav předchozí úlohy a načtením hodnoty <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti může použít výstup předchůdce jako vstup pro pokračování.

V následujícím příkladu `getData` je úloha spuštěna voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> metody. `processData`Úkol se spustí automaticky po `getData` dokončení a `displayData` po dokončení se spustí `processData` . `getData`Vytvoří celočíselné pole, které je přístupné pro `processData` úkol prostřednictvím `getData` <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti úkolu. `processData`Úkol zpracuje toto pole a vrátí výsledek, jehož typ je odvozen z návratového typu výrazu lambda, který je předán <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> metodě. `displayData`Úloha se spustí automaticky po `processData` dokončení a <xref:System.Tuple%603> objekt vrácený `processData` výrazem lambda je přístupný pro `displayData` úkol prostřednictvím `processData` <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti úkolu. `displayData`Úloha vezme výsledek `processData` úlohy a vytvoří výsledek, jehož typ je odvozen podobným způsobem a který je zpřístupněn programu ve <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnosti.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Vzhledem k tomu <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> , že je metoda instance, můžete zřetězit volání metody společně namísto vytvoření instance <xref:System.Threading.Tasks.Task%601> objektu pro každou předchozí úlohu. Následující příklad je funkčně totožný s předchozím příkladem, s tím rozdílem, že řetězí volání <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Všimněte si, že <xref:System.Threading.Tasks.Task%601> objekt vrácený řetězcem volání metody je poslední úloha pokračování.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>Metody a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> umožňují pokračovat z více úloh.

Další informace najdete v tématu [zřetězení úloh pomocí úloh pokračování](chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Vytváření odpojených podřízených úloh

Když uživatelský kód, který běží v rámci úlohy, vytvoří novou úlohu a neurčí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost, není nová úloha žádným zvláštním způsobem synchronizována s nadřazenou úlohou. Tento typ nesynchronizované úlohy se nazývá *odpojená vnořená úloha* nebo *odpojená podřízená úloha*. Následující příklad zobrazuje úlohu, která vytváří jednu odpojenou podřízenou úlohu.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Nadřazená úloha nečeká na dokončení odpojené podřízené úlohy.

## <a name="creating-child-tasks"></a>Vytváření podřízených úloh

Když uživatelský kód, který běží v rámci úlohy, vytvoří úlohu s <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možností, je nová úloha známá jako *připojená podřízená úloha* nadřazené úlohy. Tuto možnost můžete použít <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> k vyjádření paralelismu strukturovaného úkolu, protože nadřazená úloha implicitně čeká na dokončení všech připojených podřízených úloh. Následující příklad zobrazuje nadřazenou úlohu, která vytvoří deset připojených podřízených úloh. Všimněte si, že přestože příklad volá <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodu pro čekání na dokončení nadřazené úlohy, nemusí explicitně čekat na dokončení připojených podřízených úloh.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Nadřazená úloha může využít <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost k tomu, aby se zabránilo připojení jiných úloh k nadřazené úloze. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Čeká se na dokončení úloh.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Typy a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> poskytují několik přetížení <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metod, které vám umožňují počkat na dokončení úlohy. Kromě toho přetížení statických <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metod umožňují počkat na dokončení všech nebo všech polí úkolů.

Obvykle se na úlohu čeká z některého z těchto důvodů:

- Hlavní vlákno závisí na konečném výsledku vypočítaném úlohou.

- Je potřeba zpracovat výjimky, které mohou být vyvolány z úlohy.

- Aplikace se může ukončit předtím, než se dokončí všechny úlohy. Například konzolové aplikace budou ukončeny hned po provedení veškerého synchronního kódu v `Main` (vstupní bod aplikace).

Následující příklad zobrazuje základní vzor, který nezahrnuje zpracování výjimek.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Příklad zobrazující zpracování výjimek naleznete v tématu [zpracování výjimek](exception-handling-task-parallel-library.md).

Některá přetížení umožňují určit časový limit a jiné přijímají <xref:System.Threading.CancellationToken> jako vstupní parametr další, aby bylo možné samotné čekání zrušit buď programově, nebo jako odpověď na uživatelský vstup.

Při čekání na úlohu se implicitně čeká na všechny podřízené položky této úlohy, které byly vytvořeny pomocí <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> Možnosti. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Vrátí hodnotu okamžitě, pokud úloha již byla dokončena. Jakékoli výjimky vyvolané úlohou budou vyvolány <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodou, a to i v případě, že <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> byla metoda volána po dokončení úlohy.

## <a name="composing-tasks"></a>Vytváření úloh

<xref:System.Threading.Tasks.Task>Třídy a <xref:System.Threading.Tasks.Task%601> poskytují několik metod, které vám pomohou vytvořit více úkolů pro implementaci běžných vzorů a lépe používat asynchronní funkce jazyka, které jsou k dispozici v jazyce C#, Visual Basic a F #. Tato část popisuje <xref:System.Threading.Tasks.Task.WhenAll%2A> metody, <xref:System.Threading.Tasks.Task.WhenAny%2A> , <xref:System.Threading.Tasks.Task.Delay%2A> a <xref:System.Threading.Tasks.Task.FromResult%2A> .

### <a name="taskwhenall"></a>Task.WhenAll

<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>Metoda asynchronně čeká na <xref:System.Threading.Tasks.Task> dokončení více <xref:System.Threading.Tasks.Task%601> objektů nebo. Poskytuje přetížené verze, které umožňují čekání na nerovnoměrné sady úloh. Například můžete počkat na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> dokončení více objektů a z jednoho volání metody.

### <a name="taskwhenany"></a>Task.WhenAny

<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>Metoda asynchronně čeká na dokončení jednoho z více <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> objektů nebo. Stejně jako v <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodě Tato metoda poskytuje přetížené verze, které umožňují počkat na nejednotné sady úloh. Tato <xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda je obzvláště užitečná v následujících scénářích.

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu k výběru operace, která skončí jako první, a pak zrušit zbývající operace.

- Prokládané operace. Můžete spustit více operací, které se musí dokončit, a použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu k prodloužení předchozího scénáře omezením počtu souběžných operací.

- Operace, jejichž platnost vypršela. Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu k výběru jedné nebo více úloh a úlohy, která skončí po určité době, jako je například úkol vrácený <xref:System.Threading.Tasks.Task.Delay%2A> metodou. <xref:System.Threading.Tasks.Task.Delay%2A>Metoda je popsána v následující části.

### <a name="taskdelay"></a>Task.Delay

<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>Metoda vytvoří <xref:System.Threading.Tasks.Task> objekt, který skončí po specifikovaném čase. Tuto metodu můžete použít k vytvoření cyklů, které občas provádějí dotazování na data, zavedení limitů, zpracování vstupu uživatele na předem stanovenou dobu zpoždění a tak dále.

### <a name="tasktfromresult"></a>Task(T).FromResult

Pomocí <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody můžete vytvořit <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje předem vypočítaný výsledek. Tato metoda je užitečná při provádění asynchronní operace, která vrací <xref:System.Threading.Tasks.Task%601> objekt a výsledek tohoto <xref:System.Threading.Tasks.Task%601> objektu je již vypočítán. Příklad, který používá <xref:System.Threading.Tasks.Task.FromResult%2A> k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti, naleznete v tématu [How to: Create předběžně počítané úkoly](how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Zpracování výjimek v úlohách

Když úloha vyvolá jednu nebo více výjimek, výjimky jsou zabaleny do <xref:System.AggregateException> výjimky. Tato výjimka je šířena zpět do vlákna, které se spojí s úlohou, což je obvykle vlákno, které čeká na dokončení úlohy nebo vlákno, které přistupuje k <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnosti. Toto chování slouží k vynucení, aby při všech neošetřených výjimkách ve výchozím nastavení zásady rozhraní .NET Framework ukončily proces. Volající kód může zpracovávat výjimky pomocí některého z následujících v `try` / `catch` bloku:

- <xref:System.Threading.Tasks.Task.Wait%2A>Metoda

- <xref:System.Threading.Tasks.Task.WaitAll%2A>Metoda

- <xref:System.Threading.Tasks.Task.WaitAny%2A>Metoda

- <xref:System.Threading.Tasks.Task%601.Result%2A>Vlastnost

Spojovací vlákno může také zpracovávat výjimky přístupem k <xref:System.Threading.Tasks.Task.Exception%2A> vlastnosti předtím, než je úloha uvolněna z paměti. Přístupem k této vlastnosti nebude nezpracovaná výjimka spouštět chování šíření výjimky, které ukončí proces, když je objekt finalizován.

Další informace o výjimkách a úlohách naleznete v tématu [zpracování výjimek](exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Rušení úloh

<xref:System.Threading.Tasks.Task>Třída podporuje kooperativní zrušení a je plně integrovaná s <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> <xref:System.Threading.CancellationToken?displayProperty=nameWithType> třídami a, které byly představeny v .NET Framework 4. Mnoho konstruktorů ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídě přijímá <xref:System.Threading.CancellationToken> objekt jako vstupní parametr. Mnoho z <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> přetížení a <xref:System.Threading.Tasks.Task.Run%2A> také obsahuje <xref:System.Threading.CancellationToken> parametr.

Můžete vytvořit token a vystavit žádost o zrušení později pomocí <xref:System.Threading.CancellationTokenSource> třídy. Předání tokenu <xref:System.Threading.Tasks.Task> jako argumentu a také odkazování na stejný token v uživatelském delegátu, který provádí reakci na žádost o zrušení.

Další informace naleznete v tématu [zrušení úlohy](task-cancellation.md) a [Postup: zrušení úlohy a jejích podřízených objektů](how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Třída TaskFactory

<xref:System.Threading.Tasks.TaskFactory>Třída poskytuje statické metody, které zapouzdřují některé běžné vzory pro vytváření a spouštění úloh a pokračujících úloh.

- Nejběžnějším vzorem je <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> , který vytvoří a spustí úlohu v jednom příkazu.

- Při vytváření pokračujících úloh z více předchůdců použijte <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metodu nebo <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metodu nebo jejich ekvivalenty ve <xref:System.Threading.Tasks.Task%601> třídě. Další informace najdete v tématu [zřetězení úloh pomocí úloh pokračování](chaining-tasks-by-using-continuation-tasks.md).

- Pro zapouzdření asynchronního programovacího modelu `BeginX` a `EndX` metod <xref:System.Threading.Tasks.Task> v <xref:System.Threading.Tasks.Task%601> instanci nebo použijte <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Další informace naleznete v tématu [TPL a tradiční .NET Framework asynchronní programování](tpl-and-traditional-async-programming.md).

Výchozí hodnota je <xref:System.Threading.Tasks.TaskFactory> k dispozici jako statická vlastnost <xref:System.Threading.Tasks.Task> třídy nebo třídy <xref:System.Threading.Tasks.Task%601> . Můžete také vytvořit instanci <xref:System.Threading.Tasks.TaskFactory> přímo a určit různé možnosti, které zahrnují <xref:System.Threading.CancellationToken> , <xref:System.Threading.Tasks.TaskCreationOptions> možnost, <xref:System.Threading.Tasks.TaskContinuationOptions> možnost nebo <xref:System.Threading.Tasks.TaskScheduler> . Jakékoli možnosti, které jsou zadány při vytváření továrny úloh, budou použity pro všechny úlohy, které vytvoří, pokud <xref:System.Threading.Tasks.Task> se nevytvoří pomocí <xref:System.Threading.Tasks.TaskCreationOptions> výčtu, v takovém případě možnosti úlohy přepíší tyto úlohy.

## <a name="tasks-without-delegates"></a>Úlohy bez delegátů

V některých případech můžete chtít použít <xref:System.Threading.Tasks.Task> k zapouzdření některé asynchronní operace, kterou provádí externí komponenta namísto uživatelského delegáta. Pokud je operace založena na vzoru Begin/End modelu asynchronního programování, můžete použít <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. V takovém případě můžete použít <xref:System.Threading.Tasks.TaskCompletionSource%601> objekt k zabalení operace v úloze a získat tak některé výhody <xref:System.Threading.Tasks.Task> programovatelnosti, například podporu pro šíření výjimek a pokračování. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Vlastní plánovače

Většina vývojářů aplikací nebo knihoven nezáleží na tom, na kterém procesoru je úloha spuštěna, jak synchronizuje svou práci s ostatními úkoly nebo jak je naplánována <xref:System.Threading.ThreadPool?displayProperty=nameWithType> . Vyžadují pouze to, aby byly tyto úkony v hostitelském počítači prováděny tak efektivně, jak je to možné. Pokud požadujete jemněji odstupňovanou kontrolu nad podrobnostmi plánování, Task Parallel Library umožňuje konfigurovat některá nastavení výchozího plánovače úloh a dokonce umožňuje zadat vlastní plánovač. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Související datové struktury

TPL má několik nových veřejných typů, které jsou použitelné jak v situacích paralelního, tak i sekvenčního vykonávání. Mezi ně patří několik bezpečných a škálovatelných tříd kolekcí v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů a několik nových typů synchronizace, například <xref:System.Threading.Semaphore?displayProperty=nameWithType> a <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , které jsou efektivnější než jejich předchůdce pro konkrétní druhy úloh. Další nové typy v .NET Framework 4, například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.SpinLock?displayProperty=nameWithType> , poskytují funkce, které v dřívějších verzích nebyly k dispozici. Další informace najdete v tématu [datové struktury pro paralelní programování](data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Vlastní typy úloh

Doporučujeme Nedědit z <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> . Místo toho doporučujeme použít <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost k přidružení dalších dat nebo stavu k <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> objektu nebo. Můžete také použít rozšiřující metody k rozšíření funkčnosti <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> tříd a. Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) a [metody rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Pokud je nutné dědit z <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , nelze použít <xref:System.Threading.Tasks.Task.Run%2A> třídy, nebo <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> , <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> k vytvoření instancí vlastního typu úkolu, protože tyto mechanismy vytváří pouze <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> objekty a. Kromě toho nemůžete použít mechanismy pokračování úloh, které jsou k dispozici pomocí <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.TaskFactory> a <xref:System.Threading.Tasks.TaskFactory%601> k vytvoření instancí vlastního typu úkolu, protože tyto mechanismy také vytvářejí pouze <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> objekty a.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-|-|
|[Řetězení úloh pomocí úloh pokračování](chaining-tasks-by-using-continuation-tasks.md)|Popisuje, jak fungují pokračování.|
|[Připojené a odpojené podřízené úlohy](attached-and-detached-child-tasks.md)|Popisuje rozdíl mezi připojenými a odpojenými podřízenými úlohami.|
|[Zrušení úlohy](task-cancellation.md)|Popisuje podporu zrušení, která je integrována do <xref:System.Threading.Tasks.Task> objektu.|
|[Zpracování výjimek](exception-handling-task-parallel-library.md)|Popisuje způsob zpracování výjimek v souběžných vláknech.|
|[Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací](how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Popisuje, jak používat <xref:System.Threading.Tasks.Parallel.Invoke%2A> .|
|[Postupy: Vrácení hodnoty z úlohy](how-to-return-a-value-from-a-task.md)|Popisuje, jak z úloh vracet hodnoty.|
|[Postupy: Zrušení úlohy a podřízených elementů](how-to-cancel-a-task-and-its-children.md)|Popisuje, jak zrušit úlohy.|
|[Postupy: Vytváření předvypočítaných úloh](how-to-create-pre-computed-tasks.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti.|
|[Postupy: Procházení binárního stromu s paralelními úlohami](how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Popisuje, jak použít úlohy k procházení binárního stromu.|
|[Postupy: Rozbalení vnořené úlohy](how-to-unwrap-a-nested-task.md)|Ukazuje, jak použít <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metodu rozšíření.|
|[Datový paralelismus](data-parallelism-task-parallel-library.md)|Popisuje, jak používat <xref:System.Threading.Tasks.Parallel.For%2A> a <xref:System.Threading.Tasks.Parallel.ForEach%2A> k vytvoření paralelních smyček pro data.|
|[Paralelní programování](index.md)|Uzel nejvyšší úrovně pro paralelní programování rozhraní .NET Framework.|

## <a name="see-also"></a>Viz také

- [Paralelní programování](index.md)
- [Ukázky pro paralelní programování s rozhraním .NET Core & .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
