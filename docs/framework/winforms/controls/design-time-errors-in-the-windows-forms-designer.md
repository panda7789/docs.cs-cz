---
title: Chyby v době návrhu v Návrhář formulářů
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e2366513183337c3c5dd05ff45f8a6f724deaae
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988434"
---
# <a name="windows-forms-designer-error-page"></a>Chybová stránka Návrhář formulářů

Pokud se Návrhář formulářů nepovede načíst z důvodu chyby ve vašem kódu, v komponentě třetí strany nebo jinde, zobrazí se místo návrháře chybová stránka. Tato chybová stránka nemusí nutně znamenat chybu v návrháři. Chyba se může nacházet někde na stránce s kódem na pozadí, která \<je pojmenována na název-formuláře >. Designer.cs. Chyby se zobrazují v sbalitelných žlutých pruzích s odkazem na přechod na umístění chyby na znakové stránce.

![Chybová stránka Návrhář formulářů](media/windows-forms-designer-error-page-collapsed.png)

Můžete se rozhodnout ignorovat chyby a pokračovat v načítání návrháře kliknutím na **ignorovat a pokračovat**. Tato akce může vést k neočekávanému chování, například ovládací prvky se nemusí zobrazit na návrhové ploše.

## <a name="instances-of-this-error"></a>Instance této chyby

Po rozbalení žluté chybové úsečky se zobrazí všechny výskyty chyby. Mnoho typů chyb zahrnuje přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádek: *[řádek číslo]* sloupec: *[číslo sloupce]* . Pokud je k chybě přidružen zásobník volání, můžete kliknutím na odkaz **Zobrazit zásobník volání** zobrazit. Prozkoumání zásobníku volání může další pomoc při řešení této chyby.

