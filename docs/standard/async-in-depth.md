---
title: Asynchronní do hloubky
description: Zjistěte, jak je psaní asynchronního kódu vázaného na vstupně-výstupní chod a procesoru jednoduché pomocí asynchronního modelu založeného na úlohách .NET.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 91fd37ce329c03b43b5472e4579be7f5ef961738
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70169111"
---
# <a name="async-in-depth"></a>Asynchronní do hloubky

Zápis asynchronního kódu vázaného na vstupně-výstupní a procesor je jednoduchý pomocí asynchronního modelu založeného na úlohách .NET. Model je vystaven `Task` a `Task<T>` typy `async` a `await` a klíčová slova v jazyce C# a Visual Basic. (Prostředky specifické pro jazyk se nacházejí v části [Viz také.)](#see-also) Tento článek vysvětluje, jak používat asynchronní rozhraní .NET a poskytuje přehled o asynchronní rámci používané pod kryty.

## <a name="task-and-taskt"></a>> úkol\<a úkol T

Úkoly jsou konstrukce používané k implementaci co je známé jako [promise model souběžnosti](https://en.wikipedia.org/wiki/Futures_and_promises).  Stručně řečeno, nabízejí vám "slib", že práce bude dokončena později, což vám umožní koordinovat se slibem s čistým rozhraním API.

- `Task`představuje jednu operaci, která nevrací hodnotu.
- `Task<T>`představuje jednu operaci, která `T`vrací hodnotu typu .

Je důležité důvod o úkoly jako abstrakce práce děje asynchronně a *nikoli* abstrakce přes threading. Ve výchozím nastavení se úlohy provádějí v aktuálním vlákně a delegují práci na operační systém podle potřeby. Volitelně lze úkoly explicitně požádat o `Task.Run` spuštění v samostatném vlákně prostřednictvím rozhraní API.

Úkoly vystavit protokol rozhraní API pro sledování, čekání a přístup `Task<T>`k hodnotě výsledku (v případě) úkolu. Integrace jazyků pomocí `await` klíčového slova poskytuje abstrakce vyšší úrovně pro použití úkolů.

Použití `await` umožňuje vaší aplikaci nebo službě provádět užitečnou práci, zatímco je úloha spuštěna tím, že dává řízení volajícímu, dokud není úloha hotová. Váš kód nemusí spoléhat na zpětná volání nebo události pokračovat v provádění po dokončení úlohy. Integrace rozhraní API pro jazyk a úlohy to dělá za vás. Pokud používáte `Task<T>`, `await` klíčové slovo bude navíc "rozbalit" hodnotu vrácenou po dokončení úlohy.  Podrobnosti o tom, jak to funguje, jsou vysvětleny níže.

Další informace o úkolech a různých způsobech interakce s nimi najdete v tématu [Asynchronní vzor založený na úlohách (TAP).](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Hlubší proměna úkolů pro i/o-vázanou operaci

Následující část popisuje 10 000 stop zobrazení toho, co se stane s typickou asynchronní i/O volání. Začněme s několika příklady.

První příklad volá asynchronní metodu a vrátí aktivní úlohu, pravděpodobně ještě nedokončenou.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

Druhý příklad přidá použití `async` `await` a klíčová slova pro provoz na úkolu.

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

Volání `GetStringAsync()` volání prostřednictvím knihoven .NET nižší úrovně (možná volání jiných asynchronních metod), dokud nedosáhne volání Interop P/Invoke do nativní síťové knihovny. Nativní knihovna může následně volat do `write()` volání rozhraní API systému (například do soketu v Systému Linuxu). Objekt úlohy bude vytvořen na nativní/spravované hranici, případně pomocí [taskcompletionsource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Objekt úlohy bude předán přes vrstvy, případně provozovány nebo přímo vráceny, nakonec vráceny počáteční volajícího.

Ve druhém příkladu `Task<T>` výše bude objekt `GetStringAsync`vrácen z . Použití klíčového `await` slova způsobí, že metoda vrátí nově vytvořený objekt úkolu. Ovládací prvek vrátí volajícímu z `GetFirstCharactersCountAsync` tohoto umístění v metodě. Metody a vlastnosti objektu [Task&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) umožňují volajícím sledovat průběh úlohy, která bude dokončena po spuštění zbývajícího kódu v aplikaci GetFirstCharactersCountAsync.

Po volání rozhraní API systému je nyní požadavek v prostoru jádra a provází se do síťového subsystému operačního systému (například `/net` v jádru Linuxu).  Zde operační hospací modul bude zpracovávat síťový požadavek *asynchronně*.  Podrobnosti se mohou lišit v závislosti na použitém operačním systému (volání ovladače zařízení může být naplánováno jako signál odeslaný zpět do runtime nebo může být provedeno volání ovladače zařízení a *poté* signál odeslán zpět), ale nakonec bude za běhu informováno, že probíhá požadavek na síť.  V tomto okamžiku bude práce pro ovladač zařízení buď naplánována, v průběhu, nebo již dokončena (požadavek je již mimo "přes drát") - ale protože se to všechno děje asynchronně, ovladač zařízení je schopen okamžitě zvládnout něco jiného!

Například v systému Windows podproces operačního systému provede volání ovladače síťového zařízení a požádá jej o provedení síťové operace prostřednictvím paketu požadavku přerušení (IRP), který představuje operaci.  Ovladač zařízení přijme irp, provede volání do sítě, označí IRP jako "čekající" a vrátí se zpět do operačního systému.  Vzhledem k tomu, že vlákno operačního ses nyní ví, že IRP je "čekající", nemá žádné další práce pro tuto práci a "vrátí" zpět tak, aby jej lze použít k provádění jiné práce.

Když je požadavek splněn a data se vrátí zpět prostřednictvím ovladače zařízení, upozorní procesor uhlazených na nová data přijatá prostřednictvím přerušení.  Jak se toto přerušení dostane zpracována se bude lišit v závislosti na operačním systému, ale nakonec data budou předány prostřednictvím operačního systému, dokud nedosáhne volání interop systému (například v Linuxu obslužná rutina přerušení naplánuje spodní polovinu IRQ předat data prostřednictvím operačního systému asynchronně).  Všimněte si, že se to *také* děje asynchronně!  Výsledek je zařazen do fronty, dokud další dostupné vlákno je schopen spustit asynchronní metodu a "rozbalit" výsledek dokončené úlohy.

Během celého tohoto procesu, klíčovým stánek s jídlem je, že **žádné vlákno je vyhrazeno pro spuštění úlohy**.  Přestože práce je spuštěna v některých kontextech (to znamená, že operační systém musí předat data ovladači zařízení a reagovat na přerušení), neexistuje žádné vlákno vyhrazené k *čekání na* data z požadavku, aby se vrátil.  To umožňuje systému zpracovat mnohem větší objem práce, spíše než čekat na dokončení některých vstupně-v.I volání.

Ačkoli výše uvedené se může zdát jako hodně práce, které je třeba udělat, když se měří z hlediska času nástěnných hodin, je to nepatrné ve srovnání s časem, který trvá udělat skutečnou práci i / o. I když vůbec není přesné, potenciální časová osa pro takové volání bude vypadat takto:

0-1————————————————————————————————————————————————–2-3

- Čas strávený `0` z `1` bodů je vše až do asynchronní metoda dává ovládací prvek pro jeho volajícího.
- Čas strávený `1` z `2` bodů do je čas strávený na vstupně-va, bez nákladů na procesor.
- Nakonec čas strávený `2` z `3` bodů do je předávání řízení zpět (a potenciálně hodnotu) asynchronní metody, v tomto okamžiku je provádění znovu.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to znamená pro serverový scénář?

Tento model funguje dobře s úlohou typického scénáře serveru.  Vzhledem k tomu, že neexistují žádná vlákna vyhrazená pro blokování nedokončených úloh, může serverový fond vláken obsluhovat mnohem větší objem webových požadavků.

Vezměme si dva servery: jeden, který spouští asynchronní kód a jeden, který není.  Pro účely tohoto příkladu má každý server k dispozici pouze 5 podprocesů pro požadavky na služby.  Všimněte si, že tato čísla jsou imaginární malé a slouží pouze v demonstrativním kontextu.

Předpokládejme, že oba servery obdrží 6 souběžných požadavků. Každý požadavek provede vstupně-to operaci.  Server *bez* asynchronního kódu musí zařadit do fronty 6. V okamžiku, kdy přijde 20.

Server *s* asynchronním kódem spuštěným na něm stále zařadí `async` `await`do fronty 6.  V době, kdy přijde 20th požadavek, fronta pro příchozí požadavky bude mnohem menší (pokud má vůbec nic v něm) a server se nezpomalí.

I když je to vykonstruovaný příklad, funguje to velmi podobným způsobem v reálném světě.  Ve skutečnosti můžete očekávat, že server bude schopen zpracovat řádově více požadavků pomocí `async` a `await` než kdyby byl věnován vlákna pro každý požadavek, který obdrží.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to znamená pro scénář klienta?

Největším ziskem `async` pro `await` používání a pro klientskou aplikaci je zvýšení odezvy.  I když můžete aplikaci reagovat ručním třením vláken, akt tření vlákna je nákladná `async` `await`operace vzhledem k pouhému použití a .  Zvláště pro něco jako mobilní hra, dopad na vlákno uživatelského rozhraní co nejméně, pokud jde o V/O je rozhodující.

Ještě důležitější je, protože i / V-vázaná práce tráví prakticky žádný čas na CPU, věnuje celý podproces CPU provádět téměř žádnou užitečnou práci by bylo špatné využití zdrojů.

Kromě toho odesílání práce do vlákna uživatelského rozhraní (například aktualizace `async` uživatelského rozhraní) je velmi jednoduché s metodami a nevyžaduje další práci (například volání delegáta bezpečného pro přístup z více vláken).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Hlubší proměna\<úloh a úloh y T> pro operaci vázanou na procesor

Kód vázaný `async` na procesor je trochu jiný `async` než vstupně-výstupní kód.  Vzhledem k tomu, že práce se provádí na procesoru, neexistuje žádný způsob, jak obejít věnování vlákno na výpočtu.  Použití `async` a `await` poskytuje vám čistý způsob, jak komunikovat s podprocesem na pozadí a udržet volající asynchronní metody responzivní.  Všimněte si, že to neposkytuje žádnou ochranu pro sdílená data.  Pokud používáte sdílená data, budete stále muset použít příslušnou strategii synchronizace.

Zde je 10.000 stop pohled na cpu-vázané asynchronní volání:

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

`CalculateResult()`provede ve vlákně, na které byl volán.  Při volání `Task.Run`, zařadí do fronty nákladné `DoExpensiveCalculation()`operace vázané na procesor `Task<int>` , ve fondu vláken a obdrží popisovač.  `DoExpensiveCalculation()`je nakonec spuštěn a současně na další dostupné vlákno, pravděpodobně na jiném jádru procesoru.  Je možné provádět souběžnou práci, zatímco `DoExpensiveCalculation()` je zaneprázdněn na jiném `CalculateResult()` vlákně, protože vlákno, které volal je stále provádí.

Jakmile `await` je zjištěna, `CalculateResult()` provádění je výnosné jeho volajícího, což umožňuje další `DoExpensiveCalculation()` práci, která má být provedena s aktuální vlákno, zatímco je chrlit výsledek.  Po dokončení je výsledek zařazen do fronty, aby byl spuštěn v hlavním vlákně.  Nakonec se hlavní vlákno vrátí k `CalculateResult()`provádění , v tomto okamžiku `DoExpensiveCalculation()`bude mít výsledek .

### <a name="why-does-async-help-here"></a>Proč zde pomáhá async?

`async`a `await` jsou osvědčeným postupem pro správu práce vázané na procesor, když potřebujete odezvu. Existuje více vzorů pro použití asynchronní s prací vázanou na procesor. Je důležité si uvědomit, že je malé náklady na používání asynchronní a není doporučeno pro těsné smyčky.  Je na vás určit, jak psát kód kolem této nové funkce.

## <a name="see-also"></a>Viz také

- [Asynchronní programování v C #](../csharp/async.md)
- [Asynchronní programování s asynchronní a čekat (C#)](../csharp/programming-guide/concepts/async/index.md)
- [Asynchronní programování ve F #](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Asynchronní programování s asynchronní a čeká (Visual Basic)](../visual-basic/programming-guide/concepts/async/index.md)
