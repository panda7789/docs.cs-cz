---
title: 'Asynchronní programování v C #'
description: Přehled podpory jazyka C# pro asynchronní programování pomocí async, await, Task a Task<T>
ms.date: 03/18/2019
ms.openlocfilehash: 4cbbff0f2c48f0ec2f8befa234ea5023465a1c5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169906"
---
# <a name="asynchronous-programming-with-async-and-await"></a>Asynchronní programování pomocí modifikátoru Async a operátoru Await

Úloha asynchronní programovací model (TAP) poskytuje abstrakce přes asynchronní kód. Píšete kód jako posloupnost příkazů, stejně jako vždy. Tento kód si můžete přečíst, jako by každý příkaz dokončen před dalším zahájením. Kompilátor provádí počet transformací, protože některé z těchto <xref:System.Threading.Tasks.Task> příkazů může začít pracovat a vrátit, který představuje probíhající práci.

To je cílem této syntaxe: povolit kód, který čte jako posloupnost příkazů, ale provádí v mnohem složitější pořadí na základě přidělení externích prostředků a po dokončení úkolů. Je to analogické, jak lidé dávají pokyny pro procesy, které zahrnují asynchronní úkoly. V tomto článku použijete příklad pokynů pro provedení snídaně, `async` abyste `await` zjistili, jak klíčová slova a usnadňují důvod týkající se kódu, který obsahuje řadu asynchronních pokynů. Napsali byste pokyny něco jako následující seznam, abyste vysvětlili, jak udělat snídani:

1. Nalijte šálek kávy.
1. Zahřejte pánev, pak smažte dvě vejce.
1. Smažte tři plátky slaniny.
1. Opékejte dva kusy chleba.
1. Přidejte máslo a džem do toastu.
1. Nalijte sklenici pomerančového džusu.

Pokud máte zkušenosti s vařením, provedete tyto pokyny **asynchronně**. Začal bys ohřívat pánev na vajíčka a pak začal slaninu. Dal bys chleba do toustovače a pak začal s vejci. V každém kroku procesu byste zahájili úkol a pak obrátili svou pozornost na úkoly, které jsou připraveny pro vaši pozornost.

Vaření snídaně je dobrým příkladem asynchronní práce, která není paralelní. Všechny tyto úkoly zvládne jedna osoba (nebo vlákno). Pokračování snídaně analogie, jedna osoba může snídani asynchronně spuštěním další úkol před prvním dokončením. Vaření postupuje, zda se na to někdo dívá. Jakmile začnete zahřívat pánev na vejce, můžete začít smažit slaninu. Jakmile začne slanina, můžete dát chléb do toustovače.

Pro paralelní algoritmus budete potřebovat více kuchařů (nebo vláken). Jeden by udělal vejce, jednu slaninu a tak dále. Každý z nich by se zaměřil jen na jeden úkol. Každý kuchař (nebo vlákno) by být blokovány synchronně čeká na slaninu, aby byl připraven k flip, nebo přípitek na pop.

Nyní zvažte stejné pokyny napsané jako příkazy Jazyka C#:

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

Počítače neinterpretují tyto pokyny stejným způsobem jako lidé. Počítač bude blokovat na každém příkazu, dokud práce je dokončena před přechodem na další příkaz. To vytváří neuspokojivou snídani. Pozdější úkoly nebudou zahájeny, dokud nebudou dokončeny předchozí úkoly. Trvalo by mnohem déle, než by se snídaně vytvořila, a některé položky by se před podáváním ochladila.

Pokud chcete, aby počítač provedl výše uvedené pokyny asynchronně, musíte napsat asynchronní kód.

Tyto obavy jsou důležité pro programy, které píšete dnes. Při psaní klientských programů chcete, aby uživatelské rozhraní reagovalo na vstup uživatele. Aplikace by neměla způsobit, že by telefon při stahování dat z webu vypadal zmrazený. Při psaní serverových programů nechcete blokovat vlákna. Tato vlákna mohou obsluhují jiné požadavky. Použití synchronního kódu při existenci asynchronních alternativ poškozuje vaši schopnost škálovat levněji. Platíte za ty zablokované vlákna.

Úspěšné moderní aplikace vyžadují asynchronní kód. Bez jazykové podpory, psaní asynchronní kód vyžaduje zpětná volání, události dokončení nebo jiné prostředky, které zakrývaly původní záměr kódu. Výhodou synchronního kódu je, že je snadno pochopitelný. Akce krok za krokem usnadňují skenování a pochopení. Tradiční asynchronní modely nuceni zaměřit se na asynchronní povahu kódu, nikoli na základní akce kódu.

## <a name="dont-block-await-instead"></a>Neblokujte, čekejte místo toho

Předchozí kód ukazuje chybný postup: vytvoření synchronního kódu k provádění asynchronních operací. Jak je napsáno, tento kód blokuje vlákno provádění jej z provádění jakékoli jiné práce. Nebude přerušena, zatímco některý z úkolů probíhá. Bylo by to, jako bys zíral na toustovač po chleba. Ignoroval bys každého, kdo by s tebou mluvil, dokud by se neobjevil přípitek.

Začněme aktualizací tohoto kódu tak, aby vlákno neblokovalo, když jsou spuštěny úlohy. Klíčové `await` slovo poskytuje neblokující způsob spuštění úlohy a po dokončení této úlohy pokračujte v provádění. Jednoduchá asynchronní verze kódu make a breakfast by vypadala jako následující úryvek:

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

Tento kód neblokuje, když vejce nebo slanina jsou vaření. Tento kód však nespustí žádné další úkoly. Pořád bys dával přípitek do toustovače a zíral na něj, dokud nevyskočil. Ale aspoň bys reagoval na každého, kdo by chtěl tvou pozornost. V restauraci, kde je umístěno více objednávek, by kuchař mohl začít další snídani, zatímco první je vaření.

