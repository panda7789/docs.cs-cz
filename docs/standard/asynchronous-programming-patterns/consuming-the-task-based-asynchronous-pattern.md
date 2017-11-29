---
title: "Použití asynchronního vzoru založeného na úloze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90b2a36f0e6bf06b0fefe2191d5b17c9c07d1588
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Použití asynchronního vzoru založeného na úloze
Použijete-li pracovat s asynchronních operací založený na úlohách asynchronní vzor (TAP), můžete dosáhnout čekání bez blokování zpětných volání.  Pro úlohy, můžete toho dosáhnout pomocí metody, jako <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Na základě jazyka asynchronní podpora skryje tím, že asynchronních operací, která se v rámci normálního toku řízení očekávaná zpětná volání a generované kompilátorem kódu poskytuje tato podpora stejnou úroveň rozhraní API.  
  
## <a name="suspending-execution-with-await"></a>Pozastavení provádění s Await  
 Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete použít [await](~/docs/csharp/language-reference/keywords/await.md) – klíčové slovo v jazyce C# a [Await – operátor](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic pro asynchronně await <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty. Když se čeká na <xref:System.Threading.Tasks.Task>, `await` výraz je typu `void`. Když se čeká na <xref:System.Threading.Tasks.Task%601>, `await` výraz je typu `TResult`. `await` Výraz musí dojít k uvnitř těla asynchronní metody. Další informace o jazyka C# a Visual Basic podporují v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], najdete v části specifikace jazyka C# a Visual Basic.  
  
 V pozadí nainstaluje funkci await pomocí pokračování v úloze zpětné volání.  Tato zpětného volání obnoví asynchronní metody v místě pozastavení. Když je obnoveno asynchronní metody, pokud awaited operace byla úspěšně dokončena a byla <xref:System.Threading.Tasks.Task%601>, jeho `TResult` je vrácen.  Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , očekávaná skončila v <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, <xref:System.OperationCanceledException> je vyvolána výjimka.  Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , očekávaná skončila v <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu, je vyvolána výjimka, který způsobuje její poruch. A `Task` můžete selhání v důsledku několik výjimek, ale pouze jeden z těchto výjimek rozšířena. Ale <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.AggregateException> výjimka, která obsahuje všechny chyby.  
  
 Pokud kontext synchronizace (<xref:System.Threading.SynchronizationContext> objektu) souvisí s podproces, který byl v době pozastavení provádění asynchronní metody (například pokud <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> vlastnost není `null`), asynchronní metoda obnoví na který stejný kontext synchronizace pomocí podle kontextu <xref:System.Threading.SynchronizationContext.Post%2A> metoda. Jinak je závislé na plánovače úloh (<xref:System.Threading.Tasks.TaskScheduler> objektu), který byl aktuální v době pozastavení. Obvykle je to výchozí plánovače úloh (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), které cílí fondu vláken. Tato služba Plánovač úloh Určuje, zda by měl awaited asynchronní operace pokračovat, kde byla dokončena nebo jestli má být naplánováno obnovení. Scheduler výchozí obvykle umožní pokračování ke spuštění na vlákno, které awaited operaci dokončit.  
  
 Při volání asynchronní metody, se tělo funkce synchronně provede, dokud první await výrazu v případě může používat await instance, který ještě nebyl dokončen, v tomto okamžiku se volání vrátí volajícímu. Pokud lze asynchronní metodu nevrátí `void`, <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> se vrátí objekt představující probíhající výpočet. V jiných void asynchronní metody, pokud je příkaz return zaznamenána nebo je dosaženo konce metoda textu, dokončení úlohy v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> konečného stavu. Pokud k neošetřené výjimce způsobí, že ovládací prvek chcete nechat těla asynchronní metody, úloha končí v <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu. Pokud je této výjimky <xref:System.OperationCanceledException>, úloha místo končí v <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu. Tímto způsobem výsledek nebo výjimky se nakonec publikuje.  
  
 Existuje několik důležitých variant toto chování.  Z důvodů výkonu Pokud úloha již byla dokončena v čase je očekáváno úlohu, není poskytuje ovládací prvek a funkce bude pokračovat v provádění.  Kromě toho vrácením původní kontextu není vždy požadované chování a může být změněn; To je podrobně popsaná v další v další části.  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Pozastavení a obnovení nakonfigurování Yield a ConfigureAwait  
 Existuje několik metod poskytuje větší kontrolu nad spuštění asynchronní metody. Například můžete použít <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metoda zavést bod yield do asynchronní metody:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 Jde o ekvivalent asynchronně publikování nebo plánování zpět do aktuálního kontextu.  
  
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
  
 Můžete také <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad pozastavení a obnovení v asynchronní metodu.  Jak je uvedeno nahoře, ve výchozím nastavení, je aktuální kontext zachycen v době, kdy je pozastaveno asynchronní metodu a že zaznamenané kontextu je použito k volání asynchronní metody pokračování po obnovení.  V mnoha případech je to přesné chování, které chcete.  V ostatních případech nemusí se zajímáte o pokračování kontextu a lepšího výkonu můžete dosáhnout vyhnout těchto příspěvcích zpět do původní kontextu.  Chcete-li povolit, použijte <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metoda informovat await operaci není k zaznamenání a obnovení v kontextu, ale pro pokračování v provádění bez ohledu na dokončení asynchronní operaci, která se očekávaná:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>Zrušení asynchronní operace  
 Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], klepněte na metody, které podporují zrušení zadejte alespoň jeden přetížení, která přijímá token zrušení (<xref:System.Threading.CancellationToken> objekt).  
  
 Token zrušení je vytvořena prostřednictvím zdroj tokenu zrušení (<xref:System.Threading.CancellationTokenSource> objekt).  Zdrojovém <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost vrací token zrušení, který bude signál při zdroj <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda je volána.  Například pokud chcete stáhnout jedné webové stránky a chcete být schopni zrušte operaci, vytvoříte <xref:System.Threading.CancellationTokenSource> objektu, předat klepněte na metoda jeho token a pak zavolají zdroj <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda až budete připraveni na tlačítko Storno:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 Pokud chcete zrušit více asynchronní volání, můžete předat stejný token do všech volání:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 Nebo můžete předat stejný token do podmnožinu selektivní operací:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 Zrušení žádosti může být zahájen z libovolného vlákna.  
  
 Můžete předat <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> hodnotu libovolné metody, která přijímá token zrušení pro znamenat, že bude nikdy vyžádána zrušení.  To způsobí, že <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> vlastnost vrátit `false`, a zavolat metodu můžete optimalizovat odpovídajícím způsobem.  Pro účely testování můžete předat také v předem zrušené zrušení token, který je vytvořena instance pomocí konstruktor, který přijímá logickou hodnotu označující, zda je token by se měl spustit ve stavu již zrušena nebo možné zrušit není.  
  
 Tento přístup k zrušení má několik výhod:  
  
