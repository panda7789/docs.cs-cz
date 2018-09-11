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
ms.openlocfilehash: 5b538cb53e1cbc1fdbd8e34506710a1967e50f9d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44354058"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Použití asynchronního vzoru založeného na úloze
Použijete-li založený na úlohách asynchronního vzoru (TAP) pro práci s asynchronní operace, můžete použít zpětná volání k dosažení čekání bez blokování.  Pro úlohy, toho je dosaženo pomocí metod, jako <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Založený na jazyce asynchronní podporu skryje zpětná volání tím, že asynchronní operace do ní použít operátor await v rámci normálního toku řízení a kód generovaný kompilátorem podporuje tento stejnou úroveň rozhraní API.  
  
## <a name="suspending-execution-with-await"></a>Pozastavení provádění s Await  
 Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete použít [await](~/docs/csharp/language-reference/keywords/await.md) – klíčové slovo v jazyce C# a [operátor Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic asynchronně await pro čekání <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty. Když se čeká na <xref:System.Threading.Tasks.Task>, `await` výraz je typu `void`. Když se čeká na <xref:System.Threading.Tasks.Task%601>, `await` výraz je typu `TResult`. `await` Výraz se musí vyskytovat uvnitř těla asynchronní metodu. Další informace o jazyce C# a Visual Basic podporují v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], naleznete v tématu Specifikace jazyka C# a Visual Basic.  
  
 Pod pokličkou nainstaluje funkci await pomocí pokračování na úkolu zpětné volání.  Toto zpětné volání pokračuje v okamžiku pozastavení asynchronní metody. Když se obnoví asynchronní metody, pokud očekávané operace byla úspěšně dokončena a byla <xref:System.Threading.Tasks.Task%601>, jeho `TResult` je vrácena.  Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , která byla očekávána skončila v <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, <xref:System.OperationCanceledException> je vyvolána výjimka.  Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , která byla očekávána skončila v <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu, je vyvolána výjimka, která způsobila selhání. A `Task` můžete selhání v důsledku více výjimek, ale pouze jeden z těchto výjimek je rozšířena. Ale <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.AggregateException> výjimku, která obsahuje všechny chyby.  
  
 Pokud kontext synchronizace (<xref:System.Threading.SynchronizationContext> objektu) souvisí s vláknem, které v okamžiku pozastavení provádění asynchronní metody (např. Pokud <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> jedná o vlastnost neumožňující `null`), asynchronní metody pokračuje na, který stejný kontext synchronizace s využitím daného kontextu <xref:System.Threading.SynchronizationContext.Post%2A> metody. V opačném případě spoléhá na Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler> objektu), který byl aktuální v okamžiku pozastavení. Obvykle je to výchozí Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), který se zaměřuje na fond vláken. Tento Plánovač úloh Určuje, zda očekávaná asynchronní operace měla pokračovat, kde dokončena nebo zda má být naplánováno opětovné. Výchozí plánovač obvykle umožňuje pokračování spuštěno ve vlákně, očekávané operace dokončena.  
  
 Při volání asynchronní metody, je tělo funkce synchronně spustí, až do první await výraz v očekávatelný instanci, která zatím není dokončený, v tomto okamžiku volání vrátí řízení volajícímu. Pokud asynchronní metoda nevrací `void`, <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> je vrácen objekt představující probíhající výpočtu. V asynchronní metodě není void, pokud se zjistila návratový příkaz nebo je dosaženo konce tělo metody, dokončení úlohy v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> koncový stav. Pokud k neošetřené výjimce způsobí, že ovládací prvek opustit tělo asynchronní metody, skončí tento úkol ve <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu. Pokud tuto výjimku <xref:System.OperationCanceledException>, místo toho skončí tento úkol ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu. Tímto způsobem výsledek nebo výjimku nakonec publikování.  
  
 Existuje několik důležitých variant tohoto chování.  Z důvodů výkonu Pokud úloha již byla dokončena v čase je na úkol čekáno není poskytuje ovládací prvek a pokračuje v provádění funkce.  Kromě toho vrátí do původního kontextu není vždy požadované chování a je možné změnit; To je popsáno v následující části podrobněji.  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Konfigurace pozastavení a obnovení pomocí Yield a ConfigureAwait  
 Několik metody poskytují větší kontrolu nad spouštěním asynchronní metody. Například můžete použít <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metoda zavést bod yield do asynchronní metody:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 Jde o ekvivalent asynchronně účtování nebo plánování zpět do aktuálního kontextu.  
  
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
  
 Můžete také použít <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad pozastavení a pokračování v asynchronní metodě.  Jak už bylo zmíněno dříve, ve výchozím nastavení, je aktuální kontext zaznamenané v době, kterou metodu je pozastavený, a že zachyceném kontextu se používá k volání asynchronní metody pokračování po obnovení.  V mnoha případech jde přesnou chování, které chcete.  V jiných případech nemusí starat o kontext pokračování a můžou dosahovat lepšího výkonu zabráněním takových příspěvků zpět do původního kontextu.  Chcete-li povolit, použijte <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metoda informovat operace await zaznamenat a obnovit v kontextu, ale chcete-li pokračovat v provádění bez ohledu na to, který se očekávaná asynchronní operace dokončena:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>Zrušení asynchronní operace  
 Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], metod TAP, které podporují zrušení poskytnout alespoň jedním přetížením, která přijímá token zrušení (<xref:System.Threading.CancellationToken> objekt).  
  
 Token zrušení je vytvořená prostřednictvím zdroj token zrušení (<xref:System.Threading.CancellationTokenSource> objekt).  Zdroje na <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost vrátí token zrušení, který bude signál při zdroje <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda je volána.  Pokud chcete stáhnout jediné webové stránky a chcete být schopni zrušit operaci, můžete vytvořit <xref:System.Threading.CancellationTokenSource> objektu, předejte svůj token metody TAP a následně zavolat zdroj <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda až budete připraveni na zrušení operace:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 Pokud chcete zrušit více asynchronní vyvolání, můžete předat stejný token všechna volání:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 Nebo můžete předat stejný token selektivní podmnožinu operace:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 Žádosti o zrušení, může být vyvoláno z libovolného vlákna.  
  
 Můžete předat <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> hodnotu na jakoukoli metodu, která přijímá token zrušení pro označení, že se nikdy být požadováno zrušení.  To způsobí, že <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> vlastnost vrátit `false`, a volané metody můžete optimalizovat odpovídajícím způsobem.  Pro účely testování můžete také předat token zrušení předem zrušené, jehož instance je vytvořena pomocí konstruktoru, který přijímá hodnotu typu Boolean označující, zda token, který by měl spustit ve stavu už zrušená nebo není zrušitelný.  
  
 Tento přístup k zrušení má několik výhod:  
  
