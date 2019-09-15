---
title: Migrace z .NET Remoting do WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 926ccee49c7a445c724cecd72015ec5a5307cf58
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990185"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrace z .NET Remoting do WCF
Tento článek popisuje, jak migrovat aplikaci, která používá vzdálenou komunikaci rozhraní .NET pro použití Windows Communication Foundation (WCF). Porovnává podobné koncepce mezi těmito produkty a potom popisuje, jak provést několik běžných scénářů vzdálené komunikace ve službě WCF.  
  
 Vzdálená komunikace .NET je starší verze produktu, která je podporována pouze pro zpětnou kompatibilitu. Není zabezpečený napříč prostředími se smíšeným vztahem důvěryhodnosti, protože nemůže udržovat samostatné úrovně důvěryhodnosti mezi klientem a serverem. Například nikdy byste neměli zveřejnit koncový bod vzdálené komunikace rozhraní .NET pro Internet nebo nedůvěryhodné klienty. Doporučujeme migrovat existující aplikace vzdálené komunikace na novější a bezpečnější technologie. Pokud návrh aplikace používá pouze HTTP a je RESTful, doporučujeme webové rozhraní API pro ASP.NET. Další informace najdete v tématu webové rozhraní API pro ASP.NET. Pokud je aplikace založená na protokolu SOAP nebo vyžaduje jiné protokoly než HTTP jako TCP, doporučujeme WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porovnání vzdálené komunikace .NET s WCF  
 Tato část porovnává základní stavební kameny vzdálené komunikace .NET se svými ekvivalenty WCF. Tyto stavební bloky budeme později používat k vytvoření některých běžných scénářů klient-server ve službě WCF. Následující tabulka shrnuje hlavní podobnosti a rozdíly mezi službami vzdálené komunikace a WCF v technologii .NET.  
  
||Vzdálené komunikace pomocí rozhraní .NET|WCF|  
|-|-------------------|---------|  
|Typ serveru|Třída MarshalByRefObject třídy|Označit atributem [ServiceContract]|  
|Operace služby|Veřejné metody typu serveru|Označit atributem [OperationContract]|  
|Serializace|ISerializable nebo [serializovatelný]|DataContractSerializer nebo XmlSerializer|  
|Předané objekty|Podle hodnoty nebo podle odkazu|Pouze podle hodnoty|  
|Chyby a výjimky|Jakákoli serializovatelný výjimka|FaultContract\<TDetail >|  
|Klientské proxy objekty|Silné typy transparentní proxy servery se vytvářejí automaticky z MarshalByRefObjects.|Proxy silného typu se generují na vyžádání pomocí třídy ChannelFactory\<TChannel >|  
|Požadovaná platforma|Klient i server musí používat Microsoft OS a .NET.|pro různé platformy|  
|Formát zprávy|Soukromé|Oborové standardy (SOAP, WS-* atd.)|  
  
### <a name="server-implementation-comparison"></a>Porovnání implementace serveru  
  
#### <a name="creating-a-server-in-net-remoting"></a>Vytvoření serveru v technologii vzdálené komunikace .NET  
 Typy serverů vzdálené komunikace .NET musí být odvozeny od metody MarshalByRefObject a definovat metody, které může klient volat, například následující:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Veřejné metody tohoto typu serveru se stanou veřejnými kontrakty dostupnými klientům.  Neexistuje žádné oddělení mezi veřejným rozhraním serveru a jeho implementací – jeden typ zpracovává oba.  
  
 Po definování typ serveru ho můžete zpřístupnit klientům, jako v následujícím příkladu:  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 Existuje mnoho způsobů, jak nastavit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů. Toto je pouze jeden příklad.  
  
