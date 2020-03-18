---
title: Standardní vzory událostí .NET
description: Přečtěte si o vzorcích událostí rozhraní .NET a o tom, jak vytvořit standardní zdroje událostí a přihlásit se k odběru a zpracování standardních událostí ve vašem kódu.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: dec516767e43a6bf4edfa555e34f3adcc21a46e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146138"
---
# <a name="standard-net-event-patterns"></a>Standardní vzory událostí .NET

[Předchozí](events-overview.md)

.NET události obecně postupujte několik známých vzorů. Standardizace na tyto vzory znamená, že vývojáři mohou využít znalosti těchto standardních vzorů, které lze použít pro libovolný program událostí .NET.

Projděme si tyto standardní vzory, abyste měli všechny znalosti, které potřebujete k vytvoření standardních zdrojů událostí a k odběru a zpracování standardních událostí ve vašem kódu.

## <a name="event-delegate-signatures"></a>Podpisy delegátů událostí

Standardní podpis delegáta události .NET je:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Návratový typ je void. Události jsou založeny na delegátech a jsou vícesměrové delegáty. To podporuje více odběratelů pro jakýkoli zdroj událostí. Jedna vrácená hodnota z metody nelze škálovat na více předplatitelů událostí. Jakou vrácenou hodnotu vidí zdroj události po vyvolání události? Dále v tomto článku uvidíte, jak vytvořit protokoly událostí, které podporují předplatitele událostí, kteří hlásí informace zdroji událostí.

Seznam argumentů obsahuje dva argumenty: odesílatele a argumenty události. Typ času `sender` kompilace `System.Object`je , i když pravděpodobně znáte odvozenější typ, který by byl vždy správný. Podle konvence `object`použijte .

Druhý argument byl obvykle typ, který je `System.EventArgs`odvozen od . (V [další části](modern-events.md) uvidíte, že tato konvence již není vynucena.) Pokud váš typ události nepotřebuje žádné další argumenty, budete stále poskytovat oba argumenty.
Existuje zvláštní hodnota, `EventArgs.Empty` kterou byste měli použít k označení, že událost neobsahuje žádné další informace.

Pojďme vytvořit třídu, která uvádí soubory v adresáři nebo některé z jeho podadresářů, které následují vzor. Tato součást vyvolá událost pro každý nalezený soubor, který odpovídá vzoru.

Použití modelu událostí poskytuje některé výhody návrhu. Můžete vytvořit více posluchačů událostí, které provádějí různé akce při nalezení hleby souboru. Kombinace různých naslouchacích procesech můžete vytvořit robustnější algoritmy.

Zde je počáteční argument události prohlášení pro nalezení hledaný soubor:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

I když tento typ vypadá jako malý typ pouze pro data, měli`class`byste dodržovat konvenci a vytvořit typ odkazu ( ). To znamená, že argument objekt bude předán odkazem a všechny aktualizace dat budou zobrazeny všemi odběrateli. První verze je neměnný objekt. Měli byste dát přednost tomu, aby vlastnosti v typu argumentu události byly neměnné. Tímto způsobem jeden odběratel nemůže změnit hodnoty dříve, než jiný odběratel vidí. (Existují výjimky, jak uvidíte níže.)  

Dále musíme vytvořit deklaraci události ve třídě FileSearcher. Využití `EventHandler<T>` typu znamená, že není nutné vytvářet další definici typu. Jednoduše použijte obecnou specializaci.

Vyplníme třídu FileSearcher a vyhledáme soubory, které odpovídají vzoru, a vyvoláme správnou událost, když je zjištěna shoda.

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Definování a zvyšování událostí podobných polím

Nejjednodušší způsob, jak přidat událost do třídy, je deklarovat tuto událost jako veřejné pole, jako v předchozím příkladu:

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Vypadá to, že vyhlašuje veřejné pole, což se zdá být špatná objektově orientovaná praxe. Chcete chránit přístup k datům prostřednictvím vlastností nebo metod. I když to může vypadat jako špatný postup, kód generovaný kompilátorem vytvoří obálky tak, aby objekty událostí lze přistupovat pouze bezpečným způsobem. Jediné operace, které jsou k dispozici na události podobné poli, jsou přidání obslužné rutiny:

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

a odstranit obslužnou rutinu:

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Všimněte si, že je místní proměnná pro obslužnou rutinu. Pokud jste použili tělo lambda, odstranění nebude fungovat správně. Bylo by jiné instance delegáta a tiše nedělat nic.

Kód mimo třídu nemůže vyvolat událost, ani nemůže provádět žádné jiné operace.

## <a name="returning-values-from-event-subscribers"></a>Vrácení hodnot od odběratelů událostí

Vaše jednoduchá verze funguje dobře. Přidáme další funkci: Zrušení.

Při zvýšení nalezené události, posluchači by měl být schopen zastavit další zpracování, pokud tento soubor je, že poslední hledal.

