---
title: Základní koncepty služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: c19169d61a96314e9fcfad94b013af18440e1ff5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474087"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Základní koncepty služby Windows Communication Foundation
Tento dokument obsahuje podrobný pohled na architekturu Windows Communication Foundation (WCF). Jeho účelem je vysvětlují klíčové koncepty a jak je umístit společně. Kurz týkající se vytváření nejjednodušší verzi klienta a služby WCF, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md). Další programování WCF najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>Základy WCF  
 WCF je modul runtime a sadu rozhraní API pro vytváření systémy, které odesílání zpráv mezi službami a klienty. Stejné infrastruktury a rozhraní API slouží k vytvoření aplikace, které komunikují s jinými aplikacemi ve stejném počítači systému nebo v systému, který se nachází v jiné firmě a přístupné přes Internet.  
  
### <a name="messaging-and-endpoints"></a>Zasílání zpráv a koncových bodů  
 WCF je založená na pojmu komunikace založená na zprávách a cokoli, která můžete modelovat jako jednotným způsobem v programovacím modelu lze reprezentovat zprávu (například požadavek HTTP nebo zprávy služby Řízení front zpráv (MSMQ)). To umožňuje rozhraní unified API napříč různými mechanismy přenosu.  
  
 Model rozlišuje mezi *klienti*, což jsou aplikace, které iniciují komunikaci, a *služby*, což jsou aplikace, které klientům komunikovat s nimi a reagovat na, počkejte komunikace. Jednu aplikaci může fungovat jako klient a služba. Příklady najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md) a [sítě Peer-to-Peer](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 Zprávy se posílají mezi koncovými body. *Koncové body* jsou místa, kde jsou zprávy odesílané nebo přijímané (nebo obojí), které definují všech informací potřebných k výměně zpráv. Služba zpřístupňuje jeden nebo více koncových bodů aplikace (stejně jako nula nebo více koncových bodů infrastruktury) a klient vytvoří koncový bod, který je kompatibilní s jeden z koncových bodů služby.  
  
 *Koncový bod* popisuje způsobem založené na standardu odešle zprávy, jak by měla být odeslána a jak by měla vypadat zprávy. Službu můžete zpřístupnit tyto informace jako metadata, která dokáže zpracovávat klientů ke generování odpovídající klientů WCF a komunikace *zásobníky*.  
  
### <a name="communication-protocols"></a>Komunikační protokoly  
 Jeden povinný element komunikační balík je *přenosový protokol*. Zprávy odesílat prostřednictvím intranetu a Internetu pomocí běžných přenosy, jako jsou HTTP a TCP. Jiné přenosy jsou součástí, které podporují komunikaci s aplikacemi služby Řízení front zpráv a uzlů v síťové sdílené sítě. Můžete přidat další mechanismy přenosu pomocí předdefinovaných Rozšiřovací body služby WCF.  
  
 Další požadovaný element v zásobníku komunikace je kódování, které určuje formátování jakékoli dané zprávy. WCF poskytuje následujícím kódování:  
  
-   Kódování, interoperabilní kódování textu.  
  
-   Zpráva přenosu optimalizace mechanismus (MTOM) kódování, což je interoperabilní způsob pro efektivní zasílání nestrukturovaná binární data do a ze služby.  
  
-   Binární kódování pro efektivní přenos.  
  
 Můžete přidat více kódování mechanismy (například v komprese kódování) pomocí předdefinovaných Rozšiřovací body služby WCF.  
  
### <a name="message-patterns"></a>Vzory zprávy  
 WCF podporuje několik schémata zasílání zpráv, včetně požadavek odpověď, jednosměrné a duplexní komunikaci. Jiné přenosy podporují různé vzorce zasílání zpráv a tím ovlivňovat typů interakcí, které podporují. Rozhraní API pro WCF a modul runtime také umožňují odesílat zprávy, bezpečně a spolehlivě.  
  
## <a name="wcf-terms"></a>Podmínky pro WCF  
 V následujících bodech dalších konceptů a termínů používaných v dokumentaci WCF.  
  
 – zpráva  
 Samostatná jednotka dat, která se může skládat z více částí, včetně záhlaví a text.  
  
 service  
 Konstruktor, který zpřístupňuje jeden nebo více koncových bodů se každý koncový bod vystavuje jednu nebo víc operací služeb.  
  
 endpoint  
 Konstrukce, na které zprávy jsou odeslány nebo přijaty (nebo obojí). V, který obsahuje umístění (adresa), který definuje, kde lze odesílat zprávy, specifikace mechanizmus pro komunikaci (vazba), který popisuje, jak by měly být odeslány zprávy, a definici pro sadu zpráv, které můžete odeslat ani přijmout (nebo obojí) umístění (kontraktu služby), který popisuje, jaké zprávy odesílat.  
  
 Služby WCF je přístupný na světě jako kolekce koncových bodů.  
  
 koncový bod aplikace  
 Koncového bodu určeného aplikace a, který odpovídá kontraktu služby implementované aplikace.  
  
 koncový bod infrastruktury  
 Koncový bod, který je zveřejněný prostřednictvím infrastruktury pro usnadnění funkce, které je potřeba nebo poskytovaných službou, která se nevztahuje na kontraktu služby. Služba může mít například infrastruktury koncový bod, který poskytuje informace o metadatech.  
  
 adresa  
 Určuje umístění, ve kterém jsou zprávy přijímány. Je zadaný jako identifikátor URI (Uniform Resource). Součást schématu identifikátoru URI názvy přenos mechanismus použít pro přístup k adrese, jako jsou HTTP a TCP. Hierarchické součást identifikátoru URI obsahuje jedinečné umístění, jejichž formát je závislá na přenos mechanismus.  
  
 Adresa koncového bodu vám umožňuje vytvářet adresy koncových bodů jedinečný pro každý koncový bod ve službě, nebo za určitých podmínek, sdílet adresu mezi koncovými body. Následující příklad ukazuje adresu pomocí protokolu HTTPS s jiný než výchozí port:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 vazba  
 Definuje, jak koncový bod komunikuje na celém světě. Je vytvořen z sada komponent volá prvky vazby, které "zásobníku" jednoho nad druhým vytvořit komunikační infrastrukturu. Přinejmenším vazba definuje přenos (například HTTP nebo TCP) a kódování používá (jako jsou textová nebo binární). Vazbu může obsahovat elementy vazby, které určují podrobnosti, jako jsou bezpečnostní mechanismy sloužící k zabezpečení zprávy nebo zprávy vzor použitý funkcí koncový bod. Další informace najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
 element vazby  
 Představuje konkrétní vazby, jako je například přenosu, kódování, implementace protokolu úrovni infrastruktury (třeba WS-ReliableMessaging) nebo jakoukoli jinou součástí komunikačního balíku.  
  
 chování  
 Součást, který řídí různé aspekty za běhu služby, koncový bod, určitou operaci nebo klienta. Chování jsou seskupené podle oboru: běžné chování ovlivňuje všechny koncové body globálně, služba chování ovlivňuje pouze související se službou aspekty, chování koncového bodu ovlivňuje pouze vlastnosti související se koncový bod a úrovni operace chování ovlivňuje konkrétní operace. Například je omezování chování služby za jednu, která určuje, jak služba reaguje při přebytek zpráv, které ohrožují zahlcovat možnosti zpracování. Chování koncového bodu, na druhé straně řídí pouze prvky, které jsou relevantní pro koncové body, jako je například jak a kde najít přihlašovací údaje zabezpečení.  
  
 vazby poskytované systémem  
 WCF obsahuje několik vazeb poskytovaných systémem. Toto jsou kolekce elementů, které jsou optimalizované pro určité scénáře vazby. Například <xref:System.ServiceModel.WSHttpBinding> je navržena pro spolupráci se službami, které implementují různé WS-* specifikace. Tyto předdefinované vazby ušetřit čas tím, že předloží pouze možnosti, které mohou být použity správně pro konkrétní scénář. Pokud předdefinované vazby nesplňuje vaše požadavky, můžete vytvořit vlastní vlastní vazby.  
  
 Konfigurace a psaní kódu  
 Ovládací prvek aplikace můžete udělat buď přes psaní kódu, prostřednictvím konfigurace nebo kombinaci obojího. Konfigurace má výhodu v podobě umožňuje někdo než pro vývojáře (například správce sítě) můžete nastavit parametry pro klienta a služby, po zapsání kódu a bez nutnosti znovu kompilovat. Konfigurace nejen umožňuje nastavit hodnoty, jako jsou adresy koncových bodů, ale také umožňuje další ovládací prvek tím, že můžete přidat koncové body, vazby a chování. Psaní kódu umožňuje vývojářům zachovat přísnou kontrolu všech součástí služby ani klienta, a můžete ho zkontrolovat všechna nastavení se provádí prostřednictvím konfigurace a v případě potřeby přepsat pomocí kódu.  
  
 operace služby  
 Postup uvedený v kódu služby, který implementuje funkce pro operace. Tato operace je zveřejněné klientům jako metody na klienta WCF. Metodu můžete vracet hodnotu, můžete využít libovolný počet argumentů, nebo nepřebírají žádné argumenty a vrátit žádná odpověď. Operace, která funguje jako jednoduchý "Hello" může například sloužit jako oznámení o stavu klienta a zahajte posloupnost operací.  
  
 kontrakt služby  
 Spojuje více souvisejících operací do jedné jednotky funkční. Smlouvy můžete definovat nastavení na úrovni služby, jako je například obor názvů služby, odpovídající kontrakt zpětného volání a dalších taková nastavení. Ve většině případů je definována kontrakt vytváření rozhraní v programovacím jazyce podle vašeho výběru a použití <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní. Výsledky kódu aktuální služby prostřednictvím implementace rozhraní.  
  
 operace kontraktu  
 Kontrakt operace definuje parametry a návratový typ operace. Při vytváření rozhraní, které definuje kontrakt služby s použitím místo kontrakt operace <xref:System.ServiceModel.OperationContractAttribute> atribut pro každou definici metody, která je součástí smlouvy. Operace můžete modelovat jako trvá do jedné zprávy nebo vrátit do jedné zprávy nebo jako s ohledem sadu typů a vracející typ. V takovém případě systém určí formát zpráv, které je třeba vyměnit pro danou operaci.  
  
 kontrakt zprávy  
 Popisuje formát zprávy. Například deklaruje, jestli zpráva prvky by měl přejít v záhlaví a text, jakou úroveň zabezpečení bude použito pro prvky zprávu, a tak dále.  
  
 Chyba – kontrakt  
 Můžou být spojené s operace služby k označení chyby, které mohou být vráceny volajícímu. Operace může mít nula nebo více chyb, které s ním spojená. Tyto chyby jsou chyb SOAP, které jsou modelovány jako výjimky v programovacím modelu.  
  
 kontrakt dat  
 Popisy v metadatech datových typů, které služba používá. To umožňuje ostatním uživatelům zajistit vzájemnou funkční spolupráci se službou. Datové typy, které lze použít v jakékoli části zprávy, například jako parametry nebo návratové typy. Pokud služba používá pouze jednoduché typy, není nutné explicitně kontraktů dat používat.  
  
 hostování  
 Služba musí být hostovaný ve nějaký proces. A *hostitele* je aplikace, které řídí životnost služby. Služby můžete v místním prostředí nebo spravovat existující hostitelský proces.  
  
 služba s vlastním hostováním  
 Služba, která běží v rámci procesu aplikace, kterou vytvořili vývojáři. Vývojář určuje jeho životnost, nastaví vlastnosti služby, se otevře služby (které ho nastaví do režimu naslouchání) a služba se zavře.  
  
 proces hostování  
 Aplikace, která je navržená pro hostování služeb. Patří mezi ně Internetové informační služby (IIS), aktivační služby Windows (WAS) a služby Windows. V těchto scénářích hostovaných hostitel řídí životnost služby. Například pomocí služby IIS nastavením virtuální adresář, který obsahuje sestavení a konfigurační soubor služby. Při doručení zprávy do spustí službu IIS a určuje jeho životnost.  
  
 instance  
 Služba je vytvoření instance modelu. Existují tři vytvoření instance modelů: "jednou," ve kterém jeden objekt CLR služby všichni klienti; " za volání,"ve kterém se vytvoří nový objekt CLR pro zpracování jednotlivých volání klienta; a "na relaci," v které sadu CLR objekty, je vytvořen, jeden pro každou samostatnou relaci. Možnost vytvoření instance modelu závisí na očekávané využití model služby a požadavky aplikace.  
  
 Klientská aplikace  
 Program, který vyměňuje zpráv pomocí jednoho nebo více koncových bodů. Klientská aplikace začne vytvořením instance klienta WCF a volání metod klienta WCF. Je důležité si uvědomit, že klient a služba může být jedné aplikace.  
  
 Kanál  
 Konkrétní implementaci elementu vazby. Představuje konfiguraci vazby a kanál je implementace spojené s touto konfigurací. Proto je přidružený k každý prvek vazby kanálu. Kanály zásobníku na druhé a vytvořit konkrétní implementaci vazby: zásobník kanálu.  
  
 Klienta WCF  
 Konstrukce klientskou aplikaci, která zveřejňuje operací služby jako metody (v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programovací jazyk podle vašeho výběru, jako je například Visual Basic nebo Visual C#). Všechny aplikace, můžete hostovat klienta WCF, včetně aplikace, který je hostitelem služby. Proto je možné vytvořit službu, která obsahuje klienty WCF dalších služeb.  
  
 Klienta WCF je možné vygenerovat automaticky pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a přejdete na spuštěnou službu, která publikuje metadat.  
  
 metadata  
 Ve službě popisuje vlastnosti služby, kterou je potřeba pochopit, ke komunikaci se službou externí entity. Metadata mohou být spotřebovány [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta WCF a související konfigurace, klientská aplikace můžete použít k interakci se službou.  
  
 Metadata určeného službou obsahují dokumentů schématu XML, které definují kontrakt dat služby a dokumenty WSDL, které popisují metody služby.  
  
 Při povolení metadat pro službu automaticky generuje služba WCF zkontrolováním jeho koncových bodů a služba. Být zveřejněna metadata ze služby, musíte výslovně povolit chování metadat.  
  
 zabezpečení  
 Ve službě WCF zahrnuje (šifrování zpráv, aby se zabránilo odposlouchávání) důvěrnost, integritu (prostředky pro zjištění manipulaci s touto zprávou), (prostředky pro ověření serverů a klientů) ověřování a autorizace (řízení přístupu k prostředky). Tyto funkce jsou k dispozici buď využití stávající mechanismy zabezpečení, jako je protokol TLS přes protokol HTTP (označované také jako HTTPS), nebo implementací nejméně jeden z různých WS-* specifikace zabezpečení.  
  
 režim zabezpečení Transport  
 Určuje, že důvěrnost, integritu a ověřování jsou k dispozici mechanismy přenosové vrstvy (například HTTPS). Při použití přenosu, jako je protokol HTTPS, v tomto režimu nabízí výhodu v podobě je efektivnější v jeho výkon a zaměřený z důvodu jeho rozšíření na Internetu. Nevýhodou je, že tento druh zabezpečení, použije se samostatně pro každý segment směrování v komunikační trasa, aby komunikace náchylné k útoku "man in the middle".  
  
 režim zabezpečení zpráv  
 Určuje, že zabezpečení poskytuje implementaci jeden nebo více specifikací zabezpečení, jako je specifikace s názvem [webové služby zabezpečení: zabezpečení zpráv SOAP](https://go.microsoft.com/fwlink/?LinkId=94684). Každá zpráva obsahuje nezbytné mechanismů pro zabezpečení během jeho kopírování a umožňuje příjemci umožňuje zjistit případnou manipulaci a k dešifrování zprávy. V tomto smyslu zabezpečení zapouzdřen v rámci každé zprávy poskytující-koncové zabezpečení napříč více segmenty směrování. Vzhledem k tomu, že informace o zabezpečení se stane součástí zprávy, je také možné zahrnout více druhů přihlašovací údaje se zprávou (tyto jsou označovány jako *deklarace identity*). Tento přístup také nabízí výhodu v podobě povolení zpráva, kterou chcete procházet bezpečně přes všechny dopravu, včetně více přenosy mezi její zdroj a cíl. Nevýhody tohoto přístupu je složitost kryptografických mechanismů zapojeni, což vede k vliv na výkon.  
  
 přenosu se režim zabezpečených zpráv přihlašovacích údajů  
 Určuje použití přenosové vrstvy k zajištění důvěrnosti, ověřování a integrity zprávy, při každé zprávy může obsahovat více přihlašovacích údajů (deklarace) vyžaduje spuštěné přijímače zpracovaly zprávy.  
  
 WS-*  
 Sdružená hodnota stále početnější sadu Web Service (WS) specifikace, jako je WS-Security, WS-ReliableMessaging a tak dále, které jsou implementovány ve službě WCF.  
  
## <a name="see-also"></a>Viz také  
 [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Architektura Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Architektura zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
