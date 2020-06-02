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
ms.openlocfilehash: 4a08c8a72116ea509f559e412c5f270f3471bf1c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276436"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (klepnutím)
Asynchronní vzor založený na úlohách (klepněte) je založen na <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typech a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> v <xref:System.Threading.Tasks?displayProperty=nameWithType> oboru názvů, které slouží k reprezentaci libovolných asynchronních operací. TAP je doporučený asynchronní návrh vzoru pro nový vývoj.  
  
## <a name="naming-parameters-and-return-types"></a>Pojmenovávání, parametry a návratové typy

TAP používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. To se liší od vzoru asynchronního programovacího modelu (APM nebo `IAsyncResult` ) a asynchronního vzoru založeného na událostech (EAP). APM vyžaduje `Begin` a `End` metody. Protokol EAP vyžaduje metodu, která má `Async` příponu, a také vyžaduje jednu nebo více událostí, typy delegátů obslužných rutin událostí a `EventArg` odvozené typy. Asynchronní metody v klepnutím zahrnují `Async` příponu za názvem operace pro metody, které vracejí awaitelné typy, například <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.ValueTask> a <xref:System.Threading.Tasks.ValueTask%601> . Například asynchronní `Get` operace, která vrací, `Task<String>` může být pojmenována `GetAsync` . Pokud přidáváte metodu klepněte na třídu, která již obsahuje název metody EAP s `Async` příponou, použijte `TaskAsync` místo toho příponu. Například pokud třída již obsahuje `GetAsync` metodu, použijte název `GetTaskAsync` . Pokud metoda spustí asynchronní operaci, ale nevrátí očekávaný typ, jeho název by měl začínat `Begin` na, `Start` nebo nějaký jiný příkaz, který navrhne, že tato metoda nevrátí nebo nevyvolává výsledek operace.  
  
 Metoda klepnutí vrátí buď <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo a, na <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> základě toho, zda odpovídající synchronní metoda vrátí typ void nebo typ `TResult` .  
  
 Parametry metody klepnutí by měly odpovídat parametrům jeho synchronního protějšku a měly by být zadány ve stejném pořadí.  `out` `ref` Parametry a jsou však z tohoto pravidla vyloučeny a je třeba se jim vyhnout zcela. Všechna data, která by byla vrácena prostřednictvím `out` parametru nebo `ref` , by měla být vrácena jako součást `TResult` vrácená funkcí <xref:System.Threading.Tasks.Task%601> a měla by použít řazenou kolekci členů nebo vlastní datovou strukturu pro přizpůsobení více hodnot. Měli byste také zvážit přidání <xref:System.Threading.CancellationToken> parametru i v případě, že synchronní protějšek metody klepnutí na ni nenabízí žádný.

 Metody, které jsou odčleněny výhradně na vytváření, manipulaci nebo kombinaci úloh (kde je asynchronní záměr metody jasný v názvu metody nebo v názvu typu, ke kterému patří metoda), nemusí následovat po tomto vzoru názvů. Tyto metody jsou často označovány jako *kombinátory*. Příklady kombinátory zahrnují <xref:System.Threading.Tasks.Task.WhenAll%2A> a a <xref:System.Threading.Tasks.Task.WhenAny%2A> jsou popsány v tématu [použití integrovaného oddílu založeného na úlohách kombinátory](consuming-the-task-based-asynchronous-pattern.md#combinators) článku, který [spotřebovává asynchronní vzor založený na úlohách](consuming-the-task-based-asynchronous-pattern.md).  
  
 Příklady, jak se syntaxe klepnutí liší od syntaxe používané v zastaralých asynchronních vzorech programování, jako je asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP), naleznete v tématu [asynchronní programovací vzory](index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Inicializace asynchronní operace  
 Asynchronní metoda, která je založena na TAP, zvládne malé množství práce synchronně, například validaci argumentů a spouštění asynchronní operace před vrácením výsledné úlohy. Synchronní práce by měly být neustále udržovány na minimu, aby asynchronní metody mohly vracet rychle. Mezi důvody pro rychlý návrat patří:  
  
- Asynchronní metody mohou být vyvolány z vlákna uživatelského rozhraní (UI) a dlouhotrvající synchronní práce může mít negativní dopad na odezvu aplikace.  
  
- Je možné spustit několik asynchronních metod současně. Proto by jakékoli dlouhotrvající práce v synchronní části asynchronní metody mohly zpožďovat zahájení jiné asynchronní operace, a tím zmenšit výhody souběžnosti.  
  
 V některých případech je množství práce potřebné k dokončení operace menší než množství práce potřebné ke spuštění operace asynchronně. Příkladem takového scénáře je čtení z datového proudu, kde lze operaci čtení naplnit daty, která jsou již uložena do vyrovnávací paměti. Operace v těchto případech může být dokončena synchronně a může vrátit úlohu, která již byla dokončena.  
  
## <a name="exceptions"></a>Výjimky  
 Asynchronní metoda by měla vyvolat výjimku z volání asynchronní metody pouze jako odpověď na chybu použití. Chyby použití by se nikdy neměly objevit v produkčním kódu. Například pokud předání odkazu s hodnotou null ( `Nothing` v Visual Basic) jako jeden z argumentů metody způsobí chybový stav (obvykle reprezentovaný <xref:System.ArgumentNullException> výjimku), můžete změnit volající kód, aby se zajistilo, že odkaz s hodnotou null není nikdy předán. U všech ostatních chyb by měly být výjimky, ke kterým dochází při spuštění asynchronní metody, přiřazeny vrácené úloze i v případě, že se asynchronní metoda dokončí synchronně předtím, než je úloha vrácena. Úloha obvykle obsahuje nanejvýš jednu výjimku. Pokud však úloha představuje více operací (například <xref:System.Threading.Tasks.Task.WhenAll%2A> ), může být k jedné úloze přidruženo více výjimek.  
  
## <a name="target-environment"></a>Cílové prostředí  
 Při implementaci metody TAP můžete určit, kde dochází k asynchronnímu spouštění. Úlohy můžete spouštět ve fondu vláken, implementovat je pomocí asynchronního I/O (bez vázání na vlákno pro většinu spuštění operace), spustit je na konkrétním vlákně (například vlákně UI) nebo použít libovolný počet potenciálních kontextů. Metoda klepnutí může dokonce mít nic ke spuštění a může vrátit <xref:System.Threading.Tasks.Task> , která představuje výskyt podmínky jinde v systému (například úkol, který představuje data přicházející do struktury dat ve frontě).

 Volající metody klepnutí může blokovat čekání na provedení metody klepnutí synchronním čekáním na výsledný úkol nebo může spustit další (pokračování) kód po dokončení asynchronní operace. Tvůrce kódu pokračování má kontrolu nad tím, kde se spustí kód. Kód pro pokračování můžete vytvořit buď explicitně, prostřednictvím metod <xref:System.Threading.Tasks.Task> třídy (například <xref:System.Threading.Tasks.Task.ContinueWith%2A> ) nebo implicitně pomocí jazykové podpory postavené na pokračování (například `await` v jazyce C#, `Await` v Visual Basic v `AwaitValue` F #).  
  
## <a name="task-status"></a>Stav úlohy  
 <xref:System.Threading.Tasks.Task>Třída poskytuje životní cyklus pro asynchronní operace a tento cyklus je reprezentován <xref:System.Threading.Tasks.TaskStatus> výčtem. Aby bylo možné podporovat rohové případy typů, které jsou odvozeny z <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> , a pro podporu oddělení konstrukce od plánování, <xref:System.Threading.Tasks.Task> Třída zpřístupňuje <xref:System.Threading.Tasks.Task.Start%2A> metodu. Úlohy, které jsou vytvořeny veřejnými <xref:System.Threading.Tasks.Task> konstruktory, jsou označovány jako *studené úlohy*, protože začínají jejich životní cyklus v neplánovaném <xref:System.Threading.Tasks.TaskStatus.Created> stavu a jsou naplánovány pouze <xref:System.Threading.Tasks.Task.Start%2A> v případě, že jsou na tyto instance volány.

 Všechny ostatní úlohy začínají svůj životní cyklus v horkém stavu, což znamená, že asynchronní operace, které představují, již byly iniciovány a jejich stav úlohy je hodnota výčtu jinou než <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType> . Všechny úlohy, které jsou vráceny z metod TAP, musí být aktivovány. **Pokud metoda klepnutí interně používá konstruktor úkolu k vytvoření instance úkolu, který má být vrácen, metoda klepnutí musí <xref:System.Threading.Tasks.Task.Start%2A> <xref:System.Threading.Tasks.Task> před vrácením objektu zavolat na objekt.** Příjemci metody klepnutí můžou bezpečně předpokládat, že vrácená úloha je aktivní a neměla by se pokoušet <xref:System.Threading.Tasks.Task.Start%2A> o volání <xref:System.Threading.Tasks.Task> , která se vrátí z metody klepnutí. Volání <xref:System.Threading.Tasks.Task.Start%2A> na aktivní úloze má za následek <xref:System.InvalidOperationException> výjimku.  
  
## <a name="cancellation-optional"></a>Zrušení (volitelné)  
 Pro implementátory asynchronní metody i příjemce asynchronní metody je v TAP zrušení volitelné. Pokud operace umožňuje zrušení, zveřejňuje přetížení asynchronní metody, která přijímá token zrušení ( <xref:System.Threading.CancellationToken> instance). Podle konvence má parametr název `cancellationToken` .  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Asynchronní operace sleduje tento token kvůli žádostem o zrušení. Pokud obdrží žádost o zrušení, může vyhovět žádosti a operaci zrušit. Pokud výsledkem žádosti o zrušení byla předčasně ukončena práce, metoda klepnutí vrátí úlohu, která skončí ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu. neexistují žádné výsledky k dispozici a není vyvolána žádná výjimka.  <xref:System.Threading.Tasks.TaskStatus.Canceled>Stav se považuje za poslední (dokončený) stav úlohy, spolu s <xref:System.Threading.Tasks.TaskStatus.Faulted> <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stavy a. Proto pokud je úkol ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, <xref:System.Threading.Tasks.Task.IsCompleted%2A> vrátí jeho vlastnost `true` . Když se úloha dokončí ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, naplánují se nebo spustí všechna pokračování zaregistrovaná v úloze, pokud se nezadá možnost pokračování, jako <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> je třeba zadání pro odhlášení z pokračování. Jakýkoli kód, který asynchronně čeká na zrušenou úlohu prostřednictvím použití funkcí jazyka, pokračuje v běhu, ale přijímá <xref:System.OperationCanceledException> výjimku nebo z ní odvozenou výjimku. Kód, který je blokován synchronně čekáním na úlohu prostřednictvím metod, jako je <xref:System.Threading.Tasks.Task.Wait%2A> a <xref:System.Threading.Tasks.Task.WaitAll%2A> také i nadále spouštěn s výjimkou.  
  
 Pokud token zrušení požadoval zrušení před tím, než je volána metoda klepnutí, která přijímá tento token, metoda klepnutí by měla vrátit <xref:System.Threading.Tasks.TaskStatus.Canceled> úlohu.  Pokud je však požadováno zrušení při spuštěné asynchronní operaci, asynchronní operace nemusí přijmout žádost o zrušení.  Vrácený úkol by měl končit ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu pouze v případě, že operace skončí v důsledku požadavku na zrušení. Pokud je požadováno zrušení, ale výsledek nebo výjimka jsou stále vyprodukovány, úloha by měla skončit ve <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu or.

 Pro asynchronní metody, které chtějí vystavit možnost zrušit první a nejpřednější, nemusíte poskytovat přetížení, které nepřijímá token zrušení. Pro metody, které nelze zrušit, neposkytujte přetížení, která přijímají token zrušení. To pomáhá volajícímu určit, zda je skutečně možné zrušit cílovou metodu.  Kód příjemce, který není žádoucí pro zrušení, může volat metodu, která přijímá <xref:System.Threading.CancellationToken> a <xref:System.Threading.CancellationToken.None%2A> jako hodnotu argumentu zadejte. <xref:System.Threading.CancellationToken.None%2A>je funkčně ekvivalentní výchozímu <xref:System.Threading.CancellationToken> .  
  
## <a name="progress-reporting-optional"></a>Vytváření sestav průběhu (volitelné)  
 Některé asynchronní operace těží z poskytování oznámení o průběhu. Ta se obvykle používají k aktualizaci uživatelského rozhraní informacemi o průběhu asynchronní operace.

 V klepněte na průběh je zpracováno prostřednictvím <xref:System.IProgress%601> rozhraní, které je předáno asynchronní metodě jako parametr, který je obvykle pojmenován `progress` .  Poskytnutí rozhraní průběhu při volání asynchronní metody pomáhá eliminovat konflikty časování, které jsou výsledkem nesprávného použití (to znamená, když obslužným rutinám, které jsou nesprávně zaregistrovány po zahájení operace, chybí aktualizace).  Důležitější je, že rozhraní průběhu podporuje různé implementace průběhu podle náročnosti kódu.  Náročný kód se bude například starat pouze o nejnovější aktualizaci průběhu nebo může chtít mít všechny aktualizace ve vyrovnávací paměti nebo může chtít vyvolat akci pro každou aktualizaci nebo může chtít řídit, zda je volání zařazeno do konkrétního vlákna. Všech těchto možností lze dosáhnout pomocí různých implementací rozhraní přizpůsobených potřebám konkrétního příjemce.  Stejně jako u zrušení, klepnutí na implementace by měly poskytnout <xref:System.IProgress%601> parametr pouze v případě, že rozhraní API podporuje oznámení o průběhu.

 Například pokud `ReadAsync` Metoda popsaná výše v tomto článku může nahlásit mezikrokový postup ve formě Počet přečtených bajtů, může být zpětné volání průběhu <xref:System.IProgress%601> rozhraní:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Pokud `FindFilesAsync` Metoda vrátí seznam všech souborů, které splňují konkrétní vzor hledání, zpětné volání průběhu může poskytnout odhad procentuální hodnoty dokončené práce a také aktuální sadu částečných výsledků.  To může provést buď s uspořádanou n-ticí:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 nebo s datovým typem, který je specifický pro rozhraní API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 V druhém případě se speciální datový typ obvykle používá s příponou `ProgressInfo` .  
  
 Pokud klepnutím na implementace zadáte přetížení, která přijímají `progress` parametr, musí umožnit argumentu `null` , v takovém případě se nebude hlásit žádný průběh. Klepněte na implementace, které by měly vykázat průběh na <xref:System.Progress%601> objekt synchronně, což umožňuje asynchronní metodě rychle poskytnout průběh a umožnit spotřebiteli postup určit, jak a kde je vhodné informace zpracovat. Například instance průběhu může zvolit zařazování zpětných volání a vyvolat události na zachyceném synchronizačním kontextu.  
  
## <a name="iprogresst-implementations"></a>\<T>Implementace IProgress  
 .NET Framework 4,5 poskytuje jednu <xref:System.IProgress%601> implementaci: <xref:System.Progress%601> . <xref:System.Progress%601>Třída je deklarována takto:  
  
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
  
 Instance třídy <xref:System.Progress%601> zpřístupňuje <xref:System.Progress%601.ProgressChanged> událost, která je vyvolána pokaždé, když asynchronní operace ohlásí aktualizaci průběhu. <xref:System.Progress%601.ProgressChanged>Událost je vyvolána u <xref:System.Threading.SynchronizationContext> objektu, který byl zachycen při vytváření instance <xref:System.Progress%601> instance. Pokud nebyl k dispozici žádný kontext synchronizace, je použit výchozí kontext určený pro fond vláken. Pro tuto událost lze registrovat obslužné rutiny. Jedna obslužná rutina může být také poskytnuta <xref:System.Progress%601> konstruktoru pro usnadnění a chová se stejně jako obslužná rutina události pro <xref:System.Progress%601.ProgressChanged> událost. Aktualizace průběhu jsou vyvolány asynchronně, aby se předešlo zpoždění asynchronní operace, zatímco se provádějí obslužné rutiny události. Jiná <xref:System.IProgress%601> implementace by mohla zvolit, že se má použít odlišná sémantika.  
  
## <a name="choosing-the-overloads-to-provide"></a>Výběr přetížení k poskytnutí  
 Pokud implementace klepnutí používá volitelné <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> i volitelné <xref:System.IProgress%601> parametry, může potenciálně vyžadovat až čtyři přetížení:  
  
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
  
 Aby bylo možné kompenzovat dvě chybějící mezilehlé kombinace, mohou vývojáři předat <xref:System.Threading.CancellationToken.None%2A> nebo zadat výchozí <xref:System.Threading.CancellationToken> parametry pro `cancellationToken` parametr a `null` pro `progress` parametr.  
  
 Pokud očekáváte, že každé použití metody TAP bude podporovat zrušení nebo průběh, můžete vynechat přetížení, které nepřijímá odpovídající parametr.  
  
 Pokud se rozhodnete zveřejnit více přetížení, aby bylo zrušení nebo průběh volitelné, přetížení, která nepodporují zrušení nebo průběh, by se měla chovat, jako by byla předána <xref:System.Threading.CancellationToken.None%2A> pro zrušení nebo `null` pro průběh přetížení, který je podporuje.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Vzorce asynchronního programování](index.md)|Zavádí tři vzory pro provádění asynchronních operací: synchronní vzor založený na úlohách (TAP), asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP).|  
|[Implementace asynchronního vzoru založeného na úlohách](implementing-the-task-based-asynchronous-pattern.md)|Popisuje tři způsoby implementace asynchronního vzoru založeného na úlohách (TAP): pomocí kompilátorů jazyka C# a Visual Basic v sadě Visual Studio, ručně nebo kombinací obou metod.|  
|[Použití asynchronního vzoru založeného na úlohách](consuming-the-task-based-asynchronous-pattern.md)|Popisuje, jak použít úlohy a zpětná volání k dosažení čekání bez blokování.|  
|[Interoperabilita s jinými asynchronními vzory a typy](interop-with-other-asynchronous-patterns-and-types.md)|Popisuje způsob použití asynchronního vzoru založeného na úlohách (TAP) k implementaci asynchronního programovacího modelu (APM) a asynchronního vzoru založeného na událostech (EAP).|
