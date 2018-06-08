---
title: Vzor aktualizované .NET Core událostí
description: Zjistěte, jak vzor událostí .NET Core umožňuje flexibilitu s zpětné kompatibility a jak implementovat zpracování událostí bezpečné s async odběratele.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 8f28c3ea9d8cf3e8fc68953c79def5744eb5abe4
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827177"
---
# <a name="the-updated-net-core-event-pattern"></a>Vzor aktualizované .NET Core událostí

[Předchozí](event-pattern.md)

V předchozím článku popsané nejčastější události vzory. .NET core má více volný vzor. V této verzi `EventHandler<TEventArgs>` definice již obsahuje omezení, `TEventArgs` musí být třída odvozená z `System.EventArgs`.

To zvyšuje flexibilitu pro vás a je zpětně kompatibilní. Začněme flexibilitu. Třída System.EventArgs představuje jedno z těchto metod: `MemberwiseClone()`, která vytvoří kopii objektu bez podstruktury.
Zda metoda musí používat reflexe kvůli implementaci jeho funkce pro všechny třídy odvozené od `EventArgs`. Které tuto funkci je snazší vytvářet konkrétní odvozené třídy. To efektivně znamená, že odvozování z System.EventArgs je omezení, které omezuje návrhů, ale neposkytuje žádné další výhody.
Ve skutečnosti, můžete změny definice `FileFoundArgs` a `SearchDirectoryArgs` tak, aby není odvozena od `EventArgs`.
Tento program bude fungovat stejně.

Můžete také změnit `SearchDirectoryArgs` do struktury, pokud jste provedli jednu další změny:

[!code-csharp[SearchDir](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Define search directory event")]

Další změnou je volat výchozí konstruktor před vstupem konstruktor, který inicializuje všechna pole. Bez přidání by pravidla jazyka C# hlásit, že vlastnosti přistupuje předtím, než byla přiřazena.

Byste neměli měnit `FileFoundArgs` z třídy (odkaz) za účelem struktury (typ hodnoty). Je to způsobeno protokol pro zpracování Storno vyžaduje, že jsou argumenty událostí předána odkazem. Pokud jste provedli stejnou změnu, může třída vyhledávání souboru nikdy sledovat veškeré změny provedené žádné události odběratelů. Novou kopii struktura se použije pro každý odběratele a tato kopie bude kopii jiný než ten, který pohledu hledání objektu soubor.

Dále zvažte, jak může být tato změna zpětně kompatibilní.
Odebrání omezení nemá vliv na existující kód. Všechny existující typy argumentů událostí stále odvozena od `System.EventArgs`.
Zpětné kompatibility je jedním z hlavních důvodů proč budou i nadále odvozena od `System.EventArgs`. Všechny existující události odběratelé nebudou odběratele, kteří mají na událost, která postupovali podle vzoru classic.

Všechny následující podobné logiku základy argumentu události vytvořen nyní neměli všechny odběratele v jakékoli existující kódu. Nové typy událostí, které není odvozena od `System.EventArgs` není zalomení ty základy kódu.

## <a name="events-with-async-subscribers"></a>Události se asynchronní odběratele

Máte jeden konečné vzor Další: jak napsat správně události odběratele, které volají asynchronní kódu. Na výzvu je popsána v článku na [async a operátoru await](async.md). Asynchronní metody může mít typ vrácené hodnoty void, ale který se důrazně nedoporučuje. Pokud váš kód odběratele událostí volá asynchronní metody, máte žádná volba však vytvořit `async void` metoda. Podpis obslužné rutiny událostí vyžaduje.

Je třeba sjednotit dosáhnout návod. Nějakým způsobem, je nutné vytvořit sejfu `async void` metoda. Základní informace o vzor, který je nutné implementovat jsou níže:

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

Všimněte si nejprve, aby obslužná rutina je označen jako obslužné rutiny asynchronní. Protože je právě přiřazován na obslužnou rutinu události typ delegáta, bude mít typ vrácené hodnoty void. To znamená, že musíte podle vzoru zobrazovaného v obslužné rutině a nepovolíte jakékoli výjimky vyvolání mimo kontext asynchronní obslužné rutiny. Protože nevrátí úlohu, není žádná úloha, která může hlásit chyby zadáním chybný stav. Jelikož metodou, je asynchronní, nelze vyvolat metodu jednoduše výjimka. (Volání metody pokračuje spuštění, protože je `async`.) Skutečné modul runtime chování budou jinak určené pro různá prostředí. Ukončovat vlákno, ukončovat program nebo program může zanechat v neurčeném stavu. Žádný z nich není funkční výstupy.

To je důvod, proč má obtékat příkaz await pro asynchronní úlohu v vlastní bloku try. Pokud ho způsobit úlohu chybný, můžou přihlásit k chybě. Jedná se o chybu, ze kterého nelze obnovit vaše aplikace, můžete ukončit program rychle a elegantně

Ty jsou hlavní aktualizace se vzorem událostí rozhraní .NET. Zobrazí se mnoho příkladů starší verze v knihovnách, se kterými můžete pracovat. Nicméně byste měli porozumět, co nejnovější vzory jsou také.

Další článek z této série umožňuje rozlišovat pomocí `delegates` a `events` v návrzích. Jsou podobné koncepty a tento článek vám pomůže zajistit nejlepší rozhodnutí pro vaše programy.

[Next](distinguish-delegates-events.md)
