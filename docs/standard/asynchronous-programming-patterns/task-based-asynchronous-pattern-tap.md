---
title: Asynchronní vzor založený na úlohách (TAP)
ms.date: 02/26/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 8cef1fcf-6f9f-417c-b21f-3fd8bac75007
ms.openlocfilehash: 89c486618729c334bf74f0a1f4f9dd1b3cee8b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158165"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (TAP)
Asynchronní vzor založený na úlohách (TAP) <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> je založen <xref:System.Threading.Tasks?displayProperty=nameWithType> na typech a v oboru názvů, které se používají k reprezentaci libovolných asynchronních operací. TAP je doporučený asynchronní návrh vzoru pro nový vývoj.  
  
## <a name="naming-parameters-and-return-types"></a>Názvy, parametry a návratové typy

TAP používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. To kontrastuje s vzorem Asynchronní programovací `IAsyncResult`model (APM nebo) a asynchronní vzor založený na událostech (EAP). APM `Begin` vyžaduje `End` a metody. Protokol EAP vyžaduje metodu, která má `Async` příponu a také vyžaduje `EventArg`jednu nebo více událostí, typy delegátů obslužné rutiny událostí a odvozené typy. Asynchronní metody v tap `Async` zahrnují příponu za názvem operace pro metody, <xref:System.Threading.Tasks.Task>které <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask>vracejí <xref:System.Threading.Tasks.ValueTask%601>počkejtelné typy, například , , a . Například asynchronní `Get` operace, která `Task<String>` vrací může `GetAsync`být pojmenována . Pokud přidáváte metodu TAP do třídy, která již obsahuje `Async` název metody EAP s `TaskAsync` příponou, použijte místo toho příponu. Například pokud třída již `GetAsync` má metodu, `GetTaskAsync`použijte název . Pokud metoda spustí asynchronní operaci, ale nevrátí očekávaný typ, jeho název `Begin` `Start`by měl začínat , , nebo jiné sloveso navrhnout, že tato metoda nevrátí nebo vyvolat výsledek operace.  
  
 Metoda TAP vrátí <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> buď <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>a nebo a , na základě toho, `TResult`zda odpovídající synchronní metoda vrátí hodnotu void nebo typ .  
  
 Parametry metody TAP by měly odpovídat parametrům jejího synchronního protějšku a měly by být uvedeny ve stejném pořadí.  Nicméně, `out` `ref` a parametry jsou vyňaty z tohoto pravidla a je třeba se zcela vyhnout. Všechna data, která by `out` byla `ref` vrácena prostřednictvím parametru `TResult` nebo, by měla být vrácena jako součást vráceného parametru <xref:System.Threading.Tasks.Task%601>a měla by použít řazenou strukturu nebo vlastní datovou strukturu pro více hodnot. Měli byste také <xref:System.Threading.CancellationToken> zvážit přidání parametru i v případě, že synchronní protějšek metody TAP nenabízí jeden.

 Metody, které jsou určeny výhradně k vytvoření, manipulaci nebo kombinaci úkolů (kde asynchronní záměr metody je jasné, v názvu metody nebo v názvu typu, ke kterému patří metoda) nemusí následovat tento vzor pojmenování; tyto metody jsou často označovány jako *kombinátory*. Příklady kombinátorů <xref:System.Threading.Tasks.Task.WhenAll%2A> zahrnují <xref:System.Threading.Tasks.Task.WhenAny%2A>a a jsou popsány v části [Using-in Task-based Combinators](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) v článku [Spotřebovává asynchronní vzor založený na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Příklady, jak se syntaxe TAP liší od syntaxe použité v starších asynchronních programovacích vzorcích, jako je asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP), naleznete [v tématu Asynchronní programovací vzory](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Zahájení asynchronní operace  
 Asynchronní metoda, která je založena na TAP, zvládne malé množství práce synchronně, například validaci argumentů a spouštění asynchronní operace před vrácením výsledné úlohy. Synchronní práce by měly být neustále udržovány na minimu, aby asynchronní metody mohly vracet rychle. Mezi důvody pro rychlý návrat patří:  
  
- Asynchronní metody mohou být vyvolány z vlákna uživatelského rozhraní (UI) a dlouhotrvající synchronní práce může mít negativní dopad na odezvu aplikace.  
  
- Je možné spustit několik asynchronních metod současně. Proto by jakékoli dlouhotrvající práce v synchronní části asynchronní metody mohly zpožďovat zahájení jiné asynchronní operace, a tím zmenšit výhody souběžnosti.  
  
 V některých případech je množství práce potřebné k dokončení operace menší než množství práce potřebné ke spuštění operace asynchronně. Příkladem takového scénáře je čtení z datového proudu, kde lze operaci čtení naplnit daty, která jsou již uložena do vyrovnávací paměti. Operace v těchto případech může být dokončena synchronně a může vrátit úlohu, která již byla dokončena.  
  
## <a name="exceptions"></a>Výjimky  
 Asynchronní metoda by měla vyvolat výjimku z volání asynchronní metody pouze jako odpověď na chybu použití. Chyby použití by se nikdy neměly objevit v produkčním kódu. Například pokud předání nulového`Nothing` odkazu (v jazyce Visual Basic) jako jeden z argumentů <xref:System.ArgumentNullException> metody způsobí chybový stav (obvykle reprezentovaný výjimkou), můžete upravit volající kód a zajistit tak, aby nikdy nebyl předán odkaz null. U všech ostatních chyb by měly být výjimky, ke kterým dochází při spuštění asynchronní metody, přiřazeny vrácené úloze i v případě, že se asynchronní metoda dokončí synchronně předtím, než je úloha vrácena. Úloha obvykle obsahuje nanejvýš jednu výjimku. Pokud však úkol představuje více operací <xref:System.Threading.Tasks.Task.WhenAll%2A>(například), může být k jednomu úkolu přidruženo více výjimek.  
  
## <a name="target-environment"></a>Cílové prostředí  
 Při implementaci metody TAP můžete určit, kde dochází k asynchronnímu spouštění. Úlohy můžete spouštět ve fondu vláken, implementovat je pomocí asynchronního I/O (bez vázání na vlákno pro většinu spuštění operace), spustit je na konkrétním vlákně (například vlákně UI) nebo použít libovolný počet potenciálních kontextů. Metoda TAP může mít ani nic ke spuštění <xref:System.Threading.Tasks.Task> a může pouze vrátit, který představuje výskyt podmínky jinde v systému (například úloha, která představuje data přicházející do struktury dat ve frontě).

 Volající metody TAP může blokovat čekání na dokončení metody TAP synchronním čekáním na výslednou úlohu nebo může spustit další (pokračování) kód po dokončení asynchronní operace. Tvůrce kódu pokračování má kontrolu nad tím, kde se spustí kód. Můžete vytvořit kód pokračování buď explicitně, <xref:System.Threading.Tasks.Task> prostřednictvím metod <xref:System.Threading.Tasks.Task.ContinueWith%2A>na třídu (například) nebo implicitně pomocí podpory `await` jazyka postavené `Await` na pokračování `AwaitValue` (například v jazyce C#, v jazyce Visual Basic, v F#).  
  
## <a name="task-status"></a>Stav úkolu  
 Třída <xref:System.Threading.Tasks.Task> poskytuje životní cyklus pro asynchronní operace a tento <xref:System.Threading.Tasks.TaskStatus> cyklus je reprezentován výčtu. Chcete-li podporovat rohové <xref:System.Threading.Tasks.Task> případy <xref:System.Threading.Tasks.Task%601>typů, které jsou odvozeny z <xref:System.Threading.Tasks.Task> a , <xref:System.Threading.Tasks.Task.Start%2A> a pro podporu oddělení konstrukce od plánování, třída zpřístupňuje metodu. Úkoly, které jsou <xref:System.Threading.Tasks.Task> vytvořeny veřejnými konstruktory, jsou označovány jako *studené úkoly*, protože začínají svůj životní cyklus v nenaplánovaném <xref:System.Threading.Tasks.TaskStatus.Created> stavu a jsou naplánovány pouze v případě, že <xref:System.Threading.Tasks.Task.Start%2A> jsou volány v těchto instancích.

 Všechny ostatní úkoly začínají svůj životní cyklus v horkém stavu, což znamená, že asynchronní operace, které <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>představují, již byly zahájeny a jejich stav úkolu je hodnota výčtu jiná než . Všechny úlohy, které jsou vráceny z metod TAP, musí být aktivovány. **Pokud metoda TAP interně používá konstruktor úlohy k vytvoření instance úlohy, která <xref:System.Threading.Tasks.Task.Start%2A> má <xref:System.Threading.Tasks.Task> být vrácena, musí metoda TAP před vrácením objektu volat.** Spotřebitelé metody TAP mohou bezpečně předpokládat, že vrácená úloha je aktivní a neměli by se pokoušet volat <xref:System.Threading.Tasks.Task.Start%2A> na všechny, <xref:System.Threading.Tasks.Task> které jsou vráceny z metody TAP. Volání <xref:System.Threading.Tasks.Task.Start%2A> aktivní úlohy má <xref:System.InvalidOperationException> za následek výjimku.  
  
## <a name="cancellation-optional"></a>Zrušení (nepovinné)  
 Pro implementátory asynchronní metody i příjemce asynchronní metody je v TAP zrušení volitelné. Pokud operace umožňuje zrušení, zpřístupní přetížení asynchronní metody, která přijímá<xref:System.Threading.CancellationToken> token zrušení (instance). Podle konvence je parametr `cancellationToken`pojmenován .  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Asynchronní operace sleduje tento token kvůli žádostem o zrušení. Pokud obdrží žádost o zrušení, může vyhovět žádosti a operaci zrušit. Pokud žádost o zrušení má za následek předčasnou práci, metoda <xref:System.Threading.Tasks.TaskStatus.Canceled> TAP vrátí úkol, který končí ve stavu; neexistuje žádný výsledek k dispozici a je vyvolána žádná výjimka.  Stát <xref:System.Threading.Tasks.TaskStatus.Canceled> je považován za konečný (dokončený) stav úkolu <xref:System.Threading.Tasks.TaskStatus.Faulted> spolu <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> se stavy a. Proto pokud je úkol <xref:System.Threading.Tasks.TaskStatus.Canceled> ve stavu, <xref:System.Threading.Tasks.Task.IsCompleted%2A> `true`jeho vlastnost vrátí . Po dokončení úkolu ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu jsou všechna pokračování registrovaná u úlohy naplánována nebo <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> provedena, pokud není zadána možnost pokračování, například odhlásit se z pokračování. Jakýkoli kód, který asynchronně čeká na zrušenou úlohu pomocí funkcí jazyka, <xref:System.OperationCanceledException> bude nadále spuštěn, ale obdrží výjimku nebo výjimku z ní odvozenou. Kód, který je blokován synchronně čekání na <xref:System.Threading.Tasks.Task.Wait%2A> úlohu prostřednictvím metod, jako je například a <xref:System.Threading.Tasks.Task.WaitAll%2A> také nadále spouštět s výjimkou.  
  
 Pokud token zrušení požádal o zrušení před metodou TAP, která přijímá tento <xref:System.Threading.Tasks.TaskStatus.Canceled> token je volána, metoda TAP by měla vrátit úkol.  Pokud je však požadováno zrušení při spuštěné asynchronní operaci, asynchronní operace nemusí přijmout žádost o zrušení.  Vrácená úloha by <xref:System.Threading.Tasks.TaskStatus.Canceled> měla končit ve stavu pouze v případě, že operace končí v důsledku požadavku na zrušení. Pokud je požadováno zrušení, ale výsledek nebo výjimka je <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> <xref:System.Threading.Tasks.TaskStatus.Faulted> stále vytvořena, úkol by měl skončit ve stavu nebo.

 Pro asynchronní metody, které chcete vystavit možnost zrušit v první řadě, není nutné poskytnout přetížení, které nepřijímá token zrušení. Pro metody, které nelze zrušit, neposkytujte přetížení, která přijímají token zrušení. To pomáhá volajícímu určit, zda je skutečně možné zrušit cílovou metodu.  Kód příjemce, který si nepřeje zrušení může <xref:System.Threading.CancellationToken> volat <xref:System.Threading.CancellationToken.None%2A> metodu, která přijímá a poskytnout jako argument hodnotu. <xref:System.Threading.CancellationToken.None%2A>je funkčně ekvivalentní <xref:System.Threading.CancellationToken>výchozímu nastavení .  
  
## <a name="progress-reporting-optional"></a>Vykazování průběhu (nepovinné)  
 Některé asynchronní operace těží z poskytování oznámení o průběhu. Ta se obvykle používají k aktualizaci uživatelského rozhraní informacemi o průběhu asynchronní operace.

 V TAP, průběh je <xref:System.IProgress%601> zpracována prostřednictvím rozhraní, který je předán asynchronní `progress`metody jako parametr, který je obvykle pojmenován .  Poskytnutí rozhraní průběhu při volání asynchronní metody pomáhá eliminovat konflikty časování, které jsou výsledkem nesprávného použití (to znamená, když obslužným rutinám, které jsou nesprávně zaregistrovány po zahájení operace, chybí aktualizace).  Důležitější je, že rozhraní průběhu podporuje různé implementace průběhu podle náročnosti kódu.  Náročný kód se bude například starat pouze o nejnovější aktualizaci průběhu nebo může chtít mít všechny aktualizace ve vyrovnávací paměti nebo může chtít vyvolat akci pro každou aktualizaci nebo může chtít řídit, zda je volání zařazeno do konkrétního vlákna. Všech těchto možností lze dosáhnout pomocí různých implementací rozhraní přizpůsobených potřebám konkrétního příjemce.  Stejně jako u zrušení by <xref:System.IProgress%601> implementace TAP měly poskytovat parametr pouze v případě, že rozhraní API podporuje oznámení o průběhu.

 Například pokud `ReadAsync` metoda popsané výše v tomto článku je schopen hlásit zprostředkující průběh ve formě počtu bajtů <xref:System.IProgress%601> číst tak daleko, zpětné volání průběhu může být rozhraní:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Pokud `FindFilesAsync` metoda vrátí seznam všech souborů, které splňují určitý vzor hledání, zpětné volání průběhu může poskytnout odhad procenta dokončené práce a aktuální sadu částečných výsledků.  To může provést buď s uspořádanou n-ticí:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 nebo s datovým typem, který je specifický pro rozhraní API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 V druhém případě je speciální datový typ obvykle `ProgressInfo`suffixed s .  
  
 Pokud tap implementace poskytují přetížení, `progress` které přijímají parametr, musí `null`povolit argument být , v takovém případě žádný pokrok budou hlášeny. Implementace TAP by měly <xref:System.Progress%601> hlásit průběh objektu synchronně, což umožňuje asynchronní metodu rychle poskytnout průběh a umožnit spotřebiteli průběhu určit, jak a kde nejlépe zpracovat informace. Například instance průběhu může zvolit zařazování zpětných volání a vyvolat události na zachyceném synchronizačním kontextu.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T> implementace  
 Rozhraní .NET Framework 4.5 <xref:System.IProgress%601> poskytuje <xref:System.Progress%601>jednu implementaci: . Třída <xref:System.Progress%601> je deklarována takto:  
  
```csharp  
public class Progress<T> : IProgress<T>  
{  
    public Progress();  
    public Progress(Action<T> handler);  
    protected virtual void OnReport(T value);  
    public event EventHandler<T> ProgressChanged;  
}  
```  
  
```vb  
Public Class Progress(Of T) : Inherits IProgress(Of T)  
    Public Sub New()  
    Public Sub New(handler As Action(Of T))  
    Protected Overridable Sub OnReport(value As T)  
    Public Event ProgressChanged As EventHandler(Of T>  
End Class  
```  
  
 Instance zpřístupňuje <xref:System.Progress%601> <xref:System.Progress%601.ProgressChanged> událost, která je vyvolána pokaždé, když asynchronní operace hlásí aktualizaci průběhu. Událost <xref:System.Progress%601.ProgressChanged> je vyvolána <xref:System.Threading.SynchronizationContext> na objekt, který <xref:System.Progress%601> byl zachycen při instance byla vytvořena instance. Pokud nebyl k dispozici žádný kontext synchronizace, je použit výchozí kontext určený pro fond vláken. Pro tuto událost lze registrovat obslužné rutiny. Jeden obslužná rutina <xref:System.Progress%601> může být také k dispozici konstruktoru pro <xref:System.Progress%601.ProgressChanged> pohodlí a chová se stejně jako obslužná rutina události pro událost. Aktualizace průběhu jsou vyvolány asynchronně, aby se předešlo zpoždění asynchronní operace, zatímco se provádějí obslužné rutiny události. Jiná <xref:System.IProgress%601> implementace by se mohla rozhodnout použít různé sémantiky.  
  
## <a name="choosing-the-overloads-to-provide"></a>Výběr přetížení, které má být poskytnuto  
 Pokud implementace TAP používá <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> volitelné <xref:System.IProgress%601> i volitelné parametry, může potenciálně vyžadovat až čtyři přetížení:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
public Task MethodNameAsync(…, IProgress<T> progress);
public Task MethodNameAsync(…,
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken cancellationToken) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task
Public MethodNameAsync(…, cancellationToken As CancellationToken,
                       progress As IProgress(Of T)) As Task  
```  
  
 Mnoho implementací TAP však neposkytuje funkce zrušení ani průběhu, takže vyžadují jedinou metodu:  
  
```csharp  
public Task MethodNameAsync(…);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
```  
  
 Pokud implementace TAP podporuje buď zrušení, nebo průběh, ale ne oboje, může poskytnout dvě přetížení:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
  
// … or …  
  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken) As Task  
  
' … or …  
  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task  
```  
  
 Pokud implementace TAP podporuje zrušení i průběh, může poskytnout všechna čtyři přetížení. Může však také poskytnout pouze dvě následující:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…,
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken,
                       progress As IProgress(Of T)) As Task  
```  
  
 Chcete-li kompenzovat dvě chybějící zprostředkující kombinace, `cancellationToken` vývojáři `null` mohou `progress` předat <xref:System.Threading.CancellationToken.None%2A> nebo výchozí <xref:System.Threading.CancellationToken> parametr a parametr.  
  
 Pokud očekáváte, že každé použití metody TAP bude podporovat zrušení nebo průběh, můžete vynechat přetížení, které nepřijímá odpovídající parametr.  
  
 Pokud se rozhodnete vystavit více přetížení, aby zrušení nebo průběh volitelné, přetížení, které nepodporují zrušení <xref:System.Threading.CancellationToken.None%2A> nebo `null` průběh by se měl chovat, jako by byly předány pro zrušení nebo pro průběh přetížení, které podporuje tyto.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Vzory asynchronního programování](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zavádí tři vzory pro provádění asynchronních operací: synchronní vzor založený na úlohách (TAP), asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP).|  
|[Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Popisuje tři způsoby implementace asynchronního vzoru založeného na úlohách (TAP): pomocí kompilátorů jazyka C# a Visual Basic v sadě Visual Studio, ručně nebo kombinací obou metod.|  
|[Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Popisuje, jak použít úlohy a zpětná volání k dosažení čekání bez blokování.|  
|[Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Popisuje způsob použití asynchronního vzoru založeného na úlohách (TAP) k implementaci asynchronního programovacího modelu (APM) a asynchronního vzoru založeného na událostech (EAP).|
