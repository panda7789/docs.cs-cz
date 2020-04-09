---
title: Běžné architektury webových aplikací
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Prozkoumejte běžné architektury webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9a8e9450d81ac2e63a8c8ea54592ed81e646e05
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988125"
---
# <a name="common-web-application-architectures"></a>Běžné architektury webových aplikací

> "Pokud si myslíte, že dobrá architektura je drahá, zkuste špatnou architekturu."  
> _- Brian Foote a Joseph Joder_

Většina tradičních aplikací .NET se nasadí jako jednotlivé jednotky odpovídající spustitelnému souboru nebo jedné webové aplikaci spuštěné v rámci jedné domény aplikace IIS. Toto je nejjednodušší model nasazení a slouží mnoho interních a menších veřejných aplikací velmi dobře. I s ohledem na tuto jedinou jednotku nasazení však většina netriviálních obchodních aplikací těží z určitého logického oddělení do několika vrstev.

## <a name="what-is-a-monolithic-application"></a>Co je monolitická aplikace?

Monolitická aplikace je aplikace, která je zcela soběstačná, pokud jde o její chování. Může komunikovat s jinými službami nebo úložišti dat v průběhu provádění svých operací, ale jádro jeho chování běží v rámci vlastního procesu a celá aplikace je obvykle nasazena jako jedna jednotka. Pokud taková aplikace potřebuje škálovat vodorovně, obvykle celá aplikace je duplikována na více serverech nebo virtuálních počítačích.

## <a name="all-in-one-applications"></a>Aplikace vše v jednom

Nejmenší možný počet projektů pro architekturu aplikace je jeden. V této architektuře je celá logika aplikace obsažena v jednom projektu, zkompilována do jednoho sestavení a nasazena jako jedna jednotka.

Nový projekt ASP.NET Core, ať už vytvořený v sadě Visual Studio nebo z příkazového řádku, začíná jako jednoduchý monolit "vše v jednom". Obsahuje všechny chování aplikace, včetně prezentace, obchodní a logiky přístupu k datům. Obrázek 5-1 znázorňuje strukturu souborů aplikace s jedním projektem.

![Jeden projekt ASP.NET aplikaci Core](./media/image5-1.png)

**Obrázek 5-1.** Jeden projekt ASP.NET aplikaci Core.

V jednom scénáři projektu je oddělení obav dosaženo pomocí složek. Výchozí šablona obsahuje samostatné složky pro odpovědnosti vzoru MVC modelů, zobrazení a řadičů a další složky pro data a služby. V tomto uspořádání by měly být podrobnosti prezentace co nejvíce omezeny na složku Zobrazení a podrobnosti implementace přístupu k datům by měly být omezeny na třídy uchovávané ve složce Data. Obchodní logika by měla být umístěna ve službách a třídách ve složce Models.

