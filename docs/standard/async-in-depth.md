---
title: Asynchronní do hloubky
description: Zjistěte, jak psát kód asynchronní vstupně-výstupní a vázané na procesor je jednoduché pomocí modelu .NET úkolově orientovanou asynchronní.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 7aa2bcdad9584ecf05dfee35e0887ed70737795d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492830"
---
# <a name="async-in-depth"></a>Asynchronní do hloubky

Zápis vázané na vstupně-výstupní operace a procesor asynchronní kód je jednoduchý pomocí modelu .NET úkolově orientovanou asynchronní. Model je zveřejněný prostřednictvím `Task` a `Task<T>` typy a `async` a `await` klíčová slova v jazyce C# a Visual Basic. (Specifické pro jazyk prostředky se nacházejí v [viz také](#see-also) části.) Tento článek vysvětluje, jak použít operátory async .NET a poskytuje podrobné informace o asynchronní framework použitá na pozadí.

## <a name="task-and-tasklttgt"></a>Úlohy a úkolů&lt;T&gt;

Úkoly jsou konstrukce používaný k implementaci, která se označuje jako [Promise modelu Concurrency](https://en.wikipedia.org/wiki/Futures_and_promises).  Stručně řečeno nabízejí, že jste "příslib", které pracují se dokončit později, umožňuje zajistěte ve spolupráci se příslib pomocí rozhraní API pro vyčištění.

*   `Task` představuje jednu operaci, která nevrací hodnotu.
*   `Task<T>` představuje jednu operaci, která vrátí hodnotu typu `T`.

Je důležité o úlohy jako abstrakce práce děje asynchronně, a *není* abstrakci přes dělení na vlákna. Ve výchozím nastavení se úkoly spustí v aktuální vlákno a delegátem práci do operačního systému, podle potřeby. Volitelně můžete úlohy můžete výslovně požadovány ke spuštění v samostatném vlákně prostřednictvím `Task.Run` rozhraní API.

Úlohy vystavit protokol rozhraní API pro monitorování, čeká na a přístup k výsledku hodnotu (v případě třídy `Task<T>`) úlohy. Integrace jazyka s `await` – klíčové slovo, poskytuje vyšší úroveň abstrakce pro používání úloh. 

Pomocí `await` umožňuje vaše aplikace nebo služba provádět užitečnou práci, zatímco úloha běží získávání řízení volajícímu, až po dokončení úkolu. Váš kód nemusí spoléhat na zpětná volání nebo událostí, které pokračovat v provádění po dokončení úlohy. Jazyk a úlohy integrace rozhraní API, které udělá za vás. Pokud používáte `Task<T>`, `await` – klíčové slovo bude kromě "rozbalení" hodnota vrácená po dokončení úkolu.  Podrobnosti o tom, jak to funguje jsou vysvětleny níže.

Další informace o úlohách a různé způsoby, jak pracovat s nimi v [úkolově orientovanou asynchronní vzor (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) tématu.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Prozkoumejte podrobněji úkoly pro vstupně-výstupní operace

Následující část popisuje, co se stane s volání typické asynchronní vstupně-výstupních operací 10 000 stopy zobrazení. Začněme několik příkladů.

První příklad volá asynchronní metodu a vrátí aktivní úkol, pravděpodobně zatím k dokončení.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

Druhý příklad přidá použití `async` a `await` klíčová slova se má operace provést úlohu.

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("https://www.dotnetfoundation.org");
    
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

Volání `GetStringAsync()` volání prostřednictvím nižší úrovně knihovny .NET (například voláním ostatních metod asynchronní) dokud nedosáhne P/Invoke spolupráce volání do nativního síťové knihovny. Nativní knihovna může následně volání do volání rozhraní API systému (například `write()` na soket v Linuxu). Objekt úlohy se vytvoří spravované/nativní hranice, případně pomocí [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Objekt úlohy se předává vrstvy, pravděpodobně provozovaná nebo přímo vrácená, nakonec se vrátí volajícímu počáteční. 

V druhém příkladu výše `Task<T>` objektu bude vrácen z `GetStringAsync`. Použití `await` – klíčové slovo způsobí, že metoda vrátí objekt nově vytvořené úlohy. Ovládací prvek vrátí volajícímu z tohoto umístění v `GetFirstCharactersCountAsync` metody. Metody a vlastnosti [úloh&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) objektu povolení volajícím můžete sledovat průběh úlohy, která bude dokončena, pokud byl proveden v GetFirstCharactersCountAsync zbývající kód.

Po volání rozhraní API systému žádost je nyní v prostoru jádra zajistit jeho způsob, jak síťový subsystém operačního systému (například `/net` v jádro Linuxu).  Tady operačního systému bude zpracovávat síťové žádosti *asynchronně*.  Podrobnosti se může lišit v závislosti na operační systém používá (volání ovladače zařízení může být naplánovaná jako signál odesílaných zpět do modulu runtime nebo volání ovladače zařízení se dají vytvořit a *pak* signál zaslal zpět), ale nakonec bude informován modulu runtime síťové žádosti se v průběhu.  V současné době práce pro ovladače zařízení budou být buď plánované, probíhá nebo už skončila (žádost je už si "při přenosu") – ale vzhledem k tomu, že to vše proběhne asynchronně, ovladače zařízení je schopná zpracovat okamžitě něco jiného!

V operační systém Windows například vlákno provede volání k ovladači zařízení sítě a vyzve ho k provedení této operace sítě prostřednictvím přerušení žádosti paketů (IRP), která představuje operaci.  Ovladače zařízení obdrží kontrolní, provede volání do sítě, označí IRP jako "čekající na vyřízení" a vrátí zpět do operačního systému.  Protože vlákna operačního systému nyní ví, že je kontrolní "čekající na vyřízení", nemá žádné další práci pro tuto úlohu a "vrátí" tak, aby je možné provádět jinou práci.

Pokud je požadavek splněn a data se vrátí zpět prostřednictvím ovladače zařízení, upozorní procesoru nová data přijatá přes přerušení.  Získá zpracování této přerušení se budou lišit v závislosti na operační systém, ale nakonec data se předají pomocí operačního systému dokud nedosáhne volání interop systému (třeba v systému Linux obslužné rutiny přerušení se naplánuje dolní polovinu IRQ předávání dat operačního systému  asynchronně).  Všimněte si, že tento *také* probíhá asynchronně!  Výsledkem je zařazena do fronty až další vlákno k dispozici je možné provést asynchronní metody a "rozbalení" výsledek dokončené úlohy.

V průběhu celý tento proces hlavní, co vyplývá je, že **žádné vlákno je vyhrazen pro spuštění úlohy**.  I když práce provádí v kontextu (to znamená, že operační systém nemá předat data do ovladače zařízení a reagovat na přerušení), je vyhrazený pro žádné vlákno *čekání* pro data z požadavku k téhle akci vrátit.  To umožňuje zpracovat mnohem větší objem práce spíše než čekání na některé volání vstupně-výstupních operací na dokončení systému.

I když výše může jevit jako toho ještě hodně udělat, když se měří se počtem skutečný čas, miniscule k je čas potřebný k vykonávají samotnou práci vstupně-výstupních operací. I když vůbec ne přesné potenciální časovou osu pro takové volání bude vypadat takto:

0-1————————————————————————————————————————————————–2-3

*   Doba trvání z bodů `0` k `1` všechno, co je až do asynchronní metody vrací řízení volajícímu.
*   Doba trvání z bodů `1` k `2` čas strávený vstupně-výstupní operace se žádné náklady.
*   A konečně, doba trvání z bodů `2` k `3` předává řízení zpět (a potenciálně hodnotu) do asynchronní metody, v tomto okamžiku je znovu prováděna.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to znamená pro scénář serveru?

Tento model funguje dobře s úlohou scénář typický server.  Vzhledem k tomu, že neexistují žádná vlákna vyhrazený pro blokování nedokončené úkoly, fondu vláken server služby mnohem větší objem webových požadavků.

Vezměte v úvahu dva servery: ten, který spouští asynchronní kód a ten, který se nepodporuje.  Pro účely tohoto příkladu má každý server jenom 5 vlákna, které jsou k dispozici pro žádosti o služby.  Všimněte si, že tato čísla jsou imaginarily malé a slouží pouze v rámci Demonstrativní.

Předpokládejme, že oba servery přijímat 6 souběžných požadavků. Každý požadavek provádí vstupně-výstupní operace.  Server *bez* asynchronní kód má zařadit do fronty požadavek 6 až jedno z 5 vláken mít dokončené práce vstupně-výstupní zapsán odpovědi. V okamžiku, 20. prosincem požadavek odeslaný v, může server spustit zpomalit, protože fronta je stále příliš dlouhý.

Server *s* asynchronní kód spuštěný na ní stále fronty 6 požadavek, ale protože používá `async` a `await`, každý z jeho vlákna jsou uvolněna při spuštění vstupně-výstupní pracovní místo po dokončení.  Ve čas 20. prosincem žádost obsahuje ve frontě příchozích požadavků bude mnohem menší (pokud ho neobsahuje nic vůbec), a nebude server zpomalovat.

Přestože je toto contrived příklad, funguje ve velmi podobně jako ochrana čipem v reálném světě.  Ve skutečnosti můžete očekávat, že server moct zpracovávat další požadavky na použití jednotkách o řád `async` a `await` než pokud to bylo vyhradíte vlákno pro každý požadavek přijme.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to znamená pro scénář klienta?

Největší zisk pro používání `async` a `await` pro klienta je zvýšení rychlosti odezvy aplikace.  I když responzivní aplikace můžete vytvořit pomocí ruční vytváření podřízeného procesu vlákna, v rámci vytváření podřízeného procesu vlákna je náročná operace vzhledem k použití pouze `async` a `await`.  Zejména u něco jako mobilní hru vliv na vlákně UI při co kde jde o vstupně-výstupních operací je velmi důležité.

Důležitější je protože pracovní vstupně-výstupní stráví prakticky žádný čas na CPU, vyhradíte celé vlákno procesor k provádění i neziskovky jakékoli užitečné práce by špatné využití prostředků.

Kromě toho, kterému dodává práci na vlákno uživatelského rozhraní (např. aktualizace uživatelského rozhraní) je velmi jednoduchý s `async` metody a nevyžaduje další práce (jako je například volání delegáta bezpečným pro vlákno).

## <a name="deeper-dive-into-task-and-tasklttgt-for-a-cpu-bound-operation"></a>Dozvědět více o úkolu a úkolu&lt;T&gt; pro operace vázané na procesor

Vázané na procesor `async` kód je trochu jiná než vstupně-výstupní `async` kódu.  Protože práce se provádí na CPU, neexistuje žádný způsob, jak překonat vyhradíte vlákno k výpočtu.  Použití `async` a `await` poskytuje čistý způsob, jak pracovat s pozadí vlákna a zachovat responzivní volajícímu asynchronní metody.  Všimněte si, že to neposkytuje ochranu pro sdílená data.  Pokud používáte sdílených dat, je stále potřeba použití strategie příslušné synchronizace.

Tady je přehled 10 000 stopy asynchronního volání vázané na procesor:

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

`CalculateResult()` provede na vlákno, byla volána pro.  Když volá `Task.Run`, se zařadí do fronty náročná operace vázané na procesor `DoExpensiveCalculation()`, ve fondu vláken a přijímá `Task<int>` zpracovat.  `DoExpensiveCalculation()` Nakonec běží souběžně na další dostupný vlákně, pravděpodobně na další Procesorové jádro.  Je možné provádět souběžné práce při `DoExpensiveCalculation()` je zaneprázdněný v jiném vlákně, protože vlákno, které volá `CalculateResult()` stále probíhá.

Jednou `await` nalezen, provádění `CalculateResult()` se vrátil volajícímu, což jiné práce s aktuálním vláknem při `DoExpensiveCalculation()` odchází si výsledek.  Po dokončení, výsledek je ve frontě ke spuštění v hlavním vlákně.  Nakonec vrátí hlavního vlákna pro provádění `CalculateResult()`, kdy bude mít výsledek `DoExpensiveCalculation()`.

### <a name="why-does-async-help-here"></a>Proč asynchronní pomůže tady?

`async` a `await` jsou doporučené správu práce vázané na procesor při potřebujete rychlost odezvy. Existuje více vzory pro použití modifikátoru async pomocí práce vázané na procesor. Je důležité si uvědomit, že je s malými náklady na použití modifikátoru async a se nedoporučuje úzkou smyčky for.  To je na vás k určení, jak při psaní kódu kolem této nové funkci.

## <a name="see-also"></a>Viz také:

- [Asynchronní programování v jazyce C#](~/docs/csharp/async.md)
- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../csharp/programming-guide/concepts/async/index.md)
- [Asynchronní programování vF#](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
