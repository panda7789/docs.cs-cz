---
title: Verze služby
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: ea5e80e33d1b29e01e6d1867c50bb3bb973b01c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183112"
---
# <a name="service-versioning"></a>Verze služby
Po počátečním nasazení a potenciálně několikrát během jejich životnosti může být nutné změnit služby (a koncové body, které zveřejňují) z různých důvodů, jako je změna obchodních potřeb, požadavky na informační technologie nebo řešení jiných Problémy. Každá změna zavádí novou verzi služby. Toto téma vysvětluje, jak zvážit správu verzí v systému Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Čtyři kategorie změn služeb  
 Změny služeb, které mohou být požadovány, lze rozdělit do čtyř kategorií:  
  
- Změny smlouvy: Může být například přidána operace nebo datový prvek ve zprávě může být přidán nebo změněn.  
  
- Změny adresy: Například služba přesune do jiného umístění, kde koncové body mají nové adresy.  
  
- Změny vazby: Například změnit mechanismus zabezpečení nebo jeho nastavení změnit.  
  
- Změny implementace: Například při změně implementace interní metody.  
  
 Některé z těchto změn se nazývají "lámání" a jiné jsou "nonbreaking." Změna je *nerozdělitelné,* pokud všechny zprávy, které by byly úspěšně zpracovány v předchozí verzi jsou úspěšně zpracovány v nové verzi. Každá změna, která nesplňuje toto kritérium, je *zásadní* změnou.  
  
## <a name="service-orientation-and-versioning"></a>Orientace služby a správa verzí  
 Jedním z principů orientace na služby je, že služby a klienti jsou autonomní (nebo nezávislí). Mimo jiné to znamená, že vývojáři služeb nemohou předpokládat, že řídí nebo dokonce vědí o všech klientech služeb. To eliminuje možnost opětovného sestavení a opětovného nasazení všech klientů při změně verze služby. Toto téma předpokládá, že služba dodržuje tento princip a proto musí být změněna nebo "verzí" nezávisle na svých klientech.  
  
 V případech, kdy je neočekávaná změna a nelze se jí vyhnout, může se aplikace rozhodnout ignorovat tento princip a vyžadovat, aby klienti byli znovu sestaveni a znovu nasazeni s novou verzí služby.  
  
## <a name="contract-versioning"></a>Správa verzí smlouvy  
 Smlouvy používané klientem nemusí být stejné jako smlouvy používané službou; musí být pouze kompatibilní.  
  
 U servisních smluv znamená kompatibilita nové operace vystavené službou, ale existující operace nelze odebrat nebo změnit sémanticky.  
  
 U kontraktů dat znamená kompatibilita nové definice typů schématu, ale existující definice typu schématu nelze změnit způsoby přerušení. Porušení změn může zahrnovat odebrání datových členů nebo nekompatibilitu změny jejich datového typu. Tato funkce umožňuje službě určitou šířku při změně verze svých smluv bez přerušení klientů. Další dvě části vysvětlují nenarušující a narušující změny, které lze provést v datových a servisních smlouvách WCF.  
  
## <a name="data-contract-versioning"></a>Správa verzí kontraktů dat  
 Tato část se zabývá správu <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> verzí dat při použití tříd y a.  
  
### <a name="strict-versioning"></a>Striktní správa verzí  
 V mnoha scénářích při změně verze je problém, vývojář služby nemá kontrolu nad klienty a proto nemůže dělat předpoklady o tom, jak by reagovali na změny ve zprávě XML nebo schématu. V těchto případech je nutné zaručit, že nové zprávy budou ověřeny proti staré schéma, ze dvou důvodů:  
  
- Staří klienti byli vyvinuti s předpokladem, že schéma se nezmění. Mohou selhat při zpracování zpráv, pro které nebyly nikdy navrženy.  
  
- Staří klienti mohou provádět ověření skutečného schématu proti staré schéma ještě před pokusem o zpracování zpráv.  
  
 Doporučeným přístupem v těchto scénářích je považovat existující kontrakty dat za neměnné a vytvořit nové s jedinečnými kvalifikovanými názvy XML. Vývojář služby by pak buď přidat nové metody do existující smlouvy o poskytování služeb nebo vytvořit novou servisní smlouvu s metodami, které používají novou smlouvu dat.  
  
 To bude často v případě, že vývojář služby potřebuje napsat nějakou obchodní logiku, která by měla běžet ve všech verzích kontraktu dat plus obchodní kód specifický pro verzi pro každou verzi kontraktu dat. Dodatek na konci tohoto tématu vysvětluje, jak lze rozhraní použít k uspokojení této potřeby.  
  