-   Můžete předat stejný token zrušení do libovolného počtu synchronní a asynchronní operace.  
  
-   Stejný požadavek na zrušení může proliferated do libovolného počtu naslouchacích procesů.  
  
-   Vývojář asynchronní rozhraní API je plně pod kontrolou, jestli může být požadováno zrušení a kdy ji může platit.  
  
-   Kód, který využívá rozhraní API může určit selektivně asynchronní vyvolání, které požadavky zrušení se rozšíří do.  
  
## <a name="monitoring-progress"></a>Sledování průběhu  
 Některé asynchronní metody vystavit průběh prostřednictvím rozhraní postupu předané do asynchronní metody.  Představte si třeba, že funkce, která asynchronně stáhne řetězec textu a na cestě vyvolává průběh aktualizace, které zahrnují procentuální stažení, které doposud dokončeno.  Tato metoda může spotřebovat v aplikaci Windows Presentation Foundation (WPF) následujícím způsobem:  
  
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
## <a name="using-the-built-in-task-based-combinators"></a>Pomocí předdefinovaných Combinators založené na úlohách  
 <xref:System.Threading.Tasks> Obor názvů obsahuje několik metod pro vytváření a práci s úkoly.  
  
### <a name="taskrun"></a>Task.Run  
 <xref:System.Threading.Tasks.Task> Třída obsahuje několik <xref:System.Threading.Tasks.Task.Run%2A> metody, které vám umožní snadno snižování zátěže fungovat stejně jako <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> s fondem vláken, například:  
  
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
  
 Některé z těchto <xref:System.Threading.Tasks.Task.Run%2A> metody, například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> přetížení, existují jako zkratka pro <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda.  Druhé přetížení, jako například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, povolit použití operátoru await sníženou zátěží díla, například:  
  
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
  
 Takovými přetíženími jsou logicky ekvivalentní k použití <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda ve spojení s <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metoda v knihovně Task Parallel Library.  
  
