---
title: Základní koncepty služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 41bef6bf5a69a51738c6848050972a1a4e01c153
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Základní koncepty služby Windows Communication Foundation
Tento dokument poskytuje podrobný pohled na architekturu Windows Communication Foundation (WCF). Je určena k vysvětlují klíčové koncepty a jak je umístit společně. Kurz týkající se vytváření nejjednodušší verzi klienta a služby WCF, najdete v části [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md). Další programování WCF najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>Základy WCF  
 WCF je modul runtime a sada rozhraní API pro vytváření systémy, které odesílají zprávy mezi služeb a klientů. Stejné infrastruktury a rozhraní API slouží k vytvoření aplikace, které komunikují s jinými aplikacemi ve stejném počítači systému nebo v systému, který se nachází v jiné společnosti a je k ní přistupovat přes Internet.  
  
### <a name="messaging-and-endpoints"></a>Koncové body a zasílání zpráv  
 WCF je založena na představu o komunikaci na základě zpráv a nic, který je možné modelovat jako zprávu (například požadavek HTTP nebo zprávy služby Řízení front zpráv (MSMQ)) může být reprezentován jednotným způsobem v programovací model. To umožňuje jednotné rozhraní API napříč různými mechanismy přenosu.  
  
 Model rozlišuje mezi *klienti*, což jsou aplikace, které zahájí komunikaci, a *služby*, což jsou aplikace, které klientům komunikovat s nimi a reagovat na událost, počkejte komunikace. Jednu aplikaci může fungovat jako klient a služba. Příklady najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md) a [Peer-to-Peer sítě](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 Zprávy se posílají mezi koncovými body. *Koncové body* jsou míst, kde jsou zprávy odesílané nebo přijímané (nebo obě) a že definují všechny požadované informace o výměně zpráv. Služba vystavuje jeden nebo více koncových bodů aplikace (stejně jako nula nebo víc koncových bodů infrastruktury) a klient vytvoří koncový bod, který je kompatibilní s jedním z koncových bodů služby.  
  
 *Koncový bod* popisuje způsobem založené na standardu, kde by měly být odeslány zprávy, jak by měly být odeslány a co by měl vypadat zprávy. Službu můžete vystavit tyto informace jako metadata, která může zpracovat klientů pro generování příslušné klienti WCF a komunikace *zásobníky*.  
  
### <a name="communication-protocols"></a>Komunikační protokoly  
 Jeden požadovaný element zásobníku komunikace *přenosu protokolu*. Prostřednictvím intranetu a Internetu pomocí běžných přenosy, jako je například HTTP a TCP nelze odesílat zprávy. Ostatní přenosy jsou zahrnuty podporující komunikaci s aplikací služby Řízení front zpráv a uzly na mřížku sdílené sítě. Pomocí předdefinovaných rozšíření body služby WCF se dá přidat další mechanismy přenosu.  
  
 Další požadovaný element v zásobníku komunikace je kódování, které určuje způsob formátování jakékoli dané zprávy. WCF poskytuje následující kódování:  
  
-   Kódování, umožňuje vzájemnou spolupráci kódování textu.  
  
-   Zpráva přenosu optimalizace mechanismus (MTOM) kódování, které je umožňuje vzájemnou spolupráci způsob pro efektivní odesílání nestrukturovaných binární data do a ze služby.  
  
-   Binární kódování pro efektivní přenos.  
  
 Více kódování mechanismy (například komprese kódování) lze přidat pomocí předdefinovaných rozšíření body služby WCF.  
  
### <a name="message-patterns"></a>Vzory zpráv  
 WCF podporuje několik zasílání zpráv způsoby, včetně požadavku a odpovědi, jednosměrné a duplexní komunikace. Různé přenosy podporují různé vzorce zasílání zpráv a proto ovlivnit typy interakce, které podporují. Rozhraní API WCF a prostředí runtime také dozvíte, jak bezpečně a spolehlivě odesílat zprávy.  
  
## <a name="wcf-terms"></a>Podmínky WCF  
 Další konceptů a termínů používaných v dokumentaci WCF patří.  
  
 – zpráva  
 Samostatná jednotka data, která se může skládat z několika částí, včetně text a záhlaví.  
  
 service  
 Konstruktor, který vystavuje jeden nebo více koncových bodů, každý koncový bod vystavení jeden nebo víc operací služeb.  
  
 endpoint  
 Konstrukce zprávy, které jsou odesílané nebo přijímané (nebo obě). Zahrnuje umístění (adresu), která definuje, kde lze odesílat zprávy, specifikaci komunikační mechanizmus (vazbu), který popisuje, jak by měly být odeslány zprávy, a definici pro sadu zpráv, které můžete odesílané nebo přijímané (nebo obě) v daném okamžiku umístění (kontraktu služby), který popisuje, jaké zprávy lze odeslat.  
  
 Služby WCF je vystaven na světě jako kolekce koncových bodů.  
  
 koncový bod aplikace  
 Koncový bod vystavené aplikace a který odpovídá kontraktu služby implementované aplikace.  
  
 koncový bod infrastruktury  
 Koncový bod, který je zveřejněný prostřednictvím infrastrukturu k zajištění funkcí, které je potřeba nebo poskytované na službu, kterou se nevztahuje na kontraktu služby. Například služby může mít infrastruktury koncový bod, který poskytuje informace o metadatech.  
  
 adresa  
 Určuje umístění, kde jsou přijaty zprávy. Je zadán jako identifikátor URI (Uniform Resource). Části schématu identifikátoru URI názvy přenosový mechanismus, který má použít pro přístup na adresu, jako je například HTTP a TCP. Hierarchická součástí identifikátor URI obsahuje jedinečné umístění, jejichž formát je závislá na přenosový mechanismus.  
  
 Adresa koncového bodu můžete vytvořit jedinečný koncový bod adresy pro každý koncový bod, ve službě nebo za určitých podmínek, chcete-li sdílet adresu napříč koncovými body. Následující příklad ukazuje adresu pomocí protokolu HTTPS na jiné než výchozí port:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 vazba  
 Definuje, jak koncový bod komunikuje na celém světě. Vytvořená sady součástí názvem prvky vazby, které "zásobníku" přes sebe vytvořit infrastrukturu komunikace. V každém vazbu definuje přenosu (například HTTP nebo TCP) a kódování používá (například textu nebo binárních). Vazba může obsahovat prvky vazby, které určit podrobnosti, třeba mechanismy zabezpečení sloužící k zabezpečení zprávy nebo vzor zprávy používá koncový bod. Další informace najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
 element vazby  
 Představuje konkrétním vazby, jako je například přenos, kódování, implementaci protokol úrovni infrastruktury (třeba WS-ReliableMessaging) nebo jakoukoli jinou součástí komunikačního balíku.  
  
 chování  
 Komponenta, která řídí různé aspekty spuštění služby, koncový bod, určité operace nebo klienta. Chování jsou seskupené podle oboru: společné chování ovlivňuje všechny koncové body globálně, pouze související se službou aspekty ovlivnit chování služby, koncový bod chování ovlivňuje pouze vlastnosti týkající se koncový bod a úrovni operace chování ovlivňuje konkrétní operace. Například je omezování jeden chování služby, která určuje, jak služba reaguje při nad zpráv hrozí zahlcovat jeho funkce pro zpracování. Chování koncového bodu na druhé straně řídí pouze aspekty, které jsou relevantní pro koncové body, například jak a kde najít pověření zabezpečení.  
  
 vazby poskytované systémem  
 WCF zahrnuje několik vazeb poskytovaných systémem. Toto jsou kolekce elementů, které jsou optimalizované pro určité scénáře vazby. Například <xref:System.ServiceModel.WSHttpBinding> je navržen pro interakci s službami, které implementují různé WS-* specifikace. Tyto předdefinované vazby ušetřit čas prezentací pouze možnosti, které mohou být správně použity pro konkrétní scénář. Pokud předdefinované vazbu nesplňuje vaše požadavky, můžete vytvořit vlastní vlastní vazby.  
  
 Konfigurace a kódování  
 Řízení aplikace, můžete udělat buď pomocí kódování, prostřednictvím konfigurace, nebo obojí. Konfigurace má výhodu v podobě povolení někdo než developer (například správce sítě) můžete nastavit parametry klienta a služby po zapsání kód a bez nutnosti její kompilace. Konfigurace pouze umožňuje nastavit hodnoty, jako jsou adresy koncových bodů, ale také umožňuje další ovládání povolením můžete přidat koncové body, vazeb a chování. Kódování umožňuje vývojáři zachovat přísnou kontrolu všech součástí služby nebo klienta, a všechna nastavení provést prostřednictvím konfigurace může být prověřovány a v případě potřeby přepsat kód.  
  
 operaci služby  
 Postup uvedený v kódu služby, která implementuje funkce pro operaci. Tato operace je pro klienty zpřístupněná jako metody pro klienta WCF. Metodu můžete vrátit hodnotu, může trvat libovolný počet argumentů, nebo nepřebírají žádné argumenty a vrátit žádná odpověď. Například operace, která funguje jako jednoduchý "Hello" slouží jako upozornění stavu klienta a zahájíte řady operací.  
  
 kontrakt služby  
 Sváže společně více souvisejících operací do jedné jednotky funkční. Nastavení úrovně služby, například obor názvů služby, odpovídající kontrakt zpětného volání a jiné těchto nastavení můžete definovat kontrakt. Ve většině případů kontrakt definované vytváření rozhraní ve programovací jazyk podle vašeho výběru a použití <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní. Výsledky skutečných služby kódu implementací rozhraní.  
  
 operace kontraktu  
 Operaci kontrakt definuje parametry a návratový typ operace. Při vytváření rozhraní, které definuje kontrakt služby, můžete použitím označily operaci kontrakt <xref:System.ServiceModel.OperationContractAttribute> atribut každý definici metody, která je součástí smlouvy. Operace můžete modelován jako přepnutím do jedné zprávy a vrátilo se do jedné zprávy, nebo jako trvá sadu typů a vrácení typu. V takovém případě bude systém určit formát zprávy, které potřebují k výměně pro tuto operaci.  
  
 kontrakt zprávy  
 Popisuje formát zprávy. Například deklaruje, zda zpráva prvky by měli přejít v záhlaví a text, jakou úroveň zabezpečení má být použita na jaké elementy zprávu, a tak dále.  
  
 Chyba – kontrakt  
 Může být přidružen operace služby k označení chyb, které mohou být vrácena volajícímu. Operace může obsahovat nula nebo více chyb, které jsou s ním spojená. Tyto chyby jsou SOAP chyb, které jsou modelovat jako výjimky v programovací model.  
  
 kontrakt dat  
 Popisy v metadatech datové typy, které služba používá. To umožňuje ostatním uživatelům zajistit vzájemnou funkční spolupráci se službou. Datové typy lze v libovolnou část zprávy, například jako parametry nebo návratové typy. Pokud služba používá pouze jednoduché typy, není nutné explicitně povoleno používat kontrakty dat.  
  
 hostování  
 V některých procesu musí být hostované služby. A *hostitele* je aplikace, která řídí životnost služby. Služby můžete hostovanou na vlastním nebo spravovat existující hostitelského procesu.  
  
 služba s vlastním hostováním  
 Služba, která běží v rámci procesu aplikace, který vytvořili vývojáři. Vývojář celé jeho životnosti ovládací prvky, nastaví vlastnosti služby, otevře služby (která ji nastaví do režimu naslouchání) a ukončení služby.  
  
 proces hostování  
 Aplikace, která je určená pro hostování služeb. Mezi ně patří Internetové informační služby (IIS), aktivační služby systému Windows (WAS) a služby systému Windows. V těchto scénářích hostované hostitele řídí životnost služby. Například pomocí služby IIS nastavením virtuální adresář, který obsahuje soubor sestavení a konfiguraci služby. Po přijetí zprávy spustí službu IIS a řídí celé jeho životnosti.  
  
 instance  
 Služba má model zřizování instancí. Existují tři zřizování instancí modely: "single," ve kterém jeden objekt CLR služeb všichni klienti; " za volání"ve kterém se vytvoří nový objekt CLR pro zpracování jednotlivých volání klienta; a "na relaci," v které sadu CLR objekty, se vytvoří, jednou pro každou samostatné relaci. Volba zřizování instancí modelu závisí na požadavky na aplikace a vzoru očekávané využití služby.  
  
 klientské aplikace  
 Program, který výměny zpráv pomocí jednoho nebo víc koncových bodů. Klientská aplikace začíná vytvoření instance klienta WCF a volání metod klienta WCF. Je důležité si uvědomit, že jednu aplikaci může být klienta a služby.  
  
 Kanál  
 Konkrétní implementaci prvku vazby. Představuje konfiguraci vazby a kanál je implementace přidružené k této konfiguraci. Proto je kanál, spojené s každou prvku vazby. Kanály skládat na sebe vytvořit konkrétní implementaci vazby: zásobník kanálu.  
  
 Klienta WCF  
 Konstrukce klientskou aplikaci, která zveřejňuje operací služby jako metody (v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programovací jazyk podle vaší volby, jako je například jazyka Visual Basic a Visual C#). Všechny aplikace, může hostovat klienta WCF, včetně aplikace, který je hostitelem služby. Proto je možné vytvořit službu, která zahrnuje klienti WCF dalších služeb.  
  
 Klienta WCF pomocí automaticky generovány [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a přejdete na spuštěnou službu, která publikuje metadat.  
  
 metadata  
 Ve službě jsou popsané charakteristiky služby, která externí entity je potřeba pochopit ke komunikaci se službou. Metadata mohou být využívány službou [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro generování klienta WCF a doprovodné konfigurace, který klientská aplikace můžete použít k interakci se službou.  
  
 Metadata vystavené služba zahrnuje dokumentech schémat XML, které definují kontrakt dat služby, a WSDL dokumenty, které popisují metody služby.  
  
 Když je povolené, metadata pro službu automaticky generuje služba WCF zkontrolováním služba a její koncové body. K publikování metadat ze služby, je potřeba explicitně povolit chování metadat.  
  
 zabezpečení  
 Ve službě WCF zahrnuje důvěrnost (šifrování zpráv, aby se zabránilo odposlouchávání), integritu (znamená pro zjišťování manipulaci se zprávou), ověřování (prostředky pro ověření serverů a klientů) a autorizace (řízení přístupu k prostředky). Tyto funkce jsou k dispozici buď využívání stávající mechanismy zabezpečení, jako je například TLS přes protokol HTTP (také označované jako HTTPS), nebo implementovat jednu nebo více různých WS-* bezpečnostní specifikací.  
  
 režim zabezpečení přenosu  
 Určuje, že důvěrnost, integritu a ověřování jsou poskytovány na mechanismy transport layer (jako je například HTTPS). Při použití přenosu jako protokol HTTPS, tento režim má výhodu v podobě se efektivní v jeho výkon a popsaných z důvodu jeho jejich rozšíření na Internetu. Nevýhodou je, že je tento druh zabezpečení samostatně použitá jednotlivých směrování v cestě komunikace, provedení komunikace náchylná k útoku "man uprostřed".  
  
 režim zabezpečení zpráv  
 Určuje, že zabezpečení poskytuje implementace jeden nebo více bezpečnostní specifikací, jako je specifikace s názvem [zabezpečení webové služby: zabezpečení zpráv protokolu SOAP](http://go.microsoft.com/fwlink/?LinkId=94684). Každá zpráva obsahuje nezbytné mechanismů pro zabezpečení během jeho přenosu a umožňuje příjemci, chcete-li zjistit případnou manipulaci a k dešifrování zpráv. V této smysl je zabezpečení zapouzdřený v rámci každé zprávy, zajištění zabezpečení začátku do konce napříč více segmenty směrování. Protože informace o zabezpečení stane součástí zprávy, je také možné zahrnout více druhů přihlašovací údaje se zprávou (to se označuje jako *deklarace identity*). Tento přístup také nabízí výhodu v podobě povolení zprávu, která se bezpečně procházet přes všechny přenos, včetně více přenosy mezi jeho původní a cílové. Nevýhodou tohoto přístupu je složitosti kryptografických mechanismů zaměstnání, což vede k ovlivnit výkon.  
  
 přenos s režim zabezpečení přihlašovacích údajů zprávy  
 Určuje použití přenosové vrstvy k zajištění důvěrnosti, ověřování a integritu zprávy, když všechny zprávy může obsahovat více přihlašovací údaje (deklarace identity) vyžaduje, že příjemci zprávy.  
  
 WS-*  
 Sdružená vlastnost rostoucí sadu webové služby (WS) specifikace, jako je WS-zabezpečení, WS-ReliableMessaging a tak dále, které jsou implementované ve WCF.  
  
## <a name="see-also"></a>Viz také  
 [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Architektura Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
