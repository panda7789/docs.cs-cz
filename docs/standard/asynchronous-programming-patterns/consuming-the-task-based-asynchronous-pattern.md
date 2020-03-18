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
ms.openlocfilehash: f80e6ae520ab03c0f5f4edc30c0b7102193ee6c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139811"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Použití asynchronního vzoru založeného na úloze

Při použití task-based asynchronní vzor (TAP) pro práci s asynchronní operace, můžete použít zpětná volání k dosažení čekání bez blokování.  U úkolů je toho dosaženo <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>prostřednictvím metod, jako je například . Jazyková asynchronní podpora skryje zpětná volání tím, že umožňuje asynchronní operace, které mají být očekávány v rámci normálního toku řízení a kód generovaný kompilátorem poskytuje stejnou podporu na úrovni rozhraní API.

## <a name="suspending-execution-with-await"></a>Pozastavení provádění s Čeká
 Počínaje rozhraním .NET Framework 4.5 můžete použít klíčové slovo [await](../../csharp/language-reference/operators/await.md) v jazyce C# a operátor <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> [Await](../../visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic asynchronně await a objekty. Pokud čekáte <xref:System.Threading.Tasks.Task>na , `await` výraz je `void`typu . Pokud čekáte <xref:System.Threading.Tasks.Task%601>na , `await` výraz je `TResult`typu . Výraz `await` musí dojít uvnitř těla asynchronní metody. Další informace o podpoře jazyka C# a visual basicv rozhraní .NET Framework 4.5 naleznete specifikace jazyka C# a visual basic.

 Pod kryty await funkce nainstaluje zpětné volání na úlohu pomocí pokračování.  Toto zpětné volání obnoví asynchronní metodu v okamžiku pozastavení. Po obnovení asynchronní metody, pokud byla očekávaná operace úspěšně <xref:System.Threading.Tasks.Task%601>dokončena `TResult` a byla , je vrácena její.  Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> které bylo očekáváno <xref:System.Threading.Tasks.TaskStatus.Canceled> skončil <xref:System.OperationCanceledException> ve stavu, je vyvolána výjimka.  Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> které bylo očekáváno <xref:System.Threading.Tasks.TaskStatus.Faulted> skončil ve stavu, je vyvolána výjimka, která způsobila jeho chybu. Může `Task` chyba v důsledku více výjimek, ale pouze jedna z těchto výjimek je rozšířena. Vlastnost však <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vrátí <xref:System.AggregateException> výjimku, která obsahuje všechny chyby.

 Pokud kontext synchronizace<xref:System.Threading.SynchronizationContext> ( objekt) je přidružen k podprocesu, který byl provádění asynchronní metody <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> v `null`době pozastavení (například pokud vlastnost není ), asynchronní metoda <xref:System.Threading.SynchronizationContext.Post%2A> pokračuje ve stejném kontextu synchronizace pomocí metody kontextu. V opačném případě se spoléhá na<xref:System.Threading.Tasks.TaskScheduler> plánovač úloh ( objekt), který byl aktuální v době pozastavení. Obvykle se jedná o výchozí plánovač<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>úloh ( ), který cílí na fond vláken. Tento plánovač úloh určuje, zda by očekávaná asynchronní operace měla pokračovat tam, kde byla dokončena, nebo zda má být naplánována obnova. Výchozí plánovač obvykle umožňuje pokračování spustit ve vlákně, které byla dokončena očekávaná operace.

 Při volání asynchronní metoda synchronně provede tělo funkce až do první await výraz na čekat nouzi, která ještě nebyla dokončena, na kterém místě vyvolání vrátí volajícímu. Pokud asynchronní metoda nevrátí `void`, <xref:System.Threading.Tasks.Task> je <xref:System.Threading.Tasks.Task%601> vrácen a nebo objekt představující probíhající výpočtu. V nevoid asynchronní metody, pokud je zjištěn příkaz return nebo je dosaženo konce těla metody, úkol je dokončen v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> konečném stavu. Pokud neošetřená výjimka způsobí, že ovládací prvek opustit tělo asynchronní metody, úloha končí ve <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu. Pokud je tato <xref:System.OperationCanceledException>výjimka , úloha místo toho končí ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu. Tímto způsobem je nakonec publikován výsledek nebo výjimka.

 Existuje několik důležitých variant tohoto chování.  Z důvodů výkonu, pokud úkol již dokončena v době, kdy je úkol očekáván, ovládací prvek není výnosný a funkce pokračuje v provádění.  Kromě toho návrat do původního kontextu není vždy požadované chování a lze změnit; to je podrobněji popsáno v další části.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Konfigurace pozastavení a obnovení s yield a configureAwait
 Několik metod poskytují větší kontrolu nad provádění asynchronní metody. Metodu <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> můžete například použít k zavedení bodu výnosu do asynchronní metody:

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 To je ekvivalentní asynchronně zaúčtování nebo plánování zpět do aktuálního kontextu.

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

 Můžete také použít <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad pozastavení a obnovení v asynchronní metody.  Jak již bylo zmíněno dříve, ve výchozím nastavení aktuální kontext je zachycen v době pozastavení asynchronní metody a zachycené kontextu se používá k vyvolání pokračování asynchronní metody při obnovení.  V mnoha případech je to přesně požadované chování.  V ostatních případech se nemusí starat o kontext pokračování a můžete dosáhnout lepšího výkonu tím, že se těmto příspěvkům vrátíte do původního kontextu.  Chcete-li to <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> povolit, použijte metodu k informování operace await, která nemá zachytit a pokračovat v kontextu, ale pokračovat v provádění všude tam, kde byla dokončena asynchronní operace, která byla právě očekávána:

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Zrušení asynchronní operace
 Počínaje rozhraním .NET Framework 4, metody TAP, které podporují zrušení poskytují<xref:System.Threading.CancellationToken> alespoň jedno přetížení, které přijímá token zrušení (objekt).

 Token zrušení je vytvořen prostřednictvím<xref:System.Threading.CancellationTokenSource> zdroje tokenu zrušení (objektu).  <xref:System.Threading.CancellationTokenSource.Token%2A> Vlastnost zdroje vrátí token zrušení, který bude signalizován při <xref:System.Threading.CancellationTokenSource.Cancel%2A> volání metody zdroje.  Chcete-li například stáhnout jednu webovou stránku a chcete mít možnost <xref:System.Threading.CancellationTokenSource> operaci zrušit, vytvořte objekt, předajte jeho <xref:System.Threading.CancellationTokenSource.Cancel%2A> token metodě TAP a poté zavoláte metodu zdroje, až budete připraveni operaci zrušit:

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Chcete-li zrušit více asynchronních vyvolání, můžete předat stejný token všem vyvoláním:

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Nebo můžete předat stejný token selektivní podmnožině operací:

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 Žádosti o zrušení mohou být iniciovány z libovolného vlákna.

 Můžete předat <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> hodnotu libovolnou metodu, která přijímá token zrušení označující, že zrušení nikdy nebude požadováno.  To způsobí, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> že `false`vlastnost vrátit a volaná metoda můžete optimalizovat odpovídajícím způsobem.  Pro účely testování můžete také předat předzrušený token zrušení, který je vytvořen pomocí konstruktoru, který přijímá logickou hodnotu k označení, zda by měl token spustit v již zrušeném nebo nezrušitelném stavu.

 Tento přístup ke zrušení má několik výhod:

