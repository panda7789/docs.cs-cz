---
title: Použití asynchronního vzoru založeného na úloze
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 723f07fb3fb4eda1c0071eec2b1d012948a10f77
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666559"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Použití asynchronního vzoru založeného na úloze

Při použití asynchronního vzoru založeného na úlohách (klepnutím) pro práci s asynchronními operacemi můžete pomocí zpětných volání dosáhnout čekání bez blokování.  Pro úlohy je to dosaženo prostřednictvím metod <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>, jako je. Jazyková asynchronní podpora skrývá zpětná volání tím, že umožňuje v normálním toku řízení očekávat asynchronní operace a kód generovaný kompilátorem poskytuje stejnou podporu na úrovni API.

## <a name="suspending-execution-with-await"></a>Pozastavení provádění s operátorem await
 Počínaje .NET Framework 4,5 můžete použít klíčové slovo [await](../../csharp/language-reference/keywords/await.md) C# v a [operátor await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic k asynchronnímu await <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objektům. Když očekáváte <xref:System.Threading.Tasks.Task> `await` , je výraz typu `void`. Když očekáváte <xref:System.Threading.Tasks.Task%601> `await` , je výraz typu `TResult`. `await` Výraz musí být uvnitř těla asynchronní metody. Další informace o C# a Visual Basic podpoře jazyků v .NET Framework 4,5 naleznete v tématu Specifikace jazyka C# a Visual Basic.

 V rámci pokrývá funkce await nainstaluje zpětné volání na úkol pomocí pokračování.  Toto zpětné volání pokračuje asynchronní metodou v okamžiku pozastavení. Pokud je asynchronní metoda obnovena, pokud se očekávaná operace úspěšně dokončila a byla <xref:System.Threading.Tasks.Task%601>a `TResult` , je vrácena.  <xref:System.Threading.Tasks.Task> Pokud nebo <xref:System.Threading.Tasks.Task%601> , který byl <xref:System.Threading.Tasks.TaskStatus.Canceled> ukončen<xref:System.OperationCanceledException> ve stavu, je vyvolána výjimka.  <xref:System.Threading.Tasks.Task> Pokud nebo <xref:System.Threading.Tasks.Task%601> , který byl ukončen ve <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu, je vyvolána výjimka, která způsobila chybu. `Task` Může dojít k chybě v důsledku více výjimek, ale je šířena pouze jedna z těchto výjimek. <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> Nicméně vlastnost<xref:System.AggregateException> vrací výjimku, která obsahuje všechny chyby.

 Pokud je kontext synchronizace (<xref:System.Threading.SynchronizationContext> objekt) spojen s vláknem, které provádělo asynchronní metodu v době pozastavení (například <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> Pokud vlastnost `null`není), asynchronní metoda pokračuje v tomto stejný kontext synchronizace pomocí <xref:System.Threading.SynchronizationContext.Post%2A> metody kontextu. V opačném případě spoléhá na to, že<xref:System.Threading.Tasks.TaskScheduler> Plánovač úloh (objekt) byl aktuální v době pozastavení. Obvykle se jedná o výchozí Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), který cílí na fond vláken. Tento Plánovač úloh určuje, zda má očekávaná asynchronní operace pokračovat v místě, kde byla dokončena, nebo zda má být obnovení plánováno. Výchozí Plánovač obvykle umožňuje spuštění pokračování ve vlákně, které čekalé operace dokončila.

 Když je volána asynchronní metoda, synchronně spustí tělo funkce až do prvního výrazu await v neočekávané instanci, která ještě nebyla dokončena, v tomto okamžiku se volání vrátí volajícímu. Pokud asynchronní metoda nevrátí `void` <xref:System.Threading.Tasks.Task> , je vrácen objekt nebo <xref:System.Threading.Tasks.Task%601> pro reprezentaci průběžného výpočtu. V asynchronní metodě, která není typu void, je-li k disřádku návratový příkaz nebo je dosaženo konce textu metody, je úloha dokončena v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> konečném stavu. Pokud Neošetřená výjimka způsobí, že ovládací prvek opustí tělo asynchronní metody, úloha skončí ve <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu. Pokud je tato výjimka <xref:System.OperationCanceledException>, úloha je místo toho ukončena <xref:System.Threading.Tasks.TaskStatus.Canceled> ve stavu. Tímto způsobem je výsledek nebo výjimka nakonec publikována.

 Existuje několik důležitých variant tohoto chování.  Z důvodu výkonu, pokud úloha již byla dokončena v době, kdy je úkol očekáván, řízení není získáno a funkce bude pokračovat v provádění.  Navíc návrat do původního kontextu není vždy požadovaným chováním a lze jej změnit. Tato informace je podrobněji popsána v následující části.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Konfigurace pozastavení a obnovení s využitím yield a ConfigureAwait
 Několik metod poskytuje větší kontrolu nad prováděním asynchronní metody. Například můžete použít <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metodu k zavedení bodu kluzu do asynchronní metody:

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 Jedná se o ekvivalent asynchronního účtování nebo plánování zpět do aktuálního kontextu.

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 Můžete také použít <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad přerušením a pokračováním v asynchronní metodě.  Jak bylo zmíněno dříve, aktuální kontext je zachycen v době pozastavení asynchronní metody a tento zachycený kontext slouží k vyvolání pokračování asynchronní metody při obnovení.  V mnoha případech se jedná o přesné chování, které požadujete.  V jiných případech se může stát, že nebudete mít pozor na kontext pokračování a můžete dosáhnout lepšího výkonu tím, že tyto příspěvky vyloučíte zpět do původního kontextu.  Pokud to chcete povolit, použijte <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> k informování operace await, aby se v kontextu nezachytává a obnovila, ale pokud chcete pokračovat v provádění, ať už je dokončená asynchronní operace, která se očekává:

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Zrušení asynchronní operace
 Počínaje .NET Framework 4 klepněte na metody, které podporují zrušení, poskytují alespoň jedno přetížení, které přijímá token zrušení (<xref:System.Threading.CancellationToken> objekt).

 Token zrušení se vytvoří prostřednictvím zdroje tokenu zrušení (<xref:System.Threading.CancellationTokenSource> Object).  <xref:System.Threading.CancellationTokenSource.Token%2A> Vlastnost zdroje vrátí token zrušení, který bude signalizována při volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> metody zdroje.  Například pokud chcete stáhnout jednu webovou stránku a chcete mít možnost operaci zrušit, vytvořte <xref:System.Threading.CancellationTokenSource> objekt, předejte jeho token do metody klepnutí a pak zavolejte <xref:System.Threading.CancellationTokenSource.Cancel%2A> metodu zdroje, až budete připraveni operaci zrušit:

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Chcete-li zrušit více asynchronních volání, můžete stejný token předat všem voláním:

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Nebo můžete stejný token předat do selektivní podmnožiny operací:

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 Žádosti o zrušení můžou být iniciované z libovolného vlákna.

 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> Hodnotu můžete předat libovolné metodě, která přijímá token zrušení, aby označovalo, že zrušení nebude nikdy požadováno.  To způsobí, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> že se vlastnost `false`vrátí a volaná metoda může odpovídajícím způsobem optimalizovat.  Pro účely testování můžete také předat předem zrušený token zrušení, jehož instance je vytvořena pomocí konstruktoru, který přijímá logickou hodnotu, k určení, zda má být token začínat již zrušeným nebo nestornovaným stavem.

 Tento přístup k zrušení má několik výhod:

