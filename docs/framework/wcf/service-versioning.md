---
title: Verze služby
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: f3cb01531c594df5262963567438b47cbbed58a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923020"
---
# <a name="service-versioning"></a>Verze služby
Po počátečním nasazení a potenciálně delší dobu během své životnosti, služeb (a koncových bodů, které zveřejňuje) může být potřeba změnit z nejrůznějších důvodů, jako jsou třeba změny obchodních potřeb, požadavky na informační technologie nebo jiné adresy Chyba. Každá změna zavádí novou verzi služby. Toto téma vysvětluje, jak zvážit správu verzí v Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Čtyři kategorie změn služby  
 Změny služeb, které mohou být požadovány, lze klasifikovat do čtyř kategorií:  
  
- Změny kontraktu: Například může být přidána operace, nebo je možné přidat nebo změnit datový prvek ve zprávě.  
  
- Změny adresy: Například služba se přesune na jiné místo, kde koncové body mají nové adresy.  
  
- Změny vazeb: Například změna mechanismu zabezpečení nebo změny nastavení.  
  
- Změny implementace: Například při změně implementace interní metody.  
  
 Některé z těchto změn se nazývají "přerušení" a jiné jsou "nerozdělitelné". Změna je nepřerušená, pokud se všechny zprávy, které by byly úspěšně zpracovány v předchozí verzi, úspěšně zpracovaly v nové verzi. Jakékoli změny, které nesplňují toto kritérium, jsou zásadní změnou.  
  
## <a name="service-orientation-and-versioning"></a>Orientace služby a správa verzí  
 Jednou z principyí služby je, že služby a klienti jsou autonomní (nebo nezávislé). Mimo jiné to znamená, že vývojáři služeb nemůžou předpokládat, že ovládají nebo dokonce znají informace o všech klientech služeb. Tím se eliminuje možnost opětovného sestavení a opětovného nasazení všech klientů, když služba změní verze. Toto téma předpokládá, že služba dodržuje tyto principem, a proto musí být změněna nebo "se správou" verzí nezávisle na svých klientech.  
  
 V případech, kdy je zásadní změna neočekávaná a nelze se jí vyhnout, může aplikace zvolit ignorování tohoto principem a vyžadovat, aby klienti znovu vytvořili a nasadili novou verzi služby.  
  
## <a name="contract-versioning"></a>Správa verzí kontraktů  
 Smlouvy používané klientem nemusí být stejné jako kontrakt používaný službou. potřebují být jenom kompatibilní.  
  
 Pro kontrakty služeb se dá přidat nové operace vystavené službou, ale existující operace se nedají odebrat ani změnit sémanticky.  
  
 U kontraktů dat se dají přidat nové definice typu schématu, ale existující definice typu schématu se nedají změnit rozlomeným způsobem. Průlomové změny můžou zahrnovat odebrání datových členů nebo změnu jejich datového typu konstrukce. Tato funkce umožňuje službě určitou zeměpisnou šířku při změně verze svých smluv bez přerušujících klientů. Následující dvě části vysvětlují nepřerušené a zásadní změny, které je možné provést na data WCF a kontrakty služby.  
  
## <a name="data-contract-versioning"></a>Správa verzí kontraktů dat  
 Tato část se zabývá používáním správy verzí dat při <xref:System.Runtime.Serialization.DataContractSerializer> použití <xref:System.Runtime.Serialization.DataContractAttribute> tříd a.  
  
### <a name="strict-versioning"></a>Striktní verze  
 V mnoha scénářích, kdy dochází k potížím s změnou verzí, vývojář služby nemá kontrolu nad klienty, a proto nemůže vytvořit předpoklady, jak by mohly reagovat na změny ve zprávě XML nebo schématu. V těchto případech je potřeba zaručit, že se nové zprávy ověřují oproti starému schématu, a to z těchto důvodů:  
  
- Původní klienti byli vyvinuti s předpokladem, že se schéma nezmění. Nemusí podařit zpracovat zprávy, pro které nebyly nikdy navrženy.  
  
- Starší klienti mohou provádět skutečné ověření schématu proti původnímu schématu před tím, než se bude pokoušet o zpracování zpráv.  
  
 Doporučený postup v takových scénářích je považovat stávající kontrakty dat za neměnné a vytvořit nové s jedinečnými názvy XML kvalifikovaných názvů. Vývojář služby by pak buď přidal nové metody do existující smlouvy o službě, nebo vytvořil novou kontrakt služby s metodami, které používají novou kontrakt dat.  
  
 Často se jedná o případ, kdy vývojář služby potřebuje napsat nějakou obchodní logiku, která by se měla spustit ve všech verzích kontraktu dat a obchodním kódem specifickém pro každou verzi kontraktu dat. Příloha na konci tohoto tématu vysvětluje, jak lze použít rozhraní pro splnění této potřeby.  
  
