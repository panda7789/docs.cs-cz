---
title: 'Asynchronní programování v jazyce C #'
description: Přehled podpory jazyka C# pro asynchronní programování pomocí asynchronního, operátoru await, úlohy a úlohy<T>
ms.date: 03/18/2019
ms.openlocfilehash: 4bf00d5c77138dfa2d527a262a6cd54a72a688f5
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761847"
---
# <a name="asynchronous-programming-with-async-and-await"></a>Asynchronní programování pomocí modifikátoru Async a operátoru Await

Asynchronní programovací model úlohy (klepněte na) poskytuje abstrakci pro asynchronní kód. Kód můžete napsat jako posloupnost příkazů, stejně jako vždycky. Tento kód si můžete přečíst, jako by byl každý příkaz dokončen před dalším začátkem. Kompilátor provádí řadu transformací, protože některé z těchto příkazů mohou začít pracovat a vracet <xref:System.Threading.Tasks.Task> , který představuje probíhající práci.

To je cílem této syntaxe: umožňuje povolit kód, který se čte jako sekvence příkazů, ale provádí se v mnohem složitějším pořadí založeném na externím přidělení prostředků a po dokončení úkolů. Podobá se tomu, jak lidé dávají pokyny pro procesy, které zahrnují asynchronní úlohy. V tomto článku použijete příklad pokynů pro vytvoření snídani k tomu, abyste viděli, jak `async` `await` klíčová slova a usnadňují odůvodnění kódu, který obsahuje řadu asynchronních instrukcí. Měli byste napsat pokyny, jako je v následujícím seznamu, abyste se vysvětlují, jak vytvořit snídani:

1. Nalijte konvičku z kávy.
1. Zastavte pánev a pak dvě vejce v SRJ.
1. SRJ tři řezy slanina
1. Informační zprávy jsou dvě části chleba.
1. Přidejte máslo a zaseknutí do informačních zpráv.
1. Nalijte sklo oranžové šťávy.

Pokud máte zkušenosti s vařením, spusťte tyto pokyny **asynchronně**. Začnete zahříváním pánev pro vejce a pak zahájíte slanina. Vložili jste chléb do informačního pole a pak vejce začali. V každém kroku procesu byste úlohu spustili a pak jste si měli pozor na úkoly, které jsou připravené na vaši pozornost.

Vaření snídaně je dobrým příkladem asynchronní práce, která není paralelní. Všechny tyto úlohy může zvládnout jedna osoba (nebo vlákno). Pokračováním v analogovém režimu může jedna osoba provést asynchronní zpracování asynchronně spuštěním další úlohy před prvním dokončením. Vaření bude postupovat bez ohledu na to, jestli ho někdo sleduje. Jakmile začnete zahříváním pánev pro vejce, můžete začít Frying slanina. Po spuštění slanina můžete přidat chléb do informačního části.

Pro paralelní algoritmus budete potřebovat více cooků (neboli vláken). To by mělo být vejce, jedna slanina a tak dále. Každé z nich by se zaměřilo jenom na jeden úkol. Každé Cookovy (nebo vlákno) se zablokuje synchronně, čeká se, až bude slanina připravený k převrácení, nebo informační zprávy, které se mají blokovat.

Nyní zvažte stejné pokyny, které jsou zapsány jako příkazy jazyka C#:

