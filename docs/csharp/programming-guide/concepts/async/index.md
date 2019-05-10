---
title: Asynchronní programování v jazyce C#
description: Přehled C# jazykovou podporu pro asynchronní programování pomocí asynchronní, await, úloh a úkolů<T>
ms.date: 03/18/2019
ms.openlocfilehash: 350ccdeeb31e318ca0c1a8158691f58bf5208efb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65064119"
---
# <a name="the-task-asynchronous-programming-model-in-c"></a>Asynchronní programovací model úkolu v jazyce C\#

Asynchronní programovací model úloh (TAP) poskytuje abstrakci přes asynchronní kód. Při psaní kódu jako sekvenci příkazů, stejně jako vždy. Tento kód si můžete přečíst, jakoby dokončení každého příkazu před zahájením na další. Kompilátor provede několik transformace, protože některé z těchto příkazů může zahájit práci a vrátí <xref:System.Threading.Tasks.Task> , která představuje probíhající práci.

To je ten cíl této syntaxe: Povolit kód, který čte jako posloupnost příkazy, ale spustí mnohem složitější pořadí podle přidělení externích prostředků, a po dokončení úlohy. Je analogické k tom, jak lidé poskytují pokyny pro procesy, které zahrnují asynchronní úlohy. V celém tomto článku budete používat příkladem pokyny pro provedení snídani zobrazíte jak `async` a `await` klíčová slova usnadňují argumentovat o kód, který obsahuje řadu asynchronní pokyny. Měli byste napsat pokynů něco jako vysvětlují, jak je nechat snídani následujícího seznamu:

1. Přidá Šálek kávy.
1. Zahřívá se nahoru posun a pak ratifikoval dvě vajíčka.
1. Ratifikoval tři kolekce obsahuje nějaké řezy slanina.
1. Informační zprávu dva druhy chléb.
1. Přidání másle a zaseknutý do informační zprávy.
1. Přidá skla oranžové šťávu.

Pokud máte zkušenosti s dá uvařit, by se spustit tyto pokyny **asynchronně**. by start připravuje pan vejce a pak spusťte slanina. Byste umístit toaster chléb a pak spusťte vejce. V každém kroku procesu by spuštění úlohy a pak pozornost na úlohy, které jsou připravené pro vaši pozornost.

Dá uvařit snídani je dobrý příklad asynchronní práce, která není paralelní. Všechny tyto úlohy může zpracovat jenom jedna osoba (nebo vlákno). Pokračování snídani matric, jedna osoba může být snídani asynchronně pomocí před dokončením prvního spuštění další úlohy. Dá uvařit, postupuje jestli někdo ho sleduje. Jakmile začnete připravuje posun pro vejce, můžete začít frying slanina. Po spuštění slanina můžete umístit chléb do toaster.

Pro paralelní algoritmus budete potřebovat více můžeme (nebo vláken). Jeden s žádným vajíčka, jeden slanina, a tak dále. Každý z nich by zaměřuje na právě jednu úlohu. Každý Cookovy (nebo vlákno) by být blokován při synchronním čekání slanina až bude připravená k převrácení nebo informační zprávy na vyvolat přes pop. 

Nyní, vezměte v úvahu tyto stejné pokyny jako C# příkazy:

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

Počítače není interpretovat tyto pokyny, které stejný způsob, jak lidé dělají. Počítač bude blokovat u každého příkazu, dokud před přechodem na další příkaz dokončení práce. Který vytváří unsatisfying snídani. Dalších úlohách nebude možné spustit až do dokončení předchozích úkolů. Bude trvat déle vytvářet snídani a některé položky by jste získali studenou před používané pro služby. 

Pokud chcete počítač spustit asynchronně viz pokyny výše, psaní asynchronního kódu.

