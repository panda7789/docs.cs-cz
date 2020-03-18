---
title: Implementace asynchronního vzoru založeného na úlohách
ms.date: 06/14/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: fab6bd41-91bd-44ad-86f9-d8319988aa78
ms.openlocfilehash: 6218aa1a7b813601e9b718abf862e20a7cbcd313
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124305"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementace asynchronního vzoru založeného na úlohách
Asynchronní vzor založený na úkolech (TAP) můžete implementovat třemi způsoby: pomocí kompilátorů jazyka C# a Visual Basic v sadě Visual Studio, ručně nebo kombinací obou metod. Jednotlivé metody jsou podrobně popsány v následujících částech. Vzor TAP můžete použít k implementaci asynchronních operací vázaných na výpočetní prostředky i vstupně-výstupních operací. Pracovní [zatížení](#workloads) části popisuje každý typ operace.

## <a name="generating-tap-methods"></a>Generování metod TAP

### <a name="using-the-compilers"></a>Použití kompilátorů
Počínaje rozhraním .NET Framework 4.5 je jakákoli `async` metoda, která je přiřazena klíčovému slovu (`Async` v jazyce Visual Basic, považována za asynchronní metodu a kompilátory jazyka C# a Visual Basic provádějí nezbytné transformace k implementaci metody asynchronně pomocí tap. Asynchronní metoda by měla vrátit buď objekt <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, nebo objekt <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Pro druhé tělo funkce by měla `TResult`vrátit a , a kompilátor zajišťuje, že tento výsledek je k dispozici prostřednictvím výsledné ho task object. Stejně tak veškeré výjimky, které nejsou zpracovány v těle metody, jsou zařazeny do výstupního úkolu, což způsobí, že výsledný úkol bude ukončen ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>. Výjimkou je situace, kdy není zpracována výjimka typu <xref:System.OperationCanceledException> (nebo odvozeného typu). V takovém případě skončí výsledný úkol ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.

### <a name="generating-tap-methods-manually"></a>Ruční generování metod TAP
Vzor TAP můžete implementovat ručně a dosáhnout tak lepší kontroly nad implementací. Kompilátor spoléhá na veřejnou oblast vystavenou z oboru názvů <xref:System.Threading.Tasks?displayProperty=nameWithType> s podporou typů v oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Při vlastní implementaci vzoru TAP vytvoříte objekt <xref:System.Threading.Tasks.TaskCompletionSource%601>, provedete asynchronní operaci a po jejím dokončení zavoláte metodu <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> nebo <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> anebo verzi `Try` jedné z těchto metod. Při ruční implementaci metody TAP musíte dokončit výsledný úkol po dokončení zastoupené asynchronní operace. Například:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Hybridní přístup
 Pravděpodobně pro vás bude užitečné, pokud implementujete vzor TAP ručně, ale delegujete základní logiku pro implementaci na kompilátor. Hybridní přístup budete pravděpodobně uplatňovat při ověřování argumentů mimo kompilátorem generovanou asynchronní metodu tak, aby výjimky mohly namísto vystavení prostřednictvím objektu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> uniknout přímému volajícímu metody:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Dalším užitečným použitím takového delegování je implementace optimalizace rychlé cesty a vrácení úkolu v mezipaměti.

## <a name="workloads"></a>Úlohy
Jako metody TAP lze implementovat výpočetní i vstupně-výstupní asynchronní operace. Jsou-li však metody TAP vystaveny veřejně z knihovny, měly by být poskytnuty pouze pro úkoly, které se týkají vstupně-výstupních operací (mohou také zahrnovat výpočet, ale neměly by být čistě výpočetní). Pokud je metoda čistě vázána na výpočetní prostředky, měla by být vystavena pouze jako synchronní implementace. Kód, který spotřebovává to pak může zvolit, zda zabalit vyvolání této synchronní metody do úkolu převést práci do jiného vlákna nebo k dosažení paralelismu. A pokud je metoda vázána na vstupně-výstupní informace, měla by být vystavena pouze jako asynchronní implementace.

### <a name="compute-bound-tasks"></a>Úlohy vázané na výpočetní výkon
Třída <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> je nejvhodnější pro zastoupení výpočetně náročných operací. Ve výchozím nastavení využívá speciální podporu v rámci třídy <xref:System.Threading.ThreadPool> za účelem poskytování účinného provádění a zároveň poskytuje významnou kontrolu nad tím, kdy, kde a jakým způsobem lze provádět asynchronní výpočty.

Úlohy vázané na výpočetní výkon můžete generovat následujícími způsoby:

- V rozhraní .NET Framework 4 použijte metodu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, jež přijímá delegát (obvykle typu <xref:System.Action%601> nebo <xref:System.Func%601>), který se provádí asynchronně. Pokud poskytnete delegát typu <xref:System.Action%601>, vrátí metoda objekt <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, který představuje asynchronní provádění tohoto delegátu. Pokud zadáte delegát typu <xref:System.Func%601>, vrátí metoda objekt <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Přetížení metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> přijímá token zrušení (<xref:System.Threading.CancellationToken>), možnosti vytvoření úkolu (<xref:System.Threading.Tasks.TaskCreationOptions>) a plánovač úkolů (<xref:System.Threading.Tasks.TaskScheduler>), které poskytují detailní kontrolu nad plánováním a prováděním úkolu. Instance objektu pro vytváření úkolů, která je určena pro aktuální plánovač úkolů, je k dispozici jako statická vlastnost (<xref:System.Threading.Tasks.Task.Factory%2A>) třídy <xref:System.Threading.Tasks.Task>, například `Task.Factory.StartNew(…)`.

- V rozhraní .NET Framework 4.5 a novějších verzích (včetně .NET Core a .NET Standard) použijte statickou <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodu jako zástupce aplikace <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Metodu <xref:System.Threading.Tasks.Task.Run%2A> můžete použít pro snadné spouštění výpočetního úkolu, který se zaměřuje na fond vláken. V rozhraní .NET Framework 4.5 a novějších verzích je to toto upřednostňovaný mechanismus pro spuštění úlohy vázané na výpočetní výkon. Přímo `StartNew` používejte pouze v případě, že chcete mít nad úkolem větší kontrolu.

- Pokud chcete generovat a plánovat úkol samostatně, použijte konstruktory typu `Task` nebo metodu `Start`. Veřejné metody smí vracet pouze úkoly, které již byly zahájeny.

- Použijte přetížení metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Tato metoda vytvoří nový úkol, jehož spuštění je naplánováno po dokončení jiného úkolu. Některá přetížení <xref:System.Threading.Tasks.Task.ContinueWith%2A> přijímají token zrušení, možnosti pokračování a plánovač úkolů pro lepší kontrolu nad plánováním a prováděním úkolu pokračování.

- Použijte <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> a. Tyto metody vytvoří nový úkol, který je naplánován na dobu, kdy skončí všechny nebo libovolná zadaná sada úkolů. Tyto metody také poskytují přetížení pro řízení plánování a provádění těchto úkolů.

V případě výpočetních úkolů může systém zabránit spuštění naplánovaného úkolu, pokud obdrží požadavek na zrušení před spuštěním úkolu. Pokud je takto poskytován token zrušení (<xref:System.Threading.CancellationToken>), můžete tento token předat asynchronnímu kódu, který tento token sleduje. Token můžete také poskytnout jedné z výše uvedených metod, jako je `StartNew` nebo `Run`, aby modul runtime typu `Task` mohl tento token také sledovat.

Zvažte například asynchronní metodu, která vytváří obrázek. Tělo úkolu může dotazovat token zrušení tak, aby se kód mohl předčasně ukončit, pokud bude požadavek na zrušení doručen během vykreslování. Pokud bude navíc požadavek na zrušení doručen před spuštěním vykreslování, budete chtít zabránit operaci vykreslování:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Výpočetní úkoly skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>, pokud je splněna alespoň jedna z následujících podmínek:

- Dříve než úkol přejde do stavu <xref:System.Threading.CancellationToken>, je požadavek na zrušení doručen prostřednictvím objektu `StartNew`, který je k dispozici ve formě argumentu metody vytváření (například metody `Run` nebo <xref:System.Threading.Tasks.TaskStatus.Running>).

- Výjimka <xref:System.OperationCanceledException> zůstane v těle takového úkolu nezpracovaná. Tato výjimka obsahuje stejný token <xref:System.Threading.CancellationToken>, který je předán úkolu. Tento token dokazuje, že je požadováno zrušení.

Pokud uvnitř těla úkolu zůstane další nezpracovaná výjimka, skončí tento úkol ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted> a pokusy o čekání na úkol nebo přístup k výsledku úkolu způsobí vyvolání výjimky.

### <a name="io-bound-tasks"></a>I/V-vázané úkoly
Chcete-li vytvořit úkol, pro který by po celou dobu provádění nemělo existovat podkladové vlákno, použijte typ <xref:System.Threading.Tasks.TaskCompletionSource%601>. Tento typ vystavuje vlastnost <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A>, která vrací přidruženou instanci typu <xref:System.Threading.Tasks.Task%601>. Životní cyklus tohoto úkolu je řízen metodami typu <xref:System.Threading.Tasks.TaskCompletionSource%601>, jako jsou <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>, a jejich variantami `TrySet`.

Předpokládejte, že chcete vytvořit úkol, který bude dokončen po určitém časovém období. Například budete chtít odložit aktivitu v uživatelském rozhraní na pozdější dobu. Třída <xref:System.Threading.Timer?displayProperty=nameWithType> již poskytuje schopnost asynchronního vyvolání delegátu po zadaném časovém intervalu a pomocí typu <xref:System.Threading.Tasks.TaskCompletionSource%601> lze umístit typ <xref:System.Threading.Tasks.Task%601> před časovač, například:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Počínaje rozhraním .NET Framework 4.5 je <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda k dispozici pro tento účel a můžete ji použít uvnitř jiné asynchronní metody, například k implementaci asynchronní smyčky dotazování:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

Třída <xref:System.Threading.Tasks.TaskCompletionSource%601> nemá neobecný protějšek. Typ <xref:System.Threading.Tasks.Task%601> je však odvozen od typu <xref:System.Threading.Tasks.Task>, takže obecný objekt <xref:System.Threading.Tasks.TaskCompletionSource%601> můžete použít pro vstupně-výstupní metody, které jednoduše vrátí úkol. Chcete-li tuto operaci provést, můžete použít prostředek s fiktivním typem `TResult` (<xref:System.Boolean> je dobrá výchozí volba, ale pokud se obáváte, že uživatel typu <xref:System.Threading.Tasks.Task> ji bude přetypovávat dolů na typ <xref:System.Threading.Tasks.Task%601>, lze namísto toho použít privátní typ `TResult`). Například metoda `Delay` v předchozím příkladu vrátí aktuální čas s výsledným posunem (`Task<DateTimeOffset>`). Pokud je výsledná hodnota nepotřebná, může být metoda kódována spíše takto (všimněte si změny návratového typu a změny argumentu na hodnotu <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Smíšené úlohy vázané na výpočetní výkon a vstupně-výstupní úkoly
Asynchronní metody nejsou omezeny pouze na výpočetní nebo vstupně-výstupní operace, ale mohou představovat kombinaci obou metod. Ve skutečnosti je větší počet asynchronních operací často sloučen do větších smíšených operací. Například metoda `RenderAsync` v předchozím příkladu provedla výpočetně náročnou operaci za účelem vykreslení obrázku na základě vstupu proměnné `imageData`. Zdrojem této proměnné `imageData` může být webová služba s asynchronním přístupem:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Tento příklad také znázorňuje, jakým způsobem lze jeden token zrušení zřetězit prostřednictvím několika asynchronních operací. Další informace naleznete v části využití zrušení v [tématu Náročné asynchronní vzor založené na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
