---
title: "Postup: Migrace spravovaného kódu DCOM do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af401cafe0740dcd9a313ae9143f9772605137d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Postup: Migrace spravovaného kódu DCOM do WCF
Windows Communication Foundation (WCF) je volba doporučené a zabezpečení přes distribuované modelu DCOM (Component Object) pro spravovaný kód volání mezi servery a klienty v distribuovaném prostředí. Tento článek ukazuje, jak je možné migrovat kód z modelu DCOM do WCF pro následující scénáře.  
  
-   Vzdálená služba vrátí klientovi pomocí hodnota objektu  
  
-   Klient odešle službě Vzdálené podle hodnota objektu  
  
-   Vzdálená služba vrátí odkaz na objekt podle-klientovi  
  
 Z bezpečnostních důvodů odeslání odkaz na objekt podle-klienta ke službě není povolena v WCF. Ve službě WCF pomocí duplexní služby se dá dosáhnout scénáře, který vyžaduje konverzace přepínat mezi klientem a serverem.  Další informace o duplexní služby najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Další informace o vytvoření služby WCF a klienty pro tyto služby najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md), [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [sestavování klientů](../../../docs/framework/wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>Příklad kódu DCOM  
 Pro tyto scénáře rozhraní DCOM, které jsou zobrazené pomocí WCF mít následující strukturu:  
  
```  
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
  
## <a name="the-service-returns-an-object-by-value"></a>Služba vrátí podle hodnota objektu  
 V tomto scénáři provedete volání služby a metoda vrátí objekt, který je předán-hodnota ze serveru do klienta. Tento scénář představuje následující volání COM:  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 V tomto scénáři klient obdrží kopii deserializovat objekt ze vzdálené služby. Klient mohou komunikovat s této místní kopie bez zpětné volání do služby.  Jinými slovy klient je zaručeno, že služba nebude zahrnuta žádným způsobem, pokud jsou volány metody na místní kopii. WCF vždy vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření regulární služby WCF.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1: Definování rozhraní služby WCF  
 Definujte veřejné rozhraní pro službu WCF a označte ji pomocí [<xref:System.ServiceModel.ServiceContractAttribute>] atributu.  Označit metody, kterou chcete vystavit klientů [<xref:System.ServiceModel.OperationContractAttribute>] atributu. Následující příklad ukazuje, pomocí těchto atributů k identifikaci rozhraní na straně serveru a metody rozhraní, které můžete volat klienta. Metoda použitá pro tento scénář je zobrazeny tučně.  
  
```  
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
 Dále byste měli vytvořit kontraktu dat pro služby, která popisují, jak se budou vyměňovat data mezi službou a jeho klienty.  Třídy, které jsou popsané v kontrakt dat by měl být označen s [<xref:System.Runtime.Serialization.DataContractAttribute>] atributu. Jednotlivé vlastnosti nebo pole, které chcete viditelná pro klientské a serverové by měl být označen s [<xref:System.Runtime.Serialization.DataMemberAttribute>] atributu. Pokud chcete typy odvozené od třídy, v kontraktu dat mají být povolena, je potřeba určit pomocí [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atributu. WCF bude pouze serializaci nebo deserializaci typy identifikovat jako známé typy a typy v rozhraní služby. Pokud se pokusíte použít typ, který není typu známé, dojde k výjimce.  
  
 Další informace o kontraktech dat najdete v tématu [kontrakty dat](../../../docs/framework/wcf/samples/data-contracts.md).  
  
```  
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
 Další měli byste implementovat třídu služby WCF, který implementuje rozhraní, které jste definovali v předchozím kroku.  
  
```  
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
 Pokud chcete spustit službu WCF, musíte deklarovat koncový bod, který zpřístupňuje rozhraní této služby na konkrétní adrese URL, pomocí konkrétní vazby WCF. Vazba Určuje podrobnosti přenosu, kódování a protokol pro klienty a server, ke komunikaci. Obvykle přidat vazby do konfiguračního souboru služby projektu (web.config). Na obrázku je položka vazby pro službu příkladu:  
  
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
  
 Dále musíte nakonfigurovat klienta tak, aby odpovídaly informace o vazbě zadaná služba. Uděláte to tak, přidejte následující k souboru konfigurace (app.config) aplikace klienta.  
  
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
  
### <a name="step-5-run-the-service"></a>Krok 5: Spouštění služby  
 Nakonec můžete svým hostovat ho v konzolové aplikaci přidáním následující řádky do aplikace služby a spuštění aplikace. Další informace o jiných způsobech hostovat aplikaci služby WCF [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6: Zavolejte službu z klienta  
 Pro volání služby z klienta, budete muset vytvoření postupu kanálu pro službu a požádat o kanál, který vám umožní volat přímo `GetCustomer` metoda přímo z klienta. Kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku pro vás.  Vrácená hodnota z volání této metody se deserializovat kopii odpověď služby.  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient odešle objekt podle hodnoty k serveru  
 V tomto scénáři klient odešle příslušný objekt na server, pomocí hodnoty. To znamená, že server dostanou kopii deserializovat objekt.  Server můžete volat metody pro tuto kopii a zaručit, že neexistuje žádná zpětného volání do kódu klienta. Jak je uvedeno nahoře, normální WCF výměny dat jsou-hodnota.  To zaručuje, že volání metod v jednom z těchto objektů místně spustí, pouze – ho nebude vyvolání kódu na straně klienta.  
  
 Tento scénář představuje následující volání metody COM:  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Tento scénář používá stejný kontrakt rozhraní a data služby, jak je znázorněno v prvním příkladu. Kromě toho se klient a služba nakonfigurovat stejným způsobem. V tomto příkladu se vytvoří kanál pro odeslání objektu a spusťte stejným způsobem. V tomto příkladu klienta, který volá službě předávání pomocí hodnota objektu vytvoříte. Metoda služby klienta bude volat v kontrakt služby se zobrazí tučným písmem:  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Přidejte kód klientovi, který odešle objekt podle hodnoty  
 Následující kód ukazuje, jak klient vytvoří nový objekt-hodnota zákazníka, vytvoří kanál ke komunikaci s `ICustomerManager` služby a odešle objekt zákazníka k němu.  
  
 Objekt zákazníka bude serializován a odešle do služby, kde je deserializovat službou do novou kopii tohoto objektu.  Žádné metody službu volání na tento objekt, budou spuštěny pouze místně na serveru. Je důležité si uvědomit, že tento kód ukazuje odesílání odvozený typ (`PremiumCustomer`).  Kontrakt služby očekává `Customer` objektu, ale data služby smlouvy používá [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atributu, která označuje, že `PremiumCustomer` je také povoleno.  WCF se nezdaří pokusy o serializaci nebo deserializaci žádným jiným typem prostřednictvím tohoto rozhraní služby.  
  
```  
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
  
## <a name="the-service-returns-an-object-by-reference"></a>Služba vrátí objekt odkazem  
 Pro tento scénář klientská aplikace zavolá vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby do klienta.  
  
 Jak je uvedeno nahoře, služby WCF vždy vrátí objekt hodnotou.  Podobně jako výsledek však můžete dosáhnout pomocí <xref:System.ServiceModel.EndpointAddress10> třídy.  <xref:System.ServiceModel.EndpointAddress10> Je objekt serializovatelný podle hodnoty, které je možné klientem pro získání objektu relacemi odkazem na serveru.  
  
 Chování objektu odkazem ve WCF uvedené v tomto scénáři se liší od DCOM.  V modelu DCOM server může objekt odkazem vracet klientovi přímo a klient může volat metody tento objekt, které spustit na serveru.  Ve službě WCF ale objekt vrácený je vždy podle hodnota.  Klient musí mít tento objekt-hodnota reprezentována <xref:System.ServiceModel.EndpointAddress10> a použít ho k vytvoření vlastního objektu relacemi odkazem.  Volání metod klienta na objekt relacemi spustit na serveru. Jinými slovy tento objekt odkazem ve WCF je normální služby WCF, který je nakonfigurovaný jako relacemi.  
  
 Ve službě WCF relace je způsob korelace více zprávy odeslané mezi dva koncové body.  To znamená, že Jakmile klient obdrží připojení k této službě, relace navázat mezi klientem a serverem.  Klient použije jeden jedinečný výskyt serverový objekt pro všechny jeho interakce v rámci této jedné relace. Kontrakty relacemi WCF se podobá vzory požadavků a odpovědí orientovaná na připojení sítě.  
  
 Tento scénář je reprezentována metodu DCOM.  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1: Definování rozhraní služby Sessionful WCF a implementace  
 Nejprve definujte rozhraní služby WCF, který obsahuje objekt relacemi.  
  
 V tomto kódu je označené relacemi objektu `ServiceContract` atribut, který ji identifikuje jako regulární rozhraní služby WCF.  Kromě toho <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> je nastavena k označení, bude relacemi služby.  
  
```  
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
  
 Služba je označena atributem [ServiceBehavior], a jeho vlastnost režim InstanceContextMode nastavením InstanceContextMode.PerSessions označíte, že jedinečné instance tohoto typu by měl být vytvořen pro každou relaci.  
  
```  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2: Definování factory služby WCF pro objekt relací  
 Služba, která vytvoří relacemi objekt musí být definovaný a implementovat. Následující kód ukazuje, jak to udělat. Tento kód vytvoří jiné služby WCF, který vrací <xref:System.ServiceModel.EndpointAddress10> objektu.  Toto je serializovatelný formu koncový bod může použít k vytvoření objektu relace úplné.  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Toto je implementací této služby. Tato implementace udržuje singleton postup kanálu k vytváření relací objektů.  Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> objekt, který odkazuje na vzdálené adresy přidružené k tomuto kanálu.   <xref:System.ServiceModel.EndpointAddress10>je datový typ, který může být vrácen do klienta pomocí hodnota.  
  
```  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Krok 3: Konfigurace a spuštění služby WCF  
 K hostování těchto služeb, bude třeba, aby těmito přídavky do konfiguračního souboru serveru (web.config).  
  
1.  Přidat `<client>` oddíl, který popisuje koncový bod pro objekt relacemi.  V tomto scénáři serveru taky funguje jako klient a musí být nakonfigurován pro povolení této.  
  
2.  V `<services>` část, deklarovat koncové body služby objektu factory a sessionful.  To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvoření kanálu relací.  
  
 Následující příklad je konfigurační soubor s tímto nastavením:  
  
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
  
 Přidejte následující řádky do konzoly aplikace, k hostování samoobslužné služby a spusťte aplikaci.  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4: Konfigurace klienta a volání služby  
 Konfigurace klienta ke komunikaci se službami WCF tím, že provedete následující položky v konfiguračním souboru projektu aplikace (app.config).  
  
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
  
 Pro volání služby, přidejte do klienta, proveďte následující kód:  
  
1.  Vytvoření kanálu pro `ISessionBoundFactory` služby.  
  
2.  Kanál používaná k volání `ISessionBoundFactory` služby získat <xref:System.ServiceModel.EndpointAddress10> bbject.  
  
3.  Použití <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu relacemi.  
  
4.  Volání `SetCurrentValue` a `GetCurrentValue` metody k předvedení zůstane stejné instance objektu se používá napříč více volání.  
  
```  
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
 [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Sestavování klientů](../../../docs/framework/wcf/building-clients.md)  
 [Duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md)