### <a name="lax-versioning"></a>Správa verzí LAX  
 V mnoha dalších scénářích může vývojář služby provést předpoklad, že přidání nového volitelného člena do kontraktu dat nebude rušit stávající klienty. To vyžaduje, aby vývojář služby zkontroloval, jestli stávající klienti neprováděli ověřování schématu a jestli ignorují neznámé datové členy. V těchto scénářích je možné využít výhod funkcí kontraktu dat pro přidání nových členů do nepřerušeného způsobu. Vývojář služby může tento předpoklad s jistotou provést, pokud byly funkce kontraktů dat pro správu verzí pro první verzi služby již použity.  
  
 WCF, webové služby ASP.NET a mnoho dalších zásobníků webových služeb podporují *správu verzí LAX*: to znamená, že nevyvolávají výjimky pro nové neznámé datové členy v přijatých datech.  
  
 Nemusíte se snadno domnívat, že přidáním nového člena nedojde k přerušení stávajících klientů. Pokud si nejste jistí, že všichni klienti můžou zpracovávat správu verzí Lax, doporučuje se používat přísné pokyny pro správu verzí a považovat kontrakty dat za neměnné.  
  
 Podrobné pokyny pro LAX i striktní správu kontraktů dat najdete v tématu [osvědčené postupy: Správa verzí](../../../docs/framework/wcf/best-practices-data-contract-versioning.md)kontraktů dat  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Odlišení mezi kontraktem dat a typy .NET  
 Třídu nebo strukturu .NET lze projektovat jako kontrakt <xref:System.Runtime.Serialization.DataContractAttribute> dat použitím atributu na třídu. Typ .NET a jeho výčnělky mají dva různé věci. Je možné mít více typů .NET se stejnou projekcí kontraktu dat. Toto rozlišení je zvlášť užitečné v případě, že vám umožní změnit typ .NET při zachování kontraktu s plánovanými daty, což zachovává kompatibilitu se stávajícími klienty i v přísném smyslu slova. Existují dvě věci, které byste měli vždycky udělat, abyste zachovali toto rozlišení mezi typem .NET a kontraktem dat:  
  
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> Zadejte a .<xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> Vždy byste měli zadat název a obor názvů kontraktu dat, abyste zabránili zveřejnění názvu a oboru názvů .NET typu v kontraktu. Tímto způsobem se rozhodnete, že pokud později změníte obor názvů nebo název typu .NET, váš kontrakt dat zůstane stejný.  
  
- Zadejte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Vždy byste měli zadat název svých datových členů, abyste zabránili zveřejnění názvu člena .NET v kontraktu. Tímto způsobem se rozhodnete, že pokud se později rozhodnete změnit název .NET člena, váš kontrakt dat zůstane stejný.  
  
### <a name="changing-or-removing-members"></a>Změna nebo odebrání členů  
 Změna názvu nebo datového typu člena nebo odebrání datových členů je zásadní změnou, i když je povolená Správa verzí Lax. Pokud je to nezbytné, vytvořte novou kontrakt dat.  
  
 Pokud je Kompatibilita služby Vysoká důležitost, může být vhodné ignorovat nepoužívané datové členy ve vašem kódu a nechat je na místě. Pokud rozdělíte datový člen na více členů, můžete zvážit, že stávající člen je v místě jako vlastnost, která může provádět požadované rozdělení a opětovné agregace pro klienty nižší úrovně (klienti, kteří nejsou upgradováni na nejnovější verzi).  
  
 Podobně se změny v názvu nebo oboru názvů kontraktu dat mění.  
  
### <a name="round-trips-of-unknown-data"></a>Zpáteční cesty neznámých dat  
 V některých scénářích je potřeba "zpáteční trip" neznámá data, která pocházejí od členů přidaných v nové verzi. Například služba "versionNew" odesílá data s některými nově přidanými členy do klienta "versionOld". Klient při zpracování zprávy ignoruje nově přidané členy, ale znovu odešle stejná data, včetně nově přidaných členů, zpátky do služby versionNew. Typický scénář pro toto je aktualizace dat, kde se data načítají ze služby, která se změnila a vrátí.  
  
 Chcete-li povolit příkaz round-trip pro konkrétní typ, musí tento typ <xref:System.Runtime.Serialization.IExtensibleDataObject> implementovat rozhraní. Rozhraní obsahuje jednu vlastnost, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> která <xref:System.Runtime.Serialization.ExtensionDataObject> vrací typ. Vlastnost se používá k uložení jakýchkoli dat z budoucích verzí kontraktu dat, který není aktuální verzí znám. Tato data jsou neprůhledná pro klienta, ale při serializaci instance se obsah <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnosti zapisuje se zbytkem dat členů kontraktu dat.  
  
 Doporučuje se, aby všechny typy implementovaly toto rozhraní tak, aby vyhovovalo novým a neznámým budoucím členům.  
  
