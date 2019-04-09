---
title: Verze služby
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: 27d54cdf6f49bd9433f43290c97706af81d98b6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122405"
---
# <a name="service-versioning"></a>Verze služby
Po počátečním nasazení a potenciálně několikrát během jejich životního cyklu služeb (a koncové body, které, která zpřístupňují) potřebovat změnit pro celou řadu důvodů, jako je například změna obchodních potřeb, požadavků informačních technologií, nebo jiné řešení problémy. Každá změna zavádí novou verzi služby. Toto téma vysvětluje, jak vzít v úvahu správy verzí Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Čtyři kategorie změny služby  
 Změny služeb, které může být vyžadováno, je možné rozdělit do čtyř kategorií:  
  
-   Změny smlouvy: Například operace, které mohou být přidány nebo datový prvek ve zprávě mohou přidat nebo změnit.  
  
-   Vyřešení změn: Například služba přesune do jiného umístění, kde mají nové adresy koncových bodů.  
  
-   Vazba změny: Třeba změny zabezpečení mechanismus nebo změnit její nastavení.  
  
-   Provádění změn: Například interní metoda implementaci změny.  
  
 Některé z těchto změn se používá označení "slov" a jiné jsou "Pevná". Změna je *pevná* Pokud jsou v nové verzi úspěšně zpracovala všechny zprávy, které by byly zpracovány úspěšně v předchozí verzi. Je každá změna, která splňuje toto kritérium *zásadní* změnit.  
  
## <a name="service-orientation-and-versioning"></a>Orientaci na služby a správy verzí  
 Jedním z principů orientaci na služby je, že jsou služby a klienti autonomní (nebo nezávislé). Mimo jiné to znamená, že vývojáři služeb nelze předpokládat, že ovládací prvek nebo dokonce vědět o všech klientech služby. Tím se eliminuje možnost znovu sestavovat a nasazovat všichni klienti, když service změny verze. Toto téma předpokládá služba používá tato zásada a proto musí být změněné nebo "verze" bez ohledu na jeho klienty.  
  
 V případech, kdy k zásadní změně neočekávaný a nejde se vyhnout může aplikace rozhodnout Ignorovat tento princip a vyžaduje, aby se klienti znovu sestavit a znovu nasadit novou verzi služby.  
  
## <a name="contract-versioning"></a>Správa verzí kontraktů  
 Kontrakty používaný klientem nemusí být stejný jako kontrakt používá služba; potřebují pouze aby byly kompatibilní.  
  
 Pro servisní smlouvy kompatibilita znamená, že nové operace vystavené služby je možné přidat, ale stávající operace nelze odebrat nebo změnit sémanticky.  
  
 Pro datové kontrakty kompatibilita znamená, že nový typ schématu, které je možné přidat definice, ale existující definice typů schématu nelze změnit selhání způsoby. Rozbíjející změny mohou zahrnovat datové členy odstranění nebo změna datového typu konstrukce. Tato funkce umožňuje službě některé šířky při změně verze smlouvy bez narušení klientů. Pevná a blokuje změny, které lze provést k WCF data a služby v následujících dvou částech.  
  
## <a name="data-contract-versioning"></a>Správa verzí kontraktů dat  
 Tato část se zabývá Správa verzí dat při použití <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute> třídy.  
  
### <a name="strict-versioning"></a>Striktní správy verzí  
 V mnoha situacích při změně verze představuje problém, vývojářské služby nemá kontrolu nad klienty a proto nelze vytvářet předpoklady o tom, jak bude reagovat na změny ve zprávě, XML nebo schéma. V těchto případech je nutné zaručit, že nové zprávy budou ověřovat proti staré schématu dvou důvodů:  
  
-   Staré klienty byly vyvinuty s předpokladem, že nedojde ke změně schématu. Nemusí se jim podařit zpracovávat zprávy, které nikdy byly navrženy pro.  
  
-   Staré klienti mohou provádět ověřování skutečné schématu pro staré schématu před i pokusem o zpracování zpráv.  
  
 V takových scénářích doporučuje považovat za stávající smlouvy dat neměnné a vytvořit nové jedinečné XML kvalifikované názvy. Vývojářem služeb by pak přidejte nové metody do existující kontrakt služby nebo vytvořit nové kontrakt služby s metodami, které používají nové smlouvy data.  
  
 Často se bude v případě, kterou je potřeba napsat spustí nějakou obchodní logiku, která se má spustit ve všech verzích kontraktu dat a business specifické pro verzi kódu pro jednotlivé verze kontraktu dat pro vývojáře služby. Dodatku na konci tohoto tématu vysvětluje, jak lze pomocí rozhraní splnění tohoto požadavku.  
  
