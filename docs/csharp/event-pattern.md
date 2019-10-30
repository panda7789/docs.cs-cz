---
title: Standardní vzory událostí .NET
description: Přečtěte si o vzorech událostí .NET a o tom, jak vytvořit standardní zdroje událostí a přihlásit se k odběru a zpracovávat standardní události ve vašem kódu.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: a050dc9a11470ff3b71488ce2ab4b92e607aa9b0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037170"
---
# <a name="standard-net-event-patterns"></a>Standardní vzory událostí .NET

[Předchozí](events-overview.md)

Události .NET obecně následují několik známých vzorů. Standardizace těchto vzorů znamená, že vývojáři mohou využít znalosti těchto standardních vzorů, které lze použít na jakýkoli program událostí .NET.

Pojďme si projít tyto standardní vzory, abyste měli všechny znalosti, které potřebujete k vytvoření standardních zdrojů událostí, a přihlásit se k odběru a zpracovávat standardní události v kódu.

## <a name="event-delegate-signatures"></a>Signatury delegátů událostí

Standardní signatura pro delegáta události .NET je:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Návratový typ je void. Události jsou založené na delegátech a jsou delegáti vícesměrového vysílání. Který podporuje více předplatitelů pro libovolný zdroj události. Jediná návratová hodnota z metody se neškáluje na více odběratelů událostí. Jakou návratovou hodnotu zdroj události uvidí po vyvolání události? Později v tomto článku se dozvíte, jak vytvořit protokoly událostí, které podporují předplatitele událostí, které oznamují informace do zdroje událostí.

Seznam argumentů obsahuje dva argumenty: odesílatel a argumenty události. Typ doby kompilace `sender` je `System.Object`, i když pravděpodobně znáte více odvozeného typu, který by byl vždy správný. Podle konvence použijte `object`.

Druhý argument byl obvykle typ, který je odvozen od `System.EventArgs`. (Uvidíte v [Další části](modern-events.md) , že tato konvence už není vynutila.) Pokud váš typ události nepotřebuje žádné další argumenty, budete přesto poskytovat oba argumenty.
Existuje zvláštní hodnota `EventArgs.Empty`, kterou byste měli použít k označení, že vaše událost neobsahuje žádné další informace.

Pojďme sestavit třídu, která obsahuje seznam souborů v adresáři, nebo některé z jeho podadresářů, které následují vzor. Tato komponenta vyvolá událost pro každý nalezený soubor, který odpovídá vzoru.

Použití modelu událostí poskytuje některé výhody návrhu. Můžete vytvořit několik posluchačů událostí, které při nalezení hledaného souboru provádějí různé akce. Kombinování různých posluchačů může vytvářet robustnější algoritmy.

Tady je počáteční deklarace argumentu události pro vyhledání hledaného souboru: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

I když tento typ vypadá jako malý, pouze datový typ, měli byste postupovat podle konvence a vytvořit z něj referenční (`class`) typ. To znamená, že objekt argumentu bude předán odkazem a všechny aktualizace dat budou zobrazeny všemi předplatiteli. První verze je neproměnlivý objekt. Měli byste raději nastavit vlastnosti v argumentu události typ unmutableed. Jeden předplatitel pak nemůže změnit hodnoty předtím, než je uvidí jiný odběratel. (V takovém případě jsou k dispozici výjimky, jak vidíte níže.)  

Dále je potřeba vytvořit deklaraci události ve třídě hledání ve službě. Využití `EventHandler<T>`ho typu znamená, že ještě nemusíte vytvářet jinou definici typu. Jednoduše použijete obecnou specializaci.

Pojďme vyplňovat třídu hledání souborů, aby bylo možné vyhledávat soubory, které odpovídají vzoru, a vyvolat správnou událost při zjištění shody.

