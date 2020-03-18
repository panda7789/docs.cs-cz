---
title: Asynchronní programování založené na úlohách - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 51292d977f2be87cec7c3481f5004fe5fe756224
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74204539"
---
# <a name="task-based-asynchronous-programming"></a>Asynchronní programování založené na úlohách

Paralelní knihovna úloh (TPL) je založena na konceptu *úlohy*, která představuje asynchronní operaci. V některých ohledech úkol podobá <xref:System.Threading.ThreadPool> vlákno nebo pracovní položku, ale na vyšší úrovni abstrakce. Termín *paralelismus úlohy* odkazuje na jeden nebo více nezávislých úloh spuštěných současně. Úlohy poskytují dvě hlavní výhody:

- Větší škálovatelnost a efektivnější využívání systémových prostředků.

     Na pozadí jsou úkoly zařazeny do fronty na <xref:System.Threading.ThreadPool>, který byl rozšířen o algoritmy, které určují a upravují počet podprocesů a které poskytují vyrovnávání zatížení pro maximalizaci propustnost. Díky tomu jsou úlohy relativně lehké a lze jich vytvořit mnoho, takže lze dosáhnout jemně odstupňovaného paralelismu.

- Více programového ovládání než je k dispozici s vláknem nebo pracovní položkou.

     Úlohy a architektura kolem nich vytvořená poskytují bohatou sadu rozhraní (API), která podporují čekání, zrušení, pokračování, robustní zpracování výjimek, podrobný stav, vlastní plánování a další.

Pro oba z těchto důvodů je v rozhraní .NET Framework TPL upřednostňovaným rozhraním API pro psaní vícevláknového, asynchronního a paralelního kódu.

## <a name="creating-and-running-tasks-implicitly"></a>Implicitní vytváření a spouštění úloh

Metoda <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> poskytuje pohodlný způsob, jak spustit libovolný počet příkazů současně. Stačí předat <xref:System.Action> delegáta pro každou položku práce. Nejsnadnější způsob, jak vytvořit tyto delegáty, je použití lambda výrazů. Lambda výraz může buďto volat pojmenovanou metodu, nebo poskytnout vložený kód. Následující příklad ukazuje <xref:System.Threading.Tasks.Parallel.Invoke%2A> základní volání, které vytvoří a spustí dva úkoly, které běží souběžně. První úkol je reprezentován výrazem lambda, `DoSomeWork`který volá metodu s názvem a druhý úkol `DoSomeOtherWork`je reprezentován výrazem lambda, který volá metodu s názvem .

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Počet <xref:System.Threading.Tasks.Task> instancí, které jsou vytvořeny <xref:System.Threading.Tasks.Parallel.Invoke%2A> na pozadí podle nemusí nutně rovnat počtu delegátů, které jsou k dispozici. Knihovna TPL může využít různé optimalizace, zejména s velkým počtem delegátů.