#### <a name="creating-a-server-in-wcf"></a>Vytvoření serveru ve službě WCF  
 Ekvivalentní krok v rámci WCF zahrnuje vytvoření dvou typů – veřejné "kontrakt služby" a konkrétní implementaci. První je deklarován jako rozhraní s označením [ServiceContract]. Metody, které jsou k dispozici pro klienty, jsou označeny [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementace serveru je definována v samostatné konkrétní třídě, jako v následujícím příkladu:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Po definování těchto typů lze Server WCF zpřístupnit klientům, jako v následujícím příkladu:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> Protokol TCP se v obou příkladech používá k tomu, aby byl podobný jako možný. Příklady použití HTTP najdete v tématu věnovaném scénářům, které jsou dále v tomto tématu.  
  
 Existuje mnoho způsobů, jak nakonfigurovat a hostovat služby WCF. Toto je pouze jeden příklad, označovaný jako "místní hostování". Další informace naleznete v následujících tématech:  
  
- [Postupy: Definování kontraktu služby](how-to-define-a-wcf-service-contract.md)  
  
- [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)  
  
- [Služby hostování](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porovnání implementace klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Vytvoření klienta v technologii vzdálené komunikace .NET  
 Jakmile je objekt serveru vzdálené komunikace .NET k dispozici, může je klient spotřebovat, jako v následujícím příkladu:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Instance RemotingServer vrácená z Activator. GetObject () se označuje jako "transparentní proxy server". Implementuje veřejné rozhraní API pro typ RemotingServer na klientovi, ale všechny metody volají objekt serveru běžící v jiném procesu nebo počítači.  
  
#### <a name="creating-a-client-in-wcf"></a>Vytvoření klienta ve službě WCF  
 Stejný krok služby WCF zahrnuje použití továrny kanálu k vytvoření proxy serveru explicitně. Podobně jako u vzdálené komunikace lze objekt proxy použít k vyvolání operací na serveru, jako v následujícím příkladu:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Tento příklad ukazuje programování na úrovni kanálu, protože je nejvíce podobný příkladu vzdálené komunikace. K dispozici je také **Přidat odkaz na službu** přístup v aplikaci Visual Studio, který generuje kód pro zjednodušení programování klienta. Další informace naleznete v následujících tématech:  
  
- [Programování klienta na úrovni kanálu](./extending/client-channel-level-programming.md)  
  
- [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Využití serializace  
 Vzdálená komunikace rozhraní .NET i služba WCF používají serializace k posílání objektů mezi klientem a serverem, ale liší se v těchto důležitých způsobech:  
  
1. Používají různé serializace a konvence k označení toho, co se má serializovat.  
  
2. Vzdálená komunikace .NET podporuje serializaci "podle odkazu", která umožňuje přístup k metodě nebo vlastnostem na jedné úrovni ke spouštění kódu na jiné úrovni, který je napříč hranicemi zabezpečení. Tato funkce zveřejňuje chyby zabezpečení a je jedním z hlavních důvodů, proč by koncové body vzdálené komunikace neměly být nikdy vystaveny nedůvěryhodným klientům.  
  
3. Serializace, kterou používá Vzdálená komunikace, je odhlášená (explicitně vyloučit, co se neserializace) a serializace WCF je výslovný souhlas (explicitně označit členy k serializaci).  
  
#### <a name="serialization-in-net-remoting"></a>Serializace ve vzdálené komunikaci .NET  
 Vzdálená komunikace .NET podporuje dva způsoby serializace a deserializace objektů mezi klientem a serverem:  
  
- *Podle hodnoty* – hodnoty objektu jsou serializovány napříč hranicemi vrstev a nová instance tohoto objektu je vytvořena na druhé úrovni. Všechna volání metod nebo vlastností této nové instance se spouštějí pouze místně a neovlivňují původní objekt nebo vrstvu.  
  
- *Odkazem – speciální* "odkaz na objekt" je serializován napříč hranicemi vrstev. Když jedna vrstva komunikuje s metodami nebo vlastnostmi tohoto objektu, komunikuje zpátky původnímu objektu na původní úrovni. Objekty podle odkazu můžou v obou směrech směrovat – server na klienta nebo klienta na server.  
  
 Typy podle hodnot ve vzdálené komunikaci jsou označeny atributem [serializovatelný] nebo implementací ISerializable, jako v následujícím příkladu:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Odkazem typy jsou odvozeny ze třídy MarshalByRefObject, jako v následujícím příkladu:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Je mimořádně důležité pochopit důsledky objektů odkazujících na vzdálené komunikace. Pokud kterákoli z vrstev (klienta nebo serveru) odesílá objekt odkazem na druhou úroveň, všechny volání metody se vrátí zpět na úrovni, která je vlastníkem objektu. Například metoda volání metody na objektu podle odkazu, kterou vrátil server, bude spouštět kód na serveru. Podobně server volající metody v objektu podle odkazu poskytovaný klientem spustí kód zpět v klientovi. Z tohoto důvodu se použití vzdálené komunikace .NET doporučuje jenom v plně důvěryhodných prostředích. Zveřejnění veřejného koncového bodu vzdálené komunikace .NET pro nedůvěryhodné klienty způsobí, že se server vzdálené komunikace bude zranitelný vůči útokům.  
  
#### <a name="serialization-in-wcf"></a>Serializace ve službě WCF  
 WCF podporuje pouze serializaci podle hodnoty. Nejběžnější způsob, jak definovat typ pro výměnu mezi klientem a serverem, je jako v následujícím příkladu:  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 Atribut [DataContract] identifikuje tento typ jako ten, který lze serializovat a deserializovat mezi klientem a serverem. Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole k serializaci.  
  
 Když WCF odesílá objekt napříč vrstvami, serializovat pouze hodnoty a vytvoří novou instanci objektu na druhé úrovni. Jakékoli interakce s hodnotami objektu se projeví pouze lokálně – nekomunikují s druhou vrstvou, jak fungují objekty vzdálené komunikace .NET podle referencí. Další informace naleznete v tématu [serializace a deserializace](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Možnosti zpracování výjimek  
  
#### <a name="exceptions-in-net-remoting"></a>Výjimky při vzdálené komunikaci .NET  
 Výjimky vyvolané vzdáleným serverem jsou serializovány, odesílány klientovi a vyvolány místně na klientovi jako jakákoli jiná výjimka. Vlastní výjimky lze vytvořit pomocí dílčí třídy typu výjimky a označením pomocí [serializovatelný].   Většina výjimek rozhraní je již tímto způsobem označena, což umožňuje vyvolání serveru, jeho serializace a opětovného vyvolání v klientovi. I když je tento návrh vhodný během vývoje, můžou být informace na straně serveru neúmyslně zveřejněné klientovi. Toto je jeden z mnoha důvodů, proč by se Vzdálená komunikace mohla používat jenom v plně důvěryhodných prostředích.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Výjimky a chyby ve službě WCF  
 Služba WCF nepovoluje vrácení libovolných typů výjimek ze serveru klientovi, protože by mohlo dojít k neúmyslnému zpřístupnění informací. Pokud operace služby vyvolá neočekávanou výjimku, způsobí to, že na klientovi bude vyvolána FaultExceptiona pro obecné účely. Tato výjimka neposkytuje žádné informace, proč došlo k problému, a pro některé aplikace to postačuje. Aplikace, které potřebují sdělit rozsáhlejší informace o chybách klientovi, najdete tak, že nadefinujete kontrakt selhání.  
  
 Chcete-li to provést, vytvořte nejprve typ [DataContract], který bude obsahovat informace o chybě.  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 Zadejte kontrakt selhání, který se má použít pro každou operaci služby.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Server hlásí chybové stavy vyvoláním FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 A vždy, když klient odešle požadavek na server, může zachytit chyby jako normální výjimky.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 Další informace o smlouvách o selhání najdete v <xref:System.ServiceModel.FaultException>tématu.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
  
#### <a name="security-in-net-remoting"></a>Zabezpečení při vzdálené komunikaci .NET  
 Některé kanály vzdálené komunikace .NET podporují funkce zabezpečení, jako je ověřování a šifrování ve vrstvě kanálu (IPC a TCP). Kanál HTTP spoléhá na Internetová informační služba (IIS) pro ověřování i šifrování. I přes tuto podporu byste měli vzít v úvahu nezabezpečený komunikační protokol technologie .NET a použít ho jenom v plně důvěryhodných prostředích. Nikdy nezveřejňujte veřejný koncový bod vzdálené komunikace pro Internet nebo nedůvěryhodné klienty.  
  
#### <a name="security-in-wcf"></a>Zabezpečení ve službě WCF  
 Služba WCF byla navržena s ohledem na zabezpečení, v rámci řešení druhů ohrožení zabezpečení zjištěných při vzdálené komunikaci .NET. WCF nabízí zabezpečení na úrovni přenosu i zprávy a nabízí mnoho možností pro ověřování, autorizaci, šifrování a tak dále. Další informace naleznete v následujících tématech:  
  
- [Zabezpečení](./feature-details/security.md)  
  
- [Pokyny pro zabezpečení WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrace na WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Proč migrovat ze vzdálené komunikace na WCF?  
  
- **Vzdálená komunikace .NET je starší verze produktu.** Jak je popsáno v tématu [Vzdálená komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), se považuje za starší verzi produktu a nedoporučuje se pro vývoj nových verzí. Pro nové i existující aplikace se doporučuje webové rozhraní API WCF nebo ASP.NET.  
  
- **WCF používá standardy pro různé platformy.** Služba WCF byla navržena s ohledem na interoperabilitu různých platforem a podporuje řadu průmyslových standardů (SOAP, WS-Security, WS-Trust atd.). Služba WCF může spolupracovat s klienty, kteří běží na jiných operačních systémech než Windows. Vzdálená komunikace byla navržena primárně pro prostředí, kde jsou spouštěny servery i klientské aplikace pomocí rozhraní .NET Framework v operačním systému Windows.  
  
- **WCF má integrované zabezpečení.** Služba WCF byla navržena s ohledem na zabezpečení a nabízí mnoho možností ověřování, zabezpečení na úrovni přenosu, zabezpečení na úrovni zpráv atd. Vzdálená komunikace byla navržena tak, aby aplikacím usnadnila spolupráci, ale nebyla navržena tak, aby byla zabezpečena v nedůvěryhodných prostředích. Služba WCF byla navržena tak, aby fungovala v důvěryhodných i nedůvěryhodných prostředích.  
  
### <a name="migration-recommendations"></a>Doporučení pro migraci  
 Níže jsou uvedené doporučené kroky pro migraci ze vzdálené komunikace rozhraní .NET do WCF:  
  
- **Vytvořte kontrakt služby.** Definujte typy rozhraní služby a označte je atributem [ServiceContract]. Označte všechny metody, které budou klienti moci volat s [OperationContract].  
  
- **Vytvoření kontraktu dat.** Definujte typy dat, které se budou vyměňovat mezi serverem a klientem, a označte je atributem [DataContract]. Označte všechna pole a vlastnosti, které bude klient moci používat s [DataMember].  
  
- **Vytvořte kontrakt selhání (volitelné).** Vytvořte typy, které budou vyměňovány mezi serverem a klientem, pokud dojde k chybám. Označte tyto typy pomocí [DataContract] a [DataMember], aby je bylo možné serializovat. U všech operací služby, které jste označili pomocí [OperationContract], je také označte pomocí [FaultContract], aby označovaly chyby, které mohou vracet.  
  
- **Nakonfigurujte a hostovat službu.** Po vytvoření kontraktu služby je dalším krokem konfigurace vazby k vystavení služby na koncovém bodu. Další informace najdete v tématu [koncové body: Adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Jakmile se aplikace vzdálené komunikace migruje na WCF, je stále důležité odebrat závislosti na vzdálené komunikaci .NET. Tím se zajistí, že se z aplikace odeberou všechny chyby zabezpečení vzdálené komunikace. Tyto kroky zahrnují následující:  
  
- **Přerušit použití objektu MarshalByRefObject.** Typ MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán službou WCF. Všechny typy aplikací, které má třída MarshalByRefObject třídy MarshalByRefObject odebrat nebo změnit.  
  
- **Zrušit použití [serializovatelných vlastností] a ISerializable.** Atribut [serializovatelný] a rozhraní ISerializable byly původně určeny k serializaci typů v rámci důvěryhodných prostředí a jsou používány pro vzdálenou komunikaci. Serializace WCF spoléhá na typy označené [DataContract] a [DataMember]. Datové typy používané aplikací by měly být upraveny tak, aby používaly [DataContract] a nepoužívaly ISerializable nebo [serializovatelný].  
  
### <a name="migration-scenarios"></a>Scénáře migrace  
 Teď se podívejme, jak provádět následující běžné scénáře vzdálené komunikace ve službě WCF:  
  
1. Server vrátí klientovi objekt podle hodnoty.  
  
2. Server vrátí objekt podle odkazu na klienta.  
  
3. Klient pošle objekt po hodnotě na server.  
  
> [!NOTE]
> Odeslání objektu podle odkazu z klienta na server není v rámci WCF povoleno.  
  
 Při čtení těchto scénářů Předpokládejme, že naše základní rozhraní pro vzdálenou komunikaci rozhraní .NET vypadají jako v následujícím příkladu. Implementace vzdálené komunikace .NET není tady důležité, protože chceme ilustrovat jenom použití WCF k implementaci ekvivalentních funkcí.  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Scénář 1: Služba vrátí objekt podle hodnoty.  
 Tento scénář ukazuje server, který vrací objekt klientovi podle hodnoty. WCF vždycky vrátí objekty ze serveru podle hodnoty, takže následující kroky jednoduše popisují, jak sestavit normální službu WCF.  
  
1. Začněte tím, že definujete veřejné rozhraní pro službu WCF a označíte ho atributem [ServiceContract]. K identifikaci metod na straně serveru, které bude náš klient volat, používáme [OperationContract].  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. Dalším krokem je vytvoření kontraktu dat pro tuto službu. Provedeme to vytvořením tříd (ne rozhraní) označených atributem [DataContract]. Jednotlivé vlastnosti nebo pole, které chceme zobrazit pro klienta i server, jsou označeny [DataMember]. Pokud chceme, aby byly odvozené typy povoleny, je k jejich identifikaci nutné použít atribut [třída KnownType]. Pouze typy WCF umožní serializaci nebo deserializaci této služby jsou ty, které jsou v rozhraní služby a tyto "známé typy". Pokus o výměnu jakéhokoli jiného typu, který není v tomto seznamu, bude odmítnut.  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. Dále poskytujeme implementaci rozhraní služby.  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. Abychom mohli spustit službu WCF, musíme deklarovat koncový bod, který zveřejňuje toto rozhraní služby na konkrétní adrese URL pomocí konkrétní vazby WCF. To se obvykle provádí přidáním následujících sekcí do souboru Web. config v projektu serveru.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. Službu WCF lze následně spustit pomocí následujícího kódu:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Po spuštění této třídy ServiceHost použije soubor Web. config ke zřízení správného kontraktu, vazby a koncového bodu. Další informace o konfiguračních souborech najdete v tématu [Konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md). Tento styl spuštění serveru se označuje jako samoobslužné hostování. Další informace o dalších možnostech hostování služeb WCF najdete v tématu [hostingové služby](./hosting-services.md).  
  
6. Soubor App. config klientského projektu musí deklarovat párové informace o vazbě koncového bodu služby. Nejjednodušší způsob, jak to provést v aplikaci Visual Studio, je použít **Přidat odkaz na službu**, který bude automaticky aktualizovat soubor App. config. Tyto změny lze také přidat ručně.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Další informace o použití **Přidat odkaz na službu**naleznete v tématu [How to: Přidejte, aktualizujte nebo odeberte odkaz](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)na službu.  
  
7. Nyní můžeme volat službu WCF z klienta. Provedeme to vytvořením továrny kanálů pro tuto službu, vyžádáním pro kanál a přímo voláním metody, kterou chceme na tomto kanálu. Můžeme to udělat, protože kanál implementuje rozhraní služby a zpracovává základní logiku požadavků a odpovědí pro nás. Návratovou hodnotou z tohoto volání metody je deserializovaná kopie odpovědi serveru.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Objekty vrácené službou WCF ze serveru do klienta jsou vždy podle hodnoty. Objekty jsou deserializované kopie dat odesílaných serverem. Klient může volat metody pro tyto místní kopie bez jakéhokoli nebezpečí vyvolání kódu serveru prostřednictvím zpětných volání.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scénář 2: Server vrátí objekt podle odkazu.  
 Tento scénář ukazuje, jak server, který klientovi poskytuje objekt, odkazem. V případě vzdálené komunikace rozhraní .NET je tato služba zpracována automaticky pro jakýkoli typ odvozený od třídy MarshalByRefObject, který je serializován podle odkazu. Příkladem tohoto scénáře je umožněno, aby více klientů mělo nezávislé relace objektů na straně serveru. Jak už jsme uvedli, objekty vrácené službou WCF jsou vždycky podle hodnoty, takže neexistuje přímý ekvivalent objektu podle odkazu, ale je možné dosáhnout podobné sémantiky odkazování pomocí <xref:System.ServiceModel.EndpointAddress10> objektu. Toto je serializovatelný objekt podle hodnoty, který může klient použít k získání relace pomocí objektu odkazem na server. To umožňuje situaci, kdy je více klientů s nezávislou relací objektů na straně serveru.  
  
1. Nejdřív musíme definovat kontrakt služby WCF, který odpovídá samotnému objektu relace.  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > Všimněte si, že objekt sessioning je označený jako [ServiceContract] a vytvoří normální rozhraní služby WCF. Nastavení vlastnosti SessionMode označuje, že se jedná o službu, která se jedná o relaci. V rámci WCF je relace způsob, jak korelovat více zpráv posílaných mezi dvěma koncovými body. To znamená, že jakmile klient získá připojení k této službě, bude vytvořena relace mezi klientem a serverem. Klient bude používat jednu jedinečnou instanci objektu na straně serveru pro všechny interakce v rámci této jediné relace.  
  
2. Dál je potřeba poskytnout implementaci tohoto rozhraní služby. Informování o tom, že se jedná o [ServiceBehavior] a nastavení InstanceContextMode, sdělujeme, že WCF chceme pro každou relaci použít jedinečnou instanci tohoto typu.  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. Teď potřebujeme způsob, jak získat instanci tohoto objektu relace. Provedeme to vytvořením dalšího rozhraní služby WCF, které vrátí objekt EndpointAddress10. Jedná se o serializovatelný tvar koncového bodu, který může klient použít k vytvoření objektu relace.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     A implementujeme tuto službu WCF:  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     Tato implementace udržuje objekt pro vytváření relací s jedním prvkem. Když se zavolá GetInstanceAddress (), vytvoří kanál a vytvoří objekt EndpointAddress10, který efektivně odkazuje na vzdálenou adresu přidruženou k tomuto kanálu. EndpointAddress10 je jednoduše datový typ, který může být vrácen klientovi podle hodnoty.  
  
4. Musíme upravit konfigurační soubor serveru tak, že provedete následující dvě věci, jak je znázorněno v následujícím příkladu:  
  
    1. Deklarujte > oddíl klienta, který popisuje koncový bod objektu sessioning. \< To je nezbytné, protože server v této situaci také funguje jako klient.  
  
    2. Deklarujte koncové body objektu pro vytváření a relaci. To je nezbytné, aby klient mohl komunikovat s koncovými body služby, aby získal EndpointAddress10 a vytvořil kanál s relacemi.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     A pak můžeme spustit tyto služby:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Nakonfigurujte klienta deklarováním stejných koncových bodů v souboru App. config projektu.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. Aby bylo možné vytvořit a použít tento objekt relace, klient musí provést následující kroky:  
  
    1. Vytvořte kanál ke službě ISessionBoundFactory.  
  
    2. Použijte tento kanál k vyvolání této služby k získání EndpointAddress10.  
  
    3. Pomocí EndpointAddress10 vytvořte kanál pro získání objektu relace.  
  
    4. Interakce s objektem relace, aby se ukázalo, že zůstává stejná instance napříč více voláními.  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 WCF vždycky vrací objekty podle hodnoty, ale je možné podporovat ekvivalent sémantiky odkazování prostřednictvím použití EndpointAddress10. To umožňuje klientovi, aby si vyžádal relaci instance služby WCF, po které s ní bude moct pracovat stejně jako s ostatními službami WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scénář 3: Klient odesílá instanci Server a podle hodnoty.  
 Tento scénář ukazuje klientovi, který neprimitivní instanci objektu odesílá do serveru podle hodnoty. Protože WCF odesílá pouze objekty podle hodnoty, tento scénář ukazuje normální využití služby WCF.  
  
1. Použijte stejnou službu WCF ze scénáře 1.  
  
2. Použijte klienta k vytvoření nového objektu podle hodnoty (zákazník), vytvořte kanál ke komunikaci se službou ICustomerService a odešlete do něj objekt.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     Objekt zákazníka bude serializován a odeslán na server, kde je deserializován do nové kopie tohoto objektu.  
  
    > [!NOTE]
    > Tento kód také znázorňuje odeslání odvozeného typu (PremiumCustomer). Rozhraní služby očekává objekt zákazníka, ale atribut [třída KnownType] u třídy Customer, který je označen PremiumCustomer, byl také povolen. Služba WCF selže při pokusu o serializaci nebo deserializaci jakéhokoli jiného typu prostřednictvím tohoto rozhraní služby.  
  
 Normální výměny dat WCF jsou podle hodnoty. To zaručuje, že vyvolání metod v jednom z těchto datových objektů se spustí pouze lokálně – nevyvolává kód na druhé úrovni. I když je možné dosáhnout nějakého typu, například objektů odkazujících *na server* , není možné, aby klient předal objektu odkazem *na* Server. Scénář, který vyžaduje, aby se konverzace mezi klientem a serverem mohla docílit přes službu WCF pomocí duplexní služby. Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Souhrn  
 Vzdálená komunikace .NET je komunikační rozhraní určené k použití pouze v rámci plně důvěryhodných prostředí. Je to starší verze produktu a je podporovaná jenom pro zpětnou kompatibilitu. Neměl by se používat k vytváření nových aplikací. Naopak služba WCF byla navržena s ohledem na zabezpečení a doporučuje se pro nové a stávající aplikace. Microsoft doporučuje, aby se stávající aplikace vzdálené komunikace migrovali na místo toho použití WCF nebo ASP.NET webového rozhraní API.