-   Stejný token zrušení můžete předat libovolný počet synchronní a asynchronní operace.  
  
-   Stejné žádost o zrušení může být proliferated na libovolný počet naslouchací procesy.  
  
-   Vývojář asynchronní rozhraní API je v úplnou kontrolu, zda mohou být vyžádány zrušení a kdy může trvat vliv.  
  
-   Kód, který využívá rozhraní API může určit selektivně asynchronní volání, které požadavky zrušení se rozšíří do.  
  
## <a name="monitoring-progress"></a>Sledování průběhu  
 Některé asynchronní metody vystavit probíhá přes rozhraní průběh předané do asynchronní metody.  Zvažte například, že funkci, která asynchronně stáhne řetězec textu a cestou se vyvolá průběh aktualizace, které zahrnují procento ke stažení, které doposud dokončeno.  Tato metoda by mohly spotřebovat v aplikaci Windows Presentation Foundation (WPF) následujícím způsobem:  
  
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
## <a name="using-the-built-in-task-based-combinators"></a>Pomocí předdefinovaných Combinators založený na úlohách  
 <xref:System.Threading.Tasks> Obor názvů obsahuje několik metod pro vytváření a práci s úlohami.  
  
### <a name="taskrun"></a>Task.Run  
 <xref:System.Threading.Tasks.Task> Třída obsahuje několik <xref:System.Threading.Tasks.Task.Run%2A> metody, které vám umožní snadno snižování zátěže work jako <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> fond vláken, např.:  
  
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
  
 Některé z těchto <xref:System.Threading.Tasks.Task.Run%2A> metody, jako <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> přetížení, existovat jako sdružená vlastnost <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda.  Jiné přetížení, jako například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, povolit použití await v rámci sníženou zátěží práce, například:  
  
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
  
 Takové přetížení jsou logicky ekvivalentní použití <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda ve spojení s <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metoda rozšíření v knihovně Task Parallel Library.  
  
