---
title: Standardní vzory událostí .NET
description: Další informace o vzory událostí .NET a vytvoření zdroje událostí úrovně standard a odběru a zpracování standardní události ve vašem kódu.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 0b10c440f4d05533032aa94819ec879f6a1ca2a4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399947"
---
# <a name="standard-net-event-patterns"></a>Standardní vzory událostí .NET

[Předchozí](events-overview.md)

Události .NET obvykle postupují podle několik známých vzorců. Standardizují používáním těchto vzorců znamená, že vývojáři mohou využít znalost těchto standardní vzory, které lze použít u každého programu událost .NET.

Podívejme se tyto standardní vzory tak budou mít všechny znalosti potřebné k vytvoření zdroje událostí úrovně standard a odběru a zpracování standardní události ve vašem kódu.

## <a name="event-delegate-signatures"></a>Podpisy delegáta události

Standardní podpisu pro delegáta události .NET je:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Návratový typ je typ void. Události jsou založeny na delegáty a jsou vícesměroví delegáti. U každého zdroje událostí, která podporuje několik předplatitelů. Jednu návratovou hodnotu z metody neškáluje několika odběratelům události. Který vrátí hodnotu nemá viz zdroj událostí po vyvolání události? Dále v tomto článku uvidíte, jak vytvořit tyto sestavy informace zdroje událostí protokoly událostí, které podporují odběratelů událostí.

Seznam argumentů obsahuje dva argumenty: odesílatele a argumenty události. Typ času kompilace `sender` je `System.Object`, i když pravděpodobně znáte více odvozený typ, který by měl být vždy správná. Podle konvence, použijte `object`.

Druhý argument obvykle byl typ, který je odvozen z `System.EventArgs`. (Zobrazí se vám v [další části](modern-events.md) , který tato konvence je už nebudou vynucené.) Pokud váš typ události není nutné žádné další argumenty, se stále poskytovat oba argumenty.
Je zvláštní hodnota `EventArgs.Empty` , používejte k označení, že události neobsahuje žádné další informace.

Vytvořme třídu, která obsahuje seznam souborů v adresáři nebo některý z jeho podadresářů, které se řídí vzorem. Tato součást vyvolává událost pro každý soubor nalezen odpovídající vzoru.

Použití modelu event obsahuje některé výhody návrhu. Můžete vytvořit víc naslouchacích procesů událostí, které provádí různé akce, když se najde soubor hledané kombinaci. Kombinování různých naslouchacích procesů můžete vytvořit robustnější algoritmy.

Tady je počáteční událost deklaraci argumentu pro vyhledání souboru hledané kombinaci: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

I v případě, že tento typ vypadá jako malé, pouze pro datový typ, by měl postupovat podle úmluvy a usnadňují odkaz (`class`) typu. To znamená, že objekt argument se předá odkazem a všechny aktualizace dat se můžou zobrazit všichni předplatitelé. První verze je neměnný objekt. Měli dát přednost aby vlastnosti v váš typ argumentu události neměnné. Tímto způsobem jednoho odběratele nelze změnit hodnoty, než je uvidí jiného předplatitele. (Existují výjimky, jak uvidíte níže).  

Dále musíme vytvořit deklaraci události ve třídě FileSearcher. Využití `EventHandler<T>` typ znamená, že není nutné vytvořit další definici typu. Jednoduše použijte specializaci obecný.

Pojďme vyplňte FileSearcher třídy budou hledány soubory, které odpovídají vzoru a vyvolání správné události při zjištění shody.

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Definování a vyvolávání událostí jako pole

Chcete-li tuto událost deklarovat jako veřejné pole, jako v předchozím příkladu je nejjednodušší způsob, jak přidat událost do vaší třídy:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Vypadá to na to je deklarace veřejné pole, které by se zdají být chybný postup objektově orientovaný. Chcete chránit přístup k datům prostřednictvím vlastnosti nebo metody. Když to provést, vypadají, jako chybný postupem je kód generovaný kompilátorem vytváření obálek tak, aby objekty událostí lze přistupovat pouze v nouzovém způsoby. Pouze operace dostupné na pole podobné události jsou přidat obslužnou rutinu:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

a odebrat obslužnou rutinu:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Všimněte si, že je lokální proměnná pro obslužnou rutinu. Pokud jste použili tělo výrazu lambda, odebrat nebude fungovat správně. To bude jinou instanci delegáta a tiše Neprovádět žádnou akci.

Kód mimo třídy nemohou vyvolat události, ani provádět jiné operace.

## <a name="returning-values-from-event-subscribers"></a>Vrací hodnoty od odběratelů událostí

Jednoduchá verze funguje správně. Přidáme další funkce: zrušení.

Při zvýšení nalezených událostí naslouchacích procesů měl zastaví další zpracování, pokud tento soubor je, že žádá o poslední z nich.

