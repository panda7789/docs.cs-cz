---
title: Cloud Native DevOps
description: Architekt cloudových nativních aplikací .NET pro Azure | Cloud Native DevOps
ms.date: 06/30/2019
ms.openlocfilehash: d152989061964d78c8be97b69df413b975058319
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337404"
---
# <a name="cloud-native-devops"></a>Cloud Native DevOps

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Oblíbeným hesloem software konzultantů je odpovědět na všechny otázky, které jsou závislé na. Není to proto, že software konzultanti fond, že neprovádí žádnou pozici. Je to z toho důvodu, že neexistuje žádná skutečná odpověď na jakékoli dotazy v softwaru. Není k dispozici absolutní právo a nesprávné místo, ale rozdíl mezi opačnými hodnotami.

Vezměte v úvahu například dvě hlavní školy vývoje webových aplikací: jednostránkové aplikace (jednostránkové) oproti aplikacím na straně serveru. Na jedné straně je činnost koncového uživatele lepší díky jednostránkové a velikost provozu na webovém serveru může být minimalizována, takže je možné je hostovat na něco jako statické hostování. Na druhé straně je jednostránkové obvykle pomalejší pro vývoj a obtížnější testování. Kterou jednu si máte správnou volbu? To je dobré, záleží na vaší situaci.

Nativní aplikace v cloudu nejsou odolné vůči stejné dichotomy. Mají jasné výhody z pohledu rychlosti vývoje, stability a škálovatelnosti, ale jejich správa může být poměrně náročná.

Před lety nebylo běžné pro proces přesunu aplikace z vývoje do produkčního prostředí, které trvá měsíčně nebo ještě více. Společnosti vydaly software na 6 měsíců nebo i každý rok tempo. Abyste získali představu o tempo vydaných verzí, které byly přijatelné před začátkem zelených dnů od Windows 10, je potřeba, abyste si vyhledali ještě více než Microsoft Windows. Pět let předané mezi systémy Windows XP a Vista a dalšími 3 mezi systémy Vista a Windows 7.

Nyní je poměrně dobře navázáno, aby bylo možné rychle vydávat software, což umožňuje rychle přemísťovat společnosti s větším tržním přínosem v rámci svých podobných Sloth konkurentů. Je to z tohoto důvodu, že hlavní aktualizace Windows 10 jsou teď přibližně každých šest měsíců.

Vzorce a postupy, které umožňují rychlejší a spolehlivější vydání hodnoty podniku, jsou souhrnně označovány jako DevOps. Skládají se z široké škály nápadů, které pokrývá celý životní cyklus vývoje softwaru, od určení aplikace až po doručení a provozování této aplikace.

DevOps se předtím, než mikroslužby a je pravděpodobné, že přesun směrem k menšímu a většímu množství služeb by nebylo možné, aniž by DevOps mohl vydávat a provozovat nejen jednu, ale mnoho aplikací v produkčním prostředí je snazší.

![Obrázek 11-0 hledání trendů znázorňuje, že růst v mikroslužbách nezačíná až po DevOps je poměrně dobře zavedený nápad.](./media/microservices-vs-devops.png)

Osvědčenými postupy DevOps je, že je možné využít výhody cloudových nativních aplikací bez suffocating v rámci práce, ve které aplikace skutečně pracují.

Při vstupu do DevOps se nevyskytuje žádný zlatý kladiv. Nikdo nemůže prodávat kompletní a komplexní řešení pro uvolňování a provoz vysoce kvalitních aplikací. Je to proto, že každá aplikace je volně odlišná od všech ostatních. Existují však nástroje, které umožňují DevOps mnohem méně těžké. Jeden z těchto nástrojů je známý jako Azure DevOps.

## <a name="azure-devops"></a>Azure DevOps

Azure DevOps má dlouhého původu. Může trasovat své kořeny zpět do, když Team Foundation Server nejprve přesunuli do online režimu a prostřednictvím různých změn názvů: Visual Studio Online a Visual Studio Team Services. V průběhu let se ale stane mnohem více než jeho předchůdci.