### <a name="taskfromresult"></a>Task.FromResult  
 Použití <xref:System.Threading.Tasks.Task.FromResult%2A> musí být vrácená metodou vracející úloh zrušeno do metoda ve scénářích, kde data mohou již být k dispozici, jenom <xref:System.Threading.Tasks.Task%601>:  
  
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
 Použití <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda asynchronně čekání na více asynchronních operací, které jsou reprezentovány jako úlohy.  Metoda má několik přetížení, která podporují sadu neobecnou úloh nebo neuniformní sadu obecné úlohy (například asynchronně čekání pro více operací void vrácení, nebo asynchronně čekání na více metod vrací hodnotu kde Každá hodnota může mít jiný typ) a k podpoře uniform sadu obecné úloh (například asynchronně čekání na více `TResult`-vrácení metody).  
  
 Řekněme, že chcete poslat e-mailové zprávy několik zákazníků. Můžete se překrývají, odesílání zpráv, takže nejsou čeká jednu zprávu dokončit před odesláním Další. Můžete taky zjistit když byly dokončeny operace odesílání a jestli nedošlo k chybám:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 Tento kód není explicitně zpracování výjimek, které může dojít, ale umožní šířit z výjimky `await` na výsledný úlohy ze <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Pro zpracování výjimky, můžete použít například následující kód:  
  
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
  
 V takovém případě pokud všechny asynchronní operace selže, všechny výjimky se mají konsolidovat v <xref:System.AggregateException> výjimka, která je uložena v <xref:System.Threading.Tasks.Task> , je vrácena z <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda.  Ale pouze jeden z těchto výjimek rozšířit pomocí `await` – klíčové slovo.  Pokud chcete prozkoumejte všechny výjimky, je možné přepsat předchozí kód následujícím způsobem:  
  
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
  
 Zvažte příklad asynchronně stahování více souborů z webu.  V takovém případě všechny asynchronní operace mají typy homogenní výsledků a je snadno dostupné výsledky:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Můžete použít stejné techniky zpracování výjimek, kterou jsme probírali v předchozím scénáři vrácení void:  
  
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
 Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda asynchronně čekání pouze jedním z několika asynchronních operací vyjádřené úlohy k dokončení.  Tato metoda slouží čtyři primární použití případech:  
  
-   Redundance: Provádění operace několikrát a vyberte ten, který dokončí první (například kontaktování více akcií webové služby, které vytvoří jeden výsledek a vyberte ten, který dokončí nejrychlejší).  
  
-   Prokládání: Spouštění více operací čekajících na jejich dokončení, ale jejich zpracování po dokončení.  
  
-   Omezení šířky pásma: Povolení zahájíte ostatní dokončení dalších operací.  Toto je rozšíření interleaving scénáře.  
  
-   Časná bailout: například operace reprezentována t1 úloh mohou být seskupeny do <xref:System.Threading.Tasks.Task.WhenAny%2A> úlohy s jinou t2 úloh a může čekat <xref:System.Threading.Tasks.Task.WhenAny%2A> úloh. Úloha t2 by mohl představovat vypršení časového limitu nebo zrušení nebo jiných signál, který způsobuje, že <xref:System.Threading.Tasks.Task.WhenAny%2A> na dokončení před dokončením t1 úlohy.  
  