### <a name="taskfromresult"></a>Task.FromResult  
 Použití <xref:System.Threading.Tasks.Task.FromResult%2A> metoda ve scénářích, kde data může už být k dispozici a jenom je potřeba vrátil z metody vracející úlohy do zrušeno <xref:System.Threading.Tasks.Task%601>:  
  
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
 Použití <xref:System.Threading.Tasks.Task.WhenAll%2A> metody asynchronně čekat na více asynchronních operací, které jsou reprezentovány ve formě úlohy.  Tato metoda má několik přetížení, které podporují sadu neobecnou úloh nebo nerovnoměrné sady úloh obecný (například asynchronně čeká na více operací vracející hodnotu void, nebo asynchronně čeká na několik metod vrací hodnotu kde Každá hodnota může mít jiný typ) a podporovat jednotné sadu obecných úloh (jako je například asynchronně čeká na více `TResult`-metody vracející).  
  
 Řekněme, že chcete odeslat e-mailové zprávy pro několik zákazníků. Můžete se může překrývat odesílání zprávy, proto nejsou čekání dokončit před odesláním dalších zpráv. Můžete také získat informace při dokončení operace odesílání a určuje, zda nedošlo k chybám:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 Tento kód nezpracuje explicitně výjimky, které může dojít, ale umožní výjimky nešířily z celkového počtu `await` na výsledný úkol z <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Zpracování výjimek, můžete použít například následující kód:  
  
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
  
 V takovém případě pokud libovolné asynchronní operace selže, všechny výjimky začlení do <xref:System.AggregateException> výjimku, která je uložena v <xref:System.Threading.Tasks.Task> , který je vrácen z <xref:System.Threading.Tasks.Task.WhenAll%2A> – metoda.  Ale pouze jeden z těchto výjimek distribuovány `await` – klíčové slovo.  Pokud chcete prozkoumat všechny výjimky, můžete předchozí kód přepsat následujícím způsobem:  
  
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
  
 Zvažte následující příklad asynchronní stahování více souborů z webu.  V tomto případě mají typy homogenní výsledků asynchronních operací a snadno přistupovat k výsledkům:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Můžete použít stejné techniky zpracování výjimek, které jsme probrali v předchozím scénáři vracející typ void:  
  
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
 Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metody asynchronně čekat pouze jedna z více asynchronních operací reprezentovaná jako úkoly k dokončení.  Tato metoda má čtyři hlavní případy použití:  
  
-   Redundance: Provádění operace více než jednou a vyberte ten, který dokončí první (například kontaktování více akcií webové služby, které vytvoří jeden výsledek a vybere, která se dokončí nejrychlejší z nich).  
  
-   Prokládání: Spuštění více operací a čeká na všechny z nich k dokončení, ale jejich zpracování po dokončení.  
  
-   Omezení šířky pásma: Povolení zahájíte ostatní dokončení dalších operací.  Toto je rozšíření interleaving scénáře.  
  
