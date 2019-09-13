---
title: Běžné architektury webových aplikací
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Prozkoumat společné architektury webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: a521be147c462146775caa81b6a31fb37b4103af
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926686"
---
# <a name="common-web-application-architectures"></a>Běžné architektury webových aplikací

> "Pokud se domníváte, že dobrá architektura je náročná, vyzkoušejte si chybnou architekturu."  
> _– Briana nohou a Josepha Yoder_

Většina tradičních aplikací .NET je nasazena jako samostatné jednotky, které odpovídají spustitelnému souboru nebo jedné webové aplikaci běžící v rámci jedné domény aplikace služby IIS. Toto je nejjednodušší model nasazení a obsluhuje mnoho interních a menších veřejných aplikací. I když je však tato jediná jednotka nasazení, většina netriviálních obchodních aplikací má výhodu z některých logických oddělení do několika vrstev.

## <a name="what-is-a-monolithic-application"></a>Co je aplikace monolitické?

Aplikace monolitické je zcela samostatná, z pohledu jejího chování. Může komunikovat s jinými službami nebo úložišti dat v průběhu provádění jeho operací, ale jádro jeho chování běží v rámci svého vlastního procesu a celá aplikace je obvykle nasazena jako jediná jednotka. Pokud taková aplikace potřebuje horizontální horizontální navýšení kapacity, obvykle je celá aplikace duplikována napříč více servery nebo virtuálními počítači.

## <a name="all-in-one-applications"></a>Všechny aplikace v jednom

Nejmenší možný počet projektů pro architekturu aplikace je jeden. V této architektuře je celá logika aplikace obsažena v jednom projektu, zkompilována do jediného sestavení a nasazena jako jedna jednotka.

Nový ASP.NET Core projekt, ať už je vytvořený v aplikaci Visual Studio nebo z příkazového řádku, začíná jako jednoduché monolituy "All-in-One". Obsahuje všechna chování aplikace, včetně prezentace, obchodu a logiky přístupu k datům. Obrázek 5-1 ukazuje strukturu souborů aplikace s jedním projektem.

![Jeden projekt ASP.NET Core aplikaci](./media/image5-1.png)

**Obrázek 5-1.** Jeden projekt ASP.NET Core aplikaci.

V případě jednoho projektu je rozdělení obav zajištěno pomocí složek. Výchozí šablona obsahuje samostatné složky pro zodpovědnost vzorků MVC modelů, zobrazení a řadičů a také další složky pro data a služby. V tomto uspořádání by se měly podrobnosti o prezentaci co nejvíce omezit na složku zobrazení a podrobnosti implementace přístupu k datům by měly být omezené na třídy uchovávané ve složce data. Obchodní logika by se měla nacházet v části služby a třídy v rámci složky modely.

