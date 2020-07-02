---
title: 'Postupy: Migrace spravovaného kódu DCOM do WCF'
description: Migrace spravovaného kódu distribuovaného objektu Component Object Model (DCOM) mezi servery a klienty na Windows Communication Foundation (WCF).
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: cc6ac1dd01e17bb184d1f1faca372134d6130d33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619088"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Postupy: Migrace spravovaného kódu DCOM do WCF
Windows Communication Foundation (WCF) je doporučená a bezpečná volba pro volání spravovaného kódu mezi servery a klienty v distribuovaném prostředí pomocí modelu DCOM (Distributed Component Object Model). V tomto článku se dozvíte, jak migrovat kód z modelu DCOM do WCF v následujících scénářích.  
  
- Vzdálená služba vrátí klientovi objekt podle hodnoty.  
  
- Klient pošle objekt po jeho hodnotě do vzdálené služby.  
  
- Vzdálená služba vrátí objekt podle odkazu na klienta.  
  
 Z bezpečnostních důvodů není v WCF povolený odeslání objektu podle odkazu z klienta na službu. Scénář, který vyžaduje, aby se konverzace mezi klientem a serverem mohla docílit přes službu WCF pomocí duplexní služby.  Další informace o duplexních službách najdete v tématu [duplexní služby](../wcf/feature-details/duplex-services.md).  
  
 Další informace o vytváření služeb a klientů WCF pro tyto služby najdete v tématu [Základní programování WCF](../wcf/basic-wcf-programming.md), [navrhování a implementace služeb](../wcf/designing-and-implementing-services.md)a [vytváření klientů](../wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>Příklad kódu DCOM  
 V těchto scénářích mají rozhraní DCOM, která jsou znázorněná pomocí WCF, následující strukturu:  
  
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
 V tomto scénáři provedete volání služby a metoda IT vrátí objekt, který je předán podle hodnoty ze serveru do klienta. Tento scénář představuje následující volání modelu COM:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 V tomto scénáři klient obdrží deserializovanou kopii objektu ze vzdálené služby. Klient může s touto místní kopií pracovat bez zpětného volání ke službě.  Jinými slovy, klient garantuje, že služba nebude nijak zapojena v případě, že budou volány metody místní kopie. WCF vždycky vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření běžné služby WCF.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1: definování rozhraní služby WCF  
 Definujte veřejné rozhraní pro službu WCF a označte ji <xref:System.ServiceModel.ServiceContractAttribute> atributem [].  Označte metody, které chcete zpřístupnit klientům s <xref:System.ServiceModel.OperationContractAttribute> atributem []. Následující příklad ukazuje použití těchto atributů k identifikaci rozhraní na straně serveru a metod rozhraní, které může klient volat. Metoda použitá pro tento scénář je zobrazena tučně.  
  
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
 Dále byste měli vytvořit kontrakt dat pro službu, který popíše, jak budou data vyměněna mezi službou a jejími klienty.  Třídy popsané v kontraktu dat by měly být označeny <xref:System.Runtime.Serialization.DataContractAttribute> atributem []. Jednotlivé vlastnosti nebo pole, které chcete zobrazit pro klienta i server, by měly být označeny <xref:System.Runtime.Serialization.DataMemberAttribute> atributem []. Chcete-li, aby byly typy odvozené od třídy v kontraktu dat povoleny, je nutné je identifikovat pomocí atributu [ <xref:System.Runtime.Serialization.KnownTypeAttribute> ]. Služba WCF provede pouze serializaci nebo deserializaci typů v rozhraní služby a typech identifikovaných jako známé typy. Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.  
  
 Další informace o kontraktech dat najdete v tématu [kontrakty dat](../wcf/samples/data-contracts.md).  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a>Krok 3: implementace služby WCF  
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
 Chcete-li spustit službu WCF, je nutné deklarovat koncový bod, který zpřístupňuje toto rozhraní služby na konkrétní adrese URL pomocí konkrétní vazby WCF. Vazba určuje podrobnosti přenosu, kódování a protokolu pro klienty a server, které mají být sdělovány. Do konfiguračního souboru projektu služby se obvykle přidávají vazby (web.config). Následující příklad ukazuje položku vazby pro ukázkovou službu:  
  
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
  
 Dál je potřeba nakonfigurovat klienta tak, aby odpovídal informacím o vazbě zadaným službou. Uděláte to tak, že do souboru konfigurace aplikace klienta (app.config) přidáte následující.  
  
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
  
### <a name="step-5-run-the-service"></a>Krok 5: spuštění služby  
 Nakonec ho můžete sami hostovat v konzolové aplikaci přidáním následujících řádků do aplikace služby a spuštěním aplikace. Další informace o jiných způsobech hostování aplikace služby WCF, [hostování služeb](../wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6: volání služby z klienta  
 Chcete-li volat službu z klienta, je nutné vytvořit továrnu kanálu pro službu a požádat o kanál, který vám umožní přímo volat `GetCustomer` metodu přímo z klienta. Kanál implementuje rozhraní služby a zpracovává základní logiku požadavků a odpovědí.  Návratovou hodnotou z tohoto volání metody je deserializovaná kopie odpovědi služby.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient pošle objektu podle hodnoty na server.  
 V tomto scénáři klient pošle objekt na server podle hodnoty. To znamená, že server dostane deserializovanou kopii objektu.  Server může volat metody v této kopii a zaručit, že se nejedná o zpětné volání do klientského kódu. Jak už bylo zmíněno dříve, běžné výměny dat WCF jsou podle hodnoty.  To zaručuje, že volající metody na jednom z těchto objektů se spouští pouze místně – nevyvolává kód na klientovi.  
  
 Tento scénář představuje následující volání metody COM:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 V tomto scénáři se používá stejné rozhraní služby a kontrakt dat, jak je znázorněno v prvním příkladu. Kromě toho se klient a služba nakonfigurují stejným způsobem. V tomto příkladu je vytvořen kanál pro odeslání objektu a spuštění stejným způsobem. V tomto příkladu však vytvoříte klienta, který bude volat službu, a předáte objekt podle hodnoty. Metoda služby, kterou klient bude volat v kontraktu služby, je zobrazená tučně:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Přidání kódu do klienta odesílajícího objekt podle hodnoty  
 Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka podle hodnoty, vytvoří kanál ke komunikaci se `ICustomerManager` službou a odešle do něj objekt zákazníka.  
  
 Objekt zákazníka bude serializován a odeslán službě, kde je deserializována službou do nové kopie tohoto objektu.  Jakékoli metody, které služba volá s tímto objektem, se spustí jenom místně na serveru. Je důležité si uvědomit, že tento kód znázorňuje odeslání odvozeného typu ( `PremiumCustomer` ).  Kontrakt služby očekává `Customer` objekt, ale kontrakt dat služby používá <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut [] k označení toho, že `PremiumCustomer` je povolen také.  Služba WCF selže při pokusu o serializaci nebo deserializaci jiného typu prostřednictvím tohoto rozhraní služby.  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a>Služba vrátí objekt podle odkazu.  
 V tomto scénáři klientská aplikace provede volání vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby na klienta.  
  
 Jak bylo zmíněno dříve, služby WCF vždy vracejí objekt podle hodnoty.  Podobný výsledek však můžete dosáhnout použitím <xref:System.ServiceModel.EndpointAddress10> třídy.  <xref:System.ServiceModel.EndpointAddress10>Je serializovatelný objekt podle hodnoty, který může klient použít k získání relace odkazem objektu na serveru.  
  
 Chování objektu podle odkazu ve službě WCF zobrazené v tomto scénáři se liší od modelu DCOM.  V modelu DCOM může server vrátit objekt podle odkazu přímo klientovi a klient může volat metody tohoto objektu, které jsou spuštěny na serveru.  Ve službě WCF je však vrácen objekt vždy podle hodnoty.  Klient musí přijmout objekt podle hodnoty reprezentovaný <xref:System.ServiceModel.EndpointAddress10> a použít ho k vytvoření vlastního relace pomocí objektu s odkazem.  Metoda klienta volá objekt relace spuštěný na serveru. Jinými slovy je tento objekt odkazem na WCF normální službu WCF, která je nakonfigurovaná tak, aby byla relace.  
  
 V rámci WCF je relace způsob, jak korelovat více zpráv posílaných mezi dvěma koncovými body.  To znamená, že jakmile klient získá připojení k této službě, bude vytvořena relace mezi klientem a serverem.  Klient bude používat jednu jedinečnou instanci objektu na straně serveru pro všechny interakce v rámci této jediné relace. Relace WCF jsou podobné vzorům pro požadavky na síťový požadavek a odpověď orientovaný na připojení.  
  
 Tento scénář je reprezentován následující metodou DCOM.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1: definování relace rozhraní WCF a implementace služby WCF  
 Nejdřív definujte rozhraní služby WCF, které obsahuje objekt sessioning.  
  
 V tomto kódu je objekt relace označen `ServiceContract` atributem, který ho identifikuje jako regulární rozhraní služby WCF.  <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>Vlastnost je navíc nastavená tak, aby označovala, že se jedná o relaci služby.  
  
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
  
 Služba je označena atributem [ServiceBehavior] a jeho vlastnost InstanceContextMode je nastavena na hodnotu InstanceContextMode. PerSessions, aby označovala, že pro každou relaci by měla být vytvořena jedinečná instance tohoto typu.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2: definování služby WCF Factory pro objekt sessioning  
 Služba, která vytváří objekt relace, musí být definovaná a implementovaná. Následující kód ukazuje, jak to provést. Tento kód vytvoří jinou službu WCF, která vrací <xref:System.ServiceModel.EndpointAddress10> objekt.  Jedná se o serializovatelný tvar koncového bodu, pomocí kterého lze vytvořit objekt s úplnými relacemi.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Níže je tato implementace této služby. Tato implementace udržuje objekt pro vytváření relací s jedním prvkem.  Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> objekt, který odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.   <xref:System.ServiceModel.EndpointAddress10>je datový typ, který může být vrácen klientovi podle hodnoty.
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Krok 3: konfigurace a spuštění služeb WCF  
 Chcete-li hostovat tyto služby, budete muset provést následující přidání do konfiguračního souboru serveru (web.config).  
  
1. Přidejte `<client>` část, která popisuje koncový bod objektu Session.  V tomto scénáři server funguje taky jako klient a musí se nakonfigurovat, aby se povolil.  
  
2. V `<services>` části deklarujete koncové body služby objektu pro vytváření a relaci.  To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvořit kanál s relacemi.  
  
 Následuje příklad konfiguračního souboru s těmito nastaveními:  
  
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
  
 Přidejte následující řádky do konzolové aplikace, pro samoobslužnou hostování služby a aplikaci spusťte.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4: Konfigurace klienta a volání služby  
 Nakonfigurujte klienta tak, aby komunikoval se službami WCF, a to tak, že v konfiguračním souboru aplikace projektu (app.config) provedete následující položky.  
  
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
  
 Chcete-li zavolat službu, přidejte do klienta kód, abyste mohli provést následující akce:  
  
1. Vytvořte kanál ke `ISessionBoundFactory` službě.  
  
2. Použití kanálu k vyvolání služby a `ISessionBoundFactory` získání <xref:System.ServiceModel.EndpointAddress10> objektu.  
  
3. Použijte <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu relace.  
  
4. Zavolejte `SetCurrentValue` metody a `GetCurrentValue` , abyste ukázali, že zůstane stejná instance objektu použita v rámci více volání.  
  
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

- [Základní programování WCF](../wcf/basic-wcf-programming.md)
- [Navrhování a implementace služeb](../wcf/designing-and-implementing-services.md)
- [Sestavování klientů](../wcf/building-clients.md)
- [Duplexní služby](../wcf/feature-details/duplex-services.md)
