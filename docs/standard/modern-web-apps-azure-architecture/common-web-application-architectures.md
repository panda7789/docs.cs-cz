---
title: Společné architektury webové aplikace
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Microsoft Azure | společné architektury webové aplikace
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 911935379fd126ccbafe825a6ce4049c2e9b5cde
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="common-web-application-architectures"></a>Společné architektury webové aplikace

> "Pokud se domníváte, že je dobré architektura náročná, zkuste architektura chybné."  
> _-Brian zápatí a Joseph Yoder_

## <a name="summary"></a>Souhrn

Většina tradičních aplikací .NET jsou nasazeny jako jedné jednotky odpovídající spustitelný soubor nebo jedné webové aplikace běžící v rámci jedné domény aplikace služby IIS. Toto je nejjednodušší model nasazení a velmi dobře slouží mnoho interních a veřejných menší aplikací. Ale i zadána tato jedné jednotky nasazení nejvíce netriviální obchodních aplikací těžit z některé logického oddělení do několika vrstev.

## <a name="what-is-a-monolithic-application"></a>Co je monolitický aplikace?

Monolitický aplikace je ten, který je zcela samostatné, z hlediska své chování. Může komunikovat s další služby nebo datové úložiště v průběhu provádění jeho operací, ale základní své chování běží v rámci vlastní proces a bude celá aplikace se obvykle nasazují jako na jednu jednotku. Pokud je takové aplikace je potřeba škálovat horizontálně, obvykle v celé aplikaci duplicitní mezi více serverů nebo virtuální počítače.

## <a name="all-in-one-applications"></a>Aplikace: 1

Nejmenší možný počet projekty pro architekturu aplikace je jedna. V této architektuře celý logiku aplikace obsažené v jednom projektu, zkompilovány do jednoho sestavení a nasadit jako na jednu jednotku.

Nový projekt ASP.NET Core, vytvořené v sadě Visual Studio nebo z příkazového řádku, spustí jako jednoduchý monolitu "vše v jednom". Obsahuje všechny chování aplikace, včetně přístupu logiku prezentační, obchodní a data. Obrázek 5-1 zobrazuje strukturu souborů jednoprojektové aplikace.

**Obrázek 5-1.** Jeden projektu aplikace ASP.NET Core

![](./media/image5-1.png)

V případě jedné projektu oddělené oblasti zájmu se dosahuje prostřednictvím složky. Výchozí šablony obsahuje samostatné složky pro odpovědnosti vzor MVC modely, zobrazení, a řadiče, a také další složky pro Data a služby. V tomto případě prezentace podrobnosti by měl být omezeny co nejvíce do složky, zobrazení a podrobnosti implementace přístup data by měla být omezená na třídy zachovány ve složce Data. Obchodní logika by měl být umístěn v služeb a tříd v rámci složku modely.