I když je jednoduché řešení monolitické s jedním projektem nějaké nevýhody. Jak roste velikost a složitost projektu, počet souborů a složek bude i nadále rostoucí. Problematika uživatelského rozhraní (modely, zobrazení, řadiče) se nachází ve více složkách, které nejsou seskupeny abecedně. K tomuto problému dochází pouze v případě, že se do vlastních složek přidávají další konstrukce na úrovni uživatelského rozhraní, jako jsou například filtry nebo ModelBinders. Obchodní logika je rozptýlená mezi složkami modely a služby a neexistuje žádné jasné označení tříd, na kterých by měly složky záviset. Tato nedostatečná organizace na úrovni projektu často vede k [Spaghetti kódu](https://deviq.com/spaghetti-code/).

Pro vyřešení těchto problémů se aplikace často rozvíjejí do řešení s více projekty, kde každý projekt je považován za umístěný v konkrétní _vrstvě_ aplikace.

## <a name="what-are-layers"></a>Co jsou vrstvy?

Vzhledem k tím, že aplikace výrazně roste, je třeba tuto složitost zvládnout tak, že se aplikace rozdělují podle svých povinností nebo obav. To se řídí oddělením zásad, které vám pomůžou udržet rostoucí základ kódu, aby mohli vývojáři snadno najít, kde jsou určité funkce implementované. Vrstvená architektura nabízí řadu výhod mimo organizaci s kódem, i když.

Díky uspořádání kódu do vrstev lze v celé aplikaci znovu použít běžné funkce nízké úrovně. Toto opakované použití je užitečné, protože znamená, že je nutné zapsat méně kódu a protože může aplikaci povolit standardizaci na jednu implementaci, a to po [neopakuji (suchý)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) princip.

Pomocí vrstvené architektury můžou aplikace vyhovět omezením, které vrstvy můžou komunikovat s jinými vrstvami. To pomáhá dosáhnout zapouzdření. Když je vrstva změněna nebo nahrazena, mělo by to mít vliv pouze na ty vrstvy, které s ní pracují. Omezením, které vrstvy závisí na tom, na které jiné vrstvy, může dopad změn zmírnit, aby jedna změna neovlivnila celou aplikaci.

Vrstvy (a zapouzdření) výrazně usnadňují nahrazování funkcí v rámci aplikace. Například aplikace může zpočátku používat svou vlastní databázi SQL Server pro trvalost, ale později se může rozhodnout použít cloudovou strategii trvalosti nebo jedno za webovým rozhraním API. Pokud aplikace správně zapouzdřuje jeho implementaci trvalosti v rámci logické vrstvy, může být SQL Server konkrétní vrstva nahrazena novou jednou implementací stejného veřejného rozhraní.

Kromě potenciálu záměny implementací v reakci na budoucí změny v požadavcích může aplikační vrstvy také usnadnit výměnu implementací pro účely testování. Místo toho, aby bylo nutné zapisovat testy, které pracují s reálnými datovými vrstvami nebo ve vrstvě uživatelského rozhraní aplikace, lze tyto vrstvy nahradit v době testování pomocí falešných implementací, které poskytují známé odpovědi na požadavky. To obvykle usnadňuje psaní a mnohem rychlejší spouštění testů ve srovnání se spouštěním testů v rámci reálné infrastruktury aplikace.

Logická vrstva je běžná technika pro zlepšení organizace kódu v podnikových softwarových aplikacích a existuje několik způsobů, jak lze kód uspořádat do vrstev.

> [!NOTE]
 > _Vrstvy_ reprezentují logické oddělování v rámci aplikace. V případě, že je aplikační logika fyzicky distribuována na samostatné servery nebo procesy, jsou tyto samostatné cíle fyzického nasazení označovány jako _vrstvy_. Je možné a poměrně běžné, aby bylo možné používat N-vrstvou aplikaci, která je nasazena na jednu vrstvu.

## <a name="traditional-n-layer-architecture-applications"></a>Tradiční aplikace architektury N-Layer

Nejběžnější uspořádání logiky aplikace do vrstev je znázorněno na obrázku 5-2.

![Typické aplikační vrstvy](./media/image5-2.png)

**Obrázek 5-2.** Typické vrstvy aplikace.

Tyto vrstvy jsou často zkrácené jako uživatelské rozhraní, knihoven BLL (vrstva obchodní logiky) a DAL (Data Access Layer). Pomocí této architektury můžou uživatelé provádět žádosti přes vrstvu uživatelského rozhraní, která komunikuje jenom s knihoven BLL. KNIHOVEN BLL pak může volat DAL pro žádosti o přístup k datům. Vrstva uživatelského rozhraní by neměla přímo předávat žádné požadavky na DAL, ani by nemusela komunikovat s persistencí přímo jiným způsobem. Stejně tak by knihoven BLL mělo pracovat pouze s trvalou cestou přes DAL. Tímto způsobem má každá vrstva svou vlastní dobře známou zodpovědnost.

Jednou z nevýhod tohoto tradičního přístupu k vrstvení je to, že se závislosti při kompilaci spouštějí shora dolů. To znamená, že vrstva uživatelského rozhraní závisí na knihoven BLL, který závisí na DAL. To znamená, že knihoven BLL, který obvykle obsahuje nejdůležitější logiku v aplikaci, závisí na podrobnostech implementace přístupu k datům (a často při existenci databáze). Testování obchodní logiky v takové architektuře je často obtížné a vyžaduje testovací databázi. Princip inverze závislostí lze použít k vyřešení tohoto problému, jak se zobrazí v další části.

Obrázek 5-3 ukazuje ukázkové řešení a rozdělení aplikace na tři projekty podle zodpovědnosti (nebo vrstvy).

![Jednoduchá aplikace monolitické se třemi projekty](./media/image5-3.png)

**Obrázek 5-3.** Jednoduchá aplikace monolitické se třemi projekty.

I když tato aplikace používá pro organizační účely několik projektů, je stále nasazena jako jediná jednotka a její klienti s ní budou pracovat jako jedna webová aplikace. To umožňuje velmi jednoduchý proces nasazení. Obrázek 5-4 ukazuje, jak může být taková aplikace hostovaná pomocí Azure.

![Jednoduché nasazení webové aplikace Azure](./media/image5-4.png)

**Obrázek 5-4.** Jednoduché nasazení webové aplikace Azure

Vzhledem k rostoucí potřebě aplikací se může vyžadovat složitější a robustní řešení nasazení. Obrázek 5-5 ukazuje příklad složitějšího plánu nasazení, který podporuje další možnosti.

![Nasazení webové aplikace do Azure App Service](./media/image5-5.png)

**Obrázek 5-5.** Nasazení webové aplikace do Azure App Service

Interně, organizace tohoto projektu do více projektů na základě zodpovědnosti zlepšuje udržovatelnost aplikace.

Tato jednotka se dá škálovat nahoru nebo dolů, aby využila výhody cloudové škálovatelnosti na vyžádání. Vertikální škálování znamená přidání dalšího procesoru, paměti, místa na disku nebo jiných prostředků na servery hostující vaši aplikaci. Horizontální navýšení kapacity znamená přidání dalších instancí takových serverů, ať už jde o fyzické servery, virtuální počítače nebo kontejnery. Pokud je vaše aplikace hostována v rámci více instancí, používá nástroj pro vyrovnávání zatížení k přiřazování požadavků jednotlivým instancím aplikací.

Nejjednodušší způsob, jak škálovat webovou aplikaci v Azure, je nakonfigurovat škálování ručně v plánu App Service aplikace. Obrázek 5-6 ukazuje příslušnou obrazovku řídicího panelu Azure ke konfiguraci, kolik instancí obsluhuje aplikace.

![App Service plánování škálování v Azure](./media/image5-6.png)

**Obrázek 5-6.** App Service plánování škálování v Azure.

## <a name="clean-architecture"></a>Čistá architektura

Aplikace, které následují po principu inverze závislostí, a také principy návrhu založeného na doméně (DDD), které mají za následek podobnou architekturu. Tato architektura prošla řadou názvů za roky. Jedním z prvních názvů je Šestiúhelníkická architektura následovaný porty-a-adaptery. V poslední době je citována jako [cibulová architektura](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) nebo [čistá architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Tento název se používá jako název pro tuto architekturu v této elektronické příručce.

> [!NOTE]
> Pojem čistá architektura se dá použít pro aplikace, které jsou vytvořené pomocí DDD principu, i pro ty, které nejsou sestavené pomocí DDD. V případě bývalého příkazu se tato kombinace může označovat jako "čistá DDD architektura".

Čistá architektura vloží model obchodní logiky a aplikace do středu aplikace. Místo toho, aby obchodní logika závisela na přístupu k datům nebo jiné infrastruktuře, je tato závislost opačná: informace o infrastruktuře a implementaci závisí na jádru aplikace. Toho je dosaženo definováním abstrakcí nebo rozhraní v jádru aplikace, které jsou následně implementovány pomocí typů definovaných ve vrstvě infrastruktury. Běžným způsobem vizualizace této architektury je použití řady soustředných kruhů, podobně jako cibule. Obrázek 5-7 ukazuje příklad tohoto stylu strukturální reprezentace.

![Čistá architektura; zobrazení průsvitek](./media/image5-7.png)

**Obrázek 5-7.** Čistá architektura; zobrazení průsvitek

V tomto diagramu se závislosti nasměrují k vnitřnímu kruhu. Jádro aplikace přebírá svůj název od pozice v jádru tohoto diagramu. A můžete se podívat na diagram, že jádro aplikace nemá žádné závislosti na jiných vrstvách aplikace. Entity a rozhraní aplikace jsou ve velmi středu. Stejně jako mimo, ale i v jádru aplikace, jsou doménové služby, které obvykle implementují rozhraní definovaná ve vnitřním kruhu. Mimo jádro aplikace závisí rozhraní a vrstvy infrastruktury na jádru aplikace, ale ne na jednom jiném (nutně).

Obrázek 5-8 ukazuje obecnější vodorovný Diagram vrstev, který lépe odráží závislosti mezi uživatelským rozhraním a dalšími vrstvami.

![Čistá architektura; horizontální zobrazení vrstvy](./media/image5-8.png)

**Obrázek 5-8.** Čistá architektura; horizontální zobrazení vrstvy

Všimněte si, že plné šipky představují závislosti v době kompilace, zatímco Čárkovaná šipka představuje závislost pouze za běhu. V případě čisté architektury pracuje vrstva uživatelského rozhraní s rozhraními definovanými v jádru aplikace v době kompilace a v ideálním případě by neměla znát typy implementace definované v infrastruktuře vrstev. V době běhu jsou však tyto typy implementace požadovány, aby bylo možné aplikaci spustit, takže musí být přítomna a zapojena do základních rozhraní aplikace prostřednictvím injektáže závislosti.

Obrázek 5-9 ukazuje podrobnější zobrazení architektury aplikace ASP.NET Core při sestavení těchto doporučení.

![Diagram architektury ASP.NET Core po čisté architektuře](./media/image5-9.png)

**Obrázek 5-9.** ASP.NET Core diagramu architektury po vyčištění architektury.

Vzhledem k tomu, že jádro aplikace nezávisí na infrastruktuře, je velmi snadné zapsat automatizované testy jednotek pro tuto vrstvu. Obrázky 5-10 a 5-11 ukazují, jak testy spadají do této architektury.

![UnitTestCore](./media/image5-10.png)

**Obrázek 5-10.** Jádro testování částí aplikace v izolaci.

![IntegrationTests](./media/image5-11.png)

**Obrázek 5-11.** Implementace testování infrastruktury v rámci integrace s externími závislostmi.

Vzhledem k tomu, že vrstva uživatelského rozhraní nemá žádnou přímou závislost na typech definovaných v projektu infrastruktury, je také velmi snadné vyměňovat implementace, a to buď pro usnadnění testování, nebo v reakci na změnu požadavků aplikace. ASP.NET Core integrované použití a podpora pro vkládání závislostí dává této architektuře nejvhodnější způsob, jak strukturovat jiné než triviální aplikace monolitické.

Pro aplikace monolitické jsou všechny projekty jádra, infrastruktury a uživatelského rozhraní spouštěny jako jedna aplikace. Běhová architektura aplikace může vypadat přibližně jako obrázek 5-12.

![ASP.NET Core architektura 2](./media/image5-12.png)

**Obrázek 5-12.** Ukázková Architektura modulu runtime ASP.NET Core aplikace

### <a name="organizing-code-in-clean-architecture"></a>Organizování kódu v čisté architektuře

V řešení čisté architektury má každý projekt jasné zodpovědnosti. V takovém případě určité typy patří do každého projektu a často najdete složky odpovídající těmto typům v příslušném projektu.

Jádro aplikace obsahuje obchodní model, který zahrnuje entity, služby a rozhraní. Mezi tato rozhraní patří abstrakce pro operace, které budou provedeny pomocí infrastruktury, jako je například přístup k datům, přístup k systému souborů, volání sítě atd. Někdy služby nebo rozhraní definované v této vrstvě budou potřebovat pracovat s typy bez entit, které neobsahují žádné závislosti na uživatelském rozhraní nebo infrastruktuře. Ty lze definovat jako jednoduché objekty Přenos dat (DTO).

### <a name="application-core-types"></a>Základní typy aplikace

- Entity (třídy obchodního modelu, které jsou trvalé)
- Rozhraní
- Služby
- DTO

Projekt infrastruktury obvykle zahrnuje implementace přístupu k datům. V typické ASP.NET Core webové aplikaci zahrnuje tyto implementace Entity Framework (EF) DbContext, všechny EF Core `Migration` objekty, které byly definovány, a třídy implementace přístupu k datům. Nejběžnější způsob, jak abstraktní kód pro implementaci přístupu k datům, je použití [vzoru návrhu úložiště](https://deviq.com/repository-pattern/).

Kromě implementace přístupu k datům by měl projekt infrastruktury obsahovat implementace služeb, které musí komunikovat s infrastrukturou infrastruktury. Tyto služby by měly implementovat rozhraní definovaná v jádru aplikace, takže infrastruktura by měla mít odkaz na projekt Application Core.

### <a name="infrastructure-types"></a>Typy infrastruktury

- Typy EF Core (`DbContext`, `Migration`)
- Typy implementace přístupu k datům (úložiště)
- Služby specifické pro infrastrukturu (například `FileLogger` nebo) `SmtpNotifier`

Vrstva uživatelského rozhraní v aplikaci ASP.NET Core MVC je vstupním bodem pro aplikaci. Tento projekt by měl odkazovat na projekt základního projektu a jeho typy by měly komunikovat s infrastrukturou výhradně prostřednictvím rozhraní definovaných v Application Core. Ve vrstvě uživatelského rozhraní by se měly povolit žádné přímé vytváření instancí ani statická volání typů vrstev infrastruktury.

### <a name="ui-layer-types"></a>Typy vrstev uživatelského rozhraní

- Kontrolery
- Filtry
- Zobrazení
- ViewModels
- Třída pro spuštění

Třída po spuštění zodpovídá za konfiguraci aplikace a pro zapojení typů implementace do rozhraní, což umožňuje, aby vkládání závislostí fungovalo správně v době běhu.

> [!NOTE]
> Aby bylo možné vytvořit ConfigureServices závislostí v souboru Startup.cs projektu uživatelského rozhraní, může se stát, že projekt bude potřebovat odkaz na projekt infrastruktury. Tuto závislost lze pomocí vlastního kontejneru DI snadno eliminovat. Pro účely této ukázky je nejjednodušší přístup k tomu, aby projekt uživatelského rozhraní odkazoval na projekt infrastruktury.

## <a name="monolithic-applications-and-containers"></a>Monolitické aplikací a kontejnerů

Můžete vytvořit jednu a monolitické webovou aplikaci nebo službu založenou na nasazení a nasadit ji jako kontejner. V rámci aplikace nemusí být monolitické, ale uspořádány do několika knihoven, komponent nebo vrstev. Externě se jedná o jediný kontejner, jako je jeden proces, jedna webová aplikace nebo jedna služba.

Chcete-li spravovat tento model, nasadíte jeden kontejner, který bude představovat aplikaci. Chcete-li škálovat, stačí přidat další kopie pomocí nástroje pro vyrovnávání zatížení předem. Jednoduchost pochází ze správy jednoho nasazení v jednom kontejneru nebo virtuálním počítači.

![](./media/image5-13.png)

V rámci každého kontejneru můžete zahrnout více komponent, knihoven nebo vnitřních vrstev, jak je znázorněno na obrázku 5-13. Ale podle principu kontejneru _"kontejner provede jednu věc a provede ho v jednom procesu_", vzor monolitické může být konflikt.

K Nevýhodou tohoto přístupu přijde, když/když aplikace roste a vyžaduje, aby se škálovat. Pokud se celá aplikace škáluje, není ve skutečnosti problém. Ve většině případů některé části aplikace jsou však potlačením bodů vyžadujících škálování, zatímco jiné součásti jsou používány méně.

Pomocí typického příkladu elektronického obchodování, co pravděpodobně budete potřebovat ke škálování, je součást informace o produktu. Mnoho dalších zákazníků prochází produkty, než je koupí. Další zákazníci používají svůj koš, než používá platební kanál. Méně zákazníkům přidávají komentáře nebo zobrazují historii jejich nákupu. A máte pravděpodobně pouze několik zaměstnanců v jedné oblasti, které potřebují spravovat obsah a marketingové kampaně. Díky škálování návrhu monolitické je veškerý kód nasazen několikrát.

Kromě problému "škálovat vše", změny jedné součásti vyžadují dokončení opětovného testování celé aplikace a úplné opětovné nasazení všech instancí.

Přístup k monolitické je společný a mnoho organizací vyvíjí s tímto přístupem k architektuře. Mnoho z nich má dostatečný dobrý výsledek, zatímco jiné jsou omezení na více počítačů. Řada navrhla své aplikace v tomto modelu, protože nástroje a infrastruktura byly příliš obtížné sestavovat architektury orientované na služby (SOA) a nemusely být potřebné, dokud se aplikace vypnula. Pokud zjistíte, že jste dosáhli limitu přístupu monolitické, rozbalíte aplikaci, aby ji bylo možné lépe využívat kontejnery a mikroslužby se může jednat o další logický krok.

![](./media/image5-14.png)

Nasazení aplikací monolitické v Microsoft Azure lze dosáhnout použitím vyhrazených virtuálních počítačů pro každou instanci. Pomocí [Azure Virtual Machine Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)můžete virtuální počítače snadno škálovat. [Azure App Services](https://azure.microsoft.com/services/app-service/) může spouštět aplikace v monolitické a snadno škálovat instance bez nutnosti správy virtuálních počítačů. Azure App Services může také spouštět jednotlivé instance kontejnerů Docker a zjednodušit tak nasazení. Pomocí Docker můžete nasadit jeden virtuální počítač jako hostitele Docker a spustit víc instancí. Pomocí služby Azure Balancer, jak je znázorněno na obrázku 5-14, můžete spravovat škálování.

Nasazení na různé hostitele je možné spravovat pomocí tradičních technik nasazení. Hostitele Docker je možné spravovat pomocí příkazů, jako je například **spuštění Docker** , a to prostřednictvím automatizace, jako jsou kanály pro průběžné doručování (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Aplikace monolitické nasazená jako kontejner

Existují výhody použití kontejnerů ke správě nasazení aplikací monolitické. Škálování instancí kontejnerů je mnohem rychlejší a jednodušší než nasazení dalších virtuálních počítačů. I v případě, že se k škálování virtuálních počítačů používá Virtual Machine Scale Sets, doba jejich instance trvá. Když se nasadí jako instance aplikace, bude se konfigurace aplikace spravovat jako součást virtuálního počítače.

Nasazování aktualizací jako imagí Docker je mnohem rychlejší a efektivně v síti. Image Docker obvykle začínají během sekund a urychlují uvádění. Zrušení instance Docker je stejně snadné jako vydávání `docker stop` příkazu, obvykle dokončení za méně než sekundu.

Vzhledem k tomu, že jsou kontejnery v podstatě neměnné, nemusíte si dělat starosti s poškozenými virtuálními počítači, zatímco skripty pro aktualizace se nemusí zapomenout na určitou konkrétní konfiguraci nebo soubor, který zůstal na disku.

Kontejnery Docker můžete použít k nasazení monolitické pro jednodušší webové aplikace. Tím se zlepší průběžná integrace a kanály průběžného nasazování a pomáhá dosáhnout úspěchu nasazení na produkční prostředí. Žádné další "na mém počítači funguje, proč nefunguje v produkčním prostředí?"

Architektura založená na mikroslužbách má spoustu výhod, ale tyto výhody přináší náklady na zvýšení složitosti. V některých případech náklady převažují nad výhodami, takže aplikace nasazení monolitické spuštěná v jednom kontejneru nebo v několika kontejnerech je lepší volbou.

Aplikace monolitické se možná snadno nedokáže snadno desestavit do dobře oddělených mikroslužeb. Mikroslužby by měly pracovat nezávisle na sobě, aby poskytovaly pružnější aplikaci. Pokud nemůžete doručovat nezávislé řezy funkcí aplikace, oddělení IT pouze zvyšuje složitost.

Aplikace nemusí ještě potřebovat škálování funkcí nezávisle. Mnoho aplikací, pokud potřebují škálovat nad rámec jedné instance, to může prozatím poměrně jednoduchý proces klonování celého instance. Další práce, která odděluje aplikaci do diskrétních služeb, poskytuje minimální přínos při škálování úplných instancí aplikace je jednoduché a nákladově efektivní.

V rané fázi vývoje aplikace možná nemáte jasný nápad, kde jsou hranice přirozené funkčnosti. Když vyvíjíte minimální životaschopný produkt, přirozené oddělení se ještě nemusí narazit. Některé z těchto podmínek můžou být dočasné. Můžete začít vytvořením aplikace v monolitické a později oddělit některé funkce, které se budou vyvíjet a nasazovat jako mikroslužby. Další podmínky můžou být nezbytné pro místo v oblasti problému aplikace, což znamená, že aplikace nemusí být nikdy rozdělená do více mikroslužeb.

Oddělení aplikace do mnoha diskrétních procesů také přináší režijní náklady. Oddělení funkcí do různých procesů je složitější. Komunikační protokoly se stanou složitější. Místo volání metod je nutné použít asynchronní komunikaci mezi službami. Při přesunu do architektury mikroslužeb je potřeba přidat spoustu stavebních bloků implementovaných ve verzi mikroslužeb aplikace eShopOnContainers: zpracování sběrnice událostí, odolnost zpráv a opakované pokusy, konečná konzistence a další.

Mnohem jednodušší [Referenční aplikace eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) podporuje použití kontejneru monolitické s jedním kontejnerem. Aplikace zahrnuje jednu webovou aplikaci, která zahrnuje tradiční zobrazení MVC, webová rozhraní API a Razor Pages. Tuto aplikaci lze spustit z kořene řešení pomocí `docker-compose build` příkazů a. `docker-compose up` Tento příkaz nakonfiguruje kontejner pro webovou instanci pomocí `Dockerfile` elementu nalezeného v kořenovém adresáři webového projektu a spustí kontejner na zadaném portu. Zdroj pro tuto aplikaci si můžete stáhnout z GitHubu a spustit místně. I tyto výhody aplikace v monolitické se nesadí do prostředí kontejneru.

U jednoho z kontejnerových nasazení znamená, že každá instance aplikace běží ve stejném prostředí. To zahrnuje vývojové prostředí, ve kterém se provádí předčasné testování a vývoj. Vývojový tým může spustit aplikaci v kontejnerovém prostředí, které odpovídá provoznímu prostředí.

Kromě toho se v kontejnerových aplikacích naškálují snížení nákladů. Použití prostředí kontejneru umožňuje větší sdílení prostředků než tradiční prostředí virtuálních počítačů.

Nakonec uzavření aplikace vynutí oddělení mezi obchodní logikou a serverem úložiště. Jak aplikace škáluje, budou se všechny kontejnery spoléhat na jedno fyzické paměťové médium. Toto paměťové médium by normálně představovalo Server s vysokou dostupností, na kterém běží databáze SQL Server.

## <a name="docker-support"></a>Podpora Docker

`eShopOnWeb` Projekt běží na .NET Core. Proto je možné jej spustit buď v kontejnerech se systémem Linux nebo Windows. Všimněte si, že pro nasazení Docker chcete pro SQL Server použít stejný typ hostitele. Kontejnery se systémem Linux umožňují menší nároky a jsou preferovány.

Pomocí sady Visual Studio 2017 nebo novější můžete přidat podporu Docker do existující aplikace tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a zvolíte **Přidat** > **podporu Docker**. Tím se přidají potřebné soubory a aplikace se upraví tak, aby se používaly. Aktuální `eShopOnWeb` ukázka již má tyto soubory na místě.

Soubor na úrovni `docker-compose.yml` řešení obsahuje informace o tom, jaké obrázky se mají sestavit a jaké kontejnery se mají spustit. Soubor umožňuje použít `docker-compose` příkaz ke spuštění více aplikací současně. V tomto případě se spouští pouze webový projekt. Můžete ji také použít ke konfiguraci závislostí, například samostatného kontejneru databáze.

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

Soubor odkazuje na `Dockerfile` v`Web`projektu. `docker-compose.yml` `Dockerfile` Slouží k určení, který základní kontejner bude použit a jakým způsobem bude aplikace konfigurována. `Web`: `Dockerfile`

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

# Optional: Set this here if not setting it from docker-compose.yml
# ENV ASPNETCORE_ENVIRONMENT Development

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Řešení potíží s Docker

Po spuštění kontejnerové aplikace bude nadále běžet, dokud ji nezastavíte. Pomocí `docker ps` příkazu můžete zobrazit kontejnery, které jsou spuštěny. Běžící kontejner můžete zastavit pomocí `docker stop` příkazu a zadáním ID kontejneru.

Všimněte si, že spuštěné kontejnery Docker mohou být vázány na porty, které můžete jinak zkusit použít ve vašem vývojovém prostředí. Pokud se pokusíte spustit nebo ladit aplikaci pomocí stejného portu jako běžícího kontejneru Docker, zobrazí se chyba s oznámením, že se server nemůže přivážet k tomuto portu. Poté by se měl tento problém vyřešit zastavením kontejneru.

Pokud chcete přidat podporu Docker do aplikace pomocí sady Visual Studio, ujistěte se, že je na něm spuštěný Docker Desktop. Průvodce nebude správně fungovat, pokud při spuštění Průvodce neběží dokovací plocha. Kromě toho průvodce prověřuje aktuální možnost kontejneru a přidá správnou podporu Docker. Pokud chcete přidat podporu pro kontejnery Windows, musíte spustit průvodce, když máte na počítači Docker běžící s nakonfigurovanými kontejnery Windows. Pokud chcete přidat podporu pro kontejnery pro Linux, spusťte průvodce, když máte k dispozici Docker s nakonfigurovanými kontejnery systému Linux.

### <a name="references--common-web-architectures"></a>Odkazy – společné webové architektury

- **Čistá architektura**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **Průsvitky**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Vzor úložiště**  
  <https://deviq.com/repository-pattern/>
- **Ukázka řešení čištění architektury**  
  <https://github.com/ardalis/cleanarchitecture>
- **Elektronická kniha – architekti mikroslužeb**  
  <https://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
>[Předchozí](architectural-principles.md)Další
>[](common-client-side-web-technologies.md)
