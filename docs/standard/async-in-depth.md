---
title: "Asynchronní podrobněji"
description: "Zjistěte, jak zápis I/čítači a vázané na procesor asynchronní kódu je přehledné pomocí modelu .NET Task-based asynchronní."
keywords: "Rozhraní .NET, rozhraní .NET core, Standard rozhraní .NET"
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b23a90de991b31005ba5a07a959c717c24869ffb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="async-in-depth"></a>Asynchronní podrobněji

Zápis vázané na vstupně-výstupních operací a procesor asynchronní kód je přehledné pomocí modelu .NET Task-based asynchronní. Model je zveřejněný prostřednictvím `Task` a `Task<T>` typy a `async` a `await` klíčová slova v C# a Visual Basic. (Prostředky pro konkrétní jazyky, které se nacházejí v [viz také](#see-also) části.) Tento článek vysvětluje, jak použít asynchronní rozhraní .NET a poskytuje vhled do rozhraní asynchronní použít v pozadí.

## <a name="task-and-tasklttgt"></a>Úlohy a úkolů&lt;T&gt;

Úlohy jsou konstrukce používané k implementaci, která se označuje jako [Promise modelu Concurrency](https://en.wikipedia.org/wiki/Futures_and_promises).  Stručně řečeno nabízejí můžete "příslib" které pracují se dokončit později, umožňují koordinaci s promise s čistou rozhraní API.

*   `Task`představuje jednu operaci, která nevrátí hodnotu.
*   `Task<T>`představuje jednu operaci, která vrátí hodnotu typu `T`.

Je důležité důvod o úlohách jako abstrakce pracovní děje asynchronně, a *není* abstrakci přes dělení na vlákna. Ve výchozím nastavení úlohy spustit na aktuální pracovní vlákno a delegovat do operačního systému, podle potřeby. Volitelně můžete úlohy můžete explicitně požadovanou ke spuštění na samostatné vlákno prostřednictvím `Task.Run` rozhraní API.

Úlohy vystavit protokol rozhraní API pro monitorování, čeká na a přístup k hodnotě výsledek (u `Task<T>`) úlohy. Integrace jazyka s `await` – klíčové slovo, poskytuje vyšší úrovni abstrakce pro používání úlohy. 

Pomocí `await` umožňuje provádět užitečné práci, zatímco úloha běží je ovládací prvek jeho volajícího, dokud se provádí úloha vaše aplikace nebo služba. Váš kód není nutné spoléhají na zpětná volání nebo události pro pokračování v provádění po dokončení úlohy. Jazyk a úloh integrace rozhraní API nepodporuje který pro vás. Pokud používáte `Task<T>`, `await` – klíčové slovo bude kromě "rozbalení" hodnota vrácená po dokončení úlohy.  Podrobnosti o tom, jak to funguje jsou vysvětleny níže.

Další informace o úlohách a různé způsoby, jak pracovat s nimi v [založený na úlohách asynchronní vzor (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) tématu.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Podrobnější prohlídku do úlohy I/čítači operace

Následující část popisuje, co se stane s typické asynchronní vstupně-výstupních operací volání 10 000 stopy zobrazení. Začněme několik příkladů.

V prvním příkladu volá asynchronní metody a vrátí aktivní úkol, pravděpodobně ještě dokončit.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("http://www.dotnetfoundation.org");
}
```

V druhém příkladu přidá použití `async` a `await` klíčová slova pracovat v úloze.

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("http://www.dotnetfoundation.org");
    
    // Execution resumes when the client.GetStringAsync task completes,
    // becoming synchronous again.
    
    if (count > page.Length)
    {
        return page;
    }
    else
    {
        return page.Substring(0, count);
    }
}
```

Volání `GetStringAsync()` volání nižší úrovně knihovny .NET (například volání jiných asynchronní metody) dokud dosáhne P/Invoke spolupráce volání do nativního síťové knihovny. Nativní knihovny může následně volání do volání rozhraní API systému (například `write()` na soket v systému Linux). Objekt úlohy se vytvoří v nativní nebo spravovaný hranic, které by mohly mít pomocí [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Objekt úlohy budou předána vrstvy, pravděpodobně zpracovat nebo přímo vrátil, nakonec vrátí počáteční volajícího. 

V druhém příkladu výše `Task<T>` objekt se vrátil z `GetStringAsync`. Použití `await` – klíčové slovo způsobí, že metoda vrátí objekt nově vytvořená úloha. Vrátí ovládací prvek na volajícího z tohoto umístění v `GetFirstCharactersCountAsync` metoda. Metody a vlastnosti [úloh&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) objektu volajícím povolit pro monitorování průběhu úlohy, která se dokončí po zbývající kód v GetFirstCharactersCountAsync má provedení.

Po volání rozhraní API systému požadavku je nyní v prostoru jádra zajistit jeho způsob, jak síťového podsystému operačního systému (například `/net` Linux jádra systému).  Zde operačního systému sítě požadavek zpracuje *asynchronně*.  Podrobnosti se může lišit v závislosti na operačního systému používá (volání ovladače zařízení může být naplánovaná jako signál odeslána zpět do modulu runtime, nebo může být provedeno volání ovladačů zařízení a *pak* signál k odeslání zpět), ale nakonec budou informováni modul runtime aby sítě žádost je zpracovávána.  V tomto okamžiku pracovní ovladače zařízení budou buď být naplánované, probíhá nebo již bylo dokončeno, (požadavek je již na "přenášených v síti") – ale protože je to všechny děje asynchronně, ovladače zařízení je schopna okamžitě zpracovávat něco jiného!

V systému Windows operační systém například vlákno zavolá k ovladači zařízení sítě a požádá ji k provedení operace sítě prostřednictvím přerušení požadavku paketů (IRP), která představuje operaci.  Ovladače zařízení obdrží kontrolní, provede volání k síti, označí IRP jako "čekající na vyřízení" a vrátí zpět do operačního systému.  Vzhledem k tomu, že vlákno operačního systému teď ví, že je kontrolní "čekající", nemá žádné další práci udělat pro tuto úlohu a "vrátí" tak, aby ho lze provádět jinou práci.

Při splnění požadavku na a data zpátky prostřednictvím ovladače zařízení, upozorní procesoru nová data obdržel prostřednictvím přerušení.  Získá zpracování této přerušení se liší podle operačního systému, ale nakonec data budou předány prostřednictvím operačního systému dokud nedosáhne spolupráce volání systému (třeba v systému Linux obslužné rutiny přerušení se naplánuje dolní polovinu požadavku přerušení na předání dat operačního systému  asynchronně).  Poznámka: Tento to *také* probíhá asynchronně!  Výsledkem je ve frontě, dokud další vlákno k dispozici je možné provést asynchronní metody a "rozbalení" výsledek dokončené úlohy.

V rámci celého tohoto procesu klíče takeaway je, že **žádný přístup z více vláken je vyhrazen pro spuštění úlohy**.  I když pracovní se spouštějí v kontextu některé (to znamená, operačního systému nutné předat data do ovladač zařízení a reagovat na přerušení), žádný přístup z více vláken je vyhrazený pro *čekání* pro data z požadavku opět online.  To umožňuje systému pro zpracování mnohem větší objem práce místo čekání volání některé vstupně-výstupních operací na dokončení.

Výše se mohou jevit jako hodně práce má být provedena, když měří podle skutečný čas, sice miniscule ve srovnání s čas potřebný k vykonávají samotnou práci vstupně-výstupní operace. I když nejsou vůbec přesné potenciální časovou osu pro volání bude vypadat takto:

0-1————————————————————————————————————————————————–2-3

*   Čas strávený z bodů `0` k `1` je všechno, dokud asynchronní metody vypočítá ovládacího prvku do jeho volajícího.
*   Čas strávený z bodů `1` k `2` časem stráveným na vstupně-výstupních operací s žádné procesoru náklady.
*   Nakonec čas strávený z bodů `2` k `3` je předávání řízení zpět (a potenciálně hodnotu) do asynchronní metody, které okamžiku je znovu prováděna.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to znamená pro scénář serveru?

Tento model funguje dobře u zatížení scénář typické serveru.  Protože nejsou k dispozici nejsou žádná vlákna vyhrazený pro blokování nedokončené úloh, můžete server fondu služby mnohem vyšší objem webových žádostí.

Vezměte v úvahu dva servery: ten, který spouští asynchronní kód a ten, který neexistuje.  Pro účely tohoto příkladu má každý server jenom 5 vláken, které jsou k dispozici pro žádosti o služby.  Všimněte si, že tato čísla jsou imaginarily malé a sloužit pouze v kontextu demonstrative.

Předpokládejme, že oba servery přijímat 6 souběžných požadavků. Každý požadavek provede vstupně-výstupní operace.  Server *bez* asynchronní kódu má do fronty až 6. žádost, dokud jeden z 5 vláken dokončení práce I/čítači a zapsán odpovědi. V místě, které 20 požadavek odeslán může server spustit zpomalit, protože fronta je získávání příliš dlouhý.

Server *s* asynchronní kód spuštěný na něm stále fronty až 6. požadavek, ale protože používá `async` a `await`, každý z jeho vláken jsou uvolněna, když se spustí I/čítači pracovní místo po dokončení.  V čase 20 žádost pochází ve frontě příchozích požadavků bude mnohem menší (pokud ho neobsahuje nic vůbec), a nebude zpomalit serveru.

Přestože je toto contrived příklad, funguje velmi podobně jako ochrana v reálném světě.  Ve skutečnosti můžete očekávat, že server moct zpracovávat další požadavky pomocí řádově `async` a `await` než pokud ho byly vyhradit vlákno pro každý požadavek obdrží.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to znamená pro scénář klienta?

Největších nárůst pro používání `async` a `await` pro klienta aplikace je zvýšení odezvy.  I když reaguje aplikace můžete vytvořit pomocí při vytváření kopie vlákna ručně, v rámci při vytváření kopie vlákna je náročná operace relativně k jenom pomocí `async` a `await`.  Hlavně pro něco jako mobilní hry je velmi důležitý co nejméně vlákna uživatelského rozhraní kde problémem vstupně-výstupních operací, které mají vliv.

Je důležité protože pracovní I/čítači stráví prakticky žádný čas na procesoru, vyhradit celé vlákno procesoru provádět sotva jakékoli užitečné práce by špatné využití prostředků.

Kromě toho odeslání pracovní vlákno uživatelského rozhraní (například aktualizace uživatelského rozhraní) je velmi jednoduchý s `async` metody a nevyžaduje další práci (jako například volání delegáta vláken).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Podrobnější prohlídku do úloh a úloh<T> operace vázané na procesor

Vázané na procesor `async` kód je trochu jiná než I/čítači `async` kódu.  Protože práci na procesoru, neexistuje žádný způsob, jak získat kolem vyhradit vlákno pro výpočet.  Použití `async` a `await` poskytuje můžete s čistou způsob, jak pracovat s pozadí vláken a ponechat volající asynchronní metody reaguje.  Všimněte si, že to neposkytuje ochranu pro sdílená data.  Pokud používáte sdílená data, musíte pořád vztahují příslušné synchronizace strategie.

Tady je 10 000 stopy zobrazení asynchronního volání vázané na procesor:

```csharp
public async Task<int> CalculateResult(InputData data)
{
    // This queues up the work on the threadpool.
    var expensiveResultTask = Task.Run(() => DoExpensiveCalculation(data));
    
    // Note that at this point, you can do some other work concurrently,
    // as CalculateResult() is still executing!
    
    // Execution of CalculateResult is yielded here!
    var result = await expensiveResultTask;
    
    return result;
}
```

`CalculateResult()`provede ve vlákně na byla volána.  Při volání `Task.Run`, se zařadí do fronty náročná operace vázané na procesor, `DoExpensiveCalculation()`, ve fondu vláken a přijímá `Task<int>` zpracování.  `DoExpensiveCalculation()`Nakonec běží souběžně na další dostupný vlákno, pravděpodobně na jiné jádro procesoru.  Je možné souběžných práci při `DoExpensiveCalculation()` je zaneprázdněn na jiné vlákno, protože vláken, který označuje `CalculateResult()` stále probíhá.

Jednou `await` bez provedení `CalculateResult()` jeho volajícího, povolení dalších práce s aktuálním vláknem při, je vhodné `DoExpensiveCalculation()` je produkování výsledku.  Po dokončení, výsledek je zařadit do fronty ke spuštění na hlavní vlákno.  Nakonec se vrátí hlavního vlákna pro provádění `CalculateResult()`, na bod, který bude mít výsledek `DoExpensiveCalculation()`.

### <a name="why-does-async-help-here"></a>Proč asynchronní pomáhá tady?

`async`a `await` jsou nejlepší praxi Správa pracovních vázané na procesor, když potřebujete odezvy. Existuje více vzory pro použití modifikátoru async s pracovní vázané na procesor. Je důležité si uvědomit, že je malé náklady na použití modifikátoru async a není doporučeno pro úzkou smyčky.  Je to na určit, jak psát kód kolem této nové funkci.

## <a name="see-also"></a>Viz také

[Asynchronní programování v jazyce C#](~/docs/csharp/async.md)   
[Asynchronní programování v F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