### <a name="data-contract-libraries"></a>Knihovny datových kontraktů  
 Mohou existovat knihovny kontraktů dat, ve kterých je smlouva publikována v centrálním úložišti, a implementace služeb a typů implementuje a zveřejňuje kontrakty dat z daného úložiště. V takovém případě, když publikujete kontrakt dat do úložiště, nemáte žádnou kontrolu nad tím, kdo vytvoří typy, které ji implementují. Proto nemůžete smlouvu po publikování změnit, takže její vynechání je efektivně neměnné.  
  
### <a name="when-using-the-xmlserializer"></a>Při použití objektu XmlSerializer  
 Stejné zásady správy verzí platí při použití <xref:System.Xml.Serialization.XmlSerializer> třídy. Když je potřeba striktní Správa verzí, považovat kontrakty dat za neměnné a vytvoří nové kontrakty dat s jedinečnými a kvalifikovanými názvy pro nové verze. Pokud jste si jisti, že je možné použít správu verzí Lax, můžete přidat nové serializovatelné členy v nových verzích, ale ne měnit nebo odebírat stávající členy.  
  
> [!NOTE]
> Používá atributy a<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>pro podporu kulatých Trip neznámých dat. <xref:System.Xml.Serialization.XmlAnyElementAttribute> <xref:System.Xml.Serialization.XmlSerializer>  
  
## <a name="message-contract-versioning"></a>Správa verzí kontraktů zpráv  
 Pokyny pro správu verzí kontraktů zpráv jsou velmi podobné kontraktům s daty správy verzí. Pokud je potřeba striktní Správa verzí, neměli byste měnit text zprávy, ale místo toho můžete vytvořit nový kontrakt zprávy s jedinečným kvalifikovaným názvem. Pokud víte, že můžete použít správu verzí Lax, můžete přidat nové části těla zprávy, ale nemůžete je změnit nebo odebrat. Tento návod platí pro smlouvy se zabalením a zabaleného hlášení.  
  
 Záhlaví zpráv může být vždy přidáno i v případě, že se používá striktní Správa verzí. Příznak MustUnderstand může mít vliv na správu verzí. Obecně platí, že model správy verzí pro hlavičky v rámci WCF je jak je popsáno ve specifikaci SOAP.  
  
## <a name="service-contract-versioning"></a>Správa verzí kontraktů služeb  
 Podobně jako správa verzí kontraktů dat zahrnuje také operace přidávání, změny a odebírání operací služby.  
  
### <a name="specifying-name-namespace-and-action"></a>Zadání názvu, oboru názvů a akce  
 Ve výchozím nastavení je název kontraktu služby název rozhraní. Jeho výchozí obor názvů je http://tempuri.org "" a akce každé operace http://tempuri.org/contractname/methodname je "". Doporučuje se explicitně zadat název a obor názvů pro kontrakt služby a akci pro každou operaci vyhnout používání http://tempuri.org příkazu "" a zabránit zveřejnění názvů rozhraní a metod v kontraktu služby.  
  
### <a name="adding-parameters-and-operations"></a>Přidání parametrů a operací  
 Přidání operací služby vystavených službou je nepřerušená změna, protože stávající klienti nemusí být o těchto nových operacích zajisti.  
  
> [!NOTE]
> Přidávání operací do duplexního kontraktu zpětného volání je zásadní změna.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Mění se parametry operace nebo návratové typy.  
 Změna parametrů nebo návratových typů obecně představuje zásadní změnu, pokud nový typ neimplementuje stejný kontrakt dat implementovaný starým typem. Chcete-li takovou změnu provést, přidejte novou operaci do kontraktu služby nebo Definujte novou kontrakt služby.  
  
### <a name="removing-operations"></a>Odebírání operací  
 Odebírání operací je také zásadní změna. Pokud chcete takovou změnu udělat, definujte novou kontrakt služby a zpřístupněte ji na novém koncovém bodu.  
  
### <a name="fault-contracts"></a>Smlouvy o selhání  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut umožňuje vývojářům kontraktu služby zadat informace o chybách, které mohou být vráceny z operací smlouvy.  
  
 Seznam chyb popsaných v kontraktu služby není považován za vyčerpávající. Operace může kdykoli vracet chyby, které nejsou popsány ve smlouvě. Proto se změna množiny chyb popsaných ve smlouvě nepovažuje za přerušení. Přidejte například novou chybu ke smlouvě pomocí <xref:System.ServiceModel.FaultContractAttribute> nebo odeberte existující chybu ze smlouvy.  
  
