---
title: "Asynchronní vzor založený na úlohách (TAP)"
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
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 8cef1fcf-6f9f-417c-b21f-3fd8bac75007
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d195cc046ad7ea50cd3695ef32bf53be75c387da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (TAP)
Založený na úlohách asynchronní vzor (TAP) je založena na <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy v <xref:System.Threading.Tasks?displayProperty=nameWithType> obor názvů, které se používají k vyjádření libovolný asynchronní operace. TAP je doporučený asynchronní návrh vzoru pro nový vývoj.  
  
## <a name="naming-parameters-and-return-types"></a>Pojmenování, parametry a návratové typy  
 TAP používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. Tím se liší od modelu asynchronního programování (APM nebo `IAsyncResult`) vzor, který vyžaduje `Begin` a `End` metody a na rozdíl od se na základě událostí asynchronním vzorem (EAP), což vyžaduje, aby metoda, která má `Async`přípona a také vyžaduje jeden nebo více událostí, typy delegáta obslužných rutin událostí, a `EventArg`-odvozených typů. Zahrnout asynchronních metod v klepněte na `Async` příponu po název operace; například `GetAsync` pro `Get` operaci. Pokud přidáváte metoda klepněte na třídu, která již obsahuje název této metody se `Async` přípona, použijte příponu `TaskAsync` místo. Například, pokud třída již `GetAsync` metoda, použijte název `GetTaskAsync`.  
  
 Vrátí metoda klepněte buď <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, závislosti na tom, jestli odpovídající synchronní metoda vrátí hodnotu typu void nebo typ `TResult`.  
  
 Parametry metody TAP by měly odpovídat parametrům jejího synchronního protějšku a měly by být ve stejném pořadí.  Ale `out` a `ref` parametrů se vyloučí z tohoto pravidla a je nutno zcela. Všechna data, která by byly vráceny prostřednictvím `out` nebo `ref` parametru by měla být vrácena místo jako součást `TResult` vrácený <xref:System.Threading.Tasks.Task%601>a měli použít řazenou kolekci členů nebo vlastní datovou strukturu pro přizpůsobení více hodnot. Metody, které jsou odeberte výhradně pro vytvoření, manipulaci nebo kombinace úlohy (kde záměr asynchronní metody je jasné, v názvu metody nebo název typu, do které patří metodu) nemusí postupujte podle tohoto vzoru pro pojmenovávání; Tyto metody jsou často označovány jako *combinators*. Příklady combinators <xref:System.Threading.Tasks.Task.WhenAll%2A> a <xref:System.Threading.Tasks.Task.WhenAny%2A>a jsou popsané v [pomocí Combinators na základě integrovanou úlohu](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) části článku [použití asynchronního vzoruzaloženýnaúlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Příklady, jak se liší od syntaxe používá starší verze asynchronní programování vzory například asynchronní programování modelu (APM) a na základě událostí asynchronní vzor (EAP) klepněte na syntaxi, najdete v části [vzory asynchronního programování ](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Spouštění asynchronní operace  
 Asynchronní metoda, která je založena na TAP, zvládne malé množství práce synchronně, například validaci argumentů a spouštění asynchronní operace před vrácením výsledné úlohy. Synchronní práce by měly být neustále udržovány na minimu, aby asynchronní metody mohly vracet rychle. Mezi důvody pro rychlý návrat patří:  
  
-   Asynchronní metody mohou být vyvolány z vlákna uživatelského rozhraní (UI) a dlouhotrvající synchronní práce může mít negativní dopad na odezvu aplikace.  
  
-   Je možné spustit několik asynchronních metod současně. Proto by jakékoli dlouhotrvající práce v synchronní části asynchronní metody mohly zpožďovat zahájení jiné asynchronní operace, a tím zmenšit výhody souběžnosti.  
  
 V některých případech je množství práce potřebné k dokončení operace menší než množství práce potřebné ke spuštění operace asynchronně. Příkladem takového scénáře je čtení z datového proudu, kde lze operaci čtení naplnit daty, která jsou již uložena do vyrovnávací paměti. Operace v těchto případech může být dokončena synchronně a může vrátit úlohu, která již byla dokončena.  
  
## <a name="exceptions"></a>Výjimky  
 Asynchronní metoda by měla vyvolat výjimku z volání asynchronní metody pouze jako odpověď na chybu použití. Chyby použití by se nikdy neměly objevit v produkčním kódu. Například, pokud předávání odkaz s hodnotou null (`Nothing` v jazyce Visual Basic) jako jeden z argumentů metody způsobí, že stav chyby (obvykle reprezentována <xref:System.ArgumentNullException> výjimky), můžete upravit kód volání zajistit, že je předán nikdy odkaz s hodnotou null. U všech ostatních chyb by měly být výjimky, ke kterým dochází při spuštění asynchronní metody, přiřazeny vrácené úloze i v případě, že se asynchronní metoda dokončí synchronně předtím, než je úloha vrácena. Úloha obvykle obsahuje nanejvýš jednu výjimku. Ale pokud úloha představuje více operací (například <xref:System.Threading.Tasks.Task.WhenAll%2A>), několik výjimek může být přidružený jeden úkol.  
  
## <a name="target-environment"></a>Cílové prostředí  
 Při implementaci metody TAP můžete určit, kde dochází k asynchronnímu spouštění. Úlohy můžete spouštět ve fondu vláken, implementovat je pomocí asynchronního I/O (bez vázání na vlákno pro většinu spuštění operace), spustit je na konkrétním vlákně (například vlákně UI) nebo použít libovolný počet potenciálních kontextů. Klepněte na metodu může mít i nic provést a může vrátit pouze <xref:System.Threading.Tasks.Task> představující výskytem podmínku jinde v systému (například úloha, která reprezentuje dat odesílaných do zařazených do fronty datová struktura). Volající metody, klepněte na může blokovat čeká na metodu klepněte k dokončení synchronně čekání na výsledný úlohy, nebo může spustit kód další (pokračování), po dokončení asynchronní operace. Tvůrce kódu pokračování má kontrolu nad tím, kde se spustí kód. Můžete vytvořit kód pokračování buď explicitně, prostřednictvím metody na <xref:System.Threading.Tasks.Task> – třída (například <xref:System.Threading.Tasks.Task.ContinueWith%2A>) nebo implicitně, pomocí jazyková podpora postavená na pokračování (například `await` v jazyce C#, `Await` v Jazyků Visual Basic, `AwaitValue` v jazyce F #).  
  
## <a name="task-status"></a>Stav úlohy  
 <xref:System.Threading.Tasks.Task> Třída poskytuje životního cyklu pro asynchronní operace, a je reprezentována tohoto cyklu <xref:System.Threading.Tasks.TaskStatus> výčtu. Pro podporu náročnějších případech typů, které jsou odvozeny od <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601>a k podpoře oddělení konstrukce z plánování, <xref:System.Threading.Tasks.Task> třídy zpřístupňuje <xref:System.Threading.Tasks.Task.Start%2A> metoda. Úlohy, které jsou vytvořené veřejná <xref:System.Threading.Tasks.Task> konstruktory se označují jako *studenou úlohy*, protože bylo počítač jejich životního cyklu v neplánovanou <xref:System.Threading.Tasks.TaskStatus.Created> stavu a jsou naplánované pouze tehdy, když <xref:System.Threading.Tasks.Task.Start%2A> se volá na Tyto instance. 
 
 Všechny ostatní úlohy začít jejich životního cyklu v aktivního stavu, což znamená, že asynchronní operace představují již bylo zahájeno a jejich stav úlohy je jiné než hodnota výčtu <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Všechny úlohy, které jsou vráceny z metod TAP, musí být aktivovány. **Pokud metoda klepněte na úkolu konstruktor interně používá k vytvoření instance úlohy, který se má vrátit, musí volat metoda klepněte na <xref:System.Threading.Tasks.Task.Start%2A> na <xref:System.Threading.Tasks.Task> objekt před vrácením.** Příjemci metody klepněte na může bezpečně předpokládají, že vrácený úloh je aktivní a by se neměl pokoušet volání <xref:System.Threading.Tasks.Task.Start%2A> na žádném <xref:System.Threading.Tasks.Task> , klepněte na metoda vrátí. Volání metody <xref:System.Threading.Tasks.Task.Start%2A> na aktivní úkol má za následek <xref:System.InvalidOperationException> výjimka.  
  
## <a name="cancellation-optional"></a>Zrušení (volitelné)  
 Pro implementátory asynchronní metody i příjemce asynchronní metody je v TAP zrušení volitelné. Pokud operace umožňuje zrušení, vystavuje přetížení asynchronní metody, která přijímá token zrušení (<xref:System.Threading.CancellationToken> instance). Podle konvence je parametr s názvem `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Asynchronní operace sleduje tento token kvůli žádostem o zrušení. Pokud obdrží žádost o zrušení, může vyhovět žádosti a operaci zrušit. Pokud žádost o zrušení výsledkem pracovní se byl předčasně ukončen, vrátí metoda klepněte na úlohy, které <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu; žádný dostupný výsledek a nedojde k výjimce.  <xref:System.Threading.Tasks.TaskStatus.Canceled> Stavu se považuje za konečného stavu (dokončení) pro úlohy, spolu s <xref:System.Threading.Tasks.TaskStatus.Faulted> a <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stavy. Proto pokud úlohu <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, jeho <xref:System.Threading.Tasks.Task.IsCompleted%2A> vlastnost vrátí `true`. Při dokončení úkolu <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu všech pokračování zaregistrována úlohy jsou naplánované nebo provést, není-li například možnost pokračování <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> byl zadán pro vyjádření výslovného nesouhlasu pokračování. Kód, který asynchronně čeká zrušené úlohy prostřednictvím použití funkcí jazyka pokračuje v činnosti, ale zobrazí <xref:System.OperationCanceledException> nebo z něj odvozenou výjimku. Kód, který je blokovaný synchronně čekání na úlohu prostřednictvím metody, jako <xref:System.Threading.Tasks.Task.Wait%2A> a <xref:System.Threading.Tasks.Task.WaitAll%2A> i nadále spouštět s výjimkou.  
  
 Pokud token zrušení vyžaduje zrušení před klepněte na metodu, která přijímá token je volána, klepněte na metoda by měla vrátit <xref:System.Threading.Tasks.TaskStatus.Canceled> úloh.  Pokud je však požadováno zrušení při spuštěné asynchronní operaci, asynchronní operace nemusí přijmout žádost o zrušení.  Vrácený úloh musí končit <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, pouze pokud operaci končí v důsledku žádost o zrušení. Pokud zrušení je požadováno, ale stále vytvořeného výsledku nebo výjimku, úloha musí končit <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> nebo <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu. U asynchronních metod používaných vývojářem, který chce především zrušení, nemusíte poskytovat přetížení, které nepřijímá token zrušení.  Pro metody, které nelze zrušit, neposkytujte přetížení, která přijímají token zrušení. To pomáhá volajícímu určit, zda je skutečně možné zrušit cílovou metodu.  Příjemce kód, který není požadavky zrušení může volat metodu, která přijímá <xref:System.Threading.CancellationToken> a zadejte <xref:System.Threading.CancellationToken.None%2A> jako hodnota argumentu. <xref:System.Threading.CancellationToken.None%2A>je funkčně srovnatelný výchozí <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>Hlášení průběhu (volitelné)  
 Některé asynchronní operace těží z poskytování oznámení o průběhu. Ta se obvykle používají k aktualizaci uživatelského rozhraní informacemi o průběhu asynchronní operace. V KLEPNUTÍ průběh zpracovává prostřednictvím <xref:System.IProgress%601> rozhraní, které se předá do asynchronní metody jako parametr, který je obvykle s názvem `progress`.  Poskytnutí rozhraní průběhu při volání asynchronní metody pomáhá eliminovat konflikty časování, které jsou výsledkem nesprávného použití (to znamená, když obslužným rutinám, které jsou nesprávně zaregistrovány po zahájení operace, chybí aktualizace).  Důležitější je, že rozhraní průběhu podporuje různé implementace průběhu podle náročnosti kódu.  Náročný kód se bude například starat pouze o nejnovější aktualizaci průběhu nebo může chtít mít všechny aktualizace ve vyrovnávací paměti nebo může chtít vyvolat akci pro každou aktualizaci nebo může chtít řídit, zda je volání zařazeno do konkrétního vlákna. Všech těchto možností lze dosáhnout pomocí různých implementací rozhraní přizpůsobených potřebám konkrétního příjemce.  Jako s zrušení, by měl poskytovat implementace klepněte <xref:System.IProgress%601> parametr pouze v případě, že rozhraní API podporuje průběh oznámení. Například pokud `ReadAsync` metoda popsané výše v tomto článku je moct podávat zprávy zprostředkující průběh ve formě počet bajtů číst doposud, může být průběh zpětného volání <xref:System.IProgress%601> rozhraní:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Pokud `FindFilesAsync` metoda vrátí seznam hodnot všechny soubory, které splňují konkrétní vyhledávání vzor, průběh zpětné volání, poskytovat odhad procento práce dokončena a také aktuální sadu částečné výsledky.  To může provést buď s uspořádanou n-ticí:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 nebo s datovým typem, který je specifický pro rozhraní API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 V takovém případě speciální datový typ je obvykle na konci `ProgressInfo`.  
  
 Pokud implementace klepněte na poskytují přetížení pracujících `progress` parametr, se musí povolit argumentem být `null`, v takovém případě bude hlášené žádné průběh. Klepněte na implementace musí hlásit průběh k <xref:System.Progress%601> objektu synchronně, což umožňuje asynchronní metody můžete rychle zajistit průběh a umožňuje příjemci průběhu zjistit, jak a kde nejlépe pro zpracování informací. Například instance průběhu může zvolit zařazování zpětných volání a vyvolat události na zachyceném synchronizačním kontextu.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T > Implementace  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Poskytuje jeden <xref:System.IProgress%601> implementace: <xref:System.Progress%601>. <xref:System.Progress%601> Třída je deklarovaná následujícím způsobem:  
  
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
  
 Instance <xref:System.Progress%601> zpřístupní <xref:System.Progress%601.ProgressChanged> událost, která je vyvolána pokaždé, když probíhá aktualizace sestavy asynchronní operaci. <xref:System.Progress%601.ProgressChanged> Událost se vyvolá při <xref:System.Threading.SynchronizationContext> objekt, který byl při zachycení <xref:System.Progress%601> byla vytvořena instance. Pokud nebyl k dispozici žádný kontext synchronizace, je použit výchozí kontext určený pro fond vláken. Pro tuto událost lze registrovat obslužné rutiny. Jeden obslužná rutina může zadat i k <xref:System.Progress%601> konstruktor pro usnadnění práce a se chová stejně jako obslužné rutiny události pro <xref:System.Progress%601.ProgressChanged> událostí. Aktualizace průběhu jsou vyvolány asynchronně, aby se předešlo zpoždění asynchronní operace, zatímco se provádějí obslužné rutiny události. Jiné <xref:System.IProgress%601> implementace může zvolit použití různých sémantiku.  
  
## <a name="choosing-the-overloads-to-provide"></a>Volba poskytovaných přetížení  
 Pokud klepněte na implementace používá i nepovinný <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> a volitelné <xref:System.IProgress%601> parametry, se může potenciálně vyžadovat až čtyři přetížení:  
  
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
  
 Pro kompenzaci dva chybí zprostředkující kombinace, může předat vývojáři <xref:System.Threading.CancellationToken.None%2A> nebo výchozí <xref:System.Threading.CancellationToken> pro `cancellationToken` parametr a `null` pro `progress` parametr.  
  
 Pokud očekáváte, že každé použití metody TAP bude podporovat zrušení nebo průběh, můžete vynechat přetížení, které nepřijímá odpovídající parametr.  
  
 Pokud se rozhodnete vystavit více přetížení se zrušení nebo průběhu volitelná, přetížení, které nepodporují zrušení nebo průběhu by měl chovat, jako je předat <xref:System.Threading.CancellationToken.None%2A> pro zrušení nebo `null` průběh přetížení, podporuje tyto.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vzory asynchronního programování](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zavádí tři vzory pro provádění asynchronních operací: synchronní vzor založený na úlohách (TAP), asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP).|  
|[Implementace asynchronního vzoru založeného na úloze](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Popisuje tři způsoby implementace asynchronního vzoru založeného na úlohách (TAP): pomocí kompilátorů jazyka C# a Visual Basic v sadě Visual Studio, ručně nebo kombinací obou metod.|  
|[Použití asynchronního vzoru založeného na úloze](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Popisuje, jak použít úlohy a zpětná volání k dosažení čekání bez blokování.|  
|[Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Popisuje způsob použití asynchronního vzoru založeného na úlohách (TAP) k implementaci asynchronního programovacího modelu (APM) a asynchronního vzoru založeného na událostech (EAP).|
