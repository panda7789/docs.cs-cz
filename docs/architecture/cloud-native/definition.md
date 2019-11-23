---
title: Definování aplikací nativních pro cloud
description: Přečtěte si o základních pilířích, které poskytují Bedrock pro nativní cloudové systémy.
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 27191a67b2964ac2e1636a4d7dc55d5314b78439
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087536"
---
# <a name="defining-cloud-native"></a>Definování nativního cloudu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zastavte si, co děláte, a text 10 vašich kolegů. Požádejte je, aby definovali pojem Cloud Native. Dobrá pravděpodobnost, že získáte osm různých odpovědí. V současné době šest měsíců od teď až po vývoj technologií a postupů nativních pro Cloud, takže se jejich definice změní.

Cloud Native je vše o změně způsobu, jakým se myslíme na vytváření důležitých podnikových systémů.

Systémy nativní pro Cloud jsou navržené tak, aby zajišťují rychlou změnu, velký rozsah a odolnost.

Cloud Native Computing Foundation poskytuje [oficiální definici](https://github.com/cncf/foundation/blob/master/charter.md):

> *Cloudové nativní technologie umožňují organizacím vytvářet a spouštět škálovatelné aplikace v moderních, dynamických prostředích, jako jsou veřejné, privátní a hybridní cloudy. Tento přístup exemplify kontejnery, sítě, služby, mikroslužby, neměnné infrastruktury a deklarativní rozhraní API.*

> *Tyto techniky umožňují volně spojené systémy, které jsou odolné, spravovatelné a pozorovatelné. V kombinaci s robustní automatizací umožňují inženýrům provádět často a prediktivní změny s minimálním toil.*

Aplikace jsou stále složitější s tím, že uživatelé přibývají více a více. Uživatelé očekávají rychlou odezvu, inovativní funkce a nulové výpadky. Problémy s výkonem, opakujícími se chybami a neschopností rychlé přesuny již nejsou přijatelné. Budou snadno přesunuty na konkurenci.

Nativní Cloud je mnohem o *rychlosti* a *flexibilitě*. Firemní systémy se vyvíjející od umožnění obchodních schopností prostřednictvím zbraní při strategické transformaci a urychlení obchodních rychlostí a růstu. Je naprosto nezbytné získat návrhy na uvedení na trh hned.

Zde jsou některé společnosti, které implementovaly tyto techniky. Vezměte v úvahu rychlost, flexibilitu a škálovatelnost, které dosáhly.

| Společnosti | Využij |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Má 600 + služby v produkčním prostředí. Nasadí stovky časů za den. |
| [Uber](https://eng.uber.com/micro-deploy/) | Má 1000 000 služeb uložených v produkčním prostředí. Každý týden nasadí několik tisíc sestavení. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Má 300 + služby v produkčním prostředí. Provede téměř 1 000 změn za den. |

Jak vidíte, Netflix, Uber a WeChat zpřístupňují systémy, které se skládají ze stovek nezávislých mikroslužeb. Tento styl architektury umožňuje rychle reagovat na podmínky na trhu. Můžou okamžitě aktualizovat malé oblasti živé, složité aplikace a individuálně škálovat tyto oblasti podle potřeby.

Rychlost a flexibilita cloudového nativního řešení pocházejí z řady faktorů. Nejpřednější je cloudová infrastruktura. Pět dalších základních sloupků, které jsou znázorněné na obrázku 1-3, také poskytuje Bedrock pro nativní cloudové systémy.

![Základní pilíře pro Cloud – nativní](./media/cloud-native-foundational-pillars.png)

**Obrázek 1-3**. Základní pilíře pro Cloud – nativní

Pojďme chvíli trvat, abychom lépe pochopili význam každého pilíře.

## <a name="the-cloud"></a>Cloud...

Cloudové nativní systémy plně využívají model cloudové služby.

Tyto systémy, které jsou navržené tak, aby i v dynamickém virtualizovaném cloudovém prostředí, využívají výpočetní infrastrukturu [Platform as a Service (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) a spravované služby. *Považují základní infrastrukturu za dobu* v řádu minut a změnila velikost, zmenšování, přesunutí nebo zničení na vyžádání – prostřednictvím automatizace.

Vezměte v úvahu široce přijatý koncept DevOps [domácího a skotu](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). V tradičním datovém centru se servery považují za *domácí*: fyzický počítač, s ohledem na smysluplný název a staráte pro. Škálujte přidáním dalších prostředků do stejného počítače (škálování nahoru). Pokud se server bude nemocenný, nebudete ho moct vrátit do stavu. Má-li server být nedostupný, každý vyhlášení.

Model služby pro *skot* se liší. Každou instanci zřizujete jako virtuální počítač nebo kontejner. Jsou identické a mají přiřazený systémový identifikátor, třeba Service-01, Service-02 a tak dále. Můžete škálovat tak, že vytvoříte více z nich (horizontální škálování). Když některý z nich nebude k dispozici, nikdo z vás nevšiml.

Model skotu zahrnuje *neproměnlivou infrastrukturu*. Servery nejsou opraveny ani upravovány. Pokud se jeden nepovede nebo vyžaduje aktualizaci, je zničený a nové zřízení se zřídí – vše se provádí prostřednictvím automatizace.

Systémy nativní pro Cloud mají model služby pro skot. I nadále pracují s tím, jak se infrastruktura dokončí, a to bez ohledu na počítače, na kterých běží.

Cloudová platforma Azure podporuje tento typ vysoce elastické infrastruktury s automatickým škálováním, automatickým opravou a možnostmi monitorování.

## <a name="modern-design"></a>Moderní návrh

Jak by bylo možné navrhnout nativní cloudovou aplikaci? Jak vaše architektura vypadá? Jaké zásady, vzory a osvědčené postupy byste měli dodržovat? Jaká infrastruktura a provozní aspekty by byly důležité?

### <a name="the-twelve-factor-application"></a>Aplikace v dvanácti faktorech

Široce uznávaná metodologie pro vytváření cloudových aplikací je aplikace v [dvanácti faktorech](https://12factor.net/). Popisuje sadu zásad a postupů, které vývojáři postupují při vytváření aplikací optimalizovaných pro moderní cloudová prostředí. Zvláštní pozornost se věnuje přenositelnosti napříč prostředími a deklarativní automatizaci.

I když se to týká jakékoli webové aplikace, mnoho specialistů je považuje za Solid Foundation pro vytváření cloudových nativních aplikací. Systémy postavené na těchto principech se dají rychle nasadit a škálovat a přidat funkce, které rychle reagují na změny v trhu.

V následující tabulce je zdůrazněna dvanáct-Factor metodologie:

|    |  faktor | Vysvětlení  |
| :-------- | :-------- | :-------- |
| 1 | Základ kódu | Jediný základ kódu pro každou mikroslužbu uložený ve vlastním úložišti. Sledováno pomocí správy verzí, může být nasazeno do více prostředí (QA, fázování, produkce). |
| 2 | Závislosti | Každá mikroslužba izoluje a zabalí vlastní závislosti, přechodu změny bez dopadu na celý systém. |
| 3 | Konfigurace  | Informace o konfiguraci se přesunou z mikroslužby a externě prostřednictvím nástroje pro správu konfigurace mimo kód. Stejné nasazení se může šířit v různých prostředích se správnou nainstalovanou konfigurací.  |
| 4 | Záložní služby | Pomocné prostředky (úložiště dat, mezipaměti, zprostředkovatelé zpráv) by měly být vystavené prostřednictvím adres URL. Tím se oddělí prostředek od aplikace a tím se umožní jejich zaměnitelné.  |
| 5 | Sestavení, vydání, spuštění | Každá verze musí vyhovět striktnímu oddělení napříč fázemi sestavení, vydaných verzí a spuštění. Každý by měl být označený jedinečným ID a podporovat možnost vracet se zpátky. Moderní systémy CI/CD můžou splnit tento princip. |
| 6 | Procesy | Každá mikroslužba by se měla spustit ve vlastním procesu izolovaném od ostatních spuštěných služeb. Externalize požadovaný stav na zálohovací službu, jako je například distribuovaná mezipaměť nebo úložiště dat. |
| 7 | Vazba portu | Každá mikroslužba by měla být sama o sobě obsažená s rozhraními a funkcemi zveřejněnými na vlastním portu. V takovém případě poskytuje izolaci od ostatních mikroslužeb. |
| 8 | Souběžnost | Služby se škálují napříč velkým počtem malých identických procesů (kopií) na rozdíl od škálování jedné velké instance na nejvýkonnějším počítači, který je k dispozici. |
| 9 | Disposability | Instance služby by měly být jednorázově, dávají přednost rychlému spuštění, aby se zvýšily možnosti škálovatelnosti a aby bylo možné bezproblémové vypnutí systému zůstat ve správném stavu. Kontejnery Docker společně s nástrojem Orchestrator splňují tento požadavek. |
| 10 | Parita pro vývoj/prod | Snažte se v životním cyklu aplikace považovat za co možná podobná, a vyhnout se nákladným zkratkám. V tomto případě může přijetí kontejnerů významně přispět tím, že povýší stejné spouštěcí prostředí. |
| 11 | protokolování | Protokoly generované mikroslužbami se považují za streamy událostí. Zpracujte je pomocí Agregátoru událostí a rozšiřujte data na nástroje pro správu dolování dat a protokolů, jako je Azure Monitor nebo Splunk, a nakonec dlouhodobou archivaci. |
| 12 | Procesy správy | Spouštět úlohy správy a správy jako jednorázové procesy. Úkoly můžou zahrnovat data pro vyčištění a navýšení analýzy pro sestavu. Nástroje spouštějící tyto úlohy by se měly vyvolávat z produkčního prostředí, ale odděleně od aplikace. |

V knize, [mimo dvanáct-Factor App](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), si autor Kevin Hoffman podrobnosti o všech původních 12 faktorech (napsaných v 2011). Navíc kniha nabízí tři další faktory, které odráží dnešní moderní návrh cloudové aplikace.

|    |  Nový faktor | Vysvětlení  |
| :-------- | :-------- | :-------- |
| 13 | Nejdřív rozhraní API | Udělejte všechno jako služba. Předpokládejme, že váš kód bude využit klientem front-end, bránou nebo jinou službou. |
| 14 | Telemetrie | Na pracovní stanici máte hlubokou viditelnost své aplikace a jejího chování. V cloudu to neuděláte. Ujistěte se, že váš návrh zahrnuje shromažďování dat monitorování, specifických pro doménu a stavu a systému. |
| 15 | Ověřování/autorizace  | Implementujte identitu od začátku. Vezměte v úvahu funkce [RBAC (řízení přístupu na základě role)](https://docs.microsoft.com/azure/role-based-access-control/overview) , které jsou dostupné ve veřejných cloudech.  |

V této kapitole a v celé knize budeme odkazovat na spoustu 12 dalších faktorů.

### <a name="critical-design-considerations"></a>Důležité faktory návrhu

Kromě pokynů uvedených v rámci 12 rad metodologie existuje několik důležitých rozhodnutí o návrhu, která je nutné provést při vytváření distribuovaných systémů.

*Telecommunication*

Jak budou klientské aplikace front-endu komunikovat s back-end základními službami? Povolíte přímou komunikaci? Nebo je možné, že máte k dispozici služby back-endu s fasádou brány, která poskytuje flexibilitu, kontrolu a zabezpečení?

Jak budou služby back-endu mezi sebou navzájem komunikovat? Povolíte Přímá volání HTTP, která vedou ke spojení a ovlivňují výkon a flexibilitu? Nebo můžete zvážit oddělené zasílání zpráv s technologiemi front a témat?

Komunikace je popsána v podrobnostech kapitoly 4, *vzory komunikace nativní pro Cloud*.

*Odolnost*

Architektura mikroslužeb přesouvá váš systém z procesu do síťové komunikace. V distribuovaném prostředí, co uděláte, když služba B nereaguje na volání ze služby A? Co se stane, když dojde k dočasnému nedostupnosti služby C a dalším službám, které vyvolají zásobník IT a snižují výkon systému?

Odolnost proti chybám je popsaná v podrobnostech v kapitole 6, *odolnosti proti nativnímu cloudu*.

*Distribuovaná data*

Podle návrhu každá mikroslužba zapouzdřuje svá vlastní data a zveřejňuje operace přes své veřejné rozhraní. Pokud ano, jak se dotazovat na data nebo implementovat transakci napříč více službami?

Distribuovaná data jsou popsána v části Podrobnosti o *vzorcích nativních dat v cloudu*5.

*Identita*

Jak vaše služba identifikuje, kdo k němu přistupuje a jaká oprávnění mají?

Identita je uvedena v podrobnostech kapitoly 8, *identity*.

## <a name="microservices"></a>Mikroslužby

Nativní systémy pro Cloud mají mikroslužby, což je oblíbený styl architektury pro vytváření moderních aplikací.

Mikroslužby vytvořené jako distribuovaná sada malých nezávislých služeb, které komunikují prostřednictvím sdílených prostředků infrastruktury, sdílí následující vlastnosti:

- Každá z nich implementuje určitou obchodní funkci v rámci většího kontextu domény.

- Každý se vyvíjí samostatně a dá se nasadit nezávisle.

- Každý z nich obsahuje zapouzdřenou svou vlastní technologii úložiště dat (SQL, NoSQL) a programovací platformu.

- Každá spouští ve vlastním procesu a komunikuje s ostatními pomocí standardních komunikačních protokolů, jako jsou HTTP/HTTPS, WebSockets nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Vytvářejí dohromady, aby bylo možné vytvořit aplikaci.

Obrázek 1-4 kontrastuje přístup k aplikaci monolitické s přístupem k mikroslužbám. Všimněte si, jak se monolitu skládá z vrstvené architektury, která se spouští v jednom procesu. Obvykle spotřebovává relační databázi. Přístup k mikroslužbám ale odděluje funkce na nezávislé služby, které obsahují logiku a data. Každá mikroslužba hostuje své vlastní úložiště dat.

![Monolitické nasazení versus mikroslužby](./media/monolithic-vs-microservices.png)

**Obrázek 1-4.** Monolitické nasazení versus mikroslužby

Všimněte si, jak mikroslužby povýší "jeden základ kódu, jedna aplikace" z [aplikace na základě dvanácti faktorů](https://12factor.net/)popsaných výše v části.

> *Faktor \#1 určuje "jeden základ kódu pro každou mikroslužbu uložený ve vlastním úložišti. Sledováno pomocí správy verzí, může být nasazeno do více prostředí. "*

### <a name="why-microservices"></a>Proč mikroslužby?

Mikroslužby poskytují flexibilitu.

Dříve v této kapitole jsme porovnali elektronického obchodování aplikaci sestavenou jako monolitu s mikroslužbami. V tomto příkladu jsme viděli nějaké výhody, které jsou jasné:

- Každá mikroslužba má autonomní životní cyklus a může se vyvíjet nezávisle a často se nasazovat. Nemusíte čekat na čtvrtletní vydání, aby se nasadily nové funkce nebo aktualizace. Malou oblast komplexní aplikace můžete aktualizovat s menším rizikem, které by narušilo celý systém.

- Jednotlivé mikroslužby se můžou škálovat nezávisle. Místo škálování celé aplikace jako jedné jednotky můžete škálovat pouze ty služby, které vyžadují větší kapacitu napájení nebo šířku pásma sítě. Tento jemně odstupňovaný přístup k škálování poskytuje lepší kontrolu nad vaším systémem a pomáhá snižovat celkové náklady při škálování částí systému, ne všeho.

Vynikající referenční příručka pro porozumění mikroslužbám je [mikroslužby .NET: architektura pro kontejnerové aplikace .NET](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Kniha hluboko komentáře na návrh a architekturu mikroslužeb. Je to Pomocník pro [kompletní referenční architekturu mikroslužeb](https://github.com/dotnet-architecture/eShopOnContainers) , který je k dispozici zdarma ke stažení od Microsoftu.

### <a name="developing-microservices"></a>Vývoj mikroslužeb

Mikroslužby se dají vytvořit s libovolnou moderní vývojovou platformou.

Platforma Microsoft .NET Core je vynikající volbou. Bezplatný a Open Source má mnoho vestavěných funkcí, které zjednodušují vývoj mikroslužeb. .NET Core je platforma pro různé platformy. Aplikace se dají vytvářet a spouštět na Windows, macOS a nejvíc charakterech systému Linux.

.NET Core je vysoce výkonné a má ve srovnání s Node. js a dalšími konkurenčními platformami velmi kvalitní skóre. [TechEmpower](https://www.techempower.com/) vede ke spárování rozsáhlé sady [srovnávacích testů výkonu](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) v mnoha platformách a architekturách webových aplikací. .NET Core skóre v horních 10 – dobře nad Node. js a dalšími konkurenčními platformami.

.NET Core spravuje Microsoft a komunita .NET na GitHubu.

## <a name="containers"></a>Kontejnery

Současné době, je přirozené, že uslyšíte pojem *kontejner* uvedený v jakékoli konverzaci týkající se *cloudového nativního*řešení. V této knize se v [cloudových nativních vzorcích](https://www.manning.com/books/cloud-native-patterns)vytvoří Cornelia Davis s tím, že "kontejnery představují skvělý aktivátor cloudového nativního softwaru." Cloudová služba Native Computing Foundation umisťuje kontejner mikroslužeb jako první krok v rámci svých [cloudových nativních map](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) – doprovodné materiály pro podniky, které začínají svoji nativní cloudovou cestu.

Uzavření mikroslužby je jednoduchá a jednoduchá. Kód, jeho závislosti a modul runtime jsou zabaleny do binárního souboru s názvem [Image kontejneru](https://docs.docker.com/glossary/?term=image). Image jsou uložené v [registru kontejneru](https://caylent.com/container-registries/), který funguje jako úložiště nebo knihovna pro image. Registr se může nacházet ve vývojovém počítači, ve vašem datovém centru nebo ve veřejném cloudu. Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/). Cloud Azure nabízí [registr kontejnerů](https://azure.microsoft.com/services/container-registry/) pro ukládání imagí kontejneru blízko do cloudových aplikací, které je budou spouštět.

V případě potřeby Transformujte obrázek na spuštěnou instanci kontejneru. Instance se spouští na jakémkoli počítači, který má nainstalovaný modul pro modul [runtime kontejneru](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) . V případě potřeby můžete mít tolik instancí služby kontejneru.

Obrázek 1-5 ukazuje tři různé mikroslužby, každé ve vlastním kontejneru spuštěném na jednom hostiteli.

![Více kontejnerů spuštěných v hostiteli kontejneru](./media/hosting-mulitple-containers.png)

**Obrázek 1-5**. Více kontejnerů spuštěných v hostiteli kontejneru

Všimněte si, jak každý kontejner udržuje svou vlastní sadu závislostí a modulu runtime, který se může lišit. Tady vidíte různé verze mikroslužby produktu běžící na stejném hostiteli. Každý kontejner sdílí řez základního hostitelského operačního systému, paměti a procesoru, ale je od sebe izolovaný.

Všimněte si, jak dobře model kontejneru zahrnuje Princip závislostí z [aplikace v dvanácti faktorech](https://12factor.net/).

> *Faktor \#2 určuje, že "každá mikroslužba izoluje a zabalí vlastní závislosti, přechodu změny bez dopadu na celý systém."*

Kontejnery podporují úlohy se systémy Linux a Windows. Cloud Azure se otevře v obou případech. V tomto případě se jedná o Linux, ne Windows Server, které se staly nejoblíbenějším operačním systémem v Azure.

I když existuje několik dodavatelů kontejnerů, Docker zachytil podíl na trhu Lion. Společnost řídí pohyb kontejneru softwaru. Pro balení, nasazování a spouštění cloudových nativních aplikací se stala fakta de facto standard.

### <a name="why-containers"></a>Proč kontejnery?

Kontejnery poskytují přenositelnost a zaručují konzistenci napříč prostředími. Zapouzdřením všeho do jednoho balíčku *izolujete* mikroslužbu a její závislosti z základní infrastruktury.

Stejný kontejner můžete nasadit v jakémkoli prostředí, které má modul runtime Docker. Kontejnerové úlohy také odstraňují náklady před konfigurací jednotlivých prostředí s architekturou, softwarovými knihovnami a běhovými moduly.

Díky sdílení základního operačního systému a prostředků hostitele mají kontejnery mnohem menší nároky než plný virtuální počítač. Menší velikost zvyšuje *hustotu*nebo počet mikroslužeb, které může daný hostitel spustit najednou.

### <a name="container-orchestration"></a>Orchestrace kontejnerů

I když nástroje, jako je Docker, vytvářejí image a spouštějí kontejnery, potřebujete nástroje pro jejich správu. Správa kontejnerů se provádí pomocí speciálního softwarového programu nazvaného produkt Orchestrator pro kontejner. Při současném škálování je orchestrace kontejnerů zásadní.

Obrázek 1-6 ukazuje úlohy správy, které poskytují orchestrace kontejnerů.

![Co dělají orchestrace kontejnerů](./media/what-container-orchestrators-do.png)

**Obrázek 1-6**. Co dělají orchestrace kontejnerů

V následující tabulce jsou popsány běžné úlohy orchestrace.

|  Tasks | Vysvětlení  |
| :-------- | :-------- |
| Plánuje | Automaticky zřídí instance kontejnerů.|
| Spřažení/proti spřažení | Zřizování kontejnerů blízko sebe nebo daleko od sebe navzájem, což pomáhá zajistit dostupnost a výkon. |
| Monitorování stavu | Automatické zjišťování a opravy chyb.|
| Při selhání | Automaticky znovu zřídit neúspěšnou instanci pro počítače v pořádku.|
| Škálování | Automaticky přidat nebo odebrat instanci kontejneru, aby splňovala požadavky.|
| Sítě | Spravujte překrytí sítě pro komunikaci s kontejnerem.|
| Zjišťování služby | Umožněte, aby kontejnery navzájem vyhledaly.|
| Postupné upgrady | Koordinuje přírůstkové upgrady při nasazení s nulovými výpadky. Automaticky vrátí problematické změny.|

Všimněte si, jak orchestrace vychází ze zásad disposability a souběžnosti z [aplikace z dvanácti faktorů](https://12factor.net/)popsaných výše v části.

> *Faktor \#9 určuje, že "instance služby by měly být jednorázově, dávají přednost rychlému spuštění, aby se zvýšily možnosti škálovatelnosti, a bezproblémové vypnutí, aby systém zůstal ve správném stavu. Kontejnery Docker společně s nástrojem Orchestrator splňují tento požadavek. "*

> *Faktor \#8 určuje, že "služby se škálují napříč velkým počtem malých identických procesů (kopií) na rozdíl od vertikálního škálování jedné velké instance na nejvýkonnějším počítači, který je k dispozici."*

I když existuje několik orchestrací kontejnerů, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) se stal de facto standardem pro cloudově Native World. Je to přenosná, rozšiřitelná a open source platforma pro správu kontejnerových úloh.

Mohli byste hostovat svou vlastní instanci Kubernetes, ale pak byste měli být odpovědni za zřizování a správu svých prostředků – což může být složité. Azure Cloud Features Kubernetes jako spravovaná služba [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). Spravovaná služba vám umožňuje plně využít své funkce, aniž byste je museli instalovat a udržovat.

Služba Azure Kubernetes Services je podrobně popsána v kapitole 2, *škálování cloudových nativních aplikací*.

## <a name="backing-services"></a>Záložní služby

Nativní systémy cloudu závisí na mnoha různých pomocných zdrojích, jako jsou úložiště dat, zprostředkovatelé zpráv, monitorování a služby identit. Tyto služby se označují jako [záložní služby](https://12factor.net/backing-services).

 Obrázek 1-7 ukazuje mnoho běžných zálohovacích služeb, které využívají cloudové nativní systémy.

![Běžné služby zálohování](./media/common-backing-services.png)

**Obrázek 1-7**. Běžné služby zálohování

Služba back-Factor Services povýší zásadu "Statelessness" z [aplikace na dvanácti](https://12factor.net/), která je popsána výše v kapitole.

>*Faktor \#6* určuje, že "každá mikroslužba by se měla spustit ve vlastním procesu, izolovaná od ostatních spuštěných služeb. Externalize požadovaný stav na zálohovací službu, jako je například distribuovaná mezipaměť nebo úložiště dat. "

Mohli byste hostovat své vlastní služby zálohování, ale pak budete odpovědni za licencování, zřizování a správu těchto prostředků.

Poskytovatelé cloudu nabízejí bohatou řadu *spravovaných služeb zálohování.* Místo vlastnícího službu ji stačí využít. Poskytovatel pracuje se škálováním prostředku a nese zodpovědnost za výkon, zabezpečení a údržbu. Sledování, redundance a dostupnost jsou součástí služby. Poskytovatelé plně podporují své spravované služby – otevřete lístek a vyřešte svůj problém.

Cloudové nativní systémy mají na starosti spravované záložní služby od dodavatelů cloudu. Úspory v čase a práci jsou skvělé. Provozní riziko hostování vlastního problému a problémy, které se vyskytly, může rychle získat náklady.

Osvědčeným postupem je považovat záložní službu za *připojeného prostředku*, která je dynamicky vázaná na mikroslužby s informacemi (adresa URL a přihlašovací údaje) uložené v externí konfiguraci. Tyto pokyny se napíší v aplikaci v [dvanácti faktorech](https://12factor.net/), které jsou popsány dříve v této kapitole.

>*Faktor \#4* určuje, že záložní služby by měly být zveřejněny prostřednictvím adresované adresy URL. Tím se oddělí prostředek od aplikace a umožní se jeho změna. "

>*Faktor \#3* určuje, že "informace o konfiguraci se z mikroslužeb přesunou a externě prostřednictvím nástroje pro správu konfigurace mimo kód."

V tomto modelu je možné připojit a odpojit zálohovací službu beze změny kódu. Mikroslužbu můžete povýšit z QA do přípravného prostředí. Aktualizujete konfiguraci mikroslužeb tak, aby odkazovala na služby, které jsou v pracovním prostředí, a do svého kontejneru se vloží nastavení pomocí proměnné prostředí.

Dodavatelé cloudu poskytují rozhraní API pro komunikaci se svými speciálními službami zálohování. Tyto knihovny zapouzdřují instalace a složitost. Komunikace přímo s těmito rozhraními API bude pevně přidružit váš kód k back-službě. Je to vhodnější pro izolaci podrobností implementace rozhraní API dodavatele. Představte si mezilehlou vrstvu nebo zprostředkující rozhraní API, které zveřejňují obecné operace s kódem služby. Toto volné spojení vám umožňuje vyměňovat jednu záložní službu pro jiný nebo přesunout kód do jiného veřejného cloudu, aniž by bylo nutné provádět změny v kódu služby hlavní.

Služby zálohování jsou popsané v podrobnostech v kapitolách 5, *nativních datových vzorcích pro Cloud*a v kapitole 4, *cloudové vzory komunikace*.

## <a name="automation"></a>Automation

Jak jste viděli, nativní systémy cloudu přiřadí mikroslužby, kontejnery a moderní návrh systému, aby dosáhly rychlosti a flexibility. Ale to je jenom část tohoto scénáře. Jak můžete zřídit cloudová prostředí, na kterých se tyto systémy spouštějí? Jak rychle nasazujete funkce a aktualizace aplikací? Jak vyplníte celý obrázek?

Zadejte široce přijatý postup [infrastruktury jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)nebo IAC.

Pomocí IaC automatizujete zřizování platforem a nasazení aplikací. V podstatě budete uplatňovat postupy softwarového inženýrství, jako je testování a správa verzí, a to v praxi DevOps. Vaše infrastruktura a nasazení jsou automatizované, konzistentní a opakované.

### <a name="automating-infrastructure"></a>Automatizace infrastruktury

Nástroje jako [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraformu a [Azure CLI](https://docs.microsoft.com/cli/azure/)umožňují deklarativní skriptování cloudové infrastruktury, kterou požadujete. Názvy prostředků, umístění, kapacity a tajné klíče jsou parametrizované a dynamické. Skript se zaznamená ve verzi a do správy zdrojového kódu se zaregistruje jako artefakt vašeho projektu. Vyvoláte skript, který zřídí jednotnou a možnou infrastrukturu v rámci systémových prostředí, jako je třeba QA, fázování a produkce.

V digestoři je IaC idempotentní, což znamená, že můžete spustit stejný skript i bez vedlejších účinků. Pokud tým potřebuje provést změnu, upraví a znovu spustí skript. Ovlivněny jsou pouze aktualizované prostředky.

V článku [co je infrastruktura jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), vytváření Sam Guckenheimer popisuje, jak "týmy, které implementují IAC, můžou doručovat stabilní prostředí rychle a ve velkém měřítku. Týmy zabraňují ruční konfiguraci prostředí a vynutily konzistenci tím, že představují požadovaný stav prostředí prostřednictvím kódu. Nasazení infrastruktury s IaC se opakují a zabraňují problémům za běhu způsobeným posunem konfigurace nebo chybějícími závislostmi. Týmy DevOps můžou spolupracovat s jednotným sadou postupů a nástrojů a rychle a spolehlivě doručovat aplikace a jejich podpůrnou infrastrukturu. "

### <a name="automating-deployments"></a>Automatizace nasazení

[32bitová aplikace](https://12factor.net/), která je popsána dříve, volá samostatné kroky při transformaci dokončeného kódu do běžící aplikace.

> *Faktor \#5* určuje, že každá verze musí vymáhat striktní oddělení napříč fázemi sestavení, vydaných verzí a spuštění. Každá by měla být označena jedinečným IDENTIFIKÁTORem a podporuje možnost vracet se zpět. "

Moderní systémy CI/CD můžou splnit tento princip. Poskytují samostatné kroky nasazení a umožňují zajistit konzistentní a kvalitní kód, který je uživatelům snadno dostupný.

Obrázek 1-8 ukazuje oddělení v rámci procesu nasazení.

![Kroky nasazení v kanálu CI/CD](./media/build-release-run-pipeline.png)

**Obrázek 1-8**. Postup nasazení v kanálu CI/CD

Na předchozím obrázku věnujte zvláštní pozornost oddělení úloh.

Vývojář sestaví funkci ve vývojovém prostředí a provede iteraci tím, co se nazývá vnitřní smyčka kódu, spuštění a ladění. Po dokončení bude tento kód *vložen* do úložiště kódu, jako je GitHub, Azure DevOps nebo Bitbucket.

Nabízená oznámení spustí fázi sestavení, která transformuje kód do binárního artefaktu. Práce je implementovaná pomocí kanálu [průběžné integrace (CI)](https://martinfowler.com/articles/continuousIntegration.html) . Automaticky vytvoří, otestuje a zabalí aplikaci.

Fáze vydaných verzí převezme binární artefakt, použije informace o konfiguraci externích aplikací a prostředí a vytvoří neměnné vydání. Verze je nasazená v zadaném prostředí. Práce je implementována s kanálem [průběžného doručování (CD)](https://martinfowler.com/bliki/ContinuousDelivery.html) . Každá verze by měla být identifikovatelná. Můžete vyslovit "Toto nasazení používá verzi 2.1.1 aplikace."

Nakonec se vydaná funkce spustí v cílovém prostředí pro spuštění. Verze jsou neměnné, což znamená, že každá změna musí vytvořit novou verzi.

Při použití těchto postupů se organizacím při dodávání softwaru odvíjejí základní informace. Mnohé se přesunuly z čtvrtletních vydání na aktualizace na vyžádání. Cílem je zachytit problémy v předstihu vývojového cyklu, pokud je jejich oprava méně náročná. Čím déle trvá integrace, tím dražší problémy se vyřeší.  Díky konzistenci v procesu integrace můžou týmy potvrzovat změny kódu častěji, což vede k lepší spolupráci a kvalitě softwaru.

### <a name="azure-pipelines"></a>Kanály Azure

Cloud Azure obsahuje novou službu CI/CD s oprávněním [Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/), která je součástí nabídky [Azure DevOps](https://azure.microsoft.com/services/devops/) , která je znázorněna na obrázku 1-9.

![Azure Pipelines v DevOps](./media/devops-components.png)

**Obrázek 1-9**. Nabídky Azure DevOps

Azure Pipelines je cloudová služba, která kombinuje průběžnou integraci (CI) a průběžné doručování (CD). Můžete automaticky testovat, sestavovat a dodávat kód do libovolného cíle.

Kanál můžete definovat v kódu v souboru YAML vedle zbytku kódu pro vaši aplikaci.

- Kanál se používá ve verzi kódu a řídí se stejnou strukturou větvení.
- Pomocí revizí kódu v rámci žádostí o přijetí změn a zásad sestavení větví získáte ověření změn.
- Každá větev, kterou použijete, může přizpůsobit zásadu sestavení úpravou souboru Azure-Pipelines. yml.
- Soubor kanálu je vrácen do správy verzí a lze jej prozkoumat, pokud dojde k potížím.

Služba Azure Pipelines podporuje většinu poskytovatelů Git a může generovat kanály nasazení pro aplikace napsané na platformách Linux, macOS a Windows. Zahrnuje podporu pro Java, .NET, JavaScript, Python, PHP, přejít, XCode a C++.

>[!div class="step-by-step"]
>[Předchozí](introduction.md)
>[Další](candidate-apps.md)