-   Časná bailout: například operace reprezentována t1 úlohy mohou být seskupeny do <xref:System.Threading.Tasks.Task.WhenAny%2A> úloha s jinou t2 úloh a může čekat <xref:System.Threading.Tasks.Task.WhenAny%2A> úloh. Úloha t2 by mohly představovat vypršení časového limitu nebo zrušení nebo některé jiné signál, který způsobí, že <xref:System.Threading.Tasks.Task.WhenAny%2A> úlohy dokončení před dokončením t1.  
  
#### <a name="redundancy"></a>Redundance  
 Představte si případ, ve které chcete rozhodnutí o tom, jestli si chcete koupit stejných akcií.  Existuje několik doporučení základní webové služby, kterým důvěřujete, ale v závislosti na denní zatížení, každá služba skončit se pomalé v různých časech.  Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu pro příjem oznámení po dokončení všechny operace:  
  
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
  
 Na rozdíl od <xref:System.Threading.Tasks.Task.WhenAll%2A>, která vrací rozbalení výsledcích všechny úlohy, které se nedokončil úspěšně, <xref:System.Threading.Tasks.Task.WhenAny%2A> vrátí úkol, který byl dokončen. Pokud se úkol nezdaří, je důležité vědět, že se nepovedlo, a pokud úkol proběhne úspěšně, je důležité vědět, který úkol vrácená hodnota je přidružena.  Proto potřebujete přístup k výsledku vrácené úlohy nebo další await, jak ukazuje tento příklad.  
  
 Stejně jako u <xref:System.Threading.Tasks.Task.WhenAll%2A>, budete muset být schopni nastavit výjimky.  Vzhledem k tomu, že se zobrazí dokončené úlohy, můžete očekávat Vrácená úloha šíří, chyby se a `try/catch` je odpovídajícím způsobem; například:  
  
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
  
 Kromě toho i v případě, že první úloha úspěšně dokončí, následné úlohy může selhat.  V tomto okamžiku máte několik možností pro nakládání s výjimkami: můžete počkat, dokud nebyly dokončeny všechny spuštěné úlohy, v takovém případě můžete použít <xref:System.Threading.Tasks.Task.WhenAll%2A> metodu, nebo můžete rozhodnout, že všechny výjimky jsou důležité a musíte být přihlášeni.  V takovém případě můžete použít pokračování pro příjem oznámení po dokončení asynchronní úlohy:  
  
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
  
 Nakonec můžete chtít zrušení zbývajících operací:  
  
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
 Představte si případ, ve kterém jste stahování imagí z webu a zpracování každé bitové kopie (například přidání image do ovládacího prvku uživatelského rozhraní).  Je nutné provést zpracování postupně ve vlákně uživatelského rozhraní, ale chcete stáhnout Image jako současně. Navíc není nutné zdržet přidávání obrázků na uživatelské rozhraní, dokud se všechny stáhnou, které chcete přidat, je po dokončení:  
  
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
  
 Můžete také použít prokládání scénář, který zahrnuje výpočetně náročné na zpracování na <xref:System.Threading.ThreadPool> stažený imagí, třeba:  
  
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
 Podívejte se na příklad interleaving s tím rozdílem, že uživatel stahuje tolik obrázky, soubory ke stažení jsou potřeba k omezení; například chcete jenom určitý počet stažení probíhají souběžně. Za tím účelem můžete spustit podmnožinu asynchronních operací.  Dokončení operace, můžete spustit další operace k provedení jejich:  
  
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
 Vezměte v úvahu, že čekáte asynchronní operaci dokončit během současně reakce na žádosti o zrušení uživatele (například uživatel klikl na tlačítko Storno). Následující kód ukazuje tento scénář:  
  
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
  
 Tato implementace znovu povolí uživatelského rozhraní, co nejdříve, rozhodněte, do nichž navýšení kapacity, ale nezruší základní asynchronních operací.  Jinou alternativou by také bylo zrušení čekající operace při rozhodování, na nichž navýšení kapacity, ale ne znovu vytvořit uživatelské rozhraní až dokončíte, potenciálně z důvodu ukončení již v rané fázi kvůli žádost o zrušení operace:  
  
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
  
 Další příklad předčasné bailout zahrnuje použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda ve spojení s <xref:System.Threading.Tasks.Task.Delay%2A> způsob, jak je popsáno v další části.  
  
