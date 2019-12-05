---
title: Základní koncepty služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 360479a2ba17c4542d61a737856d23992296e276
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802309"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Základní koncepty služby Windows Communication Foundation

Tento dokument poskytuje podrobný pohled na architekturu Windows Communication Foundation (WCF). Je určena k vyjasnění klíčových konceptů a způsobu jejich vzájemného přizpůsobení. Kurz týkající se vytvoření nejjednodušší verze služby WCF a klienta najdete v tématu [Začínáme kurzu](getting-started-tutorial.md). Další informace o programování WCF najdete v tématu [Základní programování WCF](basic-wcf-programming.md).

## <a name="wcf-fundamentals"></a>Základy WCF

WCF je modul runtime a sada rozhraní API pro vytváření systémů, které odesílají zprávy mezi službami a klienty. Stejná infrastruktura a rozhraní API se používají k vytváření aplikací, které komunikují s jinými aplikacemi ve stejném počítačovém systému nebo v systému, který se nachází v jiné společnosti a je k němu přistup přes Internet.

### <a name="messaging-and-endpoints"></a>Zasílání zpráv a koncových bodů

Služba WCF je založena na pojmu komunikace založené na zprávách a cokoli, co je možné modelovat jako zprávu (například požadavek HTTP nebo zpráva služby Řízení front zpráv (označované také jako MSMQ)), mohou být reprezentovány jednotným způsobem v programovacím modelu. To umožňuje sjednocení rozhraní API napříč různými mechanismy přenosu.

Model rozlišuje mezi _klienty_, což jsou aplikace, které iniciují komunikaci, a _služby_, které jsou aplikace, které čekají na komunikaci klientů a reagují na tuto komunikaci. Jedna aplikace může fungovat jako klient i služba. Příklady najdete v tématu [duplexní služby](./feature-details/duplex-services.md) a [sítě peer-to-peer](./feature-details/peer-to-peer-networking.md).

Mezi koncovými body se odesílají zprávy. _Koncové body_ jsou místa, kde jsou odesílány nebo přijímány zprávy (nebo obojí), a definují všechny informace požadované pro výměnu zpráv. Služba zveřejňuje jeden nebo více koncových bodů aplikace (stejně jako nula nebo více koncových bodů infrastruktury) a klient vygeneruje koncový bod, který je kompatibilní s jedním z koncových bodů služby.

_Koncový bod_ popisuje standardní způsob, jakým se mají odesílat zprávy, jak by se měly Odeslat a jaké by měly zprávy vypadat jako. Služba může tyto informace vystavit jako metadata, která klienti můžou zpracovat, aby vygenerovala příslušné klienty WCF a komunikační _zásobníky_.

### <a name="communication-protocols"></a>Komunikační protokoly

Jedním z vyžadovaných prvků komunikačního zásobníku je _Transportní protokol_. Zprávy můžete odesílat přes intranety a Internet pomocí běžných přenosů, jako je HTTP a TCP. K dispozici jsou další přenosy, které podporují komunikaci s aplikacemi služby Řízení front zpráv a uzly na síti peer-to-peer. Pomocí integrovaných rozšiřovacích bodů služby WCF je možné přidat další transportní mechanismy.

Dalším vyžadovaným prvkem v komunikačním zásobníku je kódování, které určuje, jak se daná zpráva naformátuje. WCF poskytuje následující kódování:

- Kódování textu, interoperabilní kódování.

- Kódování nástroje pro optimalizaci přenosu zpráv (MTOM), což je interoperabilní způsob efektivního posílání nestrukturovaných binárních dat do a ze služby.

- Binární kódování pro efektivní přenos

Další mechanismy kódování (například kódování komprese) lze přidat pomocí integrovaných rozšiřovacích bodů služby WCF.

### <a name="message-patterns"></a>Vzory zpráv

Služba WCF podporuje několik vzorů zasílání zpráv, včetně požadavků a odpovědí, jednosměrné a duplexní komunikace. Různá přenosová podpora podporuje různé vzory zasílání zpráv, takže mají vliv na typy interakcí, které podporují. Rozhraní API WCF a modul runtime vám také pomůžou bezpečně a spolehlivě odesílat zprávy.

## <a name="wcf-terms"></a>Výrazy WCF

K dalším konceptům a pojmům, které se používají v dokumentaci WCF, patří následující:

**Zpráva**  
 Samostatně obsažená jednotka dat, která se může skládat z několika částí, včetně těla a záhlaví.

