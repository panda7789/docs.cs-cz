---
title: Asynchronní v hloubkě
description: Přečtěte si, jak je možné zapisovat do vstupně-výstupních operací a asynchronního kódu vázaného na procesor, pomocí asynchronního modelu založeného na úlohách .NET.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 91fd37ce329c03b43b5472e4579be7f5ef961738
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169111"
---
# <a name="async-in-depth"></a>Asynchronní v hloubkě

Zápisy do vstupně-výstupních operací a asynchronního kódu vázaného na procesor jsou jednoduché pomocí asynchronního modelu založeného na úlohách .NET. Model je `Task` zveřejněn typy a `async` `Task<T>` a klíčovými slovy `await` C# a a Visual Basic. (Prostředky specifické pro jazyk najdete v části [Viz také](#see-also) .) Tento článek vysvětluje, jak použít .NET Async a poskytuje přehled o asynchronním rozhraní, které se používá v rámci pokrývání.

## <a name="task-and-taskt"></a>Úloha a úloha\<T >

Úkoly jsou konstrukce používané k implementaci toho, co je známo jako [model příslib souběžnosti](https://en.wikipedia.org/wiki/Futures_and_promises).  V krátkém případě vám nabídne "příslib", který se v pozdější fázi dokončí, takže budete mít k dispozici příslib s čistým rozhraním API.

- `Task`představuje jednu operaci, která nevrací hodnotu.
- `Task<T>`představuje jednu operaci, která vrací hodnotu typu `T`.

Je důležité mít důvod na úlohy, jako abstrakce práce, které provádí asynchronně, a *ne* abstrakce nad vlákny. Ve výchozím nastavení se úlohy spouštějí v aktuálním vlákně a podle potřeby deleguje práci s operačním systémem. Volitelně je možné úlohy explicitně požadovat, aby se spouštěly na samostatném vlákně přes `Task.Run` rozhraní API.

Úlohy zpřístupňují protokol rozhraní API pro monitorování, čeká na něj a přistupuje k výsledné hodnotě (v případě `Task<T>`) úkolu. Jazyková integrace s `await` klíčovým slovem poskytuje abstrakci vyšší úrovně pro používání úkolů.

Pomocí `await` nástroje umožňuje vaše aplikace nebo služba provádět užitečnou práci, zatímco je úloha spuštěná, a to tak, že je řízení volajícího, dokud se úkol nedokončí. Váš kód nemusí spoléhat na zpětná volání nebo události, aby bylo možné pokračovat v provádění po dokončení úkolu. Integrace rozhraní API jazyka a úloh to dělá za vás. Pokud používáte `Task<T>` `await` , klíčové slovo dále "rozbalení" vrátí hodnotu vrácenou po dokončení úkolu.  Podrobnosti o tom, jak tyto funkce jsou vysvětleny níže.

Další informace o úlohách a různých způsobech, jak s nimi pracovat, najdete v tématu [asynchronního vzoru založeného na úlohách (klepnutím)](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) .

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Hlubší podrobně v úlohách operace vázané na vstup a výstup

Následující část popisuje pohled 10 000 na to, co se stane s typickým asynchronním vstupně-výstupním voláním. Pojďme začít několika příklady.

První příklad volá asynchronní metodu a vrátí aktivní úlohu, která se nejspíš ještě dokončila.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

Druhý příklad přidá použití `async` klíčového slova a `await` pro práci na úkolu.

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

Volání `GetStringAsync()` volání prostřednictvím knihoven rozhraní .NET nižší úrovně (případně volání jiných asynchronních metod), dokud nedosáhne volání Interop volání nespravovaného kódu do nativní síťové knihovny. Nativní knihovna může následně volat volání rozhraní API systému (například `write()` k soketu na platformě Linux). Objekt úlohy bude vytvořen v nativní/spravované hranici, případně pomocí [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Objekt Task se předává přes vrstvy, případně spuštěný nebo přímo vracený, nakonec vráceného počátečnímu volajícímu.

V druhém příkladu výše `Task<T>` se vrátí objekt z. `GetStringAsync` Použití `await` klíčového slova způsobí, že metoda vrátí nově vytvořený objekt Task. Řízení se vrátí volajícímu z tohoto umístění v `GetFirstCharactersCountAsync` metodě. Metody a vlastnosti objektu [Task&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) umožňují volajícím monitorovat průběh úkolu, který bude dokončen, když zbývající kód v GetFirstCharactersCountAsync proveden.

Po volání rozhraní API systému je požadavek teď v prostoru jádra a díky němu se bude jednat o Síťový subsystém operačního systému (například `/net` v jádru Linux).  V tomto případě bude operační systém zpracovávat požadavky sítě *asynchronně*.  Podrobnosti se můžou lišit v závislosti na použitém operačním systému (může být volání ovladače zařízení naplánované jako signál, který se zpátky do modulu runtime), nebo může být provedeno volání ovladače zařízení, které se *pak* pošle zpátky. za běhu se ale bude informovat, že se jedná o síť. žádost probíhá.  V tuto chvíli bude práce pro ovladač zařízení buď naplánována, probíhá, nebo již dokončena (žádost již je přenášena po síti "), ale vzhledem k tomu, že k této situaci dojde asynchronně, ovladač zařízení bude moci okamžitě zvládnout něco jiného.

Například ve Windows vlákno operačního systému zavolá ovladač síťového zařízení a požádá ho, aby provedl síťové operace prostřednictvím paketu požadavku přerušení (IRP), který představuje operaci.  Ovladač zařízení přijme požadavek IRP, provede volání do sítě, označí požadavek IRP jako "pending" a vrátí se zpět do operačního systému.  Vzhledem k tomu, že vlákno operačního systému nyní ví, že je IRP "čeká", nemá další práci pro tuto úlohu a "vrátí" zpět, aby je bylo možné použít k provedení jiné práce.

Když je žádost splněná a data se vrátí přes ovladač zařízení, upozorní procesor nových dat přijatých prostřednictvím přerušení.  Způsob zpracování tohoto přerušení se bude lišit v závislosti na operačním systému, ale data budou předána operačním systémem, dokud nedosáhne volání interoperability systému (například v systému Linux obslužná rutina přerušení naplánuje poslední polovinu IRQ, aby předávala data v operačním systému.  asynchronně).  Všimněte si, že se k tomu *taky* dochází asynchronně.  Výsledek je zařazen do fronty, dokud další dostupné vlákno nebude moci spustit asynchronní metodu a "rozbalení" výsledku dokončeného úkolu.

V celém rámci celého procesu Key poznatkem je, že **pro spuštění úlohy není žádné vlákno vyhrazené**.  I když se práce provádí v nějakém kontextu (to znamená, že operační systém musí předávat data do ovladače zařízení a reagovat na přerušení), neexistuje žádné vlákno vyhrazené k *čekání* na to, aby se data od žádosti vrátila zpět.  Díky tomu může systém zpracovávat mnohem větší objem práce, a ne čekat na dokončení některých vstupně-výstupních volání.

I když výše se může zdát, že je třeba udělat spoustu práce, která se měří z pohledu na hodinový čas, je miniscule v porovnání s časem potřebným ke skutečnému vstupně-výstupní práci. I když to není zcela přesné, potenciální časová osa pro takové volání by vypadala takto:

0-1————————————————————————————————————————————————–2-3

- Čas strávený z `0` bodů `1` na je vše až do chvíle, kdy asynchronní metoda neposkytne řízení volajícímu.
- Čas strávený z `1` bodů `2` na je čas strávený na vstupu a výstupu bez nákladů na procesor.
- Nakonec čas strávený z bodů `2` na `3` je předání řízení zpět (a potenciálně hodnoty) asynchronní metodě, při které je prováděna znovu.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to znamená pro serverový scénář?

Tento model funguje dobře s typickou úlohou serverového scénáře.  Vzhledem k tomu, že nejsou k dispozici žádná vlákna vyhrazená pro blokování nedokončených úloh, může služba nečinnosti serveru dosloužit mnohem větší objem webových požadavků.

Vezměte v úvahu dva servery: jeden, který spouští asynchronní kód, a druhý, který ne.  Pro účely tohoto příkladu má každý server pouze 5 vláken dostupných pro žádosti o služby.  Všimněte si, že tato čísla jsou imaginarily malá a slouží pouze jako provedený kontext.

Předpokládat, že oba servery obdrží 6 souběžných požadavků. Každý požadavek provede vstupně-výstupní operaci.  Server *bez* asynchronního kódu musí zařadit šest požadavků do fronty, dokud jedna z 5 vláken nedokončí práci v/v vázané na vstup/výstup a napsala odpověď. V okamžiku, kdy dojde k dvacáté žádosti, může server začít zpomalovat, protože fronta je příliš dlouhá.

Server *s* asynchronním kódem, který je v něm spuštěný, stále zařadí do fronty šestý `await`požadavek, ale protože používá `async` a, každé z jeho vláken se uvolní při zahájení práce na vstupu/výstupu, a ne po jeho dokončení.  V době, kdy se 20 žádostí dostanou, bude fronta pro příchozí požadavky mnohem menší (Pokud má vůbec vše) a server nebude pomalý.

I když se jedná o contrived příklad, funguje v reálném světě velmi podobným způsobem.  Ve skutečnosti můžete očekávat, že server bude schopen zpracovat pořadí většího počtu požadavků pomocí `async` a, `await` než kdyby vyhradí vlákno pro každý požadavek, který obdrží.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to znamená pro klientský scénář?

Největším ziskem při `async` používání `await` a pro klientské aplikace je zvýšení rychlosti odezvy.  I když lze aplikaci nastavit jako odezvu ručním vytvářením vláken, je operace vytvoření vlákna náročná na to, že právě používá `async` a. `await`  Zvláště pro něco podobného mobilní hře, což ovlivňuje co nejmenší stav vlákna uživatelského rozhraní, kde je důležité vstup/výstup.

Důležitější je, vzhledem k tomu, že práce vázané na vstupně-výstupní operace tráví prakticky bez času na procesoru, což vyhradí celé PROCESORové vlákno, aby fungovalo zlomek, by mohlo být špatné využití prostředků.

Kromě toho odesílání práce do vlákna uživatelského rozhraní (například aktualizace uživatelského rozhraní) je velmi jednoduché s `async` metodami a nevyžaduje další práci (například volání delegáta bezpečného pro přístup z více vláken).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Hlubší podrobně do úlohy a úlohy\<T > pro operace vázané na procesor

Kód vázaný `async` na procesor je trochu jiný než kód vázaný `async` na vstupně-výstupní operace.  Vzhledem k tomu, že práce se provádí na procesoru, neexistuje žádný způsob, jak se vyhnout vyhradit vlákno pro výpočet.  Použití `async` a`await` poskytuje čistě způsob, jak pracovat s vláknem na pozadí a udržet volající asynchronní metody reagovat.  Všimněte si, že to neposkytuje žádnou ochranu pro sdílená data.  Pokud používáte sdílená data, budete stále muset použít vhodnou strategii synchronizace.

Zde je zobrazení asynchronního volání vázané na procesor 10 000:

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

`CalculateResult()`provede se ve vlákně, ve kterém byla volána.  Při volání `Task.Run`do fronty zařadí nákladné operace vázané na procesor, `DoExpensiveCalculation()`ve fondu `Task<int>` vláken a získá popisovač.  `DoExpensiveCalculation()`je nakonec spouštěn souběžně v dalším dostupném vlákně, což je pravděpodobný jiný procesor.  Je možné provést souběžnou práci, zatímco `DoExpensiveCalculation()` je zaneprázdněna jiným vláknem, protože vlákno, které `CalculateResult()` se volá, je stále spuštěno.

Po `await` zjištění, že `CalculateResult()` spuštění je vráceno volajícímu, což umožňuje, aby se v průběhu `DoExpensiveCalculation()` provádění jiné práce s aktuálním vláknem prováděla výsledek.  Po dokončení je výsledek zařazen do fronty pro spuštění v hlavním vlákně.  Nakonec se hlavní vlákno vrátí ke spuštění `CalculateResult()`a v tomto okamžiku bude mít `DoExpensiveCalculation()`výsledek.

### <a name="why-does-async-help-here"></a>Proč tady funguje asynchronní pomoc?

`async`a `await` jsou osvědčenými postupy pro správu práce vázané na procesor, když potřebujete reagovat. Je k dispozici několik vzorů pro použití asynchronních v práci vázané na procesor. Je důležité si uvědomit, že pro použití asynchronního přenosu a pro těsné smyčky se nedoporučuje používat asynchronní operace.  Je to až na to, abyste zjistili, jak píšete kód kolem této nové funkce.

## <a name="see-also"></a>Viz také:

- [Asynchronní programování vC#](../csharp/async.md)
- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](../csharp/programming-guide/concepts/async/index.md)
- [Asynchronní programování vF#](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../visual-basic/programming-guide/concepts/async/index.md)