Další informace naleznete v [tématu How to: Use Parallel.Invoke to Execute Parallel Operations](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Pro větší kontrolu nad provádění úloh nebo vrátit hodnotu z <xref:System.Threading.Tasks.Task> úkolu, budete muset pracovat s objekty explicitněji.

## <a name="creating-and-running-tasks-explicitly"></a>Explicitní vytváření a spouštění úloh

Úkol, který nevrací hodnotu, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> je reprezentován třídou. Úloha, která vrací hodnotu, je reprezentována třídou, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> která dědí z <xref:System.Threading.Tasks.Task>. Objekt úlohy zpracovává podrobnosti infrastruktury a poskytuje metody a vlastnosti, které jsou přístupné z volajícího vlákna po celou dobu trvání úlohy. Můžete například kdykoli <xref:System.Threading.Tasks.Task.Status%2A> přistupovat k vlastnosti úlohy a zjistit, zda byla spuštěna, spuštěna, byla zrušena nebo vyvolala výjimku. Stav je reprezentován <xref:System.Threading.Tasks.TaskStatus> výčtu.

Když je vytvořena úloha, je jí zadán uživatelský delegát, jenž provádí zapouzdření kódu, který úloha provede. Tento delegát může být vyjádřen jako pojmenovaný delegát, anonymní metoda nebo lambda výraz. Lambda výrazy mohou obsahovat volání pojmenované metody, jak ukazuje následující příklad. Všimněte si, že příklad <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> obsahuje volání metody k zajištění, že úloha dokončí spuštění před ukončením konzolového režimu.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Metody můžete také <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> použít k vytvoření a spuštění úkolu v jedné operaci. Chcete-li spravovat <xref:System.Threading.Tasks.Task.Run%2A> úkol, metody používají výchozí plánovač úloh, bez ohledu na to, který plánovač úloh je přidružen k aktuálnímu vláknu. Metody <xref:System.Threading.Tasks.Task.Run%2A> jsou upřednostňovaným způsobem vytváření a spouštění úkolů, pokud není potřeba větší kontrola nad vytvářením a plánováním úkolu.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Metodu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> můžete také použít k vytvoření a spuštění úkolu v jedné operaci. Tuto metodu použijte, pokud vytváření a plánování není nutné oddělit a potřebujete další možnosti vytvoření úkolu nebo použití konkrétního plánovače, <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> nebo když potřebujete předat další stav do úkolu, který můžete načíst prostřednictvím jeho vlastnosti, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task>a <xref:System.Threading.Tasks.Task%601> každý vystavit <xref:System.Threading.Tasks.Task.Factory%2A> statickou vlastnost, <xref:System.Threading.Tasks.TaskFactory>která vrací výchozí instanci `Task.Factory.StartNew()`, takže můžete volat metodu jako . Také v následujícím příkladu, protože úkoly jsou typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> , každý z nich mají veřejnou vlastnost, která obsahuje výsledek výpočtu. Úlohy běží asynchronně a mohou být dokončeny v libovolném pořadí. Pokud <xref:System.Threading.Tasks.Task%601.Result%2A> je vlastnost přístupná před dokončením výpočtu, vlastnost blokuje volající vlákno, dokud není k dispozici hodnota.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Další informace naleznete v [tématu How to: Return a Value from a Task](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Při použití lambda výrazu k vytvoření delegáta máte přístup ke všem proměnným, které jsou v daném okamžiku viditelné ve zdrojovém kódu. V některých případech, zejména v rámci smyčky, však lambda nezachytí proměnnou podle očekávání. Pouze zachycuje konečnou hodnotu, nikoli mutaci hodnoty po každé iteraci. Následující příklad ukazuje tento problém. Předá čítač smyčky výrazu lambda, `CustomData` který konkretizovat objekt a používá čítač smyčky jako identifikátor objektu. Jak ukazuje výstup z příkladu, každý `CustomData` objekt má stejný identifikátor.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

K hodnotě v každé iteraci můžete přistupovat zadáním objektu stavu úlohy pomocí jeho konstruktoru. Následující příklad upraví předchozí příklad pomocí čítače `CustomData` smyčky při vytváření objektu, který je zase předán výrazu lambda.  Jak ukazuje výstup z příkladu, každý `CustomData` objekt má nyní jedinečný identifikátor založený na hodnotě čítače smyčky v době, kdy byl objekt vytvořena.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Tento stav je předán jako argument delegátovi úkolu a lze k němu <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> přistupovat z objektu úlohy pomocí vlastnosti.  Následující příklad je podobný předchozímu příkladu. Používá <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost k zobrazení informací `CustomData` o objektech předaných výrazu lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>ID úlohy

Každá úloha obdrží celé ID, které jej jednoznačně identifikuje v doméně aplikace <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> a lze k němu přistupovat pomocí této vlastnosti. ID je užitečné pro zobrazení informací o úlovcích v oknech **paralelních zásobníků** a **úloh** y sady Visual Studio. ID využívá líné vytváření, což znamená, že není vytvořeno, dokud se o něj nepožádá, proto může mít úloha při každém spuštění programu jiné ID. Další informace o zobrazení ID úkolů v ladicím programu naleznete v [tématu Použití okna Úlohy](/visualstudio/debugger/using-the-tasks-window) a [Použití okna Paralelní hromádky](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Možnosti vytvoření úkolu

Většina rozhraní API, které vytvářejí <xref:System.Threading.Tasks.TaskCreationOptions> úkoly poskytují přetížení, které přijímají parametr. Zadáním jedné z těchto možností lze dát pokyn plánovači úloh, jak naplánovat úlohy ve fondu vláken. V následující tabulce jsou uvedeny různé možnosti pro vytváření úloh.

|<xref:System.Threading.Tasks.TaskCreationOptions>hodnota parametru|Popis|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Výchozí hodnota, pokud není zadána jiná. Plánovač používá k plánování úlohy své výchozí heuristické metody.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Určuje, že úlohy by měly být naplánovány tak, aby se úlohy vytvořené dříve pravděpodobně prováděly dříve a později vytvořené úlohy aby se s větší pravděpodobností prováděly později.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Určuje, že úloha představuje dlouhotrvající operaci.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Určuje, že úloha by měla být vytvořena jako připojená podřízená úloha aktuální úlohy, pokud existuje. Další informace naleznete v [tématu Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Určuje, že pokud vnitřní úloha určuje `AttachedToParent` možnost, nebude se tato úloha stát připojenou podřízenou úlohou.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Určuje, že plánovač úloh pro úlohy <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> vytvořené <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> voláním metod, jako je nebo z určité úlohy, je výchozím plánovačem namísto plánovače, na kterém je tato úloha spuštěna.|

Možnosti lze kombinovat pomocí bitové operace **OR.** Následující příklad ukazuje úkol, <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> který <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> má a možnost.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Úkoly, vlákna a jazyková verze

Každé vlákno má přidružené jazykové verze a jazykové <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> verze <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> uživatelského rozhraní, která je definována a vlastnosti, v uvedeném pořadí. Jazyková verze vlákna se používá v takových operacích, jako je formátování, analýza, řazení a porovnávání řetězců. Jazyková verze uživatelského rozhraní vlákna se používá ve vyhledávání prostředků. Obvykle, pokud zadáte výchozí jazykovou verzi pro všechna vlákna <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> v <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> doméně aplikace pomocí vlastností a, výchozí jazyková verze a jazyková verze uživatelského rozhraní vlákna je definována jazykovou verzí systému. Pokud explicitně nastavíte jazykovou verzi vlákna a spustíte nové vlákno, nové vlákno nezdědí jazykovou verzi volajícího vlákna; místo toho jeho jazyková verze je výchozí jazyková verze systému. Programovací model založený na úlohách pro aplikace, které cílí na verze rozhraní .NET Framework před rozhraním .NET Framework 4.6, dodržuje tento postup.

> [!IMPORTANT]
> Všimněte si, že jazyková verze volajícího vlákna jako součást kontextu úlohy se vztahuje na aplikace, které *cílí* na rozhraní .NET Framework 4.6, nikoli na aplikace, které *běží v rámci* rozhraní .NET Framework 4.6. Určitou verzi rozhraní .NET Framework můžete cílit při vytváření projektu v sadě Visual Studio výběrem této verze z rozevíracího seznamu v <xref:System.Runtime.Versioning.TargetFrameworkAttribute> horní části dialogového okna Nový **projekt** nebo mimo Visual Studio můžete atribut použít. U aplikací, které cílí na verze rozhraní .NET Framework před rozhraním .NET Framework 4.6 nebo které necílí na určitou verzi rozhraní .NET Framework, bude jazyková verze úlohy nadále určována jazykovou verzí vlákna, na kterém je spuštěna.

Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6, je jazyková verze volajícího vlákna zděděna jednotlivými úlohami, i když je úloha spuštěna asynchronně ve vlákně fondu vláken.

Následující příklad obsahuje jednoduchý obrázek. Používá <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut k cílení rozhraní .NET Framework 4.6 a změní aktuální jazykovou verzi aplikace na francouzštinu (Francie) nebo, pokud francouzština (Francie) je již aktuální jazykovou verzi, angličtina (Spojené státy). Potom vyvolá delegáta `formatDelegate` s názvem, který vrací některá čísla formátovaná jako hodnoty měny v nové jazykové verzi. Všimněte si, že zda delegát jako úkol synchronně nebo asynchronně, vrátí očekávaný výsledek, protože jazyková verze volajícího vlákna je zděděna asynchronní úlohou.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Pokud používáte Visual Studio, můžete <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atribut vynechat a místo toho vybrat rozhraní .NET Framework 4.6 jako cíl při vytváření projektu v dialogovém okně Nový **projekt.**

Pro výstup, který odráží chování aplikací cílové verze rozhraní .NET Framework před rozhraním <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET Framework 4.6, odeberte atribut ze zdrojového kódu. Výstup bude odrážet konvence formátování výchozí jazykové verze systému, nikoli jazykovou verzi volajícího vlákna.

Další informace o asynchronních úlohách a jazykové verzi naleznete v části "Jazyková <xref:System.Globalization.CultureInfo> verze a operace založené na asynchronních úlohách" v tématu.

## <a name="creating-task-continuations"></a>Vytváření pokračování úkolu

Metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> a umožňují určit úkol, který má být zahájen po dokončení *předchozíúlohy.* Delegát úlohy pokračování je předán odkaz na předchozí úkol tak, aby mohl prozkoumat stav předchozí úlohy a <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> načtením hodnoty vlastnosti použít výstup předchůdce jako vstup pro pokračování.

V následujícím příkladu `getData` je úloha spuštěna <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> voláním metody. Úloha `processData` je spuštěna automaticky po `getData` dokončení a `displayData` je spuštěna po `processData` dokončení. `getData`vytvoří celé pole, které je přístupné `processData` úkolu prostřednictvím `getData` <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti úkolu. Úloha `processData` zpracovává pole a vrátí výsledek, jehož typ je odvozen z návratového <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> typu výrazu lambda předaného metodě. Úloha se `displayData` spustí `processData` automaticky po <xref:System.Tuple%603> dokončení a `processData` objekt vrácený výrazem `displayData` lambda `processData` je <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> přístupný úkolu prostřednictvím vlastnosti úlohy. Úkol `displayData` přebírá výsledek `processData` úkolu a vytváří výsledek, jehož typ je odvozen podobným způsobem a který je <xref:System.Threading.Tasks.Task%601.Result%2A> k dispozici programu ve vlastnosti.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Protože <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> je metoda instance, můžete zřetězit volání metody <xref:System.Threading.Tasks.Task%601> společně namísto vytváření instancí objektu pro každou předchozí úlohu. Následující příklad je funkčně identický s předchozím příkladem, <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> s tím rozdílem, že řetězy společně volání metody. Všimněte <xref:System.Threading.Tasks.Task%601> si, že objekt vrácený řetězcem volání metody je konečný úkol pokračování.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> a umožňují pokračovat z více úkolů.

Další informace naleznete v [tématu Chaining Tasks pomocí pokračování úlohy](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Vytváření odpojených podřízených úkolů

Pokud uživatelský kód spuštěný v úloze vytvoří novou <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> úlohu a neurčí možnost, nebude nová úloha žádným zvláštním způsobem synchronizována s nadřazenou úlohou. Tento typ nesynchronizované úlohy se nazývá *odpojená vnořená úloha* nebo *odpojená podřízená úloha*. Následující příklad zobrazuje úlohu, která vytváří jednu odpojenou podřízenou úlohu.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Nadřazená úloha nečeká na dokončení odpojené podřízené úlohy.

## <a name="creating-child-tasks"></a>Vytváření podřízených úkolů

Pokud kód uživatele spuštěný v úloze <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> vytvoří úlohu s možností, nová úloha se označuje jako *připojený podřízený úkol nadřazené* úlohy. Můžete použít <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost vyjádřit paralelismu strukturovanéúlohy, protože nadřazená úloha implicitně čeká na dokončení všech připojených podřízených úloh. Následující příklad zobrazuje nadřazenou úlohu, která vytvoří deset připojených podřízených úloh. Všimněte si, že <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> i když příklad volá metodu čekat na dokončení nadřazené úlohy, nemusí explicitně čekat na dokončení připojených podřízených úkolů.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Nadřazený <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> úkol může tuto možnost použít k zabránění připojení jiných úkolů k nadřazenému úkolu. Další informace naleznete v [tématu Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Čekání na dokončení úkolů

Typy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a poskytují několik přetížení <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, které umožňují čekat na dokončení úkolu. Kromě toho přetížení statické <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody umožňují čekat na některé nebo všechny pole úloh y dokončení.

Obvykle se na úlohu čeká z některého z těchto důvodů:

- Hlavní vlákno závisí na konečném výsledku vypočítaném úlohou.

- Je potřeba zpracovat výjimky, které mohou být vyvolány z úlohy.

- Aplikace se může ukončit předtím, než se dokončí všechny úlohy. Například konzolové aplikace budou ukončeny, jakmile `Main` bude spuštěn veškerý synchronní kód v (vstupní bod aplikace).

Následující příklad zobrazuje základní vzor, který nezahrnuje zpracování výjimek.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Příklad, který ukazuje zpracování výjimek, naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Některá přetížení umožňují zadat časový režim a jiné <xref:System.Threading.CancellationToken> přijmout další jako vstupní parametr, tak, aby čekání sám může být zrušena programově nebo v reakci na vstup uživatele.

Při čekání na úkol implicitně čekat na všechny podřízené funkce tohoto <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> úkolu, které byly vytvořeny pomocí možnosti. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>vrátí okamžitě, pokud je úkol již dokončen. Všechny výjimky vyvolané úkolem budou vyvolány <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodou, <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> i když byla metoda volána po dokončení úkolu.

## <a name="composing-tasks"></a>Vytváření úkolů

A <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> třídy poskytují několik metod, které vám mohou pomoci vytvořit více úkolů k implementaci běžných vzorů a lépe používat funkce asynchronního jazyka, které jsou poskytovány C#, Visual Basic a F#. Tato část popisuje <xref:System.Threading.Tasks.Task.WhenAll%2A> <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, <xref:System.Threading.Tasks.Task.FromResult%2A> , a metody.

### <a name="taskwhenall"></a>Task.WhenAll

Metoda <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> asynchronně čeká na dokončení <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> více nebo objektů. Poskytuje přetížené verze, které umožňují čekání na nerovnoměrné sady úloh. Můžete například počkat <xref:System.Threading.Tasks.Task> na <xref:System.Threading.Tasks.Task%601> více a objekty k dokončení z jednoho volání metody.

### <a name="taskwhenany"></a>Task.WhenAny

Metoda <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> asynchronně čeká na jeden z <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> více nebo objektů k dokončení. Stejně <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jako v metodě tato metoda poskytuje přetížené verze, které umožňují čekat na nejednotné sady úkolů. Metoda <xref:System.Threading.Tasks.Task.WhenAny%2A> je zvláště užitečná v následujících scénářích.

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. <xref:System.Threading.Tasks.Task.WhenAny%2A> Pomocí této metody můžete vybrat operaci, která se dokončí jako první, a potom zrušit zbývající operace.

- Prokládané operace. Můžete spustit více operací, které musí <xref:System.Threading.Tasks.Task.WhenAny%2A> dokončit a použít metodu ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. Metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete rozšířit předchozí scénář omezením počtu souběžných operací.

- Operace, jejichž platnost vypršela. <xref:System.Threading.Tasks.Task.WhenAny%2A> Pomocí této metody můžete vybrat mezi jedním nebo více úkoly a úkolem, který se dokončí <xref:System.Threading.Tasks.Task.Delay%2A> po určitém čase, například úkol, který je vrácen metodou. Metoda <xref:System.Threading.Tasks.Task.Delay%2A> je popsána v následující části.

### <a name="taskdelay"></a>Task.Delay

Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> vytvoří <xref:System.Threading.Tasks.Task> objekt, který dokončí po zadaném čase. Tuto metodu můžete použít k vytvoření cyklů, které občas provádějí dotazování na data, zavedení limitů, zpracování vstupu uživatele na předem stanovenou dobu zpoždění a tak dále.

### <a name="tasktfromresult"></a>Task(T).FromResult

Pomocí <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody můžete vytvořit <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje předem vypočítaný výsledek. Tato metoda je užitečná, když provedete asynchronní operaci, která vrátí <xref:System.Threading.Tasks.Task%601> objekt a výsledek tohoto <xref:System.Threading.Tasks.Task%601> objektu je již vypočítán. Příklad, který <xref:System.Threading.Tasks.Task.FromResult%2A> se používá k načtení výsledků asynchronních operací stahování, které jsou uloženy v mezipaměti, najdete v [tématu How to: Create Pre-Computed Tasks](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Zpracování výjimek v úkolech

Když úloha vyvolá jednu nebo více výjimek, výjimky jsou zabaleny do <xref:System.AggregateException> výjimky. Tato výjimka je šířena zpět do vlákna, které se připojuje k úloze, což je obvykle vlákno, <xref:System.Threading.Tasks.Task%601.Result%2A> které čeká na dokončení úlohy nebo vlákno, které přistupuje k vlastnosti. Toto chování slouží k vynucení, aby při všech neošetřených výjimkách ve výchozím nastavení zásady rozhraní .NET Framework ukončily proces. Volající kód může zpracovat výjimky pomocí některého `try` / `catch` z následujících v bloku:

- Metoda <xref:System.Threading.Tasks.Task.Wait%2A>

- Metoda <xref:System.Threading.Tasks.Task.WaitAll%2A>

- Metoda <xref:System.Threading.Tasks.Task.WaitAny%2A>

- Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A>

Spojovací vlákno může také zpracovat výjimky přístupem k vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> před úkol je uvolněna. Přístupem k této vlastnosti nebude nezpracovaná výjimka spouštět chování šíření výjimky, které ukončí proces, když je objekt finalizován.

Další informace o výjimkách a úkolech naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Zrušení úkolů

Třída <xref:System.Threading.Tasks.Task> podporuje kooperativní zrušení a <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> je <xref:System.Threading.CancellationToken?displayProperty=nameWithType> plně integrován s a třídy, které byly zavedeny v rozhraní .NET Framework 4. Mnoho konstruktorů ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídě trvat <xref:System.Threading.CancellationToken> objekt jako vstupní parametr. Mnoho <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> a <xref:System.Threading.Tasks.Task.Run%2A> přetížení také obsahuje <xref:System.Threading.CancellationToken> parametr.

Můžete vytvořit token a vystavit požadavek na zrušení později <xref:System.Threading.CancellationTokenSource> pomocí třídy. Předejte token <xref:System.Threading.Tasks.Task> jako argument a také odkazovat na stejný token v delegáta uživatele, který provádí práci reagovat na žádost o zrušení.

Další informace naleznete v [tématu Zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md) a [postup: Zrušení úkolu a jeho podřízených úloh](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Třída TaskFactory

Třída <xref:System.Threading.Tasks.TaskFactory> poskytuje statické metody, které zapouzdřují některé běžné vzory pro vytváření a spouštění úloh a pokračování úlohy.

- Nejběžnější vzor je <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, který vytvoří a spustí úkol v jednom příkazu.

- Při vytváření úloh pokračování z více předchůdců <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> použijte <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metodu nebo metodu nebo jejich ekvivalenty ve <xref:System.Threading.Tasks.Task%601> třídě. Další informace naleznete v [tématu Chaining Tasks pomocí pokračování úlohy](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Chcete-li zapouzdřit `BeginX` asynchronní programovací model a `EndX` metody v <xref:System.Threading.Tasks.Task> instanci nebo, <xref:System.Threading.Tasks.Task%601> použijte <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Další informace naleznete v [tématech TPL a Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Výchozí <xref:System.Threading.Tasks.TaskFactory> lze přistupovat jako statické vlastnosti na třídu <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> třídu. Můžete také vytvořit instanci <xref:System.Threading.Tasks.TaskFactory> přímo a určit <xref:System.Threading.CancellationToken>různé <xref:System.Threading.Tasks.TaskCreationOptions> možnosti, <xref:System.Threading.Tasks.TaskContinuationOptions> které zahrnují <xref:System.Threading.Tasks.TaskScheduler>, možnost, možnost nebo . Jakékoli možnosti jsou určeny při vytváření úloh budou použity pro <xref:System.Threading.Tasks.Task> všechny úkoly, které vytvoří, pokud je vytvořen pomocí <xref:System.Threading.Tasks.TaskCreationOptions> výčtu, v takovém případě možnosti úkolu přepsat ty z továrny úloh.

## <a name="tasks-without-delegates"></a>Úkoly bez delegátů

V některých případech můžete použít <xref:System.Threading.Tasks.Task> zapouzdřit některé asynchronní operace, která se provádí externí součást namísto vlastního delegáta uživatele. Pokud je operace založena na vzoru Asynchronní programovací model Begin/End, můžete použít <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Pokud tomu tak není, můžete <xref:System.Threading.Tasks.TaskCompletionSource%601> použít objekt k zalomení operace v úkolu <xref:System.Threading.Tasks.Task> a tím získat některé výhody programovatelnosti, například podporu pro šíření výjimek a pokračování. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Vlastní plánovače

Většina vývojářů aplikací nebo knihoven se nestará o to, na kterém procesoru úloha běží, jak synchronizuje svou práci s jinými úkoly nebo jak je naplánována na rozhraní <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Vyžadují pouze to, aby byly tyto úkony v hostitelském počítači prováděny tak efektivně, jak je to možné. Pokud požadujete jemněji odstupňovanou kontrolu nad podrobnostmi plánování, Task Parallel Library umožňuje konfigurovat některá nastavení výchozího plánovače úloh a dokonce umožňuje zadat vlastní plánovač. Další informace naleznete v tématu <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Související datové struktury

TPL má několik nových veřejných typů, které jsou použitelné jak v situacích paralelního, tak i sekvenčního vykonávání. Patří mezi ně několik tříd kolekce bezpečné pro <xref:System.Collections.Concurrent?displayProperty=nameWithType> přístup z více vláken, rychlé a <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>škálovatelné v oboru názvů a několik nových typů synchronizace, například a , které jsou efektivnější než jejich předchůdci pro určité druhy úloh. Další nové typy v rozhraní .NET <xref:System.Threading.Barrier?displayProperty=nameWithType> Framework <xref:System.Threading.SpinLock?displayProperty=nameWithType>4, například a , poskytují funkce, které nebyly k dispozici v předchozích verzích. Další informace naleznete [v tématu Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Vlastní typy úkolů

Doporučujeme, abyste nedědili z <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Místo toho doporučujeme použít <xref:System.Threading.Tasks.Task.AsyncState%2A> vlastnost k přidružení dalších <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> dat nebo stavu k objektu nebo. Můžete také použít metody rozšíření rozšířit funkce <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> a třídy. Další informace o metodách rozšíření naleznete v [tématu Metody rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) a [Metody rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Pokud je nutné <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>dědit z <xref:System.Threading.Tasks.Task.Run%2A>nebo <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>nelze <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> použít , nebo třídy k vytvoření instancí vlastního typu úkolu, protože tyto mechanismy vytvářejí pouze <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty. Kromě toho nelze použít mechanismy pokračování úlohy, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>které <xref:System.Threading.Tasks.TaskFactory>jsou <xref:System.Threading.Tasks.TaskFactory%601> poskytovány , , a vytvořit instance vlastního <xref:System.Threading.Tasks.Task> typu <xref:System.Threading.Tasks.Task%601> úkolu, protože tyto mechanismy také vytvořit pouze a objekty.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-|-|
|[Řetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Popisuje, jak fungují pokračování.|
|[Připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Popisuje rozdíl mezi připojenými a odpojenými podřízenými úlohami.|
|[Zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md)|Popisuje podporu zrušení, která je <xref:System.Threading.Tasks.Task> integrována do objektu.|
|[Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Popisuje způsob zpracování výjimek v souběžných vláknech.|
|[Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Postupy: Vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Popisuje, jak z úloh vracet hodnoty.|
|[Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Popisuje, jak zrušit úlohy.|
|[Postupy: Vytváření předvypočítaných úloh](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Popisuje, jak pomocí <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody načíst výsledky asynchronní operace stahování, které jsou uloženy v mezipaměti.|
|[Postupy: Procházení binárního stromu s paralelními úlohami](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Popisuje, jak použít úlohy k procházení binárního stromu.|
|[Postupy: Rozbalení vnořené úlohy](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Ukazuje, jak používat <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metodu rozšíření.|
|[Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Popisuje, jak <xref:System.Threading.Tasks.Parallel.For%2A> používat <xref:System.Threading.Tasks.Parallel.ForEach%2A> a vytvářet paralelní smyčky přes data.|
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Uzel nejvyšší úrovně pro paralelní programování rozhraní .NET Framework.|

## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Ukázky pro paralelní programování s rozhraním .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