#### <a name="redundancy"></a>Redundance  
 Představte si případ, kam chcete učinit rozhodnutí o tom, jestli koupit populace.  Existuje několik webových služeb uložených doporučení, kterým důvěřujete, avšak v závislosti na denní zatížení, můžou skončit se pomalé v různou dobu jednotlivých služeb.  Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda pro příjem oznámení po dokončení všechny operace:  
  
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
  
 Na rozdíl od <xref:System.Threading.Tasks.Task.WhenAll%2A>, která vrací všechny úkoly, které úspěšně dokončit, rozbalenou výsledky <xref:System.Threading.Tasks.Task.WhenAny%2A> vrátí úlohu, která byla dokončena. Pokud se úloha nezdaří, je důležité vědět, že se nezdařilo, a pokud úloha úspěšná, je důležité vědět, jaké úlohu vrácená hodnota je přidružen.  Proto musíte získat přístup výsledek vrácený úlohy, nebo další await, jak ukazuje tento příklad.  
  
 Stejně jako u <xref:System.Threading.Tasks.Task.WhenAll%2A>, budete muset být schopni nastavit výjimky.  Vzhledem k tomu, že se zobrazí zpět dokončené úlohy, můžete await vrácený úlohy chyby rozšíří, a `try/catch` je správně; například:  
  
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
  
 Kromě toho i v případě, že první úloha skončí úspěšně, může selhat úlohy.  V tuto chvíli máte několik možností pro práci s výjimkami: můžete počkat, dokud všechny spuštěného úkoly dokončí, v takovém případě můžete použít <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda, nebo můžete rozhodnout, že všechny výjimky jsou důležité a musí být zaprotokolovány.  V takovém případě můžete použít pokračování pro příjem oznámení po dokončení úlohy asynchronně:  
  
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
  