![Rozšířená chyba Návrhář formulářů](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - U Visual Basic aplikací se na stránce s chybou návrhu nezobrazuje více než jedna chyba, ale může zobrazit několik instancí stejné chyby.
> - Pro C++ aplikace neobsahují chyby odkazy na umístění kódu.

## <a name="help-with-this-error"></a>Pomáhat s touto chybou

Pokud je k dispozici téma nápovědy pro chybu, klikněte na odkaz **nápovědy MSDN** , který umožňuje přejít přímo na stránku nápovědy na docs.Microsoft.com.

## <a name="forum-posts-about-this-error"></a>Příspěvky o této chybě ve fórech

Kliknutím na **Prohledat diskuze na fórech MSDN pro příspěvky související s tímto** odkazem na tuto chybu přejdete na fóra Microsoftu pro vývojáře v síti. Možná budete chtít vyhledat konkrétní [Návrhář formulářů](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) nebo [model Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) fóra.

## <a name="design-time-errors"></a>Chyby v době návrhu

V této části jsou uvedené některé chyby, se kterými se můžete setkat.

### <a name="identifier-name-is-not-a-valid-identifier"></a>'\<název identifikátoru > ' není platný identifikátor.

Tato chyba označuje, že pole, metoda, událost nebo objekt jsou nesprávně pojmenovány.

### <a name="name-already-exists-in-project-name"></a>'\<název > ' již existuje v '\<název projektu > '

Chybová zpráva:\<název > již\<v projektu název > existuje. Zadejte prosím jedinečný název. "

Zadali jste název zděděného formuláře, který již v projektu existuje. Chcete-li tuto chybu opravit, udělte zděděnému formuláři jedinečný název.

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>'\<Název karty panelu nástrojů > ' není kategorie panelu nástrojů

Návrhář třetí strany se pokusil o přístup k kartě na panelu nástrojů, který neexistuje. Obraťte se na dodavatele součásti.

### <a name="a-requested-language-parser-is-not-installed"></a>Požadovaný analyzátor jazyka není nainstalován

Chybová zpráva: Není nainstalován požadovaný analyzátor jazyka. Název analyzátoru jazyka je{0}.

Aplikace Visual Studio se pokusila načíst návrháře, který je zaregistrován pro typ souboru, ale nebyl nalezen. Příčinou je pravděpodobně chyba, ke které došlo při instalaci. Obraťte se na dodavatele jazyka, který používáte k opravě.

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>Chybí služba nezbytná pro vygenerování a analýzu zdrojového kódu

Jedná se o problém se součástí třetí strany. Obraťte se na dodavatele součásti.

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>Při pokusu o vytvoření instance '\<Object Name > ' došlo k výjimce.

Chybová zpráva: "Při pokusu o vytvoření instance\<názvu objektu > došlo k výjimce. Výjimka byla "\<řetězec\>výjimky".

Návrhář třetí strany požadoval, aby aplikace Visual Studio vytvořila objekt, ale objekt vyvolal chybu. Obraťte se na dodavatele součásti.

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>Jiný editor má '\<název dokumentu > ' otevřený v nekompatibilním režimu

Chybová zpráva: "Jiný editor má '\<název dokumentu > ' otevřený v nekompatibilním režimu. Zavřete prosím Editor a zkuste tuto operaci znovu. "

K této chybě dojde, pokud se pokusíte otevřít soubor, který je již otevřen v jiném editoru. Zobrazí se editor, který již soubor otevřel. Pokud chcete tuto chybu opravit, zavřete Editor, který má soubor otevřený, a zkuste to znovu.

### <a name="another-editor-has-made-changes-to-document-name"></a>Jiný Editor provedl změny v '\<> názvu dokumentu '

Zavřete a znovu otevřete návrháře, aby se změny projevily. Aplikace Visual Studio obvykle po provedení změn automaticky znovu načte návrháře. Ostatní návrháři, jako jsou například Návrháři součástí třetích stran, pravděpodobně nepodporují chování při opětovném načtení. V tomto případě vás Visual Studio vyzve k zavření a opětovnému otevření návrháře ručně.

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>Jiný editor má soubor otevřený v nekompatibilním režimu

Chybová zpráva: "Jiný editor má soubor otevřený v nekompatibilním režimu. Zavřete prosím Editor a zkuste tuto operaci znovu. "

Tato zpráva je podobná "jinému editoru\<je název dokumentu > otevřen v nekompatibilním režimu", ale Visual Studio nemůže určit název souboru. Pokud chcete tuto chybu opravit, zavřete Editor, který má soubor otevřený, a zkuste to znovu.

### <a name="array-rank-rank-in-array-is-too-high"></a>\<Rozměr pole pořadí v poli > je příliš vysoký.

Visual Studio podporuje pouze pole s jednou dimenzí v bloku kódu, který je analyzován návrhářem. Multidimenzionální pole jsou platná mimo tuto oblast.

### <a name="assembly-assembly-name-could-not-be-opened"></a>Sestavení '\<Assembly Name > ' se nepodařilo otevřít.

Chybová zpráva: \<Název sestavení Assembly > nelze otevřít. Ověřte, zda soubor stále existuje. "

Tato chybová zpráva nastane, když se pokusíte otevřít soubor, který nebylo možné otevřít. Ověřte, zda soubor existuje a je platným sestavením.

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>Chybný typ prvku Tento serializátor očekává element typu\<type name >.

Jedná se o problém se součástí třetí strany. Obraťte se na dodavatele součásti.

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>V tomto momentu nelze přistupovat k nástrojům sady Visual Studio

Sada Visual Studio provedla volání sady nástrojů, která nebyla k dispozici. Pokud se zobrazí tato chyba, pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>Nelze vytvořit vazby obslužné rutiny události k\<události > název události, protože je jen pro čtení.

K této chybě nejčastěji dochází, když se pokusíte připojit událost k ovládacímu prvku, který je zděděn ze základní třídy. Pokud je členská proměnná ovládacího prvku soukromá, Visual Studio nemůže připojit událost k metodě. Soukromým zděděným ovládacím prvkům nelze s nimi navázat další události.

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>Nelze vytvořit název metody pro požadovanou komponentu, protože není členem kontejneru návrhu

Aplikace Visual Studio se pokusila přidat obslužnou rutinu události do součásti, která nemá členskou proměnnou v návrháři. Obraťte se na dodavatele součásti.

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>Nelze pojmenovat objekt '\<Name > ', protože je již nazván '\<Name > '

Toto je vnitřní chyba serializátoru sady Visual Studio. Indikuje, že se serializátor pokusil pojmenovat objekt dvakrát, což není podporováno. Pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>Zděděnou součást\<názvu součásti > nelze odstranit ani zničit.

Zděděné ovládací prvky jsou pod vlastnictvím své třídy dědění. Změny zděděného ovládacího prvku musí být provedeny ve třídě, ze které ovládací prvek pochází. Proto jej nelze přejmenovat ani zničit.

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>Kategorie '\<název karty panelu nástrojů > ' neobsahuje Nástroj pro třídu '\<název třídy > '

Návrhář se pokusil o odkaz na třídu na konkrétní kartě panelu nástrojů, ale Třída neexistuje. Obraťte se na dodavatele součásti.

### <a name="class-class-name-has-no-matching-constructor"></a>Třída název\<třídy > nemá žádný vyhovující konstruktor.

Návrhář třetí strany požádal aplikaci Visual Studio, aby vytvořila objekt s konkrétními parametry v konstruktoru, který neexistuje. Obraťte se na dodavatele součásti.

### <a name="code-generation-for-property-property-name-failed"></a>Generování kódu pro\<vlastnost názvu vlastnosti > se nezdařilo.

Toto je obecná obálka pro chybu. Řetězec chyby, který doprovází tuto zprávu, bude obsahovat další podrobnosti o chybové zprávě a odkazy na konkrétnější téma nápovědy. Chcete-li tuto chybu opravit, vyřešte chybu uvedenou v chybové zprávě připojené k této chybě.

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>Součást s názvem součásti > nevolala ve svém konstruktoru Container. Add ().\<

Jedná se o chybu v komponentě, kterou jste právě načetli nebo umístili do formuláře. Označuje, že součást nebyla přidána k ovládacímu prvku kontejneru (ať už je to jiný ovládací prvek nebo formulář). Návrhář bude nadále fungovat, ale v době běhu mohou nastat problémy s komponentou.

Chcete-li chybu opravit, obraťte se na dodavatele součásti. Nebo, pokud se jedná o komponentu, kterou jste vytvořili, `IContainer.Add` zavolejte metodu v konstruktoru komponenty.

### <a name="component-name-cannot-be-empty"></a>Název součásti nesmí být prázdný

Tato chyba nastane, když se pokusíte přejmenovat komponentu na prázdnou hodnotu.

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>Nepovedlo se získat přístup\<k proměnné s názvem proměnné >, protože ještě není inicializovaný.

K této chybě může dojít z důvodu dvou scénářů. Dodavatel komponent třetí strany má problém s ovládacím prvkem nebo součástí, které byly distribuovány, nebo vytvořeným kódem je rekurzivní závislosti mezi komponentami.

Chcete-li tuto chybu opravit, ujistěte se, že váš kód nemá rekurzivní závislost. Pokud je takovým problémům zdarma, poznamenejte si přesný text chybové zprávy a obraťte se na dodavatele součásti.

### <a name="could-not-find-type-type-name"></a>Nejde najít typ\<type name >.

Chybová zpráva: Nepovedlo se najít typ\<název typu >. Ujistěte se, že je odkazováno na sestavení, které obsahuje tento typ. Pokud je tento typ součástí projektu vývoje, ujistěte se, že projekt byl úspěšně sestaven. "

K této chybě došlo, protože nebyl nalezen odkaz. Ujistěte se, že je odkazován typ uvedený v chybové zprávě a že existují také odkazy na všechna sestavení, která typ vyžaduje. Často se jedná o problém, že ovládací prvek v řešení nebyl sestaven. Sestavení vytvoříte tak, že v nabídce **sestavení** vyberete **Sestavit řešení** . V opačném případě, pokud je ovládací prvek již sestaven, přidejte odkaz ručně z místní nabídky na **odkazech** nebo ve složce **závislosti** v Průzkumník řešení.

### <a name="could-not-load-type-type-name"></a>Typ\<typu Name > nelze načíst.

Chybová zpráva: Nepovedlo se načíst typ\<název typu >. Ujistěte se prosím, že se do odkazů projektu přidalo sestavení obsahující tento typ. "

V aplikaci Visual Studio došlo k pokusu o navázání metody zpracování událostí a pro tuto metodu nebyl nalezen jeden nebo více typů parametrů. To je obvykle způsobeno chybějícím odkazem. Chcete-li tuto chybu opravit, přidejte odkaz obsahující typ do projektu a akci opakujte.

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>Nebyly nalezeny šablony položek projektu pro zděděné komponenty

Šablony pro zděděné formuláře v aplikaci Visual Studio nejsou k dispozici. Pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>Třída delegáta\<' název třídy > ' neobsahuje metodu Invoke. Je tato třída delegátem?

Aplikace Visual Studio se pokusila vytvořit obslužnou rutinu události, ale v typu události je něco špatného. K tomu může dojít, pokud byla událost vytvořena nekompatibilním jazykem, který není kompatibilní se specifikací CLS. Obraťte se na dodavatele součásti.

### <a name="duplicate-declaration-of-member-member-name"></a>Duplicitní deklarace členu\<Name >

K této chybě dojde, protože členská proměnná byla deklarována dvakrát (například dva ovládací prvky s `Button1` názvem jsou deklarovány v kódu). Názvy musí být v děděných formulářích jedinečné. Názvy se navíc nesmí lišit pouze v případě malých a velkých písmen.

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>Došlo k chybě při čtení prostředků ze souboru prostředků pro jazykovou verzi Culture s\<názvem >.

K této chybě může dojít, pokud je v projektu chybný soubor. resx.

Oprava této chyby:

1. Klikněte na tlačítko **Zobrazit všechny soubory** v Průzkumník řešení k zobrazení souborů. resx přidružených k řešení.
2. Načtěte soubor. resx v editoru XML tak, že kliknete pravým tlačítkem na soubor. resx a kliknete na **otevřít**.
3. Pokud chcete chyby vyřešit, upravte soubor. resx ručně.

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>Při čtení prostředků ze souboru prostředků pro výchozí jazykovou\<verzi názvu jazykové verze > došlo k chybě.

K této chybě může dojít, pokud je v projektu chybný soubor. resx pro výchozí jazykovou verzi.

Oprava této chyby:

1. Klikněte na tlačítko **Zobrazit všechny soubory** v Průzkumník řešení k zobrazení souborů. resx přidružených k řešení.
2. Načtěte soubor. resx v editoru XML tak, že kliknete pravým tlačítkem na soubor. resx a kliknete na **otevřít**.
3. Pokud chcete chyby vyřešit, upravte soubor. resx ručně.

### <a name="failed-to-parse-method-method-name"></a>Nepovedlo se analyzovat\<metodu s názvem metody >.

Chybová zpráva: "Nepovedlo se analyzovat\<metodu s názvem metody >. Analyzátor ohlásil následující chybu: '\<Error String > '. Podívejte se prosím na Seznam úkolů potenciální chyby. "

Jedná se o obecnou chybovou zprávu pro problémy, které vznikají při analýze. Tyto chyby jsou často způsobeny syntaktickými chybami. Konkrétní zprávy týkající se chyby najdete v Seznam úkolů.

### <a name="invalid-component-name-component-name"></a>Neplatný název součásti:\<název součásti >

Pokusili jste se přejmenovat komponentu na neplatnou hodnotu pro daný jazyk. Chcete-li tuto chybu opravit, pojmenujte komponentu tak, aby splňovala pravidla pojmenování pro daný jazyk.

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>Typ "\<název třídy >" je tvořen několika částečnými třídami ve stejném souboru

Při definování třídy ve více souborech pomocí klíčového slova [Partial](/dotnet/csharp/language-reference/keywords/partial-type) lze v každém souboru mít pouze jednu částečnou definici.

Chcete-li tuto chybu opravit, odeberte všechny kromě jedné z částečných definic vaší třídy ze souboru.

### <a name="the-assembly-assembly-name-could-not-be-found"></a>Sestavení '\<Assembly Name > ' nebylo nalezeno.

Chybová zpráva: Sestavení s\<názvem sestavení > nebylo nalezeno. Ujistěte se, že je odkazováno na sestavení. Pokud je sestavení součástí aktuálního vývojového projektu, ujistěte se, že projekt byl sestaven. "

Tato chyba je podobná typu\<typ název typu > nelze nalézt, ale k této chybě obvykle dochází z důvodu atributu metadata. Chcete-li tuto chybu opravit, ověřte, zda jsou odkazována všechna sestavení používaná atributy.

### <a name="the-assembly-name-assembly-name-is-invalid"></a>Název sestavení s názvem\<sestavení > není platný.

Komponenta požádala o konkrétní sestavení, ale název poskytnutý součástí není platný název sestavení. Obraťte se na dodavatele součásti.

### <a name="the-base-class-class-name-cannot-be-designed"></a>Základní třídu\<názvu Class > nelze navrhnout.

Aplikace Visual Studio načetla třídu, ale třídu nelze navrhnout, protože Implementátor třídy neposkytl návrháře. Pokud třída podporuje návrháře, ujistěte se, že nejsou k dispozici žádné problémy, které by způsobily problémy s jejich zobrazením v návrháři, například chyby kompilátoru. Také se ujistěte, že jsou všechny odkazy na třídu správné a že jsou správně zadány názvy všech tříd. V opačném případě, pokud není třída navržená, upravte ji v zobrazení kódu.

### <a name="the-base-class-class-name-could-not-be-loaded"></a>Základní třídu\<název třídy > nelze načíst.

Na třídu není odkazováno v projektu, takže je Visual Studio nemůže načíst. Chcete-li opravit tuto chybu, přidejte odkaz na třídu v projektu a zavřete a znovu otevřete okno Návrhář formulářů.

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>Třída\<název třídy > nemůže být navržena v této verzi sady Visual Studio.

Návrhář pro tento ovládací prvek nebo součást nepodporuje stejné typy jako aplikace Visual Studio. Obraťte se na dodavatele součásti.

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>Název třídy není platným identifikátorem tohoto jazyka

Zdrojový kód, který vytváří uživatel, má název třídy, který není platný pro používaný jazyk. Chcete-li tuto chybu opravit, pojmenujte třídu tak, aby splňovala jazykové požadavky.

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>Komponentu nejde přidat, protože obsahuje cyklický odkaz na\<název odkazu >.

Nelze přidat ovládací prvek nebo komponentu do sebe samé. Další situací, kdy k tomu může dojít, je v případě, že existuje kód v metodě InitializeComponent formuláře (například Form1), která vytvoří jinou instanci Form1.

### <a name="the-designer-cannot-be-modified-at-this-time"></a>Návrháře aktuálně nelze změnit

K této chybě dojde, pokud je soubor v editoru označen jako jen pro čtení. Zajistěte, aby soubor nebyl označen jen pro čtení a aplikace neběžela.

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>Návrháře nelze pro tento soubor zobrazit, protože nelze navrhnout žádnou z obsažených tříd

K této chybě dochází, když Visual Studio nemůže najít základní třídu, která splňuje požadavky návrháře. Formuláře a ovládací prvky musí být odvozeny ze základní třídy, která podporuje návrháře. Pokud jste odvozeni z zděděného formuláře nebo ovládacího prvku, zajistěte, aby byl projekt sestaven.

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>Není nainstalovaný Návrhář pro základní třídu\<název třídy >.

Aplikaci Visual Studio se nepodařilo načíst návrháře pro třídu. Pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>Návrhář musí vytvořit instanci typu "\<název typu >", ale nelze jej, protože typ je deklarován jako abstraktní.

K této chybě došlo, protože základní třída objektu předaná do návrháře je [abstraktní](/dotnet/csharp/language-reference/keywords/abstract), což není povoleno.

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>Soubor nelze načíst do návrháře

Základní třída tohoto souboru nepodporuje žádné návrháře. Alternativním řešením je použití zobrazení kódu pro práci na souboru. Klikněte pravým tlačítkem na soubor v Průzkumník řešení a vyberte **Zobrazit kód**.

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>Jazyk tohoto souboru nepodporuje nezbytné služby analýzy a vytváření kódu

Chybová zpráva: "Jazyk tohoto souboru nepodporuje nezbytné služby pro analýzu a generování kódu. Ujistěte se prosím, že soubor, který otevíráte, je členem projektu a pak zkuste soubor otevřít znovu. "

Tato chyba je pravděpodobně způsobena otevřením souboru, který je v projektu, který nepodporuje návrháře.

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>Třída analyzátoru jazyka '\<název třídy > ' není správně implementována

Chybová zpráva: "Třída analyzátoru jazyka"\<název třídy ">" není správně implementována. Obraťte se na dodavatele s aktualizovaným modulem analyzátoru. "

Používaný jazyk zaregistroval třídu návrháře, která není odvozena od správné základní třídy. Obraťte se na dodavatele jazyka, který používáte.

### <a name="the-name-name-is-already-used-by-another-object"></a>Název Name >\<už používá jiný objekt.

Toto je vnitřní chyba serializátoru sady Visual Studio. Pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>Objekt '\<název objektu > ' neimplementuje rozhraní IComponent.

Aplikace Visual Studio se pokusila o vytvoření komponenty, ale objekt, který vytvořil, <xref:System.ComponentModel.IComponent> neimplementuje rozhraní. Pro opravu se obraťte na dodavatele součásti.

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>Objekt '\<název objektu > ' vrátil hodnotu null pro vlastnost '\<název vlastnosti > ', ale tato hodnota není povolena.

Existují některé vlastnosti rozhraní .NET, které by měly vždy vracet objekt. Například **ovládací prvky** kolekce formuláře by měly vždy vracet objekt, i když v něm nejsou žádné ovládací prvky.

Chcete-li tuto chybu opravit, ujistěte se, že vlastnost zadaná v této chybě není null.

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>Objekt serializace dat nemá vhodný typ

Datový objekt nabízený serializátorem není instancí typu, která odpovídá aktuálně používanému serializátoru. Obraťte se na dodavatele součásti.

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>Služba > název\<služby je povinná, ale nedala se najít.

Chybová zpráva: Je vyžadován název služby > Service, ale nebyl nalezen.\< Může se jednat o problém s instalací sady Visual Studio. "

Služba vyžadovaná v rámci sady Visual Studio není k dispozici. Pokud jste se pokoušeli načíst projekt, který nepodporuje tohoto návrháře, použijte Editor kódu k provedení změn, které požadujete. Jinak, pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>Instance služby musí být odvozená od rozhraní s\<názvem > a implementovat ho.

Tato chyba označuje, že komponenta nebo Návrhář komponent volala metodu **AddService** , která vyžaduje rozhraní a objekt, ale zadaný objekt neimplementuje zadané rozhraní. Obraťte se na dodavatele součásti.

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>Text v okně kódu nelze upravit

Chybová zpráva: "Text v okně kódu nebylo možné změnit. Ověřte, že soubor není jen pro čtení a že je na disku dostatek místa. "

K této chybě dochází, pokud Visual Studio nemůže upravit soubor z důvodu problémů s místem na disku nebo paměti nebo je soubor označený jen pro čtení.

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>Objekt čítače výčtu panelu nástrojů podporuje pouze načítání položek po jedné

Pokud se zobrazí tato chyba, pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>Z panelu nástrojů nelze načíst\<položku sady nástrojů pro název součásti >.

Chybová zpráva: Položku sady nástrojů pro\<název součásti > nelze načíst ze sady nástrojů. Ujistěte se, že sestavení, které obsahuje položku sady nástrojů, je správně nainstalováno. Položka sady nástrojů vyvolala následující chybu \<: řetězec chyby >. "

V dané součásti došlo k výjimce při jejím použití v aplikaci Visual Studio. Obraťte se na dodavatele součásti.

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>Položku sady nástrojů pro\<položku název položky sady nástrojů > nelze načíst ze sady nástrojů.

Chybová zpráva: Položku panelu nástrojů pro\<položku název položky sady nástrojů > nelze načíst ze sady nástrojů. Zkuste položku odebrat ze sady nástrojů a přidat ji zpátky. "

K této chybě dojde, pokud jsou data v rámci položky sady nástrojů poškozena nebo se změnila verze součásti. Zkuste položku odebrat ze sady nástrojů a znovu ji přidat.

### <a name="the-type-type-name-could-not-be-found"></a>Typ typu "\<> názvu" nebyl nalezen.

Chybová zpráva: \<Typ typu Name > nebyl nalezen. Ujistěte se, že je odkazováno na sestavení, které obsahuje daný typ. Pokud je sestavení součástí aktuálního vývojového projektu, ujistěte se, že projekt byl sestaven. "

Při načítání návrháře se nepodařilo najít typ v aplikaci Visual Studio. Ujistěte se, že je odkazováno na sestavení, které obsahuje daný typ. Pokud je sestavení součástí aktuálního vývojového projektu, ujistěte se, že projekt byl sestaven.

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>Službu pro rozlišení typ lze volat pouze z hlavního vlákna aplikace

Aplikace Visual Studio se pokusila získat přístup k požadovaným prostředkům z chybného vlákna. Tato chyba se zobrazí, pokud kód použitý k vytvoření návrháře se nazývá služba překladu typu z jiného vlákna než z hlavního vlákna aplikace. Chcete-li tuto chybu opravit, zavolejte službu ze správného vlákna nebo se obraťte na dodavatele součásti.

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>Proměnná '\<název proměnné > ' je buď nedeklarovaná, nebo nebyla nikdy přiřazena.

Zdrojový kód obsahuje odkaz na proměnnou, jako je například **Button1**, která není deklarována nebo přiřazena. Pokud se proměnná nepřiřadila, zobrazí se tato zpráva jako upozornění, nikoli chyba.

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>Již existuje obslužná rutina příkazu pro příkaz nabídky ' název\<příkazu nabídky ' > '

K této chybě dojde, pokud návrhář třetí strany přidá příkaz, který již má obslužnou rutinu do tabulky příkazů. Obraťte se na dodavatele součásti.

### <a name="there-is-already-a-component-named-component-name"></a>Komponenta s názvem "\<název součásti >" již existuje.

Chybová zpráva: "Již existuje součást s názvem"\<název součásti > ". Komponenty musí mít jedinečné názvy a názvy nesmí rozlišovat velká a malá písmena. Název také nemůže být v konfliktu s názvem žádné součásti ve zděděné třídě. "

Tato chybová zpráva nastane, pokud došlo ke změně názvu komponenty v okno Vlastnosti. Chcete-li opravit tuto chybu, zajistěte, aby všechny názvy součástí byly jedinečné, nerozlišují velká a malá písmena a nekolidují s názvy všech komponent ve zděděných třídách.

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>Pro formát\<Format Name > už je registrovaný tvůrce položky sady nástrojů.

Komponenta třetí strany provedla zpětné volání položky na kartě panelu nástrojů, ale položka již obsahuje zpětné volání. Obraťte se na dodavatele součásti.

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>Modul tohoto jazyka nepodporuje CodeModel, jehož prostřednictvím má být načten návrhář

Tato zpráva je podobná "jazyku pro tento soubor nepodporuje nezbytné služby pro analýzu a generování kódu", ale tato zpráva zahrnuje interní problém s registrací. Pokud se zobrazí tato chyba, pokud se zobrazí tato chyba, Zaprotokolujte prosím problém pomocí [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>\<Typ\<typu Typenemákonstruktorsparametrytypůnázev\>typu parametru >.

Visual Studio nemohlo najít [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) , který má odpovídající parametry. To může být výsledkem poskytnutí konstruktoru s jinými typy, než které jsou požadovány. Například konstruktor **Point** může mít dvě celá čísla. Pokud jste zadali float, tato chyba je vyvolána.

Chcete-li tuto chybu opravit, použijte jiný konstruktor nebo explicitně přetypujte typy parametrů tak, aby odpovídaly hodnotám poskytnutým konstruktorem.

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>Do aktuální aplikace se nedá\<přidat odkaz > odkazu.

Chybová zpráva: "Nepovedlo se přidat\<odkaz na název odkazu > do aktuální aplikace. Ověřte, že na jinou verzi\<> odkaz na název se už neodkazuje.

Visual Studio nemůže přidat odkaz. Tuto chybu opravíte tak, že zkontrolujete, že na jinou verzi odkazu ještě není odkazováno.

### <a name="unable-to-check-out-the-current-file"></a>Nelze rezervovat aktuální soubor

Chybová zpráva: "Nepovedlo se rezervovat aktuální soubor. Soubor může být zamčený nebo může být nutné soubor rezervovat ručně. "

Tato chyba nastane, když změníte soubor, který je aktuálně vrácen se změnami do správy zdrojového kódu. Visual Studio obvykle prezentuje dialogové okno registrace souborů, takže uživatel může soubor rezervovat. Tentokrát se soubor nerezervoval, možná kvůli konfliktu sloučení během rezervace. Pokud chcete tuto chybu opravit, ujistěte se, že soubor není uzamčený, a zkuste soubor rezervovat ručně.

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>Nelze najít stránku s názvem '\<karta dialogového okna Možnosti název > '

Tato chyba nastane, když Návrhář komponent požaduje přístup k stránce z dialogového okna Možnosti pomocí názvu, který neexistuje. Obraťte se na dodavatele součásti.

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>Nelze najít vlastnost '\<název vlastnosti > ' na stránce '\<karta dialogového okna Možnosti název > '

Tato chyba nastane, když Návrhář komponent vyžaduje přístup k určité hodnotě na stránce v dialogovém okně Možnosti, ale tato hodnota neexistuje. Obraťte se na dodavatele součásti.

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>Visual Studio nemůže otevřít Návrháře pro soubor, protože třída v souboru nedědí ze třídy, kterou lze vizuálně navrhovat

Aplikace Visual Studio načetla třídu, ale návrháře pro tuto třídu nelze načíst. Visual Studio vyžaduje, aby návrháři používali první třídu v souboru. Chcete-li tuto chybu opravit, přesuňte kód třídy tak, aby byl první třídou v souboru, a poté znovu načtěte návrháře.

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>Visual Studio nemůže uložit nebo načíst instance typu\<type name >.

Jedná se o problém se součástí třetí strany. Obraťte se na dodavatele součásti.

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>Visual Studio nemůže otevřít\<dokument s názvem > v zobrazení Návrh

Chybová zpráva: Visual Studio nemůže v zobrazení Návrh otevřít\<dokument s názvem >. Pro tento typ souboru není nainstalován žádný analyzátor. "

Tato chyba označuje, že jazyk projektu nepodporuje návrháře a nastane při pokusu o otevření souboru v dialogovém okně otevřít soubor nebo z Průzkumník řešení. Místo toho upravte soubor v zobrazení kódu.

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>Visual Studio nemohlo najít návrháře pro třídy typu\<type name >.

Aplikace Visual Studio načetla třídu, ale třídu nelze navrhnout. Místo toho upravte třídu v zobrazení kódu tak, že kliknete pravým tlačítkem na třídu a zvolíte **Zobrazit kód**.

## <a name="see-also"></a>Viz také:

- [Vývoj model Windows Formsch ovládacích prvků pomocí návrháře](developing-windows-forms-controls-at-design-time.md)
- [Fórum Návrhář formulářů](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
