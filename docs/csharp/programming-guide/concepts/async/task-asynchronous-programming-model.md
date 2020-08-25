---
title: Úloha asynchronního programování (klepnutím) s modifikátorem Async a operátoru Await (C#)
description: Naučte se, kdy a jak používat asynchronní programování založené na úlohách, zjednodušený přístup k asynchronnímu programování v jazyce C#.
ms.date: 08/19/2020
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 5e85b99025b31e205c66468d4bd886701cbaea17
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812082"
---
# <a name="task-asynchronous-programming-model"></a>Model asynchronního programování úloh

Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.

[Jazyk C# 5](../../../whats-new/csharp-version-history.md#c-version-50) představil zjednodušený přístup, asynchronní programování, které využívá asynchronní podporu v .NET Framework 4,5 a vyšších, .NET Core a prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.

Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a> Asynchronní funkce vylepšuje rychlost odezvy.

Asynchronii je nezbytné pro aktivity, které jsou potenciálně blokovány, například webový přístup. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková aktivita zablokovaná v synchronním procesu, musí počkat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.

Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z rozhraní .NET a prostředí Windows Runtime obsahují metody, které podporují asynchronní programování.

| Oblast aplikace | Typy .NET s asynchronními metodami | Typy prostředí Windows Runtime s asynchronními metodami |
|--|--|--|
| Webový přístup | <xref:System.Net.Http.HttpClient> | <xref:Windows.Web.Http.HttpClient?displayProperty=nameWithType> <br> <xref:Windows.Web.Syndication.SyndicationClient> |
| Práce se soubory | <xref:System.Text.Json.JsonSerializer> <br> <xref:System.IO.StreamReader> <br> <xref:System.IO.StreamWriter> <br> <xref:System.Xml.XmlReader> <br> <xref:System.Xml.XmlWriter> | <xref:Windows.Storage.StorageFile> |
| Práce s obrázky |  | <xref:Windows.Media.Capture.MediaCapture> <br> <xref:Windows.Graphics.Imaging.BitmapEncoder> <br> <xref:Windows.Graphics.Imaging.BitmapDecoder> |
| Programování WCF | [Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md) |  |

Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.

Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.

Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.

## <a name="async-methods-are-easy-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a> Asynchronní metody se snadno zapisují

Klíčová slova [Async](../../../language-reference/keywords/async.md) a [await](../../../language-reference/operators/await.md) v jazyce C# představují srdce asynchronního programování. Pomocí těchto dvou klíčových slov můžete použít prostředky v .NET Framework, .NET Core nebo prostředí Windows Runtime k vytvoření asynchronní metody téměř stejně snadno, jako vytváříte synchronní metodu. Asynchronní metody, které definujete pomocí `async` klíčového slova, jsou označovány jako *asynchronní metody*.

Následující příklad ukazuje asynchronní metodu. Téměř vše v kódu by mělo vypadat dobře.

Můžete najít kompletní příklad Windows Presentation Foundation (WPF), který je k dispozici ke stažení z [asynchronního programování s modifikátorem Async a await v jazyce C#](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs).

:::code language="csharp" source="snippets/access-web/Program.cs" id="ControlFlow":::

V předchozím příkladu se můžete seznámit s několika postupy. Začněte s podpisem metody. Obsahuje `async` modifikátor. Návratový typ je `Task<int>` (další možnosti najdete v části "návratové typy"). Název metody končí `Async` . V těle metody `GetStringAsync` vrátí `Task<string>` . To znamená, že po `await` obdržení úlohy získáte `string` ( `contents` ). Před čekáním na úlohu můžete provádět práci, která nespoléhá na `string` z `GetStringAsync` .

Věnujte velkou pozornost `await` operátoru. Pozastavuje se `GetUrlContentLengthAsync` :

- `GetUrlContentLengthAsync` nedá se pokračovat `getStringTask` , dokud se nedokončí.
- Mezitím se ovládací prvek vrátí volajícímu `GetUrlContentLengthAsync` .
- Po dokončení se ovládací prvek obnoví `getStringTask` .
- `await`Operátor následně načte `string` výsledek z `getStringTask` .

Příkaz return určuje celočíselný výsledek. Všechny metody, které čekají `GetUrlContentLengthAsync` na načtení hodnoty Length.

Pokud nemá `GetUrlContentLengthAsync` žádnou práci, kterou může provést mezi voláním `GetStringAsync` a čekáním na jeho dokončení, můžete zjednodušit kód voláním a čekáním v následujícím jediném příkazu.

```csharp
string contents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Následující charakteristiky shrnují, co dělá předchozí příklad asynchronní metodou:

- Signatura metody obsahuje `async` modifikátor.
- Název asynchronní metody končí podle konvence příponou „Async“.
- Návratový typ je jeden z následujících typů:

  - <xref:System.Threading.Tasks.Task%601> Pokud vaše metoda má návratový příkaz, ve kterém je operand typu `TResult` .
  - <xref:System.Threading.Tasks.Task> Pokud vaše metoda nemá návratový příkaz nebo má návratový příkaz bez operandu.
  - `void` Pokud píšete asynchronní obslužnou rutinu události.
  - Jakýkoli jiný typ, který má `GetAwaiter` metodu (počínaje jazykem C# 7,0).

  Další informace naleznete v části [návratové typy a parametry](#BKMK_ReturnTypesandParameters) .

- Metoda obvykle zahrnuje nejméně jeden `await` výraz, který označuje bod, kde metoda nemůže pokračovat, dokud není dokončena očekávaná asynchronní operace. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.

V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.

Další informace o asynchronii v předchozích verzích .NET Framework naleznete v tématu [TPL a tradiční .NET Framework asynchronní programování](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co se stane v asynchronní metodě

Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem:

:::image type="content" source="media/task-asynchronous-programming-model/navigation-trace-async-program.png" alt-text="Trasování navigace toku asynchronního řízení" lightbox="media/task-asynchronous-programming-model/navigation-trace-async-program.png":::

Čísla v diagramu odpovídají následujícím krokům, které jsou iniciovány, když volající metoda volá asynchronní metodu.

1. Volající metoda volá a očekává `GetUrlContentLengthAsync` asynchronní metodu.

1. `GetUrlContentLengthAsync` vytvoří <xref:System.Net.Http.HttpClient> instanci a zavolá <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronní metodu pro stažení obsahu webu jako řetězce.

1. Dojde k tomu `GetStringAsync` , že se něco pozastaví. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Aby nedocházelo k blokování prostředků, `GetStringAsync` poskytne řízení volajícímu, `GetUrlContentLengthAsync` .

     `GetStringAsync` Vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je řetězec, a `GetUrlContentLengthAsync` přiřadí úkol `getStringTask` proměnné. Úkol představuje pokračující proces pro volání `GetStringAsync` s závazkem vytvořit skutečnou řetězcovou hodnotu po dokončení práce.

1. Vzhledem k tomu `getStringTask` , že se ještě nečekalo, `GetUrlContentLengthAsync` může pokračovat v jiné práci, která nezávisí na konečném výsledku z `GetStringAsync` . Tato práce je reprezentována voláním synchronní metody `DoIndependentWork` .

1. `DoIndependentWork` je synchronní metoda, která provede svou práci a vrátí jejímu volajícímu.

1. `GetUrlContentLengthAsync` nemá dostatek práce, kterou může dělat bez výsledku z `getStringTask` . `GetUrlContentLengthAsync` Dále chce vypočítat a vrátit délku staženého řetězce, ale metoda nemůže tuto hodnotu vypočítat, dokud metoda nemá řetězec.

    Proto `GetUrlContentLengthAsync` pomocí operátoru await pozastaví svůj průběh a vrátí řízení metodě, která je volána `GetUrlContentLengthAsync` . `GetUrlContentLengthAsync` Vrátí hodnotu `Task<int>` volajícímu. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.

    > [!NOTE]
    > Pokud `GetStringAsync` (a tedy `getStringTask` ) se dokončí před tím `GetUrlContentLengthAsync` , než očekává, ovládací prvek zůstane v `GetUrlContentLengthAsync` . Náklady na pozastavení a návrat do `GetUrlContentLengthAsync` by byly nevyužité, pokud se pojmenovaný asynchronní proces `getStringTask` již dokončil a `GetUrlContentLengthAsync` nemusí čekat na konečný výsledek.

    Uvnitř metody volání pokračuje vzor zpracování. Volající může provést další práci, která nezávisí na výsledku před čekáním na `GetUrlContentLengthAsync` výsledek, nebo volající může očekávat okamžitě. Volající metoda čeká na `GetUrlContentLengthAsync` a `GetUrlContentLengthAsync` čeká na `GetStringAsync` .

1. `GetStringAsync` dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácen voláním `GetStringAsync` způsobem, který by mohl očekávat. (Nezapomeňte, že metoda již vrátila úlohu v kroku 3.) Místo toho je výsledek řetězce uložen v úkolu, který představuje dokončení metody `getStringTask` . Operátor await načte výsledek z `getStringTask` . Příkaz přiřazení přiřadí načtený výsledek do `contents` .

1. Když `GetUrlContentLengthAsync` má výsledek řetězce, metoda může vypočítat délku řetězce. Pak `GetUrlContentLengthAsync` je práce také dokončena a může pokračovat obslužná rutina čekající události. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.
Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a> Asynchronní metody rozhraní API

Možná vás zajímá, kde najít metody, jako je například `GetStringAsync` Podpora asynchronního programování. .NET Framework 4,5 nebo vyšší a .NET Core obsahují mnoho členů, kteří pracují s `async` a `await` . Můžete je rozpoznat pomocí přípony "Async", která je připojena k názvu člena a podle jejich návratového typu <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> . Například `System.IO.Stream` Třída obsahuje metody, jako <xref:System.IO.Stream.CopyToAsync%2A> , a <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A> vedle synchronních metod <xref:System.IO.Stream.CopyTo%2A> , <xref:System.IO.Stream.Read%2A> a <xref:System.IO.Stream.Write%2A> .

Prostředí Windows Runtime taky obsahuje spoustu metod, které můžete používat s `async` `await` aplikacemi a v aplikacích pro Windows. Další informace naleznete v tématech [dělení vlákna a asynchronní programování](/windows/uwp/threading-async/) pro vývoj UWP a [asynchronní programování (aplikace pro Windows Store)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) a [rychlý Start: volání asynchronních rozhraní api v jazyce C# nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) , pokud používáte starší verze prostředí Windows Runtime.

## <a name="threads"></a><a name="BKMK_Threads"></a> Vláken

Asynchronní metody mají být neblokující operace. `await`Výraz v asynchronní metodě neblokuje aktuální vlákno, zatímco je spuštěn očekávaný úkol. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.

`async` `await` Klíčová slova a nezpůsobí vytvoření dalších vláken. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pro přesun práce vázané na procesor do vlákna na pozadí, ale vlákno na pozadí nepomůže s procesem, který právě čeká na zpřístupnění výsledků.

Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je lepší než <xref:System.ComponentModel.BackgroundWorker> třída pro operace vázané na vstup/výstup, protože kód je jednodušší a nemusíte se chránit před konflikty časování. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodou je asynchronní programování lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor, protože asynchronní programování odděluje koordinační údaje o spuštění kódu z práce, která se `Task.Run` přenáší do fondu vláken.

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a> Async a await

Pokud určíte, že metoda je asynchronní metodou pomocí modifikátoru [Async](../../../language-reference/keywords/async.md) , povolíte následující dvě možnosti.

- Označená asynchronní metoda může použít [operátor await](../../../language-reference/operators/await.md) k určení bodů zavěšení. `await`Operátor instruuje kompilátor, že asynchronní metoda nemůže pokračovat za tento bod, dokud není dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.

     Pozastavení asynchronní metody ve `await` výrazu nepředstavuje příkaz exit z metody a `finally` bloky nejsou spuštěny.

- Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.

Asynchronní metoda obvykle obsahuje jeden nebo více výskytů `await` operátoru, ale absence `await` výrazů nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá `await` operátor k označení bodu pozastavení, metoda se spustí jako synchronní metoda bez ohledu na `async` modifikátor. Kompilátor u takových metod zahlásí upozornění.

`async` a `await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a> Návratové typy a parametry

Asynchronní metoda obvykle vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> . V rámci asynchronní metody `await` je operátor použit pro úkol, který je vrácen z volání jiné asynchronní metody.

Zadáte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud metoda obsahuje [`return`](../../../language-reference/keywords/return.md) příkaz, který určuje operand typu `TResult` .

Použijete <xref:System.Threading.Tasks.Task>  jako návratový typ, pokud metoda nemá žádný návratový příkaz nebo má návratový příkaz, který nevrací operand.

Počínaje jazykem C# 7,0 můžete také zadat jakýkoli jiný návratový typ za předpokladu, že typ obsahuje `GetAwaiter` metodu. <xref:System.Threading.Tasks.ValueTask%601> je příkladem takového typu. Je k dispozici v balíčku NuGet [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) .

Následující příklad ukazuje, jak deklarovat a volat metodu, která vrací <xref:System.Threading.Tasks.Task%601> nebo a <xref:System.Threading.Tasks.Task> :

```csharp
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);

    return hours;
}


Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// Single line
// int intResult = await GetTaskOfTResultAsync();

async Task GetTaskAsync()
{
    await Task.Delay(0);
    // No return statement needed
}

Task returnedTask = GetTaskAsync();
await returnedTask;
// Single line
await GetTaskAsync();
```

Každá vrácená úloha představuje probíhající práci. Úloha zapouzdřuje informace o stavu asynchronního procesu a posléze buď konečný výsledek z procesu, nebo výjimku, kterou proces vyvolá v případě neúspěchu.

Asynchronní metoda může mít také `void` návratový typ. Tento návratový typ slouží primárně k definování obslužných rutin událostí, kde `void` je požadován návratový typ. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.

Asynchronní metoda, která má `void` návratový typ, nemůže být očekávána a volající metody vracející typ void nemůže zachytit žádné výjimky, které metoda vyvolá.

Asynchronní metoda [nemůže deklarovat parametry](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) nebo [out](../../../language-reference/keywords/out-parameter-modifier.md) , ale metoda může volat metody, které mají tyto parametry. Podobně asynchronní metoda nemůže vrátit hodnotu odkazem, přestože může volat metody s návratovými hodnotami ref.

Další informace a příklady naleznete v tématu [Async Return Types (C#)](async-return-types.md). Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v tématu [try-catch](../../../language-reference/keywords/try-catch.md).

Asynchronní rozhraní API v prostředí Windows Runtime programování mají jeden z následujících návratových typů, které jsou podobné úlohám:

- <xref:Windows.Foundation.IAsyncOperation%601>, který odpovídá <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, který odpovídá <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a> Konvence pojmenování

Podle konvence metody, které vracejí běžně čekajíelné typy (například, `Task` `Task<T>` , `ValueTask` ,), `ValueTask<T>` by měly mít názvy končící na "Async". Metody, které spouštějí asynchronní operaci, ale nevracejí očekávaný typ, by neměly mít názvy, které končí na "Async", ale mohou začínat na "begin", "Start" nebo některé jiné operace, které tuto metodu navrhují, nevrátí ani nevyvolávají výsledek operace.

Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, jako je například `OnButtonClick` .

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a> Související témata a ukázky (Visual Studio)

| Nadpis | Popis | Ukázka |
|--|--|--|
| [Jak zajistit paralelní více webových požadavků pomocí modifikátoru Async a operátoru Await (C#)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) | Ukazuje, jak spustit několik úloh současně. | [Asynchronní vzorek: paralelní provádění více webových požadavků](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e) |
| [Asynchronní návratové typy (C#)](async-return-types.md) | Znázorňuje typy, které mohou vracet asynchronní metody, a vysvětluje, kdy je každý typ vhodný. |  |
| Zruší úkoly s tokenem zrušení jako mechanismus signalizace. | Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br><br> - [Zrušení seznamu úkolů (C#)](cancel-an-async-task-or-a-list-of-tasks.md)<br>- [Zrušení úloh po určitém časovém intervalu (C#)](cancel-async-tasks-after-a-period-of-time.md)<br>- [Zpracovat asynchronní úlohu po dokončení (C#)](start-multiple-async-tasks-and-process-them-as-they-complete.md) |  |
| [Použití Async pro přístup k souborům (C#)](using-async-for-file-access.md) | Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům. |  |
| [Asynchronní vzor založený na úlohách (klepnutím)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Popisuje asynchronní vzorek, je vzor založen na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> typech a. |  |
| [Asynchronní videa na Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en) | Poskytuje odkazy na různá videa o asynchronním programování. |  |

## <a name="see-also"></a>Viz také

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Asynchronní programování](../../../async.md)
- [Asynchronní přehled](../../../../standard/async.md)