- Můžete předat stejný token zrušení libovolný počet asynchronních a synchronních operací.

- Stejný požadavek na zrušení může být množí libovolný počet posluchačů.

- Vývojář asynchronní rozhraní API má úplnou kontrolu nad tím, zda může být požadováno zrušení a kdy se může projevit.

- Kód, který spotřebovává rozhraní API může selektivně určit asynchronní vyvolání, které budou rozšířeny požadavky na zrušení.

## <a name="monitoring-progress"></a>Sledování průběhu
 Některé asynchronní metody zveřejňují průběh prostřednictvím rozhraní průběhu předaných do asynchronní metody.  Zvažte například funkci, která asynchronně stáhne řetězec textu a cestou vyvolá aktualizace průběhu, které zahrnují procento stahování, které bylo dosud dokončeno.  Tato metoda by mohla být spotřebována v aplikaci WPF (Windows Presentation Foundation) takto:

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
## <a name="using-the-built-in-task-based-combinators"></a>Použití integrovaných kombinátorů založených na úlohách
 Obor <xref:System.Threading.Tasks> názvů obsahuje několik metod pro skládání a práci s úkoly.

### <a name="taskrun"></a>Úloha.Spustit
 Třída <xref:System.Threading.Tasks.Task> obsahuje <xref:System.Threading.Tasks.Task.Run%2A> několik metod, které umožňují snadno <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> offload práce jako nebo do fondu vláken, například:

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

 Některé z <xref:System.Threading.Tasks.Task.Run%2A> těchto metod, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> jako je například <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> přetížení, existují jako zkratka pro metodu.  Další přetížení, například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, umožňují použít await v rámci vyložené práce, například:

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

 Taková přetížení jsou logicky ekvivalentní <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> použití metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> ve spojení s metodou rozšíření v paralelní knihovně úloh.