**Service**  
 Konstrukce, která zveřejňuje jeden nebo více koncových bodů s každým koncovým bodem, který zveřejňuje jednu nebo více operací služby.

**Endpoint**  
 Konstrukce, na které jsou odesílány nebo přijímány zprávy (nebo obojí). Skládá se z umístění (adresy), které definuje, kde se dají odesílat zprávy, specifikaci komunikačního mechanismu (vazby), který popisuje, jak se zprávy mají odeslat, a definici pro sadu zpráv, která se dá odeslat nebo přijmout (nebo obojí) na této adrese. umístění (kontrakt služby) popisující zprávu, kterou je možné odeslat.

Služba WCF se zveřejňuje na světě jako kolekce koncových bodů.

**Koncový bod aplikace**  
 Koncový bod vystavený aplikací a, který odpovídá kontraktu služby implementovanému aplikací.

**Koncový bod infrastruktury**  
 Koncový bod, který je zpřístupněný infrastrukturou, aby usnadnil funkčnost, kterou vyžaduje nebo poskytuje služba, která se nevztahují k kontraktu služby. Například služba může mít koncový bod infrastruktury, který poskytuje informace o metadatech.

**Adresa**  
 Určuje umístění, kde jsou přijímány zprávy. Je zadaný jako identifikátor URI (Uniform Resource Identifier). Část schématu identifikátoru URI pojmenovává transportní mechanismus, který se má použít pro přístup k adrese, například HTTP a TCP. Hierarchická část identifikátoru URI obsahuje jedinečné umístění, ve kterém je formát závislý na transportním mechanismu.

Adresa koncového bodu umožňuje vytvořit jedinečné adresy koncových bodů pro každý koncový bod ve službě nebo za určitých podmínek pro sdílení adresy mezi koncovými body. Následující příklad ukazuje adresu pomocí protokolu HTTPS s jiným než výchozím portem:

```http
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService
```

**Vazby**  
 Definuje, jak koncový bod komunikuje po celém světě. Je tvořen sadou komponent nazvaných vazby, které jsou v zásobníku v jednom nad druhou k vytvoření komunikační infrastruktury. Vazba také definuje přenos (například HTTP nebo TCP) a používané kódování (například text nebo binární). Vazba může obsahovat prvky vazby, které určují podrobnosti, jako jsou mechanismy zabezpečení používané k zabezpečení zpráv, nebo vzor zprávy, který je používán koncovým bodem. Další informace najdete v tématu [Konfigurace služeb](configuring-services.md).

**Element Binding**  
 Představuje konkrétní část vazby, jako je například Transport, kódování, implementaci protokolu na úrovni infrastruktury (například WS-ReliableMessaging) nebo jakékoli jiné součásti komunikačního zásobníku.

**Chování**  
 Komponenta, která řídí různé aspekty běhu služby, koncového bodu, konkrétní operace nebo klienta. Chování jsou seskupena podle rozsahu: běžné chování ovlivňuje všechny koncové body globálně, chování služby ovlivňuje pouze aspekty související se službami, chování koncového bodu ovlivňuje pouze vlastnosti související s koncovým bodem a chování na úrovni provozu ovlivní konkrétní Operations. Například jedno chování služby je omezování, které určuje, jak služba reaguje, když nadměrné zprávy hrozí zahlcením možností manipulace. Chování koncového bodu na druhé straně řídí pouze aspekty, které jsou relevantní pro koncové body, například jak a kde najít bezpečnostní pověření.

**Vazby poskytované systémem**  
 WCF zahrnuje řadu vazeb poskytovaných systémem. Jedná se o kolekce prvků vazby, které jsou optimalizované pro konkrétní scénáře. Například <xref:System.ServiceModel.WSHttpBinding> je navržený pro interoperabilitu se službami, které implementují různé specifikace WS-\*. Tyto předdefinované vazby šetří čas tím, že prezentují jenom možnosti, které se dají správně použít pro konkrétní scénář. Pokud předdefinovaná vazba nesplňuje vaše požadavky, můžete vytvořit vlastní vazbu.

