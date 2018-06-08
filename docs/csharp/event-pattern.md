---
title: Standardní vzory událostí rozhraní .NET
description: Další informace o události vzory .NET a postup vytvoření zdroje Standardní událostí a přihlášení k odběru a zpracování standardních událostí v kódu.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 9bd9f71726647966dd1e4426b260484decb048c6
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827245"
---
# <a name="standard-net-event-patterns"></a>Standardní vzory událostí rozhraní .NET

[Předchozí](events-overview.md)

Události rozhraní .NET obecně podle několik známé vzorce. Standardizace na tyto vzory znamená, že vývojáři můžou využít znalosti o tyto standardní vzorce, které lze použít pro žádné program událostí rozhraní .NET.

Přejděte přes tyto standardní vzory, budete mít všechny znalostní báze, které potřebujete k vytvoření zdroje Standardní událostí a přihlášení k odběru a zpracování standardních událostí v kódu.

## <a name="event-delegate-signatures"></a>Podpisy delegáta událostí

Standardní podpis pro delegáta události .NET je:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Návratový typ je neplatné. Události jsou založené na Delegáti a jsou vícesměroví delegáti. U každého zdroje událostí, která podporuje více odběrateli. Jeden návratovou hodnotu z metody nemá škálování víc odběratelům událostí. Které návratová hodnota nemá najdete zdroje událostí po vyvolání události? Později v tomto článku uvidíte, jak vytvořit událost protokoly, které podporují událostí Odběratelé, kteří tyto informace sestav ke zdroji událostí.

Seznam argumentů obsahuje dva argumenty: odesílatel a argumenty událostí. Typ doba kompilace `sender` je `System.Object`, i když znáte pravděpodobně více odvozený typ, který by měl být vždy správný. Podle konvence, použijte `object`.

Druhý argument obvykle byl typ, který je odvozený od `System.EventArgs`. (Se zobrazí v [další části](modern-events.md) už vynucované touto konvencí.) Pokud váš typ události není nutné žádné další argumenty, bude stále zadat oba argumenty.
Speciální hodnotu, `EventArgs.Empty` že se mají používat k označení, že vaše události neobsahuje žádné další informace.

Umožňuje vytvořit třídu, která obsahuje soubory v adresáři, nebo libovolná z jejích podadresářů využívajících vzor. Tato součást se vyvolá událost pro každý soubor nalezeny, který odpovídá vzorku.

Pomocí model událostí obsahuje některé výhody návrhu. Můžete vytvořit víc naslouchacích procesů událostí, které provádět různé akce, když se najde soubor hledané kombinaci. Kombinování různých naslouchací procesy můžete vytvářet robustnější algoritmy.

Tady je deklaraci argument počáteční události pro hledání hledané kombinaci souboru: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

I když tento typ vypadá jako typ malé, pouze data, by měl postupovat podle konvence a nastavit jej jako odkaz (`class`) typu. To znamená, že se předají objekt argument odkazem a všechny aktualizace dat, bude zobrazit všechny odběratele. První verze je objekt neměnné. By měla přednost zkontrolujte vlastnosti ve vaší typ argumentu události neměnné. Tímto způsobem jednoho odběratele nelze změnit hodnoty, než jiné odběratele uvidí je. (Existují výjimky, jak se zobrazí níže).  

Dále je potřeba vytvořit deklaraci události ve třídě FileSearcher. Využití `EventHandler<T>` typ znamená, že nemusíte vytvářet ještě jiné definice typu. Jednoduše použijte obecné specializace.

Umožňuje vyplnit třídu FileSearcher k vyhledávání souborů, které odpovídají vzorku a vygenerovat správný událostí při zjištění shody.

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="definining-and-raising-field-like-events"></a>Definining a aktivaci událostí jako pole

Nejjednodušší způsob, jak přidat událost do vaší třídy je pro tuto událost deklarovat jako veřejné pole, jako v předchozím příkladu:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

To vypadá ho je deklarace veřejné pole, které by se zdají být chybný postup objektově orientované. Chcete chránit přístup k datům prostřednictvím vlastnosti nebo metody. Když to zkontrolujte vypadat jako chybný postup kód vygenerovaný kompilátor vytváření obálek tak, aby objektů událostí lze přistupovat pouze bezpečné způsoby. K dispozici jenom operace na pole podobné události jsou přidejte obslužnou rutinu:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

a obslužné rutiny odebírání:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Všimněte si, že je místní proměnná pro obslužnou rutinu. Pokud jste použili text argument lambda, odebrat nebude fungovat správně. By být jinou instanci delegáta a bezobslužně Neprovádět žádnou akci.

Kód mimo třídy nemohou vyvolat události, ani můžete provádět žádné jiné operace.

## <a name="returning-values-from-event-subscribers"></a>Vrácení hodnoty z události odběratele

Vaše jednoduché verze funguje bez problémů. Umožňuje přidat další funkcí: zrušení.