### <a name="service-contract-libraries"></a>Knihovny kontraktů služeb  
 Organizace mohou mít knihovny smluv, kde je smlouva publikována v centrálním úložišti, a implementátori služeb implementují smlouvy z tohoto úložiště. Pokud v takovém případě publikujete kontrakt služby do úložiště, nebudete mít kontrolu nad tím, kdo vytvoří služby, které ji implementují. Proto nemůžete po publikování změnit kontrakt služby, protože ho bude efektivně neproměnlivý. WCF podporuje dědičnost kontraktu, která se dá použít k vytvoření nové smlouvy, která rozšiřuje stávající smlouvy. Chcete-li použít tuto funkci, definujte nové rozhraní kontraktu služby, které dědí z původního rozhraní kontraktu služby, a poté přidejte do nového rozhraní metody. Pak změníte službu, která implementuje starou smlouvu pro implementaci nové smlouvy, a změňte definici koncového bodu "versionOld" tak, aby používala nový kontrakt. U klientů "versionOld" se koncový bod bude i nadále zobrazovat jako vystavení kontraktu "versionOld"; pro klienty "versionNew" se zobrazí koncový bod pro vystavení kontraktu "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Správa verzí adres a vazeb  
 Změny adresy a vazby koncového bodu jsou zásadní, pokud klienti nemůžou dynamicky zjišťovat novou adresu nebo vazbu nového koncového bodu. Jedním z mechanismů pro implementaci této funkce je použití registru popisu a integrace univerzálního zjišťování a způsobu vyvolání služby UDDI, když se klient pokusí komunikovat s koncovým bodem a při selhání se dotazuje na dobře známou službu UDDI. registr pro aktuální metadata koncového bodu Klient pak použije adresu a vazbu z těchto metadat ke komunikaci s koncovým bodem. Pokud je tato komunikace úspěšná, klient uloží adresu a informace o vazbě pro budoucí použití.  
  
## <a name="routing-service-and-versioning"></a>Směrovací služba a správa verzí  
 Pokud změny provedené ve službě přerušují změny a potřebujete mít dvě nebo víc různých verzí služby spuštěných současně, můžete použít směrovací službu WCF ke směrování zpráv do příslušné instance služby. Směrovací služba WCF používá směrování na základě obsahu, jinak řečeno, používá informace v rámci zprávy k určení, kam zprávu směrovat. Další informace o směrovací službě WCF najdete v tématu [Služba směrování](../../../docs/framework/wcf/feature-details/routing-service.md). Příklad toho, jak používat směrovací službu WCF pro správu verzí služby, najdete v tématu [How to: Verze](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)služby.  
  
## <a name="appendix"></a>Příloha  
 Obecné pokyny k vytváření verzí kontraktů dat v případě, že je potřeba striktní Správa verzí, je zacházet s tím, že se kontrakty dat při nutnosti změny nemění a vytvářejí nové. Pro každou novou kontrakt dat je třeba vytvořit novou třídu, proto je třeba zajistit, aby se zabránilo nutnosti přecházet existující kód, který byl napsán z hlediska staré třídy kontraktu dat, a přepsat jej z hlediska nové třídy kontraktu dat.  
  
 Jedním z těchto mechanismů je použití rozhraní k definování členů jednotlivých kontraktů dat a zápis interního implementačního kódu z podmínek rozhraní, nikoli tříd kontraktů dat, které implementují rozhraní. Následující kód pro verzi 1 služby zobrazuje `IPurchaseOrderV1` rozhraní `PurchaseOrderV1`a:  
  
```  
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
  
 I když by se operace kontraktu služby napsaly na `PurchaseOrderV1`základě, je skutečná obchodní logika z `IPurchaseOrderV1`pohledu. Pak, ve verzi 2, by bylo nové `IPurchaseOrderV2` rozhraní a nová `PurchaseOrderV2` třída, jak je znázorněno v následujícím kódu:  
  
```  
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
  
 Servisní smlouva by se aktualizovala tak, aby zahrnovala nové operace, které jsou `PurchaseOrderV2`zapsané ve smyslu. Existující obchodní logika vytvořená v souvislosti `IPurchaseOrderV1` s tím `OrderDate` bude i nadále `PurchaseOrderV2` fungovat pro a nová obchodní logika, která potřebuje vlastnost, bude zapsána v souvislosti s `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Viz také:

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
- [Ekvivalence kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Zpětná volání serializace tolerantní k verzím](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