Obslužné rutiny událostí nesmí vracet hodnotu, proto musíte ke komunikaci, která jiným způsobem. Vzor standardních událostí používá objekt EventArgs pro zahrnutí polí, které odběratelů událostí můžete použít ke komunikaci Storno.

Existují dva různé vzorce, které mohou být využity, podle sémantiky smlouvy zrušit. V obou případech přidáte pole boolean EventArguments nalezený soubor události. 

Jeden vzor by umožnilo jakékoli jednoho odběratele na zrušení operace.
Pro tento model je nové pole inicializovány na `false`. Libovolný předplatitel lze změnit na `true`. Po všichni předplatitelé viděli vyvolaná událost, součást FileSearcher prozkoumá logickou hodnotu a provede akci.

Druhý vzor by pouze zrušit operaci, pokud všichni předplatitelé operace byla zrušena. V tomto vzoru nové pole je inicializován do značí by měla operaci zrušit a libovolný předplatitel by mohl změnit označující, že by operace měla pokračovat.
Po všichni předplatitelé viděli vyvolaná událost, součást FileSearcher prozkoumá logickou hodnotu a provede akci. Existuje jeden další krok v tomto vzoru: součást potřebuje vědět, pokud jste viděli všechny předplatitele události. Pokud neexistují žádné předplatitele, pole by označoval zrušení nesprávně.

Můžeme implementovat první verzi pro tuto ukázku. Je třeba přidat pole boolean s názvem `CancelRequested` k `FileFoundArgs` typu:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

Toto nové pole je automaticky inicializován na `false`, výchozí hodnota pro pole Boolean, takže nezrušíte omylem. Jediná další změna součást je kontrola příznak po vyvolání události pro zobrazení, pokud některý z odběratele odeslali žádost o zrušení:

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

Jednou z výhod tohoto modelu je, že to není zásadní změnu.
Žádný odběratelů požadováno zrušení před a stále nejsou. Žádný kód odběratele musí, aktualizaci, pokud chtějí podporují nový protokol Storno. Je velmi volně vázány.

Umožňuje aktualizovat odběratele tak, aby požaduje zrušení, jakmile nalezne první spustitelný soubor:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Přidání další deklarace událostí

Pojďme přidat jeden další funkce a ukazují další idiomy jazyk pro události. Přidejme přetížení `Search()` metodu, která prochází přes všechny podadresáře při hledání souborů.

To mohl být dlouhotrvající operace v adresáři s mnoha podadresáře. Přidejme událost, která získá vyvolá, když začne každé nové prohledávání adresáře. To umožňuje předplatitelům sledování průběhu a aktualizaci uživatele jde o průběhu. Všechny ukázky, které jste vytvořili zatím byly veřejné. Vnitřní událost vytvoříme tohoto objektu. To znamená, že můžete provést také typy používané pro interní argumenty také.

Začnete vytvořením nového EventArgs odvozené třídy pro vytváření sestav nový adresář a průběh. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Znovu postupujte podle doporučení pro nezměnitelný odkazový typ pro argumenty události.

Dále definujte události. Tentokrát použijeme odlišnou syntaxi. Kromě použití syntaxe pole, můžete explicitně vytvořit vlastnost, s přidat a odebrat obslužné rutiny. V této ukázce nebude potřebovat další kód v těchto obslužných rutinách, ale to ukazuje, jak by je vytvořit.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

V mnoha směrech kód, který napíšete zde zrcadlení, že kód, kompilátor vygeneruje pro definice pole událostí jste viděli dříve. Vytvořit událost pomocí syntaxe velmi podobné, který používá pro [vlastnosti](properties.md). Všimněte si, že obslužných rutin mají odlišné názvy: `add` a `remove`. Nazývají se přihlášení k odběru události, nebo zrušit odběr události. Všimněte si, že je také třeba deklarovat privátní pomocné pole k uložení proměnné události. Je inicializován na hodnotu null.

V dalším kroku přidejme přetížení metody Search(), který prochází skrz podadresářů a vyvolává události, i. Nejjednodušší způsob, jak to provést, je výchozí argument použít k určení, zda chcete vyhledávat všechny adresáře:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

V tomto okamžiku spustíte aplikaci volání přetížení pro vyhledávání všech podadresářích. Nejsou žádné předplatitele na novém `ChangeDirectory` události, ale používat `?.Invoke()` idiom zajistí, že to funguje správně.

 Přidejme obslužnou rutinu zapsat řádek, který zobrazuje průběh v okně konzoly. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

Už víte, vzorů, které jsou použity v celém ekosystému .NET.
Podle studijního tyto vzory a konvence, budete psát idiomatickou C# a .NET rychle.

V dalším kroku se zobrazí některé změny v tyto vzory v nejnovější verzi rozhraní .NET.

[Next](modern-events.md)
