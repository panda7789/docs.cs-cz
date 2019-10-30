---
ms.openlocfilehash: 0783c6ab80f3a07bd7b7e5a005444218c17e85fb
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035462"
---
# <a name="contributing"></a>Zvaní

Děkujeme za váš zájem o přispívání do dokumentace k .NET.

> Právě probíhá přesouvání našich pokynů do Průvodce příspěvkem v rámci nejrůznějších webů.
> Nové doprovodné materiály najdete v tématu [Přehled průvodce Microsoft Docsem přispěvatelem](https://docs.microsoft.com/contribute/).

Dokument popisuje proces pro přispívání do článků a ukázek kódu, které jsou hostovány na [webu dokumentace rozhraní .NET](https://docs.microsoft.com/dotnet). Příspěvky můžou být jednoduché jako překlepné opravy nebo jako nové články.

- [Proces pro přispívání](#process-for-contributing)
- [C# Interaktivní prostředí](#the-c-interactive-experience)
- [DOs a DON'Ts](#dos-and-donts)
- [Licenční smlouva přispěvatele](#contributor-license-agreement)

Toto úložiště obsahuje koncepční dokumentaci pro .NET. Kromě tohoto nástroje je web dokumentace .NET sestaven z více úložišť:

- [Ukázky kódu a fragmenty kódu](https://github.com/dotnet/samples)  
    Problémy a úkoly pro toto úložiště jsou sledovány v [dotnet/docs/problémech](https://github.com/dotnet/docs/issues).
- [Referenční dokumentace k rozhraní .NET API](https://github.com/dotnet/dotnet-api-docs)  
    Problémy a úkoly pro toto úložiště jsou sledovány v příkazu [dotnet/dotnet-API-docs/problémy](https://github.com/dotnet/dotnet-api-docs/issues).
- [Referenční informace k sadě .NET Compiler Platform SDK](https://github.com/dotnet/roslyn-api-docs)  
    Problémy a taks pro toto úložiště jsou sledovány v [dotnet/docs/problémech](https://github.com/dotnet/docs/issues).

## <a name="process-for-contributing"></a>Proces pro přispívání

Budete potřebovat základní porozumění [Gitu a GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Přeskočit tento krok pro malé změny (například pokud opravíte překlep nebo hned otevřete žádost o přijetí změn, které řeší problém, který najdete v dokumentaci). Pokud vás zajímá psaní nového obsahu nebo důkladné revize stávajícího obsahu, otevřete [problém](https://github.com/dotnet/docs/issues) popisující, co chcete udělat.
Obsah uvnitř složky *docs* je uspořádán do oddílů, které se projeví v obsahu (obsahu). Definujte, kde bude téma umístěno v obsahu. Získejte zpětnou vazbu k vašemu návrhu.

-nebo-

Můžete si také vybrat z existujících problémů, pro které jsou příspěvky komunitou Welcome. [Projekty pro přispěvatele komunity .NET](https://github.com/dotnet/docs/projects/35) obsahují mnoho pracovních položek, které jsou k dispozici pro komunitní přispěvatele. V závislosti na vašich zájmech a úrovni závazku si můžete vybrat z problémů v následujících kategoriích:

- **Údržba**. Tato kategorie zahrnuje poměrně jednoduché příspěvky, jako je třeba oprava poškozených nebo nesprávných odkazů, přidávání chybějících příkladů kódu nebo adresování omezených problémů s obsahem. V některých případech mohou tyto problémy pobývat se velkým počtem souborů. V takovém případě byste měli sdělit, na co byste chtěli pracovat, než začnete.

- **Aktualizace obsahu**. Vzhledem k enormity sady dokumentů se obsah snadno zastará a vyžaduje revizi. Kromě toho z nejrůznějších důvodů byl nějaký obsah duplikován nebo dokonce triplicated. Aktualizace obsahu zahrnuje kontrolu aktuálnosti jednotlivých témat nebo revizi obsahu v oblasti funkcí, aby eliminace duplicit a zajistila zachování veškerého jedinečného obsahu v menší sadě dokumentace.

- **Nový obsah**, který se vytváří. Pokud vás zajímá vytváření vlastního tématu, tato témata obsahují seznam problémů, které bychom chtěli přidat do naší sady dokumentů. Dejte nám prosím jistotu, než začnete pracovat na tématu, i když. Pokud vás zajímá psaní tématu, které tady není uvedené, otevřete problém.

Můžete si také prohlédnout náš seznam [otevřených problémů](https://github.com/dotnet/docs/issues) a začít pracovat s těmi, které vás zajímají. Pomocí popisku [up-for-drapáky](https://github.com/dotnet/docs/labels/up-for-grabs) označíte problémy otevřené pro příspěvky. 

**Krok 2:** Podle potřeby rozvětvete úložiště `dotnet/docs`, `dotnet/samples` nebo `dotnet/dotnet-api-docs` a vytvořte větev pro změny.

Pro malé změny můžete použít webové rozhraní GitHubu. Jednoduše klikněte na soubor, ve kterém se nachází **ve větvi tohoto projektu** , na soubor, který chcete změnit. GitHub vytvoří novou větev při odeslání změn.

**Krok 3:** Proveďte změny v této nové větvi.

Pokud se jedná o nové téma, můžete tento [soubor šablony](./styleguide/template.md) použít jako výchozí bod. Obsahuje pokyny pro zápis a také vysvětluje metadata požadovaná pro každý článek, například informace o autorovi.

Přejděte do složky, která odpovídá umístění obsahu určenému pro váš článek v kroku 1.
Tato složka obsahuje soubory Markdownu pro všechny články v této části.
V případě potřeby vytvořte novou složku, do které se umístí soubory pro svůj obsah. Hlavní článek pro tento oddíl se nazývá *index.MD*.
V případě obrázků a dalších statických prostředků vytvořte podsložku s názvem *Media* ve složce, která obsahuje váš článek, pokud ještě neexistuje. Uvnitř složky *Media* vytvořte podsložku s názvem článku (kromě souboru indexu).
Do složky *Samples* v kořenovém adresáři úložiště přidejte větší vzorky.

Nezapomeňte postupovat podle správné syntaxe Markdownu. Další informace najdete v příručce k [stylu](./styleguide/template.md).

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

**Krok 4:** Odešlete žádost o přijetí změn z větve a `dotnet/docs/master`, `dotnet/dotnet-api-docs/master` nebo `dotnet/samples/master`.

Vaše žádost o přijetí změn by měla *vždycky* cílit na výchozí větev úložiště (Pokud nepracujete na větvi vydané verze). Pro dotnet/Docs je hlavní větev výchozí větev. V případě lokalizovaných úložišť je výchozím nastavením jedna živá větev. *Nikdy* byste neměli otevřít žádost o přijetí změn, která se zaměřuje na živou větev v dotnet/docs.

Každá žádost o přijetí změn by obvykle měla řešit jeden problém v jednom okamžiku. Žádosti o přijetí změn můžou upravovat jeden nebo víc souborů. Pokud řešíte více oprav v různých souborech, jsou upřednostňovány samostatné pr.

Pokud vaše žádost o přijetí změn řeší existující problém, přidejte klíčové slovo `Fixes #Issue_Number` do zprávy potvrzení nebo popisu žádosti o přijetí změn. Tímto způsobem se problém automaticky uzavře při sloučení žádosti o přijetí změn. Další informace najdete v tématu [uzavírání problémů prostřednictvím zpráv potvrzení](https://help.github.com/articles/closing-issues-via-commit-messages/).

Tým .NET zkontroluje vaši žádost o přijetí změn a nabídne vám informace o tom, jestli jsou nějaké jiné aktualizace nebo změny potřebné k jejímu schválení.

**Krok 5:** Proveďte všechny nezbytné aktualizace vaší větve, jak je popsáno v týmu.

Když se vaše žádost o přijetí změn a vaše změna schválí, budou služby správy slučovat do hlavní větve.

Na určitých tempo budeme nahrávat všechna potvrzení z hlavní větve do živé větve a pak budete moct svůj příspěvek zobrazit živě na https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Přispívání do ukázek

U kódu, který existuje v našem úložišti, provedeme následující rozdíl:

- Ukázky: čtenáři můžou stáhnout a spustit ukázky. Všechny ukázky by měly být kompletní aplikace nebo knihovny. Kde ukázka vytvoří knihovnu, měla by zahrnovat testy jednotek nebo aplikaci, která umožňuje čtenářům spustit kód.

- Fragmenty: ilustruje menší koncept nebo úlohu. Zkompiluje, ale nejsou určeny k dokončení aplikací.

Celý kód v úložišti [dotnet/Samples](https://github.com/dotnet/samples) . Pracujeme na modelu, ve kterém struktura složek ukázky odpovídá naší struktuře složek docs. Níže jsou uvedené standardy:

- Složka *fragmenty* na nejvyšší úrovni obsahuje fragmenty pro malé a cílené ukázky.
- Ukázky odkazů na rozhraní API byly ve složce za tímto vzorem: *fragmenty/\<language >/api/\<namespace >/\<apiname >* .
- Ostatní složky nejvyšší úrovně odpovídají složkám nejvyšší úrovně v úložišti *docs* . Například úložiště docs má složku *Machine-Learning/kurzy* a ukázky pro kurzy strojového učení jsou ve složce *Samples/Machine-Learning/kurzy* .

Kromě toho by se všechny ukázky v rámci *základní* a *standardní* složky měly sestavit a spustit na všech platformách, které .NET Core podporuje. Náš systém sestavení CI bude vyhovět. Složka *architektury* nejvyšší úrovně obsahuje ukázky, které jsou sestaveny a ověřovány ve Windows.

Tyto adresáře můžeme rozšířit, protože úložiště docs přidává nový obsah. Například přidáme adresáře Xamarin, například `xamarin-ios` a `xamarin-android` adresáře.

Každá kompletní ukázka, kterou vytvoříte, by měla obsahovat soubor *Readme.MD* . Tento soubor by měl obsahovat krátký popis ukázky (jeden nebo dva odstavce). Váš *Readme.MD* by měl sdělit čtenářům, co se dozví, pomocí této ukázky. Soubor *Readme.MD* by měl také obsahovat odkaz na živý dokument na [webu dokumentace k rozhraní .NET](https://docs.microsoft.com/dotnet/welcome).
Chcete-li zjistit, kde se daný soubor v úložišti mapuje k této lokalitě, nahraďte `/docs` v cestě k úložišti pomocí `https://docs.microsoft.com/dotnet`.

Vaše téma bude obsahovat také odkazy na ukázku. Odkaz přímo na složku ukázky na GitHubu.

Další informace najdete v [souboru Readme ukázek](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>C# Interaktivní prostředí

Krátké ukázky kódu v C# nástroji můžou použít značku jazyka `csharp-interactive` k určení C# ukázky, která běží v prohlížeči. (Vložené ukázky kódu používají značku `csharp-interactive` pro fragmenty, které jsou součástí zdroje, použijte značku `code-csharp-interactive`.) Tyto ukázky kódu zobrazují okno kódu a výstupní okno v článku. V okně výstup se zobrazí jakýkoli výstup z provádění interaktivního kódu, jakmile uživatel spustí ukázku. 

C# Interaktivní prostředí mění způsob práce s ukázkami. Návštěvníci můžou ukázku spustit, aby se zobrazily výsledky. Řada faktorů vám pomůže určit, zda má vzorek nebo odpovídající text obsahovat informace o výstupu.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kdy zobrazit očekávaný výstup bez spuštění ukázky

- Články určené pro začátečníky by měly poskytovat výstup, aby čtenáři mohli porovnat výstup své práce s očekávanou odpovědí.
- Ukázky, ve kterých je výstup celočíselný pro téma, by měl zobrazit tento výstup. Například články týkající se formátovaného textu by měly zobrazovat textový formát bez spuštění ukázky.
- Pokud je ukázka i očekávaný výstup krátká, zvažte zobrazení výstupu. Šetří čas.
- Články vysvětlující, jak aktuální jazyková verze nebo invariantní jazyková verze ovlivňují výstup by měly vysvětlit očekávaný výstup. Interaktivní REPL (čtení vyhodnocení tiskové smyčky) běží na hostiteli se systémem Linux. Výchozí jazyková verze a invariantní jazyková verze vytváří různý výstup v různých operačních systémech a počítačích. Článek by měl vysvětlit výstup v systémech Windows, Linux a Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kdy se má vyřadit očekávaný výstup z ukázky 

- Články, ve kterých ukázka vygeneruje větší výstup by neměl obsahovat v komentářích. Po spuštění ukázkového kódu ho skryje.
- Články, ve kterých Ukázka ukazuje téma, ale výstup není integrální pro porozumění. Například kód, který spouští dotaz LINQ pro vysvětlení syntaxe dotazu a následně zobrazuje každou položku v kolekci výstupu.

## <a name="dos-and-donts"></a>DOs a DON'Ts

Následující seznam obsahuje pravidla pro GUID, která byste měli mít na paměti při přispívání do dokumentace rozhraní .NET:

- **Nedělejte** si u velkých žádostí o přijetí změn. Místo toho nahlaste problém a začněte diskuzi, abychom mohli vyjádřit souhlas s orientací ještě před tím, než investovat velké množství času. Pro hromadné změny Přerušte práci na menší PR (až 100 souborů).
- **Přečtěte si** článek [Průvodce stylem](./styleguide/template.md) a pokyny pro [hlasové a tónové](./styleguide/voice-tone.md) funkce.
- **Použijte soubor** [šablony](./styleguide/template.md) jako výchozí bod vaší práce.
- Než začnete pracovat na článcích **, vytvořte na** svém rozvětve samostatnou větev.
- **Postupujte podle** [pracovního postupu Flow GitHub](https://guides.github.com/introduction/flow/).
- **Udělejte to** na blogu (nebo cokoli) o příspěvcích, často!

> Poznámka: můžete si všimnout, že některá témata aktuálně nejsou v současné době podle všech uvedených pokynů a také v [Průvodci styly](./styleguide/template.md) . Pracujeme na dosažení konzistence v celé lokalitě.

## <a name="contributor-license-agreement"></a>Licenční smlouva přispěvatele

Před sloučením žádosti o přijetí změn musíte podepsat [licenční smlouvu .NET Foundation (cla)](https://cla.dotnetfoundation.org) . Jedná se o jednorázový požadavek pro projekty v rozhraní .NET Foundation. Můžete si přečíst další informace o [licenčních smlouvách k příspěvcích (cla)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) na Wikipedii.

Smlouva: [NET-Foundation-Contribution-License-Agreement. PDF](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Smlouvu nemusíte podepsat předem. Můžete naklonovat, rozvětvit a odeslat žádost o přijetí změn obvyklým způsobem. Když je vaše žádost o přijetí změn vytvořená, klasifikuje ji robotka CLA. Pokud je změna triviální (například jste opravili překlep), je žádost o přijetí změn označena `cla-not-required`. V opačném případě je klasifikována jako `cla-required`. Po podepsání CLA se aktuální a všechny budoucí žádosti o přijetí změn označí jako `cla-signed`.