**Konfigurace versus kódování**  
 Kontrolu aplikace lze provádět buď prostřednictvím kódu, prostřednictvím konfigurace, nebo kombinací obou. Konfigurace má výhodu povolit jiným uživatelům než vývojář (například správce sítě) nastavit parametry klienta a služby po zápisu kódu a bez nutnosti překompilovat. Konfigurace neumožňuje nastavit jenom hodnoty, jako jsou adresy koncových bodů, ale také umožňuje další kontrolu tím, že vám umožní přidat koncové body, vazby a chování. Kódování umožňuje vývojářům zachovat přísnou kontrolu nad všemi komponentami služby nebo klienta. všechna nastavení prováděná prostřednictvím konfigurace lze zkontrolovat a v případě potřeby přepsat kódem.

**Operace služby**  
 Procedura definovaná v kódu služby, která implementuje funkce pro operaci. Tato operace je vystavena klientům jako metody v klientovi WCF. Metoda může vracet hodnotu a může mít nepovinný počet argumentů, nemůžou mít žádné argumenty a vracet žádnou odpověď. Například operace, která funguje jako jednoduché "Hello", se dá použít jako oznámení o přítomnosti klienta a k zahájení řady operací.

**Kontrakt služby**  
 Spojuje více souvisejících operací s jednou funkční jednotkou. Kontrakt může definovat nastavení na úrovni služby, jako je například obor názvů služby, odpovídající kontrakt zpětného volání a další taková nastavení. Ve většině případů je smlouva definována vytvořením rozhraní v programovacím jazyce podle vašeho výběru a použitím atributu <xref:System.ServiceModel.ServiceContractAttribute> na rozhraní. Skutečný výsledek kódu služby implementuje rozhraní.

**Kontrakt operace**  
 Kontrakt operace definuje parametry a návratový typ operace. Při vytváření rozhraní, které definuje kontrakt služby, značíte kontrakt operace použitím atributu <xref:System.ServiceModel.OperationContractAttribute> pro každou definici metody, která je součástí smlouvy. Operace lze modelovat jako přebírání jedné zprávy a vrácení jedné zprávy nebo při přijetí sady typů a vrácení typu. V druhém případě systém určí formát pro zprávy, které je potřeba vyměňovat pro danou operaci.

**Kontrakt zprávy**  
 Popisuje formát zprávy. Například deklaruje, zda by měly prvky zprávy jít v záhlavích versus text, jakou úroveň zabezpečení má být použita na prvky zprávy atd.

**Smlouva o selhání**  
 Dá se přidružit k operaci služby k označení chyb, které se můžou vrátit volajícímu. K operaci může být přidružena nula nebo více chyb. Tyto chyby jsou chyby protokolu SOAP, které jsou modelovány jako výjimky v programovacím modelu.

**Kontrakt dat**  
 Popis v metadatech datových typů, které služba používá. To umožňuje ostatním uživatelům spolupracovat s touto službou. Datové typy lze použít v jakékoli části zprávy, například jako parametry nebo návratové typy. Pokud služba používá pouze jednoduché typy, není nutné explicitně používat kontrakty dat.

**Hostování**  
 Služba musí být hostována v některém procesu. _Hostitel_ je aplikace, která řídí dobu života služby. Služby je možné hostovat nebo spravovat pomocí stávajícího hostitelského procesu.

**Samoobslužná služba**  
 Služba, která je spuštěna v aplikaci procesu, kterou vytvořil vývojář. Vývojář řídí svou dobu života, nastavuje vlastnosti služby, otevírá službu (nastaví režim naslouchání) a zavírá službu.

**Hostitelský proces**  
 Aplikace, která je navržena pro hostování služeb. Patří mezi ně Internetová informační služba (IIS), aktivační služba Windows (WAS) a služby systému Windows. V těchto hostovaných scénářích hostitel řídí dobu života služby. Například pomocí služby IIS můžete nastavit virtuální adresář, který obsahuje sestavení a konfigurační soubor služby. Po přijetí zprávy služba IIS spustí službu a nařídí její dobu života.

**Vytváření instancí**  
 Služba má model vytváření instancí. Existují tři modely vytváření instancí: "Single", ve kterém jeden objekt CLR Services všichni klienti; " za volání ", kde je vytvořen nový objekt CLR pro zpracování každého volání klienta; a "na relaci", ve které je vytvořena sada objektů CLR, jedna pro každou samostatnou relaci. Výběr modelu vytváření instancí závisí na požadavcích aplikace a na očekávaném způsobu použití služby.

**Klientská aplikace**  
 Program, který vyměňuje zprávy s jedním nebo více koncovými body. Klientská aplikace začíná vytvořením instance klienta WCF a voláním metod klienta WCF. Je důležité si uvědomit, že jedna aplikace může být klient i služba.