### <a name="lax-versioning"></a>Lax správy verzí  
 V mnoha jiných scénářích může být vývojářem služeb za předpokladu, že přidání nového člena volitelné kontraktu dat nebudou porušovat existující klienty. To vyžaduje, aby služba pro vývojáře prozkoumat, jestli nejsou existující klienti provádí ověřování schématu a ignorují Neznámý datové členy. V těchto scénářích je možné využít výhod funkcí kontraktu dat pro přidání nové členy pevné způsobem. Vývojářské služby můžete provést tento předpoklad bez obav, pokud funkce kontraktu dat pro správu verzí, již byly použity pro první verzi této služby.  
  
 WCF, webových služeb ASP.NET a mnoho dalších webových služeb podpory zásobníky *lax správy verzí*: to znamená, že nevyvolají výjimky pro nové členy Neznámý datový v přijatá data.  
  
 Je snadné se omylem domnívat, že přidáte nového člena nebudou porušovat existující klienty. Pokud si nejste jistí, že všichni klienti zvládne lax správy verzí, doporučuje se postupujte podle pokynů striktní správy verzí a zpracovávat data smlouvy jako neměnné.  
  
 Podrobné pokyny pro lax a striktní Správa verzí kontraktů dat, naleznete v tématu [osvědčených postupů: Správa verzí kontraktů dat](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Rozlišování mezi typy rozhraní .NET a kontrakt dat  
 .NET třídy nebo struktury je možné promítnout jako smlouvy dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut třídy. Typ formátu .NET a jeho projekce kontraktu dat jsou dvě různé důležité. Je možné mít více typů .NET s stejný kontrakt projekce data. Tento rozdíl je zvláště užitečná v umožňuje změnit typ formátu .NET při zachování kontraktu předpokládané dat, a tím zachování kompatibility se stávající klienty i v tom smyslu striktní slova. Existují dvě věci, které byste měli dělat vždy zachovat tento rozdíl mezi .NET typu a data smlouvy:  
  
-   Zadejte <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> a <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. By měl vždycky zadat název a obor názvů váš kontraktu dat. aby typ formátu .NET název a obor názvů z vystaven kontrakt. Tímto způsobem, pokud se později rozhodnete změnit obor názvů .NET nebo zadejte název, kontrakt dat zůstává stejná.  
  
-   Zadejte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. By měl vždy zadejte název vaší datové členy zabránit vystaven kontrakt jména člena rozhraní .NET. Tímto způsobem, pokud se později rozhodnete, chcete-li změnit .NET název členu, váš kontraktu dat zůstává stejná.  
  
### <a name="changing-or-removing-members"></a>Změna nebo odebrání členů  
 Změna názvu nebo data typu člena nebo odebrání datových členů je k zásadní změně i v případě, že lax správy verzí je povolen. Pokud je to nutné, vytvořte nové smlouvy data.  
  
 Pokud kompatibility služby je důležitý, může být vezměte v úvahu ignoruje nepoužívaná data členů ve vašem kódu a nechat na místě. Pokud jsou rozdělení datový člen do více členů, můžete zvážit, že byste museli opustit existujícího člena v místě jako vlastnost, která můžete provést požadované rozdělení a opakované agregace pro klienty nižší úrovně (klientů, které nejsou upgradováni na nejnovější verzi).  
  
 Podobně změny název nebo obor názvů kontraktu dat jsou rozbíjející změny.  
  
### <a name="round-trips-of-unknown-data"></a>Opakované Neznámá Data  
 V některých případech je třeba "round-trip" Neznámý dat, který přichází od členů přidá nová verze. Například "versionNew" služba odesílá data s některými nově přidané členy klientovi "versionOld". Klient ignoruje nově přidaní členové při zpracování zprávy, ale opětovně odešle ke stejným datům, včetně nově přidaných členů zpět ke službě versionNew. Typický scénář pro toto je aktualizace dat, ve kterém se data načte ze služby, změnit a vrátí.  
  
 Pokud chcete povolit verzemi pro určitý typ, musí implementovat typ <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Rozhraní obsahuje jednu vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> , která vrací <xref:System.Runtime.Serialization.ExtensionDataObject> typu. Vlastnost se používá k ukládání dat v budoucích verzích kontraktu dat, který neznámý pro aktuální verzi. Tato data jsou neprůhledné klientovi, ale pokud je serializována instance, obsah <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost byl napsán s zbývající členů kontraktu dat data.  
  
 Doporučuje se, že všechny typy implementovat toto rozhraní tak, aby vyhovovaly nové a neznámé budoucích členů.  
  
### <a name="data-contract-libraries"></a>Knihovny kontraktu dat  
 Můžou existovat knihovny kontraktů dat kontrakt publikovaná v centrálním úložišti, kde služby a typ implementátory implementovat a vystavit kontraktů dat z tohoto úložiště. Když publikujete kontraktu dat do úložiště, v takovém případě máte žádnou kontrolu nad tím, kdo vytváří typy, které je implementují. Proto nemůžete upravovat kontrakt publikovaný produkt, vykreslování efektivně neměnné.  
  
### <a name="when-using-the-xmlserializer"></a>Při používání třídy XmlSerializer  
 Správa verzí stejné zásady platí i při použití <xref:System.Xml.Serialization.XmlSerializer> třídy. Když se vyžaduje striktní správy verzí, považovat za kontraktů dat neměnné a vytvořit nové kontrakty dat s jedinečný a kvalifikované názvy pro nové verze. Když jste si jisti, že lax správy verzí je možné, nejde přidat nové serializovatelné členy v nových verzích ale změnit nebo odebrat existující členy.  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> Používá <xref:System.Xml.Serialization.XmlAnyElementAttribute> a <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atributy pro podporu dopad na dobu odezvy neznámá data.  
  
## <a name="message-contract-versioning"></a>Správa verzí kontraktů zpráv  
 Pokyny pro Správa verzí kontraktů zpráv jsou velmi podobné kontraktů dat správy verzí. Pokud se vyžaduje striktní správy verzí, by měl nezměníte vaše zprávy, ale místo vytvoření nové zprávy kontraktu s jedinečný kvalifikovaný název. Pokud víte, které můžete použít lax správy verzí, nejde přidat nové části textu zprávy, ale změnit nebo odebrat existující aplikace. Tento návod se vztahuje i na úplné a zabalené kontraktů zpráv.  
  
 Záhlaví zprávy mohou být přidány vždy, i v případě, že striktní správy verzí je používána. Příznak MustUnderstand může mít vliv na správu verzí. Model správy verzí pro záhlaví ve službě WCF je obecně platí, jak je popsáno ve specifikaci protokolu SOAP.  
  
## <a name="service-contract-versioning"></a>Správa verzí kontraktů služby  
 Podobně jako správa verzí kontraktů dat, Správa verzí kontraktů služby také zahrnuje přidání, změně a odebrání operace.  
  
### <a name="specifying-name-namespace-and-action"></a>Zadáním názvu, Namespace a akce  
 Název kontraktu služby ve výchozím nastavení, je název rozhraní. Výchozí obor názvů je "http://tempuri.org", a akce pro každou operaci "http://tempuri.org/contractname/methodname". Doporučuje se explicitně zadat název a obor názvů kontraktu služby a akce pro každou operaci, abyste se vyhnuli použití "http://tempuri.org" a zabránit názvy rozhraní a metoda vystaven v kontraktu služby.  
  
### <a name="adding-parameters-and-operations"></a>Přidání operace a parametry  
 Přidání operace služby, vystavený službou je méně zásadních změn, protože existující klienti nemusí mít obavy o těchto nových operací.  
  
> [!NOTE]
>  Přidání operací do duplexního zpětného volání kontraktu je zásadní změnu.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Změna parametrů operace nebo návratové typy  
 Změna parametrů nebo návratových typů obecně je rozbíjející změny, pokud nový typ implementuje stejné kontraktu dat pomocí starého typu implementovat. Chcete-li tuto změnu, přidat nové operace pro kontrakt služby nebo definujte nové kontrakt služby.  
  
### <a name="removing-operations"></a>Odebírá se operace  
 Odebrání operace je také k narušující změně. Chcete-li tuto změnu, definujte nové kontrakt služby a zveřejníte ho na nový koncový bod.  
  
### <a name="fault-contracts"></a>Kontrakty selhání  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut umožňuje vývojář smlouvy k zadání informací o chybách, které mohou být vráceny z operace kontraktu.  
  
 Seznam chyb je popsáno v kontraktu služby se nepovažuje za vyčerpávající. V každém okamžiku může vrátit operace chyb, které nebyly popsány v její smlouvy. Proto změna sady chyb je popsáno v kontraktu není považováno za rozbíjející. Například přidáním nové chyby pomocí kontraktu <xref:System.ServiceModel.FaultContractAttribute> nebo odebrání existující chybu ze smlouvy.  
  
### <a name="service-contract-libraries"></a>Knihovny kontrakt služby  
 Organizace mohou mít knihovny kontraktů kde kontrakt publikovaná v centrálním úložišti a implementátoři služby implementace kontraktů z tohoto úložiště. Když publikujete kontraktu služby do úložiště v tomto případě máte žádnou kontrolu nad tím, kdo vytváří služby, které je implementují. Proto nelze upravit smlouvu, jakmile ji publikujete, vykreslování efektivně neměnné. WCF podporuje Dědičnost kontraktů, který slouží k vytvoření nové smlouvy, která rozšiřuje stávající smlouvy. Pokud chcete používat tuto funkci, definujte nové rozhraní kontraktu služby, která dědí ze staré rozhraní kontraktu služby a pak přidejte metody na nové rozhraní. Potom změňte službu, která implementuje starého kontraktu implementovat nové smlouvy a změnit definice koncového bodu "versionOld" používat nové smlouvy. Klientům "versionOld" budou se nadále zobrazovat jako zpřístupňuje "versionOld" smlouvy; koncový bod klientům "versionNew" zobrazí se na koncový bod ke zveřejnění kontraktu "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Adresy a vazby správy verzí  
 Změny adresa koncového bodu a vazby jsou rozbíjející změny, pokud klienti nejsou schopné dynamicky zjišťování na novou adresu koncového bodu nebo vazby. Jeden mechanismus pro implementaci této funkce je pomocí registru univerzální popis zjišťování a integrace (UDDI) a vzor vyvolání UDDI, kde klient se pokouší navázat komunikaci s koncovým bodem a, nebude úspěšná, dotazuje dobře známé UDDI registr pro aktuální koncový bod metadat. Klient potom použije adresu a vazbu z těchto metadat ke komunikaci s koncovým bodem. Pokud je tato komunikace úspěšná, klient ukládá do mezipaměti informace o adrese a vazbu pro budoucí použití.  
  
## <a name="routing-service-and-versioning"></a>Služba Směrování a správa verzí  
 Pokud změny do služby jsou zásadní změny a musí mít minimálně dva různé verze služby spuštěné současně můžete směrovací služba WCF pro směrování zpráv do instance příslušnou službu. Směrovací služba WCF používá směrování na základě obsahu, jinými slovy, používá informace v něm k určení, kam chcete směrovat zprávy. Další informace o směrování služby WCF najdete v tématu [směrovací služba](../../../docs/framework/wcf/feature-details/routing-service.md). Příklad použití směrovací služba WCF pro správu verzí služby najdete v části [How To: Správa verzí služby](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Příloha  
 Pokyny správy verzí kontraktu obecná data v případě potřeby striktní správy verzí je považovat za neměnné kontraktech dat a vytvářet nové, když nejsou nutné nějaké změny. Nová třída je potřeba vytvořit pro každou novou kontraktu dat, takže mechanismus je potřeba, abyste nemuseli vzít existující kód, který byl napsán z hlediska stará data smlouvy třídy a přepsat jde o novou třídu kontraktu dat.  
  
 Jedním z takových mechanismů je pomocí rozhraní definují členy jednotlivých kontraktu dat a okamžitý zápis vnitřní implementace kódu z hlediska rozhraní spíše než třídy kontraktu dat, které implementují rozhraní. Následující kód pro verzi 1 služby ukazuje `IPurchaseOrderV1` rozhraní a `PurchaseOrderV1`:  
  
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
  
 Během operace kontraktu služby by byla zapsána z hlediska `PurchaseOrderV1`, skutečné obchodní logika by být z hlediska `IPurchaseOrderV1`. Potom ve verzi 2, bude nový `IPurchaseOrderV2` rozhraní a nový `PurchaseOrderV2` třídy, jak je znázorněno v následujícím kódu:  
  
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
  
 Kontrakt služby bude aktualizováno, aby zahrnovalo nové operace, které jsou napsány z hlediska `PurchaseOrderV2`. Stávající obchodní logiky zapisovat z hlediska `IPurchaseOrderV1` by pokračovat v práci pro `PurchaseOrderV2` a nové obchodní logiky, které potřebuje `OrderDate` vlastnost by byla zapsána z hlediska `IPurchaseOrderV2`.  
  
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