Nyní vlákno pracující na snídani není blokováno, zatímco čeká na jakýkoli zahájený úkol, který ještě nebyl dokončen. Pro některé aplikace je tato změna vše, co je potřeba. Gui aplikace stále reaguje na uživatele právě s touto změnou. Však pro tento scénář chcete další. Nechcete, aby každý z úloh komponenty, které mají být provedeny postupně. Je lepší spustit každý z úloh komponenty před čekáním na dokončení předchozího úkolu.

## <a name="start-tasks-concurrently"></a>Souběžné zahájení úloh

V mnoha scénářích chcete okamžitě spustit několik nezávislých úloh. Po dokončení každého úkolu pak můžete pokračovat v další práci, která je připravena. V analogie snídaně, to je, jak se dostanete snídani udělat rychleji. Také dostanete všechno udělat blízko ke stejnému času. Dostaneš teplou snídani.

A <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> související typy jsou třídy, které můžete použít k důvodu o probíhajících úkolech. To vám umožní napsat kód, který se více podobá způsobu, jakým byste skutečně vytvořit snídani. Začal bys vařit vejce, slaninu a toast ve stejnou dobu. Jako každý vyžaduje akci, měli byste obrátit svou pozornost k tomuto úkolu, postarat se o další akci, pak čekají na něco jiného, co vyžaduje vaši pozornost.

Můžete zahájit úkol a <xref:System.Threading.Tasks.Task> podržte objekt, který představuje práci. Budete `await` každý úkol před prací s jeho výsledkem.

Pojďme udělat tyto změny v kódu snídaně. Prvním krokem je uložení úkolů pro operace při jejich spuštění, nikoli jejich čekání:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggsTask = FryEggs(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Task<Bacon> baconTask = FryBacon(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Console.WriteLine("Breakfast is ready!");
```

Dále můžete přesunout `await` prohlášení o slanině a vejcích na konec metody, než servírujete snídani:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggsTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

Předchozí kód funguje lépe. Spuštění všech asynchronních úloh najednou. Na každý úkol čekáte pouze v případě, že potřebujete výsledky. Předchozí kód může být podobný kódu ve webové aplikaci, která provádí požadavky různých mikroslužeb, pak kombinuje výsledky do jedné stránky. Budete dělat všechny požadavky okamžitě, `await` pak všechny tyto úkoly a tvoří webové stránky.

## <a name="composition-with-tasks"></a>Složení s úkoly

 Máte vše připravené k snídani ve stejnou dobu kromě přípitku. Tvorba toast je složení asynchronní operace (opékání chleba), a synchronní operace (přidání másla a džemu). Aktualizace tohoto kódu ilustruje důležitý koncept:

> [!IMPORTANT]
> Složení asynchronní operace následované synchronní prací je asynchronní operace. Uvedeno jiným způsobem, pokud je jakákoli část operace asynchronní, je celá operace asynchronní.

Předchozí kód ukázal, že můžete <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> použít nebo objekty pro uložení spuštěných úloh. Každý `await` úkol před použitím jeho výsledek. Dalším krokem je vytvoření metod, které představují kombinaci jiné práce. Před podáváním snídaně, chcete počkat na úkol, který představuje opékání chleba před přidáním másla a džemu. Tuto práci můžete reprezentovat pomocí následujícího kódu:

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Předchozí metoda má `async` modifikátor ve svém podpisu. To signalizuje kompilátoru, `await` že tato metoda obsahuje příkaz; obsahuje asynchronní operace. Tato metoda představuje úkol, který opéká chléb, pak přidá máslo a džem. Tato metoda <xref:System.Threading.Tasks.Task%601> vrátí, který představuje složení těchto tří operací. Hlavní blok kódu se nyní stane:

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

Předchozí změna ilustrovala důležitou techniku pro práci s asynchronním kódem. Úlohy můžete vytvořit oddělením operací do nové metody, která vrací úkol. Můžete si vybrat, kdy na tento úkol čekat. Další úkoly můžete spustit současně.

## <a name="await-tasks-efficiently"></a>Vyčkejte efektivně na úkoly

Řada `await` příkazů na konci předchozího kódu lze zlepšit pomocí metod `Task` třídy. Jedním z těchto <xref:System.Threading.Tasks.Task.WhenAll%2A>api je <xref:System.Threading.Tasks.Task> , který vrátí, který dokončí po dokončení všech úkolů v seznamu argumentů, jak je znázorněno v následujícím kódu:

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Další možností je <xref:System.Threading.Tasks.Task.WhenAny%2A>použití , `Task<Task>` který vrátí, který dokončí po dokončení některého z jeho argumentů. Můžete čekat na vrácený úkol s vědomím, že již byla dokončena. Následující kód ukazuje, jak <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete použít čekat na první úkol k dokončení a potom zpracovat jeho výsledek. Po zpracování výsledku dokončeného úkolu odeberete tento dokončený `WhenAny`úkol ze seznamu úkolů předaných aplikaci .

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Po všech těchto změnách `Main` vypadá konečná verze aplikace následující kód:

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

Tento konečný kód je asynchronní. To přesněji odráží, jak by člověk vařit snídani. Porovnejte předchozí kód s první ukázkou kódu v tomto článku. Základní akce jsou stále jasné ze čtení kódu. Tento kód si můžete přečíst stejným způsobem, jakým jste si přečetli tyto pokyny pro snídani na začátku tohoto článku. Jazykové funkce `async` pro `await` a poskytují překlad každý člověk dělá následovat tyto písemné pokyny: spuštění úkolů, jak můžete a neblokujte čekání na dokončení úkolů.
