---
title: "Verze služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 791e201907f72f9d590f6d835fd6ec1bfc25633f
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="service-versioning"></a>Verze služby
Po počátečním nasazení a potenciálně několikrát během své životnosti může potřebovat služby (a koncových bodů, které vystavují) se musí změnit z různých důvodů, jako je například změna obchodních potřeb, požadavků informačních technologií, nebo k jiné řešení problémy. Každé změně zavádí novou verzi služby. Toto téma vysvětluje, jak vzít v úvahu správu verzí v [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="four-categories-of-service-changes"></a>Čtyř kategorií změny služby  
 Změny služby, které mohou být vyžadovány lze rozdělit do několika kategorií:  
  
-   Sbalit změny: například operace, které mohou být přidány nebo datový prvek ve zprávě může přidat nebo změnit.  
  
-   Adresa změny: například služby přesune do jiného umístění, kde koncové body mají nové adresy.  
  
-   Vazba změny: například změní mechanismus zabezpečení nebo změnit jeho nastavení.  
  
-   Implementace změny: při implementaci interní metoda například změní.  
  
 Mezi tyto změny se používá označení "ukončování" a jiné jsou "Pevná". Je změna *pevných* Pokud jsou v nové verzi úspěšně zpracovala všechny zprávy, které by byly zpracovány úspěšně v předchozí verzi. Všechny změny, který nesplňuje splnění tohoto kritéria se *nejnovější* změnit.  
  
## <a name="service-orientation-and-versioning"></a>Orientaci na služby a správa verzí  
 Jedním z principů orientaci na služby je, že jsou služby a klienti autonomního (nebo nezávislé). Kromě jiných věcí to znamená, že vývojáři služeb nelze předpokládat, že řízení nebo i vědět o všech klientech služby. Tím se eliminuje možnost znovu sestavit a znovu nasazovat všichni klienti, když service změny verze. Toto téma předpokládá službu dodržuje tento principem a proto musí být změněné nebo "verzí" bez ohledu na jeho klienty.  
  
 V případě narušující změně neočekávaná a se nelze vyhnout spojení aplikace rozhodnout ignorovat tuto principem a vyžadovat, klienty znovu sestavit a znovu nasadit s novou verzí služby.  
  
## <a name="contract-versioning"></a>Správa verzí kontraktů  
 Kontrakty používaný klientem nemusí být stejný jako kontrakt, který používá služba; potřebují pouze, aby byla kompatibilní.  
  
 Pro kontraktů služby kompatibility přidáním nových operací znamená vystavený službou, ale existující operace nelze odebrat nebo změnit sémanticky.  
  
 Pro datové kontrakty kompatibilita znamená nový typ schématu, které lze přidat definice ale existující definice typu schématu nelze změnit v nejnovější způsoby. Nejnovější změny mohou zahrnovat odebrání datových členů nebo incompatibly Změna datového typu. Tato funkce umožňuje službě některé zeměpisnou šířku při změně verze jeho kontrakty, aniž by vás klientů. V následujících dvou oddílech se popisuje pevná a dodatečné změny, které můžete provedeny [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kontraktů dat a služby.  
  
## <a name="data-contract-versioning"></a>Správa verzí kontraktů dat  
 Tato část pojednává o Správa verzí dat při použití <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute> třídy.  
  
### <a name="strict-versioning"></a>Striktní Správa verzí  
 V mnoha scénářích při změně verze je nějaký problém, developer služby nemá kontrolu nad klienty a proto nelze provést, předpoklady o tom, jak bude reagovat na změny ve zprávě XML nebo schéma. V těchto případech musí zaručit, že bude nové zprávy ověření pro původní schéma, dvou důvodů:  
  
-   Původní klienty byly vyvinuty s za předpokladu, že nedojde ke změně schématu. Může se nepodaří zpracovat zprávy, které nebyly nikdy nebyl navržený pro.  
  
-   Původní klienti mohou provádět skutečné schéma ověřování pro původní schéma před i pokusu o zpracování zprávy.  
  
 Doporučený přístup v takových případech je považovat za existující kontrakty dat neměnné a vytvořit nové položky obsahující jedinečný XML kvalifikované názvy. Vývojář služby by pak buď přidejte nové metody existující servisní smlouvou nebo vytvořit nový kontrakt služby s metodami, které používají nové kontrakt dat.  
  
 Často bude případě, že vývojář služby potřebuje k zápisu některé obchodní logiky, která by měla spustit ve všech verzích kontrakt dat plus specifické pro verzi obchodní kód pro každou verzi kontrakt dat. Příloha na konci tohoto tématu vysvětluje, jak lze pomocí rozhraní splnění tohoto požadavku.  
  
### <a name="lax-versioning"></a>Hodnotě lax Správa verzí  
 V mnoha jiných scénářích vývojáře služby můžete provést za předpokladu, že přidání nové, volitelné člena do kontrakt dat nebudou porušovat existující klienti. To vyžaduje, aby služba vývojáři prozkoumat, jestli existující klienti nejsou provádění ověřování schématu a s jejich ignorovat členy dat je neznámý. V těchto scénářích je možné využít výhod funkce kontraktu dat pro přidání nové členy pevných způsobem. Vývojář služby mohou být tento předpoklad s jistotou, pokud funkce kontraktu dat pro správu verzí, již byly použity pro první verzi služby.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], Webových služeb ASP.NET a mnoho dalších podpora webové služby zásobníky *hodnotě lax Správa verzí*: to znamená, že nevyvolá výjimku výjimky pro nové členy dat je neznámý v přijatá data.  
  
 Je snadné se omylem domnívat, že přidání nového člena nebudou porušovat existující klienti. Pokud si nejste jistí, že všichni klienti dokáže zpracovat hodnotě lax Správa verzí, doporučuje se považovat data a postupujte podle pokynů striktní Správa verzí kontraktů jako neměnné.  
  
 Podrobné pokyny k hodnotě lax a striktní Správa verzí kontraktů dat najdete v části [osvědčené postupy: Správa verzí kontraktů dat](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Rozlišit kontrakt dat a typů .NET  
 Rozhraní .NET třídu nebo strukturu můžete použít k projekci jako kontraktu dat s použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut třídy. Typ formátu .NET a její projekce kontraktu dat jsou dvě odlišné záleží. Je možné, že více typů .NET s stejné projekce kontrakt data. Tento rozdíl je obzvláště užitečná při umožňuje změnit typ formátu .NET při zachování kontrakt předpokládané dat, a tím zachování kompatibility s existující klienty i v tom smyslu striktní aplikace word. Existují dvě věci, které byste měli vždy udělat udržovat tento rozdíl mezi kontrakt .NET typu a data:  
  
-   Zadejte <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> a <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Musíte vždycky zadat název a obor názvů vaší kontrakt dat, aby se zabránilo typ formátu .NET název oboru názvů vystavení v kontraktu. Tímto způsobem, pokud se později rozhodnete změnit obor názvů .NET nebo zadejte název, kontrakt dat se nezmění.  
  
-   Zadejte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Musíte vždycky zadat název datových členů, aby název člena .NET vystavení v kontraktu. Tímto způsobem, pokud se rozhodnete později změnit název .NET člena, vaše kontrakt dat se nezmění.  
  
### <a name="changing-or-removing-members"></a>Změně nebo odebrání členů  
 Změna názvu nebo datového typu člena nebo odebrání datových členů je i v případě, že je povoleno hodnotě lax Správa verzí narušující změně. Pokud je to nutné, vytvořte nové smlouvy data.  
  
 Pokud je služba kompatibility vysokou důležitost, můžete zvážit ignoruje nepoužívané datových členů v kódu a ponechejte je na místě. Pokud jsou rozdělení členem data do více členů, můžete zvážit, a existujícího člena v místě jako vlastnost, která lze provést požadované rozdělením a opakované agregaci pro klienty nižší úrovně (klientů, které nejsou upgradovány na nejnovější verzi).  
  
 Podobně platí jsou změny název nebo obor názvů kontraktu dat nejnovější změny.  
  
### <a name="round-trips-of-unknown-data"></a>Uložení dat je neznámý  
 V některých případech je potřeba "odezvy" Neznámý data, která pochází z členů přidaných v nové verzi. Například "versionNew" service odešle data pomocí některé nově přidat členy do klienta "versionOld". Klient ignoruje nově přidaných členů při zpracování zprávy, ale opětovně odešle tato data, včetně nově přidaných členů zpět ke službě versionNew. Typické scénáře je aktualizace dat, kde získaný ze služby, změnit a vrácená data.  
  
 Pokud chcete povolit odezvy pro určitý typ, musí typ implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Rozhraní obsahuje jednu vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> , který vrací <xref:System.Runtime.Serialization.ExtensionDataObject> typu. Vlastnost se používá k ukládání dat v budoucích verzích kontrakt dat, který neznámý na aktuální verzi. Tato data jsou neprůhledné klientovi, ale v případě, že instance je serializováno, obsah <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnosti zapisují se zbytkem datové kontrakt členy se data.  
  
 Doporučuje se, že všechny typy implementovat toto rozhraní pro uložení nové a neznámé budoucí členy.  
  
### <a name="data-contract-libraries"></a>Knihovny kontraktu dat  
 Může být knihovny kontraktů dat kontraktu je publikovaná v centrálním úložišti, kde služby a typ implementátory implementovat a vystavit kontrakty dat z tohoto úložiště. V takovém případě při publikování kontraktu dat do úložiště, nemáte žádnou kontrolu nad kdo vytvoří typy, které implementují ho. Proto se nedá změnit kontrakt po publikování, vykreslování efektivně neměnné.  
  
### <a name="when-using-the-xmlserializer"></a>Při používání třídy XmlSerializer  
 Při použití platí stejné zásady správy verzí <xref:System.Xml.Serialization.XmlSerializer> třídy. Pokud se vyžaduje striktní Správa verzí, považovat za kontrakty dat neměnné a vytvořte nové kontrakty dat s jedinečná a kvalifikované názvy pro nové verze. Pokud jste si jisti, že může být použita hodnotě lax Správa verzí, můžete přidat nové serializovatelné členy v nové verze, ale není změnit nebo odebrat existující členy.  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> Používá <xref:System.Xml.Serialization.XmlAnyElementAttribute> a <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> atributy pro podporu odezvy dat je neznámý.  
  
## <a name="message-contract-versioning"></a>Správa verzí kontraktů zpráv  
 Pokyny pro Správa verzí kontraktů zpráv jsou velmi podobné kontrakty dat správy verzí. Pokud se vyžaduje striktní Správa verzí, by měl nemění vaše tělo zprávy ale místo toho vytvořte nové kontrakt zprávy s jedinečným názvem kvalifikovaný. Pokud víte, které můžete použít hodnotě lax Správa verzí, nelze přidat nové části textu zprávy, ale změnit nebo odebrat existující. Tyto pokyny platí i pro úplné a zabalit kontrakty zpráv.  
  
 Hlavičky zpráv můžete kdykoli přidat, i když striktní správy verzí je používán. Příznak MustUnderstand může mít vliv na správu verzí. Obecně platí, Správa verzí model pro hlavičky v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] je, jak je popsáno v specifikace protokolu SOAP.  
  
## <a name="service-contract-versioning"></a>Správa verzí kontraktů služby  
 Podobně jako správa verzí kontraktů dat, Správa verzí kontraktů služby také zahrnuje přidání, změně a odebrání operace.  
  
### <a name="specifying-name-namespace-and-action"></a>Zadání názvu, Namespace a akce  
 Ve výchozím nastavení je název kontraktu služby název rozhraní. Jeho výchozí obor názvů je "http://tempuri.org", a každou operaci akce je "http://tempuri.org/contractname/methodname". Doporučujeme explicitně zadáte název a obor názvů pro kontrakt služby a akci pro každou operaci zrušení "http://tempuri.org" a aby se zabránilo názvy rozhraní a metoda vystavení v kontrakt služby.  
  
### <a name="adding-parameters-and-operations"></a>Přidání parametrů a operace  
 Přidání operací služby vystavené služby není pevných změnit, protože existující klienti nemusí být obavy o těchto nových operací.  
  
> [!NOTE]
>  Přidání operací do kontraktu duplexní zpětné volání je narušující změně.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Změna parametrů operaci nebo návratové typy  
 Změna, nebo parametr návratové typy obecně je narušující změně, pokud nový typ implementuje stejné kontrakt dat implementované původní typ. Chcete-li tuto změnu, přidejte novou servisní smlouvou nebo definovat nové smlouvy o poskytování služeb.  
  
### <a name="removing-operations"></a>Odebrání operace  
 Odebrání operace je také narušující změně. Chcete-li tuto změnu, zadejte nové smlouvy o poskytování služeb a vystavit na nový koncový bod.  
  
### <a name="fault-contracts"></a>Kontrakty selhání  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut umožňuje vývojáři kontraktu služby zadejte informace o chyb, které mohou být vráceny z operace této smlouvy.  
  
 Seznam chyb, které jsou popsané v kontraktu služby není považováno za vyčerpávající. V každém okamžiku může operace vrátí chyb, které nejsou popsané v její smlouvy. Proto změna sadu chyb, které jsou popsané v kontraktu není považováno za nejnovější. Například přidávání nové chybu kontrakt pomocí <xref:System.ServiceModel.FaultContractAttribute> nebo odebrání existující chyby ze smlouvy.  
  
### <a name="service-contract-libraries"></a>Knihovny kontrakt služby  
 Organizace můžou mít zavedené knihovny kontrakty kde kontraktu je publikovaná v centrálním úložišti a služby implementátory implementace kontraktů z tohoto úložiště. Při publikování kontraktu služby do úložiště v tomto případě nemáte žádnou kontrolu nad kteří vytváří služby, které implementaci. Proto nelze změnit po publikování, kontrakt služby vykreslování efektivně neměnné. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] podporuje smlouvy dědičnosti, který můžete použít k vytvoření nové smlouvy, které rozšiřuje stávající smlouvy. Chcete-li tuto funkci používat, definujte nové rozhraní kontraktu služby, která dědí z původního rozhraní kontraktu služby a pak přidejte metody na nové rozhraní. Služba, která implementuje staré kontrakt a implementaci nové smlouvy. Změňte definici koncového bodu "versionOld" používat nové smlouvy. změňte. Klientům "versionOld" budou nadále vypadat jako zpřístupňuje "versionOld" kontrakt; koncový bod klientům "versionNew" zobrazí se koncový bod vystavit kontrakt "versionNew".  
  