### <a name="taskfromresult"></a>Task.FromResult
 Metodu <xref:System.Threading.Tasks.Task.FromResult%2A> použijte ve scénářích, kde data již mohou být k dispozici a je <xref:System.Threading.Tasks.Task%601>třeba je vrátit z metody vrácení úlohy, která byla zrušena do :

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
 Pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A> metody asynchronně čekat na více asynchronních operací, které jsou reprezentovány jako úkoly.  Metoda má více přetížení, které podporují sadu neobecných úloh nebo nejednotné sady obecných úloh (například asynchronně čekání na více operací vrácení prázdnoty nebo asynchronně čekání na více metod vrácení hodnoty, kde každá hodnota může mít jiný `TResult`typ) a podporovat jednotnou sadu obecných úloh (například asynchronně čekání na více metod vrácení).

 Řekněme, že chcete posílat e-mailové zprávy několika zákazníkům. Odesílání zpráv můžete překrývat, takže před odesláním další zprávy nečekáte na dokončení jedné zprávy. Můžete také zjistit, kdy byly operace odesílání dokončeny a zda došlo k chybám:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Tento kód explicitně nezpracovává výjimky, které mohou nastat, ale `await` umožňuje výjimky šířit <xref:System.Threading.Tasks.Task.WhenAll%2A>z na výsledné úlohy z .  Chcete-li zpracovat výjimky, můžete použít kód, jako je například následující:

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

 V tomto případě pokud se nezdaří všechny asynchronní operace, všechny <xref:System.AggregateException> výjimky budou konsolidovány ve výjimce, která je uložena <xref:System.Threading.Tasks.Task> v tom, který je vrácen z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.  Klíčové `await` slovo je však šířena pouze jednou z těchto výjimek.  Pokud chcete prozkoumat všechny výjimky, můžete přepsat předchozí kód takto:

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

 Podívejme se na příklad stahování více souborů z webu asynchronně.  V tomto případě všechny asynchronní operace mají homogenní typy výsledků a je snadný přístup k výsledkům:

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Můžete použít stejné techniky zpracování výjimek, které jsme probrali v předchozím scénáři vrácení prázdnoty:

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
 Metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete použít k asynchronnímu čekání pouze na jednu z více asynchronních operací reprezentované jako úkoly k dokončení.  Tato metoda slouží čtyři případy primární použití:

- Redundance: Provedení operace vícekrát a výběr té, která dokončí první (například kontaktování více webových služeb nabídky akcií, které vytvoří jeden výsledek a vybere ten, který dokončí nejrychlejší).

- Prokládání: Spuštění více operací a čekání na dokončení všech, ale jejich zpracování po dokončení.

- Omezení: Povolení dalších operací začít jako ostatní dokončení.  Toto je rozšíření prokládání scénář.