Tyto problémy jsou důležité pro programy, které napíšete ještě dnes. Při psaní klientských programů služby má uživatelské rozhraní bude reagovat na vstup uživatele. Vaše aplikace by neměla provést telefonu zdát, zatímco je stahování dat z webu. Při psaní serverových programů nechcete vlákna blokované. Tato vlákna může poskytovat další požadavky. Použití synchronního kódu existovat asynchronní alternativy neuškodí jednu možnost možnost pro horizontální navýšení kapacity menší vytištěny. Platíte za tyto blokovaná vlákna.

Úspěšné moderní aplikace vyžadují asynchronní kód. Bez podpory jazyka psaní asynchronního kódu vyžaduje zpětná volání, dokončení události nebo jiným způsobem, který zakryto původní záměr kódu. Výhodou synchronního kódu je, že je snadno pochopitelný. Podrobné akce, které umožňují snadno prohledávat a pochopit. Tradiční asynchronní modely vynutit můžete zaměřit na asynchronní povaze kód, nikoli na základní akce kódu.

## <a name="dont-block-await-instead"></a>Není blokovat, místo toho await

Předchozí kód ukazuje špatné postupy: vytváření synchronního kódu k provádění asynchronních operací. Jak je uvedená, tento kód blokuje vlákno provádění z provádění jiné práce. Nebudou přerušeny, zatímco všechny úlohy probíhají. Bylo by jakoby stared na Toaster byl po vložení chléb. Bude ignorovat kdokoli se mluví, dokud informační zpráva odebrány. 

Začněme tím, že aktualizace tento kód tak, aby vlákno nebrání v běhu úlohy. `await` – Klíčové slovo poskytuje neblokující způsob, jak spustit úlohu a potom pokračovat v provádění po dokončení této úlohy. Jednoduchá asynchronní verze bylo možné vytvořit kód snídani by vypadalo podobně jako následující fragment kódu:

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

Tento kód nebude blokovat, když se dá uvařit vejce nebo slanina. Tento kód nespustí všechny úkoly, i když. Stále byste umístit informační zprávy toaster a stare na to, až se zobrazí místní okno. Ale nejméně, by Odpovědět všem uživatelům chtěla vaši pozornost. V restaurace, kde jsou umístěny více objednávek může Cookovy zahájit jiného snídani, dokud se dá uvařit, první.

Vlákno pracují snídani se zablokují během čekání na spuštěná úloha, která ještě nebyla dokončena. Tato změna u některých aplikací je vše, co potřebujete. Grafické uživatelské rozhraní aplikace stále odpovídá uživateli s právě tuto změnu. V tomto scénáři má však další. Nechcete, aby každá komponenta úkoly, které mají být prováděny postupně. Je lepší pro spuštění jednotlivých úloh součásti před čekáním na dokončení předchozí úlohy.

## <a name="start-tasks-concurrently"></a>Souběžné spuštění úlohy

V mnoha případech budete chtít několik nezávislých úloh spustit okamžitě. Potom když každý úkol dokončí, můžete pokračovat v další práci, která je připravená. Analogicky snídani, který se dá dosáhnout snídani provádí rychleji. Také získáte všechno, co udělat blízko stejnou dobu. Získáte horké snídani.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a souvisejících typů jsou třídy, které vám umožní důvod o úlohách, které probíhají. Která umožňuje napsat kód, který lépe vypadá podobně jako způsob, vytvořili byste ve skutečnosti snídani. Byste začali dá uvařit vajíčka, slanina a informačních zpráv ve stejnou dobu. Jako každý vyžaduje akci, by pozornost tento úkol, postará o další akci a operátoru await na něco jiného, který vyžaduje vaši pozornost.

Spuštění úlohy a k uložení <xref:System.Threading.Tasks.Task> objekt, který reprezentuje práce. Budete `await` každý úkol před zahájením práce s jeho výsledek.

Pojďme provést tyto změny kódu snídani. Prvním krokem je pro uložení úlohy pro operace při spuštění, nikoli čeká se na nich:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Egg eggs = await eggTask;
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