Azure DevOps je rozdělené na pět hlavních součástí:

![Obrázek 11-1 pět hlavních oblastí služby Azure DevOps](./media/devops-components.png)

**Azure boards** – poskytuje nástroj pro sledování problémů a pracovních položek, který se snaží dovolit uživatelům vybrat pracovní postupy, které jsou pro ně nejvhodnější. Obsahuje řadu předem nakonfigurovaných šablon, včetně těch, které podporují SCRUM a kanbanové styly vývoje.

**Azure Repos** – Správa zdrojového kódu, která podporuje Venerable Správa verzí Team Foundation (TFVC) a obor oblíbených v oboru Git. Žádosti o přijetí změn poskytují způsob, jak povolit sociální kódování prostřednictvím diskuze o změnách, které se provedou.

**Azure Pipelines** – systém pro správu sestavení a vydání, který podporuje úzkou integraci s Azure. Buildy je možné spouštět na různých platformách od Windows po Linux až po MacOS. Agenti sestavení můžou být zřízené v cloudu nebo místně.

**Azure test Plans** – žádná osoba s funkcí QA nezůstane na pozadí pro správu testů a podporu průzkumného testování, kterou nabízí funkce test Plans.

**Azure Artifacts** – kanál artefaktu, který společnostem umožňuje vytvářet vlastní, interní, verze NuGet, npm a další. Pokud dojde k selhání centralizovaného úložiště, slouží pro ně dvojitý účel, který funguje jako mezipaměť pro nadřazené balíčky.

