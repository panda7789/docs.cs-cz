---
ms.openlocfilehash: e5da9a98e8725880223df3737dc60f773db8d20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79141130"
---
# <a name="contributing"></a>Přispívání

Děkujeme za váš zájem o psaní příspěvků do dokumentace k .NET.

> Jsme v procesu přesunutí našich pokynů do průvodce příspěvkem pro celý web.
> Nové pokyny najdete v průvodci [přispěvateli aplikace Microsoft Docs](https://docs.microsoft.com/contribute/).

Dokument zahrnuje proces přispívání do článků a ukázky kódu, které jsou hostovány na [webu dokumentace .NET](https://docs.microsoft.com/dotnet). Příspěvky můžou být jednoduché, třeba oprava překlepu, nebo složité, třeba nové články.

- [Co a DON'Ts](#dos-and-donts)
- [Proces přispívání](#process-for-contributing)
- [Interaktivní prostředí jazyka C#](#the-c-interactive-experience)
- [Licenční smlouva přispěvatele](#contributor-license-agreement)

Toto úložiště obsahuje koncepční dokumentaci pro rozhraní .NET. Dokumentační web .NET je sestaven z více úložišť kromě tohoto:

- [Ukázky kódu a úryvky](https://github.com/dotnet/samples) Problémy a úkoly pro toto úložiště jsou sledovány v [dotnet/docs/issues](https://github.com/dotnet/docs/issues).
- [Odkaz rozhraní .NET API](https://github.com/dotnet/dotnet-api-docs) Problémy a úkoly pro toto úložiště jsou sledovány v [dotnet/dotnet-api-docs/issues](https://github.com/dotnet/dotnet-api-docs/issues).
- [Odkaz na platformu kompilátoru rozhraní .NET](https://github.com/dotnet/roslyn-api-docs) Problémy a úkoly pro toto repo jsou sledovány v [dotnet/docs/issues](https://github.com/dotnet/docs/issues).

### <a name="contributing-to-international-content"></a>Přispívání k mezinárodnímu obsahu

Příspěvky na strojově přeložený (MT) obsah nejsou v současné době přijímány. Ve snaze zlepšit kvalitu obsahu MT jsme přešli na modul Neural MT. Přijímáme a podporujeme příspěvky pro obsah HT (Human Translated), který se používá k trénování motoru Neural MT. Takže v průběhu času, příspěvky k obsahu HT zlepší kvalitu obou HT a MT. Témata MT budou mít prohlášení o vyloučení odpovědnosti, které uvádí, že součástí tématu může být MT a tlačítko **Upravit** nebude zobrazeno jako zakázané.

## <a name="dos-and-donts"></a>Co a DON'Ts

V následujícím seznamu najdete několik pravidel, kterými byste se při psaní příspěvků do dokumentace k .NET měli řídit:

- **NEPŘEKVAPUJTE NÁS** rozsáhlými žádostmi o přijetí změn. Než budete něčemu věnovat hodně času, zadejte problém a zahajte diskusi, abychom se mohli předem dohodnout na postupu. U hromadných změn rozdělte práci na menší záznamy (až 100 souborů). Tato směrnice se důrazně doporučuje, pokud vaše PR nedodržuje následující pokyny.
- **DO** podívejte se na aktuální [až k mání](https://github.com/dotnet/docs/labels/up-for-grabs) otázky pro návrhy na úkoly.
- **Do** vytvořit jeden PR pro každý úkol. Prs, které obsahují více nesouvisejících změn je mnohem těžší zkontrolovat. To zpožďuje recenze a slučování předstupujících. Tyto pokyny platí i pro recenze: snažíme se nenavrhovat nesouvisející změny v recenzích; žádáme, aby komunitní recenze dodržovaly tyto pokyny.
- **DO** poskytnout jasný popis práce ve vašem PR. Řekněte nám, co se změnilo a proč. Výchozí popis "aktualizace article.md" není pro recenzenty užitečný.
- **Neodesílejte** předpisované záznamy o změnách pouze ve stylu bez předchozí diskuse. Tyto prs trvat více času na kontrolu přesnosti a jejich sloučení často způsobí sloučení konflikty s jinými důležitými aktualizacemi. Pracujeme na dodržování konzistentní styl, ale jsme vyvážení, které pracují s jinými úkoly. Články jsou uvedeny do stylu shody, když děláme hlavní aktualizace z jiných důvodů.
- **DO** číst [styl průvodce](./styleguide/template.md) a hlas a [tón](./styleguide/voice-tone.md) pokyny. Nové dodatky by se měly řídit těmito pokyny.
- **VYTVOŘTE** ve svém forku samostatnou větev dřív, než začnete pracovat na článcích.
- **DODRŽUJTE**[pracovní postup v toku GitHubu](https://guides.github.com/introduction/flow/).
- **BLOGUJTE A TWEETUJTE** (nebo jinak komunikujte) o svých příspěvcích co nejčastěji.

Tyto pokyny nám pomáhají respektovat čas každého z nás. Mnoho lidí přispívá k těmto úložištím. Dodržování těchto pokynů nám usnadní včas kontrolu a sloučení vašeho PR. Tyto postupy minimalizují konflikty s předkami od ostatních členů komunity a našeho týmu. Vzhledem k tomu, že žádosti o informace, které tyto pokyny nedodržují, často způsobují práci navíc pro nás a členy komunity, mohou být tyto žádosti o žádosti zamítnuty. Pokud chcete výjimku, začněte vytvořením problému.

> Poznámka: Možná jste si všimli, že některá témata nejsou v současné době po všech pokynů uvedených zde a na [styl průvodce](./styleguide/template.md) stejně. Pracujeme na tom, aby měl web konzistentní podobu.

## <a name="process-for-contributing"></a>Proces přispívání

Potřebujete základní znalostgitu [a GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Přeskočit tento krok pro malé změny (například pokud opravujete překlep nebo okamžitě otevření žádosti o přijetí změn k řešení problému, který najdete v dokumentech). Pokud se zajímáte o psaní nového obsahu nebo o úplné přepracování stávajícího obsahu, otevřete [problém](https://github.com/dotnet/docs/issues) a popište v něm, co chcete dělat.
Obsah ve složce *docs* je uspořádaný do oddílů, které odpovídají tabulce s obsahem. Určete, kde se má téma v obsahu nacházet. Získejte ke svému návrhu zpětnou vazbu.

-nebo-

Vyberte některý ze stávajících problémů, ke kterým jsou vítané komunitní příspěvky. [Projekty pro přispěvatele komunity .NET](https://github.com/dotnet/docs/projects/35) uvádí mnoho pracovních položek, které jsou k dispozici pro přispěvatele komunity. Podle svých zájmů a rozsahu své účasti si můžou vybrat z problémů uspořádaných do následujících kategorií:

- **Údržba**. Tato kategorie obsahuje relativně jednoduché příspěvky, třeba opravu nefunkčních nebo nesprávných odkazů, přidání chybějících ukázek kódu nebo řešení menších problémů týkajících se obsahu. V některých případech se tyto problémy můžou týkat velkého počtu souborů. V takovém případě nám dejte předem vědět, na čem byste chtěli začít pracovat.

- **Aktualizace obsahu:** Vzhledem k obrovskému rozsahu dokumentace se může snadno stát, že je obsah zastaralý a vyžaduje revizi. Kromě toho, z různých důvodů, byl nějaký obsah duplikován nebo dokonce triplicated. Při aktualizaci obsahu je potřeba ověřit, jestli jsou jednotlivá témata aktuální, případně revidovat obsah funkční oblasti tak, aby se vyloučily duplicity. Je také potřeba zajistit, aby byl veškerý jedinečný obsah uchováván v menší sadě dokumentace.

- **Tvorba nového obsahu:** Pokud se zajímáte o tvorbu vlastních nových témat, najdete v těchto problémech seznam témat o kterých víme, že bychom je chtěli přidat do naší sady dokumentace. Přesto nám dejte předem vědět, než na tématu začnete pracovat. Pokud máte zájem o napsání tématu, které zde není, otevřete nový problém.

Můžete si také prohlédnout seznam [otevřených problémů](https://github.com/dotnet/docs/issues) a dobrovolně pracovat na těch, které vás zajímají. Štítek [up-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) používáme k označení problémů otevřených pro příspěvek.

**Krok 2:** Rozvětvení `dotnet/docs` `dotnet/samples` nebo `dotnet/dotnet-api-docs` repos podle potřeby a vytvořit větev pro změny.

Pro malé změny můžete použít webové rozhraní GitHubu. Jednoduše klikněte na **upravit soubor v rozhledce tohoto projektu** na soubor, který chcete změnit. GitHub vytvoří novou větev pro vás při odeslání změny.

**3. krok:** Proveďte změny v této nové větvi.

Pokud je téma nové, použijte jako výchozí bod tento [soubor se šablonou](./styleguide/template.md). Obsahuje pokyny k psaní a vysvětluje metadata, která jsou ke každému článku potřeba, například informace o autorovi.

Přejděte do složky, která odpovídá místu v obsahu, které jste pro svůj článek vybrali v prvním kroku.
V této složce jsou soubory v jazyce Markdown všech článků v tomto oddílu.
Pokud je to potřeba, vytvořte novou složku, do které umístíte soubory se svým obsahem. Hlavní článek v tomto oddílu se jmenuje *index.md*.
Pro obrázky a další statické prostředky vytvořte podsložku nazvanou *media* (pokud ještě neexistuje) a dejte ji do složky se svým článkem. Ve složce *media* vytvořte podsložku s názvem článku (kromě souboru indexu).
Zahrnout větší vzorky ve složce *ukázky* pod kořenem repo.

Dodržujte správnou syntaxi jazyka Markdown. Další informace naleznete v [průvodci stylem](./styleguide/template.md).

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

**Krok 4:** Odešlete žádost o přijetí vyžádat z větve do `dotnet/docs/master`aplikace , `dotnet/dotnet-api-docs/master`, nebo `dotnet/samples/master`.

Vaše PR by měla *vždy* cílit na výchozí větev úložiště (pokud nepracujete na větev vydání). Pro dotnet/docs je hlavní větev výchozí větev. Pro lokalizované repozitáře je výchozí větev. *Nikdy* byste neměli otevírat PR, který cílí na živou větev na dotnet/docs.

Každá žádost o přijetí změn by měla vždy řešit jenom jeden problém. Žádost o přijetí změn se může týkat změny jednoho nebo několika souborů. Pokud řešíte více oprav, které se týkají různých souborů, použijte raději samostatné žádosti o přijetí změn.

Pokud vaše PR řeší existující problém, přidejte `Fixes #Issue_Number` klíčové slovo do zprávy o potvrzení nebo popisu PR. Když ho přidáte, problém se po sloučení žádosti o přijetí změn automaticky uzavře. Další informace najdete v tématu o [zavírání problémů prostřednictvím zpráv o potvrzení](https://help.github.com/articles/closing-issues-via-commit-messages/).

Tým .NET zkontroluje vaši žádost o přijetí změn a bude vás informovat, jestli jsou před schválením potřeba další aktualizace nebo změny.

**5. krok:** Proveďte ve větvi potřebné aktualizace, které jste projednali s týmem.

Jakmile jsou připomínky zapracované a změny schválené, sloučí správci vaši žádost o přijetí změn s hlavní větví.

Na určitou kadenci, budeme tlačit všechny commits z hlavní větve do živé větve a https://docs.microsoft.com/dotnet/pak budete moci vidět svůj příspěvek živě na .

### <a name="contributing-to-samples"></a>Příspěvky do ukázek kódu

Kód, který je v úložišti, rozdělujeme do dvou skupin:

- Ukázky: Čtenáři si je můžou stáhnout a spustit. Všechny ukázky musí představovat celé aplikace nebo knihovny. Pokud ukázka vytvoří knihovnu, musí obsahovat testy jednotek nebo aplikaci, která uživatelům umožní kód spustit.

- Fragmenty kódu: Ilustrují menší prvek nebo úlohu. Jsou kompilovatelné, ale nejde o kompletní aplikace.

Veškerý kód je v úložišti [dotnet/samples](https://github.com/dotnet/samples). Pracujeme na modelu, ve kterém bude struktura složek s ukázkami odpovídat struktuře složek dokumentace. Dodržujeme tato pravidla:

- Nejvyšší složka *snippets* obsahuje fragmenty kódu, které představují malé, jednoúčelové ukázky.
- Vzorky odkazů api byly ve složce následující podle tohoto vzoru: *úryvky /\<jazyk\<>/api/ obor názvů>/\<apiname>*.
- Další složky nejvyšší úrovně odpovídají nejvyšším složkám v úložišti *docs*. Například v úložišti docs je složka *machine-learning/tutorials* a ukázky ke kurzům věnovaným strojovému učení jsou ve složce *samples/machine-learning/tutorials*.

Navíc všechny ukázky ve složkách *core* a *standard* se musí dát vytvořit a spustit na všech platformách, které podporuje .NET Core. To zajistí náš systém sestavení CI. Nejvyšší složka *framework* obsahuje ukázky, které jsou vytvořené a ověřené jen ve Windows.

Tyto adresáře můžeme rozšířit, protože úložiště dokumentů přidává nový obsah. Přidáme například adresáře Xamarin, `xamarin-ios` `xamarin-android` jako a adresáře.

Každá hotová ukázka, kterou vytvoříte, má obsahovat soubor *readme.md*. V tomto souboru by měl být krátký popis ukázky (jeden nebo dva odstavce). Ze souboru *readme.md* by se čtenáři měli dozvědět, co se naučí, když si tuto ukázku vyzkouší. V souboru *readme.md* má být také odkaz na živý dokument na [webu s dokumentací k .NET](https://docs.microsoft.com/dotnet/welcome).
Pokud chcete zjistit mapování daného souboru v úložišti na tento web, nahraďte `/docs` v cestě k úložišti adresou `https://docs.microsoft.com/dotnet`.

Odkaz na ukázku bude i ve vašem tématu. Vytvořte odkaz přímo na složku s ukázkou na GitHubu.

Další informace naleznete v [tématu Ukázky Readme](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Interaktivní prostředí jazyka C#

Krátké ukázky kódu v jazyce C# používají jazykovou značku `csharp-interactive`, která znamená, že ukázku v jazyce C# můžete spustit v prohlížeči (Ukázky vložených `csharp-interactive` kódů používají značku, pro výstřižky zahrnuté ze zdroje použijte `code-csharp-interactive` značku.) Tyto ukázky kódu zobrazit okno kódu a výstupní okno v článku. V okně výstupu se zobrazuje výstup spuštěného interaktivního kódu po spuštění ukázky uživatelem.

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

Smlouvu nemusíte podepisovat předem. Žádosti o přijetí změn můžete obvyklým způsobem klonovat, odeslat nebo můžete vytvořit fork. Vytvořenou žádost o přijetí změn klasifikuje robot CLA. Pokud je změna triviální (například jste opravili překlep), pak `cla-not-required`je PR označeno . V ostatních případech bude zařazena jako `cla-required`. Po podpisu smlouvy CLA budou všechny současné i budoucí žádosti o přijetí změn označeny `cla-signed`.
