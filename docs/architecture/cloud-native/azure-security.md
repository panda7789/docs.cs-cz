---
title: Zabezpečení Azure pro nativní aplikace nanesené v cloudu
description: Navrhování cloudových nativních aplikací .NET pro Azure | Nativní aplikace Azure Security for Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 13b5ad7a883a83014913fa0a6a020610c28c524f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989139"
---
# <a name="azure-security-for-cloud-native-apps"></a>Zabezpečení Azure pro nativní aplikace nanesené v cloudu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace nativní pro cloud může být jednodušší a obtížněji zabezpečené než tradiční aplikace. Na druhou stranu, musíte zabezpečit více menších aplikací a věnovat více energie na vybudování bezpečnostní infrastruktury. Různorodá povaha programovacích jazyků a stylů ve většině nasazení služeb také znamená, že je třeba věnovat větší pozornost bulletinům zabezpečení od mnoha různých poskytovatelů.

Na druhou stranu menší služby, z nichž každá má vlastní úložiště dat, omezují rozsah útoku. Pokud útočník zkompromituje jeden systém, je pravděpodobně obtížnější pro útočníka provést přechod do jiného systému, než je v monolitické aplikaci. Hranice procesu jsou silné hranice. Také pokud dojde k úniku zálohy databáze, je poškození omezenější, protože tato databáze obsahuje pouze podmnožinu dat a je nepravděpodobné, že by obsahovala osobní údaje.

## <a name="threat-modeling"></a>Modelování hrozeb

Bez ohledu na to, zda výhody převažují nad nevýhodami aplikací nativních pro cloud, je třeba dodržovat stejné holistické zabezpečení. Bezpečnost a bezpečné myšlení musí být součástí každého kroku vývoje a provozu příběhu. Při plánování aplikace klást otázky, jako jsou:

- Jaký by byl dopad ztráty těchto dat?
- Jak můžeme omezit škody způsobené vstřikováním špatných dat do této služby?
- Kdo by měl mít přístup k těmto údajům?
- Existují auditní politiky týkající se procesu vývoje a vydávání?

Všechny tyto otázky jsou součástí procesu zvaného [modelování hrozeb](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool). Tento proces se snaží odpovědět na otázku, jaké hrozby existují pro systém, jak pravděpodobné jsou hrozby a potenciální škody z nich.

