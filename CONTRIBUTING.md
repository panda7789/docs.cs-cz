---
ms.openlocfilehash: 21266130bd44d45d03f85cdeee9480b7a9944b55
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876937"
---
# <a name="contributing"></a>Přispívání

Děkujeme vám za váš zájem o přispívání do dokumentace k .NET.

> Máme právě přesun Naše pokyny v průvodci pro přispěvatele webu. 
> Nové doprovodné materiály naleznete [Přehled Průvodce pro přispěvatele Microsoftu Docs](https://docs.microsoft.com/contribute/).

Dokument uvádí i proces pro přispívání do článků a ukázky kódu, které jsou hostované na [webu Dokumentace k .NET](https://docs.microsoft.com/dotnet). Příspěvky může být stejně jednoduché jako opravy překlep nebo komplexního, jako nové články.

* [Proces pro přispívání](#process-for-contributing)
* [C# Interaktivní prostředí](#the-c-interactive-experience)
* [Pro a proti](#dos-and-donts)
* [Přispěvatel licenční smlouvy](#contributor-license-agreement)

Toto úložiště obsahuje rámcové dokumentaci pro rozhraní .NET. Webu s dokumentací .NET je sestaven z více úložišť kromě tohle:

- [Ukázky kódu a fragmenty kódu](https://github.com/dotnet/samples)
- [Referenční dokumentace rozhraní API](https://github.com/dotnet/dotnet-api-docs)
- [Odkaz na sadu SDK platformy kompilátoru .NET](https://github.com/dotnet/roslyn-api-docs)

Tady jsou sledovány problémy a úkoly pro všechna tato úložiště.

## <a name="process-for-contributing"></a>Proces pro přispívání

Potřebujete základní znalosti o [Git a webu GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Přeskočte tento krok pro malé změny (například, pokud oprava překlep nebo okamžitě otevřít žádost o přijetí změn k vyřešení problému, který najdete v dokumentaci). Pokud vás zajímá vytváření nového obsahu nebo důkladně pozměňovacího existující obsah, otevřete [problém](https://github.com/dotnet/docs/issues) popisující, co chcete udělat.
Obsah uvnitř **dokumentace** složky je uspořádaný do oddílů, které se projeví v tabulce obsah (TOC). Definujte, kde budou umístěny na téma v obsahu. Získáte zpětnou vazbu na váš návrh.

-nebo-

Můžete také z existující problémy pro které komunitní příspěvky jsou uvítací. [Projekty .NET komunitní přispěvatelé](https://github.com/dotnet/docs/projects/35) obsahuje mnoho pracovních položek, které jsou k dispozici pro komunitní přispěvatelé. V závislosti na vašich zájmech a výši závazku můžete vybrat z problémů v následujících kategoriích:

- **Údržba**. Tato kategorie zahrnuje poměrně jednoduchý příspěvky, jako například opravujete odkazy poškozený nebo není správný, přidání chybějící příklady kódu nebo adresování omezené obsahu problémy. V některých případech může tyto problémy týkají velkého počtu souborů. V takovém případě by měl dejte nám vědět, co jste chtěli pracovat na předtím, než začnete.

- **Obsah aktualizace**. Enormity doc set, obsah jednoduše stanou zastaralými a vyžaduje revizi. Kromě toho pro celou řadu z důvodu nějaký obsah byl duplikován nebo dokonce triplicated. Aktualizace obsahu zahrnuje a ujistěte se, že jednotlivá témata jsou aktuální nebo pozměňovacího obsahu v oblasti funkce pro odstranění duplicity a ujistěte se, že všechny jedinečné obsah se zachová menší dokumentaci nastavit.

- **Vytváření nového obsahu**. Pokud vás zajímá vytváření vlastní téma, seznam těchto problémů, témata, která nám jasné, že jsme chtěli přidat do sady naší dokumentace. Dejte nám vědět, než můžete začít pracovat na téma, i když. Pokud vás zajímá vytváření tématu, který tu není uvedený, otevřete problém. 

Můžete se také podívat na naše [hlásit problémy](https://github.com/dotnet/docs/issues) seznamu a volunteer pracovat na ty, které vás zajímají. Používáme [nahoru pro vezme](https://github.com/dotnet/docs/labels/up-for-grabs) popisku na značky problémy, které jsou otevřené pro příspěvek. 

**Krok 2:** Fork `dotnet/docs`, `dotnet/samples` nebo `dotnet/dotnet-api-docs` úložišť jako potřeby a vytvořit větev pro vaše změny.

Pro malé změny můžete použít webového rozhraní na Githubu. Stačí kliknout **upravte soubor ve svém forku tohoto projektu** na soubor, který chcete změnit. GitHub vytvoří novou větev pro vás, když odešlete změny.

**Krok 3:** Proveďte změny v této nové větvi.

Pokud je nové téma, můžete to [soubor šablony](./styleguide/template.md) jako výchozí bod. Obsahuje pokyny pro zápis a také vysvětluje metadat, vyžaduje se pro každý článek, jako je například informace o autorovi.

Přejděte do složky, která odpovídá umístění obsahu pro váš článek v kroku 1.
Tato složka obsahuje soubory Markdown pro všechny články v této části.
V případě potřeby vytvořte novou složku pro soubory pro obsah. Je volána v hlavním článku pro daný oddíl *index.md*.
Pro obrázky a další statické prostředky, vytvořte podsložku nazvanou **media** ve složce, která obsahuje váš článek, pokud ještě neexistuje. Uvnitř **média** složce vytvořte podsložku s názvem článku (s výjimkou souboru indexu).
Zahrnout větší ukázky *ukázky* složku v kořenovém adresáři úložiště.

Ujistěte se, postupujte podle lze patřičnou syntaxi Markdown. Další informace najdete v tématu [průvodce správným stylem](./styleguide/template.md).

### <a name="example-structure"></a>Ukázková struktura

```
docs
  /about
  /core
    /porting
      porting-overview.md
      /media
        /porting-overview
            portability_report.png
```

**Krok 4:** Odeslat žádost o přijetí změn požádat o (o přijetí změn) z vaší větve do `dotnet/docs/master`.

Vaše žádost o přijetí změn by *vždy* cílové hlavní větvi. Měli byste *nikdy* otevřete žádost o přijetí změn živé větve cílí.

Každé žádosti o přijetí změn by měl obvykle adres jedním problémem po jednom. Žádosti o přijetí změn můžete změnit jeden nebo více souborů. Pokud jste adresování více opravy na jiné soubory, jsou upřednostňované samostatné žádosti o přijetí změn.

Pokud vaše žádost o přijetí změn řeší stávající problém, přidejte `Fixes #Issue_Number` – klíčové slovo na zprávu potvrzení nebo popis žádosti o přijetí změn. Tímto způsobem, problém je automaticky uzavřena žádosti o přijetí změn se sloučí. Další informace najdete v tématu [uzavírá chyby prostřednictvím zprávy potvrzení](https://help.github.com/articles/closing-issues-via-commit-messages/).

Tým .NET zkontrolujte vaše žádost o přijetí změn a umožňují zjistit, pokud jsou nezbytné, aby ho schválit aktualizace/změny.

**Krok 5:** Proveďte potřebné změny do vaší větve, jak je popsáno s týmem.

Programu dojde ke sloučení vaší žádosti o přijetí změn do hlavní větve po použití zpětnou vazbu a vaše schválení.

Některé čím dál jsme nasdílení změn všechna potvrzení změn z hlavní větve do živé větve a pak budete moci zobrazit svůj příspěvek, za provozu na https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Přispívání do vzorků

Provedeme následující rozlišení pro kód, který existuje v našem úložišti:

- ukázky: čtenáři můžete stáhnout a spuštění ukázek. Všechny ukázky by měl být kompletních aplikací nebo knihovnami. Pokud vzorovým kódem se vytvoří knihovnu, měl by obsahovat testování částí nebo aplikaci, která umožňuje uživatelům spouštět kód.

- fragmenty kódu: ilustrují menší koncept nebo úkolu. Jsou kompilovány, ale nejsou určeny k dokončení aplikace.

Všechny odpovídající kód [dotnet/samples](https://github.com/dotnet/samples) úložiště. Pracujeme na tom k modelu, kde naše ukázky strukturu složek odpovídá strukturu složek naší dokumentace. Standardy, které budeme postupovat podle jsou:

- Na nejvyšší úrovni *fragmenty* složka obsahuje fragmenty kódu pro malé a soustředěné ukázky.
- Ukázky referenční dokumentace rozhraní API se ve složce podle tohoto vzoru: *fragmenty /\<jazyk > /api/\<oboru názvů > /\<apiname >*.
- Složky nejvyšší úrovně v shodovat s další složky nejvyšší úrovně *dokumentace* úložiště. Například má úložiště dokumentů *machine-learning/kurzy* složky a ukázky pro službu machine learning kurzy jsou v *ukázky/machine-learning/kurzy* složky.

Kromě toho všechny ukázky v části *core* a *standardní* složky by měl sestavit a spustit na všech platformách podporovaných aplikací .NET Core. Náš systém sestavení CI, která vynutí. Na nejvyšší úrovni *framework* složka obsahuje ukázky, které jsou pouze integrované a ověřit na Windows.

Možná budeme dále tyto adresáře, protože úložiště dokumentů přidá nový obsah. Například přidáme Xamarin adresářů, jako je třeba `xamarin-ios` a `xamarin-android` adresáře.

By měl obsahovat každou úplnou ukázku, kterou vytvoříte *readme.md* souboru. Tento soubor by měl obsahovat krátký popis ukázky (jeden nebo dva odstavce). Vaše *readme.md* by vám měl sdělit čtenáři co se dozvíte, ve kterých tuto ukázku. *Readme.md* soubor by měl také obsahovat odkaz na dokument za provozu na [webu Dokumentace k .NET](https://docs.microsoft.com/dotnet/welcome).
Pokud chcete zjistit, kde se daný soubor v úložišti mapuje na dané lokalitě, nahraďte `/docs` v cestě k úložišti s `https://docs.microsoft.com/dotnet`.

Vaše téma se bude také obsahovat odkazy na ukázky. Přímý odkaz na složku ukázky na Githubu.

Další informace najdete v tématu [ukázky Readme](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>C# Interaktivní prostředí

Krátké ukázky kódu v C# můžete použít `csharp-interactive` značku jazyka k určení C# ukázky, která běží v prohlížeči. (Ukázky použití vloženého kódu `csharp-interactive` označit, pro zahrnuté ze zdroje, fragment kódu používá `code-csharp-interactive` značka.) Tyto ukázky kódu zobrazit okno kódu a oknem výstupu v následujícím článku. V okně výstupu se zobrazí všechny výstupy z provádění interaktivního kódu, jakmile uživatel má spuštění ukázky. 

C# Interaktivní změní, jak Pracujeme s ukázkami. Návštěvníci můžete spuštění ukázky pro zobrazení výsledků. Řadě faktorů pomůže určit, pokud ukázkový nebo odpovídající text by měl obsahovat informace o výstupu.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kdy se má zobrazit očekávaný výstup bez spuštění ukázky

- Články, které jsou určené pro začátečníky by měla poskytnout výstup tak, aby se čtenáři můžete porovnat výstup své práce očekávané odpovědí.
- Ukázky, ve kterém je nedílnou součástí tématu výstupu by se zobrazit tento výstup. Například články o formátovaný text by měl zobrazit v textovém formátu bez spuštění ukázky.
- Když vzorku a očekávaný výstup je krátký, zvažte zobrazující výstup. Uloží hodně času.
- Články s vysvětlením, jak aktuální jazykové verze invariantní jazykovou verzi vliv výstup nebo by měl vysvětlit očekávaný výstup. Interaktivní okno REPL (čtení vyhodnotit smyčka tisku) běží na hostiteli se systémem Linux. Výchozí jazykovou verzi a invariantní jazyková verze generovat různé výstup na různé operační systémy a počítače. Článek by měl v systémech Windows, Linux a Mac popisují výstup.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kdy se mají vyloučit očekávaný výstup z ukázky 

- Články, ve kterém ukázka generuje větší výstup, který by neměl obsahovat v komentářích. Po spuštění ukázky zakrývá kód.
- Články, kde ukázce tématu, ale výstup není celočíselný k jeho pochopení. Například kód, který spustí dotaz LINQ vysvětlují syntaxe dotazu a pak zobrazí všechny položky v kolekci výstup.

## <a name="dos-and-donts"></a>Pro a proti

Následující seznam uvádí některé hlavní pravidla, které jste měli vzít v úvahu při při přispívání do dokumentace k .NET:

- **Není** překvapí nám s žádostí o přijetí změn velké. Místo toho založte problém a vytvořit diskusi tak jsme můžou dohodnout na směru, než investovat velké množství času.
- **PROVEĎTE** čtení [průvodce správným stylem](./styleguide/template.md) a [pro hlasové hovory a tón](./styleguide/voice-tone.md) pokyny.
- **PROVEĎTE** použít [šablony](./styleguide/template.md) soubor jako výchozí bod své práce.
- **PROVEĎTE** vytvořit samostatné větvi ve vašem forku před zahájením práce v článcích.
- **PROVEĎTE** postupujte [pracovního postupu GitHub Flow](https://guides.github.com/introduction/flow/).
- **PROVEĎTE** blogu a tweet (nebo cokoli jiného) vaše příspěvky, často!

> Poznámka: můžete si všimnout, že některá témata jsou aktuálně po všech pokynů tady zadané a na [průvodce správným stylem](./styleguide/template.md) také. Pracujeme dosahování konzistence v celém webu. Zkontrolujte seznam [hlásit problémy](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) jsme se aktuálně sledování pro tento konkrétní cíl.

## <a name="contributor-license-agreement"></a>Přispěvatel licenční smlouvy

Musíte podepsat [.NET Foundation licenční smlouvy (CLA)](https://cla.dotnetfoundation.org) předtím, než se vaše žádost o přijetí změn sloučí. Toto je jednorázový požadavek pro projekty .NET Foundation. Další informace o [licenční smlouvy (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) v encyklopedii Wikipedia.

Smlouva: [net-foundation příspěvek licence agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Není nutné k podepsání smlouvy předem. Můžete klonování forku a odeslání vaší žádosti o přijetí změn jako obvykle. Když se vaše žádost o přijetí změn, je klasifikován sloupcem robotem. Pokud je jednoduchá změna (například jste opravili překlep), pak žádosti o přijetí změn je označena `cla-not-required`. V opačném případě je klasifikován tak `cla-required`. Po podepsání CLA aktuální a všechny budoucí žádosti jsou označeny jako `cla-signed`.
