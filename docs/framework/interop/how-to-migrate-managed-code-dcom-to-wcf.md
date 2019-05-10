---
title: 'Postupy: Migrace spravovaného kódu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fad8a73c41379cac7523db6266951b8abab26e27
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626298"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Postupy: Migrace spravovaného kódu DCOM do WCF
Windows Communication Foundation (WCF) je volba doporučené a zabezpečené přes distribuované DCOM Component Object Model () pro spravovaný kód volání mezi servery a klienty v distribuovaném prostředí. Tento článek popisuje, jak vám migrace kódu z modelu DCOM do WCF v následujících scénářích.  
  
- Vzdálená služba vrátí objektu podle hodnoty do klienta  
  
- Klient odešle objektu podle hodnoty do vzdálené služby  
  
- Vzdálená služba vrátí klientovi pomocí – odkaz na objekt  
  
 Z bezpečnostních důvodů odesílání pomocí – odkaz na objekt z klienta do služby není povolena ve službě WCF. Tento scénář vyžaduje konverzace vpřed a zpět mezi klientem a serverem lze dosáhnout pomocí duplexní služby WCF.  Další informace o duplexní služby najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Další podrobnosti o vytvoření služby WCF a klienty pro tyto služby najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md), [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [sestavování klientů](../../../docs/framework/wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>Příklad kódu DCOM  
 Pro tyto scénáře, které jsou znázorněny pomocí technologie WCF rozhraní DCOM mají následující strukturu:  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a>Tato služba vrátí objektu podle hodnoty  
 V tomto scénáři provedete volání služby a metoda vrátí objekt, který je předán podle hodnoty ze serveru do klienta. Tento scénář představuje následující volání COM:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 V tomto scénáři klient obdrží kopii objekt deserializovaný ze vzdálené služby. Klient může interagovat s tuto místní kopii bez nutnosti volat zpět do služby.  Jinými slovy klient je zaručeno, že služba nebude možné zahrnutí žádným způsobem při volání metody v místní kopii. WCF vždy vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření regulárního služby WCF.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1: Definování rozhraní služby WCF  
 Definování veřejného rozhraní pro službu WCF a označte ji pomocí [<xref:System.ServiceModel.ServiceContractAttribute>] atributu.  Označení metody, kterou chcete zpřístupnit klientům s [<xref:System.ServiceModel.OperationContractAttribute>] atributu. Následující příklad ukazuje použití těchto atributů k určení rozhraní na straně serveru a klienta můžete volat metody rozhraní. Metoda použitá v tomto scénáři se zobrazí tučným písmem.  
  
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
 Dále byste měli vytvořit kontraktu dat pro službu, která popisuje výměna dat mezi službou a klienty.  Třídy je popsáno v kontraktu dat by měl být označeny atributem [<xref:System.Runtime.Serialization.DataContractAttribute>] atributu. Jednotlivé vlastnosti nebo pole má viditelná pro klientské a serverové by měly být označené [<xref:System.Runtime.Serialization.DataMemberAttribute>] atributu. Pokud chcete typy odvozené od třídy v kontraktu dat. Chcete-li být povoleny, je potřeba určit pomocí [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atributu. WCF se pouze serializaci nebo deserializaci typy v rozhraní služby a typy, které jsou identifikovány jako známé typy. Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.  
  
 Další informace o kontraktech dat najdete v tématu [kontraktů dat](../../../docs/framework/wcf/samples/data-contracts.md).  
  
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
 V dalším kroku měli byste implementovat třídu služby WCF, která implementuje rozhraní, které jste definovali v předchozím kroku.  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a>Krok 4: Nakonfigurujte službu a klienta  
 Pokud chcete spustit službu WCF, musíte deklarovat koncový bod, který zpřístupňuje rozhraní služby na konkrétní adrese URL použití konkrétní vazeb WCF. Vazbu určuje přenos, kódování a protokolu podrobnosti pro klienty a serverem komunikovat. Obvykle přidáte vazby do konfiguračního souboru projektu služby (web.config). Následuje ukázka zadání vazby služby příklad:  
  
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
  
 Dále je třeba nakonfigurovat klienta tak, aby odpovídaly informace o vazbě určeného službou. Uděláte to tak, přidejte následující k souboru konfigurace (app.config) klienta aplikace.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>Krok 5: Spuštění služby  
 Nakonec můžete svým hostovat ho v konzolové aplikaci, přidáním následující řádky do service app a spuštění aplikace. Další informace o dalších způsobech k hostování aplikace služby WCF [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6: Volání služby z klienta  
 Volání služby z klienta, budete muset vytvořit objekt pro vytváření kanálů pro službu a požádat o kanálu, která vám umožní volat přímo `GetCustomer` metoda přímo z klienta. Kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku za vás.  Návratová hodnota z volání této metody je deserializovat kopie odezvy služby.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient odešle objekt podle hodnoty do serveru  
 V tomto scénáři klient zasílá objektu na server, podle hodnoty. To znamená, že server dostanou kopii deserializovaného objektu.  Server může volat metody na tuto kopii a zaručit, že není žádná zpětné volání do kódu klienta. Jak už bylo zmíněno dříve, jsou normální WCF výměny dat podle hodnoty.  Zaručí se tak, že volání metody v jednom z těchto objektů místně spustí, pouze – nebude volat kód na straně klienta.  
  
 Tento scénář představuje následující volání metody COM:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Tento scénář používá stejný kontrakt rozhraní a dat služby, jak je znázorněno v prvním příkladu. Kromě toho klient a služba se nakonfigurují stejným způsobem. V tomto příkladu se vytvoří kanál pro odesílání objektu a spustit stejným způsobem. Ale v tomto příkladu vytvoříte klienta, který volá služby předávání objektu podle hodnoty. Metoda služby, které bude klient volat v kontraktu služby se zobrazí tučně:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Přidání kódu do klienta, který odešle objekt podle hodnoty  
 Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka podle hodnoty, vytvoří kanál, ke komunikaci s `ICustomerManager` služby a odešle objekt zákazníka.  
  
 Objekt zákazníka se serializovat a odešle do služby, kde je deserializovat službou do novou kopii tohoto objektu.  Všechny metody volá služby na tento objekt se spustí jenom místně na serveru. Je důležité si uvědomit, že tento kód ukazuje odesílání odvozeného typu (`PremiumCustomer`).  Očekává, že kontrakt služby `Customer` objektu, ale data služby smlouvy používá [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atribut označuje, že `PremiumCustomer` je také povolena.  WCF se nezdaří pokusy o serializaci nebo deserializaci jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.  
  
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
 V tomto scénáři klientské aplikace volá vzdálenou službu a metoda vrátí objekt, který se předá odkazem ze služby ke klientovi.  
  
 Jak už bylo zmíněno dříve, služby WCF se kdykoli vrátit objekt podle hodnoty.  Však můžete podobného výsledku dosáhnout pomocí <xref:System.ServiceModel.EndpointAddress10> třídy.  <xref:System.ServiceModel.EndpointAddress10> Je objekt serializovatelný podle hodnoty, který je možné k získání objektu s relacemi odkazem na serveru klientem.  
  
 Chování pomocí odkazu na objekt ve službě WCF je znázorněno v tomto scénáři se liší od modelu DCOM.  V modelu DCOM server vrátit objekt podle odkazu do klienta přímo a klient může volat metody tohoto objektu, které se spustí na serveru.  Ve službě WCF ale objekt vrácený je vždy podle hodnoty.  Klient musí přijmout tento objekt podle hodnoty, reprezentovaný <xref:System.ServiceModel.EndpointAddress10> a použijte ji k vytvoření vlastní objekt s relacemi podle odkazu.  Volání metody klienta s relacemi objektu spustit na serveru. Jinými slovy tento objekt podle odkazu ve službě WCF je běžné služby WCF, který je nakonfigurován s relacemi.  
  
 Relace ve službě WCF, je způsob, jak korelace více posílané mezi dva koncové body.  To znamená, že Jakmile klient získá připojení pro tuto službu, relace navázat mezi klientem a serverem.  Klient použije jeden jedinečný instance objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace. Kontrakty relací WCF jsou podobné vzory požadavku nebo odpovědi síťové připojení objektově orientovaný.  
  
 Tento scénář je reprezentován metodu modelu DCOM.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1: Definování rozhraní služby WCF který neobsahuje relace a implementaci  
 Nejprve definujte rozhraní služby WCF, které obsahuje objekt s relacemi.  
  
 V tomto kódu je označeno objekt s relacemi `ServiceContract` atribut, který ji identifikuje jako regulární rozhraní služby WCF.  Kromě toho <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> je nastavena na označení bude s relacemi service.  
  
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
  
 Služba je označená pomocí atributu [ServiceBehavior] a jeho vlastností InstanceContextMode nastavenou na InstanceContextMode.PerSessions udávající, že jedinečné instance tohoto typu by měl být vytvářeny pro každou relaci.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2: Definovat objekt pro vytváření služby WCF u objektu s relacemi  
 Služba, která vytvoří objekt s relacemi musí být definován a implementovat. Následující kód ukazuje, jak to provést. Tento kód vytvoří jiné služby WCF, který vrátí <xref:System.ServiceModel.EndpointAddress10> objektu.  Toto je serializovatelného tvaru koncového bodu může použít k vytvoření objektu relace režim.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Tady je implementace této služby. Tato implementace udržuje typu singleton objektu pro vytváření kanálů vytváření relací objektů.  Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> , která odkazuje na vzdálenou adresu přidružené k tomuto kanálu.   <xref:System.ServiceModel.EndpointAddress10> je datový typ, který může být vrácen do klienta podle hodnota.  
  
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
 K hostování těchto služeb, je potřeba provést následující položky na server konfigurační soubor (web.config).  
  
1. Přidat `<client>` část popisující koncový bod pro objekt s relacemi.  V tomto scénáři server také funguje jako klient a musí být nakonfigurované tak, aby to.  
  
2. V `<services>` části, deklarujte koncových bodů služby pro objekt factory a který neobsahuje relace.  To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvořte kanál s relacemi.  
  
 Tady je příklad souboru konfigurace s tímto nastavením:  
  
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
  
 Přidejte následující řádky do konzolové aplikace, k hostování na vlastním serveru služby a spusťte aplikaci.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4: Konfigurace klienta a volání služby  
 Konfigurace klienta ke komunikaci se službami WCF tím, že následující položky projektu konfiguračního souboru aplikace (app.config).  
  
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
  
 K vyvolání služby, přidejte kód do klienta provést následující kroky:  
  
1. Vytvoření kanálu pro `ISessionBoundFactory` služby.  
  
2. Používaná k volání kanálu `ISessionBoundFactory` služby získání <xref:System.ServiceModel.EndpointAddress10> objektu.  
  
3. Použití <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu s relacemi.  
  
4. Volání `SetCurrentValue` a `GetCurrentValue` metody k předvedení zůstává stejná instance objektu se používá napříč více volání.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Sestavování klientů](../../../docs/framework/wcf/building-clients.md)
- [Duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md)