- Včasná výpomoc: Například operace reprezentovaná úkolem t1 může být seskupena do úkolu s jiným úkolem <xref:System.Threading.Tasks.Task.WhenAny%2A> t2 a můžete na <xref:System.Threading.Tasks.Task.WhenAny%2A> úkol počkat. Úloha t2 může představovat časový čas nebo zrušení nebo <xref:System.Threading.Tasks.Task.WhenAny%2A> jiný signál, který způsobí dokončení úkolu před dokončením t1.

#### <a name="redundancy"></a>Redundance
 Vezměme si případ, kdy chcete učinit rozhodnutí o tom, zda koupit akcie.  Existuje několik webových služeb doporučení akcií, kterým důvěřujete, ale v závislosti na každodenním zatížení může každá služba skončit v různých časech pomalá.  Tuto metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete použít k přijetí oznámení po dokončení jakékoli operace:

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

 Na <xref:System.Threading.Tasks.Task.WhenAll%2A>rozdíl od , který vrátí nezabalené výsledky <xref:System.Threading.Tasks.Task.WhenAny%2A> všech úkolů, které byly úspěšně dokončeny, vrátí úkol, který byl dokončen. Pokud se úkol nezdaří, je důležité vědět, že se nezdařilo, a pokud je úkol úspěšný, je důležité vědět, ke kterému úkolu je vrácená hodnota přidružena.  Proto je třeba získat přístup k výsledku vrácené úlohy nebo dále čekat, jak ukazuje tento příklad.

 Stejně <xref:System.Threading.Tasks.Task.WhenAll%2A>jako u , musíte být schopni vyhovět výjimkám.  Vzhledem k tomu, že obdržíte dokončený úkol zpět, můžete čekat `try/catch` vrácené úlohy mít chyby šířené a je odpovídajícím způsobem; například:

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

 Navíc i v případě, že první úkol úspěšně dokončí, následné úkoly může selhat.  V tomto okamžiku máte několik možností pro řešení výjimek: Můžete počkat, dokud nebudou dokončeny <xref:System.Threading.Tasks.Task.WhenAll%2A> všechny spuštěné úkoly, v takovém případě můžete použít metodu, nebo se můžete rozhodnout, že všechny výjimky jsou důležité a musí být zaznamenány.  Za tímto účelem můžete použít pokračování přijímat oznámení po dokončení úlohami asynchronně:

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

#### <a name="interleaving"></a>Prokládání
 Zvažte případ, kdy stahujete obrázky z webu a zpracováváte jednotlivé obrázky (například přidání obrázku do ovládacího prvku uživatelského rozhraní).  Je třeba provést zpracování postupně ve vlákně uživatelského rozhraní, ale chcete stáhnout obrázky co nejaktuálněji. Také nechcete zdržovat přidávání obrázků do hlavního nastavení, dokud nejsou všechny stažené – chcete je přidat po dokončení:

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

 Můžete také použít prokládání na scénář, který zahrnuje <xref:System.Threading.ThreadPool> výpočtově náročné zpracování na stažené obrázky; například:

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

#### <a name="throttling"></a>Throttling
 Vezměme si příklad prokládání, s tím rozdílem, že uživatel stahuje tolik obrázků, že stahování musí být omezen; například chcete, aby současně došlo pouze k určitému počtu stahování. Chcete-li toho dosáhnout, můžete spustit podmnožinu asynchronních operací.  Po dokončení operací můžete zahájit další operace, které zaujmou jejich místo:

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

#### <a name="early-bailout"></a>Včasná výpomoc
 Vezměte v úvahu, že asynchronně čekáte na dokončení operace a současně reagujete na požadavek na zrušení uživatele (například uživatel klepnul na tlačítko storno). Následující kód ilustruje tento scénář:

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

 Tato implementace znovu povolí uživatelské rozhraní, jakmile se rozhodnete provést vyřazení, ale nezruší základní asynchronní operace.  Další alternativou by bylo zrušit čekající operace, když se rozhodnete provést kauci, ale neobnovit uživatelské rozhraní, dokud operace skutečně dokončeny, potenciálně z důvodu předčasného ukončení z důvodu žádosti o zrušení:

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

 Dalším příkladem včasné horečné pomoci zahrnuje použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metody ve spojení s <xref:System.Threading.Tasks.Task.Delay%2A> metodou, jak je popsáno v další části.

