---
title: Zabezpečení Azure pro Cloud – nativní aplikace
description: Architekt cloudových nativních aplikací .NET pro Azure | Zabezpečení Azure pro nativní cloudové aplikace
ms.date: 05/13/2020
ms.openlocfilehash: 996c7075b252466a3b3374f1e75e64315fdd6fc7
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557643"
---
# <a name="azure-security-for-cloud-native-apps"></a>Zabezpečení Azure pro Cloud – nativní aplikace

Nativní aplikace v cloudu můžou být jednodušší a obtížnější pro zabezpečení než tradiční aplikace. Na nevýhodou je nutné zabezpečit více menších aplikací a zvýšit spotřebu energie pro sestavení infrastruktury zabezpečení. Heterogenní povaha programovacích jazyků a stylů ve většině nasazení služeb také znamená, že je potřeba věnovat větší pozornost bulletinům zabezpečení z mnoha různých poskytovatelů.

V případě překlopení menších služeb, z nichž každá má vlastní úložiště dat, omezte rozsah útoku. Pokud útočník napadnout jeden systém, je pravděpodobnější, že by útočník mohl přejít na jiný systém, než je v aplikaci monolitické. Hranice procesu jsou silné hranice. Pokud se navíc nevrátí záloha databáze, poškození je více omezené, protože tato databáze obsahuje pouze podmnožinu dat a pravděpodobně neobsahuje osobní údaje.

## <a name="threat-modeling"></a>Modelování hrozeb

Bez ohledu na to, zda výhody převažují z nevýhod aplikací nativních pro Cloud, musí být dodržena stejná holistický zabezpečení místo. Zabezpečení a bezpečnostní úvaha musí být součástí všech kroků vývojového a provozního scénáře. Při plánování aplikace klást otázky jako:

- Jaký by byl dopad těchto dat ztracen?
- Jak můžeme omezit škody ze špatných dat vložených do této služby?
- Kdo má mít přístup k těmto datům?
- Jsou v rámci procesu vývoje a vydávání k dispozici zásady auditu?

Všechny tyto otázky jsou součástí procesu nazývaného [modelování hrozeb](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool). Tento proces se snaží odpovědět na otázku, jaké hrozby se v systému nacházejí, jak by se staly hrozbami, a potenciální poškození.

