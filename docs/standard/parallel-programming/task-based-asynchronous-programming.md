---
title: Asynchronní programování založené na úlohách – .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 51292d977f2be87cec7c3481f5004fe5fe756224
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204539"
---
# <a name="task-based-asynchronous-programming"></a>Asynchronní programování založené na úlohách

Task Parallel Library (TPL) je založen na konceptu *úlohy*, která představuje asynchronní operaci. V některých způsobech se úkol podobá vláknu nebo pracovní položce <xref:System.Threading.ThreadPool>, ale na vyšší úrovni abstrakce. Pojem *úkol paralelismus* odkazuje na jednu nebo více nezávislých úloh, které jsou spuštěny souběžně. Úlohy poskytují dvě hlavní výhody:

- Větší škálovatelnost a efektivnější využívání systémových prostředků.

     Na pozadí jsou úlohy zařazené do <xref:System.Threading.ThreadPool>, což bylo vylepšené s algoritmy, které určují a upravují počet vláken, která poskytují vyrovnávání zatížení pro maximalizaci propustnosti. Díky tomu jsou úlohy relativně lehké a lze jich vytvořit mnoho, takže lze dosáhnout jemně odstupňovaného paralelismu.

- Více programového ovládání než je k dispozici s vláknem nebo pracovní položkou.

     Úlohy a architektura kolem nich vytvořená poskytují bohatou sadu rozhraní (API), která podporují čekání, zrušení, pokračování, robustní zpracování výjimek, podrobný stav, vlastní plánování a další.

Pro oba z těchto důvodů je v rozhraní .NET Framework TPL upřednostňovaným rozhraním API pro psaní vícevláknového, asynchronního a paralelního kódu.

## <a name="creating-and-running-tasks-implicitly"></a>Implicitní vytváření a spouštění úloh

Metoda <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> poskytuje pohodlný způsob, jak souběžně spustit libovolný počet libovolných příkazů. Stačí předat delegáta <xref:System.Action> pro každou položku práce. Nejsnadnější způsob, jak vytvořit tyto delegáty, je použití lambda výrazů. Lambda výraz může buďto volat pojmenovanou metodu, nebo poskytnout vložený kód. Následující příklad ukazuje základní volání <xref:System.Threading.Tasks.Parallel.Invoke%2A>, které vytvoří a spustí dvě úlohy, které běží souběžně. První úloha je reprezentována výrazem lambda, který volá metodu s názvem `DoSomeWork`a druhá úloha je reprezentována výrazem lambda, který volá metodu s názvem `DoSomeOtherWork`.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Počet instancí <xref:System.Threading.Tasks.Task>, které jsou vytvořeny na pozadí pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A>, nemusí být nutně roven počtu poskytnutých delegátů. Knihovna TPL může využít různé optimalizace, zejména s velkým počtem delegátů.