Když zvýšíte nachází události, moduly pro naslouchání byste měli mít k zastavení další zpracování, pokud tento soubor je, že poslední Hledat.

Obslužné rutiny událostí nevrátí hodnotu, takže potřebujete komunikovat, jiným způsobem. Vzor standardní událostí používá objekt EventArgs pro zahrnutí polí, které události odběratele používat ke komunikaci Storno.

Existují dva různé vzorce, které by mohly být použity, podle sémantika kontrakt Storno. V obou případech přidáte logická pole EventArguments pro událost nalezený soubor. 

Jeden vzor by umožnilo žádné jednoho odběratele na tlačítko Storno.
Pro tento vzor, je inicializováno nové pole `false`. Všechny odběratele lze změnit na `true`. Po všech Odběratelé, kteří mají vidět vyvolaná událost, komponentu FileSearcher prozkoumá logickou hodnotu a provede akci.

Druhý vzor by pouze zrušte operaci, pokud všechny Odběratelé, kteří chtěli operace byla zrušena. V tomto vzoru se inicializovat nové pole označíte, má-li zrušit operaci, a všechny odběratele může změnit se indikovat, že by měl v operaci pokračovat.
Po všech Odběratelé, kteří mají vidět vyvolaná událost, komponentu FileSearcher prověří logickou hodnotu a provede akci. V tomto vzoru je jeden další krok: součást musí vědět, pokud žádné Odběratelé, kteří mají vidět události. Pokud neexistují žádné odběratele, pole by nesprávně indikovat Storno.

Umožňuje implementovat první verzi pro tato ukázka. Je nutné přidat pole boolean s názvem `CancelRequested` k `FileFoundArgs` typu:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

Toto nové pole je automaticky inicializován na `false`, výchozí hodnota pro pole Boolean, tak nejsou omylem zrušit. Jediná další změna součást je kontrola příznak po vyvolání události pro zobrazení, pokud žádné z odběratele, kteří odeslali žádost o zrušení:

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

Jednou z výhod tohoto vzoru je, že to není narušující změně.
Žádná z odběratele požadovaný zrušení před, a stále nejsou. Žádný kód odběratele musí, aktualizaci, pokud chtějí nový protokol Storno. Je velmi volně vázány.

Umožňuje aktualizovat odběratele tak, aby požadavků zrušení, jakmile najde první spustitelný soubor:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Přidání jiného deklarace událostí

Umožňuje přidat jeden další funkce a ukažte, ostatní idioms jazyk pro události. Přidejme přetížení `Search()` metoda, který prochází skrz všechny podadresáře při hledání souborů.

To může získat být časově náročná operace v adresáři s mnoha podadresářů. Přidejme událost, která se získá vyvolá, když začne každou nové vyhledávání v adresáři. To umožňuje odběratele, kteří mají sledování postupu a aktualizovat uživatele o průběhu. Všechny ukázky, které jste vytvořili, pokud jsou veřejné. Provedeme tato interní událost. To znamená, že můžete provést také typy používané pro interní argumenty také.

Spusťte tak, že vytvoříte novou třídu odvozenou EventArgs pro vytváření sestav nový adresář a průběh. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Znovu postupujte podle doporučení pro neměnné odkaz pro argumenty událostí.

V dalším kroku definujte událost. Tentokrát budete používat jinou syntaxi. Kromě použití syntaxe pole, můžete explicitně vytvořit vlastnosti s přidat a odebrat obslužné rutiny. V této ukázce nebude potřebovat další kód v těchto obslužných rutin, ale to ukazuje, jak by je vytvořit.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

V mnoha směrech kód napsaný v tomto poli zrcadlení, že kód kompilátor generuje pro definice pole událostí Seznámili jste se dříve. Vytvoření událostí pomocí syntaxe velmi podobná používá pro [vlastnosti](properties.md). Všimněte si, že obslužných rutin mají odlišné názvy: `add` a `remove`. Toto nastavení se nazývá k přihlášení k odběru události nebo odhlášení odběru událostí. Všimněte si, že také musíte deklarovat privátní základní pole pro uložení proměnné události. Inicializací na hodnotu null.

V dalším kroku přidejme přetížení metody Search(), který prochází podadresáře a vyvolá obou události. Nejjednodušší způsob, jak tomu se má používat výchozí argument k určení, zda chcete vyhledávat všechny adresáře:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

V tomto okamžiku můžete spustit aplikace volání přetížení pro vyhledávání všech dílčí adresářů. Neexistují žádné odběratele na nové `ChangeDirectory` událostí, ale pomocí `?.Invoke()` stylu zajistí, že to funguje správně.

 Přidejme obslužnou rutinu k zápisu řádku, který zobrazuje průběh v okně konzoly. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

Seznámili jste se vzorů, které je třeba v rámci ekosystému .NET.
Podle informací tyto vzory a konvence, budete psát idiomatickou C# a .NET rychle.

V dalším kroku se zobrazí některé změny v tyto vzory v nejnovější verzi rozhraní .NET.

[Next](modern-events.md)