Po navázání seznamu hrozeb se musíte rozhodnout, jestli se mají zmírnit. V některých případech je hrozba nepravděpodobné a nákladná k plánování za to, že nestojí za to, že se na ni stráví energie. Například některý objekt actor na úrovni stavu může vložit změny do návrhu procesu, který je používán miliony zařízení. Nyní namísto spuštění určité části kódu v [okruhu 3](https://en.wikipedia.org/wiki/Protection_ring)se tento kód spouští na prstenci 0. To umožňuje zneužití, které může obejít hypervisor a spustit kód útoku na holé počítače, což umožňuje útoky na všech virtuálních počítačích, které jsou na tomto hardwaru spuštěny.

Změněné procesory se obtížně zjišťují bez použití mikrooboru a pokročilých znalostí na návrh Silicon tohoto procesoru. Tento scénář se pravděpodobně nestane a finančně se omezuje, takže by pravděpodobně nedocházelo k tomu, že by pro něj bylo vhodné vytvářet ochranu proti zneužití.

Pravděpodobnější hrozby, jako je například řízení přerušeného přístupu, které `Id` umožňuje zvýšení útoků (nahrazení `Id=2` `Id=3` v rámci adresy URL) nebo injektáže kódu SQL, jsou přitažlivější k vytváření ochrany proti. Zmírnění těchto hrozeb je poměrně přijatelné pro sestavování a ochranu proti bezpečnostním otvorům absolutně, které vycházejí ze své pověsti společnosti.

## <a name="principle-of-least-privilege"></a>Princip nejnižších oprávnění

Jednou z nalezených nápadů v zabezpečení počítače je princip minimálního oprávnění (POLP). V podstatě je to základní nápad v podobě zabezpečení, který je digitální nebo fyzický. V krátkém případě se jedná o to, že každý uživatel nebo proces by měl mít nejnižší počet práv ke spuštění úkolu.

Jako příklad si můžete představit jako v bance: přístup k bezpečnosti je neobvyklá aktivita. Proto Průměrná známka nemůže otevřít bezpečný sám sebe. Aby bylo možné získat přístup, musí zvýšit svůj požadavek pomocí Správce banky, který provede další kontroly zabezpečení.

V systému počítače je příkladem fantastická práva uživatele, který se připojuje k databázi. V mnoha případech existuje jeden uživatelský účet, který se používá pro sestavení struktury databáze a spuštění aplikace. S výjimkou případů, kdy účet, na kterém běží aplikace, nemusí mít možnost aktualizovat informace o schématu. Měl by existovat několik účtů, které poskytují různé úrovně oprávnění. Aplikace by měla používat pouze úroveň oprávnění, která uděluje přístup pro čtení a zápis k datům v tabulkách. Tento druh ochrany eliminuje útoky zaměřené na vyřazení tabulek databáze nebo zavedení škodlivých triggerů.

Skoro každá část sestavování nativních cloudových aplikací může mít za to, že je nutné vytvořit princip nejnižších oprávnění. Při nastavování bran firewall, skupin zabezpečení sítě, rolí a oborů v řízení přístupu na základě role (RBAC) je můžete najít při hraní.

## <a name="penetration-testing"></a>Testování průniku

Vzhledem k většímu počtu aplikací se počet vektorů útoku zvyšuje na míru alarmu. Pro modelování hrozeb dochází k chybě, která by mohla být vykonána stejnými lidmi, kteří sestavují systém. Stejně jako v případě, že mnoho vývojářů má potíže s plánováním interakcí uživatelů a pak vytvářet nepoužitelná uživatelská rozhraní, většina vývojářů má potíže se zobrazením všech vektorů útoku. Je také možné, že vývojáři, kteří sestavují systém, nejsou dobře vycházet z metodologie útoků a nezpůsobují něco důležitého.

Testování průniku nebo "testování perem" zahrnuje uvedení do externích aktérů k pokusu o útok na systém. Tyto útočníci můžou být externími poradenskými společnostmi nebo jinými vývojáři, kteří mají dobré znalosti zabezpečení z jiné části firmy. Přidávají se carte blanche k pokusu o převýšení systému. Často se v nich nacházejí velké bezpečnostní otvory, které je potřeba opravit. Někdy se může stát, že vektor útoku bude něco zcela neočekávaně, například zneužití útoku phishing proti generální ŘEDITELi.

Samotný Azure neustále prochází útoky z [týmu hackerů v Microsoftu](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/). V průběhu let byly nejprve vyhledány desítky potenciálně závažných vektorů útoku a jejich uzavírání předtím, než bude možné je zneužít externě. Lépe se zaměřuje na cíl, což je pravděpodobnější, že se externí actor pokusí ho zneužít a existuje několik cílů na světovém větším cíli, než je Azure.

## <a name="monitoring"></a>Monitorování

Pokud by se útočník pokusil proniknout aplikaci, mělo by to být upozornění. Často se útoky můžou Spotted prozkoumáním protokolů ze služeb. Útoky opouští příznakem příznaku, který může být Spotted před úspěchem. V případě, že se útočník pokouší odhadnout heslo, provede mnoho požadavků na přihlašovací systém. Monitorování systému přihlášení dokáže detekovat divné vzory, které nejsou v typickém vzorovém přístupu. Toto monitorování se dá přepínat na výstrahu, která může zase upozornit na určitou osobu, aby aktivovala určitý druh protiopatření. Vysoce vyspělý monitorovací systém může dokonce provádět akce na základě těchto odchylek, které přidávají pravidla pro blokování požadavků nebo omezení odezvy.

## <a name="securing-the-build"></a>Zabezpečení sestavení

Jedno místo, kde je často přehledáno zabezpečení, je okolo procesu sestavení. Pouze by měl spustit kontroly zabezpečení, jako je například vyhledávání nezabezpečeného kódu nebo přihlašovací údaje k vrácení se změnami, ale samotný Build by měl být zabezpečený. Pokud dojde k ohrožení bezpečnosti serveru sestavení, poskytuje fantastická vektor k zavedení libovolného kódu do produktu.

Představte si, že útočník se zlými úmysly ukrást hesla uživatelů přihlašovat k webové aplikaci. Mohli by zavést krok sestavení, který upraví rezervovaného kódu tak, aby na jiný server kontroloval jakoukoli žádost o přihlášení. Při dalším kódu projde sestavení se tiše aktualizuje. Kontrola ohrožení zabezpečení zdrojového kódu nebude zachytit při spuštění před sestavením. Stejně tak nikdo nebude zachytit v revizi kódu, protože kroky sestavení jsou na serveru sestavení živé. Zneužitný kód bude jít do produkčního prostředí, kde může shromažďovat hesla. Pravděpodobně není k dispozici žádný protokol auditu změny procesu sestavení nebo alespoň nikdo nesleduje audit.

Toto je dokonalý příklad zdánlivě nízké hodnoty, který se dá použít k přerušení systému. Jakmile útočník dojde k porušení hraničního systému, může začít pracovat na hledání způsobů, jak zvýšit svoje oprávnění na místo, kde může způsobit skutečnou škodu.

## <a name="building-secure-code"></a>Sestavování zabezpečeného kódu

.NET Framework je již poměrně zabezpečenou architekturou. Zabrání některému nástrah nespravovaného kódu, jako je například procházení konců polí. Práce se aktivně provádí za účelem opravy děr zabezpečení při jejich zjištění. K dispozici je i [Bounty program](https://www.microsoft.com/msrc/bounty) , který zaplatí výzkumným pracovníkům, aby vyhledal problémy v rámci rozhraní a nahlásil je místo jejich zneužití.

Existuje mnoho způsobů, jak zvýšit zabezpečení kódu .NET. Následující pokyny, jako je například [pokyny k zabezpečenému kódování pro článek o rozhraní .NET](../../standard/security/secure-coding-guidelines.md) , jsou přijatelné krok k zajištění zabezpečení kódu od základu. [OWASP prvních 10](https://owasp.org/www-project-top-ten/) je další nevýznamný průvodce pro sestavování zabezpečeného kódu.

Proces sestavení je dobrým místem, kde můžete umístit nástroje pro kontrolu, aby se zjistily problémy ve zdrojovém kódu předtím, než se provedou v produkci. Většina každého projektu má závislosti na některých dalších balíčcích. Nástroj, který může kontrolovat zastaralé balíčky, zachytí problémy v noci. I při sestavování imagí Docker je vhodné zkontrolovat a ujistit se, že základní image nemá známá slabá místa. Další věc, kterou je třeba zkontrolovat, je, že nikdo nechtěně rezervoval přihlašovací údaje.

## <a name="built-in-security"></a>Integrované zabezpečení

Azure je navržený tak, aby se vyrovnal použitelnost a zabezpečení pro většinu uživatelů. Různí uživatelé budou mít různé požadavky na zabezpečení, takže potřebují vyladit jejich přístup k zabezpečení cloudu. Microsoft zveřejňuje v [centru](https://azure.microsoft.com/support/trust-center/)zabezpečení skvělé informace o zabezpečení. Tento prostředek by měl být prvním zastavením pro odborníky, kteří mají zájem o fungování integrovaných technologií pro zmírnění útoků.

V rámci Azure Portal je [Azure Advisor](https://azure.microsoft.com/services/advisor/) systém, který neustále kontroluje prostředí a vytváří doporučení. Některá z těchto doporučení jsou navržená tak, aby ušetřila peníze uživatelů, ale jiné jsou navržené k identifikaci potenciálně nezabezpečených konfigurací, jako je třeba otevření kontejneru úložiště na světě a ochrana Virtual Network.

## <a name="azure-network-infrastructure"></a>Síťová infrastruktura Azure

V místním prostředí nasazení se pro nastavení sítě vyhradí Skvělé úspory energie. Nastavení směrovačů, přepínačů a takových složitých práce. Sítě umožňují určitým prostředkům komunikovat s jinými prostředky a v některých případech zabraňte přístupu. Častým síťovým pravidlem je omezit přístup k produkčnímu prostředí z vývojového prostředí na vypnuté, že se částečně vyvinutá část kódu spouští Awry a odstraňuje Swath dat.

Dopředné: většina prostředků Azure PaaS má jenom základní a opravňující nastavení sítě. Například kdokoli na internetu může získat přístup ke službě App Service. Nové instance SQL Server obvykle mají omezený přístup, aby k nim externí strany nemohly přistupovat, ale rozsahy IP adres používané samotným Azure jsou povolené prostřednictvím. I když je SQL Server chráněný před externími hrozbami, stačí, když si nastavili předmost Azure, ze kterého můžou spouštět útoky na všechny instance SQL v Azure.

Naštěstí je možné do Azure Virtual Network umístit většinu prostředků Azure, které umožňují jemnější řízení přístupu. Podobně jako v případě, že místní sítě vytváří privátní sítě, které jsou chráněny před širším světem, jsou virtuální sítě ostrovy privátních IP adres, které se nacházejí v síti Azure.

![Obrázek 9-1 virtuální síť v Azure](./media/virtual-network.png)

**Obrázek 9-1**. Virtuální síť v Azure.

Stejným způsobem, že místní sítě mají bránu firewall, která řídí přístup k síti, můžete vytvořit podobnou bránu firewall na hranici virtuální sítě. Ve výchozím nastavení mohou všechny prostředky ve virtuální síti stále komunikovat s internetem. Jsou to jenom příchozí připojení, která vyžadují určitou formu explicitní výjimky brány firewall.

Po navázání sítě mohou být interní prostředky, jako jsou účty úložiště, nastavené tak, aby povolovaly jenom přístup k prostředkům, které jsou taky Virtual Network. Tato brána firewall poskytuje vyšší úroveň zabezpečení, pokud by klíče pro tento účet úložiště neunikly, útočníky se k ní nemohli připojit, aby bylo možné zneužít nevyužité klíče. Toto je další příklad principu nejnižší úrovně oprávnění.

Uzly v clusteru Azure Kubernetes se můžou zúčastnit virtuální sítě stejně jako jiné prostředky, které jsou nativní pro Azure. Tato funkce se nazývá [síťové rozhraní kontejneru Azure](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md). V důsledku toho přidělí podsíť v rámci virtuální sítě, na které se přiřazují virtuální počítače a image kontejneru.

Pokračujeme v cestě k ilustraci principu minimálního oprávnění, ne všechny prostředky v Virtual Network musí komunikovat s každým jiným zdrojem. Například v aplikaci, která poskytuje webové rozhraní API prostřednictvím účtu úložiště a databáze SQL, není pravděpodobné, že databáze a účet úložiště musí vzájemně komunikovat. Jakékoli sdílení dat mezi nimi by mohlo projít webovou aplikací. Proto je možné použít [skupinu zabezpečení sítě (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) k odepření provozu mezi těmito dvěma službami.

Zásada odepření komunikace mezi prostředky může být obtěžující k implementaci, zejména z pozadí používání Azure bez omezení provozu. V některých dalších cloudech je koncept skupin zabezpečení sítě mnohem více rozšířených. Výchozí zásadou pro AWS je například to, že prostředky nemohou komunikovat mezi sebou, dokud nejsou povoleny pravidly v NSG. I když je to pomalejší, nabízí více omezující prostředí bezpečnější výchozí nastavení. Použití řádných postupů DevOps, zejména použití [Azure Resource Manager nebo terraformu](infrastructure-as-code.md) ke správě oprávnění, může zjednodušit řízení pravidel.

Virtuální sítě mohou být užitečné také při nastavování komunikace mezi místními a cloudovým prostředkům. K bezproblémovému připojení těchto dvou sítí lze použít virtuální privátní síť. To umožňuje provozování virtuální sítě bez jakéhokoli řazení brány pro scénáře, ve kterých jsou všichni uživatelé na pracovišti. K dispozici je řada technologií, které lze použít k vytvoření této sítě. Nejjednodušší je použít síť VPN typu [site-to-site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) , kterou je možné zřídit mezi mnoha směrovači a Azure. Provoz se šifruje a tuneluje přes Internet za stejné náklady za každý bajt jako jakýkoliv jiný provoz. V případě scénářů, kde je žádoucí větší šířka pásma nebo větší zabezpečení, Azure nabízí službu s názvem [Express Route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) , která používá privátní okruh mezi místní sítí a Azure. Je levnější a obtížné vytvořit, ale také bezpečnější.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Řízení přístupu na základě role pro omezení přístupu k prostředkům Azure

RBAC je systém, který poskytuje identitu aplikacím běžícím v Azure. Aplikace mají přístup k prostředkům pomocí této identity místo nebo kromě používání klíčů nebo hesel.

## <a name="security-principals"></a>Objekty zabezpečení

První komponentou v RBAC je objekt zabezpečení. Objekt zabezpečení může být uživatel, skupina, instanční objekt nebo spravovaná identita.

![Obrázek 9-2 různé typy objektů zabezpečení](./media/rbac-security-principal.png)

**Obrázek 9-2**. Různé typy objektů zabezpečení.

- Uživatel – libovolný uživatel, který má účet v Azure Active Directory je uživatel.
- Skupina – kolekce uživatelů z Azure Active Directory. Jako člen skupiny uživatel převezme role této skupiny kromě jejich vlastních.
- Instanční objekt – identita zabezpečení, pod kterou se spouštějí služby nebo aplikace.
- Spravovaná identita – Azure Active Directory identitou, kterou spravuje Azure. Spravované identity se obvykle používají při vývoji cloudových aplikací, které spravují přihlašovací údaje pro ověřování ve službách Azure.

Objekt zabezpečení lze použít pro většinu prostředků. To znamená, že je možné přiřadit objekt zabezpečení k kontejneru běžícímu v rámci Azure Kubernetes a umožnit mu tak přístup k tajným klíčům uloženým v Key Vault. Funkce Azure by mohla převzít oprávnění, které mu umožní komunikovat s instancí služby Active Directory a ověřit token JWT pro volajícího uživatele. Po povolení služeb u instančního objektu je možné jejich oprávnění spravovat podrobně pomocí rolí a oborů.

## <a name="roles"></a>Role

Objekt zabezpečení může převzít na mnoho rolí nebo s využitím více sartorial analogie, což je hodně Hats. Každá role definuje řadu oprávnění, jako je například "čtení zpráv z Azure Service Busho koncového bodu". Efektivní sadou oprávnění objektu zabezpečení je kombinace všech oprávnění přiřazených ke všem rolím, které má objekt zabezpečení. Azure má velký počet předdefinovaných rolí a uživatelů, kteří můžou definovat své vlastní role.

![Obrázek 9-3 Definice rolí RBAC](./media/rbac-role-definition.png)

**Obrázek 9-3**. Definice rolí RBAC

Součástí Azure je také řada rolí na vysoké úrovni, jako je vlastník, přispěvatel, čtenář a správce uživatelských účtů. U role vlastníka má objekt zabezpečení přístup k všem prostředkům a přiřazuje oprávnění ostatním. Přispěvatel má stejnou úroveň přístupu ke všem prostředkům, ale nemůže přiřadit oprávnění. Čtenář může zobrazit jenom existující prostředky Azure a správce účtu uživatele může spravovat přístup k prostředkům Azure.

Podrobnější předdefinované role, jako je [Přispěvatel zóny DNS](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) , mají práva omezená na jednu službu. Objekty zabezpečení můžou převzít libovolný počet rolí.

## <a name="scopes"></a>Obory

Role se dají použít u omezené sady prostředků v Azure. Pokud například použijete obor na předchozí příklad čtení z Service Bus fronty, můžete omezit oprávnění k jedné frontě: "číst zprávy z Azure Service Bus koncového bodu `blah.servicebus.windows.net/queue1` ".

Rozsah může být zúžený jako jeden prostředek nebo může být použit pro celou skupinu prostředků, předplatné nebo dokonce skupinu pro správu.

Při testování, jestli má objekt zabezpečení určité oprávnění, se vezme v úvahu kombinace role a rozsahu. Tato kombinace poskytuje výkonný mechanizmus ověřování.

## <a name="deny"></a>Odepřít

Dříve byla pro RBAC povolena pouze pravidla "Povolit". Toto chování pomohlo vytvořit některé obory. Například povolení přístupového objektu zabezpečení ke všem účtům úložiště s výjimkou povinného udělení výslovného oprávnění pro potenciálně nekonečné seznamy účtů úložiště. Pokaždé, když se vytvoří nový účet úložiště, musí se do tohoto seznamu účtů přidat. Tato zvýšení režijních nákladů na správu, která určitě nejsou žádoucí

Pravidla zamítnutí mají přednost před pravidly povolení. Nyní představuje stejný obor "Povolit vše kromě jednoho", který může představovat dvě pravidla "Povolit vše" a "Odepřít tuto" jednu specifickou ". Pravidla zamítnutí neumožňují jenom správu, ale umožňují prostředkům, které jsou navíc zabezpečené, zakázáním přístupu všem.

## <a name="checking-access"></a>Kontrola přístupu

Jak je možné si představit, může mít velký počet rolí a oborů, aby bylo možné zjistit efektivní oprávnění instančního objektu poměrně obtížné. Piling pravidla odepření, která se na nich nacházejí, slouží pouze ke zvýšení složitosti. Naštěstí je k dispozici Kalkulačka oprávnění, která může zobrazit skutečná oprávnění pro libovolný instanční objekt. Obvykle se nachází na kartě IAM na portálu, jak je znázorněno na obrázku 10-3.

![Obrázek 9-4 – Kalkulačka oprávnění pro službu App Service](./media/check-rbac.png)

**Obrázek 9-4**. Kalkulačka oprávnění pro službu App Service.

## <a name="securing-secrets"></a>Zabezpečení tajných kódů

Hesla a certifikáty jsou běžným vektorem útoku pro útočníky. Hardware odhalující hesla může provést útok hrubou silou a pokusit se odhadnout miliardy hesel za sekundu. Proto je důležité, aby hesla používaná pro přístup k prostředkům byla silná a s velkým množstvím znaků. Tato hesla jsou přesně typu hesla, která jsou prakticky nemožná zapamatovatelná. Naštěstí hesla v Azure ve skutečnosti nemusíte znát ani žádný člověk.

Mnohé z [odborníků na zabezpečení navrhují](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) použití Správce hesel k tomu, aby vaše vlastní hesla byla nejlepším řešením. Při centralizaci hesel na jednom místě vám taky umožní používat velmi složitá hesla a zajistit, aby byly pro každý účet jedinečné. V Azure existuje stejný systém: centrální úložiště tajných kódů.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault poskytuje centralizované umístění pro ukládání hesel pro věci, jako jsou databáze, klíče rozhraní API a certifikáty. Po zadání tajného klíče do trezoru se už znovu nezobrazí a příkazy k jeho extrakci a zobrazení jsou záměrně komplikované. Informace v bezpečí jsou chráněné pomocí softwarového šifrování nebo ověřených modulů zabezpečení hardwaru na úrovni FIPS 140-2 úrovně 2.

Přístup k trezoru klíčů se poskytuje prostřednictvím RBACs, což znamená, že k informacím v trezoru nemůžou přistupovat jenom žádného uživatele. Řekněme, že webová aplikace chce získat přístup k databázovému připojovacímu řetězci uloženému v Azure Key Vault. Aby bylo možné získat přístup, aplikace musí být spuštěny pomocí instančního objektu. V rámci této předpokládané role mohou tajné klíče přečíst z bezpečného. Existuje řada různých nastavení zabezpečení, která mohou dále omezovat přístup k úložišti aplikace, aby nemohly aktualizovat tajné kódy, ale číst je pouze.

Přístup k trezoru klíčů je možné monitorovat, aby se zajistilo, že k trezoru budou přistupovat jenom očekávané aplikace. Protokoly je možné integrovat zpátky do Azure Monitor a odemknout možnost nastavení výstrah při zjištění neočekávaných podmínek.

## <a name="kubernetes"></a>Kubernetes

V rámci Kubernetes existuje podobná služba pro údržbu malých tajných informací. Tajné kódy Kubernetes lze nastavit prostřednictvím typického `kubectl` spustitelného souboru.

Vytvoření tajného klíče je jednoduché jako hledání verze Base64 hodnot, které se mají uložit:

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Pak ho přidáte do souboru tajných kódů s názvem `secret.yml` , například, který vypadá podobně jako v následujícím příkladu:

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

Nakonec můžete tento soubor načíst do Kubernetes spuštěním následujícího příkazu:

```console
kubectl apply -f ./secret.yaml
```

Tyto tajné kódy pak mohou být připojeny do svazků nebo vystaveny kontejnerovým procesům prostřednictvím proměnných prostředí. [32bitový](https://12factor.net/) přístup k aplikacím při sestavování aplikací navrhuje použití nejnižšího společného jmenovatele k přenosu nastavení do aplikace. Proměnné prostředí jsou nejnižší společný jmenovatel, protože jsou podporované bez ohledu na operační systém nebo aplikaci.

Alternativou k používání integrovaných tajných klíčů Kubernetes je přístup k tajným klíčům v Azure Key Vault v rámci Kubernetes. Nejjednodušší způsob, jak to provést, je přiřadit roli RBAC kontejneru, který hledá tajné kódy. Aplikace pak může používat rozhraní Azure Key Vault API pro přístup k tajným klíčům. Tento přístup ale vyžaduje úpravy kódu a nedodržuje vzor použití proměnných prostředí. Místo toho je možné vložit hodnoty do kontejneru. Tento přístup je ve skutečnosti bezpečnější než používání tajných klíčů Kubernetes přímo, protože k nim mají přístup uživatelé v clusteru.

## <a name="encryption-in-transit-and-at-rest"></a>Šifrování při přenosu a v klidovém provozu

Zachování bezpečnosti dat je důležité, ať už se jedná o disk nebo přenos mezi různými různými službami. Nejúčinnější způsob, jak zabránit úniku dat, je zašifrovat ho do formátu, který jiní uživatelé nemůžou snadno přečíst. Azure podporuje široké spektrum možností šifrování.

### <a name="in-transit"></a>Při přenosu

Existuje několik způsobů, jak šifrovat provoz v síti v Azure. Přístup ke službám Azure se obvykle provádí prostřednictvím připojení, která používají protokol TLS (Transport Layer Security). Například všechna připojení k rozhraním API Azure vyžadují připojení TLS. Připojení ke koncovým bodům ve službě Azure Storage může být stejně omezené jenom přes šifrovaná připojení TLS.

TLS je složitý protokol a stačí vědět, že připojení pomocí protokolu TLS nestačí k zajištění zabezpečení. Například protokol TLS 1,0 je chronicky nezabezpečený a TLS 1,1 není mnohem lepší. I v rámci verzí TLS existují různá nastavení, která umožňují snazší dešifrování připojení. Nejlepším postupem je ověřit a zjistit, jestli připojení k serveru používá aktualizované a dobře nakonfigurované protokoly.

Tuto kontrolu může provést externí služba, například test serveru SSL Labs SSL. Testovací běh na typický koncový bod Azure, v tomto případě koncový bod služby Service Bus, poskytuje téměř dokonalý výsledek A.

Dokonce i služby, jako jsou databáze SQL Azure, používají šifrování TLS, aby data zůstala skrytá. Zajímavou součástí šifrování přenášených dat pomocí protokolu TLS je to, že není možné, ani pro společnost Microsoft, aby naslouchala v souvislosti s připojením mezi počítači se systémem TLS. To by mělo poskytovat pohodlí pro společnosti, které se zabývají tím, že jejich data mohou být ohrožena společností Microsoft nebo dokonce i objektem Actor, který má více prostředků než standardní útočník.

![Obrázek 9-5 sestava SSL Labs ukazující skóre pro Service Bus koncový bod.](./media/ssl-report.png)

**Obrázek 9-5**. Sestava SSL Labs zobrazuje skóre pro Service Bus koncový bod.

I když tato úroveň šifrování nebude stačit pro celou dobu, měla by inspirovat jistotu, že připojení Azure TLS jsou poměrně zabezpečená. Azure bude i nadále vyvíjet standardy zabezpečení, protože se zlepšuje šifrování. Je dobré si poznat, že někdo sleduje standardy zabezpečení a aktualizuje Azure při jejich vylepšování.

### <a name="at-rest"></a>V klidovém umístění

V libovolné aplikaci je k dispozici několik míst, kde jsou data na disku. Samotný kód aplikace je načten z nějakého mechanismu úložiště. Většina aplikací používá také určitý druh databáze, například SQL Server, Cosmos DB nebo dokonce i cenově výhodnější Table Storage. Tyto databáze využívají velmi šifrované úložiště, aby se zajistilo, že vaše data budou moct číst nikdo jiný než aplikace se správnými oprávněními. I systémové operátory nemohou číst data, která byla zašifrována. Takže si zákazníci mohou zůstat tajnosti i nadále tajnými informacemi.

### <a name="storage"></a>Storage

Jako modul Azure Storage se používá větší počet Azure. Disky virtuálního počítače jsou připojené k Azure Storage. Služby Azure Kubernetes běží na virtuálních počítačích, které samy o sebou hostují Azure Storage. Mimo jiné technologie bez serveru, například Azure Functions aplikace a Azure Container Instances, se vyčerpá disk, který je součástí Azure Storage.

Pokud je Azure Storage dobře zašifrovaná, pak poskytuje základ pro většinu všeho jiného, než se šifrují taky. Azure Storage [je šifrovaný](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) pomocí standardu AES [140-2](https://en.wikipedia.org/wiki/FIPS_140) kompatibilního s [256 AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard). Jedná se o dobře používanou technologii šifrování, která byla předmětem rozsáhlých akademickch kontrol za posledních 20 let. V současné době neexistuje žádný známý praktický útok, který by někomu neměl vědět, že by mohl číst data zašifrovaná pomocí AES.

Ve výchozím nastavení jsou klíče používané pro šifrování Azure Storage spravovány společností Microsoft. Existují rozsáhlé ochrany, které zajišťují, aby se zabránilo škodlivému přístupu k těmto klíčům. Uživatelé s konkrétními požadavky na šifrování ale můžou taky [poskytovat vlastní klíče úložiště](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) , které se spravují v Azure Key Vault. Tyto klíče můžete kdykoli odvolat, což by efektivně vykreslilo obsah účtu úložiště, který je nepřístupný.

Virtuální počítače používají šifrované úložiště, ale je možné poskytnout další vrstvu šifrování pomocí technologií, jako je BitLocker ve Windows nebo DM-crypt v systému Linux. Tyto technologie znamenají, že i v případě, že se image disku nevrátila z úložiště, zůstane v blízkosti nemožné ji přečíst.

### <a name="azure-sql"></a>Azure SQL

Databáze hostované v Azure SQL používají technologii nazvanou [transparentní šifrování dat (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) k zajištění, že data zůstanou zašifrovaná. Tato možnost je ve výchozím nastavení povolená u všech nově vytvořených databází SQL, ale musí být povolená ručně pro starší databáze. TDE provádí šifrování a dešifrování v reálném čase nejen pro databázi, ale také pro zálohy a protokoly transakcí.

Parametry šifrování jsou uloženy v `master` databázi a při spuštění jsou načteny do paměti pro zbývající operace. To znamená, že `master` databáze musí zůstat nezašifrovaná. Skutečný klíč spravuje Microsoft. Uživatelé s přesnými požadavky na zabezpečení však mohou poskytovat vlastní klíč v Key Vault podobným způsobem jako u Azure Storage. Key Vault poskytuje takové služby jako střídání a odvolávání klíčů.

"Transparentní" část protokolu TDS pochází ze skutečnosti, že nejsou k dispozici žádné změny klienta k používání šifrované databáze. I když tento přístup poskytuje dobré zabezpečení, je nevrácení hesla databáze dostatečné, aby mohli uživatelé data dešifrovat. Existuje další postup, který šifruje jednotlivé sloupce nebo tabulky v databázi. [Always Encrypted](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) zajistí, že šifrovaná data se v rámci databáze zobrazí v prostém textu.

Nastavení této úrovně šifrování vyžaduje spuštění prostřednictvím průvodce v SQL Server Management Studio k výběru řazení šifrování a místa, kde v Key Vault ukládat přidružené klíče.

![Obrázek 9-6 Výběr sloupců v tabulce k šifrování pomocí Always Encrypted](./media/always-encrypted.png)

**Obrázek 9-6**. Výběr sloupců v tabulce k šifrování pomocí Always Encrypted.

Klientské aplikace, které čtou informace z těchto šifrovaných sloupců, potřebují speciální příspěvky pro čtení šifrovaných dat. Připojovací řetězce je potřeba aktualizovat pomocí `Column Encryption Setting=Enabled` a přihlašovací údaje klienta musí být načtené z Key Vault. Klient SQL Server musí být pak s šifrovacími klíči sloupce. Až to uděláte, zbývající akce použijí standardní rozhraní pro klienta SQL. To znamená, že nástroje jako Dapperem a Entity Framework, které jsou postavené na klientech SQL, budou i nadále fungovat beze změn. Always Encrypted nemusí být k dispozici pro všechny ovladače SQL Server v každém jazyce.

Kombinace TDE a Always Encrypted, které je možné použít s klíči specifickými pro klienta, zajišťuje, aby se podporovaly i nejpřesnější požadavky na šifrování.

### <a name="cosmos-db"></a>Databáze Cosmos

Cosmos DB je nejnovější databáze poskytovaná Microsoftem v Azure. Bylo postaveno od základů k zabezpečení a šifrování. Šifrování AES-256bit je standard pro všechny databáze Cosmos DB a nedá se zakázat. V kombinaci s požadavkem TLS 1,2 pro komunikaci je celé řešení úložiště šifrované.

![Obrázek 9-7 tok šifrování dat v rámci Cosmos DB](./media/cosmos-encryption.png)

**Obrázek 9-7**. Tok šifrování dat v rámci Cosmos DB.

I když Cosmos DB neposkytuje pro poskytování šifrovacích klíčů zákazníka, má tým významnou práci provedenou týmem k tomu, aby se zajistilo, že zůstane kompatibilní se standardem PCI-DSS bez tohoto. Cosmos DB také nepodporuje žádné řazení jednoduchého šifrování sloupců podobně jako Always Encrypted Azure SQL.

## <a name="keeping-secure"></a>Zachování zabezpečení

Azure obsahuje všechny nástroje, které jsou nezbytné pro vydání vysoce zabezpečeného produktu. Řetěz je však pouze tak silný jako jeho slabý odkaz. Pokud se aplikace nasazené na Azure nevyvinuly se správnými bezpečnostními místo a dobrými audity zabezpečení, stane se slabým odkazem v řetězu. Existuje mnoho skvělých statických nástrojů pro analýzu, šifrovacích knihoven a postupů zabezpečení, které je možné použít k zajištění toho, aby byl software nainstalovaný v Azure jako takový jako samotný Azure sám zabezpečený. Mezi příklady patří [statické nástroje pro analýzu](https://www.whitesourcesoftware.com/), [knihovny šifrování](https://www.libressl.org/)a [postupy zabezpečení](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/).

>[!div class="step-by-step"]
>[Předchozí](security.md) 
> [Další](devops.md)
