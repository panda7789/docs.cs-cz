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
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="01dd1-102">Postup: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="01dd1-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="01dd1-103">Windows Communication Foundation (WCF) je doporučená a bezpečná volba přes distributed component object model (DCOM) pro volání spravovaného kódu mezi servery a klienty v distribuovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="01dd1-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="01dd1-104">Tento článek ukazuje, jak migrovat kód z DCOM na WCF pro následující scénáře.</span><span class="sxs-lookup"><span data-stu-id="01dd1-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="01dd1-105">Vzdálená služba vrátí klientovi hodnotu podle objektu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="01dd1-106">Klient odešle objekt u hodnoty vzdálené služby</span><span class="sxs-lookup"><span data-stu-id="01dd1-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="01dd1-107">Vzdálená služba vrátí objekt odkaz na klienta</span><span class="sxs-lookup"><span data-stu-id="01dd1-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="01dd1-108">Z bezpečnostních důvodů není v wcf povoleno odesílání odkazu na objekt z klienta do služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="01dd1-109">Scénář, který vyžaduje konverzaci tam a zpět mezi klientem a serverem lze dosáhnout v WCF pomocí duplexní služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="01dd1-110">Další informace o duplexních službách naleznete v [tématu Duplex Services](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="01dd1-110">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="01dd1-111">Další podrobnosti o vytváření služeb WCF a klientů pro tyto služby naleznete v [tématu Základní wcf programování](../wcf/basic-wcf-programming.md), [navrhování a implementaci služeb](../wcf/designing-and-implementing-services.md)a vytváření [klientů](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="01dd1-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="01dd1-112">Ukázkový kód DCOM</span><span class="sxs-lookup"><span data-stu-id="01dd1-112">DCOM example code</span></span>  
 <span data-ttu-id="01dd1-113">Pro tyto scénáře rozhraní DCOM, které jsou znázorněny pomocí WCF mají následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="01dd1-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="01dd1-114">Služba vrátí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="01dd1-115">V tomto scénáři provedete volání služby a metoda vrátí objekt, který je předán by-hodnota ze serveru klientovi.</span><span class="sxs-lookup"><span data-stu-id="01dd1-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="01dd1-116">Tento scénář představuje následující volání COM:</span><span class="sxs-lookup"><span data-stu-id="01dd1-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="01dd1-117">V tomto scénáři klient obdrží rekonstruovanou kopii objektu ze vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="01dd1-118">Klient může pracovat s touto místní kopii bez volání zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="01dd1-119">Jinými slovy, klientovi je zaručeno, že služba nebude zapojena žádným způsobem při volání metod na místní kopii.</span><span class="sxs-lookup"><span data-stu-id="01dd1-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="01dd1-120">WCF vždy vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření pravidelné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="01dd1-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="01dd1-121">Krok 1: Definování rozhraní služby WCF</span><span class="sxs-lookup"><span data-stu-id="01dd1-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="01dd1-122">Definujte veřejné rozhraní pro službu WCF<xref:System.ServiceModel.ServiceContractAttribute>a označte ji atributem [ ].</span><span class="sxs-lookup"><span data-stu-id="01dd1-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="01dd1-123">Označte metody, které chcete zpřístupnit<xref:System.ServiceModel.OperationContractAttribute>klientům pomocí atributu [ ].</span><span class="sxs-lookup"><span data-stu-id="01dd1-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="01dd1-124">Následující příklad ukazuje použití těchto atributů k identifikaci rozhraní na straně serveru a metody rozhraní, které může klient volat.</span><span class="sxs-lookup"><span data-stu-id="01dd1-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="01dd1-125">Metoda použitá pro tento scénář je zobrazena tučně.</span><span class="sxs-lookup"><span data-stu-id="01dd1-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="01dd1-126">Krok 2: Definování kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="01dd1-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="01dd1-127">Dále byste měli vytvořit kontrakt dat pro službu, která bude popisovat, jak budou data vyměňována mezi službou a jejími klienty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="01dd1-128">Třídy popsané ve smlouvě s daty<xref:System.Runtime.Serialization.DataContractAttribute>by měly být označeny atributem [ ].</span><span class="sxs-lookup"><span data-stu-id="01dd1-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="01dd1-129">Jednotlivé vlastnosti nebo pole, které chcete zobrazit pro klienta i server, by měly být označeny atributem [<xref:System.Runtime.Serialization.DataMemberAttribute>].</span><span class="sxs-lookup"><span data-stu-id="01dd1-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="01dd1-130">Pokud chcete, aby byly povoleny typy odvozené z třídy ve<xref:System.Runtime.Serialization.KnownTypeAttribute>smlouvě s daty, musíte je identifikovat pomocí atributu [ ].</span><span class="sxs-lookup"><span data-stu-id="01dd1-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="01dd1-131">WCF bude serializovat nebo rekonstruovat pouze typy v rozhraní služby a typy označené jako známé typy.</span><span class="sxs-lookup"><span data-stu-id="01dd1-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="01dd1-132">Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="01dd1-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="01dd1-133">Další informace o kontraktech dat naleznete v [tématu Data Contracts](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="01dd1-133">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="01dd1-134">Krok 3: Implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="01dd1-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="01dd1-135">Dále byste měli implementovat třídu služby WCF, která implementuje rozhraní, které jste definovali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="01dd1-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="01dd1-136">Krok 4: Konfigurace služby a klienta</span><span class="sxs-lookup"><span data-stu-id="01dd1-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="01dd1-137">Chcete-li spustit službu WCF, musíte deklarovat koncový bod, který zveřejňuje toto rozhraní služby na konkrétní adresu URL pomocí konkrétní vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="01dd1-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="01dd1-138">Vazba určuje podrobnosti přenosu, kódování a protokolu pro klienty a server komunikovat.</span><span class="sxs-lookup"><span data-stu-id="01dd1-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="01dd1-139">Obvykle přidáte vazby do konfiguračního souboru projektu služby (web.config).</span><span class="sxs-lookup"><span data-stu-id="01dd1-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="01dd1-140">Následující ukazuje závaznou položku pro ukázkovou službu:</span><span class="sxs-lookup"><span data-stu-id="01dd1-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="01dd1-141">Dále je třeba nakonfigurovat klienta tak, aby odpovídal avitu informace určené službou.</span><span class="sxs-lookup"><span data-stu-id="01dd1-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="01dd1-142">Chcete-li tak učinit, přidejte do souboru konfigurace aplikace klienta (app.config).</span><span class="sxs-lookup"><span data-stu-id="01dd1-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="01dd1-143">Krok 5: Spuštění služby</span><span class="sxs-lookup"><span data-stu-id="01dd1-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="01dd1-144">Nakonec jej můžete samostatně hostovat v konzolové aplikaci přidáním následujících řádků do aplikace služby a spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="01dd1-145">Další informace o dalších způsobech hostování aplikace služby [WCF, hostingové služby](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="01dd1-145">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="01dd1-146">Krok 6: Volání služby od klienta</span><span class="sxs-lookup"><span data-stu-id="01dd1-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="01dd1-147">Chcete-li volat službu z klienta, musíte vytvořit továrnu kanálu pro službu a požádat o kanál, který vám umožní přímo volat metodu `GetCustomer` přímo z klienta.</span><span class="sxs-lookup"><span data-stu-id="01dd1-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="01dd1-148">Kanál implementuje rozhraní služby a zpracovává základní logiku požadavku/odpovědi za vás.</span><span class="sxs-lookup"><span data-stu-id="01dd1-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="01dd1-149">Vrácená hodnota z tohoto volání metody je reserializovaná kopie odpovědi služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="01dd1-150">Klient odešle objekt s po kteroukonem na server.</span><span class="sxs-lookup"><span data-stu-id="01dd1-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="01dd1-151">V tomto scénáři klient odešle objekt na server, podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="01dd1-152">To znamená, že server obdrží rekonstruovanou kopii objektu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="01dd1-153">Server může volat metody pro tuto kopii a je zaručeno, že neexistuje žádné zpětné volání do klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="01dd1-154">Jak již bylo zmíněno dříve, normální WCF výměny dat jsou podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="01dd1-155">To zaručuje, že volání metody na jeden z těchto objektů spustí pouze místně – nebude vyvolat kód na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="01dd1-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="01dd1-156">Tento scénář představuje následující volání metody COM:</span><span class="sxs-lookup"><span data-stu-id="01dd1-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="01dd1-157">Tento scénář používá stejné rozhraní služby a kontrakt dat, jak je znázorněno v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="01dd1-158">Kromě toho bude klient a služba nakonfigurovánstejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="01dd1-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="01dd1-159">V tomto příkladu je vytvořen kanál pro odeslání objektu a spuštění stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="01dd1-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="01dd1-160">V tomto příkladu však vytvoříte klienta, který volá službu, předávání objektu podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="01dd1-161">Způsob služby, který bude klient volat v servisní smlouvě, je zobrazen tučně:</span><span class="sxs-lookup"><span data-stu-id="01dd1-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="01dd1-162">Přidání kódu klientovi, který odešle objekt s pokteroudkem</span><span class="sxs-lookup"><span data-stu-id="01dd1-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="01dd1-163">Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka s další `ICustomerManager` hodnotou, vytvoří kanál pro komunikaci se službou a odešle do něj objekt zákazníka.</span><span class="sxs-lookup"><span data-stu-id="01dd1-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="01dd1-164">Objekt zákazníka bude serializován a odeslán do služby, kde je službou deserializován do nové kopie tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="01dd1-165">Všechny metody, které služba volá na tento objekt, budou spuštěny pouze místně na serveru.</span><span class="sxs-lookup"><span data-stu-id="01dd1-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="01dd1-166">Je důležité si uvědomit, že tento kód ilustruje`PremiumCustomer`odeslání odvozeného typu ( ).</span><span class="sxs-lookup"><span data-stu-id="01dd1-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="01dd1-167">Servisní smlouva očekává `Customer` objekt, ale smlouva o servisních datech používá atribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>] k označení, že `PremiumCustomer` je také povolen.</span><span class="sxs-lookup"><span data-stu-id="01dd1-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="01dd1-168">WCF se nezdaří pokusy o serializaci nebo rekonstruovat jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="01dd1-169">Služba vrátí objekt odkazem.</span><span class="sxs-lookup"><span data-stu-id="01dd1-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="01dd1-170">V tomto scénáři klientská aplikace provede volání vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="01dd1-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="01dd1-171">Jak již bylo zmíněno dříve WCF služby vždy vrátit objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="01dd1-172">Můžete však dosáhnout podobného výsledku pomocí třídy. <xref:System.ServiceModel.EndpointAddress10></span><span class="sxs-lookup"><span data-stu-id="01dd1-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="01dd1-173">Je <xref:System.ServiceModel.EndpointAddress10> serializovatelný objekt podle hodnoty, který může klient použít k získání objektu sessionful by-reference na serveru.</span><span class="sxs-lookup"><span data-stu-id="01dd1-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="01dd1-174">Chování objektu podle odkazu v WCF zobrazené v tomto scénáři se liší od Modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="01dd1-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="01dd1-175">V DCOM server může vrátit objekt odkazu klientovi přímo a klient může volat metody tohoto objektu, které se spouštějí na serveru.</span><span class="sxs-lookup"><span data-stu-id="01dd1-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="01dd1-176">V WCF je však vrácený objekt vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="01dd1-177">Klient musí vzít tento objekt podle <xref:System.ServiceModel.EndpointAddress10> hodnoty, reprezentovaný a použít jej k vytvoření vlastního objektu podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="01dd1-178">Metoda klienta volá objekt relace, který se spustí na serveru. Jinými slovy tento odkaz na objekt v WCF je normální WCF služba, která je nakonfigurována jako sessionful.</span><span class="sxs-lookup"><span data-stu-id="01dd1-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="01dd1-179">V WCF relace je způsob korelace více zpráv odeslaných mezi dvěma koncovými body.</span><span class="sxs-lookup"><span data-stu-id="01dd1-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="01dd1-180">To znamená, že jakmile klient získá připojení k této službě, bude mezi klientem a serverem vytvořena relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="01dd1-181">Klient použije jednu jedinečnou instanci objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="01dd1-182">Relace WCF smlouvy jsou podobné připojení orientované na síťové požadavky/odpovědi vzory.</span><span class="sxs-lookup"><span data-stu-id="01dd1-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="01dd1-183">Tento scénář je reprezentován následující metodou DCOM.</span><span class="sxs-lookup"><span data-stu-id="01dd1-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="01dd1-184">Krok 1: Definování rozhraní a implementace služby WCF v relování</span><span class="sxs-lookup"><span data-stu-id="01dd1-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="01dd1-185">Nejprve definujte rozhraní služby WCF, které obsahuje objekt relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="01dd1-186">V tomto kódu sessionful objekt je `ServiceContract` označen atributem, který identifikuje jako pravidelné wcf rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="01dd1-187">Kromě toho <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> je vlastnost nastavena tak, aby označovala, že se bude jedná o službu relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="01dd1-188">Následující kód ukazuje implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="01dd1-189">Služba je označena atributem [ServiceBehavior] a její vlastnost í InstanceContextMode nastavenou na InstanceContextMode.PerSessions označuje, že pro každou relaci by měla být vytvořena jedinečná instance tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="01dd1-190">Krok 2: Definování služby WCF factory pro objekt relačné</span><span class="sxs-lookup"><span data-stu-id="01dd1-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="01dd1-191">Služba, která vytvoří objekt relace musí být definována a implementována.</span><span class="sxs-lookup"><span data-stu-id="01dd1-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="01dd1-192">Následující kód ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="01dd1-192">The following code shows how to do this.</span></span> <span data-ttu-id="01dd1-193">Tento kód vytvoří jinou službu WCF, která vrací <xref:System.ServiceModel.EndpointAddress10> objekt.</span><span class="sxs-lookup"><span data-stu-id="01dd1-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="01dd1-194">Toto je serializovatelná forma koncového bodu, který lze použít k vytvoření objektu úplného relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="01dd1-195">Následuje implementace této služby.</span><span class="sxs-lookup"><span data-stu-id="01dd1-195">The following is the implementation of this service.</span></span> <span data-ttu-id="01dd1-196">Tato implementace udržuje totokanálovou továrnu pro vytváření objektů relací.</span><span class="sxs-lookup"><span data-stu-id="01dd1-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="01dd1-197">Když `GetInstanceAddress` je volána, vytvoří kanál <xref:System.ServiceModel.EndpointAddress10> a vytvoří objekt, který odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="01dd1-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="01dd1-198"><xref:System.ServiceModel.EndpointAddress10>je datový typ, který lze vrátit klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01dd1-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="01dd1-199">Krok 3: Konfigurace a spuštění služeb WCF</span><span class="sxs-lookup"><span data-stu-id="01dd1-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="01dd1-200">Chcete-li tyto služby hostovat, budete muset provést následující dodatky k konfiguračnímu souboru serveru (web.config).</span><span class="sxs-lookup"><span data-stu-id="01dd1-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="01dd1-201">Přidejte `<client>` oddíl, který popisuje koncový bod pro objekt relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="01dd1-202">V tomto scénáři server také funguje jako klient a musí být nakonfigurován tak, aby to povolit.</span><span class="sxs-lookup"><span data-stu-id="01dd1-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="01dd1-203">V `<services>` části deklarujte koncové body služby pro objekt, který je určen pro vytváření a relaci.</span><span class="sxs-lookup"><span data-stu-id="01dd1-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="01dd1-204">To umožňuje klientovi komunikovat s koncovými <xref:System.ServiceModel.EndpointAddress10> body služby, získat a vytvořit kanál relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="01dd1-205">Následuje ukázkový konfigurační soubor s těmito nastaveními:</span><span class="sxs-lookup"><span data-stu-id="01dd1-205">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="01dd1-206">Přidejte následující řádky do konzolové aplikace, chcete-li službu sami hostovat, a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="01dd1-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="01dd1-207">Krok 4: Konfigurace klienta a volání služby</span><span class="sxs-lookup"><span data-stu-id="01dd1-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="01dd1-208">Nakonfigurujte klienta pro komunikaci se službami WCF provedením následujících položek v konfiguračním souboru aplikace projektu (app.config).</span><span class="sxs-lookup"><span data-stu-id="01dd1-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="01dd1-209">Chcete-li volat službu, přidejte kód do klienta provést následující:</span><span class="sxs-lookup"><span data-stu-id="01dd1-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="01dd1-210">Vytvořte kanál `ISessionBoundFactory` ke službě.</span><span class="sxs-lookup"><span data-stu-id="01dd1-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="01dd1-211">Pomocí kanálu vyvolat `ISessionBoundFactory` službu získat <xref:System.ServiceModel.EndpointAddress10> objekt.</span><span class="sxs-lookup"><span data-stu-id="01dd1-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="01dd1-212">Použijte <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu k získání objektu relace.</span><span class="sxs-lookup"><span data-stu-id="01dd1-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="01dd1-213">Volání `SetCurrentValue` a `GetCurrentValue` metody k prokázání, že zůstává stejný objekt instance se používá přes více volání.</span><span class="sxs-lookup"><span data-stu-id="01dd1-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01dd1-214">Viz také</span><span class="sxs-lookup"><span data-stu-id="01dd1-214">See also</span></span>

- [<span data-ttu-id="01dd1-215">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="01dd1-215">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="01dd1-216">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="01dd1-216">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="01dd1-217">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="01dd1-217">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="01dd1-218">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="01dd1-218">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