I když je jednoduchý, má monolitický řešení jednoprojektové některé nevýhody. S růstem velikost a složitost projektu pořád roste s tím také počet souborů a složek. Otázky uživatelského rozhraní (modely, zobrazení, řadiče) jsou umístěny ve více složkách, které nejsou seskupeny podle abecedy. Tento problém jenom získá zhoršení, když další konstruktory úrovni uživatelského rozhraní, jako jsou filtry nebo ModelBinders, se přidají do vlastních složek. Obchodní logika je různých mezi složkami modely a služby, a není není jasný náznak, které by měl třídy v složky, které závisí na které jiné. Kvůli chybějící organizace na úrovni projektu často vede k [špagety kód](http://deviq.com/spaghetti-code/).

Aby bylo možné tyto problémy řeší aplikace často momentální do řešení vícenásobného projektu, kde se každý projekt, považuje se nacházejí v konkrétní *vrstvy* aplikace.

## <a name="what-are-layers"></a>Jaké jsou vrstvy?

Jelikož aplikace v složitost, jeden způsob, jak spravovat této složitost je rozdělit aplikace podle jeho odpovědnosti nebo připomínky. To odpovídá oddělení Princip otázky a pomoct chránit rostoucí codebase uspořádaná tak, aby vývojáři mohli snadno najít, kde je implementováno určité funkce. Vrstvená architektura nabízí řadu výhod nad rámec právě kód organizaci, ale.

Podle uspořádání kódu do vrstvy, můžete znovu použít běžné funkce nízké úrovně v celé aplikaci. Vzhledem k tomu, znamená to, že méně kódu potřeba zapsat a můžou aplikace pro standardizaci na jediná implementace, podle SUCHÝCH zásady, je vhodné tuto opakované použití.

S Vrstvená architektura aplikace můžete vynutit omezení, na kterých vrstvy může komunikovat s jiných vrstev. To pomáhá zajistit zapouzdření. Když vrstvu změní nebo nahradit, by měl mít vliv pouze vrstvy, které s ním pracovat. Omezením, které závisí vrstvy, na kterých lze zmírnit jiných vrstev dopad změny, aby jediné změny nebude mít vliv na celou aplikaci.

Vrstvy (a zapouzdření) bylo mnohem snazší nahradit funkcionalitu v rámci aplikace. Například aplikace může původně trvalosti použít svou vlastní databázi systému SQL Server, ale později může zvolit strategie trvalost založené na cloudu, nebo jeden za webového rozhraní API. Pokud aplikace má správně zapouzdřené jeho implementace trvalost v rámci logické vrstvy, může být nahrazen novou implementace stejné veřejné rozhraní této konkrétní vrstvy systému SQL Server.

Kromě potenciálně záměnu implementace v reakci na budoucí změny v požadavcích vrstvy aplikace můžete taky usnadňují vyměnit implementace pro účely testování. Místo nutnosti psaní testy, které provozují proti skutečná data vrstvy nebo uživatelského rozhraní aplikace, tyto vrstvy můžou nahradit během testu falešných implementace, které poskytují známé odpovědí na požadavky. Testy díky obvykle mnohem snazší k zápisu a mnohem rychlejší spusťte ve srovnání s spuštěná testy znovu skutečné infrastruktury aplikace.

Logické rozvrstvení je běžný postup pro zlepšení organizace kódu v podnikových aplikacích softwaru a existuje několik způsobů, ve kterých mohou být uspořádány kód do vrstvy.

> [!NOTE]
> *Vrstvy* představují logického oddělení v aplikaci. V případě, že logiku aplikace je fyzicky distribuován do samostatné servery nebo procesy, tyto cíle samostatné fyzické nasazení se označují jako *vrstev*. Je možné a celkem běžné tak, aby měl N-Layer aplikaci, která je nasazena na jedné vrstvě.

## <a name="traditional-n-layer-architecture-applications"></a>Tradiční "N-Layer" Architektura aplikace

Nejběžnější organizace aplikace logiky do vrstvách je znázorněno na obrázku 5-2.

**Obrázek 5-2.** Typická aplikace vrstvy.

![](./media/image5-2.png)

Tyto vrstvy jsou často se používá zkratka jako uživatelského rozhraní, BLL (vrstvu obchodní logiky) a DAL (Data Access Layer). Pomocí této architektury, uživatelé provádět požadavky prostřednictvím uživatelského rozhraní vrstvy, která komunikuje jenom s BLL. BLL, pak můžete volat DAL data žádosti o přístup. Vrstva uživatelského rozhraní neměli provádět všechny požadavky vrstvy DAL přímo, ani musí komunikovat s trvalost přímo přes jiným způsobem. Podobně BLL by měla pouze pracovat s trvalost projít DAL. Tímto způsobem každé vrstvě má vlastní dobře známé zodpovědnost.

Jednou z nevýhod tohoto přístupu tradiční rozvrstvení je, že kompilaci závislosti shora dolů. To znamená vrstvě uživatelského rozhraní závisí na BLL, což závisí na DAL. To znamená, že BLL, což obvykle obsahuje nejdůležitější logiku v aplikaci, je závislá na podrobnosti implementace přístup dat (a často na existenci databáze). Testování obchodní logiku v takové architekturu je často složité, vyžadování testovací databáze. Princip inverzi závislosti lze použít a tento problém vyřešit, jak uvidíte v další části.

Obrázek 5-3 ukazuje řešení s příklad nejnovější aplikace do tří projektů odpovědnost (nebo layer).

**Obrázek 5-3.** Jednoduché monolitický aplikace pomocí tří projektů.

![](./media/image5-3.png)

I když tato aplikace používá několik projektů pro účely organizace, je stále nasazen jako na jednu jednotku a jeho klienty bude pracovat s ním jako jednu webovou aplikaci. To umožňuje velmi jednoduché nasazení procesu. Obrázek 5-4 ukazuje, jak může být taková aplikace hostované pomocí služby Windows Azure.

![](./media/image5-4.png)

**Obrázek 5 – 4.** Jednoduché nasazení webové aplikace Azure

Jak aplikace potřebuje, růst, mohou být vyžadovány komplexní a robustní řešení nasazení. Obrázek 5-5 ukazuje příklad složitější plán nasazení, který podporuje další funkce.

![](./media/image5-5.png)

**Obrázek 5-5.** Nasazení webové aplikace do Azure App Service

Tento projekt organizace do více projektů podle odpovědnost interně, zlepšuje udržovatelnosti aplikace.

Tato jednotka je možné rozšířit nebo horizontálně navýšit kapacitu Pokud chcete využít výhod cloudových škálovatelnost na vyžádání. Rozšiřování prostředků znamená přidávání dalších procesoru, paměti, místa na disku nebo jiným prostředkům na server(y) hostování vaší aplikace. Škálování znamená, přidávání dalších instancí těchto serverů, zda se jedná o fyzických serverech nebo virtuálních počítačů. Pokud je vaše aplikace hostované ve více instancích, nástroj pro vyrovnávání zatížení se používá k požadavky přiřadit instance jednotlivých aplikací.

Nejjednodušším přístupem při škálování webové aplikace v Azure je nakonfigurovat ručně škálování v plánu služby aplikace App Service. Obrázek 5 a 6 zobrazit obrazovce odpovídající řídicí panel Azure nakonfigurovat, kolik instancí slouží k aplikaci.

![](./media/image5-6.png)

**Obrázek 5 a 6.** Plán služby App Service škálování v Azure.

## <a name="clean-architecture"></a>Vyčištění architektura

Aplikace, které následují v inverzi Princip závislostí, jakož i Principy návrhu Domain-Driven (DDD) zpravidla přicházejí na podobnou architekturu. Tato architektura se příliš mnoho názvy průběhu let. Jeden ze zadaných názvů první byl šestiúhelníkový architekturu, za nímž následuje adaptéry a porty. Nedávno, je byla citovalo jako [průsvitek architektura](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) nebo [čisté architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Je tento poslední název čistou architektura, která slouží jako základ pro popis architektury v této příručce e.

> [!NOTE]
> Termín čistou architektura lze použít k aplikacím, které jsou vytvořené pomocí také zásady DDD, ty, které nejsou sestavené pomocí DDD. V případě dřívějším, může být tato kombinace označovány jako "Čistou DDD architektura".

Vyčištění architektura převádí model obchodní logiky a aplikace v centru aplikace. Místo nutnosti obchodní logiky, závisí na přístup k datům nebo jiných příčin infrastruktury, je obrácený tuto závislost: Podrobnosti o infrastruktury a implementace závisí na základní aplikace. Toho dosáhnete tak, že definujete abstrakce nebo rozhraní, klíčové aplikace, které jsou pak implementované pro typy definované v vrstvě infrastruktury. Běžný způsob vizualizace této architektury je použití řadu soustředných kroužky, podobně jako průsvitek. Obrázek 5 X ukazuje příklad tento styl architektury reprezentace.

![](./media/image5-7.png)

**Obrázek 5 – 7.** Vyčištění architektura; zobrazení průsvitek

V tomto diagramu toku závislostí směrem k nejvnitřnější kruhu. Proto se zobrazí, že základní aplikace (která má svůj název od pozice základem této diagramu) nemá žádné závislosti na jiných vrstev aplikace. V centru velmi jsou entity a rozhraní aplikace. Právě mimo, ale stále v základní aplikace jsou služby domény, obvykle implementující rozhraní definované v informacích o vnitřní kruh. Mimo aplikaci základní uživatelské rozhraní a infrastruktura vrstvy, které závisí na základní aplikaci, ale není na sebe navzájem (nutně).

Obrázek 5 X znázorňuje tradičnější diagram vodorovné vrstev, který lépe závislosti mezi uživatelského rozhraní a jiných vrstev.

![](./media/image5-8.png)

**Obrázek 5-8.** Vyčištění architektura; zobrazení vodorovné vrstvy

Všimněte si, že plnou šipky představují kompilaci závislosti, zatímco přerušovanou šipku představuje závislost pouze modul runtime. Pomocí architektuře čistého, vrstvě uživatelského rozhraní funguje s rozhraními definované v základní aplikace v době kompilace a v ideálním případě by neměl mít žádnou znalost typy implementace definované v vrstvě infrastruktury. Za běhu ale tyto typy implementace se bude vyžadovat pro aplikaci spustit, tak budou muset být přítomna a drátové až rozhraní základní aplikace pomocí vkládání závislostí.

Obrázek 5-9 ukazuje podrobnější pohled na architekturu aplikace ASP.NET Core při sestavení následující tato doporučení.

![Architektura jádra ASPNET](./media/image5-9.png)

**Obrázek 5-9.** Diagram architektury ASP.NET Core následující čistou architektura.

Protože základní aplikace nezávisí na infrastrukturu, je velmi snadné zápis testů částí automatizované pro tuto vrstvu. Následující obrázky 5 až 10 a 5 11 ukazují, jak testy nevejde se do této architektury.

![UnitTestCore](./media/image5-10.png)

**Obrázek 5-10.** Testování aplikací jádra v izolaci částí.

![IntegrationTests](./media/image5-11.png)

**Obrázek 5-11.** Integrace testování implementace infrastruktury s externími závislostmi.

Vzhledem k tomu, že vrstva uživatelského rozhraní neobsahuje žádné přímé závislost na typy definované v projektu infrastruktury, je rovněž velmi snadné odkládacího souboru se implementace, buď usnadňuje testování nebo v reakci na měnící se požadavky na aplikace. Předdefinované použití a podpora pro vkládání závislostí ASP.NET Core díky této architektury za nejvhodnější způsob, jak struktura netriviální monolitický aplikace.

Pro monolitický aplikace jsou všechny projekty základní aplikaci, infrastruktury a uživatelské rozhraní spustit jako jednu aplikaci. Architektura modulu runtime aplikace může vypadat jako obrázek 5-12.

![Architektura jádra ASPNET 2](./media/image5-12.png)

**Obrázek 5-12.** Architektura aplikace ukázka ASP.NET Core runtime.

### <a name="organizing-code-in-clean-architecture"></a>Uspořádání kódu v architektuře čistého

V čisté Architektura řešení každý projekt má zrušte odpovědnosti. Jako takový bude určité typy patří do každého projektu a často zjistíte složky odpovídající tyto typy v příslušné projektu.

Základní aplikace obsahuje obchodní model, který obsahuje entity, služeb a rozhraní. Tato rozhraní zahrnují abstrakce pro operace, které bude možné provést pomocí infrastruktury, například přístup k datům, přístupu k systému souborů, volání sítě atd. Pro práci s nonentity typy, které nemají žádné závislosti na uživatelského rozhraní nebo infrastruktury nutné někdy služby nebo rozhraní definované v této vrstvě. To může být definováno jako jednoduché objekty Data Transfer (DTOs).

> ### <a name="application-core-types"></a>Základní typy aplikací
> -   Entity (obchodní model třídy, které jsou nastavené jako trvalé)
> -   Rozhraní
> -   Služby
> -   DTOs

Projekt infrastruktury by měl obvykle zahrnovat implementace přístup data. V typické webové aplikace ASP.NET Core to bude zahrnovat data přístup implementace třídy Entity Framework DbContext, všechny migrace EF jádra, které byly definovány a. Nejběžnější způsob abstraktní data přístup implementace kód je prostřednictvím [vzor návrhu úložiště](http://deviq.com/repository-pattern/).

Kromě dat implementace přístup musí obsahovat projektu OMI implementace služeb, které musí spolupracovat s riziko z hlediska infrastruktury. Tyto služby musí implementovat rozhraní definované v základní aplikace, a proto infrastruktury by měl mít odkaz na projekt aplikace jádra.

> ### <a name="infrastructure-types"></a>Typy infrastruktury
> -   Základní typy EF (DbContext, migrace)
> -   Přístup k datům implementace typů (úložiště)
> -   Specifické pro infrastrukturu služby (FileLogger, SmtpNotifier atd.)

V aplikaci ASP.NET MVC základní uživatelské rozhraní vrstvě bude vstupní bod pro aplikaci a bude projektu aplikace ASP.NET MVC jádra. Tento projekt by měl odkazovat projektu základní aplikace a typy jejího musí komunikovat s infrastrukturou výhradně prostřednictvím rozhraní definované v základní aplikace. Žádné přímé vytváření instancí (nebo statické volání) musí být povolené typy vrstvy infrastruktury ve vrstvě uživatelského rozhraní.

> ### <a name="ui-layer-types"></a>Typy vrstvy uživatelského rozhraní
> -   Kontrolery
> -   Filtry
> -   zobrazení
> -   ViewModels
> -   Spuštění

Třída při spuštění je zodpovědný pro konfiguraci aplikace a kabeláž typů implementace rozhraní, což vkládání závislostí v době běhu správně fungovat.

> [!NOTE]
> Aby bylo možné propojit až vkládání závislostí v ConfigureServices v souboru Startup.cs projektu uživatelského rozhraní, možná muset projektu odkazovat projektu OMI. Tuto závislost jde je eliminovat snadno pomocí vlastní DI kontejner. Pro účely tohoto příkladu je nejjednodušší je umožnit uživatelského rozhraní projekt, který má odkazovat na projektu OMI.

## <a name="monolithic-applications-and-containers"></a>Monolitický aplikace a kontejnery 

Můžete sestavit jeden a monolitický nasazení založené na webové aplikace nebo služby a nasaďte ho jako kontejner. V aplikaci nemusí být monolitický ale uspořádány do několika knihovny, komponenty nebo vrstvy. Externě je jediný kontejner jako jeden proces, jednu webovou aplikaci nebo jedné služby.

Ke správě tohoto modelu, můžete nasadit jediný kontejner k reprezentaci aplikace. Pokud chcete použít škálování, stačí přidáte další kopie pro vyrovnávání zatížení vpředu. Jednoduchost pochází z Správa jedno nasazení v jedné kontejneru nebo virtuálních počítačů.

![](./media/image5-13.png)

Můžete zahrnout více součásti nebo knihovny nebo interní vrstvy v rámci každý kontejner, jak je znázorněno na obrázku 5-X. Objekt zabezpečení kontejneru, ale následující *"kontejner nepodporuje jednou z věcí a nemá v jednom procesu*", monolitický vzor může dojít ke konfliktu.

Nevýhodou tohoto přístupu dodává Pokud/při zvětšování aplikace vyžadující ji škálovat. Pokud bude celá aplikace škálovat, není skutečně problém. Ve většině případů několik součástí aplikace jsou však, že body potlačení nutnosti škálování, zatímco ostatní součásti jsou používá menší.

Pomocí příklad typické elektronické obchodování; Co je pravděpodobně potřeba škálování je součást informace o produktu. Mnoho zákazníků další Procházet produkty než jejich zakoupení. Další zákazníci využívat nákupního košíku než použití kanálu platba. Méně zákazníky přidání komentářů nebo zobrazit historii jejich nákupu. A pravděpodobně pouze existuje více zaměstnancům, najdete v jedné oblasti, která potřebují spravovat obsah a marketingových kampaní. Pomocí příjmu monolitický návrhu, všechny kód nasazen vícekrát.

Kromě měřítka všechno, co problém, změny jedinou komponentu vyžadují opětovném dokončení testování v celé aplikaci a dokončení opětovného nasazení všech instancí.

Monolitický přístup je běžné a mnoha organizacích jsou vývoj s tímto přístupem architektury. Mnoho mají s vhodné dostatek výsledky, zatímco ostatní nedosáhli limitů. Mnoho určená svých aplikací v tomto modelu, protože nástroje a infrastruktura byly příliš složité sestavení architektury služby zaměřené na konkrétní (SOA) a nebylo uvidí potřeba – dokud vzrostla aplikace. Pokud zjistíte, že jste nedosáhli limitů monolitický přístupu, může být rozdělení aplikace k tomu, aby lépe využít kontejnery a mikroslužeb logické dál.

![](./media/image5-14.png)

Nasazení monolitický aplikací v Microsoft Azure se dá dosáhnout pomocí vyhrazených virtuálních počítačích pro každou instanci. Pomocí [škálovatelné sady virtuálních počítačů Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), je možné snadno škálovat virtuálních počítačů. [Azure App Services](https://azure.microsoft.com/services/app-service/) můžete spouštět monolitický aplikace a snadno škálovat instance bez nutnosti ke správě virtuálních počítačů. Azure App Services můžete spustit jedné instance Docker kontejnery také, což výrazně zjednodušuje nasazení. Pomocí Docker, můžete nasadit jeden virtuální počítač jako hostitele Docker a spustit víc instancí. Pomocí nástroje pro vyrovnávání Azure, jak je znázorněno v obrázku 5-14, můžete spravovat škálování.

Nasazení do různých hostitelů lze spravovat pomocí techniky tradiční nasazení. Hostitelů Docker lze spravovat pomocí příkazů jako **docker spustit** provést ručně, nebo prostřednictvím automatizace, jako je nepřetržitá doručení (CD) kanálů.

### <a name="monolithic-application-deployed-as-a-container"></a>Monolitický aplikace nasazena jako kontejner

Existují výhody použití kontejnerů ke správě nasazení monolitický aplikací. Změna velikosti instancí kontejnerů je mnohem rychlejší a snadnější než nasazení dalších virtuálních počítačů. I když se používá škálovatelné sady virtuálních počítačů škálování virtuálních počítačů, jejich trvat dobu k instanci. Při nasazení jako instance aplikace, je konfigurace aplikace spravované v rámci virtuálního počítače.

Nasazení aktualizací, jako je mnohem rychlejší imagí Dockeru a efektivní sítě. Imagí dockeru obvykle spuštění v sekundách, rychlosti zavedení uživatelům. Zrušení Docker instance je stejně snadná jako vystavování **docker zastavení** příkazu, obvykle dokončení menší než za sekundu.

Jako kontejnery jsou ze své podstaty neměnné záměrné, nikdy musíte si dělat starosti poškozená virtuálních počítačích, zatímco skriptů pro aktualizaci zapomněl účet pro některé specifické konfigurace nebo vlevo soubor na disku.

Při monolitický aplikace využívat Docker, rozdělení monolitický aplikaci do dílčí systémy, které je možné rozšířit, vyvíjí a nasadit samostatně může být vašim vstupním bodem do sféru mikroslužeb.

> ### <a name="references--common-web-architectures"></a>Odkazy – společné architektury webové
> - **Vyčištění architektura**  
> <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **Architektura průsvitek**  
> <http://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **Vzor úložiště**  
> <http://deviq.com/repository-pattern/>
> - **Vyčištění ukázkové architektury řešení**  
> <https://github.com/ardalis/cleanarchitecture>
> - **Elektronická kniha Mikroslužeb architektury** <http://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
[Předchozí] (architectural-principles.md) [Další] (common-client-side-web-technologies.md)