Organizační jednotka nejvyšší úrovně ve službě Azure DevOps se označuje jako projekt. V rámci každého projektu je možné zapnout nebo vypnout různé komponenty, například Azure Artifacts. Pokud uživatelé chtějí spravovat svůj zdrojový kód v GitHubu, ale stále využívají Azure Pipelines, je to dokonale možné. Mnoho open-source projektů využívá [bezplatné buildy](https://azure.microsoft.com/blog/announcing-azure-pipelines-with-unlimited-ci-cd-minutes-for-open-source/) nabízené službou Azure DevOps a přitom udržuje jejich zdrojový kód na GitHubu. Některé významné open source projekty, například [Visual Studio Code](https://code.visualstudio.com/), [přízi](https://yarnpkg.com/en/), [Gulp](https://gulpjs.com/)a [numpy](https://www.numpy.org/) , provedly přechod.

Každá z těchto komponent poskytuje některé výhody pro cloudové nativní aplikace, ale tři nejužitečnější jsou Správa zdrojového kódu, desky a kanály.  

## <a name="source-control"></a>Správy zdrojového kódu

Uspořádání kódu pro nativní cloudové aplikace může být náročné. Pro cloudové aplikace, které se navzájem vzájemně komunikují, se místo jedné aplikace obří může jednat o web s menšími aplikacemi. Stejně jako u všech věcí v computingu si nejlepší uspořádání kódu zůstane otevřené otázky. K dispozici jsou příklady úspěšných aplikací s různými druhy rozložení, ale dvě varianty vypadají nejvíc oblíbenosti.

Než se pustíte do samotné vlastní správy zdrojového kódu, je pravděpodobné, že se rozhodují, kolik projektů je vhodné. V rámci jednoho projektu je podporována podpora více úložišť a vytváření kanálů. Panely jsou trochu složitější, ale existují i úkoly, které je možné snadno přiřadit více týmům v rámci jednoho projektu. V jednom projektu Azure DevOps je sice možné podporovat stovky i tisíce vývojářů. V takovém případě je pravděpodobný nejlepší přístup, protože poskytuje všem vývojářům možnost pracovat z a snížit tak nejasnost najít tuto aplikaci, když vývojáři nezjistí, ve kterých projektech se nachází.

Rozdělení kódu pro mikroslužby v rámci projektu Azure DevOps může být trochu náročnější.

![Obrázek 11-2 jedno a více úložišť](./media/single-repository-vs-multiple.png)

### <a name="repository-per-microservice"></a>Úložiště na mikroslužbu

Na první pohled se zdá, že se jedná o největší logický přístup k rozdělení zdrojového kódu pro mikroslužby. Každé úložiště může obsahovat kód potřebný k vytvoření jedné mikroslužby. Výhody tohoto přístupu jsou snadno viditelné:

1. Pokyny k sestavení a údržbě aplikace lze přidat do souboru READme v kořenovém adresáři každého úložiště. Při převracení přes úložiště je snadné najít tyto pokyny a zkrátit tak dobu trvání pro vývojáře.
2. Každá služba je umístěná na logickém místě, kterou snadno najde s pochopením názvu služby.
3. Sestavení lze snadno nastavit tak, aby se aktivovala pouze v případě, že je provedena změna na vlastnící úložiště.
4. Počet změn přicházejících do úložiště je omezen na malý počet vývojářů pracujících na projektu.
5. Zabezpečení je snadné nastavit omezením úložišť, ke kterým mají vývojáři oprávnění ke čtení a zápisu.
6. Nastavení úrovně úložiště může změnit vlastnící tým o minimum diskuze s ostatními.

Jednou z klíčových nápadů za mikroslužby je, že služby by měly být silo a oddělené od sebe. Když použijete návrh založený na doméně, můžete se rozhodnout na hranicích služeb, které služby působí jako transakční hranice. Aktualizace databáze by neměly zahrnovat více služeb. Tato kolekce souvisejících dat je označována jako ohraničený kontext.  Tato nápad se projeví v izolaci dat mikroslužeb k databázi oddělené a autonomní od ostatních služeb. Přináší skvělou představu o tom, jak tento nápad přenést až do zdrojového kódu.

Tento přístup ale není bez problémů. Jedním z dalších problémů při vývoji Gnarly je Správa závislostí. Vezměte v úvahu počet souborů, které tvoří průměrný `node_modules` adresář. Novou instalací nějakého, jako je `create-react-app`, se nejspíš s tisíci balíčků zavede. Otázka, jak tyto závislosti spravovat, je obtížné.

Pokud je závislost aktualizována, musí podřízené balíčky také aktualizovat tuto závislost. To bohužel povede k práci s vývojem, takže invariably `node_modules` Adresář skončil s více verzemi jednoho balíčku, každá z nich je závislá na nějakém jiném balíčku, který je ve verzi trochu odlišný tempo. Při nasazování aplikace by měla být použita verze závislosti? Verze, která je aktuálně v produkčním prostředí? Verze, která je aktuálně ve verzi beta, ale která je pravděpodobně v produkčním čase, když ji příjemce provede do produkce? Obtížné problémy, které se nevyřešily jenom pomocí mikroslužeb.

Existují knihovny, které jsou závislé na nejrůznějších projektech. Tím, že mikroslužby vydělíte pomocí jednoho z nich, interní závislosti se můžou nejlépe vyřešit pomocí interního úložiště, Azure Artifacts. Sestavení pro knihovny budou nabízet své nejnovější verze do Azure Artifacts pro interní spotřebu. Aby bylo možné převzít závislosti na nově aktualizovaných balíčcích, musí se projekt pro příjem dat ještě ručně aktualizovat.

Jiná nevýhoda představuje při přesouvání kódu mezi službami sám sebe. I když by bylo dobré se domnívat, že první část aplikace do mikroslužeb je 100% správnosti, je tato realita tím, že je prescient, že nebudete moct dělat žádné chyby dělení služby. Proto budou funkce a kód, které jednotky potřebují, přesunout ze služby do služby: úložiště do úložiště. Při přestupnosti z jednoho úložiště na jiný kód ztratí svou historii. K dispozici je mnoho případů, zejména v případě auditu, kde je úplná historie v části kódu necenná.

Poslední a možná nejdůležitější nevýhodou je koordinace změn. V pravdivé aplikaci mikroslužeb by neexistovaly žádné závislosti nasazení mezi službami. Mělo by být možné nasadit služby A, B a C v libovolném pořadí, protože mají volné spojení. Ve skutečnosti ale existují situace, kdy je žádoucí provést změnu, která překročí více úložišť současně. Mezi příklady patří aktualizace knihovny pro uzavření bezpečnostního otvoru nebo změna komunikačního protokolu používaného všemi službami.

Aby bylo možné provést změnu mezi úložištěm, je třeba provést potvrzení u každého úložiště v případě úspěchu. Každá změna v každém úložišti bude vyžadovat vyžádání a revizi samostatně. To může být obtížné koordinovat a obecně obtěžovat.

Alternativou k použití mnoha úložišť je vložení veškerého zdrojového kódu do obří, všechny znalosti a samostatné úložiště.

### <a name="single-repository"></a>Jedno úložiště

V tomto přístupu, který se někdy označuje jako [monorepository](https://danluu.com/monorepo/), se všechen zdrojový kód pro každou službu vloží do stejného úložiště. Napřed to vypadá jako ještěrů nápad, který se bude pravděpodobně týkat zdrojového kódu nepraktický. Existují však některé z označených výhod pro práci tímto způsobem.

První výhodou je, že je snazší spravovat závislosti mezi projekty. Nemusíte se spoléhat na některý z externích kanálů artefaktů, projekty mohou přímo naimportovat navzájem. To znamená, že aktualizace jsou rychlé a v době kompilace v pracovní stanici vývojáře budou pravděpodobně nalezeny konfliktní verze. V důsledku toho se posunují některé z bezplatných testů integrace.

Při přesouvání kódu mezi projekty je nyní snazší zachovat historii, protože soubory budou zjištěny tak, jak byly přesunuty místo přepsání.

Další výhodou je, že široký rozsah změn, které jsou mezi hranicemi služeb, se dají provádět v jednom potvrzení. Tím se snižuje nároky na to, aby se mohly kontrolovat jednotlivé možné spousty změn.

Existuje mnoho nástrojů, které mohou provádět statickou analýzu kódu ke zjištění nebezpečných postupů programování nebo problematického používání rozhraní API. Ve světě s více úložišti se musí každé úložiště iterovat, aby bylo možné zjistit problémy v nich. Jediné úložiště umožňuje spustit analýzu vše na jednom místě.

Přístup k jednomu úložišti má i mnoho nevýhody. Jedním z nejpravděpodobnějších z nich je, že při jednom úložišti dojde k ohrožení zabezpečení. Pokud se obsah úložiště nevrací v úložišti podle modelu služby, dojde k minimálnímu množství ztracených kódů. S jediným úložištěm může dojít ke ztrátě všech vlastněných společností. V minulosti existovalo mnoho příkladů a bylo propadnutí celého úsilí o vývoj her. Máte-li více úložišť, zveřejňuje méně Surface pásma, což je velmi žádoucí vlastnost ve většině postupů zabezpečení.

Velikost jednoho úložiště se nejspíš rychle stane nespravovatelným. To představuje některé zajímavé důsledky výkonu. Může se stát, že budete muset použít specializované nástroje, jako je třeba [virtuální systém souborů pro Git](https://vfsforgit.org/), který byl původně navržený tak, aby vylepšil prostředí pro vývojáře v týmu Windows.

Často je argument pro použití jednoho úložiště převařená na argument, který Facebook nebo Google používá tuto metodu pro uspořádání zdrojového kódu. Je-li přístup pro tyto společnosti dobrý, je surely správným přístupem pro všechny společnosti. Pravdivostí věci je, že hodně společností pracuje na něco, jako je například škálování Facebooku nebo Google. Problémy, ke kterým dochází v těchto škálováních, se liší od většiny vývojářů. To, co je dobré pro hus, nemusí být dobré pro Gander.

Na konci lze buď řešení použít k hostování zdrojového kódu pro mikroslužby. Ve většině případů se ale výhody správy a strojírenství provozu v jednom úložišti nemeager. Rozdělení kódu v různých úložištích podporuje lepší oddělení potíží a podporuje autonomii mezi vývojovými týmy.  

### <a name="standard-directory-structure"></a>Standardní adresářová struktura

Bez ohledu na to, jak jedna z nich má projednání každé služby, bude mít vlastní adresář. Jedna z nejlepších optimalizací, která umožňuje vývojářům vzájemnou spolupráci mezi projekty, je udržovat standardní adresářovou strukturu.

![Obrázek 11-3 standardní adresářovou strukturu pro služby e-mailu i přihlášení](./media/dir-struct.png)

Vždy, když je vytvořen nový projekt, by měla být použita šablona, která je umístěna na místo správné struktury. Tato šablona může také zahrnovat takové užitečné položky jako kostra souboru READme a `azure-pipelines.yml`. V jakékoli architektuře mikroslužeb poskytuje vysoký stupeň odchylky mezi projekty složité operace proti službám.

Existuje mnoho nástrojů, které mohou poskytnout šablonování pro celý adresář, který obsahuje několik adresářů zdrojového kódu. [Yeoman](https://yeoman.io/) je oblíbený ve světě JavaScript a GitHub nedávno vydal [šablony úložišť](https://github.blog/2019-06-06-generate-new-repositories-with-repository-templates/), které poskytují většinu stejných funkcí.

## <a name="task-management"></a>Správa úloh

Správa úloh v jakémkoli projektu může být obtížná. Předem je dlouhé otázek, které vám pomohou při sestavování pracovních postupů a zajištění optimální produktivity vývojářů.

Nativní aplikace v cloudu mají za následek menší než tradiční softwarové produkty nebo alespoň ty, které jsou rozdělené na menší služby. Sledování problémů nebo úloh souvisejících s těmito službami zůstává důležité jako u jakéhokoli jiného softwarového projektu. Nikdo nechce ztratit záznam určité pracovní položky nebo vysvětlit zákazníkovi, že jejich potíže nebyly správně zaznamenány. Panely jsou konfigurovány na úrovni projektu, ale v rámci každého projektu lze definovat oblasti. Ty umožňují rozlomení problémů mezi několika komponentami. Výhodou zachování všech práce pro celou aplikaci na jednom místě je, že je snadné přesunout pracovní položky z jednoho týmu na jiný, protože jsou lépe pochopitelné.

Azure DevOps obsahuje předem nakonfigurované množství oblíbených šablon. Ve většině základních konfiguracích je potřeba, abyste věděli, co je ve nevyřízených položkách, na kterých lidé pracují, a co se děje. Je důležité mít přehled o procesu sestavování softwaru, aby bylo možné v práci určit prioritu a dokončené úkoly hlášené zákazníkovi. Samozřejmě je samozřejmě velmi málo softwarových projektů, které jsou jednoduché jako `to do`, `doing`a `done`. Netrvá tak dlouho, aby mohli uživatelé začít přidávat kroky, jako je `QA` nebo `Detailed Specification` procesu.

Jednou z důležitějších částí agilních metod je introspekce v pravidelných intervalech. Tyto recenze jsou určeny k tomu, aby poskytovaly přehled o tom, jaké problémy tým čelí a jak se dají zlepšit. Často to znamená změnu toku potíží a funkcí prostřednictvím procesu vývoje. Proto je naprosto dobrý stav, že rozbalíte rozložení desek s dalšími fázemi.

Fáze na panelech nejsou jediným nástrojem organizace. V závislosti na konfiguraci panelu je k dispozici hierarchie pracovních položek. Nejpřesnější položka, která se může zobrazit na panelu, je úkol. Mimo pole úkol obsahuje pole pro název, popis, prioritu, odhad množství zbývající práce a možnost propojení s dalšími pracovními položkami nebo položkami vývoje (větve, potvrzení, žádosti o přijetí změn, sestavení a tak dále). Pracovní položky mohou být klasifikovány do různých oblastí aplikace a různých iterací (sprinty), aby je bylo možné snadněji najít.

![Obrázek 11-4 příklad úlohy ve službě Azure DevOps](./media/task-details.png)

Pole Popis podporuje normální styly, které byste očekávali (tučné, kurzíva a přeškrtnutí), a možnost vkládat obrázky. Díky tomu je velmi výkonný nástroj, který se používá při zadávání práce nebo chyb.

Úlohy je možné zavádět do funkcí, které definují větší pracovní jednotku. Funkce je zase možné zavádět [do náměty](https://docs.microsoft.com/azure/devops/boards/backlogs/define-features-epics?view=azure-devops). Klasifikace úkolů v této hierarchii usnadňuje pochopení toho, jak velkou funkci přináší.

![Obrázek 11-5 typy pracovních položek, které jsou ve výchozím nastavení nakonfigurovány v základní šabloně procesu](./media/board-issue-types.png)

Existují různé druhy zobrazení problémů v Azure Boards. Položky, které ještě nejsou naplánované, se zobrazí v backlogu. Odtud je lze přiřadit ke sprintu. Sprint je časové pole, ve kterém se očekává, že se dokončí některé množství práce. Tato práce může zahrnovat úkoly, ale také řešení lístků. Po tomto případě lze celý Sprint spravovat z části panelu sprintu. Toto zobrazení ukazuje, jak probíhá práce, a obsahuje graf vypálení, který umožňuje průběžnou aktualizaci odhadu, pokud bude Sprint úspěšný.

![Obrázek 11-6 panel s definovaným sprintem](./media/sprint-board.png)

Teď by se měl vyhodnotit, že se na deskách v Azure DevOps nachází velký výkon. Pro vývojáře máte k dispozici snadnou pohled na to, co se právě zpracovává. Pro zobrazení správců projektu na nadcházející práci a přehled stávající práce. Pro manažery existuje spousta sestav o reportování a kapacitě. Bohužel neexistují žádné Magical o aplikacích Cloud Native, které eliminují nutnost sledovat práci. Pokud ale potřebujete sledovat práci, je k dispozici několik míst, kde je prostředí lepší než v Azure DevOps.

## <a name="cicd-pipelines"></a>Kanály CI/CD

Téměř žádná změna v životním cyklu vývoje softwaru se proto nenástupema jako pro kontinuální integraci (CI) a průběžné doručování (CD). Sestavování a spouštění automatizovaných testů proti zdrojovému kódu projektu, jakmile se změna vrátí do brzkého výskytu chyb. Před nástupem sestavení průběžné integrace by nebylo Neběžné získat kód z úložiště a zjistit, že neuspěly v testování nebo nemohly být sestaveny. Výsledkem je velké množství sledování ze zdroje přetržení.

Tradičně dodávání softwaru do produkčního prostředí vyžaduje rozsáhlou dokumentaci a seznam kroků. Každý z těchto kroků je nutné ručně provést v rámci velmi náchylného procesu k chybám.

![Obrázek 11-7 Kontrolní seznam](./media/checklist.png)

Nedílnou součástí průběžné integrace je průběžné doručování, ve kterém se do prostředí nasadí nově připravené balíčky. Ruční zpracování se nedá škálovat tak, aby odpovídalo rychlosti vývoje, takže automatizace je důležitější. Kontrolní seznamy jsou nahrazeny skripty, které mohou provádět stejné úlohy rychleji a přesněji než jakékoli lidské.

Prostředí, do kterého doručování průběžné doručování může být testovací prostředí nebo, jak je provádí řada velkých technologických společností, může to být provozní prostředí. Ta pak vyžaduje investici do vysoce kvalitních testů, které mohou poskytnout jistotu, že změna nevede k přerušení výroby pro uživatele. Stejným způsobem, že průběžná integrace přechytila problémy v kódu předčasné průběžné doručování, zachytí v brzkém procesu nasazení problémy.

Důležitost automatizace procesu sestavení a doručování je vykládána pomocí cloudových nativních aplikací. K nasazení dochází častěji a více prostředí, takže Ruční nasazení hranic je nemožné.

### <a name="azure-builds"></a>Sestavení Azure

Azure DevOps poskytuje sadu nástrojů pro zajištění nepřetržité integrace a nasazení snadněji než kdy dřív. Tyto nástroje jsou umístěné v části Azure Pipelines. První z nich je sestavení Azure, což je nástroj pro spouštění definic sestavení založených na YAML ve velkém měřítku. Uživatelé můžou buď přenést své vlastní počítače sestavení (Skvělé pro případ, že sestavení vyžaduje prostředí pečlivě), nebo použít počítač z nepřetržitě aktualizovaného fondu virtuálních počítačů Azure hostovaných pro Azure. Tyto hostované agenti sestavení přináší předinstalované prostředí široké škály vývojářských nástrojů, nejen vývoj pro .NET, ale pro vše od jazyka Java až po vývoj pro iPhone.

DevOps zahrnuje široké spektrum neplatných definic sestavení, které lze přizpůsobit pro jakékoli sestavení. Definice sestavení jsou definovány v souboru s názvem `azure-pipelines.yml` a vráceny do úložiště, aby mohly být ve verzi společně se zdrojovým kódem. To usnadňuje změny kanálu sestavení ve větvi, protože změny lze vrátit pouze do této větve. Příklad `azure-pipelines.yml` pro sestavování webové aplikace v ASP.NET na celé platformě je znázorněn na obrázku 11-8.

```yml
name: $(rev:r)

variables:
  version: 9.2.0.$(Build.BuildNumber)
  solution: Portals.sln
  artifactName: drop
  buildPlatform: any cpu
  buildConfiguration: release
  
pool:
  name: Hosted VS2017
  demands:
  - msbuild
  - visualstudio
  - vstest

steps:
- task: NuGetToolInstaller@0
  displayName: 'Use NuGet 4.4.1'
  inputs:
    versionSpec: 4.4.1

- task: NuGetCommand@2
  displayName: 'NuGet restore'
  inputs:
    restoreSolution: '$(solution)'

- task: VSBuild@1
  displayName: 'Build solution'
  inputs:
    solution: '$(solution)'
    msbuildArgs: '-p:DeployOnBuild=true -p:WebPublishMethod=Package -p:PackageAsSingleFile=true -p:SkipInvalidConfigurations=true -p:PackageLocation="$(build.artifactstagingdirectory)\\"'
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: VSTest@2
  displayName: 'Test Assemblies'
  inputs:
    testAssemblyVer2: |
     **\$(buildConfiguration)\**\*test*.dll
     !**\obj\**
     !**\*testadapter.dll
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: CopyFiles@2
  displayName: 'Copy UI Test Files to: $(build.artifactstagingdirectory)'
  inputs:
    SourceFolder: UITests
    TargetFolder: '$(build.artifactstagingdirectory)/uitests'

- task: PublishBuildArtifacts@1
  displayName: 'Publish Artifact'
  inputs:
    PathtoPublish: '$(build.artifactstagingdirectory)'
    ArtifactName: '$(artifactName)'
  condition: succeededOrFailed()
```

**Obrázek 11-8** – vzor Azure-Pipelines. yml

Tato definice sestavení používá řadu předdefinovaných úloh, které vytvářejí sestavení tak jednoduché jako sestavení sady galerie (jednodušší než obří Millennium Falcon). Například úloha NuGet obnoví balíčky NuGet, zatímco úloha VSBuild volá nástroje pro sestavení sady Visual Studio, aby provedla vlastní kompilaci. V Azure DevOps jsou k dispozici stovky různých úloh s tisíci více, které udržuje komunita. Je možné, že bez ohledu na to, jaké úlohy sestavení chcete spustit, už někdo vytvořil.

Sestavení lze aktivovat ručně, vrácením se změnami, podle plánu nebo dokončením jiného buildu. Ve většině případů je vhodné sestavovat při každém vrácení se změnami. Sestavení lze filtrovat, aby různá sestavení běžela v různých částech úložiště nebo v různých větvích. To umožňuje scénářům, jako je spouštění rychlých buildů s omezeným testováním na žádostech o přijetí změn a spuštění úplné regresní sady na noční bázi.

Konečný výsledek sestavení je kolekce souborů označovaných jako artefakty sestavení. Tyto artefakty mohou být předány k dalšímu kroku procesu sestavení nebo přidány do informačního kanálu artefaktu Azure, aby mohly být spotřebovány jinými sestaveními.

### <a name="azure-devops-releases"></a>Verze Azure DevOps

Sestavení se postará o zkompilování softwaru do balíčku s přípravnou, ale artefakty ještě musí být vloženy do testovacího prostředí, aby bylo možné dokončit průběžné doručování. V takovém případě Azure DevOps používá samostatný nástroj nazvaný releases. Nástroj releases používá stejné knihovny, které byly k dispozici pro sestavení, ale představují koncept "fáze". Fáze je izolované prostředí, do kterého se balíček nainstaluje. Například produkt může využívat vývoj, QA a produkční prostředí. Kód se průběžně doručuje do vývojového prostředí, kde pro něj můžete spouštět automatizované testy. Po dokončení těchto testů se tato verze přesune do prostředí QA pro manuální testování. Nakonec je kód přesunut do produkčního prostředí, kde je viditelný pro každého.

![Obrázek 11-9 příklad kanálu vydaných verzí s fázemi vývoje, QA a výroby](./media/release-pipeline.png)

Každou fázi sestavení lze automaticky aktivovat dokončením předchozí fáze. V mnoha případech to však není žádoucí. Přesun kódu do produkčního prostředí může vyžadovat schválení od někoho. Nástroj releases to podporuje tím, že povoluje schvalovatele v každém kroku kanálu vydání. Pravidla je možné nastavit tak, aby se určitá osoba nebo skupina osob před tím, než se začne do produkčního prostředí, odhlásila na vydané verzi. Tyto brány umožňují ruční kontroly kvality a také dodržování zákonných požadavků souvisejících s řízením toho, co se v produkčním prostředí týká.

### <a name="everybody-gets-a-build-pipeline"></a>Každý získá kanál sestavení

Pro konfiguraci mnoha kanálů sestavení se neúčtují žádné náklady, takže je výhodné mít aspoň jeden kanál sestavení na mikroslužbu. V ideálním případě jsou mikroslužby nezávisle nasazené do jakéhokoli prostředí, takže každý z nich může být vydán prostřednictvím vlastního kanálu, aniž by bylo nutné uvolnit hmotnost nesouvisejícího kódu. Každý kanál může mít vlastní sadu schválení, která umožňuje variace procesu sestavení pro každou službu.

### <a name="versioning-releases"></a>Verze verzí

Jednou z nevýhod používání funkce releases je, že se nedá definovat v souboru `azure-pipelines.yml` se změnami. Existuje mnoho důvodů, proč byste to měli udělat, protože definice vydání pro jednotlivé větve obsahují v šabloně projektu kostru vydání. Naštěstí je práce v průběhu přesunu některých fází do komponenty buildu. Tento postup se označuje jako sestavení ve více fázích a [první verze je teď k dispozici](https://devblogs.microsoft.com/devops/whats-new-with-azure-pipelines/)!

>[!div class="step-by-step"]
>[Předchozí](azure-security.md)
>[Další](infrastructure-as-code.md)