Obslužné rutiny události nevracejí hodnotu, takže je třeba komunikovat, že jiným způsobem. Standardní vzor události používá EventArgs objekt zahrnout pole, která odběratelé událostí můžete použít ke komunikaci cancel.

Existují dva různé vzory, které by mohly být použity na základě sémantiky smlouvy Zrušit. V obou případech přidáte logické pole do eventarguments pro událost nalezeného souboru.

Jeden vzor by umožnil jednomu odběrateli zrušit operaci.
Pro tento vzor je nové pole `false`inicializováno na . Každý odběratel jej `true`může změnit na . Poté, co všichni odběratelé viděli událost aktivována, fileSearcher komponenty zkontroluje logickou hodnotu a provede akci.

Druhý vzor by pouze zrušit operaci, pokud všichni předplatitelé chtěli operaci zrušena. V tomto vzoru je inicializováno nové pole označující, že operace by měla být zrušena, a každý odběratel by jej mohl změnit a označit tak, že by operace měla pokračovat.
Poté, co všichni odběratelé viděli událost aktivována, fileSearcher komponenty zkontroluje logické a provede akci. Je jeden další krok v tomto vzoru: komponenta potřebuje vědět, pokud všichni předplatitelé viděli událost. Pokud neexistují žádné odběratelé, pole by znamenat zrušení nesprávně.

Pojďme implementovat první verzi pro tuto ukázku. Do `FileFoundArgs` typu je třeba přidat `CancelRequested` logické pole s názvem:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

Toto nové pole je `false`automaticky inicializováno na výchozí hodnotu logického pole, takže se nezrušíte omylem. Jedinou další změnou komponenty je zkontrolovat příznak po zvýšení události, abyste zjistili, zda některý z účastníků požádal o zrušení:

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

Jednou z výhod tohoto vzoru je, že to není zásadní změna.
Žádný z účastníků požádal o zrušení dříve, a stále nejsou. Žádný z kódu odběratele potřebuje aktualizaci, pokud chtějí podporovat nový protokol zrušení. Je to velmi volně svázané.

Pojďme aktualizovat odběratele tak, aby požaduje zrušení, jakmile najde první spustitelný soubor:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Přidání další deklarace události

Přidáme ještě jednu funkci a předvedeme další jazykové idiomy pro události. Přidáme přetížení `Search` metody, která prochází všechny podadresáře při hledání souborů.

To by mohlo být zdlouhavé operace v adresáři s mnoha podadresářů. Přidáme událost, která se načte, když začne každé nové hledání adresáře. To umožňuje odběratelům sledovat průběh a aktualizovat uživatele, jak postupovat. Všechny vzorky, které jste zatím vytvořili, jsou veřejné. Udělejme z toho vnitřní událost. To znamená, že můžete také vytvořit typy použité pro argumenty interní také.

Začnete vytvořením nové třídy EventArgs odvozené pro hlášení nového adresáře a průběhu.

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Opět můžete postupovat podle doporučení, aby se neměnný typ odkazu pro argumenty události.

Dále definujte událost. Tentokrát použijete jinou syntaxi. Kromě použití syntaxe pole můžete explicitně vytvořit vlastnost pomocí přidávejte a odeberte obslužné rutiny. V této ukázce nebudete potřebovat další kód v těchto obslužných rutin, ale to ukazuje, jak byste je vytvořili.

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

V mnoha ohledech kód, který zde napíšete, odráží kód, který kompilátor generuje pro definice událostí pole, které jste viděli dříve. Událost vytvoříte pomocí syntaxe velmi podobné syntaxi používané pro [vlastnosti](properties.md). Všimněte si, že obslužné rutiny mají různé názvy: `add` a `remove`. Ty jsou volány k odběru události, nebo odhlásit z akce. Všimněte si, že je také nutné deklarovat soukromé záložní pole pro uložení proměnné události. Je inicializován na hodnotu null.

Dále přidáme přetížení `Search` metody, která prochází podadresáře a vyvolává obě události. Nejjednodušší způsob, jak toho dosáhnout, je použít výchozí argument k určení, že chcete prohledávat všechny adresáře:

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

V tomto okamžiku můžete spustit aplikaci, která volá přetížení pro vyhledávání ve všech podadresářích. Na nové `ChangeDirectory` události nejsou žádní odběratelé, ale pomocí `?.Invoke()` idiomu zajistíte, že to funguje správně.

 Přidáme obslužnou rutinu k napsání řádku, který zobrazuje průběh v okně konzoly.

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

Viděli jste vzory, které jsou dodržovány v celém ekosystému .NET.
Učením tyto vzory a konvence, budete psát idiomatické C# a .NET rychle.

Dále uvidíte některé změny v těchto vzorcích v nejnovější verzi rozhraní .NET.

[Další](modern-events.md)
