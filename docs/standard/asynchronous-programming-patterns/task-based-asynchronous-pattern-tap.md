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
ms.openlocfilehash: f61ad49753da9d96e733ea667095722ddc238fe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121102"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (klepnutím)
Asynchronní vzor založený na úlohách (klepněte) je založen na <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typech v oboru názvů <xref:System.Threading.Tasks?displayProperty=nameWithType>, které slouží k reprezentaci libovolných asynchronních operací. TAP je doporučený asynchronní návrh vzoru pro nový vývoj.  
  
## <a name="naming-parameters-and-return-types"></a>Pojmenovávání, parametry a návratové typy

TAP používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. To se liší od vzoru asynchronního programovacího modelu (APM nebo `IAsyncResult`) a asynchronního vzoru založeného na událostech (EAP). APM vyžaduje `Begin` a `End` metody. Protokol EAP vyžaduje metodu, která má příponu `Async` a také vyžaduje jednu nebo více událostí, typy delegátů obslužné rutiny události a typy odvozené od `EventArg`. Asynchronní metody v klepnutím zahrnují příponu `Async` za názvem operace pro metody, které vracejí neočekávané typy, například <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>a <xref:System.Threading.Tasks.ValueTask%601>. Například asynchronní operace `Get`, která vrací `Task<String>`, může být pojmenována `GetAsync`. Pokud přidáváte metodu klepněte na třídu, která již obsahuje název metody EAP s příponou `Async`, použijte místo toho příponu `TaskAsync`. Například pokud třída již má metodu `GetAsync`, použijte název `GetTaskAsync`. Pokud metoda spustí asynchronní operaci, ale nevrátí očekávaný typ, jeho název by měl začínat `Begin`, `Start`nebo některé jiné operace, aby bylo možné navrhnout, že tato metoda nevrací nebo nevyvolává výsledek operace.  
  
 Metoda klepnutí vrátí buď <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, na základě toho, zda odpovídající synchronní metoda vrátí typ void nebo typ `TResult`.  
  
 Parametry metody klepnutí by měly odpovídat parametrům jeho synchronního protějšku a měly by být zadány ve stejném pořadí.  Parametry `out` a `ref` však nejsou z tohoto pravidla vyňaty a je třeba se jim vyhnout zcela. Všechna data, která by byla vrácena pomocí `out` nebo `ref` parametru, by měla být vrácena jako součást `TResult` vrácená <xref:System.Threading.Tasks.Task%601>a měla by použít řazenou kolekci členů nebo vlastní datovou strukturu pro přizpůsobení více hodnot. Měli byste také zvážit přidání parametru <xref:System.Threading.CancellationToken> i v případě, že se synchronní protějšek metody klepnutí na ni nenabídne.
 
 Metody, které jsou odčleněny výhradně na vytváření, manipulaci nebo kombinaci úloh (kde je asynchronní záměr metody jasný v názvu metody nebo v názvu typu, ke kterému patří metoda), nemusí následovat po tomto vzoru názvů. Tyto metody jsou často označovány jako *kombinátory*. Příklady kombinátory zahrnují <xref:System.Threading.Tasks.Task.WhenAll%2A> a <xref:System.Threading.Tasks.Task.WhenAny%2A>a jsou popsány v tématu [použití integrovaného oddílu založeného na úlohách kombinátory](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) článku, který [spotřebovává asynchronní vzor založený na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Příklady, jak se syntaxe klepnutí liší od syntaxe používané v zastaralých asynchronních vzorech programování, jako je asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP), naleznete v tématu [asynchronní programovací vzory](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Inicializace asynchronní operace  
 Asynchronní metoda, která je založena na TAP, zvládne malé množství práce synchronně, například validaci argumentů a spouštění asynchronní operace před vrácením výsledné úlohy. Synchronní práce by měly být neustále udržovány na minimu, aby asynchronní metody mohly vracet rychle. Mezi důvody pro rychlý návrat patří:  
  
- Asynchronní metody mohou být vyvolány z vlákna uživatelského rozhraní (UI) a dlouhotrvající synchronní práce může mít negativní dopad na odezvu aplikace.  
  
- Je možné spustit několik asynchronních metod současně. Proto by jakékoli dlouhotrvající práce v synchronní části asynchronní metody mohly zpožďovat zahájení jiné asynchronní operace, a tím zmenšit výhody souběžnosti.  
  
 V některých případech je množství práce potřebné k dokončení operace menší než množství práce potřebné ke spuštění operace asynchronně. Příkladem takového scénáře je čtení z datového proudu, kde lze operaci čtení naplnit daty, která jsou již uložena do vyrovnávací paměti. Operace v těchto případech může být dokončena synchronně a může vrátit úlohu, která již byla dokončena.  
  
## <a name="exceptions"></a>Výjimky  
 Asynchronní metoda by měla vyvolat výjimku z volání asynchronní metody pouze jako odpověď na chybu použití. Chyby použití by se nikdy neměly objevit v produkčním kódu. Například Pokud předáte odkaz s hodnotou null (`Nothing` v Visual Basic), protože jeden z argumentů metody způsobí chybový stav (obvykle reprezentovaný <xref:System.ArgumentNullException> výjimkou), můžete změnit volající kód, aby se zajistilo, že odkaz s hodnotou null není nikdy předán. U všech ostatních chyb by měly být výjimky, ke kterým dochází při spuštění asynchronní metody, přiřazeny vrácené úloze i v případě, že se asynchronní metoda dokončí synchronně předtím, než je úloha vrácena. Úloha obvykle obsahuje nanejvýš jednu výjimku. Pokud však úloha představuje více operací (například <xref:System.Threading.Tasks.Task.WhenAll%2A>), může být k jedné úloze přidruženo více výjimek.  
  
## <a name="target-environment"></a>Cílové prostředí  
 Při implementaci metody TAP můžete určit, kde dochází k asynchronnímu spouštění. Úlohy můžete spouštět ve fondu vláken, implementovat je pomocí asynchronního I/O (bez vázání na vlákno pro většinu spuštění operace), spustit je na konkrétním vlákně (například vlákně UI) nebo použít libovolný počet potenciálních kontextů. Metoda klepnutí může dokonce mít nic ke spuštění a může vrátit <xref:System.Threading.Tasks.Task>, která představuje výskyt podmínky jinde v systému (například úkol, který představuje data přicházející do struktury dat zařazené do fronty).
 
 Volající metody klepnutí může blokovat čekání na provedení metody klepnutí synchronním čekáním na výsledný úkol nebo může spustit další (pokračování) kód po dokončení asynchronní operace. Tvůrce kódu pokračování má kontrolu nad tím, kde se spustí kód. Kód pro pokračování můžete vytvořit buď explicitně, prostřednictvím metod <xref:System.Threading.Tasks.Task> třídy (například <xref:System.Threading.Tasks.Task.ContinueWith%2A>) nebo implicitně pomocí jazykové podpory založené na pokračováních (například `await` v C#`Await` Visual Basic @no__t _5_ v F#).  
  
## <a name="task-status"></a>Stav úlohy  
 Třída <xref:System.Threading.Tasks.Task> poskytuje životní cyklus pro asynchronní operace a tento cyklus je reprezentován výčtem <xref:System.Threading.Tasks.TaskStatus>. Pro podporu rohových případů typů, které jsou odvozeny z <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601>a pro podporu oddělení konstrukce od plánování, třída <xref:System.Threading.Tasks.Task> zpřístupňuje metodu <xref:System.Threading.Tasks.Task.Start%2A>. Úlohy, které jsou vytvořeny pomocí veřejných <xref:System.Threading.Tasks.Task> konstruktory, jsou označovány jako *studené úlohy*, protože začínají jejich životní cyklus v neplánovaném <xref:System.Threading.Tasks.TaskStatus.Created> stavu a jsou plánovány pouze v případě, že je na těchto instancích volána <xref:System.Threading.Tasks.Task.Start%2A>. 
 
 Všechny ostatní úlohy zahájí svůj životní cyklus v horkém stavu, což znamená, že asynchronní operace, které představují, již byly iniciovány a jejich stav úlohy je jiná hodnota výčtu než <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Všechny úlohy, které jsou vráceny z metod TAP, musí být aktivovány. **Pokud metoda klepnutí interně používá konstruktor úkolu k vytvoření instance úkolu, který má být vrácen, metoda klepnutí musí volat <xref:System.Threading.Tasks.Task.Start%2A> na objektu <xref:System.Threading.Tasks.Task> před jeho vrácením.** Příjemci metody klepnutí můžou bezpečně předpokládat, že vrácená úloha je aktivní a neměla by se pokoušet o volání <xref:System.Threading.Tasks.Task.Start%2A> na všech <xref:System.Threading.Tasks.Task>, které se vrátí z metody klepnutí. Volání <xref:System.Threading.Tasks.Task.Start%2A> na aktivní úloze má za následek výjimku <xref:System.InvalidOperationException>.  
  
## <a name="cancellation-optional"></a>Zrušení (volitelné)  
 Pro implementátory asynchronní metody i příjemce asynchronní metody je v TAP zrušení volitelné. Pokud operace umožňuje zrušení, zveřejňuje přetížení asynchronní metody, která přijímá token zrušení (<xref:System.Threading.CancellationToken> instance). Podle konvence má parametr název `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Asynchronní operace sleduje tento token kvůli žádostem o zrušení. Pokud obdrží žádost o zrušení, může vyhovět žádosti a operaci zrušit. Pokud výsledkem požadavku na zrušení je předčasně ukončena práce, metoda klepnutí vrátí úlohu, která skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>. k dispozici není žádný výsledek a není vyvolána žádná výjimka.  <xref:System.Threading.Tasks.TaskStatus.Canceled> stav se považuje za konečný (dokončený) stav úlohy společně s <xref:System.Threading.Tasks.TaskStatus.Faulted> a <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stavy. Proto pokud je úkol ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>, jeho vlastnost <xref:System.Threading.Tasks.Task.IsCompleted%2A> vrátí `true`. Když se úloha dokončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>, všechna pokračování zaregistrovaná v rámci úlohy se naplánují nebo spustí, pokud není možnost pokračování, jako je třeba <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled>, nedošlo k odhlášení z pokračování. Jakýkoli kód, který asynchronně čeká na zrušený úkol prostřednictvím použití funkcí jazyka, pokračuje v běhu, ale přijímá <xref:System.OperationCanceledException> nebo výjimku z něj odvozenou. Kód, který je blokován synchronně čekáním na úlohu prostřednictvím metod, jako je například <xref:System.Threading.Tasks.Task.Wait%2A> a <xref:System.Threading.Tasks.Task.WaitAll%2A> také i nadále běžet s výjimkou.  
  
 Pokud token zrušení požadoval zrušení před tím, než je volána metoda klepnutí, která přijímá tento token, metoda klepnutí by měla vrátit úlohu <xref:System.Threading.Tasks.TaskStatus.Canceled>.  Pokud je však požadováno zrušení při spuštěné asynchronní operaci, asynchronní operace nemusí přijmout žádost o zrušení.  Vrácený úkol by měl končit ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled> pouze v případě, že operace skončí v důsledku požadavku na zrušení. Pokud je požadováno zrušení, ale výsledek nebo výjimka jsou stále vyprodukovány, úloha by měla skončit ve <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> nebo <xref:System.Threading.Tasks.TaskStatus.Faulted>m stavu. 
 
 Pro asynchronní metody, které chtějí vystavit možnost zrušit první a nejpřednější, nemusíte poskytovat přetížení, které nepřijímá token zrušení. Pro metody, které nelze zrušit, neposkytujte přetížení, která přijímají token zrušení. To pomáhá volajícímu určit, zda je skutečně možné zrušit cílovou metodu.  Kód příjemce, který není žádoucí pro zrušení, může volat metodu, která přijímá <xref:System.Threading.CancellationToken> a jako hodnotu argumentu zadat <xref:System.Threading.CancellationToken.None%2A>. <xref:System.Threading.CancellationToken.None%2A> je funkčně ekvivalentní výchozímu <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>Vytváření sestav průběhu (volitelné)  
 Některé asynchronní operace těží z poskytování oznámení o průběhu. Ta se obvykle používají k aktualizaci uživatelského rozhraní informacemi o průběhu asynchronní operace. 
 
 V klepněte, průběh je zpracován prostřednictvím rozhraní <xref:System.IProgress%601>, které je předáno asynchronní metodě jako parametr, který je obvykle pojmenován `progress`.  Poskytnutí rozhraní průběhu při volání asynchronní metody pomáhá eliminovat konflikty časování, které jsou výsledkem nesprávného použití (to znamená, když obslužným rutinám, které jsou nesprávně zaregistrovány po zahájení operace, chybí aktualizace).  Důležitější je, že rozhraní průběhu podporuje různé implementace průběhu podle náročnosti kódu.  Náročný kód se bude například starat pouze o nejnovější aktualizaci průběhu nebo může chtít mít všechny aktualizace ve vyrovnávací paměti nebo může chtít vyvolat akci pro každou aktualizaci nebo může chtít řídit, zda je volání zařazeno do konkrétního vlákna. Všech těchto možností lze dosáhnout pomocí různých implementací rozhraní přizpůsobených potřebám konkrétního příjemce.  Stejně jako u zrušení, klepnutí na implementace by měly poskytnout parametr <xref:System.IProgress%601>, pouze pokud rozhraní API podporuje oznámení o průběhu. 
 
 Pokud například metoda `ReadAsync` popsaná výše v tomto článku dokáže podávat sestavy o mezilehlém pokroku ve formě počtu přečtených bajtů, může zpětné volání průběhu představovat <xref:System.IProgress%601> rozhraní:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Pokud metoda `FindFilesAsync` vrátí seznam všech souborů, které splňují konkrétní vzor hledání, zpětné volání průběhu může poskytnout odhad procentuální hodnoty dokončené práce a také aktuální sadu částečných výsledků.  To může provést buď s uspořádanou n-ticí:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 nebo s datovým typem, který je specifický pro rozhraní API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 V druhém případě je zvláštní datový typ obvykle `ProgressInfo`příponou.  
  
 Pokud klepnutím na implementace zadáte přetížení, která přijímají parametr `progress`, musí umožnit, aby byl argument `null`. v takovém případě se nebude hlásit žádný pokrok. Klepnutím na implementace by měl být průběh na objekt <xref:System.Progress%601> synchronně, což umožňuje asynchronní metodě rychle poskytnout průběh a umožnit spotřebiteli postup, jak určit, jak a kde nejlépe zpracovávat informace. Například instance průběhu může zvolit zařazování zpětných volání a vyvolat události na zachyceném synchronizačním kontextu.  
  
## <a name="iprogresst-implementations"></a>Implementace > IProgress\<T  
 .NET Framework 4,5 poskytuje jednu <xref:System.IProgress%601> implementaci: <xref:System.Progress%601>. Třída <xref:System.Progress%601> je deklarována takto:  
  
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
  
 Instance <xref:System.Progress%601> zpřístupňuje událost <xref:System.Progress%601.ProgressChanged>, která je vyvolána pokaždé, když asynchronní operace ohlásí aktualizaci průběhu. Událost <xref:System.Progress%601.ProgressChanged> je vyvolána na objektu <xref:System.Threading.SynchronizationContext>, který byl zachycen při vytváření instance <xref:System.Progress%601> instance. Pokud nebyl k dispozici žádný kontext synchronizace, je použit výchozí kontext určený pro fond vláken. Pro tuto událost lze registrovat obslužné rutiny. Jedna obslužná rutina může být také poskytnuta konstruktoru <xref:System.Progress%601> pro usnadnění a chová se stejně jako obslužná rutina události <xref:System.Progress%601.ProgressChanged> událost. Aktualizace průběhu jsou vyvolány asynchronně, aby se předešlo zpoždění asynchronní operace, zatímco se provádějí obslužné rutiny události. Jiná implementace <xref:System.IProgress%601> by se mohla rozhodnout použít odlišnou sémantiku.  
  
## <a name="choosing-the-overloads-to-provide"></a>Výběr přetížení k poskytnutí  
 Pokud implementace klepnutí používá volitelné <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> a volitelné <xref:System.IProgress%601> parametry, může potenciálně vyžadovat až čtyři přetížení:  
  
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
  
 Pro kompenzaci dvou chybějících mezilehlých kombinací můžou vývojáři předat <xref:System.Threading.CancellationToken.None%2A> nebo výchozí <xref:System.Threading.CancellationToken> pro parametr `cancellationToken` a `null` pro parametr `progress`.  
  
 Pokud očekáváte, že každé použití metody TAP bude podporovat zrušení nebo průběh, můžete vynechat přetížení, které nepřijímá odpovídající parametr.  
  
 Pokud se rozhodnete vystavit více přetížení, aby bylo zrušení nebo průběh volitelné, přetížení, která nepodporují zrušení nebo průběh, by se měla chovat, jako by předala <xref:System.Threading.CancellationToken.None%2A> pro zrušení nebo `null` pro průběh přetížení, které podporuje jsou.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vzory asynchronního programování](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zavádí tři vzory pro provádění asynchronních operací: synchronní vzor založený na úlohách (TAP), asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP).|  
|[Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Popisuje tři způsoby implementace asynchronního vzoru založeného na úlohách (TAP): pomocí kompilátorů jazyka C# a Visual Basic v sadě Visual Studio, ručně nebo kombinací obou metod.|  
|[Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Popisuje, jak použít úlohy a zpětná volání k dosažení čekání bez blokování.|  
|[Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Popisuje způsob použití asynchronního vzoru založeného na úlohách (TAP) k implementaci asynchronního programovacího modelu (APM) a asynchronního vzoru založeného na událostech (EAP).|