```  
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
  
 Nakonec můžete zrušit všechny zbývající operace:  
  
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
 Představte si případ, kdy jste z webu stažení bitové kopie a zpracování každé bitové kopie (například přidání bitovou kopii do ovládacího prvku uživatelského rozhraní).  Je nutné provést zpracování postupně ve vlákně UI, ale chcete stáhnout bitové kopie jako současně. Navíc nechcete pojmout až Přidání bitové kopie do uživatelského rozhraní, dokud se všechny stáhnou – chcete přidat, je po dokončení:  
  
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
  
 Můžete taky použít prokládání pro scénář, který zahrnuje výpočetně intenzivní zpracování na <xref:System.Threading.ThreadPool> stažené bitových kopií; například:  
  
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
 Podívejte se na příklad interleaving, s tím rozdílem, že uživatel stahuje mnoho bitové kopie, stahování jsou potřeba k omezeny; například, že chcete pouze konkrétní počet souborů ke stažení provést současně. Jak toho docílit, můžete začít podmnožinu asynchronní operace.  Dokončení operace, můžete spustit další operace jejich proběhla:  
  
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
  
#### <a name="early-bailout"></a>Časná Bailout  
 Zvažte, že čekáte asynchronně na dokončení při současně reakci na žádost uživatele zrušení operace (například uživatel kliknutí na tlačítko Storno). Následující kód ukazuje tento scénář:  
  
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
  
 Tato implementace znovu povolí uživatelské rozhraní, při nichž rozhodnete, ale není zrušte základní asynchronní operace.  Další alternativou by zrušit čekající operace, pokud se rozhodnete nichž, ale není znovu vytvořit uživatelské rozhraní až ve skutečnosti dokončení potenciálně kvůli ukončuje již v rané fázi kvůli žádost o zrušení operace:  
  
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
  
 Další příklad časná bailout zahrnuje použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda ve spojení s <xref:System.Threading.Tasks.Task.Delay%2A> metoda, jak je popsáno v následující části.  
  
### <a name="taskdelay"></a>Task.Delay  
 Můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda zavádět pozastaví do asynchronní metody spouštění.  To je užitečné pro různé druhy funkce, včetně vytváření dotazování smyčky a zpozdit zpracování vstupu uživatele předem určenou dobu.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda také může být užitečná v kombinaci s <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pro implementace vypršení časových limitů na čeká.  
  
 Pokud úloha, která je součástí větší asynchronní operace (například webové služby ASP.NET) trvá příliš dlouho dokončení, může celkové operace sníží, obzvláště pokud se nepodaří někdy dokončit.  Z tohoto důvodu je důležité, abyste mohli vypršení časového limitu při čekání na asynchronní operace.  Synchronní <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody přijímají hodnoty časového limitu, ale odpovídající <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše uvedených <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>metody nepodporují.  Místo toho můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> v kombinaci implementovat vypršení časového limitu.  
  
 Například v aplikaci uživatelského rozhraní Řekněme, že chcete stáhnout bitovou kopii a zakázat uživatelské rozhraní během stahuje bitovou kopii. Ale pokud stahování trvá příliš dlouho, chcete znovu zapnout uživatelského rozhraní a zrušení stahování:  
  
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
  
 Totéž platí i pro více souborů ke stažení, protože <xref:System.Threading.Tasks.Task.WhenAll%2A> vrátí úlohu:  
  
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
  
## <a name="building-task-based-combinators"></a>Vytváření Combinators založený na úlohách  
 Protože úloha je schopen úplně představují asynchronní operaci a zadejte možnosti synchronní a asynchronní pro připojení v operaci, načítání jeho výsledky a tak dále, můžete vytvořit užitečné knihovny combinators, které tvoří úloh sestavení větší vzory.  Jak je popsáno v předchozí části, rozhraní .NET Framework zahrnuje několik předdefinovaných combinators, ale můžete také vytvořit vlastní. Následující části obsahují několik příkladů, potenciální kombinátorem metody a typy.  
  
### <a name="retryonfault"></a>RetryOnFault  
 V mnoha situacích můžete opakovat operace, pokud se předchozí pokus selže.  Pro synchronní kód, může sestavování Pomocná metoda, jako `RetryOnFault` v následujícím příkladu se:  
  
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
  
 Můžete vytvořit téměř identický pomocnou metodu pro asynchronní operace, které jsou implementovány pomocí klepněte na a proto vrátí úlohy:  
  
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
  
 Pak můžete toto kombinátorem ke kódování opakování do aplikace logiky; například:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 Můžete rozšířit `RetryOnFault` další funkce. Například funkce může přijímat jiné `Func<Task>` , který bude vyvolán mezi opakovanými pokusy k určení, kdy k akci znovu; například:  
  
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
  
 Můžete potom použít funkci takto čekat před opakováním operace druhý:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 V některých případech můžete využít výhod redundance, aby zlepšit latenci a pravděpodobnost úspěchu operaci.  Vezměte v úvahu více webových služeb, které poskytují akcií, ale v různých časech dne, může každá služba poskytovat různé úrovně kvality a časy odezvy.  K řešení těchto kolísání, můžete vydat požadavky pro všechny webové služby a také získat odpověď z některého, zrušit zbývající žádosti.  Můžete implementovat pomocné funkce, aby bylo snazší implementovat tento běžný vzor spouštění více operací, čekání na všechny a pak zrušení zbytek. `NeedOnlyOne` Tento scénář ukazuje funkce v následujícím příkladu:  
  
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
  
 Potom můžete tuto funkci použít následujícím způsobem:  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a>Prokládaná operace  
 Došlo k potížím potenciální výkon pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda pro podporu interleaving scénář, když pracujete s velmi velkých sad úloh.  Každé volání <xref:System.Threading.Tasks.Task.WhenAny%2A> výsledkem pokračování registrované s každý úkol. Pro N počet úloh výsledkem O(N2) pokračování vytvořit během životního cyklu interleaving operace.  Pokud pracujete s velké sadu úloh, můžete použít kombinátorem (`Interleaved` v následujícím příkladu) Chcete-li vyřešit problémy s výkonem:  
  
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
  
 Potom můžete kombinátorem zpracování výsledků úloh po dokončení; například:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 V některých scénářích bodového nebo shromáždění můžete počkat, všechny úlohy v sadě, pokud jeden z nich chyb, v takovém případě chcete zastavit, čekání, jakmile dojde k výjimka.  Můžete provést, pomocí metody kombinátorem například `WhenAllOrFirstException` v následujícím příkladu:  
  
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
  
## <a name="building-task-based-data-structures"></a>Vytváření založený na úlohách datové struktury  
 Kromě možnost vytváření vlastních combinators založený na úlohách, že datová struktura v <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> výsledky asynchronní operace, která představuje a potřeby synchronizace k připojení k němu umožňuje velmi efektivní Zadejte, na které se mají vytvářet vlastní datové struktury pro použití v asynchronní scénáře.  
  
### <a name="asynccache"></a>AsyncCache  
 Jednou z důležitým aspektem úlohy je, že ho může možné předat službě více příjemcům, které může await ho zaregistrovat pokračování s ním, získat jeho výsledek nebo výjimky (u <xref:System.Threading.Tasks.Task%601>), a tak dále.  Díky tomu <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> perfektně vhodná pro použití v infrastruktuře asynchronní ukládání do mezipaměti.  Tady je příklad malá, ale výkonné asynchronní mezipaměť postavený na <xref:System.Threading.Tasks.Task%601>:  
  
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
  
 [AsyncCache\<TKey, TValue >](http://go.microsoft.com/fwlink/p/?LinkId=251941) třída přijímá jako delegáta jeho konstruktoru funkce, která přebírá `TKey` a vrátí <xref:System.Threading.Tasks.Task%601>.  Veškeré dříve používaná hodnoty z mezipaměti jsou uloženy ve slovníku interní a `AsyncCache` zajistí, aby pouze jeden úkol se vygeneruje pro klíč, i v případě, že mezipaměť přistupuje souběžně.  
  
 Můžete například vytvořit mezipaměť pro stažené webové stránky:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Potom můžete tuto mezipaměť v asynchronních metod kdykoli budete potřebovat obsah na webové stránce. `AsyncCache` Třída zajistí, že při stahování co nejméně stránky jako možné a mezipaměti výsledky.  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection  
 Úlohy můžete použít také k vytvoření datové struktury pro spolupráci asynchronní aktivity.  Jedním ze vzorů classic paralelní návrhu zvažte: producent nebo příjemce.  V tomto vzoru producenti generování dat, která se využívá spotřebiteli a producenti a spotřebitelé může běží paralelně. Například příjemce zpracovává položky 1, který byl dříve vygenerovat podle výrobce, který je nyní generovala položku 2.  Pro vzoru producent nebo příjemce je vždy nutné některé datovou strukturu pro ukládání pracovních vytvořené producenti tak, aby uživatelé být upozorněni na nová data a najít, když je k dispozici.  
  
 Zde je jednoduchá datová struktura postavená na úlohy, která umožňuje asynchronní metody, které má být použit jako producenti a spotřebitelé:  
  
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
  
 Pomocí této datové struktury v místě můžete napsat kód například následující:  
  
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
  
 <xref:System.Threading.Tasks.Dataflow> Obor názvů zahrnuje <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typu, který můžete použít podobným způsobem, ale bez nutnosti vytvořit vlastní kolekce typ:  
  
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
>  <xref:System.Threading.Tasks.Dataflow> Je k dispozici v oboru názvů [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] prostřednictvím **NuGet**. Instalace sestavení, který obsahuje <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online balíček Microsoft.Tpl.Dataflow.  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Implementace asynchronního vzoru založeného na úloze](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
