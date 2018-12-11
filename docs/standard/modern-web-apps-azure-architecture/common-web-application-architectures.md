---
title: Běžné architektury webových aplikací
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Prozkoumejte běžné architektury webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 3b0b109b0910eb5763ecab228115b7bc932d4a10
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129932"
---
# <a name="common-web-application-architectures"></a>Běžné architektury webových aplikací

> "Pokud se domníváte, že je dobré architektura nákladné, zkuste chybný architektury."  
> _– Brian zápatí a Joseph Yoder_

Většina tradičních aplikací rozhraní .NET jsou nasazeny jako jedné jednotky odpovídající spustitelný soubor nebo jednu webovou aplikaci spuštěnou v rámci jedné domény aplikace služby IIS. Toto je nejjednodušší model nasazení a velmi dobře slouží řada aplikací menší veřejné a vnitřní. Ale i směru tato jedna jednotka nasazení, většina netriviální obchodních aplikací těžit z některé logické rozdělení do několika vrstev.

## <a name="what-is-a-monolithic-application"></a>Co je u monolitické aplikace?

Monolitické aplikace je ten, který je zcela nezávislý, z hlediska své chování. Může komunikovat s dalšími službám nebo datům úložišti v průběhu provádění jeho operací, ale základní chování aplikace běží v rámci svého vlastního procesu a celá aplikace je obvykle nasazeni jako jeden celek. Pokud takové aplikace potřebuje k horizontálnímu škálování, obvykle bude celá aplikace je duplicitní v rámci více serverů nebo virtuálních počítačů.

## <a name="all-in-one-applications"></a>Aplikace: 1

Nejmenší možný počet projektů pro architekturu aplikace patří. V této architektuře celý logiku aplikace je obsažená v jednom projektu zkompilován do jednoho sestavení a nasazených jako celek.

Nový projekt ASP.NET Core, vytvořené v sadě Visual Studio nebo z příkazového řádku, je na začátku jako jednoduchý monolitu "vše v jednom". Obsahuje všechny chování aplikace, včetně logikou přístupu prezentační, obchodní a datové sady. Obrázek 5-1 zobrazuje strukturu souborů z jednoho projektu aplikace.

![](./media/image5-1.png)

**Obrázek 5-1.** Jednoho projektu aplikace ASP.NET Core.

V případě jediného projektu v oddělení oblastí zájmu je dosaženo pomocí složky. Výchozí šablona obsahuje samostatné složky pro vzor odpovědnosti modelů, zobrazení a Kontrolerů MVC, stejně jako další složky pro Data a služby. V tomto případě by měla být omezena prezentace podrobnosti co nejvíc do zobrazení složky a podrobnosti implementace přístupu dat by měla být omezena na třídy, které jsou uloženy ve složce Data. Obchodní logika by měl být uložený v třídy v rámci složky modelů a služeb.