## <a name="address-and-binding-versioning"></a>Adresa a správa verzí vazby  
 Změny adresa koncového bodu a vazby jsou nejnovější změny, pokud klienti podporují dynamicky zjišťování nové adresa koncového bodu nebo vazby. Jeden mechanismus pro implementaci tato funkce je pomocí registru Universal popis zjišťování a integrace (UDDI) a vzor volání UDDI, kde klient pokoušet o komunikaci s koncovým bodem a, při selhání, dotazuje dobře známé UDDI v registru pro aktuální koncový bod metadat. Klient potom použije adresu a vazbu z tato metadata ke komunikaci s koncovým bodem. Pokud tato komunikace úspěšná, klient ukládá do mezipaměti informace o adresu a vazba pro budoucí použití.  
  
## <a name="routing-service-and-versioning"></a>Služba Směrování a správa verzí  
 Pokud na změny služby jsou nejnovější změny a musí mít minimálně dva různé verze služby spuštěné současně můžete služby WCF směrování pro směrování zpráv do instance příslušné služby. Směrovací služby WCF používá směrování podle obsahu, jinými slovy, používá informace ve zprávě k určení, kam směrovat zprávy. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Směrovací služby WCF najdete [směrovací služby](../../../docs/framework/wcf/feature-details/routing-service.md). Příklad toho, jak používat službu WCF směrování pro správu verzí služby naleznete v části [postupy: Správa verzí služeb](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Příloha  
 Obecné data kontrakt Správa verzí pokyny potřeby striktní Správa verzí je považovat za kontrakty dat neměnné a vytvořit nové, když je nutné provést změny. Novou třídu musí být vytvořen pro každý nový kontrakt dat, aby bylo vyhnout se nutnosti trvat existujícího kódu, která byla zapsána z hlediska mechanismus stará data smlouvy – třída a přepisování z hlediska novou třídu kontraktu dat.  
  
 Jeden takový mechanismus je použití rozhraní k definování členů každý kontrakt dat a napsat kód vnitřní implementace z hlediska rozhraní než třídy kontraktu dat, které implementují rozhraní. Následující kód pro verze 1 služby ukazuje `IPurchaseOrderV1` rozhraní a `PurchaseOrderV1`:  
  
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
  
 Během operace kontrakt služby by byla zapsána z hlediska `PurchaseOrderV1`, skutečné obchodní logiky by být z hlediska `IPurchaseOrderV1`. Potom v verze 2 by novou `IPurchaseOrderV2` rozhraní a nový `PurchaseOrderV2` třídy, jak je znázorněno v následujícím kódu:  
  
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
  
 Kontrakt služby by došlo k přidání nových operací, které jsou zapsány z hlediska `PurchaseOrderV2`. Existující obchodní logika napsaná z hlediska `IPurchaseOrderV1` bude pokračovat v práci pro `PurchaseOrderV2` a nové obchodní logiky, která potřebuje `OrderDate` vlastnost by byla zapsána z hlediska `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Ekvivalence kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Zpětná volání serializace tolerantní k verzím](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