### <a name="taskdelay"></a>Task.Delay
 Metodu <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> můžete použít k zavedení pozastavení do spuštění asynchronní metody.  To je užitečné pro mnoho druhů funkcí, včetně vytváření smyčk dotazování a zpoždění zpracování vstupu uživatele pro předem určené časové období.  Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> může být také užitečné <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> v kombinaci s pro implementaci časové odnože na čeká.

 Pokud úkol, který je součástí větší asynchronní operace (například ASP.NET webové služby) trvá příliš dlouho na dokončení, celková operace může utrpět, zejména v případě, že se nezdaří někdy dokončit.  Z tohoto důvodu je důležité mít možnost časový režim při čekání na asynchronní operace.  <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Synchronní , <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody přijímají hodnoty časového času, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ale odpovídající <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše uvedené metody nikoli.  Místo toho můžete <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> použít a v kombinaci k implementaci časového odčasového času.

 Například v aplikaci ui řekněme, že chcete stáhnout obrázek a zakázat ui při stahování obrázku. Pokud však stahování trvá příliš dlouho, chcete znovu povolit ui a zahodit stahování:

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

 Totéž platí pro více stažení, protože <xref:System.Threading.Tasks.Task.WhenAll%2A> vrátí úkol:

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

## <a name="building-task-based-combinators"></a>Vytváření kombinátorů založených na úlohách
 Vzhledem k tomu, že úloha je schopna zcela reprezentovat asynchronní operaci a poskytovat synchronní a asynchronní funkce pro připojení k operaci, načítání jejích výsledků a tak dále, můžete vytvořit užitečné knihovny kombinátorů, které vytvářejí úkoly vytvářet větší vzory.  Jak je popsáno v předchozí části rozhraní .NET Framework obsahuje několik předdefinovaných kombinátorů, ale můžete také vytvořit vlastní. Následující části obsahují několik příkladů možných metod a typů kombinátoru.

### <a name="retryonfault"></a>Opakováníon-fault
 V mnoha situacích můžete chtít opakovat operaci, pokud předchozí pokus selže.  Pro synchronní kód můžete vytvořit pomocnou metodu, například `RetryOnFault` v následujícím příkladu k dosažení tohoto cíle:

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

 Můžete vytvořit téměř identickou pomocnou metodu pro asynchronní operace, které jsou implementovány pomocí tap a tím vrátit úkoly:

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

 Potom můžete použít tento kombinátor ke kódování opakování do logiky aplikace; například:

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 Můžete rozšířit `RetryOnFault` funkci dále. Funkce může například přijmout `Func<Task>` jinou, která bude vyvolána mezi opakovanými pokusy o určení, kdy chcete operaci zkusit znovu; například:

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

 Funkci pak můžete použít následujícím způsobem a počkat na chvíli před opakováním operace:

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne
 V některých proto můžete využít redundance ke zlepšení latence operace a šancí na úspěch.  Zvažte více webových služeb, které poskytují kurzy akcií, ale v různých denních dobách může každá služba poskytovat různé úrovně kvality a doby odezvy.  Chcete-li se vypořádat s těmito výkyvy, můžete vydávat žádosti na všechny webové služby, a jakmile dostanete odpověď od jednoho, zrušit zbývající požadavky.  Můžete implementovat pomocnou funkci, která usnadňuje implementaci tohoto společného vzoru spuštění více operací, čekání na všechny a následné zrušení ostatních. Funkce `NeedOnlyOne` v následujícím příkladu ilustruje tento scénář:

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