### <a name="lax-versioning"></a>Laxní správa verzí  
 V mnoha jiných scénářích může vývojář služby předpokládat, že přidání nového volitelného člena do datové smlouvy nepřeruší stávající klienty. To vyžaduje, aby vývojář služby prověřil, zda stávající klienti neprovádějí ověření schématu a zda ignorují neznámé datové členy. V těchto scénářích je možné využít funkce smlouvy dat pro přidávání nových členů nerozdělitým způsobem. Vývojář služby může tento předpoklad provést s jistotou, pokud byly funkce kontraktu dat pro správu verzí již použity pro první verzi služby.  
  
 WCF, ASP.NET webové služby a mnoho dalších zásobníků webových služeb podporují *laxní správu verzí*: to znamená, že nepředstavují výjimky pro nové neznámé datové členy v přijatých datech.  
  
 Je snadné mylně věřit, že přidání nového člena nezlomí stávající klienty. Pokud si nejste jisti, že všichni klienti mohou zpracovávat laxní správu verzí, doporučujeme použít přísné pokyny pro správu verzí a považovat kontrakty dat za neměnné.  
  
 Podrobné pokyny pro laxní a přísné správu verzí kontraktů s daty naleznete v [tématu Best Practices: Data Contract Versioning](best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Rozlišování mezi datovou smlouvou a typy rozhraní .NET  
 Třídu nebo strukturu rozhraní .NET lze promítnout jako datovou smlouvu použitím atributu <xref:System.Runtime.Serialization.DataContractAttribute> na třídu. Typ .NET a jeho projekce smlouvy dat jsou dvě odlišné záležitosti. Je možné mít více typů .NET se stejnou projekcí kontraktu dat. Toto rozlišení je užitečné zejména v umožňuje změnit typ .NET při zachování smlouvy o plánovaných dat, a tím zachovat kompatibilitu s existujícími klienty i v pravém slova smyslu. Existují dvě věci, které byste měli vždy udělat pro zachování tohoto rozlišení mezi typem .NET a kontraktem dat:  
  
- Zadejte <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>a a . Vždy byste měli zadat název a obor názvů kontraktu dat, abyste zabránili zobrazení názvu a oboru názvů typu .NET ve smlouvě. Tímto způsobem, pokud se později rozhodnete změnit obor názvů .NET nebo název typu, zůstane kontrakt dat stejný.  
  
- Zadejte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Vždy byste měli zadat název vašich datových členů, abyste zabránili vystavení vašeho jména člena .NET ve smlouvě. Tímto způsobem, pokud se rozhodnete později změnit název .NET člena, vaše smlouva dat zůstane stejná.  
  
### <a name="changing-or-removing-members"></a>Změna nebo odebrání členů  
 Změna názvu nebo datového typu člena nebo odebrání datových členů je narušující změna i v případě, že je povolena laxní správa verzí. Pokud je to nutné, vytvořte novou datovou smlouvu.  
  
 Pokud je kompatibilita služby velmi důležitá, můžete zvážit ignorování nepoužívaných datových členů v kódu a ponechat je na místě. Pokud rozdělujete datový člen na více členů, můžete zvážit ponechání existujícího člena na místě jako vlastnosti, která může provádět požadované rozdělení a opětovné agregace pro klienty nižší úrovně (klienty, kteří nejsou upgradována na nejnovější verzi).  
  
 Podobně změny názvu datové smlouvy nebo oboru názvů narušují změny.  
  
### <a name="round-trips-of-unknown-data"></a>Round-Výlety neznámých dat  
 V některých scénářích je potřeba "round-trip" neznámá data, která pochází z členů přidány v nové verzi. Například služba "versionNew" odesílá data s některými nově přidanými členy klientovi "versionOld". Klient ignoruje nově přidané členy při zpracování zprávy, ale znovu odešle stejná data, včetně nově přidaných členů, zpět do služby versionNew. Typický scénář pro tento je aktualizace dat, kde jsou data načtena ze služby, změněna a vrácena.  
  
 Chcete-li povolit round-tripping pro určitý <xref:System.Runtime.Serialization.IExtensibleDataObject> typ, musí typ implementovat rozhraní. Rozhraní obsahuje jednu <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> <xref:System.Runtime.Serialization.ExtensionDataObject> vlastnost, která vrací typ. Vlastnost se používá k ukládání dat z budoucích verzí kontraktu dat, který je neznámý aktuální verzi. Tato data jsou pro klienta neprůhledná, ale když <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> je instance serializována, obsah vlastnosti je zapsán s daty ostatních členů smlouvy dat.  
  
 Doporučuje se, aby všechny typy implementovat toto rozhraní tak, aby vyhovovaly nové a neznámé budoucí členy.  
  
### <a name="data-contract-libraries"></a>Knihovny kontraktů dat  
 Mohou existovat knihovny kontraktů dat, kde je smlouva publikována do centrálního úložiště a implementátoři služeb a typů implementují a zveřejňují kontrakty dat z tohoto úložiště. V takovém případě při publikování smlouvy dat do úložiště, nemáte žádnou kontrolu nad tím, kdo vytváří typy, které ji implementují. Proto nelze změnit smlouvy po jeho publikování, vykreslování efektivně neměnné.  
  
### <a name="when-using-the-xmlserializer"></a>Při použití xmlserializeru  
 Stejné zásady správy verzí platí <xref:System.Xml.Serialization.XmlSerializer> při použití třídy. Pokud je vyžadována striktní správa verzí, považovat kontrakty dat za neměnné a vytvořit nové kontrakty dat s jedinečnými, kvalifikovanými názvy pro nové verze. Pokud jste si jisti, že lze použít laxní správu verzí, můžete přidat nové serializovatelné členy v nových verzích, ale nelze změnit nebo odebrat existující členy.  
  
> [!NOTE]
> Atributy <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Xml.Serialization.XmlAnyElementAttribute> a <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> používá pro podporu round-tripping neznámých dat.  
  
## <a name="message-contract-versioning"></a>Správa verzí smlouvy se zprávou  
 Pokyny pro správu verzí smlouvy zprávy jsou velmi podobné kontrakty správu verzí. Pokud je vyžadována striktní správa verzí, neměli byste měnit text zprávy, ale místo toho vytvořit novou smlouvu o zprávě s jedinečným kvalifikovaným názvem. Pokud víte, že můžete použít laxní správu verzí, můžete přidat nové části textu zprávy, ale neměnit nebo odebrat existující. Tento návod platí pro smlouvy holé a zabalené zprávy.  
  
 Záhlaví zpráv lze vždy přidat, i když se používá striktní správa verzí. Příznak MustUnderstand může ovlivnit správu verzí. Obecně platí, že model správy verzí pro záhlaví v WCF je popsáno ve specifikaci SOAP.  
  
## <a name="service-contract-versioning"></a>Správa verzí servisní smlouvy  
 Podobně jako správa verzí kontraktu dat, správa verzí smlouvy o službách zahrnuje také přidání, změnu a odebrání operací.  
  
### <a name="specifying-name-namespace-and-action"></a>Určení názvu, oboru názvů a akce  
 Ve výchozím nastavení je název servisní smlouvy název rozhraní. Jeho výchozí oborhttp://tempuri.orgnázvů je " ", ahttp://tempuri.org/contractname/methodnamekaždá operace akce je " ". Doporučujeme explicitně zadat název a obor názvů pro servisní smlouvu a akcihttp://tempuri.orgpro každou operaci, aby se zabránilo použití " " a aby se zabránilo rozhraní a názvy metod z vystaveny ve smlouvě služby.  
  
### <a name="adding-parameters-and-operations"></a>Přidání parametrů a operací  
 Přidání operací služby vystavených službou je nezlomná změna, protože stávající klienti nemusí být znepokojeni těmito novými operacemi.  
  
> [!NOTE]
> Přidání operací do smlouvy zpětného volání duplexní je narušující změnu.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Změna parametru operace nebo návratových typů  
 Změna parametru nebo návratové typy obecně je narušující změna, pokud nový typ implementuje stejnou datovou smlouvu implementovanou starým typem. Chcete-li provést takovou změnu, přidejte novou operaci do servisní smlouvy nebo definujte novou servisní smlouvu.  
  
### <a name="removing-operations"></a>Odebrání operací  
 Odebrání operace je také narušující změny. Chcete-li provést takovou změnu, definujte novou smlouvu o poskytování služeb a zpřístupníte ji na nový koncový bod.  
  
### <a name="fault-contracts"></a>Smlouvy o poruchách  
 Atribut <xref:System.ServiceModel.FaultContractAttribute> umožňuje vývojáři servisní smlouvy zadat informace o chybách, které mohou být vráceny z operací smlouvy.  
  
 Seznam závad popsaný ve smlouvě o poskytování služeb se nepovažuje za vyčerpávající. Operace může kdykoli vrátit chyby, které nejsou popsány v jeho smlouvě. Proto změna souboru chyb popsaných ve smlouvě se nepovažuje za porušení. Například přidání nové chyby do <xref:System.ServiceModel.FaultContractAttribute> smlouvy pomocí nebo odebrání existující chyby ze smlouvy.  
  
### <a name="service-contract-libraries"></a>Knihovny servisních smluv  
 Organizace mohou mít knihovny smluv, kde je smlouva publikována do centrálního úložiště a implementátoři služeb implementují smlouvy z tohoto úložiště. V takovém případě při publikování smlouvy o poskytování služeb do úložiště nemáte žádnou kontrolu nad tím, kdo vytváří služby, které ji implementují. Proto nelze změnit smlouvy o poskytování služeb po publikování, vykreslování efektivně neměnné. WCF podporuje dědičnost smlouvy, které lze použít k vytvoření nové smlouvy, která rozšiřuje stávající smlouvy. Chcete-li použít tuto funkci, definujte nové rozhraní servisní smlouvy, které dědí ze starého rozhraní servisní smlouvy, a pak přidejte metody do nového rozhraní. Potom změnit službu, která implementuje staré smlouvy k implementaci nové smlouvy a změnit definici koncového bodu "versionOld" použít novou smlouvu. Chcete-li "versionOld" klienty, koncový bod bude i nadále zobrazovat jako vystavení "versionOld" smlouvy; "versionNew" klientům, koncový bod se zobrazí vystavit "versionNew" smlouvy.  
  
## <a name="address-and-binding-versioning"></a>Správa verzí adres a vazeb  
 Změny adresy koncového bodu a vazby jsou narušující změny, pokud klienti jsou schopni dynamicky zjišťovat novou adresu koncového bodu nebo vazbu. Jedním z mechanismů pro implementaci této funkce je pomocí univerzální discovery popis a integrace (UDDI) registru a UDDI vyvolání vzor, kde se klient pokusí komunikovat s koncovým bodem a po selhání, dotazy známý UDDI aktuální metadata koncového bodu. Klient pak používá adresu a vazbu z tohoto metadatke komunikaci s koncovým bodem. Pokud je tato komunikace úspěšná, klient uloží adresu a informace o vazbě pro budoucí použití.  
  
## <a name="routing-service-and-versioning"></a>Služba směrování a správa verzí  
 Pokud změny provedené ve službě jsou narušující změny a je třeba mít dvě nebo více různých verzí služby spuštěné současně, můžete použít službu WCF Routing Service ke směrování zpráv do příslušné instance služby. Služba Směrování WCF používá směrování založené na obsahu, jinými slovy používá informace ve zprávě k určení, kam se má zpráva směrovat. Další informace o službě Směrování WCF naleznete v [tématu Routing Service](./feature-details/routing-service.md). Příklad použití služby WCF Routing Service pro správu verzí služby naleznete v [tématu How To: Service Versioning](./feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Příloha  
 Obecné pokyny pro správu verzí kontraktu dat, když je vyžadována přísná správa verzí, je považovat kontrakty dat za neměnné a vytvořit nové, když jsou požadovány změny. Pro každou novou datovou smlouvu je třeba vytvořit novou třídu, takže je potřeba mechanismus, aby nemuseli přijmout existující kód, který byl napsán z hlediska třídy staré smlouvy dat a přepsat ji z hlediska nové třídy smlouvy dat.  
  
 Jedním z takových mechanismů je použití rozhraní k definování členů každé smlouvy dat a zápisu vnitřního implementačního kódu z hlediska rozhraní, nikoli tříd y kontraktu dat, které implementují rozhraní. Následující kód pro verzi 1 služby `IPurchaseOrderV1` zobrazuje `PurchaseOrderV1`rozhraní a :  
  
```csharp  
public interface IPurchaseOrderV1  
{  
    string OrderId { get; set; }  
    string CustomerId { get; set; }  
}  
  
[DataContract(  
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2005/10/PurchaseOrder")]  
public class PurchaseOrderV1 : IPurchaseOrderV1  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
}  
```  
  
 Zatímco operace smlouvy o poskytování služeb by `PurchaseOrderV1`byly sepsány z hlediska `IPurchaseOrderV1`, skutečná obchodní logika by byla z hlediska . Pak ve verzi 2 by bylo `IPurchaseOrderV2` nové rozhraní `PurchaseOrderV2` a nové třídy, jak je znázorněno v následujícím kódu:  
  
```csharp
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}

[DataContract(
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 Smlouva o poskytování služeb by byla aktualizována tak, aby zahrnovala nové operace, které jsou napsány `PurchaseOrderV2`ve smyslu . Existující obchodní logika `IPurchaseOrderV1` napsaná v `PurchaseOrderV2` podmínkách by i `OrderDate` nadále pracovat pro `IPurchaseOrderV2`a nové obchodní logiky, která potřebuje vlastnost by být zapsány z hlediska .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Ekvivalence kontraktů dat](./feature-details/data-contract-equivalence.md)
- [Zpětná volání serializace tolerantní k verzím](./feature-details/version-tolerant-serialization-callbacks.md)