V dalším kroku přesunete `await` příkazy pro slanina a vejce na konec metody, ještě před obsluhou snídani:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

Předchozí kód lépe funguje. Spuštění asynchronních úloh současně. Každý úkol await, pouze v případě, že potřebujete výsledky. Předcházející kód může být podobná kódu ve webové aplikaci, který zadává požadavky do různých mikroslužeb a pak sloučí výsledky do jediné stránce. Provede všechny požadavky okamžitě, pak `await` všechny úlohy a vytvářet webové stránky.

## <a name="composition-with-tasks"></a>Kompozice s úkoly

 Máte vše připraveno k snídani současně s výjimkou informační zprávy. Provádění informační zprávy je složení asynchronní operaci (toasting chléb) a synchronní operace (přidání v másle a zaseknutý). Aktualizuje se tento kód ukazuje důležitý koncept:

> [!IMPORTANT]
> Složení asynchronní operace, za nímž následuje synchronní práce je asynchronní operace. Uvádí další způsob, pokud operace jakékoli její části je asynchronní, celá operace je asynchronní.

Předchozí kód ukázala, že můžete použít <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekty pro uložení spuštěné úkoly. Můžete `await` každý úkol před použitím jeho výsledek. Dalším krokem je vytvoření metody, které představují kombinaci další práci. Ještě před obsluhou snídani, budete chtít await úloha, která představuje toasting chléb před přidáním másle a zaseknutý. Může představovat, které pracují s následujícím kódem:

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Předchozí metoda má `async` modifikátor v podpisu. Který signalizuje kompilátoru, že tato metoda obsahuje `await` příkazu; obsahuje asynchronní operace. Tato metoda představuje úloha, která toasts chléb, poté přičte másle a zaseknutý. Tato metoda vrátí hodnotu <xref:System.Threading.Tasks.Task%601> , která představuje složení těchto tří operací. Teď bude hlavní blok kódu:

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

Předchozí Změna zobrazené důležitou technikou pro práci s asynchronní kód. Vytvořit úkolů tak, že oddělíte operací do nové metody, která vrátí úkol. Můžete při await pro tuto úlohu. Současně můžete spustit další úkoly.

## <a name="await-tasks-efficiently"></a>Efektivně await úlohy

Řadu `await` příkazy na konci předchozí kód lze zvýšit pomocí metody `Task` třídy. Jedním z těchto rozhraní API je <xref:System.Threading.Tasks.Task.WhenAll%2A>, který vrátí hodnotu <xref:System.Threading.Tasks.Task> , která se dokončí po dokončení všech úkolů v seznamu argumentů, jak je znázorněno v následujícím kódu:

```csharp
await Task.WhenAll(eggTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Další možností je použít <xref:System.Threading.Tasks.Task.WhenAny%2A>, který vrátí hodnotu `Task<Task>` , která se dokončí při dokončení kterýkoliv z jejích argumentů. Můžete očekávat vrácené úlohy vědomím, že již byla dokončena. Následující kód ukazuje, jak můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> await pro čekání na dokončení a následně zpracovat výsledek první úlohy. Po zpracování výsledku dokončeného úkolu, odeberete ze seznamu úkolů předán dokončeného úkolu `WhenAny`.

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Za všechny tyto změny, finální verzi `Main` vypadá podobně jako následující kód:

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

Tento poslední kód je asynchronní. Přesněji odráží, jak by osoba Cookovy snídani. Porovnání předchozí kód s první příklad v tomto článku. Základní akce jsou stále zřejmé z čtení kódu. Tento kód si můžete přečíst stejně jako byste si přečíst tyto pokyny pro vytváření snídani na začátku tohoto článku. Funkce jazyka `async` a `await` poskytnout překlad každá osoba díky dodržovat ty písemných pokynů: zahájení úloh můžete a nemusíte blokovat čekání na dokončení úloh.