Jakmile je sestaven seznam hrozeb, musíte se rozhodnout, zda stojí za zmírnění. Někdy je hrozba tak nepravděpodobné a drahé plánovat, že to nestojí za to utrácet energii na to. Například některé objektactor na úrovni stavu může vstřikovat změny do návrhu procesu, který je používán miliony zařízení. Nyní namísto spuštění určité části kódu v [ringu 3](https://en.wikipedia.org/wiki/Protection_ring), tento kód je spuštěn v Ring 0. To umožňuje zneužití, které může obejít hypervisor a spustit kód útoku na holé kovové počítače, což umožňuje útoky na všechny virtuální počítače, které jsou spuštěny na tomto hardwaru.

Změněné procesory je obtížné detekovat bez mikroskopu a pokročilé znalosti o křemíkové konstrukci tohoto procesoru. Tento scénář je nepravděpodobné, že by se stalo a nákladné zmírnit, takže pravděpodobně žádný model hrozby by doporučil stavební zneužití ochrany pro něj.

Pravděpodobnější hrozby, jako jsou nefunkční `Id` ovládací prvky přístupu `Id=2` `Id=3` umožňující zvýšení útoků (nahrazení v adrese URL) nebo vkládání SQL, jsou atraktivnější pro vytváření ochrany proti. Zmírnění těchto hrozeb je docela rozumné vybudovat a zabránit trapným bezpečnostním dírám, které pošpiní pověst společnosti.

## <a name="principle-of-least-privilege"></a>Zásada nejnižšího privilegia

Jedním ze zakládajících nápadů v oblasti počítačové bezpečnosti je Princip nejmenšího privilegia (POLP). Je to vlastně základní myšlenka ve většině jakékoli formy zabezpečení, ať už digitální nebo fyzické. Stručně řečeno, princip je, že každý uživatel nebo proces by měl mít nejmenší počet práv možné provést svůj úkol.

Jako příklad si představte pokladníky v bance: přístup k trezoru je neobvyklá aktivita. Takže průměrný pokladník nemůže otevřít trezor sám. Chcete-li získat přístup, je třeba eskalovat své žádosti prostřednictvím správce banky, který provádí další bezpečnostní kontroly.

V počítačovém systému jsou fantastickým příkladem práva uživatele, který se připojuje k databázi. V mnoha případech existuje jeden uživatelský účet, který slouží k sestavení struktury databáze a spuštění aplikace. S výjimkou v extrémních případech účet spuštěné aplikace nepotřebuje možnost aktualizovat informace o schématu. Mělo by existovat několik účtů, které poskytují různé úrovně oprávnění. Aplikace by měla používat pouze úroveň oprávnění, která uděluje přístup pro čtení a zápis k datům v tabulkách. Tento druh ochrany by eliminoval útoky, jejichž cílem bylo vynechat databázové tabulky nebo zavést škodlivé aktivační události.

Téměř každá část vytváření aplikace nativní pro cloud může mít prospěch z zapamatování principu nejnižší oprávnění. Můžete najít ve hře při nastavování brány firewall, skupiny zabezpečení sítě, role a obory v řízení přístupu na základě rolí (RBAC).

## <a name="penetration-testing"></a>Testování průniku

Jak se aplikace stávají složitějšími, počet útočných vektorů se zvyšuje alarmujícím tempem. Modelování hrozeb je chybné v tom, že má tendenci být proveden stejnými lidmi, kteří budují systém. Stejně jako mnoho vývojářů má potíže s představou uživatelských interakcí a poté vytváří nepoužitelná uživatelská rozhraní, většina vývojářů má potíže vidět každý vektor útoku. Je také možné, že vývojáři, kteří budují systém, nejsou dobře zběhlí v metodách útoku a postrádají něco zásadního.

Penetrační testování nebo "testování pera" zahrnuje uvedení externích aktérů, aby se pokusili zaútočit na systém. Tito útočníci mohou být externí poradenská společnost nebo jiní vývojáři s dobrými znalostmi zabezpečení z jiné části podnikání. Dostali volnou ruku, aby se pokusili rozvrátit systém. Často najdou rozsáhlé bezpečnostní díry, které je třeba opravit. Někdy útok vektor bude něco naprosto nečekaného, jako je zneužití phishingový útok proti generálnímu řediteli.

Samotný Azure neustále prochází útoky od [týmu hackerů uvnitř Microsoftu](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/). V průběhu let, oni byli první najít desítky potenciálně katastrofických útočných vektorů, jejich uzavření před tím, než mohou být využívány externě. Čím lákavější cíl, tím je pravděpodobnější, že se ho věční aktéři pokusí zneužít a na světě je několik lákavějších cílů než Azure.

## <a name="monitoring"></a>Monitorování

Pokud se útočník pokusí proniknout do aplikace, mělo by na ni být nějaké upozornění. Často útoky mohou být spatřeny kontrolou protokoly ze služeb. Útoky zanechávají výmluvné znaky, které mohou být spatřeny dříve, než uspějí. Například útočník, který se pokouší uhodnout heslo, provede mnoho požadavků na přihlašovací systém. Sledování kolem přihlašovacího systému může detekovat podivné vzory, které jsou mimo linii s typickým vzorem přístupu. Toto monitorování může být přeměněno na výstrahu, která může zase upozornit provozní osobu, aby aktivovala nějaký druh protiopatření. Vysoce vyspělý monitorovací systém může dokonce provést akci na základě těchto odchylek proaktivně přidávat pravidla pro blokování požadavků nebo odezvy omezení.

## <a name="securing-the-build"></a>Zabezpečení sestavení

Jedno místo, kde je zabezpečení často přehlíženo, je kolem procesu sestavení. Sestavení by mělo nejen spustit kontroly zabezpečení, jako je například hledání nezabezpečeného kódu nebo přihlašovacích údajů se změnami, ale samotné sestavení by mělo být zabezpečené. Pokud je server sestavení ohrožen, poskytuje fantastický vektor pro zavedení libovolného kódu do produktu.

Představte si, že útočník hledá ukrást hesla lidí, kteří se přihlašují do webové aplikace. Mohou zavést krok sestavení, který upravuje kód rezervováného tak, aby odrážel jakýkoli požadavek na přihlášení na jiný server. Další kód prochází sestavení, je tiše aktualizován. Prohledávání zranitelnosti zdrojového kódu nebude zachytit to, jak to běží před sestavením. Stejně tak nikdo nechytí v revizi kódu, protože kroky sestavení žijí na serveru sestavení. Vykořisťovaný kód půjde do výroby, kde může sklízet hesla. Pravděpodobně neexistuje žádný protokol auditu změn procesu sestavení nebo alespoň nikdo sledování auditu.

Toto je dokonalý příklad zdánlivě nízké hodnoty cíle, který lze použít k prolomení do systému. Jakmile útočník poruší obvod systému, může začít pracovat na hledání způsobů, jak zvýšit svá oprávnění do té míry, že mohou způsobit skutečnou škodu kdekoli se jim líbí.

## <a name="building-secure-code"></a>Vytváření zabezpečeného kódu

Rozhraní .NET Framework je již poměrně zabezpečené rozhraní. Zabraňuje některé úskalí nespravovaného kódu, jako je například chůze z konců polí. Aktivně se pracuje na opravě bezpečnostních děr při jejich zjištění. K dispozici je i [bug bounty program,](https://www.microsoft.com/msrc/bounty) který platí výzkumníkům najít problémy v rámci a nahlásit je místo jejich využití.

Existuje mnoho způsobů, jak vytvořit kód .NET bezpečnější. Následující pokyny, jako je [například bezpečné kódování pokyny pro](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines) článek .NET je rozumný krok k zajištění, že kód je bezpečný od základu. [OWASP top 10](https://owasp.org/www-project-top-ten/) je další neocenitelný průvodce pro vytvoření zabezpečeného kódu.

Proces sestavení je dobrým místem pro umístění nástrojů pro skenování pro detekci problémů ve zdrojovém kódu před jejich vstupem do produkčního prostředí. Většina každého projektu má závislosti na některých jiných balíčcích. Nástroj, který může hledat zastaralé balíčky, zachytí problémy v nočním sestavení. I při vytváření imitací Dockeru je užitečné zkontrolovat a ujistit se, že základní bitová kopie nemá známé chyby zabezpečení. Další věc, kterou je třeba zkontrolovat, je, že nikdo omylem zkontroloval přihlašovací údaje.

## <a name="built-in-security"></a>Integrované zabezpečení

Azure je navržený tak, aby vyvažuje použitelnost a zabezpečení pro většinu uživatelů. Různí uživatelé budou mít různé požadavky na zabezpečení, takže je třeba doladit svůj přístup k zabezpečení cloudu. Společnost Microsoft zveřejňuje velké množství informací o zabezpečení v [Centru zabezpečení](https://azure.microsoft.com/support/trust-center/). Tento zdroj by měl být první zastávkou pro profesionály, kteří mají zájem pochopit, jak fungují integrované technologie zmírňování útoků.

V rámci portálu Azure je [Azure Advisor](https://azure.microsoft.com/services/advisor/) systém, který neustále skenuje prostředí a poskytuje doporučení. Některá z těchto doporučení jsou navržena tak, aby uživatelům ušetřila peníze, ale jiná jsou navržena tak, aby identifikovala potenciálně nezabezpečené konfigurace, jako je například otevření kontejneru úložiště pro svět a nechráněný virtuální sítí.

## <a name="azure-network-infrastructure"></a>Síťová infrastruktura Azure

V místním prostředí nasazení je velké množství energie věnováno na nastavování sítí. Nastavení směrovačů, přepínačů a takové je komplikovaná práce. Sítě umožňují určitým prostředkům mluvit s jinými prostředky a v některých případech zabránit přístupu. Častým síťovým pravidlem je omezit přístup k produkčnímu prostředí z vývojového prostředí na šanci, že se napůl vyvinutý kus kódu spustí nakřivo a odstraní pás dat.

Po vybalení má většina prostředků PaaS Azure pouze nejzákladnější a nejtolerantnější síťové nastavení. Například kdokoli na Internetu má přístup ke službě aplikace. Nové instance SQL Serveru se obvykle omezují, takže k nim nemají přístup externí strany, ale rozsahy IP adres používané samotným Azure jsou povoleny. Takže zatímco SQL server je chráněn před externími hrozbami, útočník potřebuje pouze nastavit předmostí Azure, odkud může spustit útoky proti všem instancím SQL v Azure.

Naštěstí většinu prostředků Azure můžete umístit do virtuální sítě Azure, která umožňuje jemnější odstupňované řízení přístupu. Podobně jako místní sítě vytvářejí privátní sítě, které jsou chráněné před širším světem, virtuální sítě jsou ostrovy privátních IP adres umístěných v síti Azure.

![Obrázek 10-1 Virtuální](./media/virtual-network.png)
síť na obrázku Azure**10-1**. Virtuální síť v Azure.

Stejným způsobem, že místní sítě mají bránu firewall, která řídí přístup k síti, můžete vytvořit podobnou bránu firewall na hranici virtuální sítě. Ve výchozím nastavení mohou všechny prostředky ve virtuální síti stále mluvit s Internetem. Jsou to pouze příchozí připojení, která vyžadují určitou formu explicitní výjimky brány firewall.

Po vytvoření sítě lze nastavit interní prostředky, jako jsou účty úložiště, tak, aby umožňovaly přístup pouze prostředkům, které jsou také ve virtuální síti. Tato brána firewall poskytuje další úroveň zabezpečení, pokud by klíče pro tento účet úložiště unikly, útočníci by se k němu nemohli připojit, aby zneužili uniklé klíče. To to je další příklad principu nejnižší houževnatosti.

Uzly v clusteru Azure Kubernetes se můžou účastnit virtuální sítě stejně jako ostatní prostředky, které jsou nativní pro Azure. Tato funkce se nazývá [Azure Container Networking Interface](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md). Ve skutečnosti přiděluje podsíť v rámci virtuální sítě, na které jsou přiděleny virtuální počítače a image kontejnerů.

Pokračování dolů cestu ilustrující princip nejmenší oprávnění, ne každý prostředek v rámci virtuální sítě musí mluvit s každým jiným zdrojem. Například v aplikaci, která poskytuje webové rozhraní API přes účet úložiště a databázi SQL, je nepravděpodobné, že databáze a účet úložiště potřebují mluvit mezi sebou. Jakékoli sdílení dat mezi nimi by projít webové aplikace. Skupina [zabezpečení sítě (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) by tedy mohla být použita k odepření provozu mezi těmito dvěma službami.

Zásada odepření komunikace mezi prostředky může být nepříjemné implementovat, zejména z pozadí používání Azure bez omezení provozu. V některých jiných cloudech je koncept skupin zabezpečení sítě mnohem rozšířenější. Například výchozí zásadou v AWS je, že prostředky nemohou komunikovat mezi sebou, dokud nejsou povoleny pravidly v souboru zabezpečení sítě. Zatímco pomalejší rozvíjet to, více omezující prostředí poskytuje bezpečnější výchozí. Použití správné DevOps postupy, zejména pomocí [Azure Resource Manager nebo Terraform](infrastructure-as-code.md) pro správu oprávnění můžete usnadnit řízení pravidel.

Virtuální sítě mohou být užitečné také při nastavování komunikace mezi místními a cloudovými prostředky. Virtuální privátní síť lze bez problémů připojit dvě sítě dohromady. To umožňuje spuštění virtuální sítě bez jakéhokoli druhu brány pro scénáře, kde jsou všichni uživatelé na místě. Existuje celá řada technologií, které lze použít k vytvoření této sítě. Nejjednodušší je použít [síť VPN typu site-to-site,](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) kterou lze vytvořit mezi mnoha směrovači a Azure. Provoz je šifrován a tunelován přes Internet za stejnou cenu za bajt jako jakýkoli jiný provoz. Pro scénáře, kde je žádoucí větší šířka pásma nebo větší zabezpečení, Azure nabízí službu nazvanou [Express Route,](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) která používá privátní okruh mezi místní sítí a Azure. Je to nákladnější a obtížněji vytvořit, ale také bezpečnější.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Řízení přístupu na základě rolí pro omezení přístupu k prostředkům Azure

RBAC je systém, který poskytuje identitu aplikacím spuštěným v Azure. Aplikace mohou přistupovat k prostředkům pomocí této identity namísto nebo kromě použití klíčů nebo hesel.

## <a name="security-principals"></a>Objekty zabezpečení

První součást v RBAC je objekt zabezpečení. Zaregistrovaný objekt zabezpečení může být uživatel, skupina, instanční objekt nebo spravovaná identita.

![Obrázek 10-2 Různé typy](./media/rbac-security-principal.png)
zmocničů zabezpečení**Obrázek 10-2**. Různé typy objektů zabezpečení.

- Uživatel – každý uživatel, který má účet ve službě Azure Active Directory, je uživatel.
- Skupina – kolekce uživatelů ze služby Azure Active Directory. Jako člen skupiny, uživatel převezme role této skupiny kromě jejich vlastní.
- Instanční objekt - Identita zabezpečení, pod kterou jsou spuštěny služby nebo aplikace.
- Spravovaná identita – identita Azure Active Directory spravovaná Azure. Spravované identity se obvykle používají při vývoji cloudových aplikací, které spravují přihlašovací údaje pro ověřování služeb Azure.

Objekt zabezpečení lze použít pro většinu libovolných prostředků. To znamená, že je možné přiřadit objekt zabezpečení ke kontejneru spuštěného v rámci Azure Kubernetes, což mu umožňuje přístup k tajným kódům uloženým v trezoru klíčů. Funkce Azure může mít oprávnění umožňující mu mluvit s instancí služby Active Directory k ověření JWT pro volajícího uživatele. Jakmile jsou služby povoleny s objektem zabezpečení služby, jejich oprávnění lze spravovat granulovaně pomocí rolí a oborů.

## <a name="roles"></a>Role

Bezpečnostní princip může převzít mnoho rolí nebo pomocí krejčovské analogie nosit mnoho klobouků. Každá role definuje řadu oprávnění, jako je například "Čtení zpráv z koncového bodu Služby Azure Service Bus". Efektivní sada oprávnění zaregistrovaný objekt zabezpečení je kombinací všech oprávnění přiřazených ke všem rolím, které má zaregistrovaný objekt zabezpečení. Azure má velký počet předdefinovaných rolí a uživatelé můžou definovat své vlastní role.

![Obrázek 10-3 Definice](./media/rbac-role-definition.png)
rolí RBAC**Obrázek 10-3**. Definice rolí RBAC.

Integrované do Azure jsou také řada rolí na vysoké úrovni, jako je vlastník, přispěvatel, čtenář a správce uživatelských účtů. S rolí Vlastník může zaregistrovaný objekt zabezpečení přistupovat ke všem prostředkům a přiřazovat oprávnění ostatním. Přispěvatel má stejnou úroveň přístupu ke všem prostředkům, ale nemůže přiřadit oprávnění. Čtenář může zobrazit jenom existující prostředky Azure a správce uživatelského účtu může spravovat přístup k prostředkům Azure.

Podrobnější předdefinované role, jako je [například přispěvatel zóny DNS,](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) mají práva omezená na jednu službu. Objekty zabezpečení mohou převzít libovolný počet rolí.

## <a name="scopes"></a>Obory

Role lze použít pro omezenou sadu prostředků v rámci Azure. Například použití oboru na předchozí příklad čtení z fronty služby Service Bus, můžete zúžit oprávnění na `blah.servicebus.windows.net/queue1`jednu frontu: "Čtení zpráv z koncového bodu Služby Azure Service Bus "

Obor může být stejně úzký jako jeden prostředek nebo jej lze použít pro celou skupinu prostředků, předplatné nebo dokonce skupinu pro správu.

Při testování, pokud má objekt zabezpečení určité oprávnění, je zohledněna kombinace role a oboru. Tato kombinace poskytuje výkonný autorizační mechanismus.

## <a name="deny"></a>Odepřít

Dříve byla povolena pouze pravidla "povolit" pro RBAC. Toto chování zkomplikovalo sestavení některých oborů. Například povolení primárnípřístup k zabezpečení ke všem účtům úložiště s výjimkou jednoho vyžaduje udělení explicitní oprávnění k potenciálně nekonečný seznam účtů úložiště. Při každém vytvoření nového účtu úložiště by musel být přidán do tohoto seznamu účtů. To to přidalo režii managementu, která rozhodně nebyla žádoucí.

Odepřít pravidla mají přednost před povolit pravidla. Nyní představuje stejný "povolit všechny kromě jednoho" rozsah by mohly být reprezentovány jako dvě pravidla "povolit všechny" a "odepřít tento konkrétní jeden". Odepřít pravidla nejen usnadnit správu, ale umožňují prostředky, které jsou extra bezpečné tím, že odepře přístup všem.

## <a name="checking-access"></a>Kontrola přístupu

Jak si dokážete představit, s velkým počtem rolí a oborů může zjišťovat efektivní oprávnění instančního objektu poměrně obtížné. Hromadí popřít pravidla na vrcholu, že slouží pouze ke zvýšení složitosti. Naštěstí existuje kalkulačka oprávnění, která může zobrazit platná oprávnění pro všechny instanční objekt. Obvykle se nachází pod kartou IAM na portálu, jak je znázorněno na obrázku 10-3.

![Obrázek 10-4 Kalkulačka](./media/check-rbac.png)
oprávnění pro aplikační**službu Obrázek 10-4**. Kalkulačka oprávnění pro službu aplikace.

## <a name="securing-secrets"></a>Zabezpečení tajemství

Hesla a certifikáty jsou běžným vektorem útoku pro útočníky. Password-cracking hardware může udělat útok hrubou silou a pokusit se uhodnout miliardy hesel za sekundu. Proto je důležité, aby hesla, která se používají pro přístup k prostředkům, byla silná, s velkým množstvím znaků. Tato hesla jsou přesně ten druh hesel, které jsou téměř nemožné si zapamatovat. Naštěstí hesla v Azure ve skutečnosti nemusí být známy žádné lidské.

Mnoho odborníků na zabezpečení [naznačuje,](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) že nejlepším přístupem je použití správce hesel k uchování vlastních hesel. I když centralizuje vaše hesla na jednom místě, umožňuje také používat velmi složitá hesla a zajistit, aby byla jedinečná pro každý účet. Stejný systém existuje v rámci Azure: centrální úložiště tajných kódů.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault poskytuje centralizované umístění pro ukládání hesel pro věci, jako jsou databáze, klíče rozhraní API a certifikáty. Jakmile je tajný klíč vložen do trezoru, už se nikdy nezobrazí a příkazy k jeho extrakci a zobrazení jsou záměrně komplikované. Informace v trezoru jsou chráněny pomocí softwarového šifrování nebo ověřených modulů hardwarového zabezpečení FIPS 140-2 Level 2.

Přístup k trezoru klíčů je poskytován prostřednictvím paměti RBAC, což znamená, že k informacím v úložišti nemá přístup pouze každý uživatel. Řekněme, že webová aplikace chce získat přístup k připojovacímu řetězci databáze uloženému v úložišti klíčů Azure. Chcete-li získat přístup, aplikace je třeba spustit pomocí instančního objektu. Pod touto převzatou rolí si mohou přečíst tajemství ze sejfu. Existuje řada různých nastavení zabezpečení, které mohou dále omezit přístup, který má aplikace k trezoru, takže nemůže aktualizovat tajné klíče, ale pouze je číst.

Přístup do trezoru klíčů lze sledovat, aby bylo zajištěno, že k trezoru přistupují pouze očekávané aplikace. Protokoly lze integrovat zpět do Azure Monitor, odemknutí možnost nastavit výstrahy, když dojde k neočekávaným podmínkám.

## <a name="kubernetes"></a>Kubernetes

V Kubernetes je podobná služba pro udržování malých tajných informací. Kubernetes Secrets lze nastavit `kubectl` pomocí typického spustitelného souboru.

Vytvoření tajného klíče je stejně jednoduché jako nalezení base64 verze hodnot, které mají být uloženy:

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Pak jej přidáte do `secret.yml` souboru tajných klíčů s názvem například, který vypadá podobně jako v následujícím příkladu:

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

Nakonec lze tento soubor načíst do Kubernetes spuštěním následujícího příkazu:

```console
kubectl apply -f ./secret.yaml
```

Tyto tajné klíče pak lze připojit do svazků nebo vystaveny procesu kontejneru prostřednictvím proměnných prostředí. [Dvanáctifaktorový přístup k vytváření aplikací](https://12factor.net/) navrhuje použití nejnižšího společného jmenovatele k přenosu nastavení do aplikace. Proměnné prostředí jsou nejnižším společným jmenovatelem, protože jsou podporovány bez ohledu na operační systém nebo aplikaci.

Alternativou k použití integrované tajné kódy Kubernetes je přístup k tajným kódům v azure key vault z Kubernetes. Nejjednodušší způsob, jak to provést, je přiřadit roli RBAC kontejneru, který hledá načíst tajné klíče. Aplikace pak můžete použít Azure Key Vault API pro přístup k tajným klíčům. Tento přístup však vyžaduje změny kódu a neřídí se vzorem použití proměnných prostředí. Místo toho je možné vložit hodnoty do kontejneru pomocí [vstřikovače trezoru klíčů Azure](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354). Tento přístup je ve skutečnosti bezpečnější než použití tajných kódů Kubernetes přímo, protože k nim mohou přistupovat uživatelé v clusteru.

## <a name="encryption-in-transit-and-at-rest"></a>Šifrování v tranzitu a v klidovém stavu

Udržování dat v bezpečí je důležité, ať už je to na disku nebo tranzit mezi různými službami. Nejúčinnějším způsobem, jak zabránit úniku dat, je zašifrovat je do formátu, který ostatní nemohou snadno číst. Azure podporuje širokou škálu možností šifrování.

### <a name="in-transit"></a>V tranzitu

Existuje několik způsobů, jak šifrovat provoz v síti v Azure. Přístup ke službám Azure se obvykle provádí přes připojení, které používají zabezpečení transportní vrstvy (TLS). Například všechna připojení k azure api vyžadují připojení TLS. Stejně tak připojení ke koncovým bodům v úložišti Azure může být omezena na práci pouze přes šifrovaná připojení TLS.

TLS je složitý protokol a jednoduše vědět, že připojení používá TLS není dostatečná k zajištění zabezpečení. Například TLS 1.0 je chronicky nejistá a TLS 1.1 není o moc lepší. Dokonce i ve verzích TLS existují různá nastavení, která mohou usnadnit dešifrování připojení. Nejlepší postup je zkontrolovat a zjistit, zda připojení k serveru používá aktuální a dobře nakonfigurované protokoly.

Tuto kontrolu lze provést externí službou, jako je například Test serveru SSL laboratoře SSL. Spuštění testu proti typickému koncovému bodu Azure, v tomto případě koncovému bodu služby Service Bus, poskytuje téměř dokonalé skóre A.

Dokonce i služby, jako jsou databáze Azure SQL, používají šifrování TLS, aby data ukryla. Zajímavá část o šifrování dat při přenosu pomocí TLS je, že není možné, a to i pro Microsoft, naslouchat na spojení mezi počítači se systémem TLS. To by mělo poskytnout pohodlí pro dotčené společnosti, že jejich data mohou být ohrožena vlastní microsoft nebo dokonce státní aktér s více prostředky než standardní útočník.

![Obrázek 10-5 SSL testovacích prostředí sestavy zobrazující skóre A pro koncový bod service sběrnice. ](./media/ssl-report.png)
 **Obrázek 10-5**. Sestava testovacích prostředí SSL zobrazující skóre A pro koncový bod služby Service Bus.

I když tato úroveň šifrování nebude dostatečná po celou dobu, měla by vzbuzovat jistotu, že připojení Azure TLS jsou poměrně bezpečná. Azure bude pokračovat ve vývoji svých standardů zabezpečení s tím, jak se šifrování zlepšuje. Je hezké vědět, že je tu někdo, kdo sleduje bezpečnostní standardy a aktualizuje Azure, jak se zlepšují.

### <a name="at-rest"></a>V klidu

V každé aplikaci existuje několik míst, kde data spočívají na disku. Samotný kód aplikace je načten z některého mechanismu úložiště. Většina aplikací také použít nějaký druh databáze, jako je NAPŘÍKLAD SQL Server, Cosmos DB nebo dokonce úžasně nákladově efektivní table storage. Všechny tyto databáze používají silně šifrované úložiště, aby bylo zajištěno, že nikdo jiný než aplikace s příslušnými oprávněními nemůže číst vaše data. Ani provozovatelé systému nemohou číst data, která byla zašifrována. Zákazníci si tak mohou být jisti, že jejich tajné informace zůstávají tajné.

### <a name="storage"></a>Storage

Základem velké části Azure je modul Azure Storage. Disky virtuálních počítačů se připojou k Azure Storage. Služby Azure Kubernetes se spouštějí na virtuálních počítačích, které jsou samy o sobě hostované ve službě Azure Storage. Dokonce i technologie bez serveru, jako jsou Aplikace Azure Functions a Azure Container Instances, vyjdou disk, který je součástí Azure Storage.

Pokud je Azure Storage dobře šifrované, pak poskytuje základ pro většinu všeho ostatního, co má být také šifrováno. Azure Storage [je šifrovaný](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) s [FIPS 140-2](https://en.wikipedia.org/wiki/FIPS_140) kompatibilní [256bitové AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard). Jedná se o dobře pokládanou šifrovací technologii, která byla v posledních 20 letech předmětem rozsáhlé akademické kontroly. V současné době neexistuje žádný známý praktický útok, který by umožnil někomu bez znalosti klíče číst data šifrovaná AES.

Ve výchozím nastavení jsou klíče používané pro šifrování Azure Storage spravované společností Microsoft. Existují rozsáhlé ochrany, které zajišťují, aby se zabránilo škodlivému přístupu k těmto klíčům. Uživatelé s konkrétní požadavky na šifrování však můžete také [poskytnout své vlastní klíče úložiště,](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) které jsou spravované v trezoru klíčů Azure. Tyto klíče lze kdykoli odvolat, což by efektivně znepřístupnilo obsah účtu úložiště, který by je používal.

Virtuální počítače používají šifrované úložiště, ale je možné poskytnout další vrstvu šifrování pomocí technologií, jako je Nástroj BitLocker v systému Windows nebo DM-Crypt na Linuxu. Tyto technologie znamenají, že i kdyby obraz disku unikl z úložiště, bylo by téměř nemožné ji přečíst.

### <a name="azure-sql"></a>Azure SQL

Databáze hostované v Azure SQL používají technologii nazvanou [Transparentní šifrování dat (TDE),](/sql/relational-databases/security/encryption/transparent-data-encryption) která zajišťuje, že data zůstanou šifrovaná. Je ve výchozím nastavení povolena ve všech nově vytvořených databázích SQL, ale musí být povolena ručně pro starší databáze. TDE provádí šifrování a dešifrování v reálném čase nejen databáze, ale také zálohy a transakční protokoly.

Šifrovací parametry `master` jsou uloženy v databázi a při spuštění jsou čteny do paměti pro zbývající operace. To znamená, `master` že databáze musí zůstat nezašifrované. Skutečný klíč spravuje společnost Microsoft. Uživatelé s náročnými požadavky na zabezpečení však může poskytnout svůj vlastní klíč v trezoru klíčů v podstatě stejným způsobem, jako je tomu u Azure Storage. Trezor klíčů poskytuje takové služby, jako je střídání klíčů a odvolání.

"Transparentní" část TDS pochází ze skutečnosti, že nejsou potřeba změny klienta k použití šifrované databáze. Zatímco tento přístup poskytuje dobré zabezpečení, únik hesla databáze je dost pro uživatele, aby mohli dešifrovat data. Existuje jiný přístup, který šifruje jednotlivé sloupce nebo tabulky v databázi. [Vždy šifrované](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) zajišťuje, že v žádném okamžiku se šifrovaná data nezobrazí ve formátu prostého textu uvnitř databáze.

Nastavení této vrstvy šifrování vyžaduje spuštění průvodce v aplikaci SQL Server Management Studio pro výběr druhu šifrování a kde v trezoru klíčů uložit přidružené klíče.

![Obrázek 10-6 Výběr sloupců v tabulce, které](./media/always-encrypted.png)
mají být šifrovány pomocí vždy šifrovaného**obrázku 10-6**. Výběr sloupců v tabulce, které mají být šifrovány pomocí vždy šifrované.

Klientské aplikace, které čtou informace z těchto šifrovaných sloupců, musí pro čtení šifrovaných dat provádět zvláštní přenosy. Připojovací řetězce je `Column Encryption Setting=Enabled` třeba aktualizovat a pověření klienta musí být načteny z trezoru klíčů. Klient serveru SQL Server pak musí být vybaven šifrovacími klíči sloupce. Jakmile je to hotovo, zbývající akce použít standardní rozhraní pro SQL Client. To znamená, že nástroje jako Dapper a Entity Framework, které jsou postaveny na sql client, budou i nadále fungovat beze změn. Vždy šifrované ještě nemusí být k dispozici pro každý ovladač serveru SQL Server v každém jazyce.

Kombinace TDE a vždy šifrované, které mohou být použity s klíči specifickými pro klienta, zajišťuje, že jsou podporovány i ty nejnáročnější požadavky na šifrování.

### <a name="cosmos-db"></a>Databáze Cosmos

Cosmos DB je nejnovější databáze poskytovaná Microsoftem v Azure. Byl postaven od základů s ohledem na bezpečnost a kryptografii. Šifrování AES-256bit je standardní pro všechny databáze Cosmos DB a nelze je zakázat. Ve spojení s požadavkem TLS 1.2 na komunikaci je celé úložné řešení šifrováno.

![Obrázek 10-7 Tok šifrování dat](./media/cosmos-encryption.png)
v rámci Cosmos DB**Obrázek 10-7**. Tok šifrování dat v rámci Cosmos DB.

Zatímco Cosmos DB neposkytuje pro poskytování šifrovacích klíčů zákazníků, došlo k významné práci provedené týmem, aby zajistily, že zůstane kompatibilní PCI-DSS bez toho. Cosmos DB také nepodporuje žádný druh šifrování jednoho sloupce podobné Azure SQL je vždy šifrované dosud.

## <a name="keeping-secure"></a>Zajištění bezpečnosti

Azure má všechny nástroje potřebné k uvolnění vysoce zabezpečeného produktu. Řetěz je však jen tak silný jako jeho nejslabší článek. Pokud aplikace nasazené nad Azure nejsou vyvinuté s řádným nastavením zabezpečení a dobrými audity zabezpečení, stanou se slabým článkem v řetězci. Existuje mnoho skvělých nástrojů pro statickou analýzu, šifrovacích knihoven a postupů zabezpečení, které lze použít k zajištění toho, aby byl software nainstalovaný v Azure stejně zabezpečený jako samotný Azure. Mezi příklady patří [nástroje statické analýzy](https://www.whitesourcesoftware.com/), [šifrovací knihovny](https://www.libressl.org/)a [postupy zabezpečení](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/).

>[!div class="step-by-step"]
>[Předchozí](security.md)
>[další](devops.md)
