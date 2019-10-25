---
title: Aktualizovaný vzor událostí .NET Core
description: Přečtěte si, jak vzor událostí .NET Core umožňuje flexibilitu proti zpětné kompatibilitě a implementaci bezpečného zpracování událostí s využitím asynchronních předplatitelů.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 85fa4fd111a9eab01c1d32949d9fcc5f6300e33c
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798889"
---
# <a name="the-updated-net-core-event-pattern"></a>Aktualizovaný vzor událostí .NET Core

[Předchozí](event-pattern.md)

Předchozí článek pojednává o nejběžnějších vzorech událostí. .NET Core má uvolněný vzor. V této verzi již definice `EventHandler<TEventArgs>` nemá omezení, které `TEventArgs` musí být třída odvozená z `System.EventArgs`.

Tím se zvyšuje flexibilita a je zpětně kompatibilní. Pojďme začít s flexibilitou. Třída System. EventArgs zavádí jednu z metod: `MemberwiseClone()`, která vytvoří kopii objektu bez podstruktury.
Tato metoda musí použít reflexi pro implementaci své funkce pro jakoukoliv třídu odvozenou z `EventArgs`. Tuto funkci je snazší vytvořit v konkrétní odvozené třídě. To efektivně znamená, že odvozený od System. EventArgs je omezení, které omezuje vaše návrhy, ale neposkytuje žádné další výhody.
Ve skutečnosti můžete změnit definice `FileFoundArgs` a `SearchDirectoryArgs` tak, že nejsou odvozeny od `EventArgs`.
Program bude fungovat přesně stejně.

Můžete také změnit `SearchDirectoryArgs` na strukturu, pokud uděláte jednu změnu:

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

Další změnou je volat konstruktor bez parametrů před vstupem do konstruktoru, který inicializuje všechna pole. Bez toho, aby se tato pravidla C# přidala, se před přiřazením k vlastnostem hlásí, že se k nim přistupovaly.

Neměňte `FileFoundArgs` z třídy (typu odkazu) na strukturu (typ hodnoty). Důvodem je, že protokol pro zpracování zrušení vyžaduje, aby byly argumenty události předány odkazem. Pokud jste provedli stejnou změnu, třída hledání souborů nemůže nikdy sledovat žádné změny provedené u žádného odběratele události. Pro každého předplatitele by se použila nová kopie struktury a tato kopie by byla jinou kopií než ta, kterou vyhledává objekt hledání souborů.

Nyní zvažte, jak tato změna může být zpětně kompatibilní.
Odebrání omezení neovlivní žádný existující kód. Všechny existující typy argumentů události jsou stále odvozeny od `System.EventArgs`.
Zpětná kompatibilita je jedním z hlavních důvodů, proč se budou nadále odvozovat z `System.EventArgs`. Všechna stávající předplatitelé událostí budou předplatitelé události, která následovala za klasickým vzorem.

Po podobné logice by jakýkoli typ argumentu události, který teď vytvořil, neměl žádné předplatitele v existujících základech kódu. Nové typy událostí, které nejsou odvozeny od `System.EventArgs`, nebudou tyto základy kódu přerušit.

## <a name="events-with-async-subscribers"></a>Události s asynchronními předplatiteli

Máte jeden finální vzor k získání informací o tom, jak správně napsat předplatitele událostí volající asynchronní kód. Tato výzva je popsaná v článku o [Async a await](async.md). Asynchronní metody mohou mít návratový typ void, ale to se důrazně nedoporučuje. Když kód předplatitele události volá asynchronní metodu, nemáte žádnou volbu, ale chcete vytvořit metodu `async void`. Podpis obslužné rutiny události vyžaduje.

Je nutné sjednotit tyto protichůdné doprovodné materiály. V některých případech je nutné vytvořit bezpečnou `async void` metodu. Níže je uveden seznam základních principů, které je třeba implementovat:

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

Nejprve si všimněte, že obslužná rutina je označena jako asynchronní obslužná rutina. Protože je přiřazen k typu delegáta události, bude mít návratový typ void. To znamená, že je nutné postupovat podle vzoru zobrazeného v obslužné rutině a neumožňovat vyvolání výjimek z kontextu asynchronní obslužné rutiny. Protože nevrací úlohu, není k dispozici žádná úloha, která by mohla ohlásit chybu zadáním chybového stavu. Vzhledem k tomu, že metoda je asynchronní, metoda nemůže jednoduše vyvolat výjimku. (Metoda volání pokračuje v provádění, protože je `async`.) Skutečné chování za běhu bude definováno pro různá prostředí odlišně. Může ukončit vlákno nebo proces, který vlastní vlákno, nebo nechat proces v neurčitém stavu. Všechny tyto potenciální výsledky jsou vysoce nežádoucí.

To je důvod, proč byste měli zabalit příkaz await pro asynchronní úlohu ve vlastním bloku try. Pokud dojde k selhání úlohy, můžete chybu zaznamenat. Pokud se jedná o chybu, ze které se aplikace nemůže zotavit, můžete rychle a řádně ukončit program.

Ty jsou hlavní aktualizace pro vzorek událostí .NET. V knihovnách, ve kterých pracujete, se zobrazí mnoho příkladů předchozích verzí. Měli byste se ale seznámit s tím, co mají i nejnovější vzory.

Další článek v této sérii vám pomůže rozlišovat mezi používáním `delegates` a `events` v návrzích. Jsou to podobné koncepty a tento článek vám pomůže udělat si nejlepší rozhodnutí pro vaše programy.

[Next](distinguish-delegates-events.md)
