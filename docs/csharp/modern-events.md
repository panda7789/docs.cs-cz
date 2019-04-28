---
title: Vzor události aktualizované rozhraní .NET Core
description: Zjistěte, jak vzor události .NET Core umožňuje flexibilitu s zpětné kompatibility a jak implementovat zpracování bezpečné událostí s asynchronní odběrateli.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 5c7b9b4cb9bc22a73b865c45e225ce5c382380b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652036"
---
# <a name="the-updated-net-core-event-pattern"></a>Vzor události aktualizované rozhraní .NET Core

[Předchozí](event-pattern.md)

Předchozí článek byl věnován nejběžnější vzory událostí. .NET core má více volný vzor. V této verzi `EventHandler<TEventArgs>` definice již obsahuje omezení, která `TEventArgs` musí být třída odvozená z `System.EventArgs`.

To zvyšuje flexibilitu pro vás a je zpětně kompatibilní. Začněme s flexibilitou. Třída System.EventArgs představuje jednu metodu: `MemberwiseClone()`, která vytvoří Mělkou kopii objektu.
Že metoda musí používat reflexe kvůli implementaci jeho funkce pro všechny třídy odvozené z `EventArgs`. Je snazší vytvářet v konkrétní odvozené třídy, které tuto funkci. Který efektivně znamená, že odvozený od System.EventArgs je omezení, které omezuje vaše návrhy, ale neposkytuje žádné další výhody.
Ve skutečnosti může změnit definice `FileFoundArgs` a `SearchDirectoryArgs` tak, aby není odvozen od `EventArgs`.
Program bude fungovat stejně.

Můžete také změnit `SearchDirectoryArgs` na strukturu, pokud jste provedli jednu další změny:

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

Další změnou je volat konstruktor bez parametrů před zadáním konstruktor, který inicializuje všechna pole. Bez tohoto přidání pravidel C# zasílat zprávy, že vlastnosti přistupuje předtím, než jí byla přiřazena.

Byste neměli měnit `FileFoundArgs` ze třídy (odkaz) na strukturu (typ hodnoty). Důvodem je, protokol pro zpracování zrušení vyžaduje, aby událost argumenty jsou předány podle odkazu. Pokud jste provedli stejnou změnu, třída hledání souborů může nikdy sledovat všechny změny provedené ve všech odběratelů událostí. Novou kopii struktura se použije pro každý předplatitel, a tuto kopii by kopii jiný než ten, který viděli vyhledávací objektem file.

Dále zvažte, jak tato změna může být zpětně kompatibilní.
Odebrání omezení nemá vliv na žádný existující kód. Všechny existující typy argumentů události stále odvozovat `System.EventArgs`.
Zpětné kompatibility je jeden hlavní důvod, proč budou i nadále odvozovat `System.EventArgs`. Všechny existující události předplatitelé budou mít Odběratelé událost, která a Klasický model.

Po každém podobnou logiku základů kódu vytvořen nyní nemusí všechny předplatitele v jakékoli existující argumentu události. Nové typy událostí, které nejsou odvozeny od `System.EventArgs` není konec ty základů kódu.

## <a name="events-with-async-subscribers"></a>Události Async předplatitele

Máte jeden poslední vzorek se dozvíte: Jak správně psát odběratelů událostí, které volají asynchronní kód. Na výzvu je popsaný v článku na [async a operátoru await](async.md). Asynchronní metody může mít návratový typ void, ale je důrazně nedoporučuje. Po události odběratele kód volá asynchronní metodu, budete mít žádná volba ale k vytvoření `async void` metody. To vyžaduje podpisu obsluhy události.

Je potřeba sloučit tyto dosáhnout doprovodné materiály. Nějakým způsobem, je nutné vytvořit bezpečný `async void` metody. Základní informace, které potřebujete k implementaci vzoru jsou níže:

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

Napřed si všimněte, že obslužná rutina je označen jako asynchronní obslužnou rutinu. Protože se přiřazuje k obslužné rutině události typ delegáta, bude mít typ vrácené hodnoty void. To znamená musí postupovat podle vzor, uvedený v obslužné rutině a, aby všechny výjimky, která je vyvolána mimo kontext asynchronní obslužnou rutinu. Protože úloha nevrací, neexistuje žádný úkol, který můžete nahlásit chybu tak, že zadáte chybovém stavu. Vzhledem k tomu, že je metoda asynchronní, nelze metodu jednoduše vyvolat výjimku. (Volání metody pokračuje provádění, protože je `async`.) Chování skutečné za běhu bude být definovány rozdílně pro různá prostředí. Ho může ukončit vlákno, se může ukončit program nebo program může zanechat v neurčeném stavu. Žádná z nich jsou dobré výsledky.

To je důvod, proč zalamován příkazu await pro asynchronní úlohy ve vlastním bloku try. Pokud to způsobit chybnou úloh, můžete protokolovat chyby. Jedná se o chybu, ze kterého nelze obnovit vaše aplikace, můžete ukončit program snadno a bez výpadku

Toto jsou hlavní aktualizace vzor události .NET. Mnoho příkladů z dřívějších verzí knihoven, které při práci s se zobrazí. Nicméně byste měli rozumět, co nejnovější vzory jsou také.

Další článek v této sérii umožňuje rozlišit mezi použitím `delegates` a `events` v návrzích. Jsou podobné koncepty a tento článek vám pomůže vytvořit nejlepší rozhodnutí pro vaše programy.

[Next](distinguish-delegates-events.md)