Další informace naleznete v tématu [How to: use Parallel. Invoke pro provádění paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Chcete-li získat větší kontrolu nad prováděním úloh nebo vrátit hodnotu z úkolu, je nutné pracovat s objekty <xref:System.Threading.Tasks.Task> více explicitně.

## <a name="creating-and-running-tasks-explicitly"></a>Explicitní vytváření a spouštění úloh

Úloha, která nevrací hodnotu, je reprezentována třídou <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. Úloha, která vrací hodnotu, je reprezentována třídou <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, která dědí z <xref:System.Threading.Tasks.Task>. Objekt úlohy zpracovává podrobnosti infrastruktury a poskytuje metody a vlastnosti, které jsou přístupné z volajícího vlákna po celou dobu trvání úlohy. Můžete například kdykoli přistupovat k vlastnosti <xref:System.Threading.Tasks.Task.Status%2A> úlohy a zjistit, zda byla spuštěna, dokončena, zrušena, nebo byla vyvolána výjimka. Stav je reprezentován výčtem <xref:System.Threading.Tasks.TaskStatus>.

Když je vytvořena úloha, je jí zadán uživatelský delegát, jenž provádí zapouzdření kódu, který úloha provede. Tento delegát může být vyjádřen jako pojmenovaný delegát, anonymní metoda nebo lambda výraz. Lambda výrazy mohou obsahovat volání pojmenované metody, jak ukazuje následující příklad. Všimněte si, že příklad obsahuje volání metody <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, aby bylo zajištěno, že úloha dokončí provádění před ukončením aplikace v režimu konzoly.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Můžete také použít metody <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> k vytvoření a spuštění úlohy v jedné operaci. Chcete-li spravovat úlohu, metody <xref:System.Threading.Tasks.Task.Run%2A> používají výchozí Plánovač úloh bez ohledu na to, který Plánovač úloh je přidružen k aktuálnímu vláknu. Metody <xref:System.Threading.Tasks.Task.Run%2A> jsou preferovaným způsobem, jak vytvářet a spouštět úlohy, když není potřeba větší kontrola nad vytvořením a plánováním úkolu.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Můžete také použít metodu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> k vytvoření a spuštění úlohy v jedné operaci. Tuto metodu použijte, když vytváření a plánování nemusí být odděleno a vyžadujete další možnosti vytvoření úlohy nebo použití konkrétního plánovače nebo pokud potřebujete předat další stav do úlohy, kterou můžete načíst prostřednictvím jeho <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastností, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> každé vystavení vlastnosti statického <xref:System.Threading.Tasks.Task.Factory%2A>, která vrací výchozí instanci <xref:System.Threading.Tasks.TaskFactory>, takže můžete volat metodu jako `Task.Factory.StartNew()`. Také v následujícím příkladu, protože jsou úkoly typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, mají každý z nich vlastnost Public <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>, která obsahuje výsledek výpočtu. Úlohy běží asynchronně a mohou být dokončeny v libovolném pořadí. Je-li vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> k dispozici před dokončením výpočtu, vlastnost blokuje volající vlákno, dokud nebude hodnota k dispozici.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Další informace najdete v tématu [Postupy: vrácení hodnoty z úkolu](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Při použití lambda výrazu k vytvoření delegáta máte přístup ke všem proměnným, které jsou v daném okamžiku viditelné ve zdrojovém kódu. V některých případech, zejména v rámci smyčky, však lambda nezachytí proměnnou podle očekávání. Pouze zachycuje konečnou hodnotu, nikoli mutaci hodnoty po každé iteraci. Následující příklad ukazuje tento problém. Předá do výrazu lambda výraz, který vytvoří instanci objektu `CustomData` a použije počítadlo smyčky jako identifikátoru objektu. Jak výstup z příkladu ukazuje, každý objekt `CustomData` má stejný identifikátor.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

K hodnotě v každé iteraci můžete přistupovat zadáním objektu stavu úlohy pomocí jeho konstruktoru. Následující příklad upravuje předchozí příklad pomocí čítače smyčky při vytváření objektu `CustomData`, který je zase předán výrazu lambda.  Jak výstup z příkladu ukazuje, každý objekt `CustomData` nyní má jedinečný identifikátor na základě hodnoty čítače smyčky v době, kdy byla vytvořena instance objektu.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Tento stav je předán jako argument delegátu úlohy a lze k němu přistupovat z objektu úlohy pomocí vlastnosti <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>.  Následující příklad je podobný předchozímu příkladu. Používá vlastnost <xref:System.Threading.Tasks.Task.AsyncState%2A> k zobrazení informací o objektech `CustomData` předaných do výrazu lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>ID úkolu

Každý úkol obdrží celočíselný identifikátor ID, který ji jednoznačně identifikuje v doméně aplikace a je k němu možné přistupovat pomocí vlastnosti <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType>. ID je užitečné pro zobrazení informací o úloze v oknech **paralelní zásobníky** a **úlohy** ladicího programu sady Visual Studio. ID využívá líné vytváření, což znamená, že není vytvořeno, dokud se o něj nepožádá, proto může mít úloha při každém spuštění programu jiné ID. Další informace o tom, jak zobrazit ID úloh v ladicím programu, najdete v tématu [použití okna úlohy](/visualstudio/debugger/using-the-tasks-window) a [použití okna Paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Možnosti vytvoření úlohy

Většina rozhraní API, která vytvářejí úlohy, poskytují přetížení, která přijímají parametr <xref:System.Threading.Tasks.TaskCreationOptions>. Zadáním jedné z těchto možností lze dát pokyn plánovači úloh, jak naplánovat úlohy ve fondu vláken. V následující tabulce jsou uvedeny různé možnosti pro vytváření úloh.

|hodnota parametru <xref:System.Threading.Tasks.TaskCreationOptions>|Popis|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Výchozí hodnota, pokud není zadána jiná. Plánovač používá k plánování úlohy své výchozí heuristické metody.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Určuje, že úlohy by měly být naplánovány tak, aby se úlohy vytvořené dříve pravděpodobně prováděly dříve a později vytvořené úlohy aby se s větší pravděpodobností prováděly později.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Určuje, že úloha představuje dlouhotrvající operaci.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Určuje, že úloha by měla být vytvořena jako připojená podřízená úloha aktuální úlohy, pokud existuje. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Určuje, že pokud vnitřní úloha Určuje možnost `AttachedToParent`, tato úloha se nestane připojenou podřízenou úlohou.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Určuje, že Plánovač úloh pro úlohy vytvořené voláním metod, jako je <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> z konkrétního úkolu, je výchozím plánovačem namísto plánovače, na kterém je tato úloha spuštěná.|

Možnosti lze kombinovat pomocí bitové operace **nebo** . Následující příklad ukazuje úlohu s možností <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness>.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Úlohy, vlákna a jazyková verze

Každé vlákno má přidruženou jazykovou verzi a jazykovou verzi uživatelského rozhraní, které je definováno <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> vlastností, v uvedeném pořadí. Jazyková verze vlákna se v takových operacích používá jako formátování, analýza, řazení a porovnávání řetězců. Jazyková verze uživatelského rozhraní vlákna se používá při vyhledávání prostředků. Pokud nezadáte výchozí jazykovou verzi pro všechna vlákna v doméně aplikace pomocí vlastností <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType>, je výchozí jazyková verze a jazyková verze uživatelského rozhraní definovaná jazykovou verzí systému. Pokud jste explicitně nastavili jazykovou verzi vlákna a spustili nové vlákno, nové vlákno nedědí jazykovou verzi volajícího vlákna; místo toho je jeho jazyková verze výchozí jazyková verze systému. Programovací model založený na úlohách pro aplikace, které cílí na verze .NET Framework před .NET Framework 4,6 v souladu s tímto postupem.

> [!IMPORTANT]
> Všimněte si, že jazyková verze volajícího vlákna je v rámci kontextu úlohy platná pro aplikace, které *cílí* na .NET Framework 4,6, ne aplikace, které *běží pod* .NET Framework 4,6. Můžete cílit na konkrétní verzi .NET Framework při vytváření projektu v aplikaci Visual Studio výběrem této verze z rozevíracího seznamu v horní části dialogového okna **Nový projekt** nebo mimo sadu Visual Studio můžete použít atribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute>. Pro aplikace, které cílí na verze .NET Framework před .NET Framework 4,6 nebo které necílí na konkrétní verzi .NET Framework, je jazyková verze úlohy i nadále určena kulturou vlákna, na které běží.

Počínaje aplikacemi, které cílí na .NET Framework 4,6, je jazyková verze volajícího vlákna zděděna každou úlohou, a to i v případě, že se úloha spouští asynchronně ve vlákně fondu vláken.

Následující příklad poskytuje jednoduchý obrázek. Používá atribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute> k cílení na .NET Framework 4,6 a změní aktuální jazykovou verzi aplikace na francouzštinu (Francie) nebo, pokud francouzština (Francie) je již aktuální jazykovou verzí, anglickou (USA). Poté vyvolá delegáta s názvem `formatDelegate`, který vrátí čísla formátovaná jako hodnoty měny v nové jazykové verzi. Všimněte si, zda delegát jako úkol buď synchronně, nebo asynchronně, vrátí očekávaný výsledek, protože jazyková verze volajícího vlákna je zděděna asynchronním úkolem.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Pokud používáte aplikaci Visual Studio, můžete vynechat atribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute> a místo toho vybrat .NET Framework 4,6 jako cíl při vytváření projektu v dialogovém okně **Nový projekt** .

Pro výstup, který odráží chování aplikací cílové verze .NET Framework před .NET Framework 4,6, odeberte atribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ze zdrojového kódu. Výstup bude odpovídat konvencím formátování výchozí jazykové verze systému, nikoli jazykové verzi volajícího vlákna.

Další informace o asynchronních úlohách a jazykové verzi naleznete v části "jazyková verze a asynchronní operace založené na úlohách" v tématu <xref:System.Globalization.CultureInfo>.

## <a name="creating-task-continuations"></a>Vytváření pokračování úlohy

Metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> umožňují určit úlohu, která se spustí po dokončení *předchozí úlohy* . Delegátem úlohy pokračování je předán odkaz na předchozí úlohu, aby mohl prověřit stav předchozí úlohy a načtením hodnoty vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> může použít výstup předchůdce jako vstup pro pokračování.

V následujícím příkladu je úloha `getData` spuštěna voláním metody <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType>. Úloha `processData` se spustí automaticky po dokončení `getData` a po dokončení `processData` se spustí `displayData`. `getData` vytváří celočíselné pole, které je přístupné `processData` úloze prostřednictvím vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> úkolu `getData`. Úloha `processData` zpracuje toto pole a vrátí výsledek, jehož typ je odvozen z návratového typu výrazu lambda, který byl předán metodě <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType>. Úloha `displayData` se spustí automaticky po dokončení `processData` a objekt <xref:System.Tuple%603> vrácený `processData` výraz lambda je přístupný `displayData` úloze prostřednictvím vlastnosti `processData` úkolu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>. Úloha `displayData` přebírá výsledek úlohy `processData` a vytváří výsledek, jehož typ je odvozen podobným způsobem a který je zpřístupněn programu ve vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A>.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Vzhledem k tomu, že <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> je metoda instance, můžete zřetězit volání metody společně namísto vytvoření instance <xref:System.Threading.Tasks.Task%601> objektu pro každou předchozí úlohu. Následující příklad je funkčně totožný s předchozím příkladem, s tím rozdílem, že řetězí volání metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Všimněte si, že objekt <xref:System.Threading.Tasks.Task%601> vrácený řetězcem volání metody je konečný úkol pokračování.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> umožňují pokračovat z více úloh.

Další informace najdete v tématu [zřetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Vytváření odpojených podřízených úloh

Když uživatelský kód, který běží v rámci úlohy, vytvoří novou úlohu a neurčí možnost <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>, není nová úloha žádným zvláštním způsobem synchronizována s nadřazenou úlohou. Tento typ nesynchronizované úlohy se nazývá *odpojená vnořená úloha* nebo *odpojená podřízená úloha*. Následující příklad zobrazuje úlohu, která vytváří jednu odpojenou podřízenou úlohu.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Nadřazená úloha nečeká na dokončení odpojené podřízené úlohy.

## <a name="creating-child-tasks"></a>Vytváření podřízených úloh

Když uživatelský kód, který běží v rámci úlohy, vytvoří úlohu s možností <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>, je nová úloha známá jako *připojená podřízená úloha* nadřazené úlohy. Možnost <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> můžete použít k vyjádření strukturovaného paralelismu úloh, protože nadřazená úloha implicitně čeká na dokončení všech připojených podřízených úloh. Následující příklad zobrazuje nadřazenou úlohu, která vytvoří deset připojených podřízených úloh. Všimněte si, že přestože příklad volá metodu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pro čekání na dokončení nadřazené úlohy, nemusí explicitně čekat na dokončení připojených podřízených úloh.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Nadřazený úkol může použít možnost <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, aby se zabránilo připojení jiných úloh k nadřazené úloze. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Čeká se na dokončení úloh.

Typy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> poskytují několik přetížení <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>ch metod, které umožňují počkat na dokončení úlohy. Kromě toho přetížení statických <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> a metod <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> umožňují počkat na dokončení všech nebo všech polí úkolů.

Obvykle se na úlohu čeká z některého z těchto důvodů:

- Hlavní vlákno závisí na konečném výsledku vypočítaném úlohou.

- Je potřeba zpracovat výjimky, které mohou být vyvolány z úlohy.

- Aplikace se může ukončit předtím, než se dokončí všechny úlohy. Například konzolové aplikace budou ukončeny co nejdříve po provedení veškerého synchronního kódu v `Main` (vstupní bod aplikace).

Následující příklad zobrazuje základní vzor, který nezahrnuje zpracování výjimek.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Příklad zobrazující zpracování výjimek naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Některá přetížení umožňují určit časový limit a jiné <xref:System.Threading.CancellationToken> jako vstupní parametr, aby bylo možné samotné čekání zrušit buď programově, nebo jako odpověď na uživatelský vstup.

Při čekání na úlohu se implicitně čeká na všechny podřízené položky této úlohy, které byly vytvořeny pomocí možnosti <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> vrátí hodnotu okamžitě, pokud úloha již byla dokončena. Jakékoli výjimky vyvolané úlohou budou vyvolány metodou <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, a to i v případě, že byla metoda <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> volána po dokončení úlohy.

## <a name="composing-tasks"></a>Vytváření úloh

Třídy <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> poskytují několik metod, které vám pomohou vytvořit více úkolů pro implementaci běžných vzorů a lépe využívat funkce asynchronního jazyka, které jsou k C#dispozici v, F#Visual Basic a. Tato část popisuje metody <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>a <xref:System.Threading.Tasks.Task.FromResult%2A>.

### <a name="taskwhenall"></a>Task.WhenAll

Metoda <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> asynchronně čeká na dokončení více objektů <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Poskytuje přetížené verze, které umožňují čekání na nerovnoměrné sady úloh. Můžete například počkat na dokončení více <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objektů z jednoho volání metody.

### <a name="taskwhenany"></a>Task.WhenAny

Metoda <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> asynchronně čeká na dokončení jednoho z více objektů <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Stejně jako v metodě <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> poskytuje tato metoda přetížené verze, které umožňují počkat na nejednotné sady úloh. Metoda <xref:System.Threading.Tasks.Task.WhenAny%2A> je obzvláště užitečná v následujících scénářích.

- Nadbytečné operace. Zvažte algoritmus nebo operaci, které lze provést mnoha způsoby. Můžete použít metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> k výběru operace, která skončí jako první, a pak zrušit zbývající operace.

- Prokládané operace. Můžete spustit více operací, které se musí dokončit, a použít metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> ke zpracování výsledků při dokončení každé operace. Po dokončení jedné operace můžete spustit jednu nebo více dalších úloh.

- Omezené operace. Můžete použít metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> k prodloužení předchozího scénáře tím, že omezíte počet souběžných operací.

- Operace, jejichž platnost vypršela. Můžete použít metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> k výběru jedné nebo více úloh a úlohy, která skončí po určitou dobu, například úlohy, která je vrácena metodou <xref:System.Threading.Tasks.Task.Delay%2A>. <xref:System.Threading.Tasks.Task.Delay%2A> metoda je popsána v následující části.

### <a name="taskdelay"></a>Task.Delay

Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> vytvoří objekt <xref:System.Threading.Tasks.Task>, který skončí po specifikovaném čase. Tuto metodu můžete použít k vytvoření cyklů, které občas provádějí dotazování na data, zavedení limitů, zpracování vstupu uživatele na předem stanovenou dobu zpoždění a tak dále.

### <a name="tasktfromresult"></a>Task(T).FromResult

Pomocí metody <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> můžete vytvořit objekt <xref:System.Threading.Tasks.Task%601>, který obsahuje předem vypočítaný výsledek. Tato metoda je užitečná při provádění asynchronní operace, která vrací objekt <xref:System.Threading.Tasks.Task%601> a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán. Příklad, který používá <xref:System.Threading.Tasks.Task.FromResult%2A> k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti, naleznete v tématu [How to: Create předběžně počítané úkoly](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Zpracování výjimek v úlohách

Pokud úkol vyvolá jednu nebo více výjimek, výjimky jsou zabaleny do výjimky <xref:System.AggregateException>. Tato výjimka je šířena zpět do vlákna, které se spojí s úlohou, což je obvykle vlákno, které čeká na dokončení úlohy nebo vlákno, které přistupuje k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A>. Toto chování slouží k vynucení, aby při všech neošetřených výjimkách ve výchozím nastavení zásady rozhraní .NET Framework ukončily proces. Volající kód může zpracovávat výjimky pomocí kterékoli z následujících v `try`/blok `catch`:

- Metoda <xref:System.Threading.Tasks.Task.Wait%2A>

- Metoda <xref:System.Threading.Tasks.Task.WaitAll%2A>

- Metoda <xref:System.Threading.Tasks.Task.WaitAny%2A>

- Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A>

Spojovací vlákno může také zpracovávat výjimky přístupem k vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> dříve, než je úloha uvolněna z paměti. Přístupem k této vlastnosti nebude nezpracovaná výjimka spouštět chování šíření výjimky, které ukončí proces, když je objekt finalizován.

Další informace o výjimkách a úlohách naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Rušení úloh

Třída <xref:System.Threading.Tasks.Task> podporuje kooperativní zrušení a je plně integrovaná s <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> a <xref:System.Threading.CancellationToken?displayProperty=nameWithType>mi třídami, které byly představeny v .NET Framework 4. Mnoho konstruktorů ve třídě <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> převezme objekt <xref:System.Threading.CancellationToken> jako vstupní parametr. Mnoho z <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> a <xref:System.Threading.Tasks.Task.Run%2A> přetížení také zahrnuje parametr <xref:System.Threading.CancellationToken>.

Můžete vytvořit token a vystavit žádost o zrušení později pomocí třídy <xref:System.Threading.CancellationTokenSource>. Předání tokenu <xref:System.Threading.Tasks.Task> jako argumentu a také odkazování na stejný token v uživatelském delegátu, který provádí reakci na žádost o zrušení.

Další informace naleznete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [Postup: zrušení úlohy a jejích podřízených objektů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Třída TaskFactory

Třída <xref:System.Threading.Tasks.TaskFactory> poskytuje statické metody, které zapouzdřují některé běžné vzory pro vytváření a spouštění úloh a pokračujících úloh.

- Nejběžnějším vzorem je <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, který vytvoří a spustí úlohu v jednom příkazu.

- Při vytváření pokračujících úloh z více předchůdců použijte metodu <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> nebo metodu <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> nebo jejich ekvivalenty ve třídě <xref:System.Threading.Tasks.Task%601>. Další informace najdete v tématu [zřetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Pro zapouzdření asynchronního programovacího modelu `BeginX` a `EndX` metody v instanci <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> použijte metody <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A>. Další informace naleznete v tématu [TPL a tradiční .NET Framework asynchronní programování](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Výchozí <xref:System.Threading.Tasks.TaskFactory> může být k dispozici jako statická vlastnost třídy <xref:System.Threading.Tasks.Task> nebo třídy <xref:System.Threading.Tasks.Task%601>. Můžete také vytvořit instanci <xref:System.Threading.Tasks.TaskFactory> přímo a určit různé možnosti, které zahrnují <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> možnost, <xref:System.Threading.Tasks.TaskContinuationOptions> možnost nebo <xref:System.Threading.Tasks.TaskScheduler>. Jakékoli možnosti, které jsou zadány při vytváření továrny úloh, budou použity pro všechny úlohy, které vytvoří, pokud se <xref:System.Threading.Tasks.Task> nevytvoří pomocí výčtu <xref:System.Threading.Tasks.TaskCreationOptions>, v takovém případě možnosti úlohy přepíší tyto továrny úloh.

## <a name="tasks-without-delegates"></a>Úlohy bez delegátů

V některých případech můžete chtít použít <xref:System.Threading.Tasks.Task> k zapouzdření některé asynchronní operace, kterou provádí externí komponenta namísto uživatelského delegáta. Pokud je operace založena na vzoru Begin/End modelu asynchronního programování, můžete použít metody <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A>. V takovém případě můžete použít objekt <xref:System.Threading.Tasks.TaskCompletionSource%601> k zabalení operace do úlohy a získat tak některé z výhod <xref:System.Threading.Tasks.Task> programovatelnosti, například podporu pro šíření výjimek a pokračování. Další informace najdete v tématu <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Vlastní plánovače

Většina vývojářů aplikací nebo knihoven nezáleží na tom, na kterém procesoru je úloha spuštěna, jak synchronizuje svou práci s ostatními úkoly nebo jak je naplánována na <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Vyžadují pouze to, aby byly tyto úkony v hostitelském počítači prováděny tak efektivně, jak je to možné. Pokud požadujete jemněji odstupňovanou kontrolu nad podrobnostmi plánování, Task Parallel Library umožňuje konfigurovat některá nastavení výchozího plánovače úloh a dokonce umožňuje zadat vlastní plánovač. Další informace najdete v tématu <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Související datové struktury

TPL má několik nových veřejných typů, které jsou použitelné jak v situacích paralelního, tak i sekvenčního vykonávání. Mezi ně patří několik bezpečných a škálovatelných tříd kolekcí v oboru názvů <xref:System.Collections.Concurrent?displayProperty=nameWithType> a několik nových typů synchronizace, například <xref:System.Threading.Semaphore?displayProperty=nameWithType> a <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, které jsou efektivnější než jejich předchůdci pro konkrétní druhy úloh. Další nové typy v .NET Framework 4, například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.SpinLock?displayProperty=nameWithType>, poskytují funkce, které v dřívějších verzích nebyly k dispozici. Další informace najdete v tématu [datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Vlastní typy úloh

Doporučujeme Nedědit z <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ani <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Místo toho doporučujeme použít vlastnost <xref:System.Threading.Tasks.Task.AsyncState%2A> k přidružení dalších dat nebo stavu k objektu <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Můžete také použít rozšiřující metody k rozšíření funkcí <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> třídy. Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) a [metody rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Pokud musíte dědit z <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, nemůžete použít <xref:System.Threading.Tasks.Task.Run%2A>nebo třídy <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>nebo <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> k vytvoření instancí vlastního typu úkolu, protože tyto mechanismy vytvářejí pouze <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty. Kromě toho nemůžete použít mechanismy pokračování úloh, které jsou k dispozici <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>a <xref:System.Threading.Tasks.TaskFactory%601> k vytvoření instancí vlastního typu úkolu, protože tyto mechanismy také vytváří pouze <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty.

## <a name="related-topics"></a>Příbuzná témata

|Název|Popis|
|-|-|
|[Řetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Popisuje, jak fungují pokračování.|
|[Připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Popisuje rozdíl mezi připojenými a odpojenými podřízenými úlohami.|
|[Zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md)|Popisuje podporu zrušení, která je integrována do objektu <xref:System.Threading.Tasks.Task>.|
|[Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Popisuje způsob zpracování výjimek v souběžných vláknech.|
|[Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Popisuje, jak používat <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Postupy: Vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Popisuje, jak z úloh vracet hodnoty.|
|[Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Popisuje, jak zrušit úlohy.|
|[Postupy: Vytváření předvypočítaných úloh](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Popisuje, jak použít metodu <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti.|
|[Postupy: Procházení binárního stromu s paralelními úlohami](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Popisuje, jak použít úlohy k procházení binárního stromu.|
|[Postupy: Rozbalení vnořené úlohy](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Ukazuje, jak použít metodu rozšíření <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.|
|[Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Popisuje, jak pomocí <xref:System.Threading.Tasks.Parallel.For%2A> a <xref:System.Threading.Tasks.Parallel.ForEach%2A> vytvořit paralelní smyčky pro data.|
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Uzel nejvyšší úrovně pro paralelní programování rozhraní .NET Framework.|

## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Ukázky pro paralelní programování s .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