- Stejný token zrušení můžete předat libovolnému počtu asynchronních a synchronních operací.

- Stejná žádost o zrušení může být předaná na libovolný počet posluchačů.

- Vývojář asynchronního rozhraní API má úplnou kontrolu nad tím, zda může být zrušení požadováno a kdy se může projevit.

- Kód, který využívá rozhraní API, může selektivně určit asynchronní vyvolání, na které se požadavky na zrušení rozšíří.

## <a name="monitoring-progress"></a>Sledování průběhu
 Některé asynchronní metody zpřístupňují průběh prostřednictvím rozhraní průběhu předaného do asynchronní metody.  Představte si například funkci, která asynchronně stáhne textový řetězec a společně způsob vyvolává aktualizace průběhu, které zahrnují procento stahování, které bylo doposud dokončeno.  Taková metoda by mohla být spotřebována v aplikaci Windows Presentation Foundation (WPF) následujícím způsobem:

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a>Použití integrovaného kombinátory založeného na úlohách
 <xref:System.Threading.Tasks> Obor názvů obsahuje několik metod pro vytváření a práci s úkoly.

### <a name="taskrun"></a>Task. Run
 Třída obsahuje několik <xref:System.Threading.Tasks.Task.Run%2A> metod, které umožňují <xref:System.Threading.Tasks.Task> snadno přesměrovat práci jako nebo <xref:System.Threading.Tasks.Task%601> do fondu vláken, například: <xref:System.Threading.Tasks.Task>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 Některé z těchto <xref:System.Threading.Tasks.Task.Run%2A> metod, jako je <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> například přetížení, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> existují jako zkratky pro metodu.  Další přetížení, jako <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>je, umožňují použití operátoru await v rámci pracovní zátěže, například:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 Taková přetížení jsou logicky ekvivalentní použití <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody ve spojení <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> s metodou rozšíření v Task Parallel Library.

