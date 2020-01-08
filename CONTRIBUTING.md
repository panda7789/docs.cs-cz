---
ms.openlocfilehash: 469be53e14c42775f21ef1ef815becd5cad03a97
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336725"
---
# <a name="contributing"></a>Přispívání

Děkujeme za váš zájem o psaní příspěvků do dokumentace k .NET.

> Právě probíhá přesouvání našich pokynů do Průvodce příspěvkem v rámci nejrůznějších webů.
> Nové doprovodné materiály najdete v tématu [Přehled průvodce Microsoft Docsem přispěvatelem](https://docs.microsoft.com/contribute/).

Dokument popisuje proces pro přispívání do článků a ukázek kódu, které jsou hostovány na [webu dokumentace rozhraní .NET](https://docs.microsoft.com/dotnet). Příspěvky můžou být jednoduché, třeba oprava překlepu, nebo složité, třeba nové články.

- [DOs a DON'Ts](#dos-and-donts)
- [Proces pro přispívání](#process-for-contributing)
- [C# Interaktivní prostředí](#the-c-interactive-experience)
- [Licenční smlouva přispěvatele](#contributor-license-agreement)

Toto úložiště obsahuje koncepční dokumentaci pro .NET. Kromě tohoto nástroje je web dokumentace .NET sestaven z více úložišť:

- [Ukázky kódu a fragmenty kódu](https://github.com/dotnet/samples) Problémy a úkoly pro toto úložiště jsou sledovány v [dotnet/docs/problémech](https://github.com/dotnet/docs/issues).
- [Reference k rozhraní .NET API](https://github.com/dotnet/dotnet-api-docs) Problémy a úkoly pro toto úložiště jsou sledovány v příkazu [dotnet/dotnet-API-docs/problémy](https://github.com/dotnet/dotnet-api-docs/issues).
- [Referenční informace k sadě .NET Compiler Platform SDK](https://github.com/dotnet/roslyn-api-docs) Problémy a úkoly pro toto úložiště jsou sledovány v [dotnet/docs/problémech](https://github.com/dotnet/docs/issues).

## <a name="dos-and-donts"></a>DOs a DON'Ts

V následujícím seznamu najdete několik pravidel, kterými byste se při psaní příspěvků do dokumentace k .NET měli řídit:

- **NEPŘEKVAPUJTE NÁS** rozsáhlými žádostmi o přijetí změn. Než budete něčemu věnovat hodně času, zadejte problém a zahajte diskusi, abychom se mohli předem dohodnout na postupu. Pro hromadné změny Přerušte práci na menší PR (až 100 souborů). Tato směrnice se důrazně doporučuje, pokud vaše žádost o přijetí změn nepostupuje podle následujících pokynů.
- **Podívejte se** [na aktuální problémy](https://github.com/dotnet/docs/labels/up-for-grabs) , které jsou k dispozici pro návrhy na úlohy.
- Pro každý úkol vytvořte jednu žádost o přijetí **změn** . PR, které zahrnují více nesouvisejících změn, je mnohem obtížnější kontrolovat. Tím se zpozdí recenze a sloučení pr. Tento návod se vztahuje i na recenze. nedoporučujeme navrhovat nesouvisející změny v recenzích. požádáme, aby kontroly komunity dodržovaly tyto zásady.
- Zadejte jasný popis práce v žádosti o přijetí **změn** . Řekněte nám, co se změnilo a proč. Výchozí popis "Update article.md" není pro kontrolory užitečný.
- **Neodesílat PR** jenom pro změny stylu bez předchozí diskuze. Tyto pry mají včas kontrolu nad přesností a jejich sloučení často způsobuje, že sloučení koliduje s jinými důležitými aktualizacemi. Pracujeme na tom, abychom s dodržováním konzistentního stylu, ale vyrovnáváme to, jak pracovat s dalšími úkoly. V případě, že provedeme hlavní aktualizace z jiných důvodů, se články přenesou do souladu se stylem.
- **Přečtěte si** článek [Průvodce stylem](./styleguide/template.md) a pokyny pro [hlasové a tónové](./styleguide/voice-tone.md) funkce. Nové přídavky by měly dodržovat tyto pokyny.
- **VYTVOŘTE** ve svém forku samostatnou větev dřív, než začnete pracovat na článcích.
- **DODRŽUJTE**[pracovní postup v toku GitHubu](https://guides.github.com/introduction/flow/).
- **BLOGUJTE A TWEETUJTE** (nebo jinak komunikujte) o svých příspěvcích co nejčastěji.

Tyto pokyny nám pomohou respektovat každý čas. Spousta lidí přispívá do těchto úložišť. Podle těchto pokynů usnadňujeme včas kontrolu a sloučení žádosti o přijetí změn. Tyto postupy minimalizují konflikty s PR od jiných členů komunity i z našeho týmu. Vzhledem k tomu, že PR, které tyto pokyny nedodržují, často způsobují další práci pro členy USA a komunity, mohou být tyto PR odmítnuty. Pokud chcete výjimku, Začněte vytvořením problému.

> Poznámka: můžete si všimnout, že některá témata aktuálně nejsou v současné době podle všech uvedených pokynů a také v [Průvodci styly](./styleguide/template.md) . Pracujeme na tom, aby měl web konzistentní podobu.

## <a name="process-for-contributing"></a>Proces pro přispívání

Budete potřebovat základní porozumění [Gitu a GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Přeskočit tento krok pro malé změny (například pokud opravíte překlep nebo hned otevřete žádost o přijetí změn, které řeší problém, který najdete v dokumentaci). Pokud se zajímáte o psaní nového obsahu nebo o úplné přepracování stávajícího obsahu, otevřete [problém](https://github.com/dotnet/docs/issues) a popište v něm, co chcete dělat.
Obsah ve složce *docs* je uspořádaný do oddílů, které odpovídají tabulce s obsahem. Určete, kde se má téma v obsahu nacházet. Získejte ke svému návrhu zpětnou vazbu.

-nebo-

Vyberte některý ze stávajících problémů, ke kterým jsou vítané komunitní příspěvky. [Projekty pro přispěvatele komunity .NET](https://github.com/dotnet/docs/projects/35) obsahují mnoho pracovních položek, které jsou k dispozici pro komunitní přispěvatele. Podle svých zájmů a rozsahu své účasti si můžou vybrat z problémů uspořádaných do následujících kategorií:

- **Údržba:** Tato kategorie obsahuje relativně jednoduché příspěvky, třeba opravu nefunkčních nebo nesprávných odkazů, přidání chybějících ukázek kódu nebo řešení menších problémů týkajících se obsahu. V některých případech se tyto problémy můžou týkat velkého počtu souborů. V takovém případě nám dejte předem vědět, na čem byste chtěli začít pracovat.

- **Aktualizace obsahu:** Vzhledem k obrovskému rozsahu dokumentace se může snadno stát, že je obsah zastaralý a vyžaduje revizi. Kromě toho z nejrůznějších důvodů byl nějaký obsah duplikován nebo dokonce triplicated. Při aktualizaci obsahu je potřeba ověřit, jestli jsou jednotlivá témata aktuální, případně revidovat obsah funkční oblasti tak, aby se vyloučily duplicity. Je také potřeba zajistit, aby byl veškerý jedinečný obsah uchováván v menší sadě dokumentace.

- **Tvorba nového obsahu:** Pokud se zajímáte o tvorbu vlastních nových témat, najdete v těchto problémech seznam témat o kterých víme, že bychom je chtěli přidat do naší sady dokumentace. Přesto nám dejte předem vědět, než na tématu začnete pracovat. Pokud máte zájem o napsání tématu, které zde není, otevřete nový problém.

Můžete si také prohlédnout seznam [otevřených problémů](https://github.com/dotnet/docs/issues) a dobrovolně pracovat na těch, které vás zajímají. Pomocí popisku [up-for-drapáky](https://github.com/dotnet/docs/labels/up-for-grabs) označíte problémy otevřené pro příspěvky.

**Krok 2:** Rozvětvení `dotnet/docs`, `dotnet/samples` nebo `dotnet/dotnet-api-docs` úložišť podle potřeby a vytvoření větve pro změny.

Pro malé změny můžete použít webové rozhraní GitHubu. Jednoduše klikněte na soubor, ve kterém se nachází **ve větvi tohoto projektu** , na soubor, který chcete změnit. GitHub vytvoří novou větev při odeslání změn.

**3. krok:** Proveďte změny v této nové větvi.

Pokud je téma nové, použijte jako výchozí bod tento [soubor se šablonou](./styleguide/template.md). Obsahuje pokyny k psaní a vysvětluje metadata, která jsou ke každému článku potřeba, například informace o autorovi.

Přejděte do složky, která odpovídá místu v obsahu, které jste pro svůj článek vybrali v prvním kroku.
V této složce jsou soubory v jazyce Markdown všech článků v tomto oddílu.
Pokud je to potřeba, vytvořte novou složku, do které umístíte soubory se svým obsahem. Hlavní článek v tomto oddílu se jmenuje *index.md*.
Pro obrázky a další statické prostředky vytvořte podsložku nazvanou *media* (pokud ještě neexistuje) a dejte ji do složky se svým článkem. Ve složce *media* vytvořte podsložku s názvem článku (kromě souboru indexu).
Do složky *Samples* v kořenovém adresáři úložiště přidejte větší vzorky.

Dodržujte správnou syntaxi jazyka Markdown. Další informace najdete v příručce k [stylu](./styleguide/template.md).

### <a name="example-structure"></a>Příklad struktury

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

**Krok 4:** Odešlete žádost o přijetí změn z větve `dotnet/docs/master`, `dotnet/dotnet-api-docs/master`nebo `dotnet/samples/master`.

Vaše žádost o přijetí změn by měla *vždycky* cílit na výchozí větev úložiště (Pokud nepracujete na větvi vydané verze). Pro dotnet/Docs je hlavní větev výchozí větev. V případě lokalizovaných úložišť je výchozím nastavením jedna živá větev. *Nikdy* byste neměli otevřít žádost o přijetí změn, která se zaměřuje na živou větev v dotnet/docs.

Každá žádost o přijetí změn by měla vždy řešit jenom jeden problém. Žádost o přijetí změn se může týkat změny jednoho nebo několika souborů. Pokud řešíte více oprav, které se týkají různých souborů, použijte raději samostatné žádosti o přijetí změn.

Pokud vaše žádost o přijetí změn řeší existující problém, přidejte klíčové slovo `Fixes #Issue_Number` do zprávy potvrzení nebo popisu žádosti o přijetí změn. Když ho přidáte, problém se po sloučení žádosti o přijetí změn automaticky uzavře. Další informace najdete v tématu o [zavírání problémů prostřednictvím zpráv o potvrzení](https://help.github.com/articles/closing-issues-via-commit-messages/).

Tým .NET zkontroluje vaši žádost o přijetí změn a bude vás informovat, jestli jsou před schválením potřeba další aktualizace nebo změny.

**5. krok:** Proveďte ve větvi potřebné aktualizace, které jste projednali s týmem.

Jakmile jsou připomínky zapracované a změny schválené, sloučí správci vaši žádost o přijetí změn s hlavní větví.

Na některém tempo zadáváme všechna potvrzení z hlavní větve do živé větve a potom budete moct svůj příspěvek sledovat na https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Příspěvky do ukázek kódu

Kód, který je v úložišti, rozdělujeme do dvou skupin:

- Ukázky: Čtenáři si je můžou stáhnout a spustit. Všechny ukázky musí představovat celé aplikace nebo knihovny. Pokud ukázka vytvoří knihovnu, musí obsahovat testy jednotek nebo aplikaci, která uživatelům umožní kód spustit.

- Fragmenty kódu: Ilustrují menší prvek nebo úlohu. Jsou kompilovatelné, ale nejde o kompletní aplikace.

Veškerý kód je v úložišti [dotnet/samples](https://github.com/dotnet/samples). Pracujeme na modelu, ve kterém bude struktura složek s ukázkami odpovídat struktuře složek dokumentace. Dodržujeme tato pravidla:

- Nejvyšší složka *snippets* obsahuje fragmenty kódu, které představují malé, jednoúčelové ukázky.
- Ukázky odkazů na rozhraní API byly ve složce, která následuje po tomto vzoru: *fragmenty/\<jazyk >/api/\<obor názvů >/\<apiname >* .
- Další složky nejvyšší úrovně odpovídají nejvyšším složkám v úložišti *docs*. Například v úložišti docs je složka *machine-learning/tutorials* a ukázky ke kurzům věnovaným strojovému učení jsou ve složce *samples/machine-learning/tutorials*.

Navíc všechny ukázky ve složkách *core* a *standard* se musí dát vytvořit a spustit na všech platformách, které podporuje .NET Core. To zajistí náš systém sestavení CI. Nejvyšší složka *framework* obsahuje ukázky, které jsou vytvořené a ověřené jen ve Windows.

Tyto adresáře můžeme rozšířit, protože úložiště docs přidává nový obsah. Například přidáme adresáře Xamarin, jako je `xamarin-ios` a `xamarin-android` adresáře.

Každá hotová ukázka, kterou vytvoříte, má obsahovat soubor *readme.md*. V tomto souboru by měl být krátký popis ukázky (jeden nebo dva odstavce). Ze souboru *readme.md* by se čtenáři měli dozvědět, co se naučí, když si tuto ukázku vyzkouší. V souboru *readme.md* má být také odkaz na živý dokument na [webu s dokumentací k .NET](https://docs.microsoft.com/dotnet/welcome).
Pokud chcete zjistit mapování daného souboru v úložišti na tento web, nahraďte `/docs` v cestě k úložišti adresou `https://docs.microsoft.com/dotnet`.

Odkaz na ukázku bude i ve vašem tématu. Vytvořte odkaz přímo na složku s ukázkou na GitHubu.

Další informace najdete v [souboru Readme ukázek](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Interaktivní prostředí jazyka C#

Krátké ukázky kódu v jazyce C# používají jazykovou značku `csharp-interactive`, která znamená, že ukázku v jazyce C# můžete spustit v prohlížeči (Vzorky vloženého kódu používají značku `csharp-interactive` pro fragmenty kódu, které jsou součástí zdroje, použijte značku `code-csharp-interactive`.) Tyto ukázky kódu zobrazují okno kódu a výstupní okno v článku. V okně výstupu se zobrazuje výstup spuštěného interaktivního kódu po spuštění ukázky uživatelem.

Prostředí kompilačního nástroje C# Interactive mění způsob práce s ukázkami. Návštěvníci můžou ukázku spustit a podívat se na výsledky. To, jestli mají být v ukázce nebo v příslušném textu i informace o výstupu, záleží na řadě okolností.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kdy zobrazit očekávaný výstup bez spuštění ukázky

- Výstup by měly obsahovat články, které jsou určené začátečníkům, aby čtenáři mohli porovnat svůj výstup s očekávanou odpovědí.
- Výstup by také měl být v ukázkách, ve kterých je nedílnou součástí tématu. Například v článcích o formátovaném textu by se měl zobrazovat formát textu bez spouštění ukázky.
- Zobrazení výstupu byste měli zvážit i v případě, že ukázka i očekávaný výsledek jsou krátké. Trochu to šetří čas.
- Očekávaný výsledek by také měl být popsaný v článcích, které vysvětlují vliv aktuální jazykové verze nebo invariantní jazykové verze na výstup. Interaktivní prostředí REPL (Read Evaluate Print Loop) běží na linuxovém hostiteli. Výchozí jazyková verze a invariantní jazyková verze vytvářejí v různých operačních systémech a na různých počítačích odlišné výstupy. V článku by měl být popsaný výstup v systémech Windows, Linux a Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kdy z ukázky očekávaný výstup vyloučit

- Pokud je v článcích ukázka, která generuje větší výstup, neměl by být v komentáři. Kód je po spuštění ukázky nepřehledný.
- Pokud článek předvádí nějaké téma, ale výstup není k jeho pochopení nezbytně nutný. Pokud třeba kód spustí dotaz LINQ kvůli vysvětlení syntaxe dotazu a pak zobrazí každou položku výstupní kolekce.

## <a name="contributor-license-agreement"></a>Licenční smlouva přispěvatele

Před sloučením žádosti o přijetí změn musíte podepsat [licenční smlouvu s přispěvatelem (CLA) pro .NET Foundation](https://cla.dotnetfoundation.org). Jde o jednorázový požadavek u projektů pro .NET Foundation. Další informace o [licenční smlouvě s přispěvatelem (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) najdete na wikipedii.

Smlouva: [net-foundation-contribution-license-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Smlouvu nemusíte podepisovat předem. Žádosti o přijetí změn můžete obvyklým způsobem klonovat, odeslat nebo můžete vytvořit fork. Vytvořenou žádost o přijetí změn klasifikuje robot CLA. Pokud je změna triviální (například jste opravili překlep), je žádost o přijetí změn označená `cla-not-required`. V ostatních případech bude zařazena jako `cla-required`. Po podpisu smlouvy CLA budou všechny současné i budoucí žádosti o přijetí změn označeny `cla-signed`.
