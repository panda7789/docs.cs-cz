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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 052f6a61fb1b03b060e22bbff2d8124ac3a1c0c0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377660"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (TAP)
Založený na úlohách asynchronního vzoru (TAP) je založena na <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> napíše <xref:System.Threading.Tasks?displayProperty=nameWithType> obor názvů, které představují libovolné asynchronní operace. TAP je doporučený asynchronní návrh vzoru pro nový vývoj.  
  
## <a name="naming-parameters-and-return-types"></a>Pojmenování, parametry a návratové typy

TAP používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. Tím se liší od obou modelu asynchronního programování (APM nebo `IAsyncResult`) vzor a založený na událostech asynchronní vzor (EAP). Vyžaduje APM `Begin` a `End` metody. EAP vyžaduje metodu, která má `Async` přípony a také vyžaduje jeden nebo více událostí, typy delegátu obslužné rutiny událostí, a `EventArg`-odvozené typy. Asynchronní metody v TAP patří `Async` přípony po operaci název metody, které vracejí očekávatelný typy, jako <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, a <xref:System.Threading.Tasks.ValueTask%601>. Příklad asynchronního `Get` operace, která vrací `Task<String>` může mít název `GetAsync`. Pokud přidáváte metodu TAP do třídy, který již obsahuje název metody EAP s `Async` přípony, použijte příponu `TaskAsync` místo. Například, pokud třída již má `GetAsync` metody, použijte název `GetTaskAsync`. Pokud metoda spustí asynchronní operaci, ale nevrací typ očekávatelný, její název by měl začínat `Begin`, `Start`, nebo jiné operace naznačuje, že tato metoda vrátí nebo vyvolat výsledek operace.  
  
 Metoda TAP vrací buď <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>závislosti na tom, zda odpovídající synchronní metoda vrací hodnotu void nebo typ `TResult`.  
  
 Parametry metody TAP by měly odpovídat parametrům jejího synchronního protějšku a měly by být ve stejném pořadí.  Ale `out` a `ref` parametry jsou z tohoto pravidla vyjmuty a mělo by se vyhnout úplně. Všechna data, která by byla vrácena prostřednictvím `out` nebo `ref` parametru by měla být vrácena místo toho jako součást `TResult` vrácený <xref:System.Threading.Tasks.Task%601>a používejte n-tici nebo vlastní datovou strukturu pro přizpůsobení se více hodnotám. Měli byste také zvážit přidání <xref:System.Threading.CancellationToken> i pokud metoda TAP synchronního protějšku nenabízí jeden parametr.
 
 Metody, které jsou vyhrazeny pouze k vytváření, manipulaci nebo kombinaci úloh (kde asynchronní záměr metody je jasný z názvu metody nebo názvu typu, do kterého metoda patří), se nemusí řídit tímto vzorem pojmenování; Tyto metody jsou často označovány jako *combinators*. Mezi combinators patří <xref:System.Threading.Tasks.Task.WhenAll%2A> a <xref:System.Threading.Tasks.Task.WhenAny%2A>a jsou popsány v [pomocí integrované Task-based Combinators](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) část článku [použití asynchronního vzoruzaloženénaúlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Příklady, jak se syntaxe TAP liší od syntaxe používané ve starších asynchronních programovacích vzorech například asynchronní programovací Model (APM) a založený na událostech asynchronní vzor (EAP), najdete v části [Asynchronous Programming Patterns ](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Spouštění asynchronní operace  
 Asynchronní metoda, která je založena na TAP, zvládne malé množství práce synchronně, například validaci argumentů a spouštění asynchronní operace před vrácením výsledné úlohy. Synchronní práce by měly být neustále udržovány na minimu, aby asynchronní metody mohly vracet rychle. Mezi důvody pro rychlý návrat patří:  
  
- Asynchronní metody mohou být vyvolány z vlákna uživatelského rozhraní (UI) a dlouhotrvající synchronní práce může mít negativní dopad na odezvu aplikace.  
  
- Je možné spustit několik asynchronních metod současně. Proto by jakékoli dlouhotrvající práce v synchronní části asynchronní metody mohly zpožďovat zahájení jiné asynchronní operace, a tím zmenšit výhody souběžnosti.  
  
 V některých případech je množství práce potřebné k dokončení operace menší než množství práce potřebné ke spuštění operace asynchronně. Příkladem takového scénáře je čtení z datového proudu, kde lze operaci čtení naplnit daty, která jsou již uložena do vyrovnávací paměti. Operace v těchto případech může být dokončena synchronně a může vrátit úlohu, která již byla dokončena.  
  
## <a name="exceptions"></a>Výjimky  
 Asynchronní metoda by měla vyvolat výjimku z volání asynchronní metody pouze jako odpověď na chybu použití. Chyby použití by se nikdy neměly objevit v produkčním kódu. Například, pokud předání hodnoty null (`Nothing` v jazyce Visual Basic) jako jeden z argumentů metody způsobí stav chyby (obvykle reprezentováno <xref:System.ArgumentNullException> výjimku), můžete upravit volající kód tak, aby nebyl nikdy předán nulový odkaz. U všech ostatních chyb by měly být výjimky, ke kterým dochází při spuštění asynchronní metody, přiřazeny vrácené úloze i v případě, že se asynchronní metoda dokončí synchronně předtím, než je úloha vrácena. Úloha obvykle obsahuje nanejvýš jednu výjimku. Nicméně pokud úloha představuje více operací (například <xref:System.Threading.Tasks.Task.WhenAll%2A>), více výjimek, může být spojen s jeden úkol.  
  
## <a name="target-environment"></a>Cílové prostředí  
 Při implementaci metody TAP můžete určit, kde dochází k asynchronnímu spouštění. Úlohy můžete spouštět ve fondu vláken, implementovat je pomocí asynchronního I/O (bez vázání na vlákno pro většinu spuštění operace), spustit je na konkrétním vlákně (například vlákně UI) nebo použít libovolný počet potenciálních kontextů. Metody TAP může mít ani nic ke spuštění a může vrátit pouze <xref:System.Threading.Tasks.Task> , která představuje výskyt podmínky jinde v systému (například úlohu představující data přicházející do zařazených do fronty datové struktury).
 
 Volající metody TAP může blokovat čekání na metodu TAP k dokončení synchronním čekání na výsledný úkol nebo může spustit další (pokračování) kód po dokončení asynchronní operace. Tvůrce kódu pokračování má kontrolu nad tím, kde se spustí kód. Můžete vytvořit kód pokračování buď explicitně, prostřednictvím metod na <xref:System.Threading.Tasks.Task> třídy (například <xref:System.Threading.Tasks.Task.ContinueWith%2A>) nebo implicitně pomocí jazykové podpory postavené na pokračování (například `await` v C#, `Await` v jazyce Visual Basic `AwaitValue` v F#).  
  
## <a name="task-status"></a>Stav úlohy  
 <xref:System.Threading.Tasks.Task> Třída poskytuje životní cyklus pro asynchronní operace, a tento cyklus je reprezentována <xref:System.Threading.Tasks.TaskStatus> výčtu. Podpory mezních případů typů, které jsou odvozeny z <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601>a podpory oddělení konstrukce od plánování <xref:System.Threading.Tasks.Task> třídy zpřístupňuje <xref:System.Threading.Tasks.Task.Start%2A> metoda. Úlohy, které jsou vytvořeny veřejnými <xref:System.Threading.Tasks.Task> konstruktory jsou označovány jako *studené úlohy*, protože tyto zahajují svůj životní cyklus v neplánovaném <xref:System.Threading.Tasks.TaskStatus.Created> stavu a jsou naplánovány pouze tehdy, když <xref:System.Threading.Tasks.Task.Start%2A> je volán na Tyto instance. 
 
 Všechny ostatní úlohy zahajují svůj životní cyklus v horkém stavu, což znamená, že asynchronní operace, které představují, již byly zahájeny a jejich stav úlohy je jiné než hodnoty výčtu <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Všechny úlohy, které jsou vráceny z metod TAP, musí být aktivovány. **Pokud metoda TAP interně používá konstruktor k vytvoření instance úlohy, který se má vrátit, musí metoda TAP volat <xref:System.Threading.Tasks.Task.Start%2A> na <xref:System.Threading.Tasks.Task> objektu před jeho vrácením.** Příjemci metody TAP mohou bezpečně předpokládat, že vrácená úloha je aktivní a neměli by zkoušet volat <xref:System.Threading.Tasks.Task.Start%2A> na žádném <xref:System.Threading.Tasks.Task> vrácené metodou TAP. Volání <xref:System.Threading.Tasks.Task.Start%2A> na aktivní úlohy vede <xref:System.InvalidOperationException> výjimky.  
  
## <a name="cancellation-optional"></a>Zrušení (volitelné)  
 Pro implementátory asynchronní metody i příjemce asynchronní metody je v TAP zrušení volitelné. Pokud operace umožňuje zrušení, poskytuje přetížení asynchronní metody, která přijímá token zrušení (<xref:System.Threading.CancellationToken> instance). Podle konvence je parametr pojmenovaný `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Asynchronní operace sleduje tento token kvůli žádostem o zrušení. Pokud obdrží žádost o zrušení, může vyhovět žádosti a operaci zrušit. Pokud žádost o zrušení vede předčasnému ukončení práce, vrátí metoda TAP úlohu, která končí <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu; neexistuje žádný k dispozici výsledek a není vyvolána žádná výjimka.  <xref:System.Threading.Tasks.TaskStatus.Canceled> Stavu je považován za konečný (dokončený) stav úlohy, společně s <xref:System.Threading.Tasks.TaskStatus.Faulted> a <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stavy. Proto pokud je úloha ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, jeho <xref:System.Threading.Tasks.Task.IsCompleted%2A> vrátí vlastnost `true`. Při dokončení úlohy <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu veškeré zaregistrované úkolu pokračování naplánováno nebo provedeno, pokud není možnost pokračování jako například <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> byl zadán k odhlášení pokračování. Veškerý kód, který asynchronně čeká na zrušenou úlohu pomocí funkcí jazyka i nadále běžel, ale obdrží <xref:System.OperationCanceledException> nebo výjimku z něj odvozenou. Kód, který je blokován při synchronním čekání na úlohu pomocí metod, jako <xref:System.Threading.Tasks.Task.Wait%2A> a <xref:System.Threading.Tasks.Task.WaitAll%2A> také nadále běží s výjimkou.  
  
 Pokud token zrušení požadoval zrušení před voláním metody TAP, která přijímá token, měla, by metoda TAP vrátit <xref:System.Threading.Tasks.TaskStatus.Canceled> úloh.  Pokud je však požadováno zrušení při spuštěné asynchronní operaci, asynchronní operace nemusí přijmout žádost o zrušení.  Vrácená úloha by měla končit <xref:System.Threading.Tasks.TaskStatus.Canceled> pouze stav, pokud operace končí v důsledku žádosti o zrušení. Pokud je zrušení požadováno, ale výsledek nebo výjimka se stále vytváří, úloha by měla končit <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> nebo <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu. 
 
 Pro asynchronní metody, které chcete je zveřejnit schopnost zrušit prvé řadě za záležitost nemusíte poskytovat přetížení, které nepřijímá token zrušení. Pro metody, které nelze zrušit, neposkytujte přetížení, která přijímají token zrušení. To pomáhá volajícímu určit, zda je skutečně možné zrušit cílovou metodu.  Uživatelský kód, který nepožaduje zrušení, může volat metodu, která přijímá <xref:System.Threading.CancellationToken> a poskytují <xref:System.Threading.CancellationToken.None%2A> jako hodnotu argumentu. <xref:System.Threading.CancellationToken.None%2A> je funkčně ekvivalentní výchozí <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>Hlášení průběhu (volitelné)  
 Některé asynchronní operace těží z poskytování oznámení o průběhu. Ta se obvykle používají k aktualizaci uživatelského rozhraní informacemi o průběhu asynchronní operace. 
 
 V TAP je průběh zpracován <xref:System.IProgress%601> rozhraní, které je předáno asynchronní metodě jako parametr, který je obvykle pojmenován `progress`.  Poskytnutí rozhraní průběhu při volání asynchronní metody pomáhá eliminovat konflikty časování, které jsou výsledkem nesprávného použití (to znamená, když obslužným rutinám, které jsou nesprávně zaregistrovány po zahájení operace, chybí aktualizace).  Důležitější je, že rozhraní průběhu podporuje různé implementace průběhu podle náročnosti kódu.  Náročný kód se bude například starat pouze o nejnovější aktualizaci průběhu nebo může chtít mít všechny aktualizace ve vyrovnávací paměti nebo může chtít vyvolat akci pro každou aktualizaci nebo může chtít řídit, zda je volání zařazeno do konkrétního vlákna. Všech těchto možností lze dosáhnout pomocí různých implementací rozhraní přizpůsobených potřebám konkrétního příjemce.  Jak se zrušení, implementace TAP by měly poskytnout <xref:System.IProgress%601> parametr pouze v případě, že rozhraní API podporuje oznámení o průběhu. 
 
 Například pokud `ReadAsync` metody popsané dříve v tomto článku se bude moct sestavu doposud, přečtených přechodném průběhu ve formě počet bajtů, zpětné volání průběhu může být <xref:System.IProgress%601> rozhraní:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Pokud `FindFilesAsync` metoda vrátí seznam všech souborů, které splňují konkrétní vzor hledání, zpětné volání průběhu může poskytnout odhad procenta dokončení a aktuální sadu částečných výsledků práce.  To může provést buď s uspořádanou n-ticí:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 nebo s datovým typem, který je specifický pro rozhraní API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 V druhém případě má zvláštní datový typ obvykle příponu `ProgressInfo`.  
  
 Pokud implementace TAP poskytují přetížení, která přijímají `progress` parametru, musí umožnit, aby argument představoval `null`, v takovém případě bude hlášené nijak nepokročila. Implementace TAP by měly vykazovat průběh <xref:System.Progress%601> objektu synchronně, což umožňuje asynchronní metodě rychle poskytnout průběh a umožnit příjemci průběhu určit, jak a kde nejlépe zpracovávat informace. Například instance průběhu může zvolit zařazování zpětných volání a vyvolat události na zachyceném synchronizačním kontextu.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T > Implementace  
 Rozhraní .NET Framework 4.5 poskytuje jedinou <xref:System.IProgress%601> implementace: <xref:System.Progress%601>. <xref:System.Progress%601> Třída je deklarována následovně:  
  
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
  
 Instance <xref:System.Progress%601> zpřístupňuje <xref:System.Progress%601.ProgressChanged> událost, která je vyvolána pokaždé, když asynchronní operace nahlásí aktualizaci průběhu. <xref:System.Progress%601.ProgressChanged> Událost se vyvolá při <xref:System.Threading.SynchronizationContext> objekt, který byl zachycen při <xref:System.Progress%601> instance byla vytvořena instance. Pokud nebyl k dispozici žádný kontext synchronizace, je použit výchozí kontext určený pro fond vláken. Pro tuto událost lze registrovat obslužné rutiny. Jedna obslužná rutina může být rovněž uvedena pro <xref:System.Progress%601> konstruktor pro usnadnění práce a chová se stejně jako obslužná rutina události <xref:System.Progress%601.ProgressChanged> událostí. Aktualizace průběhu jsou vyvolány asynchronně, aby se předešlo zpoždění asynchronní operace, zatímco se provádějí obslužné rutiny události. Jiné <xref:System.IProgress%601> implementace se může rozhodnout použít jinou sémantiku.  
  
## <a name="choosing-the-overloads-to-provide"></a>Volba poskytovaných přetížení  
 Pokud implementace TAP používá volitelné <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> a volitelné <xref:System.IProgress%601> parametry, může potenciálně vyžadovat až čtyři přetížení:  
  
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
  
 Pro kompenzaci dvou chybějících mezilehlých kombinací mohou vývojáři předat <xref:System.Threading.CancellationToken.None%2A> nebo výchozí hodnotu <xref:System.Threading.CancellationToken> pro `cancellationToken` parametr a `null` pro `progress` parametru.  
  
 Pokud očekáváte, že každé použití metody TAP bude podporovat zrušení nebo průběh, můžete vynechat přetížení, které nepřijímá odpovídající parametr.  
  
 Pokud se rozhodnete vystavit několik přetížení, aby byly zrušení nebo průběh volitelné, přetížení, která nepodporují zrušení nebo průběh by měla chovat, jako by předala <xref:System.Threading.CancellationToken.None%2A> pro zrušení nebo `null` pro průběh přetížením, která podporuje tyto.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vzory asynchronního programování](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zavádí tři vzory pro provádění asynchronních operací: synchronní vzor založený na úlohách (TAP), asynchronní programovací model (APM) a asynchronní vzor založený na událostech (EAP).|  
|[Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Popisuje tři způsoby implementace asynchronního vzoru založeného na úlohách (TAP): pomocí kompilátorů jazyka C# a Visual Basic v sadě Visual Studio, ručně nebo kombinací obou metod.|  
|[Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Popisuje, jak použít úlohy a zpětná volání k dosažení čekání bez blokování.|  
|[Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Popisuje způsob použití asynchronního vzoru založeného na úlohách (TAP) k implementaci asynchronního programovacího modelu (APM) a asynchronního vzoru založeného na událostech (EAP).|