Ačkoli jednoduché, monolitické řešení s jedním projektem má některé nevýhody. S růstem velikosti a složitosti projektu bude nadále růst i počet souborů a složek. Obavy uživatelského rozhraní (modely, zobrazení, řadiče) jsou umístěny ve více složkách, které nejsou seskupeny abecedně. Tento problém se zhorší pouze v případě, že jsou přidány další konstrukce na úrovni ui, jako jsou filtry nebo ModelBinders, ve svých vlastních složkách. Obchodní logika je rozptýlena mezi složky Modely a služby a neexistuje žádný jasný údaj o tom, které třídy, ve kterých složek by měly záviset na které ostatní. Tento nedostatek organizace na úrovni projektu často vede ke [špagetovým kódům](https://deviq.com/spaghetti-code/).

K řešení těchto problémů se aplikace často vyvíjejí do řešení s více projekty, kde se má za to, že každý projekt je umístěn v určité _vrstvě_ aplikace.

## <a name="what-are-layers"></a>Co jsou vrstvy?

Jak aplikace rostou ve složitosti, jedním ze způsobů, jak spravovat tuto složitost je rozdělit aplikace podle jeho odpovědnosti nebo obavy. To následuje oddělení obavy princip a může pomoci udržet rostoucí codebase uspořádat tak, aby vývojáři mohou snadno najít, kde je implementována určité funkce. Vrstvená architektura nabízí řadu výhod nad rámec organizace kódu.

Uspořádáním kódu do vrstev lze v celé aplikaci znovu použít běžné funkce nižší úrovně. Toto opakované použití je prospěšné, protože to znamená, že je třeba zapsat méně kódu a protože může umožnit aplikaci standardizovat na jedné implementaci, po principu [neopakujte se (DRY).](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

S vrstvenou architekturou mohou aplikace vynutit omezení, na kterých mohou vrstvy komunikovat s jinými vrstvami. To pomáhá dosáhnout zapouzdření. Při změně nebo nahrazení vrstvy by měly být ovlivněny pouze ty vrstvy, které s ní pracují. Omezením vrstev, které závisí na které další vrstvy, dopad změn lze zmírnit tak, aby jedna změna nemá vliv na celou aplikaci.

Vrstvy (a zapouzdření) usnadňují nahrazení funkcí v rámci aplikace. Například aplikace může zpočátku použít vlastní databázi SERVERU SQL Server pro trvalost, ale později může zvolit použití cloudové strategie trvalosti nebo za webové rozhraní API. Pokud aplikace správně zapouzdřila svou implementaci trvalosti v logické vrstvě, může být tato vrstva specifické pro SQL Server nahrazena novou vrstvou implementující stejné veřejné rozhraní.

Kromě potenciálu prohození implementací v reakci na budoucí změny v požadavcích mohou vrstvy aplikací také usnadnit výměnu implementací pro účely testování. Místo nutnosti psát testy, které pracují proti skutečné datové vrstvy nebo vrstvy ui aplikace, tyto vrstvy lze nahradit v době testování s falešné implementace, které poskytují známé odpovědi na požadavky. To obvykle usnadňuje psaní testů a mnohem rychlejší spuštění ve srovnání se spuštěním testů proti skutečné infrastruktuře aplikace.

Logické vrstvení je běžná technika pro zlepšení organizace kódu v podnikových softwarových aplikacích a existuje několik způsobů, jak kód lze uspořádat do vrstev.

> [!NOTE]
 > _Vrstvy_ představují logické oddělení v rámci aplikace. V případě, že je aplikační logika fyzicky distribuována na samostatné servery nebo procesy, jsou tyto samostatné cíle fyzického nasazení označovány jako _vrstvy_. Je možné a poměrně běžné mít nvrstvou aplikaci, která je nasazená do jedné vrstvy.

## <a name="traditional-n-layer-architecture-applications"></a>Tradiční aplikace architektury "N-Layer"

Nejběžnější organizace aplikační logiky do vrstev je znázorněna na obrázku 5-2.

![Typické aplikační vrstvy](./media/image5-2.png)

**Obrázek 5-2.** Typické aplikační vrstvy.

Tyto vrstvy jsou často zkráceny jako UI, BLL (Vrstva obchodní logiky) a DAL (Vrstva přístupu k datům). Pomocí této architektury uživatelé provádět požadavky prostřednictvím vrstvy uživatelského práva, který spolupracuje pouze s BLL. BLL zase můžete volat DAL pro požadavky na přístup k datům. Vrstva ui by neměla provádět žádné požadavky na DAL přímo, ani by měla komunikovat s trvalost přímo prostřednictvím jiných prostředků. Podobně BLL by měla pracovat pouze s trvalost procházením DAL. Tímto způsobem má každá vrstva svou vlastní známou odpovědnost.

Jednou z nevýhod tohoto tradičního přístupu vrstvení je, že závislosti v době kompilace spustit shora dolů. To znamená, že vrstva ui závisí na BLL, který závisí na DAL. To znamená, že BLL, který obvykle obsahuje nejdůležitější logiku v aplikaci, je závislá na podrobnostech implementace přístupu k datům (a často na existenci databáze). Testování obchodní logiky v takové architektuře je často obtížné, vyžadující testovací databázi. Princip inverze závislostí lze použít k řešení tohoto problému, jak uvidíte v další části.

Obrázek 5-3 ukazuje příklad řešení, rozdělení aplikace do tří projektů podle odpovědnosti (nebo vrstvy).

![Jednoduchá monolitická aplikace se třemi projekty](./media/image5-3.png)

**Obrázek 5-3.** Jednoduchá monolitická aplikace se třemi projekty.

Přestože tato aplikace používá několik projektů pro organizační účely, je stále nasazena jako jedna jednotka a její klienti s ní budou pracovat jako s jedinou webovou aplikací. To umožňuje velmi jednoduchý proces nasazení. Obrázek 5-4 ukazuje, jak taková aplikace může být hostované pomocí Azure.

![Jednoduché nasazení Azure Web Appu](./media/image5-4.png)

**Obrázek 5-4.** Jednoduché nasazení Azure Web Appu

S růstem potřeb aplikací mohou být vyžadována složitější a robustní řešení nasazení. Obrázek 5-5 ukazuje příklad složitější plán nasazení, který podporuje další možnosti.

![Nasazení webové aplikace do služby Azure App Service](./media/image5-5.png)

**Obrázek 5-5.** Nasazení webové aplikace do služby Azure App Service

Interně organizace tohoto projektu do více projektů založených na odpovědnosti zlepšuje udržovatelnost aplikace.

Tuto jednotku lze škálovat nebo zmenšovat, aby bylo možné využívat škálovatelnost na základě cloudu na vyžádání. Škálování znamená přidání dalšího procesoru, paměti, místa na disku nebo jiných prostředků na servery, které hostují vaši aplikaci. Horizontální navýšení kapacity znamená přidání dalších instancí těchto serverů, ať už se jedná o fyzické servery, virtuální počítače nebo kontejnery. Když je vaše aplikace hostovaná ve více instancích, slouží k přiřazení požadavků jednotlivým instancí aplikací balancer.

Nejjednodušší přístup k škálování webové aplikace v Azure je ruční konfigurace škálování v plánu služby App Service aplikace. Obrázek 5-6 ukazuje příslušnou obrazovku řídicího panelu Azure pro konfiguraci, kolik instancí obsluhuje aplikaci.

![Škálování plánu služeb aplikací v Azure](./media/image5-6.png)

**Obrázek 5-6.** Škálování plánu služeb aplikací v Azure.

## <a name="clean-architecture"></a>Čistá architektura

Aplikace, které se řídí principem inverze závislostí a principy DDD (Domain-Driven Design) mají tendenci docházet k podobné architektuře. Tato architektura se v průběhu let stala mnoha jmény. Jedním z prvních jmen byla šestihranná architektura, následovaná porty a adaptéry. Více nedávno, to bylo citováno jako [cibule architektura](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) nebo [čisté architektury](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Druhý název, Clean Architecture, se používá jako název pro tuto architekturu v této e-knize.

Referenční aplikace eShopOnWeb používá přístup Clean Architecture při organizaci svého kódu do projektů. Můžete najít šablonu řešení, kterou můžete použít jako výchozí bod pro vlastní ASP.NET Core na úložišti GitHub [ardalis / cleanarchitecture.](https://github.com/ardalis/cleanarchitecture)

Čistá architektura umístí obchodní logiku a aplikační model do středu aplikace. Místo toho, aby obchodní logika závisí na přístupu k datům nebo jiné problémy infrastruktury, tato závislost je obrácena: infrastruktura a podrobnosti implementace závisí na jádro aplikace. Toho je dosaženo definováním abstrakce nebo rozhraní v jádru aplikace, které jsou pak implementovány typy definované ve vrstvě infrastruktury. Běžným způsobem vizualizace této architektury je použití řady soustředných kruhů, podobně jako cibule. Obrázek 5-7 ukazuje příklad tohoto stylu architektonické reprezentace.

![Čistá architektura; pohled na cibuli](./media/image5-7.png)

**Obrázek 5-7.** Čistá architektura; pohled na cibuli

V tomto diagramu závislosti toku směrem k nejvnitřnější kruh. Jádro aplikace přebírá svůj název ze své pozice v jádru tohoto diagramu. A můžete vidět na diagramu, že jádro aplikace nemá žádné závislosti na jiných vrstvách aplikace. Entity a rozhraní aplikace jsou v samém centru. Jen mimo, ale stále v jádru aplikace, jsou služby domény, které obvykle implementují rozhraní definované ve vnitřním kruhu. Mimo jádro aplikace závisí vrstvy ui a infrastruktury na jádru aplikace, ale ne na sobě navzájem (nutně).

Obrázek 5-8 znázorňuje tradičnější diagram vodorovné vrstvy, který lépe odráží závislost mezi rozhraním A ostatními vrstvami.

![Čistá architektura; pohled vodorovné vrstvy](./media/image5-8.png)

**Obrázek 5-8.** Čistá architektura; pohled vodorovné vrstvy

Všimněte si, že plné šipky představují závislosti v době kompilace, zatímco přerušovaná šipka představuje závislost pouze za běhu. S čistou architekturou vrstva uživatelského rozhraní pracuje s rozhraními definovanými v jádru aplikace v době kompilace a v ideálním případě by neměla vědět o typech implementace definovaných ve vrstvě Infrastruktura. Za běhu jsou však tyto typy implementací vyžadovány pro spuštění aplikace, takže musí být přítomny a připojeny až k rozhraním Jádra aplikace prostřednictvím vkládání závislostí.

Obrázek 5-9 ukazuje podrobnější zobrazení architektury aplikace ASP.NET jádra při vytvoření podle těchto doporučení.

![ASP.NET diagram základní architektury po čisté architektuře](./media/image5-9.png)

**Obrázek 5-9.** ASP.NET diagram u základní architektury následující clean architektura.

Vzhledem k tomu, že jádro aplikace není závislé na infrastruktuře, je velmi snadné psát automatizované testy částí pro tuto vrstvu. Obrázky 5-10 a 5-11 ukazují, jak testy zapadají do této architektury.

![UnitTestCore](./media/image5-10.png)

**Obrázek 5-10.** Testování částí Application Core v izolaci.

![IntegraceTesty](./media/image5-11.png)

**Obrázek 5-11.** Integrace testování implementace infrastruktury s externízávislosti.

Vzhledem k tomu, že vrstva uj. nemá žádnou přímou závislost na typech definovaných v projektu Infrastruktura, je také velmi snadné vyměnit implementace, a to buď pro usnadnění testování, nebo v reakci na měnící se požadavky na aplikaci. ASP.NET core je vestavěné použití a podpora pro vkládání závislostí je tato architektura nejvhodnější způsob, jak strukturovat netriviální monolitické aplikace.

Pro monolitické aplikace jsou všechny projekty jádra aplikace, infrastruktury a ui spuštěny jako jedna aplikace. Architektura runtime aplikace může vypadat podobně jako obrázek 5-12.

![ASP.NET základní architektura 2](./media/image5-12.png)

**Obrázek 5-12.** Ukázka ASP.NET runtime architekturou aplikace Core.

### <a name="organizing-code-in-clean-architecture"></a>Uspořádání kódu v čisté architektuře

V řešení čisté architektury má každý projekt jasné odpovědnosti. V důsledku toho některé typy patří do každého projektu a budete často najít složky odpovídající těmto typům v příslušném projektu.

Jádro aplikace obsahuje obchodní model, který zahrnuje entity, služby a rozhraní. Tato rozhraní zahrnují abstrakce pro operace, které budou prováděny pomocí infrastruktury, jako je například přístup k datům, přístup k systému souborů, síťová volání atd. Někdy služby nebo rozhraní definované v této vrstvě bude muset pracovat s typy bez entity, které nemají žádné závislosti na uživatelském rozhraní nebo infrastruktury. Ty lze definovat jako jednoduché objekty přenosu dat (DTO).

### <a name="application-core-types"></a>Typy jádra aplikace

- Entity (třídy obchodního modelu, které jsou trvalé)
- Rozhraní
- Služby
- DTO

Projekt Infrastruktura obvykle zahrnuje implementace přístupu k datům. V typické ASP.NET základní webové aplikace, tyto implementace patří Entity Framework (EF) DbContext, všechny EF core `Migration` objekty, které byly definovány a třídy implementace přístupu k datům. Nejběžnější způsob, jak abstraktní kód implementace přístupu k datům je pomocí [návrhového vzoru úložiště](https://deviq.com/repository-pattern/).

Kromě implementace přístupu k datům by měl projekt Infrastruktura obsahovat implementace služeb, které musí být v interakci s problémy infrastruktury. Tyto služby by měly implementovat rozhraní definovaná v jádru aplikace, a proto infrastruktura by měla mít odkaz na projekt Jádra aplikace.

### <a name="infrastructure-types"></a>Typy infrastruktury

- Ef Core`DbContext`typy `Migration`( , )
- Typy implementace přístupu k datům (úložiště)
- Služby specifické pro `FileLogger` infrastrukturu `SmtpNotifier`(například nebo )

Vrstva uživatelského rozhraní v aplikaci core mvc ASP.NET je vstupním bodem aplikace. Tento projekt by měl odkazovat na projekt Jádra aplikace a jeho typy by měly interagovat s infrastrukturou výhradně prostřednictvím rozhraní definovaných v jádru aplikace. Ve vrstvě uj.

### <a name="ui-layer-types"></a>Typy vrstev ui

- Kontrolery
- Filtry
- Zobrazení
- Zobrazit modely
- Spuštění

Startup třída je zodpovědná za konfiguraci aplikace a pro zapojení typů implementace do rozhraní, což umožňuje vkládání závislostí pracovat správně za běhu.

> [!NOTE]
> Chcete-li provést vkládání závislostí v ConfigureServices v souboru Startup.cs projektu ui, projekt může být nutné odkazovat na projekt infrastruktury. Tuto závislost lze odstranit, nejsnadněji pomocí vlastního kontejneru DI. Pro účely této ukázky je nejjednodušším přístupem umožnit projektu ui odkazovat na projekt infrastruktury.

## <a name="monolithic-applications-and-containers"></a>Monolitické aplikace a nádoby

Můžete vytvořit jednu a monolitické nasazení založené webové aplikace nebo služby a nasadit jako kontejner. V rámci aplikace nemusí být monolitické, ale uspořádány do několika knihoven, komponent nebo vrstev. Externě je to jeden kontejner, jako je jeden proces, jedna webová aplikace nebo jedna služba.

Chcete-li spravovat tento model, nasadit jeden kontejner reprezentovat aplikaci. Chcete-li škálovat, stačí přidat další kopie s vyrovnáváním zatížení vpředu. Jednoduchost pochází ze správy jednoho nasazení v jednom kontejneru nebo virtuálním počítače.

![Obrázek 5-13](./media/image5-13.png)

Do každého kontejneru můžete zahrnout více součástí nebo knihoven nebo vnitřních vrstev, jak je znázorněno na obrázku 5-13. Ale po principu kontejneru _"kontejner dělá jednu věc a dělá to v jednom procesu_", monolitický vzor může být konflikt.

Nevýhodou tohoto přístupu přichází if / když aplikace roste, vyžadující škálování. Pokud se celá aplikace škáluje, není to opravdu problém. Ve většině případů je však několik částí aplikace body sytiče, které vyžadují změnu měřítka, zatímco jiné součásti se používají méně.

Pomocí typického příkladu elektronického obchodu je pravděpodobně nutné škálovat komponentu informací o produktu. Mnohem více zákazníků procházet produkty, než je zakoupit. Více zákazníků používá svůj košík než kanál plateb. Méně zákazníků přidává komentáře nebo si prohlíží historii nákupů. A pravděpodobně máte jen hrstku zaměstnanců v jedné oblasti, kteří potřebují spravovat obsah a marketingové kampaně. Změnou měřítka monolitického návrhu je veškerý kód nasazen vícekrát.

Kromě problému "škálování vše" změny jedné součásti vyžadují úplné opětovné testování celé aplikace a úplné přeřazení všech instancí.

Monolitický přístup je běžný a mnoho organizací se vyvíjí s tímto architektonickým přístupem. Mnozí mají dost dobrých výsledků, zatímco jiní jsou bít limity. Mnoho z nich navrhlo své aplikace v tomto modelu, protože nástroje a infrastruktura byly příliš obtížné vytvářet architektury orientované na služby (SOA) a neviděli potřebu, dokud aplikace nerostla. Pokud zjistíte, že jste dosažení mezí monolitické přístupu, rozdělení aplikace, aby mohla lépe využívat kontejnery a mikroslužeb může být dalším logickým krokem.

![Obrázek 5-14](./media/image5-14.png)

Nasazení monolitických aplikací v Microsoft Azure lze dosáhnout pomocí vyhrazených virtuálních počítačích pro každou instanci. Pomocí [škálovacích sad virtuálních strojů Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)můžete snadno škálovat virtuální počítače. [Azure App Services](https://azure.microsoft.com/services/app-service/) můžete spouštět monolitické aplikace a snadno škálovat instance bez nutnosti spravovat virtuální počítače. Azure App Services můžete spustit jednotlivé instance kontejnerů Dockeru také zjednodušit nasazení. Pomocí Dockeru můžete nasadit jeden virtuální počítač jako hostitele Dockeru a spustit více instancí. Pomocí azure balancer, jak je znázorněno na obrázku 5-14, můžete spravovat škálování.

Nasazení do různých hostitelů lze spravovat pomocí tradičních technik nasazení. Hostitelé Dockeru lze spravovat pomocí příkazů, jako je **spuštění dockeru** prováděné ručně, nebo prostřednictvím automatizace, jako jsou kanály průběžného doručování (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Monolitická aplikace nasazená jako kontejner

Existují výhody použití kontejnerů ke správě nasazení monolitických aplikací. Škálování instance kontejnerů je mnohem rychlejší a jednodušší než nasazení dalších virtuálních mandů. I při použití škálovacísady virtuálních počítačů pro škálování virtuálních počítačů, které nějakou dobu trvat instance. Při nasazení jako instance aplikace se konfigurace aplikace spravuje jako součást virtuálního počítače.

Nasazení aktualizací jako inamů Dockeru je mnohem rychlejší a efektivní v síti. Image Dockeru se obvykle spouštějí během několika sekund, což urychluje zavádění. Stržení instance Dockeru je stejně `docker stop` snadné jako vydání příkazu, obvykle dokončení za méně než sekundu.

Vzhledem k tomu, že kontejnery jsou ze své podstaty neměnné podle návrhu, nikdy se nemusíte starat o poškozené virtuální počítače, zatímco skripty aktualizace mohou zapomenout na účet pro některé konkrétní konfigurace nebo soubor vlevo na disku.

Kontejnery Dockeru můžete použít pro monolitické nasazení jednodušších webových aplikací. To zlepšuje průběžnou integraci a průběžné nasazení potrubí a pomáhá dosáhnout úspěchu nasazení k produkčnímu prostředí. Žádné další "Funguje to na mém stroji, proč to nefunguje ve výrobě?"

Architektura založená na mikroslužbách má mnoho výhod, ale tyto výhody jsou za cenu zvýšené složitosti. V některých případech náklady převažují nad výhodami, takže monolitické nasazení aplikace spuštěné v jednom kontejneru nebo jen v několika kontejnerech je lepší volbou.

Monolitické aplikace nemusí být snadno rozložitelné do dobře oddělené mikroslužeb. Mikroslužby by měly fungovat nezávisle na sobě, aby poskytovaly odolnější aplikaci. Pokud nemůžete dodat nezávislé funkce řezy aplikace, oddělení pouze zvyšuje složitost.

Aplikace ještě nemusí škálovat funkce nezávisle. Mnoho aplikací, pokud je třeba škálovat nad rámec jedné instance, můžete tak učinit prostřednictvím relativně jednoduchý proces klonování celé instance. Další práce na oddělení aplikace do samostatných služeb poskytuje minimální výhody při škálování plné instance aplikace je jednoduché a nákladově efektivní.

V rané fázi vývoje aplikace nemusíte mít jasnou představu o tom, kde jsou přirozené funkční hranice. Jak budete vyvíjet minimální životaschopný produkt, přirozené oddělení nemusí ještě objevily. Některé z těchto podmínek mohou být dočasné. Můžete začít vytvořením monolitické aplikace a později oddělit některé funkce, které mají být vyvinuty a nasazeny jako mikroslužby. Další podmínky může být nezbytné pro problémové místo aplikace, což znamená, že aplikace může být nikdy rozdělena do více mikroslužeb.

Oddělení aplikace do mnoha diskrétních procesů také přináší režii. Je tu větší složitost při rozdělování funkcí do různých procesů. Komunikační protokoly se stávají složitějšími. Místo volání metody je nutné použít asynchronní komunikaci mezi službami. Při přechodu na architekturu mikroslužeb je třeba přidat mnoho stavebních bloků implementovaných ve verzi mikroslužeb aplikace eShopOnContainers: zpracování sběrnice událostí, odolnost proti chybám zpráv a opakování, konečná konzistence a další.

Mnohem jednodušší [referenční aplikace eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) podporuje jednokontejnerové monolitické použití kontejnerů. Aplikace obsahuje jednu webovou aplikaci, která obsahuje tradiční zobrazení MVC, webová rozhraní API a stránky Razor. Tato aplikace může být spuštěna `docker-compose build` z `docker-compose up` kořene řešení pomocí příkazů a. Tento příkaz nakonfiguruje kontejner `Dockerfile` pro webovou instanci pomocí nalezenév kořenovém adresáři webového projektu a spustí kontejner na určeném portu. Zdroj pro tuto aplikaci si můžete stáhnout z GitHubu a spustit místně. I tato monolitická aplikace těží z nasazení v prostředí kontejneru.

Pro jednoho kontejnerizované nasazení znamená, že každá instance aplikace běží ve stejném prostředí. To zahrnuje vývojářské prostředí, kde probíhá včasné testování a vývoj. Vývojový tým může spustit aplikaci v kontejnerizovaném prostředí, které odpovídá produkčnímu prostředí.

Kromě toho kontejnerizované aplikace horizontální navýšení kapacity s nižšími náklady. Použití prostředí kontejneru umožňuje větší sdílení prostředků než tradiční prostředí virtuálních ms.

Nakonec kontejnerizace aplikace vynutí oddělení mezi obchodní logikou a serverem úložiště. Jak se aplikace škáluje, více kontejnerů bude všechny spoléhat na jedno fyzické paměťové médium. Toto paměťové médium by obvykle bylo serverem s vysokou dostupností, který používá databázi serveru SQL Server.

## <a name="docker-support"></a>Podpora pro Docker

Projekt `eShopOnWeb` běží na .NET Core. Proto jej lze spustit v kontejnerech založených na Linuxu nebo Windows. Všimněte si, že pro nasazení Dockeru chcete použít stejný typ hostitele pro SQL Server. Kontejnery založené na Linuxu umožňují menší půdorys a jsou upřednostňovány.

Pomocí Visual Studia 2017 nebo novějšího můžete přidat podporu Dockeru do existující aplikace kliknutím pravým tlačítkem myši na projekt v **Průzkumníku řešení** a výběrem **možnosti Přidat** > **podporu Dockeru**. Tím přidáte požadované soubory a upravíte projekt tak, aby je používal. Aktuální `eShopOnWeb` ukázka již tyto soubory má na místě.

Soubor na `docker-compose.yml` úrovni řešení obsahuje informace o tom, jaké image sestavit a jaké kontejnery spustit. Soubor umožňuje použít `docker-compose` příkaz ke spuštění více aplikací najednou. V tomto případě je pouze spuštění webového projektu. Můžete také použít ke konfiguraci závislostí, jako je například samostatný kontejner databáze.

```yml
version: '3'

services:
  eshopwebmvc:
    image: eshopwebmvc
    build:
      context: .
      dockerfile: src/Web/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5106:5106"

networks:
  default:
    external:
      name: nat
```

Soubor `docker-compose.yml` odkazuje v `Dockerfile` `Web` projektu. Slouží `Dockerfile` k určení, který základní kontejner bude použit a jak bude aplikace nakonfigurována. V `Web` `Dockerfile`části " :

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Řešení problémů s Dockerem

Po spuštění kontejnerizované aplikace, bude pokračovat v běhu, dokud ji nezastavíte. Pomocí příkazu můžete zobrazit, `docker ps` které kontejnery jsou spuštěny. Spuštěný kontejner můžete zastavit `docker stop` pomocí příkazu a zadáním ID kontejneru.

Všimněte si, že spuštění kontejnerů Dockeru může být vázáno na porty, které byste se jinak mohli pokusit použít ve vývojovém prostředí. Pokud se pokusíte spustit nebo ladit aplikaci pomocí stejného portu jako spuštěný kontejner Dockeru, zobrazí se chyba oznamující, že server se nemůže svázat s tímto portem. Znovu zastavení kontejneru by měl problém vyřešit.

Pokud chcete přidat podporu Dockeru do vaší aplikace pomocí Sady Visual Studio, ujistěte se, že Docker Desktop běží, když tak učiníte. Průvodce nebude fungovat správně, pokud docker desktop není spuštěn při spuštění průvodce. Kromě toho průvodce zkontroluje aktuální výběr kontejneru přidat správnou podporu Dockeru. Pokud chcete přidat podporu pro kontejnery windows, musíte spustit průvodce, když máte Docker Desktop běží s kontejnery Windows nakonfigurován. Pokud chcete přidat podporu pro linuxové kontejnery, spusťte průvodce, když máte Nakonfigurovaný Docker s kontejnery Linux.

### <a name="references--common-web-architectures"></a>Reference – běžné webové architektury

- **Čistá architektura**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **Cibulová architektura**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Vzor úložiště**  
  <https://deviq.com/repository-pattern/>
- **Šablona řešení čisté architektury**  
  <https://github.com/ardalis/cleanarchitecture>
- **E-kniha pro navrhování mikroslužeb**  
  <https://aka.ms/MicroservicesEbook>
- **DDD (návrh řízený doménou)**  
  <https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/>

>[!div class="step-by-step"]
>[Předchozí](architectural-principles.md)
>[další](common-client-side-web-technologies.md)