I když je jednoduché, monolitické řešení jednoprojektové má některé nevýhody. Nárůstu velikosti a složitosti projektu, bude počet souborů a složek i růst. Rozhraní (UI) obavy uživatelů (modelů, zobrazení, kontrolery) jsou umístěny v více složek, které nejsou seskupeny podle abecedy. Tento problém pouze získá horší, když se další úroveň uživatelského rozhraní konstruktorů, jako jsou filtry nebo ModelBinders, jsou přidány do jejich vlastních složek. Obchodní logika je rozmístěno jinde mezi složkami modelů a služeb, a není není jasný náznak, z nichž třídy do složky, které by neměly být závislé na které ostatní. Tato nedostatečná organizace na úrovni projektu často vede k [špagety kód](https://deviq.com/spaghetti-code/).

Pro řešení těchto problémů, často vyvíjet aplikace do multiprojektových řešení, kde je považován za každý projekt uložená v konkrétní _vrstvy_ aplikace.

## <a name="what-are-layers"></a>Co jsou vrstvy?

Jak aplikace jejich složitost v, je jeden způsob, jak spravovat složitost rozdělte aplikace podle její odpovědnosti nebo připomínky. Následuje oddělení hlavní otázky a pomoct chránit rostoucí základu kódu uspořádané tak, aby vývojáři mohli snadno najít, kde je implementovat určité funkce. Vrstvené architektury nabízí několik výhod nad rámec právě kódu organizace, i když.

Uspořádáním kódu do vrstev lze opětovně použít běžné funkce nízké úrovně v celé aplikaci. Použití je výhodné, protože to znamená méně kódu musí být napsaný, a proto ji povolí aplikaci používají jako standard jedna implementace, po [Neopakovat sami (zkušební)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) zásadě.

Pomocí vrstev architektury můžete aplikace vynucovat omezení, na které vrstvy mohou komunikovat s jinými vrstvami. To pomáhá zajistit zapouzdření. Když vrstvu je změnit nebo nahradit, by měla mít vliv pouze vrstvy, které s ním pracovat. Tím, že omezíte, které vrstvy závisí, na kterých můžete minimalizovat jinými vrstvami, dopad změn, tak, aby jeden změna nebude mít vliv na celou aplikaci.

Vrstvy (a zapouzdření) to značně zjednodušují nahrazují funkce v rámci aplikace. Aplikace například může zpočátku používat vlastní databázi systému SQL Server pro trvalost, ale později může zvolit strategii trvalost založené na cloudu, nebo jeden za webového rozhraní API. Pokud aplikace nemá správně zapouzdřené jeho implementace trvalého v rámci logické vrstvy, mohla být, že systém SQL Server zvláštní vrstva nahrazena novou implementaci stejné veřejné rozhraní.

Kromě potenciál záměnu implementace v reakci na budoucí změny v požadavcích aplikace může také usnadňují vyměnit implementace pro účely testování. Namísto nutnosti psát testy, které pracují na skutečné datové vrstvy nebo vrstvě uživatelského rozhraní aplikace, lze tyto vrstvy nahradit v době testu s falešnou implementace, které poskytují známé odpovědí na požadavky. Testy díky obvykle mnohem jednodušší zápis a mnohem rychlejší spouštění ve srovnání s spuštění testů znovu aplikace skutečný infrastruktury.

Logické vrstvení je běžná technika pro zlepšení organizaci kódu v oddílu podnikové aplikace softwaru a existuje několik způsobů, jimiž kódu je možné uspořádat do vrstvy.

> [!NOTE]
 > _Vrstvy_ představují logické oddělení v rámci aplikace. V případě, že aplikace logiky je fyzicky distribuovány na samostatných serverech nebo procesy, tyto cíle samostatné fyzické nasazení se označují jako _úrovně_. Je možné a celkem běžné, aby N vrstvy aplikace, která se nasadí do jedné vrstvě.

## <a name="traditional-n-layer-architecture-applications"></a>Tradiční aplikace s architekturou "N-vrstva"

Nejběžnější organizace aplikace logiky do vrstvy se zobrazí obrázek 5-2.

![](./media/image5-2.png)

**Obrázek 5-2.** Typická aplikace vrstvy.

Tyto vrstvy jsou často se zkracuje jako uživatelského rozhraní, vrstvu obchodní logiky () knihoven BLL a DAL (Data Access Layer). Pomocí této architektury, uživatelům provádět požadavky prostřednictvím vrstvě uživatelského rozhraní, která komunikuje jenom s BLL. BLL, pak můžete volat DAL data žádosti o přístup. Vrstvě uživatelského rozhraní neměli provádět všechny požadavky vrstvy DAL přímo ani by měl pracovat s trvalostí přímo prostřednictvím jiným způsobem. Podobně BLL by měl pouze pracovat s trvalostí prostřednictvím vrstvy DAL. Tímto způsobem každá vrstva má svou vlastní dobře známé odpovědnost.

Jednou z nevýhod tohoto přístupu tradiční vrstvení je, že závislostí kompilace v horní části do dolní části. To znamená vrstvě uživatelského rozhraní závisí na BLL, která závisí na vrstvy DAL. To znamená, že BLL, který obvykle obsahuje nejdůležitější logiky v aplikaci, je závislá na podrobnosti implementace přístupu dat (a často na existenci databáze). Testování obchodní logiku v takové architektury je často obtížné, které vyžadují testovací databázi. Princip inverzi závislostí lze použít k vyřešení tohoto problému, jak uvidíte v další části.

Obrázek 5 – 3 ukazuje příklad řešení, rozdělení aplikace do tří projektů odpovědnost (nebo vrstvy).

![](./media/image5-3.png)

**Obrázek 5 – 3.** Jednoduché monolitické aplikace pomocí tří projektů.

I když se tato aplikace používá několik projektů pro účely organizace, stále je nasazen jako jednu jednotku a jeho klienti budou pracovat s ním jako jednu webovou aplikaci. To umožňuje proces velmi jednoduché nasazení. Obrázek 5 – 4 ukazuje, jak mohou být takové aplikace hostované pomocí Azure.

![](./media/image5-4.png)

**Obrázek 5 – 4.** Jednoduché nasazení webové aplikace Azure

Jak rostou potřeby aplikace, může být složité a robustní řešení nasazení požadováno. Obrázek 5 až 5 ukazuje příklad složitější plánu nasazení, který podporuje další funkce.

![](./media/image5-5.png)

**Obrázek 5 – 5.** Nasazení webové aplikace do služby Azure App Service

Tento projekt organizace do více projekty založené na odpovědnost interně, zvyšuje udržovatelnost aplikace.

Tato jednotka je možné škálovat směrem nahoru nebo navýšení kapacity využívat škálovatelnost na vyžádání založené na cloudu. Vertikální navýšení kapacity znamená, že přidáte další procesor, paměť, místo na disku nebo další prostředky na serverech, které hostují vaši aplikaci. Horizontální navýšení kapacity znamená, že přidávání dalších instancí těchto serverů, ať už jde o fyzických serverech nebo virtuálních počítačů. Když aplikace běží na několika instancích, nástroj pro vyrovnávání zatížení slouží k přiřazení požadavků k instance jednotlivých aplikací.

Nejjednodušším přístupem při škálování webové aplikace v Azure je nakonfigurovat ručně škálování v plánu služby vaší aplikace App Service. Obrázek 5 – 6 se zobrazuje obrazovka odpovídající řídicí panel Azure nakonfigurovat, kolik instancí má aplikace.

![](./media/image5-6.png)

**Obrázek 5 a 6.** Plán služby App Service škálování v Azure.

## <a name="clean-architecture"></a>Vyčištění architektury

Můžete přejít na podobnou architekturu mají tendenci aplikací podle principu inverzi závislostí, jakož i principů návrhu Domain-Driven (DDD). Tato architektura se dostaly celou řadu názvů v průběhu let. Jeden z názvů první byl šestiúhelníkový architektury, za nímž následuje adaptéry a porty. Nedávno, je byl uvedený jako [průsvitek architektura](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) nebo [čisté architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Tento název, vyčistit architektury, se používá jako název pro tuto architekturu v této e knihy.

> [!NOTE]
> Termín čisté architekturu je možné použít pro aplikace, které se vytvářejí pomocí DDD zásady stejně jako ty, které nejsou sestavené pomocí DDD. V případě nejprve, může být tato kombinace označovány jako "Architektuře čistého DDD".

Vyčistit architektuře umístí obchodní logiky a aplikace modelu v Centru pro aplikace. Namísto toho, aby obchodní logika závisí na přístup k datům nebo jiných starostí o infrastrukturu, je obrácený této závislosti: infrastruktury a podrobnosti implementace závisí na základní aplikace. Toho dosáhnete tak, že definujete abstrakce, rozhraní, nebo v samotném aplikace, které jsou následně implementované typy definované ve vrstvě infrastruktury. Běžný způsob vizualizace tato architektura je použít řadu soustředných kruhy, podobně jako průsvitek. Obrázek 5 – 7 ukazuje příklad tohoto stylu architektury reprezentace.

![](./media/image5-7.png)

**Obrázek 5 – 7.** Vyčistit architektura; průsvitek zobrazení

V tomto diagramu závislosti tok směrem k nejvnitřnější kruh. Jádro aplikace trvá jeho název z jeho pozice v jádru tento diagram. A můžete zobrazit v diagramu, jádro aplikace nemá žádné závislosti na ostatních aplikačních vrstev. Entity aplikace a rozhraní jsou velmi uprostřed. Pouze mimo, ale stále v základní aplikaci jsou služby domain services, které obvykle implementují rozhraní definované v vnitřního kroužku. Mimo jádro aplikace uživatelského rozhraní a infrastruktura vrstvy závisí na základní aplikaci, ale ne na sebe navzájem (nemusí).

Obrázek 5 – 8 ukazuje tradičnější diagram vodorovné vrstev, která lépe odpovídá závislost mezi uživatelského rozhraní a dalšími vrstvami.

![](./media/image5-8.png)

**Obrázek 5 až 8.** Vyčistit architektura; horizontální vrstvy zobrazení

Všimněte si, že solid šipky představují závislosti za kompilace, zatímco představuje přerušovanou šipku závislosti jen pro modul runtime. S čistou architekturou vrstvě uživatelského rozhraní pracuje s rozhraní definované v samotném aplikace v době kompilace a v ideálním případě by neměla vědět o implementaci typů definovaných ve vrstvě infrastruktury. V době běhu ale tyto typy implementace jsou aplikace provést, vyžaduje, musí mít k dispozici i tradiční sítě až po aplikace základní rozhraní pomocí vkládání závislostí.

Obrázek 5 až 9 ukazuje podrobnější zobrazení architektury aplikace ASP.NET Core při sestavení po těchto doporučení.

![Architektura jádra ASPNET](./media/image5-9.png)

**Obrázek 5 až 9.** Diagram architektury ASP.NET Core po vyčištění architektury.

Protože základní aplikace nejsou závislé na infrastruktuře, je velmi jednoduše můžete vytvořit automatizované testy jednotky pro tuto vrstvu. Hodnoty 5 až 10 a 11. 5 ukazují, jak přizpůsobit testy do této architektury.

![UnitTestCore](./media/image5-10.png)

**Obrázek 5 – 10.** Testování jednotek základní aplikaci v izolaci.

![IntegrationTests](./media/image5-11.png)

**Obrázek 5 – 11.** Integrační testování implementace infrastruktury s externími závislostmi.

Protože vrstvě uživatelského rozhraní nemá žádné přímé závislosti na typy definované v projektu infrastruktury, je rovněž velmi snadno zaměnit implementace, buď usnadňuje testování nebo v reakci na měnící se požadavky na aplikace. Integrované použití ASP.NET Core a podpora pro vkládání závislostí díky této architektuře nejvhodnější způsob, jak struktura netriviální monolitické aplikace.

U monolitické aplikace jsou všechny projekty jádro aplikace, infrastruktury a uživatelského rozhraní spustit jako jednu aplikaci. Architektura modulu runtime aplikace bude vypadat přibližně jako obrázek 5 – 12.

![Architektura ASP.NET Core 2](./media/image5-12.png)

**Obrázek 5 – 12.** Architektura modulu runtime aplikace ASP.NET Core vzorku.

### <a name="organizing-code-in-clean-architecture"></a>Uspořádání v architektuře čistého kódu

V architektuře čistého řešení každý projekt má vymazat odpovědnosti. V důsledku toho některé typy patří do jednotlivých projektů a často zjistíte složky odpovídající typy v příslušného projektu.

Jádro aplikace obsahuje obchodní model, který obsahuje entity, služby a rozhraní. Tato rozhraní zahrnují abstrakce pro operace, které budou provedeny pomocí infrastruktury, jako je přístup k datům, přístupu k systému souborů, volání sítě atd. Někdy služby nebo rozhraní definované v této vrstvě bude nutné spolupracovat s nonentity typy, které nemají žádné závislosti na uživatelské rozhraní nebo infrastruktury. Ty lze definovat jako jednoduché objekty Data Transfer (DTO).

### <a name="application-core-types"></a>Základní typy aplikací

- Entity (obchodní model tříd, které jsou trvalé)
- Rozhraní
- Služby
- DTO

Projekt infrastruktury obvykle zahrnuje implementace dat přístup. V typické webové aplikace ASP.NET Core, patří tyto implementace Entity Framework (EF) uvolněn objekt DbContext, všechny EF Core `Migration` objekty, které byly definovány a přístupu k datům třídy implementace. Nejběžnější způsob abstraktní kód implementace přístupu k datům je prostřednictvím [vzor návrhu úložiště](https://deviq.com/repository-pattern/).

Kromě dat přístup implementace infrastruktury projektu by měl obsahovat implementace služby, které musí spolupracovat s starostí o infrastrukturu. Tyto služby by měly implementovat rozhraní definované v samotném aplikace a proto infrastruktury by měly mít odkaz na projekt aplikace Core.

### <a name="infrastructure-types"></a>Typy infrastruktury

- EF Core typy (`DbContext`, `Migration`)
- Datové typy implementace (úložiště)
- Specifické pro infrastrukturu služby (například `FileLogger` nebo `SmtpNotifier`)

Vrstva uživatelské rozhraní v aplikaci ASP.NET Core MVC je vstupním bodem pro aplikaci. Tento projekt by měl odkazovat na projekt, jádro aplikace a jeho typy by měly interakci s infrastrukturu výhradně prostřednictvím rozhraní definované v jádro aplikace. Žádné přímé vytvoření instance nebo statické volání typy vrstev infrastruktury by měl povolené ve vrstvě uživatelského rozhraní.

### <a name="ui-layer-types"></a>Typy vrstvy uživatelského rozhraní

- Kontrolery
- Filtry
- Zobrazení
- Modely ViewModels
- Třída pro spuštění

Třída při spuštění je zodpovědný pro konfiguraci aplikace a pro její implementaci typů rozhraní, což injektáž závislostí do za běhu správně fungovat.

> [!NOTE]
> Aby bylo možné nastavit injektáž závislostí v ConfigureServices v souboru Startup.cs projekt uživatelského rozhraní, možná muset projektu odkazovat na projekt infrastruktury. Tato závislost jde je eliminovat nejsnadněji použít vlastní kontejner DI. Pro účely tohoto příkladu je nejjednodušším přístupem umožnit projekt uživatelského rozhraní tak, aby se odkazovat na projekt infrastruktury.

## <a name="monolithic-applications-and-containers"></a>Monolitické aplikace a kontejnery

Můžete vytvořit jeden a monolitické nasazení na základě webové aplikace nebo služby a nasadit ho jako kontejner. V rámci aplikace nemusí být monolitické ale uspořádaných do několika knihoven, komponenty nebo vrstvy. Externě je jedním kontejnerem jako jeden proces, jednu webovou aplikaci nebo jedinou službou.

Správa tohoto modelu, nasadíte jedním kontejnerem pro reprezentaci aplikace. Pokud chcete škálovat, stačí přidáte další kopie se nástroj pro vyrovnávání zatížení v popředí. Jednoduchost pochází z jednoho nasazení ve virtuální počítač s jedním kontejnerem nebo Správa.

![](./media/image5-13.png)

Jak je znázorněno v obrázek 5-13 může obsahovat více komponent a knihovny nebo interní vrstvy v rámci každého kontejneru. Ale po Princip kontejneru _"kontejner provede jednu věc a dělá v jednom procesu_", monolitické vzorek může dojít ke konfliktu.

Nevýhodou tento přístup se dodává pokud/když aplikace poroste, požadují škálování. Pokud bude celá aplikace se škáluje, není ve skutečnosti k problému. Ve většině případů však několik částí aplikace jsou body potlačení nutnosti škálování, zatímco ostatní součásti jsou používá menší.

Použijeme příklad typické elektronického obchodování, co budete pravděpodobně muset škálovat je součást informace o produktu. Mnoho zákazníků další procházet produktů, než je koupit. Větší počet zákazníků pomocí nákupního košíku, než použití kanálu platby. Méně zákazníky přidat komentáře nebo zobrazení jejich historie nákupů. A pravděpodobně máte pouze několik zaměstnanců, v jedné oblasti, které potřebují spravovat obsah a marketingových kampaní. Díky škálování monolitický návrh, všechny se kód nasazuje více než jednou.

Kromě problém "škálovat vše" vyžadovat změny jedné komponenty kompletní opakované celé aplikace a dokončení opětovné nasazení všech instancí.

Monolitického přístupu je běžné a mnoha organizacích jsou vývoj s využitím tento architektonický přístup umožňuje vytvářet. Mnoho máte kvalitní dostatek výsledky, zatímco ostatní omezení výskytu. Mnoho navržené svých aplikací v tomto modelu, protože bylo příliš obtížné umožňuje vytvářet architektury orientované na služby (SOA) nástroje a infrastruktura a jejich nezobrazila potřeby, dokud zvětšoval aplikace. Pokud zjistíte, že narazíte na omezení monolitického přístupu, může být dalším logickým krokem po rozdělení aplikace, který umožňuje lepší využití kontejnerů a mikroslužeb.

![](./media/image5-14.png)

Nasazení monolitických aplikací v Microsoft Azure můžete dosáhnout pomocí vyhrazených virtuálních počítačů pro každou instanci. Pomocí [Škálovací sady virtuálních počítačů Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), je možné snadno škálovat virtuální počítače. [Služba Azure App Services](https://azure.microsoft.com/services/app-service/) můžete spustit monolitické aplikace a snadno škálovat instance, aniž byste museli spravovat virtuální počítače. Azure App Services můžete spustit jeden instancí kontejnerů Dockeru, zjednodušuje nasazení. Pomocí Dockeru, můžete nasadit jeden virtuální počítač jako hostitele Dockeru a spouštět více instancí. Pomocí nástroje pro vyrovnávání Azure, jak je znázorněno v obrázek 5-14, můžete spravovat škálování.

Nasazení do různých hostitelů lze spravovat pomocí nasazení tradiční techniky. Hostitele Docker můžete spravovat pomocí příkazů, jako jsou **dockeru spustit** provést ručně nebo pomocí automatizace, jako je průběžné doručování (CD) kanálů.

### <a name="monolithic-application-deployed-as-a-container"></a>Monolitické aplikace nasazená jako kontejner

Existují výhody použití kontejnerů ke správě nasazení monolitických aplikací. Škálování instance kontejnerů je mnohem jednodušší a rychlejší než nasazení dalších virtuálních počítačů. I když použijete virtuálního počítače škálovací sady škálování virtuálních počítačů, jejich trvat dobu na instanci. Po nasazení jako instance aplikace, je konfigurace aplikace spravovaná v rámci virtuálního počítače.

Nasazení aktualizací, je mnohem rychlejší imagí Dockeru a efektivní sítě. Image dockeru se obvykle začít během několika sekund, a tím i urychlení uvedení. Opětné do instance Docker je stejně jednoduché jako vydání `docker stop` příkaz obvykle dokončení v menší než druhý.

Kontejnery jsou ze své podstaty neměnné záměrné, je nikdy potřeba starat o poškozená virtuálních počítačů, zatímco zapomenout skripty pro aktualizaci. aby se zohlednily některé konkrétní konfiguraci nebo doleva souboru na disku.

_Kontejnery Dockeru můžete použít pro monolitické nasazení jednodušší webových aplikací. Tím se zlepšuje průběžnou integraci a průběžné nasazování kanálů a pomáhá dosahovat úspěšnosti nasazení do produkčního prostředí. Už to funguje"v počítači, proč to nebude fungovat v produkčním prostředí?"_

Architektura založená na mikroslužbách má spoustu výhod, ale tyto výhody pocházet za cenu zvýšení složitosti. V některých případech se náklady převažují nad přínosy, je lepší volbou monolitické nasazení aplikace s jedním kontejnerem nebo v několika kontejnerů.

Monolitické aplikace nemusí být snadno decomposable do jasně oddělené mikroslužeb. Mikroslužby by měla fungovat nezávisle na sobě zajistit odolnost aplikace. Pokud nelze doručit řezy nezávislé funkce aplikace, oddělení pouze zvyšuje složitost.

Aplikace nemusí potřebovat ještě nezávisle škálovat funkce. Mnoho aplikací, když potřebují škálovat na více než jednu instanci, můžete to udělat prostřednictvím poměrně jednoduchý proces klonování celý instance. Další práci pro oddělení aplikací do samostatných služeb poskytuje minimální výhodu při škálování úplná instance aplikace je jednoduché a nákladově efektivní.

Již v rané fázi při vývoji aplikace se nemusí mít jasno, kde jsou přirozené hranice funkční. Při vývoji minimální přijatelné produktu, nemusí mít ještě umístila fyzické oddělení. Některé z těchto podmínek může být dočasné. Může být začněte vytvořením jednotlivou aplikaci a později oddělení několik funkcí, které vyvinul a nasadit jako mikroslužeb. Další podmínky může být nezbytné pro aplikace problém místa, což znamená, že aplikace může být nikdy rozdělená do několika mikroslužeb.

Oddělení aplikace do mnoha samostatné procesy také zavádí režijní náklady. Rozdělení funkcí do různých procesů je složitější. Komunikační protokoly budou složitější. Namísto volání metody je nutné použít asynchronní komunikace mezi službami. Při přesunu na architekturu mikroslužeb, budete muset přidat řadu stavební bloky implementované v mikroslužbách verze aplikace aplikaci eShopOnContainers: zpracování událostí Service bus, zprávy odolnost proti chybám a opakovaných pokusů, konečnou konzistenci a další.

Mnohem jednodušší [eShopOnWeb referenční aplikace](https://github.com/dotnet-architecture/eShopOnWeb) podporuje použití monolitického kontejneru jeden kontejner. Aplikace obsahuje dvě webové aplikace: jednu pomocí tradiční MVC a další pomocí stránky Razor. Obojí se dají spustit pomocí kořenového řešení `docker-compose build` a `docker-compose up` příkazy. Tento příkaz nakonfiguruje samostatný kontejnery pro každé webové instance, pomocí `Dockerfile` najít v kořenovém adresáři každé webový projekt a spustí každý kontejner v samostatných portů. Můžete zdroj pro tuto aplikaci stáhnout z webu GitHub a spustit ho místně. Tato monolitické aplikace využívá výhod nasazení v prostředí kontejneru.

Za prvé nasazení kontejnerizované znamená, že každá instance aplikace běží ve stejném prostředí. Jedná se o prostředí pro vývojáře, kde vývoj a testování již v rané fázi probíhat. Vývojový tým můžete spustit aplikaci v kontejnerizovaných prostředí, která odpovídá produkčního prostředí.

Kromě toho kontejnerizovaných aplikací pro horizontální navýšení kapacity za nižší cenu. Použití prostředí kontejnerů umožňuje větší prostředků sdílení než tradiční prostředí virtuálních počítačů.

Nakonec se uzavření aplikace do kontejneru vynutí oddělení mezi obchodní logiku a storage server. Jak škálovat aplikaci se několik kontejnerů spoléhat na střední jednoho fyzického úložiště. Toto médium úložiště by obvykle vysokou dostupnost serveru databáze SQL serveru.

## <a name="docker-support"></a>Podpora dockeru

`eShopOnWeb` Projekt poběží v .NET Core. Proto můžete spustit v kontejnerech založených na Linuxu nebo založené na Windows. Všimněte si, že pro nasazení prostředí Docker, chcete použít stejný typ hostitele pro SQL Server. Kontejnery založené na Linuxu povolit menší nároky na místo a jsou upřednostňované.

Visual Studio 2017 můžete použít k přidání podpory Dockeru k existující aplikaci kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a zvolíte **přidat** > **podporu Dockeru** . To přidá potřebné soubory a změní projekt, k jejich použití. Aktuální `eShopOnWeb` ukázka již má tyto soubory na místě.

Úroveň řešení `docker-compose.yml` soubor obsahuje informace o co k sestavení Image a jaké kontejnery ke spuštění. Soubor umožňuje používat `docker-compose` příkaz spustit obě verze webové aplikace ve stejnou dobu. Také ho můžete použít ke konfiguraci závislostí, jako je například kontejner samostatné databáze.

```yml
version: '3'

services:
  eshopwebrazor:
    image: eshopwebrazor
    build:
      context: .
      dockerfile: src/WebRazorPages/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5107:5107"

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

`docker-compose.yml` Souboru odkazy `Dockerfile` v `Web` a `WebRazorPages` projekty. `Dockerfile` Slouží k určení, které základní kontejneru se použije a konfiguraci aplikace na ní. `WebRazorPages`" `Dockerfile`:

```
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.1.300-preview1 AS build
RUN npm install -g bower@1.8.4
WORKDIR /src
COPY . .
WORKDIR /src/src/WebRazorPages
RUN dotnet restore -nowarn:msb3202,nu1503
RUN dotnet build --no-restore -c Release -o /app

FROM build AS publish
RUN dotnet publish --no-restore -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Microsoft.eShopWeb.RazorPages.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Řešení potíží s Dockerem

Po spuštění kontejnerizované aplikace pokračuje v běhu až po ukončení. Můžete zobrazit, které kontejnery běží s `docker ps` příkazu. Spuštěný kontejner můžete zastavit pomocí `docker stop` příkazu a zadáte ID kontejneru.

Všimněte si, že spuštěné kontejnery Docker může být vázaný na porty, které může být jinak pokusu o použití ve vašem vývojovém prostředí. Pokud se pokusíte spustit nebo ladit aplikaci používající stejný port jako spuštěný kontejner Dockeru, získáte chybu s informacemi o tom, že server nejde vytvořit vazbu k tomuto portu. Zastavování kontejneru znovu, by měla vyřešit problém.

Pokud chcete přidat podporu Dockeru do vaší aplikace pomocí sady Visual Studio, ujistěte se, jestli že je spuštěný Docker, pokud tak učiníte. Průvodce nespustí správně, pokud Docker není spuštěn, když spustíte průvodce. Kromě toho Průvodce zkontroluje zvoleného aktuálního kontejneru pro přidání správné podpory Dockeru. Pokud chcete přidat podporu pro kontejnery Windows, musíte spustit průvodce, dokud máte Docker s kontejnery Windows nakonfigurovaný. Pokud chcete přidat podporu pro Linuxové kontejnery, spusťte Průvodce mají Dockeru s kontejnery Linuxu, které jsou nakonfigurované.

> ### <a name="references--common-web-architectures"></a>Odkazy – běžné architektury webových
>
> - **Vyčištění architektury**  
>   <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **Architektura průsvitek**  
>   <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **Model úložiště**  
>   <https://deviq.com/repository-pattern/>
> - **Vyčistit ukázkové architektury řešení**  
>   <https://github.com/ardalis/cleanarchitecture>
> - **Aplikační architektura založená na Mikroslužbách elektronickou knihu**  
>   <https://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
>[Předchozí](architectural-principles.md)
>[další](common-client-side-web-technologies.md)