### <a name="interleaved-operations"></a>Prokládaná operace
 Při práci s velmi velkými <xref:System.Threading.Tasks.Task.WhenAny%2A> sadami úkolů je potenciální problém s výkonem pomocí metody pro podporu prokládání. Každé volání <xref:System.Threading.Tasks.Task.WhenAny%2A> má za následek pokračování je registrována u každého úkolu. Pro N počet úkolů, to má za následek O(N<sup>2</sup>) pokračování vytvořené po dobu životnosti operace prokládání. Pokud pracujete s velkou sadou úkolů, můžete k`Interleaved` řešení problému s výkonem použít kombinátor (v následujícím příkladu):

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

 Kombinátor pak můžete použít ke zpracování výsledků úkolů při jejich dokončení; například:

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>Když AllOrFirstException
 V některých scénářích scatter/gather můžete chtít počkat na všechny úkoly v sadě, pokud jeden z nich chyby, v takovém případě chcete přestat čekat, jakmile dojde k výjimce.  Můžete to provést metodou kombinátoru, například `WhenAllOrFirstException` v následujícím příkladu:

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
 Kromě schopnosti vytvářet vlastní kombinátory založené na úlohách, které mají datovou strukturu a <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> která představuje výsledky asynchronní operace a nezbytné synchronizace pro připojení s ním je velmi výkonný typ, na kterém chcete vytvořit vlastní datové struktury, které mají být použity v asynchronních scénářích.

### <a name="asynccache"></a>AsyncCache
 Jedním z důležitých aspektů úkolu je, že může být rozdán více spotřebitelům, z nichž všichni mohou čekat, zaregistrovat pokračování s ním, získat jeho výsledek nebo výjimky (v případě <xref:System.Threading.Tasks.Task%601>) a tak dále.  Díky <xref:System.Threading.Tasks.Task> tomu <xref:System.Threading.Tasks.Task%601> se dokonale hodí pro použití v asynchronní infrastruktuře ukládání do mezipaměti.  Zde je příklad malé, ale výkonné asynchronní mezipaměti <xref:System.Threading.Tasks.Task%601>postavené nad :

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

 [Třída AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) přijímá jako delegáta svému konstruktoru funkci, která přebírá `TKey` a vrátí <xref:System.Threading.Tasks.Task%601>.  Všechny dříve přístupné hodnoty z mezipaměti jsou uloženy `AsyncCache` ve vnitřním slovníku a zajišťuje, že je generována pouze jedna úloha na klíč, i v případě, že je ke mezipaměti přistupovat souběžně.

 Můžete například vytvořit mezipaměť pro stažené webové stránky:

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Tuto mezipaměť pak můžete použít v asynchronních metodách, kdykoli budete potřebovat obsah webové stránky. Třída `AsyncCache` zajišťuje, že stahujete co nejméně stránek a ukládá výsledky do mezipaměti.

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
 Úkoly můžete také použít k vytváření datových struktur pro koordinaci asynchronních aktivit.  Vezměme si jeden z klasických paralelních vzorů návrhu: výrobce / spotřebitel.  V tomto modelu výrobci generují údaje, které spotřebovávají spotřebitelé, a výrobci a spotřebitelé mohou probíhat souběžně. Například spotřebitel zpracovává položku 1, která byla dříve generována výrobcem, který nyní vyrábí položku 2.  Pro výrobce / spotřebitele vzor, vždy potřebujete nějakou strukturu dat pro ukládání práce vytvořené výrobci tak, aby spotřebitelé mohou být informováni o nových údajů a najít je, když je k dispozici.

 Zde je jednoduchá datová struktura postavená na úlohách, které umožňují použití asynchronních metod jako výrobců a spotřebitelů:

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

 S touto datovou strukturou na místě můžete napsat kód, například následující:

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

Obor <xref:System.Threading.Tasks.Dataflow> názvů obsahuje <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, který můžete použít podobným způsobem, ale bez nutnosti vytvářet vlastní typ kolekce:

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
> Obor <xref:System.Threading.Tasks.Dataflow> názvů je k dispozici v rozhraní .NET Framework 4.5 až **NuGet**. Chcete-li nainstalovat sestavení, které obsahuje obor <xref:System.Threading.Tasks.Dataflow> názvů, otevřete projekt v sadě Visual Studio, zvolte Spravovat **balíčky NuGet** z nabídky Project a vyhledejte balíček Microsoft.Tpl.Dataflow online.

## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
