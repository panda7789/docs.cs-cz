---
title: Definování aplikací nativních pro cloud
description: Seznamte se se základními pilíři, které poskytují základy pro cloudové systémy
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 27191a67b2964ac2e1636a4d7dc55d5314b78439
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401569"
---
# <a name="defining-cloud-native"></a>Definování nativního cloudu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Přestaňte s tím, co děláte, a napište 10 kolegů. Požádejte je, aby definovali termín "Cloud Native". Je velká šance, že dostanete osm různých odpovědí. Zajímavé je, že za šest měsíců, jak se budou vyvíjet technologie a postupy nativní pro cloud, se budou vyvíjet i jejich definice.

Cloud nativní je především o změně způsobu, jakým přemýšlíme o konstrukci kritických podnikových systémů.

Cloud-nativní systémy jsou navrženy tak, aby zahrnovaly rychlé změny, rozsáhlé a odolnost.

Cloud Native Computing Foundation poskytuje [oficiální definici:](https://github.com/cncf/foundation/blob/master/charter.md)

> *Nativní technologie cloudu umožňují organizacím vytvářet a spouštět škálovatelné aplikace v moderních, dynamických prostředích, jako jsou veřejné, soukromé a hybridní cloudy. Kontejnery, servisní umístění, mikroslužby, neměnná infrastruktura a deklarativní api ilustrují tento přístup.*

> *Tyto techniky umožňují volně vázané systémy, které jsou odolné, zvládnutelné a pozorovatelné. V kombinaci s robustní automatizací umožňují inženýrům provádět působivé změny často a předvídatelně s minimální dřinou.*

Aplikace jsou stále složitější s uživateli, kteří požadují více a více. Uživatelé očekávají rychlou odezvu, inovativní funkce a nulové prostoje. Problémy s výkonem, opakované chyby a neschopnost rychle se pohybovat již nejsou přijatelné. Snadno se přestěhují k vašemu konkurentovi.

Cloud nativní je hodně o *rychlosti* a *agility*. Obchodní systémy se vyvíjejí od umožnění obchodních schopností až po zbraně strategické transformace, zrychlují obchodní rychlost a růst. Je nezbytné, aby si nápady na trh okamžitě.

Zde jsou některé společnosti, které zavedly tyto techniky. Zamyslete se nad rychlostí, hbitostí a škálovatelností, které dosáhli.

| Společnost | Prostředí |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Má více než 600 služeb ve výrobě. Nasazuje stokrát denně. |
| [Uber](https://eng.uber.com/micro-deploy/) | Má více než 1000 služeb uložených ve výrobě. Nasadí několik tisíc sestavení každý týden. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Má více než 300 služeb ve výrobě. Dělá téměř 1000 změn za den. |

Jak můžete vidět, Netflix, Uber a WeChat vystavit systémy, které se skládají ze stovek nezávislých mikroslužeb. Tento architektonický styl jim umožňuje rychle reagovat na tržní podmínky. Mohou okamžitě aktualizovat malé oblasti živé, složité aplikace a jednotlivě škálovat tyto oblasti podle potřeby.

Rychlost a hbitost cloudnativní pocházejí z mnoha faktorů. Nejdůležitější je cloudová infrastruktura. Pět dalších základních pilířů uvedených na obrázku 1-3 také poskytuje základ pro systémy nativní pro cloud.

![Základní pilíře nativní pro cloud](./media/cloud-native-foundational-pillars.png)

**Obrázek 1-3**. Základní pilíře nativní pro cloud

Udělejme nějaký čas, abychom lépe pochopili význam každého pilíře.

## <a name="the-cloud"></a>Mrak...

Cloudové nativní systémy plně využívají model cloudových služeb.

Tyto systémy jsou navrženy tak, aby prosperovaly v dynamickém virtualizovaném cloudovém prostředí, a rozsáhle využívají výpočetní [infrastrukturu platformy jako služby (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) a spravované služby. Základní infrastrukturu považují za *jednorázovou* – zřízenou během několika minut a zmenšenou velikost, zmenšenou, přesunutou nebo zničenou na vyžádání – prostřednictvím automatizace.

Vezměme si široce přijímaný DevOps koncept [domácích zvířat vs skotu](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). V tradičním datovém centru jsou servery považovány za *domácí zvířata*: fyzický stroj, který má smysluplné jméno a je o ně postaráno. Škálování přidáním dalších prostředků do stejného počítače (škálování nahoru). Pokud server onemocní, ošetřujete ho zpět ke zdraví. Pokud server přestane být k dispozici, všichni si všimnou.

Model služby *Dobytek* je jiný. Zřídíte každou instanci jako virtuální počítač nebo kontejner. Jsou identické a je jim přiřazen identifikátor systému, například Service-01, Service-02 a tak dále. Můžete škálovat vytvořením více z nich (horizontální navýšení kapacity). Když se člověk stane nedostupným, nikdo si toho nevšimne.

Model dobytka zahrnuje *neměnnou infrastrukturu*. Servery nejsou opraveny ani změněny. Pokud jeden selže nebo vyžaduje aktualizaci, je zničen a je zřízena nová – to vše prostřednictvím automatizace.

Cloud-nativní systémy zahrnují model služby Cattle. Oni i nadále běží jako infrastruktura váhy dovnitř nebo ven bez ohledu na stroje, na kterých jsou spuštěny.

Cloudová platforma Azure podporuje tento typ vysoce elastické infrastruktury s automatickým škálováním, samoopravitelností a možnostmi monitorování.

## <a name="modern-design"></a>Moderní design

Jak byste navrhli aplikaci nativní pro cloud? Jak by vypadala vaše architektura? K jakým zásadám, vzorům a osvědčeným postupům byste se drželi? Jaké obavy týkající se infrastruktury a provozu by byly důležité?

### <a name="the-twelve-factor-application"></a>Dvanáctifaktorová aplikace

Široce přijímanou metodikou pro vytváření cloudových aplikací je [aplikace s dvanácti faktory](https://12factor.net/). Popisuje sadu zásad a postupů, které vývojáři postupují při vytváření aplikací optimalizovaných pro moderní cloudová prostředí. Zvláštní pozornost je věnována přenositelnosti napříč prostředími a deklarativní automatizaci.

Zatímco platí pro všechny webové aplikace, mnoho odborníků považují za pevný základ pro vytváření aplikací nativní pro cloud. Systémy postavené na těchto principech mohou rychle nasadit a škálovat a přidávat funkce, které rychle reagují na změny na trhu.

V následující tabulce je zdůrazněna metodika dvanácti faktorů:

|    |  Faktor | Vysvětlení  |
| :-------- | :-------- | :-------- |
| 1 | Základ kódu | Jeden základ kódu pro každou mikroslužbu, uložené ve vlastním úložišti. Sledováno pomocí správy verzí, může se nasadit do více prostředí (QA, Staging, Production). |
| 2 | Závislosti | Každá mikroslužba izoluje a balí své vlastní závislosti, zahrnující změny bez dopadu na celý systém. |
| 3 | Konfigurace  | Informace o konfiguraci se přesunou z mikroslužby a externalizovány prostřednictvím nástroje pro správu konfigurace mimo kód. Stejné nasazení se může šířit napříč prostředími se správnou použitou konfigurací.  |
| 4 | Podpůrné služby | Pomocné prostředky (úložiště dat, mezipaměti, zprostředkovatelé zpráv) by měly být vystaveny prostřednictvím adresovatelné adresy URL. Tím odpojí prostředek z aplikace, což umožňuje zaměnitelné.  |
| 5 | Sestavení, uvolnění, spuštění | Každá verze musí vynutit přísné oddělení mezi fázemi sestavení, vydání a spuštění. Každý by měl být označen jedinečným ID a měl by podporovat možnost vrátit se zpět. Moderní CI/CD systémy pomáhají naplnit tento princip. |
| 6 | Procesy | Každá mikroslužba by měla být spuštěna ve vlastním procesu, izolované od jiných spuštěných služeb. Externalizujte požadovaný stav na záložní službu, jako je například distribuovaná mezipaměť nebo úložiště dat. |
| 7 | Vazba portu | Každá mikroslužba by měla být samostatná s rozhraními a funkcemi vystavenými na vlastním portu. Tím poskytuje izolaci od jiných mikroslužeb. |
| 8 | Souběžnost | Služby škálovat přes velký počet malých identických procesů (kopie) na rozdíl od škálování na jednu velkou instanci na nejvýkonnější počítač k dispozici. |
| 9 | Disposability | Instance služby by měly být na jedno použití, což upřednostňuje rychlé spuštění pro zvýšení možností škálovatelnosti a řádné vypnutí opustit systém ve správném stavu. Kontejnery Dockeru spolu s orchestrator neodmyslitelně splňují tento požadavek. |
| 10 | Vývoj/prod parita | Udržujte prostředí v celém životním cyklu aplikace co nejvíce podobné, abyste se vyhnuli nákladným zkratkám. Zde přijetí kontejnerů může výrazně přispět podporou stejného prostředí provádění. |
| 11 | Protokolování | Považovat protokoly generované mikroslužeb jako datové proudy událostí. Zpracujte je pomocí agregátoru událostí a propagujte data do nástrojů pro správu dolování dat a protokolů, jako je Azure Monitor nebo Splunk a nakonec dlouhodobá archivace. |
| 12 | Procesy správce | Spouštět úlohy správy a správy jako jednorázové procesy. Úkoly mohou zahrnovat vyčištění dat a analýzy vytahování sestavy. Nástroje provádějící tyto úkoly by měly být vyvolány z produkčního prostředí, ale odděleně od aplikace. |

V knize [Beyond the Twelve-Factor App](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)autor Kevin Hoffman podrobně popisuje každý z původních 12 faktorů (napsaných v roce 2011). Kromě toho kniha obsahuje tři další faktory, které odrážejí dnešní moderní návrh cloudové aplikace.

|    |  Nový faktor | Vysvětlení  |
| :-------- | :-------- | :-------- |
| 13 | Rozhraní API jako první | Udělejte všechno službou. Předpokládejme, že váš kód bude spotřebován front-endovým klientem, bránou nebo jinou službou. |
| 14 | Telemetrická data | Na pracovní stanici máte hluboké viditelnosti do aplikace a její chování. V cloudu ne. Ujistěte se, že váš návrh obsahuje shromažďování monitorování, specifické pro doménu a data stavu/systému. |
| 15 | Ověřování/ autorizace  | Implementujte identitu od začátku. Zvažte [funkce RBAC (řízení přístupu na základě rolí),](https://docs.microsoft.com/azure/role-based-access-control/overview) které jsou k dispozici ve veřejných cloudách.  |

Budeme odkazovat na mnoho z 12 + faktory v této kapitole a v celé knize.

### <a name="critical-design-considerations"></a>Důležité důležité informace o návrhu

Kromě pokynů poskytnutých z metodiky dvanácti faktorů je třeba provést několik kritických rozhodnutí návrhu při konstrukci distribuovaných systémů.

*Communication*

Jak bude front-endové klientské aplikace komunikovat s backed-end základní služby? Povolíte přímou komunikaci? Nebo můžete abstrahujete back-endové služby s fasádou brány, která poskytuje flexibilitu, kontrolu a zabezpečení?

Jak budou back-endové základní služby vzájemně komunikovat? Povolíte přímé volání HTTP, které vedou ke spojení a dopad u výkonu a agility? Nebo byste mohli zvážit oddělené zasílání zpráv s technologiemi fronty a tématu?

Komunikace je podrobně popsána kapitola 4, *Cloud-Nativní komunikační vzory*.

*Odolnost*

Architektura mikroslužeb přesune váš systém z procesu na síťovou komunikaci. Co budete v distribuovaném prostředí dělat, když služba B nereaguje na volání ze služby A? Co se stane, když služba C se stane dočasně nedostupným a další služby, které ji volají, stohují a snižují výkon systému?

Odolnost proti chybám je podrobně popsána kapitola 6, *Odolnost nativní pro cloud*.

*Distribuovaná data*

Podle návrhu každá mikroslužba zapouzdřuje vlastní data a vystavuje operace prostřednictvím svého veřejného rozhraní. Pokud ano, jak dotazovat data nebo implementovat transakce napříč více služeb?

Distribuovaná data jsou podrobně popsána kapitola 5, *Cloud-Nativní datové vzory*.

*Identita*

Jak vaše služba určí, kdo k ní přistupuje a jaká oprávnění má?

Identita je podrobně popsána kapitola 8, *Identita*.

## <a name="microservices"></a>Mikroslužby

Cloudnativní systémy zahrnují mikroslužby, populární architektonický styl pro vytváření moderních aplikací.

Mikroslužby, které jsou vytvořeny jako distribuovaná sada malých nezávislých služeb, které interagují prostřednictvím sdílené struktury infrastruktury, sdílejí následující charakteristiky:

- Každý implementuje konkrétní obchodní funkce v rámci kontextu větší domény.

- Každý z nich je vyvíjen samostatně a může být nasazen nezávisle.

- Každý z nich je soběstačný zapouzdření vlastní technologie ukládání dat (SQL, NoSQL) a programovací platformy.

- Každý z nich běží ve svém vlastním procesu a komunikuje s ostatními pomocí standardních komunikačních protokolů, jako je HTTP/HTTPS, WebSockets nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Skládají společně tvořit aplikaci.

Obrázek 1-4 kontrastuje monolitické aplikace přístup s přístupem mikroslužeb. Všimněte si, jak se monolit skládá z vrstvené architektury, která se spustí v jednom procesu. Obvykle spotřebovává relační databáze. Přístup mikroslužeb však odděluje funkce do nezávislé služby, které zahrnují logiku a data. Každá mikroslužba hostuje vlastní úložiště dat.

![Monolitické nasazení versus mikroslužby](./media/monolithic-vs-microservices.png)

**Obrázek 1-4.** Monolitické nasazení versus mikroslužby

Všimněte si, jak mikroslužby podporovat "Jeden základ kódu, jedna aplikace" princip z [dvanáctifaktorové aplikace](https://12factor.net/), popsané dříve v kapitole.

> *Faktor \#1 určuje "Jeden základ kódu pro každou mikroslužbu, uložený ve vlastním úložišti. Sledovánpomocí správy verzí, může se nasadit do více prostředí."*

### <a name="why-microservices"></a>Proč mikroslužby?

Mikroslužby poskytují agilitu.

Dříve v kapitole jsme porovnali aplikaci eCommerce vytvořenou jako monolit s mikroslužbami. V příkladu jsme viděli některé jasné výhody:

- Každá mikroslužba má autonomní životní cyklus a může vyvíjet nezávisle a nasazovat často. Nemusíte čekat na čtvrtletní vydání k nasazení nových funkcí nebo aktualizace. Můžete aktualizovat malou oblast složité aplikace s menším rizikem narušení celého systému.

- Každá mikroslužba můžete škálovat nezávisle. Namísto škálování celé aplikace jako jedné jednotky můžete škálovat pouze ty služby, které vyžadují větší výpočetní výkon nebo šířku pásma sítě. Tento jemně odstupňovaný přístup k škálování poskytuje větší kontrolu nad vaším systémem a pomáhá snižovat celkové náklady při škálování částí systému, ne všeho.

Vynikající referenční příručka pro pochopení mikroslužeb je [.NET Microservices: Architektura pro kontejnerizované aplikace .NET](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Kniha se ponoří do návrhu mikroslužeb a architektury. Je to společník pro [full-stack mikroservice referenční architektury](https://github.com/dotnet-architecture/eShopOnContainers) k dispozici ke stažení zdarma od společnosti Microsoft.

### <a name="developing-microservices"></a>Vývoj mikroslužeb

Mikroslužeb lze vytvořit s libovolnou moderní vývojovou platformu.

Platforma Microsoft .NET Core je vynikající volbou. Svobodný a open source, má mnoho vestavěných funkcí pro zjednodušení vývoje mikroslužeb. .NET Core je multiplatformní. Aplikace lze sestavit a spustit ve Windows, macOS a většině variant Linuxu.

.NET Core je vysoce výkonný a má dobré skóre ve srovnání s Node.js a dalších konkurenčních platforem. Zajímavé je, [že TechEmpower](https://www.techempower.com/) provedl a rozsáhlý soubor [výkonnostních měřítek](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) napříč mnoha platformami webových aplikací a rámci. .NET Core skóroval v top 10 - vysoko nad Node.js a dalších konkurenčních platforem.

.NET Core spravuje Microsoft a komunita .NET na GitHubu.

## <a name="containers"></a>Kontejnery

V dnešní době je přirozené slyšet termín *kontejner* uvedený v každém rozhovoru o *cloud nativní*. V knize [Cloud Nativní vzory](https://www.manning.com/books/cloud-native-patterns), autor Cornelia Davis poznamenává, že "Kontejnery jsou velkým umožňujícím cloud-nativní software." Cloud Native Computing Foundation umisťuje kontejnerizaci mikroslužeb jako první krok v jejich [mapě Trail native cloud](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) – pokyny pro podniky, které začínají svou cestu nativní pro cloud.

Kontejnerizace mikroslužby je jednoduchá a přímočará. Kód, jeho závislosti a runtime jsou zabaleny do binárního souboru nazývaného [image kontejneru](https://docs.docker.com/glossary/?term=image). Obrázky jsou uloženy v [registru kontejneru](https://caylent.com/container-registries/), který funguje jako úložiště nebo knihovna pro obrázky. Registr může být umístěn ve vývojovém počítači, v datovém centru nebo ve veřejném cloudu. Docker sám udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/). Cloud Azure je vybaven [registru kontejnerů](https://azure.microsoft.com/services/container-registry/) pro ukládání ibi v blízkosti cloudových aplikací, které je spustí.

V případě potřeby převedete image na spuštěnou instanci kontejneru. Instance běží na libovolném počítači, který má nainstalovaný modul [runtime kontejneru.](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) Můžete mít libovolný počet instancí kontejnerizované služby podle potřeby.

Obrázek 1-5 ukazuje tři různé mikroslužeb, každý ve svém vlastním kontejneru, spuštěné na jednom hostiteli.

![Více kontejnerů spuštěné na hostiteli kontejneru](./media/hosting-mulitple-containers.png)

**Obrázek 1-5**. Více kontejnerů spuštěné na hostiteli kontejneru

Všimněte si, jak každý kontejner udržuje vlastní sadu závislostí a runtime, které se mohou lišit. Zde vidíme různé verze mikroslužby Produktu spuštěné na stejném hostiteli. Každý kontejner sdílí část základního hostitelského operačního systému, paměti a procesoru, ale je od sebe izolován.

Všimněte si, jak dobře kontejnermodel zahrnuje princip "závislosti" z [dvanáctifaktorové aplikace](https://12factor.net/).

> *Faktor \#2 určuje, že "Každá mikroslužba izoluje a balí vlastní závislosti, zahrnující změny bez dopadu na celý systém."*

Kontejnery podporují úlohy Linuxu i Windows. Cloud Azure otevřeně zahrnuje obojí. Zajímavé je, že je to Linux, ne Windows Server, který se stal nejoblíbenějším operačním systémem v Azure.

Zatímco existuje několik prodejců kontejnerů, Docker získal lví podíl na trhu. Společnost řídila pohyb softwarových kontejnerů. Stala se de facto standardem pro balení, nasazování a spouštění aplikací nativních pro cloud.

### <a name="why-containers"></a>Proč kontejnery?

Kontejnery poskytují přenositelnost a zaručují konzistenci napříč prostředími. Zapouzdřením vše do jednoho balíčku *izolovat* mikroslužeb a jeho závislosti z podkladové infrastruktury.

Můžete nasadit stejný kontejner v jakémkoli prostředí, které má modul runtime Docker. Kontejnerizované úlohy také eliminují náklady na předběžnou konfiguraci každého prostředí pomocí architektur, softwarových knihoven a modulů runtime.

Sdílením základní operační systém a hostitelské prostředky kontejnery mají mnohem menší nároky než úplný virtuální počítač. Menší velikost zvyšuje *hustotu*nebo počet mikroslužeb, které daný hostitel může spustit najednou.

### <a name="container-orchestration"></a>Orchestrace kontejnerů

Zatímco nástroje, jako je Docker, vytvářejí image a spouštějí kontejnery, potřebujete také nástroje pro jejich správu. Správa kontejnerů se provádí pomocí speciálního softwarového programu nazvaného kontejnerový orchestrátor. Při práci ve velkém měřítku orchestrace kontejneru je nezbytné.

Obrázek 1-6 ukazuje úlohy správy, které poskytují orchestrátory kontejneru.

![Co kontejnerové orchestrátory dělají](./media/what-container-orchestrators-do.png)

**Obrázek 1-6**. Co kontejnerové orchestrátory dělají

Následující tabulka popisuje běžné úlohy orchestrace.

|  Úlohy | Vysvětlení  |
| :-------- | :-------- |
| Plánování | Automaticky zřazují instance kontejnerů.|
| Afinita/anti-afinita | Zřizování kontejnerů v blízkosti nebo daleko od sebe, což pomáhá dostupnosti a výkonu. |
| Monitorování stavu | Automaticky detekuje a opravuje chyby.|
| Převzetí služeb při selhání | Automaticky reprovision instance se nezdařilo v pořádku počítače.|
| Škálování | Automaticky přidejte nebo odeberte instanci kontejneru, abyste uspokojili poptávku.|
| Sítě | Správa síťového překrytí pro komunikaci kontejnerů.|
| Zjišťování služeb | Povolit kontejnery najít navzájem.|
| Postupné inovace | Koordinujte přírůstkové upgrady s nasazením s nulovými prostoji. Automaticky vrátit zpět problematické změny.|

Všimněte si, jak orchestrátoři přijmout disposability a souběžnosti principy z [dvanáctifaktorové aplikace](https://12factor.net/), diskutovali dříve v kapitole.

> *Faktor \#9 určuje, že "Instance služby by měly být na jedno použití, upřednostňující rychlé spuštění pro zvýšení možností škálovatelnosti a řádné vypnutí opustit systém ve správném stavu. Kontejnery Dockeru spolu s orchestrátorem neodmyslitelně splňují tento požadavek."*

> *Faktor \#8 určuje, že "Služby horizontální navýšení kapacity přes velký počet malých identických procesů (kopie) na rozdíl od škálování na jednu velkou instanci na nejvýkonnější počítač k dispozici."*

Zatímco existuje několik kontejnerových orchestrátorů, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) se stal de facto standardem pro cloud-nativní svět. Je to přenosná, rozšiřitelná, open source platforma pro správu kontejnerizovaných úloh.

Můžete hostit vlastní instanci Kubernetes, ale pak byste byli zodpovědní za zajišťování a správu jeho zdrojů - což může být složité. Cloud Azure obsahuje Kubernetes jako spravovanou službu [Azure Kubernetes Service (AKS).](https://azure.microsoft.com/services/kubernetes-service/) Spravovaná služba umožňuje plně využívat její funkce, aniž byste ji museli instalovat a udržovat.

Služby Azure Kubernetes jsou podrobně popsány v kapitole 2 *Škálování cloudových nativních aplikací*.

## <a name="backing-services"></a>Podpůrné služby

Cloudové nativní systémy závisí na mnoha různých pomocných prostředcích, jako jsou úložiště dat, zprostředkovatelé zpráv, monitorování a služby identity. Tyto služby jsou označovány jako [podpůrné služby](https://12factor.net/backing-services).

 Obrázek 1-7 ukazuje mnoho běžných záložních služeb, které cloudnativní systémy spotřebovávají.

![Společné podpůrné služby](./media/common-backing-services.png)

**Obrázek 1-7**. Společné podpůrné služby

Podpůrné služby podporují princip "bezstátní příslušnosti" z [dvanáctifaktorové aplikace](https://12factor.net/), která byla popsána dříve v kapitole.

>*Faktor \#6* určuje, že "Každá mikroslužba by měla být spuštěna ve vlastním procesu, izolované od jiných spuštěných služeb. Externalizujte požadovaný stav pro záložní službu, jako je například distribuovaná mezipaměť nebo úložiště dat."

Můžete hostovat vlastní podpůrné služby, ale pak byste byli zodpovědní za licencování, zřizování a správu těchto prostředků.

Poskytovatelé cloudu nabízejí bohatý sortiment *spravovaných doprovodných služeb.* Místo toho, abyste službu vlastnili, jednoduše ji spotřebováváte. Poskytovatel provozuje prostředek ve velkém měřítku a nese odpovědnost za výkon, zabezpečení a údržbu. Monitorování, redundance a dostupnost jsou integrovány do služby. Poskytovatelé plně podporují své spravované služby - otevřete lístek a vyřeší váš problém.

Systémy nativní pro cloud upřednostňují spravované podpůrné služby od dodavatelů cloudu. Úspory času a práce jsou skvělé. Operační riziko hostování vlastní a zažívá potíže může dostat drahé rychle.

Osvědčeným postupem je považovat záložní službu jako *připojený prostředek*, dynamicky vázaný na mikroslužbu s informacemi (adresa URL a pověření) uloženými v externí konfiguraci. Tyto pokyny jsou uvedeny v [aplikaci dvanácti faktorů](https://12factor.net/), která je popsána dříve v kapitole.

>*Faktor \#4* určuje, že podpůrné služby "by měly být vystaveny prostřednictvím adresovatelné adresy URL. Tím odpojíprostředek od aplikace, což umožňuje zaměnitelné."

>*Faktor \#3* určuje, že "Informace o konfiguraci je přesunuta z mikroslužeb a externalizována prostřednictvím nástroje pro správu konfigurace mimo kód."

Pomocí tohoto vzoru může být záložní služba připojena a odpojena bez změn kódu. Můžete propagovat mikroslužbu z QA do pracovního prostředí. Aktualizujete konfiguraci mikroslužeb tak, aby ukazovala na podpůrné služby v pracovní správě a vstříkla nastavení do kontejneru prostřednictvím proměnné prostředí.

Dodavatelé cloudu poskytují řešení API pro komunikaci s jejich proprietárními službami zálohování. Tyto knihovny zapouzdřují instalatérství a složitost. Komunikace přímo s těmito api bude úzce spárovat váš kód na podporu služby. Je lepší praxe izolovat podrobnosti implementace rozhraní API dodavatele. Zaveďte zprostředkovatelskou vrstvu nebo zprostředkující rozhraní API, které vystaví obecné operace kódu služby. Tato volná spojka umožňuje vyměnit jednu záložní službu za jinou nebo přesunout kód do jiného veřejného cloudu, aniž byste museli provádět změny v kódu hlavní linky.

Podpůrné služby jsou podrobně popsány kapitola 5, *Cloud-nativní vzory dat*a kapitola 4, *Cloud-nativní komunikační vzory*.

## <a name="automation"></a>Automatizace

Jak jste viděli, cloudové nativní systémy využívají mikroslužeb, kontejnerů a modernínávrh systému k dosažení rychlosti a flexibility. Ale to je jen část příběhu. Jak zřazujete cloudová prostředí, na kterých tyto systémy běží? Jak rychle nasazujete funkce a aktualizace aplikací? Jak završujete celý obraz?

Zadejte široce přijímanou praxi [infrastruktury jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), nebo IaC.

S IaC automatizujete zřizování platformy a nasazení aplikací. V podstatě použijete postupy softwarového inženýrství, jako je testování a správa verzí, na postupy DevOps. Vaše infrastruktura a nasazení jsou automatizované, konzistentní a opakovatelné.

### <a name="automating-infrastructure"></a>Automatizace infrastruktury

Nástroje, jako je [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform a Azure [CLI](https://docs.microsoft.com/cli/azure/), umožňují deklarativně skriptovat cloudovou infrastrukturu, kterou potřebujete. Názvy prostředků, umístění, kapacity a tajné kódy jsou parametrizovány a dynamické. Skript je verzí a vrácena se změnami do správy zdrojového kódu jako artefakt projektu. Můžete vyvolat skript zřídit konzistentní a opakovatelné infrastruktury napříč systémových prostředích, jako je qa, pracovní a produkční.

Pod kapotou, IaC je idempotentní, což znamená, že můžete spustit stejný skript znovu a znovu bez vedlejších účinků. Pokud tým potřebuje provést změnu, upraví a znovu spustí skript. Ovlivněny jsou pouze aktualizované prostředky.

V článku [Co je infrastruktura jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Autor Sam Guckenheimer popisuje, jak, "Týmy, které implementují IaC může poskytovat stabilní prostředí rychle a ve velkém měřítku. Týmy vyhnout ruční konfiguraci prostředí a vynutit konzistenci tím, že představuje požadovaný stav jejich prostředí prostřednictvím kódu. Nasazení infrastruktury s IaC jsou opakovatelné a zabránit problémům za běhu způsobené posunu konfigurace nebo chybějící závislosti. Týmy DevOps mohou spolupracovat s jednotnou sadou postupů a nástrojů pro rychlé, spolehlivé a škálování aplikací a jejich podpůrné infrastruktury."

### <a name="automating-deployments"></a>Automatizace nasazení

[Aplikace s dvanácti faktory](https://12factor.net/), diskutované dříve, volá samostatné kroky při transformaci dokončeného kódu do spuštěné aplikace.

> *Faktor \#5* určuje, že "Každá verze musí vynutit přísné oddělení mezi fázemi sestavení, vydání a spuštění. Každý z nich by měl být označen jedinečným ID a měl by podporovat možnost vrátit se zpět."

Moderní CI/CD systémy pomáhají naplnit tento princip. Poskytují samostatné kroky nasazení a pomáhají zajistit konzistentní a kvalitní kód, který je snadno dostupný uživatelům.

Obrázek 1-8 znázorňuje oddělení v rámci procesu nasazení.

![Kroky nasazení v kanálu CI/CD](./media/build-release-run-pipeline.png)

**Obrázek 1-8**. Kroky nasazení v kanálu CI/CD

Na předchozím obrázku věnujte zvláštní pozornost oddělení úkolů.

Vývojář vytvoří funkci v jejich vývojovém prostředí, iterace prostřednictvím co se nazývá "vnitřní smyčka" kódu, spustit a ladění. Po dokončení se tento kód *zasouvá* do úložiště kódu, jako je GitHub, Azure DevOps nebo BitBucket.

Push aktivuje fázi sestavení, která transformuje kód do binární artefakt. Práce je implementována pomocí kanálu [průběžné integrace (CI).](https://martinfowler.com/articles/continuousIntegration.html) Automaticky vytvoří, testuje a zabalí aplikaci.

Fáze vydání vyzvedne binární artefakt, použije informace o konfiguraci externí aplikace a prostředí a vytvoří neměnnou verzi. Verze je nasazena do zadaného prostředí. Práce je implementována s kanálem [průběžného doručování (CD).](https://martinfowler.com/bliki/ContinuousDelivery.html) Každé vydání by mělo být identifikovatelné. Můžete říci: "Toto nasazení je spuštěna verze 2.1.1 aplikace."

Nakonec uvolněná funkce je spuštěna v prostředí provádění cíle. Verze jsou neměnné, což znamená, že každá změna musí vytvořit novou verzi.

Při použití těchto postupů se organizace radikálně vyvinuly v tom, jak dodávají software. Mnoho z nich se přesunulo z čtvrtletních verzí na aktualizace na vyžádání. Cílem je zachytit problémy na počátku vývojového cyklu, když jsou levnější opravit. Čím delší je doba mezi integracemi, tím dražší problémy se řeší.  Díky konzistenci v procesu integrace mohou týmy častěji poznávat změny kódu, což vede k lepší spolupráci a kvalitě softwaru.

### <a name="azure-pipelines"></a>Azure Pipelines

Cloud Azure zahrnuje novou službu CI/CD s názvem [Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/), která je součástí nabídky [Azure DevOps](https://azure.microsoft.com/services/devops/) znázorněné na obrázku 1–9.

![Kanály Azure v devops](./media/devops-components.png)

**Obrázek 1-9**. Nabídky Azure DevOps

Azure Pipelines je cloudová služba, která kombinuje průběžnou integraci (CI) a průběžné doručování (CD). Kód můžete automaticky testovat, vytvářet a odesílat libovolnému cíli.

Kanál definujete v kódu v souboru YAML vedle zbytku kódu pro vaši aplikaci.

- Kanál je verzí s vaším kódem a řídí se stejnou strukturou větvení.
- Ověření změn získáte prostřednictvím kontrol kódu v žádostech o přijetí změn a zásadách vytváření větev.
- Každá větev, kterou používáte můžete přizpůsobit zásady sestavení úpravou souboru azure-pipelines.yml.
- Soubor kanálu je vrácena se změnami do správy verzí a může být zkoumána, pokud došlo k potížím.

Služba Azure Pipelines podporuje většinu poskytovatelů Gitu a může generovat kanály nasazení pro aplikace napsané na platformách Linux, macOS nebo Windows. Obsahuje podporu pro Java, .NET, JavaScript, Python, PHP, Go, XCode a C++.

>[!div class="step-by-step"]
>[Předchozí](introduction.md)
>[další](candidate-apps.md)