**Kanál**  
 Konkrétní implementace elementu vazby. Vazba představuje konfiguraci a kanál je implementace přidružená k této konfiguraci. Proto je k jednotlivým prvkům vazby přidružen kanál. Zásobník kanálů na sebe navzájem, aby vytvořil konkrétní implementaci vazby: zásobník kanálu.

**Klient WCF**  
 Konstrukce klient-aplikace, která zveřejňuje operace služby jako metody (v programovacím jazyce .NET Framework podle vašeho výběru, jako je například Visual Basic nebo C#vizuál). Každá aplikace může hostovat klienta WCF, včetně aplikace, která hostuje službu. Proto je možné vytvořit službu, která obsahuje klienty WCF jiných služeb.

Klient WCF se dá automaticky vygenerovat pomocí nástroje pro dodávání [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) a nasměrováním na běžící službu, která publikuje metadata.

**Metadata**  
 V rámci služby popisuje charakteristiky služby, které musí externí entita pochopit ke komunikaci se službou. Metadata mohou být spotřebována [nástrojem Svcutil. exe](servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování klienta WCF a doprovodné konfigurace, kterou může klientská aplikace použít k interakci se službou.

Metadata, která služba zveřejňuje, obsahují dokumenty schématu XML, které definují kontrakt dat služby a dokumenty WSDL, které popisují metody služby.

Pokud je povoleno, metadata pro službu jsou automaticky generována službou WCF kontrolou služby a jejích koncových bodů. Chcete-li publikovat metadata ze služby, je nutné explicitně povolit chování metadat.

**Zabezpečení**  
 V rámci služby WCF zahrnuje důvěrnost (šifrování zpráv pro předcházení odposlouchávání), integritu (prostředky pro detekci manipulace se zprávou), ověřování (prostředky pro ověření serverů a klientů) a autorizaci (řízení přístupu k prostředky). Tyto funkce se poskytují buď pomocí stávajících mechanismů zabezpečení, jako je TLS přes HTTP (označované také jako HTTPS), nebo implementací jednoho nebo více různých specifikací zabezpečení WS-\*.

**Režim zabezpečení přenosu**  
 Určuje, že mechanismy přenosové vrstvy (například HTTPS) poskytují důvěrnost, integritu a ověřování. Při použití přenosu, jako je HTTPS, má tento režim výhodu efektivního výkonu a pochopení z důvodu jeho prevalence v Internetu. Nevýhodou je, že tento druh zabezpečení se používá samostatně na každém segmentu směrování v komunikační cestě, což znamená, že komunikace je náchylná k útoku "muž v prostředním".

**Režim zabezpečení zpráv**  
 Určuje, že zabezpečení je zajištěno implementací jedné nebo více specifikací zabezpečení, jako je například specifikace s názvem [specifikace Web Services Security: zabezpečení zpráv SOAP](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf). Každá zpráva obsahuje nezbytné mechanismy pro zajištění zabezpečení během přenosu a umožňuje přijímačům detekovat manipulaci a dešifrovat zprávy. V tomto smyslu je zabezpečení zapouzdřeno v rámci každé zprávy a zajišťuje komplexní zabezpečení napříč více segmenty směrování. Vzhledem k tomu, že informace o zabezpečení se stávají součástí zprávy, je také možné zahrnout do zprávy více druhů přihlašovacích údajů (tyto údaje jsou označovány jako _deklarace_). Tento přístup má taky možnost Povolit zabezpečenou cestu prostřednictvím jakéhokoli přenosu, včetně několika přenosů mezi zdrojem a cílem. Nevýhodou tohoto přístupu je složitá složitost používaných kryptografických mechanismů, což vede k důsledkům v souvislosti s výkonem.

**Přenos pomocí režimu zabezpečení přihlašovacích údajů zprávy**  
 Určuje použití přenosové vrstvy k zajištění důvěrnosti, ověřování a integrity zpráv, zatímco každá ze zpráv může obsahovat více přihlašovacích údajů, které jsou vyžadovány příjemcem zprávy.

**WS-\***  
 Zkratka pro rostoucí sadu specifikací webové služby (WS), jako jsou WS-Security, WS-ReliableMessaging a tak dále, které jsou implementované ve službě WCF.

## <a name="see-also"></a>Viz také:

- [Co je Windows Communication Foundation](whats-wcf.md)
- [Architektura Windows Communication Foundation](architecture.md)