### <a name="taskdelay"></a>Task.Delay  
 Můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda zavést pozastaví do spuštění asynchronní metody.  To je užitečné pro různé druhy funkce, včetně vytváření smyčky cyklického dotazování a zpracování vstupu uživatele na předem určenou dobu zpoždění.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda může být také užitečné v kombinaci s <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pro implementace vypršení časových limitů pro čeká.  
  
 Pokud úloha, která je součástí větší asynchronní operace (například webovou službu ASP.NET) trvá moc dlouho, může celkovou operaci dochází, zejména v případě, že ji nebude možné nikdy dokončení.  Z tohoto důvodu je důležité mít možnost vypršení časového limitu při čekání na asynchronní operaci.  Synchronní <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody přijímají hodnot časového limitu, ale odpovídající <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše uvedených <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>metody tomu tak není.  Místo toho můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> společně k implementaci vypršení časového limitu.  
  
 Například v uživatelském rozhraní aplikace, Řekněme, že chcete stáhnout bitovou kopii a zakázat uživatelské rozhraní během stahování image. Nicméně pokud stahování trvá příliš dlouho, chcete znovu povolit uživatelské rozhraní a zrušit stahování:  
  
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
  
## <a name="building-task-based-combinators"></a>Vytváření Combinators založené na úlohách  
 Protože úloha je zcela představuje asynchronní operaci a zadejte synchronní a asynchronní funkce pro propojení s operací, načítání jeho výsledky a tak dále, můžete vytvářet užitečné knihovny combinators, které tvoří úkoly Vytvářejte větší vzory.  Jak je popsáno v předchozí části, rozhraní .NET Framework obsahuje několik předdefinovaných combinators, ale můžete také vytvořit vlastní. Následující části obsahují několik příkladů potenciální Startup v rámci combinatoru metody a typy.  
  
### <a name="retryonfault"></a>RetryOnFault  
 V mnoha případech můžete chtít opakovat operace, pokud se předchozí pokus nezdaří.  Pro synchronní kód může vytvářet Pomocná metoda, jako `RetryOnFault` v následujícím příkladu, jak toho dosáhnout:  
  
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
  
 Můžete vytvořit metodu téměř identické pomocné rutiny pro asynchronní operace, které jsou implementovány klepnutím a proto vrací úlohy:  
  
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
  
 Potom můžete tento Startup v rámci combinatoru má kódovat do vaší aplikace logiky; opakovaných pokusů Příklad:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 Můžete rozšířit `RetryOnFault` dále fungovat. Například funkce by mohl přijmout jiný `Func<Task>` , který bude vyvolán mezi opakovanými pokusy o určení toho, kdy to zkuste znovu; například:  
  
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
  
 Můžete pak použít funkci následujícím způsobem čekat před opakováním operace sekundy:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 V některých případech můžete využít redundance zvýšit pravděpodobnost úspěchu a latence operace.  Vezměte v úvahu několik webových služeb, které poskytují akcií, ale v různých časech dne, každá služba může poskytovat různé úrovně kvality a doby odezvy.  Výkyvy řešit, můžete vydávání požadavků na webové služby a co nejdříve získat odpověď z jednoho, zrušení zbývajících požadavků.  Pomocná funkce, aby bylo snazší implementace tohoto společného modelu spuštění více operací, čeká na všechny a pak zrušení zbývajících můžete implementovat. `NeedOnlyOne` Tento scénář znázorňuje funkce v následujícím příkladu:  
  
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
  