[!code-csharp[FileSearcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Definování a vyvolávání událostí podobných poli

Nejjednodušší způsob, jak přidat událost do vaší třídy, je deklarovat tuto událost jako veřejné pole, jako v předchozím příkladu:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Vypadá to, že deklaruje veřejné pole, což by znamenalo špatný objektově orientovaný postup. Chcete chránit přístup k datům prostřednictvím vlastností nebo metod. Přestože to může vypadat jako špatný postup, kód generovaný kompilátorem vytvoří obálky, aby k objektům událostí bylo možné získávat přístup pouze bezpečným způsobem. Jediné operace dostupné v události podobné poli jsou přidání obslužné rutiny:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

a odebrat obslužnou rutinu:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Všimněte si, že pro obslužnou rutinu je k dispozici místní proměnná. Pokud jste použili tělo lambda, odebrání by nefungovalo správně. By to byla jiná instance delegáta a tiše nedělá nic.

Kód mimo třídu nemůže vyvolat událost, ani nemůže provádět žádné jiné operace.

## <a name="returning-values-from-event-subscribers"></a>Vracení hodnot od odběratelů událostí

Vaše jednoduchá verze funguje správně. Pojďme přidat další funkci: zrušení.

Pokud vyvoláte nalezenou událost, naslouchací procesy by měly být schopné zastavit další zpracování, pokud je tento soubor ten, který byl naposledy vyžádán.

Obslužné rutiny událostí nevrací hodnotu, takže je třeba komunikovat jiným způsobem. Standardní vzor události používá objekt EventArgs k zahrnutí polí, které mohou předplatitelé události použít ke sdělení zrušení.

Existují dva různé vzory, které by mohly být použity na základě sémantiky zrušení smlouvy. V obou případech přidáte pole Boolean do EventArguments pro událost nalezeného souboru. 

Jeden ze vzorů umožní jednomu předplatiteli zrušit operaci.
Pro tento model je nové pole inicializováno na `false`. Každý předplatitel ho může změnit na `true`. Poté, co všichni předplatitelé viděli vyvolanou událost, ověří Tato komponenta logickou hodnotu a provede akci.

Druhý vzor by tuto operaci zrušil jenom v případě, že všichni předplatitelé chtěli operaci zrušit. V tomto modelu se nové pole inicializuje, aby označovalo, že operace se má zrušit, a každý předplatitel ho může změnit, aby označoval, že operace by měla pokračovat.
Poté, co všichni předplatitelé viděli vyvolanou událost, vyhledá součást hledání v Boolean logickou hodnotu a provede akci. Tento model obsahuje ještě jeden krok navíc: součást musí zjistit, jestli se událost objevila pro nějaké předplatitele. Pokud žádné předplatitelé neexistují, pole by znamenalo nesprávné zrušení.

Pojďme implementovat první verzi této ukázky. Do typu `FileFoundArgs` musíte přidat pole Boolean s názvem `CancelRequested`:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

Toto nové pole se automaticky inicializuje na `false`, což je výchozí hodnota pro pole Boolean, takže nebudete nic rušit. Jedinou jinou změnou součásti je zkontrolování příznaku po vyvolání události, aby bylo možné zjistit, zda některý z předplatitelů požadoval zrušení:

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

Jednou z výhod tohoto vzoru je, že se nejedná o zásadní změnu.
Žádný z předplatitelů požádal o zrušení před a ještě není. Žádný z kódů předplatitele není potřeba aktualizovat, pokud nechtějí podporovat nový protokol zrušení. Je velmi volně spojená.

Pojďme předplatitele aktualizovat, aby po nalezení prvního spustitelného souboru vyžádal zrušení.

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Přidání další deklarace události

Pojďme přidat další funkci a předvést pro události idiomy další jazyky. Pojďme přidat přetížení metody `Search`, která projde všechny podadresáře při hledání souborů.

Může se jednat o zdlouhavou operaci v adresáři s mnoha podadresáři. Pojďme přidat událost, která se aktivuje při každém zahájení hledání nového adresáře. To umožňuje předplatitelům sledovat průběh a aktualizovat uživatele jako průběh. Všechny ukázky, které jste dosud vytvořili, jsou veřejné. Pojďme udělat tuto interní událost. To znamená, že můžete také nastavit typy používané pro interní argumenty.

Začnete vytvořením nové odvozené třídy EventArgs pro vytváření sestav nového adresáře a postupu. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Znovu můžete postupovat podle doporučení a nastavit pro argumenty události neměnný typ odkazu.

Dále definujte událost. Tentokrát použijete jinou syntaxi. Kromě použití syntaxe pole můžete explicitně vytvořit vlastnost s obslužnými rutinami přidat a odebrat. V této ukázce nebudete v těchto obslužných rutinách potřebovat další kód, ale ukazuje, jak byste je vytvořili.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

V mnoha způsobech kód, který sem píšete, zrcadlí kód, který kompilátor generuje pro definice událostí pole, které jste viděli dříve. Vytvoříte událost pomocí syntaxe, která je velmi podobná jako vlastnost použitá pro [vlastnosti](properties.md). Všimněte si, že obslužné rutiny mají jiné názvy: `add` a `remove`. Jsou volány k přihlášení k odběru události nebo k odhlášení odběru události. Všimněte si, že je také nutné deklarovat soukromé pole zálohování pro uložení proměnné události. Je inicializována na hodnotu null.

Nyní přidáme přetížení metody `Search`, která projde podadresáři a vyvolá obě události. Nejjednodušší způsob, jak to provést, je použít výchozí argument k určení, že chcete prohledávat všechny adresáře:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

V tomto okamžiku můžete spustit aplikaci, která volá metodu Overload pro hledání všech podadresářů. K nové události `ChangeDirectory` neexistují žádní předplatitelé, ale použití `?.Invoke()` idiom zajišťuje správné fungování.

 Pojďme přidat obslužnou rutinu pro zápis řádku, který ukazuje průběh v okně konzoly. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

Viděli jste vzory, které jsou následovány v rámci ekosystému .NET.
Díky učení těchto vzorů a konvencí budete rychle psát idiomatickou C# a .NET.

Dále uvidíte některé změny v těchto vzorech v nejnovější verzi rozhraní .NET.

[Next](modern-events.md)
