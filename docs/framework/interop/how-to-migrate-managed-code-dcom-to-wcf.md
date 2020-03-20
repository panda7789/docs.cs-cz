---
title: 'Postup: Migrace spravovaného kódu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: 2576e88c25ae381e90ec7d613efb648048145b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181382"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Postup: Migrace spravovaného kódu DCOM do WCF
Windows Communication Foundation (WCF) je doporučená a bezpečná volba přes distributed component object model (DCOM) pro volání spravovaného kódu mezi servery a klienty v distribuovaném prostředí. Tento článek ukazuje, jak migrovat kód z DCOM na WCF pro následující scénáře.  
  
- Vzdálená služba vrátí klientovi hodnotu podle objektu.  
  
- Klient odešle objekt u hodnoty vzdálené služby  
  
- Vzdálená služba vrátí objekt odkaz na klienta  
  
 Z bezpečnostních důvodů není v wcf povoleno odesílání odkazu na objekt z klienta do služby. Scénář, který vyžaduje konverzaci tam a zpět mezi klientem a serverem lze dosáhnout v WCF pomocí duplexní služby.  Další informace o duplexních službách naleznete v [tématu Duplex Services](../wcf/feature-details/duplex-services.md).  
  
 Další podrobnosti o vytváření služeb WCF a klientů pro tyto služby naleznete v [tématu Základní wcf programování](../wcf/basic-wcf-programming.md), [navrhování a implementaci služeb](../wcf/designing-and-implementing-services.md)a vytváření [klientů](../wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>Ukázkový kód DCOM  
 Pro tyto scénáře rozhraní DCOM, které jsou znázorněny pomocí WCF mají následující strukturu:  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a>Služba vrátí objekt podle hodnoty.  
 V tomto scénáři provedete volání služby a metoda vrátí objekt, který je předán by-hodnota ze serveru klientovi. Tento scénář představuje následující volání COM:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 V tomto scénáři klient obdrží rekonstruovanou kopii objektu ze vzdálené služby. Klient může pracovat s touto místní kopii bez volání zpět do služby.  Jinými slovy, klientovi je zaručeno, že služba nebude zapojena žádným způsobem při volání metod na místní kopii. WCF vždy vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření pravidelné služby WCF.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1: Definování rozhraní služby WCF  
 Definujte veřejné rozhraní pro službu WCF<xref:System.ServiceModel.ServiceContractAttribute>a označte ji atributem [ ].  Označte metody, které chcete zpřístupnit<xref:System.ServiceModel.OperationContractAttribute>klientům pomocí atributu [ ]. Následující příklad ukazuje použití těchto atributů k identifikaci rozhraní na straně serveru a metody rozhraní, které může klient volat. Metoda použitá pro tento scénář je zobrazena tučně.  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a>Krok 2: Definování kontraktu dat  
 Dále byste měli vytvořit kontrakt dat pro službu, která bude popisovat, jak budou data vyměňována mezi službou a jejími klienty.  Třídy popsané ve smlouvě s daty<xref:System.Runtime.Serialization.DataContractAttribute>by měly být označeny atributem [ ]. Jednotlivé vlastnosti nebo pole, které chcete zobrazit pro klienta i server, by měly být označeny atributem [<xref:System.Runtime.Serialization.DataMemberAttribute>]. Pokud chcete, aby byly povoleny typy odvozené z třídy ve<xref:System.Runtime.Serialization.KnownTypeAttribute>smlouvě s daty, musíte je identifikovat pomocí atributu [ ]. WCF bude serializovat nebo rekonstruovat pouze typy v rozhraní služby a typy označené jako známé typy. Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.  
  
 Další informace o kontraktech dat naleznete v [tématu Data Contracts](../wcf/samples/data-contracts.md).  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a>Krok 3: Implementace služby WCF  
 Dále byste měli implementovat třídu služby WCF, která implementuje rozhraní, které jste definovali v předchozím kroku.  
  
```csharp  
public class CustomerService: ICustomerManager
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a>Krok 4: Konfigurace služby a klienta  
 Chcete-li spustit službu WCF, musíte deklarovat koncový bod, který zveřejňuje toto rozhraní služby na konkrétní adresu URL pomocí konkrétní vazby WCF. Vazba určuje podrobnosti přenosu, kódování a protokolu pro klienty a server komunikovat. Obvykle přidáte vazby do konfiguračního souboru projektu služby (web.config). Následující ukazuje závaznou položku pro ukázkovou službu:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Dále je třeba nakonfigurovat klienta tak, aby odpovídal avitu informace určené službou. Chcete-li tak učinit, přidejte do souboru konfigurace aplikace klienta (app.config).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>Krok 5: Spuštění služby  
 Nakonec jej můžete samostatně hostovat v konzolové aplikaci přidáním následujících řádků do aplikace služby a spuštěním aplikace. Další informace o dalších způsobech hostování aplikace služby [WCF, hostingové služby](../wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6: Volání služby od klienta  
 Chcete-li volat službu z klienta, musíte vytvořit továrnu kanálu pro službu a požádat o kanál, který vám umožní přímo volat metodu `GetCustomer` přímo z klienta. Kanál implementuje rozhraní služby a zpracovává základní logiku požadavku/odpovědi za vás.  Vrácená hodnota z tohoto volání metody je reserializovaná kopie odpovědi služby.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient odešle objekt s po kteroukonem na server.  
 V tomto scénáři klient odešle objekt na server, podle hodnoty. To znamená, že server obdrží rekonstruovanou kopii objektu.  Server může volat metody pro tuto kopii a je zaručeno, že neexistuje žádné zpětné volání do klientského kódu. Jak již bylo zmíněno dříve, normální WCF výměny dat jsou podle hodnoty.  To zaručuje, že volání metody na jeden z těchto objektů spustí pouze místně – nebude vyvolat kód na straně klienta.  
  
 Tento scénář představuje následující volání metody COM:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Tento scénář používá stejné rozhraní služby a kontrakt dat, jak je znázorněno v prvním příkladu. Kromě toho bude klient a služba nakonfigurovánstejným způsobem. V tomto příkladu je vytvořen kanál pro odeslání objektu a spuštění stejným způsobem. V tomto příkladu však vytvoříte klienta, který volá službu, předávání objektu podle hodnoty. Způsob služby, který bude klient volat v servisní smlouvě, je zobrazen tučně:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Přidání kódu klientovi, který odešle objekt s pokteroudkem  
 Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka s další `ICustomerManager` hodnotou, vytvoří kanál pro komunikaci se službou a odešle do něj objekt zákazníka.  
  
 Objekt zákazníka bude serializován a odeslán do služby, kde je službou deserializován do nové kopie tohoto objektu.  Všechny metody, které služba volá na tento objekt, budou spuštěny pouze místně na serveru. Je důležité si uvědomit, že tento kód ilustruje`PremiumCustomer`odeslání odvozeného typu ( ).  Servisní smlouva očekává `Customer` objekt, ale smlouva o servisních datech používá atribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>] k označení, že `PremiumCustomer` je také povolen.  WCF se nezdaří pokusy o serializaci nebo rekonstruovat jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a>Služba vrátí objekt odkazem.  
 V tomto scénáři klientská aplikace provede volání vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby klientovi.  
  
 Jak již bylo zmíněno dříve WCF služby vždy vrátit objekt podle hodnoty.  Můžete však dosáhnout podobného výsledku pomocí třídy. <xref:System.ServiceModel.EndpointAddress10>  Je <xref:System.ServiceModel.EndpointAddress10> serializovatelný objekt podle hodnoty, který může klient použít k získání objektu sessionful by-reference na serveru.  
  
 Chování objektu podle odkazu v WCF zobrazené v tomto scénáři se liší od Modelu DCOM.  V DCOM server může vrátit objekt odkazu klientovi přímo a klient může volat metody tohoto objektu, které se spouštějí na serveru.  V WCF je však vrácený objekt vždy podle hodnoty.  Klient musí vzít tento objekt podle <xref:System.ServiceModel.EndpointAddress10> hodnoty, reprezentovaný a použít jej k vytvoření vlastního objektu podle odkazu.  Metoda klienta volá objekt relace, který se spustí na serveru. Jinými slovy tento odkaz na objekt v WCF je normální WCF služba, která je nakonfigurována jako sessionful.  
  
 V WCF relace je způsob korelace více zpráv odeslaných mezi dvěma koncovými body.  To znamená, že jakmile klient získá připojení k této službě, bude mezi klientem a serverem vytvořena relace.  Klient použije jednu jedinečnou instanci objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace. Relace WCF smlouvy jsou podobné připojení orientované na síťové požadavky/odpovědi vzory.  
  
 Tento scénář je reprezentován následující metodou DCOM.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1: Definování rozhraní a implementace služby WCF v relování  
 Nejprve definujte rozhraní služby WCF, které obsahuje objekt relace.  
  
 V tomto kódu sessionful objekt je `ServiceContract` označen atributem, který identifikuje jako pravidelné wcf rozhraní služby.  Kromě toho <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> je vlastnost nastavena tak, aby označovala, že se bude jedná o službu relace.  
  
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
  
 Následující kód ukazuje implementaci služby.  
  
 Služba je označena atributem [ServiceBehavior] a její vlastnost í InstanceContextMode nastavenou na InstanceContextMode.PerSessions označuje, že pro každou relaci by měla být vytvořena jedinečná instance tohoto typu.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2: Definování služby WCF factory pro objekt relačné  
 Služba, která vytvoří objekt relace musí být definována a implementována. Následující kód ukazuje, jak to provést. Tento kód vytvoří jinou službu WCF, která vrací <xref:System.ServiceModel.EndpointAddress10> objekt.  Toto je serializovatelná forma koncového bodu, který lze použít k vytvoření objektu úplného relace.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Následuje implementace této služby. Tato implementace udržuje totokanálovou továrnu pro vytváření objektů relací.  Když `GetInstanceAddress` je volána, vytvoří kanál <xref:System.ServiceModel.EndpointAddress10> a vytvoří objekt, který odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.   <xref:System.ServiceModel.EndpointAddress10>je datový typ, který lze vrátit klientovi podle hodnoty.
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Krok 3: Konfigurace a spuštění služeb WCF  
 Chcete-li tyto služby hostovat, budete muset provést následující dodatky k konfiguračnímu souboru serveru (web.config).  
  
1. Přidejte `<client>` oddíl, který popisuje koncový bod pro objekt relace.  V tomto scénáři server také funguje jako klient a musí být nakonfigurován tak, aby to povolit.  
  
2. V `<services>` části deklarujte koncové body služby pro objekt, který je určen pro vytváření a relaci.  To umožňuje klientovi komunikovat s koncovými <xref:System.ServiceModel.EndpointAddress10> body služby, získat a vytvořit kanál relace.  
  
 Následuje ukázkový konfigurační soubor s těmito nastaveními:  
  
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
  
 Přidejte následující řádky do konzolové aplikace, chcete-li službu sami hostovat, a spusťte aplikaci.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4: Konfigurace klienta a volání služby  
 Nakonfigurujte klienta pro komunikaci se službami WCF provedením následujících položek v konfiguračním souboru aplikace projektu (app.config).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
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
  
 Chcete-li volat službu, přidejte kód do klienta provést následující:  
  
1. Vytvořte kanál `ISessionBoundFactory` ke službě.  
  
2. Pomocí kanálu vyvolat `ISessionBoundFactory` službu získat <xref:System.ServiceModel.EndpointAddress10> objekt.  
  
3. Použijte <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu k získání objektu relace.  
  
4. Volání `SetCurrentValue` a `GetCurrentValue` metody k prokázání, že zůstává stejný objekt instance se používá přes více volání.  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Základní programování WCF](../wcf/basic-wcf-programming.md)
- [Navrhování a implementace služeb](../wcf/designing-and-implementing-services.md)
- [Sestavování klientů](../wcf/building-clients.md)
- [Duplexní služby](../wcf/feature-details/duplex-services.md)