### <a name="interleaved-operations"></a>Prokládané operace  
 Není možný problém s výkonem s použitím <xref:System.Threading.Tasks.Task.WhenAny%2A> metody pro podporu interleaving scénáře, když pracujete s velmi velké sady úloh.  Všechna volání <xref:System.Threading.Tasks.Task.WhenAny%2A> výsledkem byla registrovaná u každého úkolu pokračování. N počet úloh v důsledku O(N2) pokračování vytvořené během životního cyklu interleaving operace.  Pokud pracujete s rozsáhlou sadou úkolů, můžete použít kombinátorem (`Interleaved` v následujícím příkladu) Chcete-li vyřešit tyto problémy s výkonem:  
  
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
  
 Startup v rámci combinatoru pak můžete použít ke zpracování výsledků úloh po dokončení; Příklad:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 V některých scénářích bodový/shromažďování může být vhodné čekat pro všechny úkoly v sadě, pokud jeden z těchto chyb, v takovém případě chcete ukončit čekání, jakmile dojde k výjimce.  Můžete provést, která pomocí metody Startup v rámci combinatoru například `WhenAllOrFirstException` v následujícím příkladu:  
  
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
  
## <a name="building-task-based-data-structures"></a>Vytváření založené na úlohách datové struktury  
 Kromě možnosti vytvářet combinators vlastních založené na úlohách, že máte datové struktury v <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> , která představuje výsledky asynchronní operace a nezbytné synchronizace k připojení s ním umožňuje velmi efektivní Zadejte, na kterém můžete vytvořit vlastní datové struktury pro použití v asynchronní scénáře.  
  
### <a name="asynccache"></a>AsyncCache  
 Jeden důležitý aspekt jazyka úkolu je, že může být předat pro několik příjemců, které může await jeho pokračování registr s ním, získat její výsledek nebo výjimky (v případě třídy <xref:System.Threading.Tasks.Task%601>), a tak dále.  Díky tomu <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> dokonale hodí pro použití v asynchronním infrastrukturu ukládání do mezipaměti.  Tady je příklad malé, ale výkonné asynchronní mezipaměť postavený na <xref:System.Threading.Tasks.Task%601>:  
  
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
  
 [AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) třídy přijímá jako konstruktoru delegáta funkce, která přijímá `TKey` a vrátí <xref:System.Threading.Tasks.Task%601>.  Všechny dříve využívaných hodnoty z mezipaměti jsou uloženy v interní slovník a `AsyncCache` zajišťuje, aby pouze jeden úkol, je vygenerována pro klíč, i v případě, že mezipaměť je k ní přistupovat zároveň.  
  
 Můžete například vytvořit mezipaměť pro stažené webové stránky:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Potom můžete tuto mezipaměť v asynchronních metodách pokaždé, když je třeba obsah na webové stránce. `AsyncCache` Třídy zajistí, že při stahování co nejméně stránky jako možné a mezipamětí výsledky.  
  
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
 Úlohy můžete použít také k vytváření datových struktur pro koordinaci asynchronních aktivitách.  Vezměte v úvahu jednomu ze vzorů návrhu classic paralelní: producenta/konzumenta.  V tomto vzoru výrobci generují data, která je využívána spotřebitelů a producenti a spotřebitelé můžou běžet paralelně. Například příjemce zpracovává položka 1, který byl dříve vytvořen výrobce, který je teď vytváření položka 2.  Pro producenta/konzumenta najdete vzorek musíte vždy některé struktura dat pro uložení práce vytvořené výrobců tak, aby spotřebitelé být upozorněni na nová data a najít, když je k dispozici.  
  
 Tady je jednoduchý datová struktura postavené na úlohy, která umožňuje asynchronní metody, které se použijí jako producenti a spotřebitelé:  
  
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
  
 <xref:System.Threading.Tasks.Dataflow> Obor názvů obsahuje <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, který můžete použít podobným způsobem, aniž by bylo potřeba vytvářet vlastní typ kolekce:  
  
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
>  <xref:System.Threading.Tasks.Dataflow> Je k dispozici v oboru názvů [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] prostřednictvím **NuGet**. Chcete-li nainstalovat sestavení, které obsahuje <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projekt a vyhledejte online balíček Microsoft.Tpl.Dataflow.  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [Interoperabilita s jinými asynchronními vzory a typy](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