[!code-csharp[SynchronousBreakfast](./snippets/index/AsyncBreakfast-starter/Program.cs#Main)]

Počítače neinterpretují tyto pokyny stejným způsobem jako lidé. Počítač bude zablokovat každý příkaz, dokud nebude dokončeno dokončení práce, než přejde k dalšímu příkazu. Tím se vytvoří nevyhovující snídaně. Pozdější úkoly by nemusely být spuštěny, dokud se předchozí úkoly nedokončí. Vytvoření snídaně by trvat mnohem delší dobu a některé položky by byly před odesláním nedoručeny.

Pokud chcete, aby počítač prováděl výše uvedené pokyny asynchronně, je nutné napsat asynchronní kód.

Tyto aspekty jsou důležité pro programy, které dnes napíšete. Při psaní klientských programů budete chtít, aby uživatelské rozhraní reagovalo na vstup uživatele. Vaše aplikace by se neměla po stažení dat z webu jevit jako zmrazená. Když píšete serverové programy, nechcete, aby byla vlákna blokovaná. Tato vlákna mohou obsluhovat jiné požadavky. Použití synchronního kódu v případě, že existují asynchronní alternativy, neuškodí schopnost horizontálního navýšení kapacity snížit kapacitu. Platíte za tato blokovaná vlákna.

Úspěšné moderní aplikace vyžadují asynchronní kód. Bez podpory jazyků, psaní zpětných volání vyžadovaných asynchronním kódem, události dokončení nebo jiné způsob, který zakrývá původní záměr kódu. Výhodou synchronního kódu je, že je snadné ho pochopit. Podrobné akce usnadňují kontrolu a pochopení. Tradiční asynchronní modely vám pomohly soustředit se na asynchronní povahu kódu, nikoli na základní akce kódu.

## <a name="dont-block-await-instead"></a>Neblokovat, místo toho očekávat

Předchozí kód demonstruje špatný postup: sestavení synchronního kódu pro provádění asynchronních operací. Jak je zapsáno, tento kód zablokuje vlákno, které ho spouští, od jakékoli jiné práce. Nedojde k přerušení, dokud nebudou dokončeny žádné úlohy. Může to být tak, jak jste v informačním části postari po vložení chleba do. Na vás bude nikdo mluvit, dokud nebudou informační zprávy odebrány.

Pojďme začít aktualizací tohoto kódu, aby vlákno neblokovalo úlohy spuštěné. `await`Klíčové slovo poskytuje neblokující způsob spuštění úlohy a pak pokračuje v provádění po dokončení této úlohy. Jednoduchá asynchronní verze kódu pro vytvoření snídani by vypadala jako následující fragment kódu:

[!code-csharp[SimpleAsyncBreakfast](./snippets/index/AsyncBreakfast-V2/Program.cs#Main)]

Tento kód se neblokuje, pokud jsou vejce nebo slanina vaření. Tento kód v takovém případě nespustí žádné další úlohy. Informační zprávy do informačního oddělení byste pořád umístili do informačních zpráv a tam, kde se neobjeví. Ale aspoň, budete reagovat na kohokoli, kdo si přeje vaši pozornost. V rámci restaurace, kde je umístěno více objednávek, může Cook Cook začít jinou snídani, zatímco první je vaření.

Vlákno, které pracuje na snídani, není nyní blokované při čekání na spuštěnou úlohu, která ještě nebyla dokončena. U některých aplikací je tato změna potřebná. Aplikace grafického uživatelského rozhraní pořád reaguje na uživatele pouze touto změnou. V tomto scénáři ale potřebujete víc. Nechcete, aby se jednotlivé úlohy komponenty prováděly sekvenčně. Před čekáním na dokončení předchozího úkolu je lepší spustit každou z těchto úloh.

## <a name="start-tasks-concurrently"></a>Spustit souběžně úlohy

V mnoha scénářích chcete okamžitě spustit několik nezávislých úloh. Po dokončení jednotlivých úkolů můžete pokračovat v práci, která je připravená. V analogické pracovní snídaně to je způsob, jak rychle získat snídani. Všechno se ale také dokončí blízko stejnou dobu. Získáte horkou snídani.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Související typy jsou třídy, které můžete použít k odůvodnění úloh, které probíhají. To vám umožňuje psát kód, který se bude lépe podobat způsobu, jakým jste ve skutečnosti vytvořili snídani. Začít vaření na vejce, slanina a informační zprávy ve stejnou dobu. Vzhledem k tomu, že každá z nich vyžaduje akci, byste měli věnovat pozornost této úloze, pořídit další akci a pak očekávat něco jiného, co vyžaduje vaši pozornost.

Spustíte úlohu a podržíte ji pro <xref:System.Threading.Tasks.Task> objekt, který představuje práci. Než budete `await` s jeho výsledkem pracovat, budete mít každý úkol.

Pojďme udělat tyto změny kódu snídani. Prvním krokem je ukládat úlohy pro operace, když se spouštějí, a nečekají na ně:

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

Dále můžete přesunout `await` příkazy pro slanina a vejce na konec metody před obsluhou snídaně:

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

Předchozí kód funguje lépe. Současně spustíte všechny asynchronní úlohy. Každou úlohu můžete očekávat pouze v případě, že potřebujete výsledky. Předchozí kód může být podobný kódu ve webové aplikaci, který vytváří požadavky na různé mikroslužby, a pak kombinuje výsledky do jediné stránky. Všechny požadavky okamžitě provedete `await` a pak všechny tyto úlohy a vytvoříte webovou stránku.

## <a name="composition-with-tasks"></a>Složení s úkoly

 Máte všechno připravené k snídani ve stejnou dobu s výjimkou informačních zpráv. Zpřístupnění informačních zpráv je složením asynchronní operace (informační zpráva o příchodu) a synchronní operace (přidání másla a zaseknutí). Aktualizace tohoto kódu ilustruje důležitý koncept:

> [!IMPORTANT]
> Složení asynchronní operace následované synchronní prací je asynchronní operace. Pokud je libovolná část operace asynchronní, je celá operace asynchronní, pokud je uvedena jinak.

Předchozí kód vám ukázal, že můžete použít <xref:System.Threading.Tasks.Task> objekty nebo <xref:System.Threading.Tasks.Task%601> pro udržení spuštěných úloh. `await`Každý úkol před použitím jeho výsledku. Dalším krokem je vytvoření metod, které reprezentují kombinaci jiné práce. Před tím, než zachováte snídani, chcete čekat na úkol, který představuje informační zprávu, před přidáním másla a zaseknutím. Tuto práci můžete vyjádřit pomocí následujícího kódu:

[!code-csharp[ComposeToastTask](./snippets/index/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Předchozí metoda má `async` v podpisu modifikátor. To signalizuje kompilátoru, že tato metoda obsahuje `await` příkaz, obsahuje asynchronní operace. Tato metoda představuje úkol, který označuje chléb a pak přidá máslo a zaseknutí. Tato metoda vrátí hodnotu <xref:System.Threading.Tasks.Task%601> , která představuje složení těchto tří operací. Hlavní blok kódu teď bude:

[!code-csharp[StartConcurrentTasks](./snippets/index/AsyncBreakfast-V3/Program.cs#Main)]

Předchozí změna ukázala důležitou techniku pro práci s asynchronním kódem. Můžete vytvářet úkoly oddělením operací s novou metodou, která vrací úlohu. Můžete vybrat, kdy se má tento úkol očekávat. Můžete spustit souběžně jiné úkoly.

## <a name="await-tasks-efficiently"></a>Pro úlohy čekají efektivně

Řadu `await` příkazů na konci předchozího kódu lze zlepšit pomocí metod `Task` třídy. Jedno z těchto rozhraní API je <xref:System.Threading.Tasks.Task.WhenAll%2A> , což vrátí, <xref:System.Threading.Tasks.Task> která se dokončí po dokončení všech úkolů v seznamu argumentů, jak je znázorněno v následujícím kódu:

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Další možností je použít <xref:System.Threading.Tasks.Task.WhenAny%2A> , který vrátí a `Task<Task>` , který se dokončí po dokončení některého z jeho argumentů. Můžete očekávat vrácenou úlohu s vědomím, že již byla dokončena. Následující kód ukazuje, jak můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> k čekání na dokončení první úlohy a následnému zpracování výsledku. Po zpracování výsledku z dokončené úlohy odstraníte tuto dokončenou úlohu ze seznamu úkolů předaných do `WhenAny` .

[!code-csharp[AwaitAnyTask](./snippets/index/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Po všech těchto změnách finální verze `Main` vypadá jako následující kód:

[!code-csharp[Final](./snippets/index/AsyncBreakfast-final/Program.cs#Main)]

Tento konečný kód je asynchronní. Přesněji odráží, jak by osoba navařené snídani. Porovnejte předchozí kód s první ukázkou kódu v tomto článku. Základní akce jsou stále jasné z čtení kódu. Tento kód si můžete přečíst stejným způsobem, jakým jste si přečetli tyto pokyny pro vytvoření snídaně na začátku tohoto článku. Jazykové funkce pro `async` a `await` poskytují překlad pro všechny uživatele, kteří se dodávají podle těchto písemných pokynů: spustit úlohy jako vy a neblokovat čekání na dokončení úkolů.