### <a name="taskfromresult"></a>Task. FromResult
 Použijte metodu ve scénářích, kdy již data mohou být k dispozici a stačí je vrátit z metody vracené úlohou <xref:System.Threading.Tasks.Task%601>do: <xref:System.Threading.Tasks.Task.FromResult%2A>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a>Task.WhenAll
 <xref:System.Threading.Tasks.Task.WhenAll%2A> Použijte metodu pro asynchronní čekání na více asynchronních operací, které jsou reprezentovány jako úkoly.  Metoda má více přetížení, které podporují sadu neobecných úkolů nebo nejednotnou sadu obecných úloh (například asynchronní čekání na více operací vracejících anulování nebo asynchronní čekání na více metod vracejících hodnoty, kde Každá hodnota může mít jiný typ a podporovat jednotnou sadu obecných úloh (například asynchronní čekání na vícenásobné `TResult`návratové metody).

 Řekněme, že chcete odesílat e-mailové zprávy několika zákazníkům. Posílání zpráv se můžete překrývat, takže nečekáte na dokončení jedné zprávy, než odešlete další. Můžete také zjistit, kdy byly operace odeslání dokončeny a zda došlo k chybám:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Tento kód explicitně nezpracovává výjimky, ke kterým může dojít, ale umožňuje výjimky rozšířit `await` na výsledný úkol z. <xref:System.Threading.Tasks.Task.WhenAll%2A>  Chcete-li zpracovat výjimky, můžete použít následující kód:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 V tomto případě, pokud dojde k chybě jakékoli asynchronní operace, všechny výjimky budou konsolidovány do <xref:System.AggregateException> výjimky, která je uložena <xref:System.Threading.Tasks.Task> v objektu <xref:System.Threading.Tasks.Task.WhenAll%2A> , který je vrácen z metody.  `await` Klíčové slovo ale rozšíří jenom jednu z těchto výjimek.  Pokud chcete kontrolovat všechny výjimky, můžete přepsat předchozí kód následujícím způsobem:

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 Podívejme se na příklad asynchronního stahování více souborů z webu.  V tomto případě mají všechny asynchronní operace homogenní typy výsledků a je snadné získat přístup k výsledkům:

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Můžete použít stejné techniky zpracování výjimek, které jsme probrali v předchozím scénáři vracejícím anulování:

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a>Task.WhenAny
 <xref:System.Threading.Tasks.Task.WhenAny%2A> Metodu lze použít k asynchronnímu čekání pouze na jednu z několika asynchronních operací, které jsou reprezentovány jako úkoly k dokončení.  Tato metoda slouží ke čtyřem primárním případům použití:

- Redundance  Operace se provádí víckrát a vybere se ta, která se nejdřív dokončí (například kontaktování více webových služeb na základě akcií, která vytvoří jeden výsledek a vybere tu, která dokončí nejrychlejší).

- Potřeba prokládání  Spuštění více operací a čekání na dokončení všech z nich, ale jejich zpracování po dokončení.

- Omezování  Umožnění dalších operací, které začnou být dokončeny s ostatními.  Toto je rozšíření scénáře pro proplutí.

- Předčasné Bailout:  Například operace reprezentovaná úlohou T1 se může seskupovat v <xref:System.Threading.Tasks.Task.WhenAny%2A> úloze s jiným úkolem T2 a <xref:System.Threading.Tasks.Task.WhenAny%2A> na úlohu můžete počkat. Úloha T2 by mohla představovat časový limit nebo zrušení nebo nějaký jiný signál, který způsobí, že se <xref:System.Threading.Tasks.Task.WhenAny%2A> úkol nedokončí, než se T1 dokončí.

#### <a name="redundancy"></a>Redundance
 Vezměte v úvahu případ, kdy si přejete rozhodnout, jestli chcete koupit zásobu.  K dispozici je několik webových služeb s doporučeními pro základní zdroje, ale v závislosti na denním zatížení může být každá služba v různou dobu pomalejší.  Tuto <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu můžete použít k získání oznámení, když se dokončí jakákoli operace:

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 Na rozdíl <xref:System.Threading.Tasks.Task.WhenAll%2A>od, což vrátí nezabalené výsledky všech úloh, které byly úspěšně <xref:System.Threading.Tasks.Task.WhenAny%2A> dokončeny, vrátí úkol, který byl dokončen. Pokud úloha selže, je důležité, abyste věděli, že se nezdařila, a pokud je úloha úspěšná, je důležité znát, ke které úloze je vrácená hodnota přidružená.  Proto potřebujete získat přístup k výsledku vráceného úkolu nebo ho očekávat více, jak ukazuje tento příklad.

 Stejně jako <xref:System.Threading.Tasks.Task.WhenAll%2A>v případě musíte být schopni vyhovět výjimkám.  Vzhledem k tomu, že obdržíte dokončenou úlohu zpět, můžete očekávat, že vrácená úloha bude obsahovat `try/catch` chyby, a odpovídajícím způsobem, například:

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 Kromě toho, i když se první úkol úspěšně dokončí, můžou následné úkoly selhat.  V tomto okamžiku máte několik možností, jak řešit výjimky:  Můžete počkat, až se dokončí všechny spuštěné úlohy, a v takovém případě můžete použít <xref:System.Threading.Tasks.Task.WhenAll%2A> tuto metodu, nebo se můžete rozhodnout, že jsou všechny výjimky důležité a musí být protokolovány.  K tomu můžete použít pokračování pro příjem oznámení, když se úkoly asynchronně dokončují:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 nebo:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 nebo dokonce:

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 Nakonec můžete chtít zrušit všechny zbývající operace:

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a>Potřeba prokládání
 Vezměte v úvahu případ, kdy stahujete obrázky z webu a zpracováváte jednotlivé Image (například přidáním obrázku do ovládacího prvku uživatelského rozhraní).  Je nutné provést zpracování postupně ve vlákně uživatelského rozhraní, ale chcete stáhnout obrázky jako souběžně. Nechcete také přidržet obrázky do uživatelského rozhraní, dokud se všechny nestáhnou – chcete je přidat po dokončení:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 Můžete také použít přejezd na scénář, který zahrnuje výpočetně náročné zpracování na <xref:System.Threading.ThreadPool> stažených obrázcích, například:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a>Omezování
 Vezměte v úvahu příklad prokládání s tím rozdílem, že uživatel je stahuje, takže mnoho imagí, které je potřeba stáhnout, je nutné omezit. například chcete, aby bylo možné současně provést pouze určitý počet souborů ke stažení. K tomuto účelu můžete spustit podmnožinu asynchronních operací.  Po dokončení operací můžete spustit další operace, které zabírají místo:

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a>Předčasné Bailout
 Vezměte v úvahu, že budete čekat asynchronně, než se operace dokončí, a současně reagovat na požadavek na zrušení uživatele (například uživatel kliknul na tlačítko Storno). Tento scénář je znázorněný v následujícím kódu:

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 Tato implementace znovu povolí uživatelské rozhraní hned po rozhodnutí Bail, ale neruší základní asynchronní operace.  Další možností je zrušit nedokončené operace, když se rozhodnete Bail, ale nebudete moci znovu vytvořit uživatelské rozhraní, dokud se operace neprojeví, potenciálně v důsledku ukončení v důsledku žádosti o zrušení:

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 Dalším příkladem předčasného Bailout je použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metody ve spojení <xref:System.Threading.Tasks.Task.Delay%2A> s metodou, jak je popsáno v další části.

### <a name="taskdelay"></a>Task.Delay
 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metodu lze použít k zavedení pozastavení do asynchronního zpracování metody.  To je užitečné pro mnoho druhů funkcí, včetně vytváření smyček cyklického dotazování a zpoždění manipulace s uživatelským vstupem pro předem stanovenou dobu.  Metoda může být také užitečná v kombinaci s <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pro implementaci časových limitů na await. <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>

 Pokud úkol, který je součástí větší asynchronní operace (například webové služby ASP.NET), trvá příliš dlouho, může to být způsobeno tím, že by celková operace byla neúspěšná, zejména v případě, že se nepovede dřív.  Z tohoto důvodu je důležité mít při čekání na asynchronní operaci časový limit.  <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Synchronní metody, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / akceptují hodnoty časového limitu, ale odpovídající <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše zmíněný <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>metody ne.  Místo toho můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> v kombinaci k implementaci časového limitu.

 Například v aplikaci uživatelského rozhraní řekněme, že chcete stáhnout image a zakázat uživatelské rozhraní při stahování image. Pokud ale stahování trvá příliš dlouho, budete chtít znovu povolit uživatelské rozhraní a zahodit stahování:

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 Totéž platí pro více souborů ke stažení, <xref:System.Threading.Tasks.Task.WhenAll%2A> protože vrátí úlohu:

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a>Sestavování kombinátory založených na úlohách
 Vzhledem k tomu, že úloha může zcela představovat asynchronní operaci a poskytovat synchronní a asynchronní možnosti pro připojení k operaci, načítání výsledků a tak dále, můžete vytvářet užitečné knihovny kombinátory, které vytvářejí úkoly. Sestavujte větší vzory.  Jak je popsáno v předchozí části, .NET Framework obsahuje několik integrovaných kombinátory, ale můžete si také vytvořit vlastní. Následující části obsahují několik příkladů potenciálních metod a typů kombinátorem.

### <a name="retryonfault"></a>RetryOnFault
 V mnoha situacích můžete zkusit operaci zopakovat, pokud se předchozí pokus nezdaří.  `RetryOnFault` V případě synchronního kódu můžete vytvořit pomocnou metodu, například v následujícím příkladu, k provedení této akce:

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Můžete vytvořit téměř identickou pomocnou metodu pro asynchronní operace, které jsou implementovány klepnutím a následně vracet úlohy:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Pak můžete použít tuto kombinátorem ke kódování opakovaných pokusů do logiky aplikace. například:

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 `RetryOnFault` Funkci můžete dál rozšířit. Funkce například může přijmout další `Func<Task>` , který bude vyvolán mezi opakovanými pokusy, aby bylo možné určit, kdy se má operace opakovat. Příklad:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 Potom můžete funkci použít následujícím způsobem, aby před opakováním operace čekala na sekundu:

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne
 V některých případech můžete využít redundanci a zlepšit latenci operace a šance na úspěch.  Vezměte v úvahu více webových služeb, které poskytují nabídky, ale v různou dobu může každá služba poskytovat různé úrovně kvality a doby odezvy.  Pokud chcete řešit tyto výkyvy, můžete vydávat požadavky na všechny webové služby a hned po obdržení odpovědi zrušit zbývající požadavky.  Můžete implementovat pomocnou funkci, která usnadňuje implementaci tohoto běžného vzoru spouštění více operací, čekání na jakékoli a následné zrušení zbytku. `NeedOnlyOne` Funkce v následujícím příkladu znázorňuje tento scénář:

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 Tuto funkci pak můžete použít následujícím způsobem:

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>Prokládané operace
 Při práci s velmi velkým počtem úloh je možné <xref:System.Threading.Tasks.Task.WhenAny%2A> využít potenciální potíže s výkonem při použití metody pro podporu scénáře prokládaných dat.  Každé volání, <xref:System.Threading.Tasks.Task.WhenAny%2A> které má za následek pokračování zaregistrované u každého úkolu. Pro N počet úkolů to vede k pokračování v O (N2), které se vytváří po dobu životnosti operace proplutí.  Pokud pracujete s velkou sadou úkolů, můžete k vyřešení problému s výkonem použít kombinátorem (`Interleaved` v následujícím příkladu):

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 Pak můžete použít kombinátorem ke zpracování výsledků úloh po jejich dokončení. například:

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenAllOrFirstException
 V určitých bodových nebo sběrných scénářích můžete chtít počkat na všechny úlohy v sadě, pokud jedna z nich selže, a v takovém případě se chcete přestat čekat, jakmile dojde k výjimce.  To lze provést pomocí metody `WhenAllOrFirstException` kombinátorem, jako v následujícím příkladu:

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a>Vytváření datových struktur založených na úlohách
 Kromě možnosti vytvářet vlastní kombinátory založenou na úlohách, které mají datovou strukturu <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> které představují jak výsledky asynchronní operace, tak i nutná synchronizace pro připojení, usnadňují to velmi výkonné typ, na který se mají vytvářet vlastní datové struktury, které se mají použít v asynchronních scénářích.

### <a name="asynccache"></a>AsyncCache
 Jedním z důležitých aspektů úkolu je, že může být předána více příjemcům, z nichž to může očekávat, zaregistrovat pokračování s ním, získat výsledek nebo výjimky (v případě <xref:System.Threading.Tasks.Task%601>) a tak dále.  Tato technologie <xref:System.Threading.Tasks.Task> je <xref:System.Threading.Tasks.Task%601> naprosto vhodná pro použití v asynchronní infrastruktuře ukládání do mezipaměti.  Tady je příklad malé, ale výkonné asynchronní mezipaměti postavené nad <xref:System.Threading.Tasks.Task%601>:

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 `TKey` <xref:System.Threading.Tasks.Task%601> [AsyncCache\<TKey třída TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) přijímá jako delegáta funkce, která přijímá a vrátí.  Všechny dříve použité hodnoty z mezipaměti se ukládají do interního slovníku a `AsyncCache` zajišťují, že se pro každý klíč generuje jenom jeden úkol, a to i v případě, že k mezipaměti dojde souběžně.

 Můžete například sestavit mezipaměť pro stažené webové stránky:

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Tuto mezipaměť pak můžete použít v asynchronních metodách vždy, když potřebujete obsah webové stránky. `AsyncCache` Třída zajišťuje, že budete stahovat co nejvíce stránek a ukládá výsledky do mezipaměti.

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection
 Úkoly můžete použít také k vytváření datových struktur pro koordinaci asynchronních aktivit.  Vezměte v úvahu jeden z klasických paralelních vzorů návrhu: producent/příjemce.  V tomto vzoru producenti generují data, která jsou využívána příjemci, a producenti a spotřebitelé můžou běžet paralelně. Například příjemce zpracuje položku 1, která byla dříve vygenerována výrobcem, který nyní vyrábí položku 2.  Pro vzorek producent/příjemce invariably potřebovat určitou datovou strukturu pro ukládání práce vytvořené producenty, aby se příjemci mohli dostat k oznámením o nových datech a najít je, když jsou k dispozici.

 Tady je jednoduchá datová struktura postavená na úkolech, která umožňuje použití asynchronních metod jako výrobců a spotřebitelů:

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 Pomocí této struktury dat můžete napsat kód, například následující:

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<xref:System.Threading.Tasks.Dataflow> Obor názvů <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> zahrnuje typ, který lze použít podobným způsobem, ale bez nutnosti sestavení vlastního typu kolekce:

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> Obor názvů je k dispozici v .NET Framework 4,5 až **NuGet.** <xref:System.Threading.Tasks.Dataflow> Chcete-li nainstalovat sestavení, které <xref:System.Threading.Tasks.Dataflow> obsahuje obor názvů, otevřete projekt v aplikaci Visual Studio, v nabídce projekt vyberte možnost **Spravovat balíčky NuGet** a vyhledejte balíček Microsoft. tpl. Dataflow online.

## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
