---
title: Aktualizovaný vzor události jádra .NET
description: Zjistěte, jak vzor událostí .NET Core umožňuje flexibilitu se zpětnou kompatibilitou a jak implementovat bezpečné zpracování událostí s asynchronními odběrateli.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170433"
---
# <a name="the-updated-net-core-event-pattern"></a>Aktualizovaný vzor události jádra .NET

[Předchozí](event-pattern.md)

V předchozím článku se diskutovalo o nejběžnější vzory událostí. .NET Core má uvolněnější vzor. V této verzi `EventHandler<TEventArgs>` definice již nemá `TEventArgs` omezení, které musí `System.EventArgs`být třídy odvozené z .

To zvyšuje flexibilitu pro vás a je zpětně kompatibilní. Začněme s flexibilitou. Třída System.EventArgs zavádí jednu `MemberwiseClone()`metodu: , která vytvoří mělkou kopii objektu.
Tato metoda musí použít reflexe za účelem implementace `EventArgs`jeho funkce pro všechny třídy odvozené z . Tato funkce je jednodušší vytvořit v konkrétní odvozené třídy. To skutečně znamená, že vyplývající z System.EventArgs je omezení, které omezuje vaše návrhy, ale neposkytuje žádné další výhody.
Ve skutečnosti můžete změnit definice `FileFoundArgs` a `SearchDirectoryArgs` tak, aby nebyly `EventArgs`odvozeny z .
Program bude fungovat úplně stejně.

Můžete také změnit `SearchDirectoryArgs` na strukturu, pokud provedete ještě jednu změnu:

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

Další změnou je volání konstruktoru bez parametrů před zadáním konstruktoru, který inicializuje všechna pole. Bez tohoto přidání by pravidla jazyka C# hlásila, že vlastnosti jsou přístupné před jejich přiřazením.

Neměli `FileFoundArgs` byste měnit z třídy (typ odkazu) na strukturu (typ hodnoty). Je to proto, že protokol pro zpracování cancel vyžaduje, aby argumenty události byly předány odkazem. Pokud jste provedli stejnou změnu, třída vyhledávání souborů nikdy nemohla sledovat žádné změny provedené žádným z odběratelů události. Pro každého odběratele by se použila nová kopie struktury a tato kopie by byla jinou kopií, než kterou viděl objekt hledání souboru.

Dále zvažme, jak může být tato změna zpětně kompatibilní.
Odebrání omezení nemá vliv na existující kód. Všechny existující typy argumentů `System.EventArgs`události stále odvozují z .
Zpětná kompatibilita je jedním z hlavních `System.EventArgs`důvodů, proč budou i nadále odvodit z . Všechny existující předplatitelé událostí budou předplatiteli události, která následovala klasický vzor.

Podle podobné logiky by žádný typ argumentu události vytvořený nyní neměl žádné předplatitele v existujících základech kódu. Nové typy událostí, které `System.EventArgs` nejsou odvozeny z nepřeruší tyto základy kódu.

## <a name="events-with-async-subscribers"></a>Události s odběrateli aplikace Async

Máte jeden konečný vzor se učit: Jak správně psát předplatitele událostí, které volají asynchronní kód. Výzva je popsána v článku o [asynchronní a čekají](async.md). Asynchronní metody mohou mít prázdný návratový typ, ale to se důrazně nedoporučuje. Když váš kód účastníka události volá asynchronní metodu, nemáte jinou možnost než vytvořit metodu. `async void` Podpis obslužné rutiny události to vyžaduje.

Musíte se smířit s tímto protichůdným vedením. Nějak musíte vytvořit bezpečnou `async void` metodu. Základy vzoru, které je třeba implementovat, jsou níže:

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

Nejprve si všimněte, že obslužná rutina je označena jako asynchronní obslužná rutina. Vzhledem k tomu, že je přiřazen k typu delegáta obslužné rutiny události, bude mít prázdný návratový typ. To znamená, že je nutné sledovat vzor uvedený v obslužné rutině a nepovolit žádné výjimky, které mají být vyvolány z kontextu obslužné rutiny asynchronní. Vzhledem k tomu, že nevrátí úkol, neexistuje žádný úkol, který může hlásit chybu zadáním chybového stavu. Vzhledem k tomu, že metoda je asynchronní, metoda nemůže jednoduše vyvolat výjimku. (Volající metoda pokračovala v provádění, `async`protože je .) Skutečné chování za běhu bude definováno odlišně pro různá prostředí. Může ukončit vlákno nebo proces, který vlastní vlákno, nebo ponechat proces v neurčitém stavu. Všechny tyto potenciální výsledky jsou velmi nežádoucí.

To je důvod, proč byste měli zabalit příkaz await pro asynchronní úlohu ve vlastním bloku try. Pokud to způsobí chybnou úlohu, můžete chybu protokolovat. Pokud se jedná o chybu, ze které se aplikace nemůže zotavit, můžete program rychle a elegantně ukončit.

Jedná se o hlavní aktualizace vzoru událostí .NET. Zobrazí se mnoho příkladů starších verzí v knihovnách, se kterými pracujete. Měli byste však také pochopit, jaké jsou nejnovější vzory.

Další článek v této sérii vám `delegates` `events` pomůže rozlišovat mezi použitím a ve vašich návrzích. Jsou to podobné koncepty, a že článek vám pomůže učinit nejlepší rozhodnutí pro vaše programy.

[Další](distinguish-delegates-events.md)
