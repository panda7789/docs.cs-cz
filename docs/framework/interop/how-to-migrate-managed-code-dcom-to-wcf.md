---
title: 'Postupy: Migrace spravovaného kódu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74acea566e4b0e407e86cb67d3f521f18c2d68af
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307714"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="5a49c-102">Postupy: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="5a49c-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="5a49c-103">Windows Communication Foundation (WCF) je volba doporučené a zabezpečené přes distribuované DCOM Component Object Model () pro spravovaný kód volání mezi servery a klienty v distribuovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="5a49c-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="5a49c-104">Tento článek popisuje, jak vám migrace kódu z modelu DCOM do WCF v následujících scénářích.</span><span class="sxs-lookup"><span data-stu-id="5a49c-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="5a49c-105">Vzdálená služba vrátí objektu podle hodnoty do klienta</span><span class="sxs-lookup"><span data-stu-id="5a49c-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="5a49c-106">Klient odešle objektu podle hodnoty do vzdálené služby</span><span class="sxs-lookup"><span data-stu-id="5a49c-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="5a49c-107">Vzdálená služba vrátí klientovi pomocí – odkaz na objekt</span><span class="sxs-lookup"><span data-stu-id="5a49c-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="5a49c-108">Z bezpečnostních důvodů odesílání pomocí – odkaz na objekt z klienta do služby není povolena ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="5a49c-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="5a49c-109">Tento scénář vyžaduje konverzace vpřed a zpět mezi klientem a serverem lze dosáhnout pomocí duplexní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5a49c-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="5a49c-110">Další informace o duplexní služby najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="5a49c-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="5a49c-111">Další podrobnosti o vytvoření služby WCF a klienty pro tyto služby najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md), [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [sestavování klientů](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5a49c-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="5a49c-112">Příklad kódu DCOM</span><span class="sxs-lookup"><span data-stu-id="5a49c-112">DCOM example code</span></span>  
 <span data-ttu-id="5a49c-113">Pro tyto scénáře, které jsou znázorněny pomocí technologie WCF rozhraní DCOM mají následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="5a49c-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="5a49c-114">Tato služba vrátí objektu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="5a49c-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="5a49c-115">V tomto scénáři provedete volání služby a metoda vrátí objekt, který je předán podle hodnoty ze serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="5a49c-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="5a49c-116">Tento scénář představuje následující volání COM:</span><span class="sxs-lookup"><span data-stu-id="5a49c-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="5a49c-117">V tomto scénáři klient obdrží kopii objekt deserializovaný ze vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="5a49c-118">Klient může interagovat s tuto místní kopii bez nutnosti volat zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="5a49c-119">Jinými slovy klient je zaručeno, že služba nebude možné zahrnutí žádným způsobem při volání metody v místní kopii.</span><span class="sxs-lookup"><span data-stu-id="5a49c-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="5a49c-120">WCF vždy vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření regulárního služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5a49c-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="5a49c-121">Krok 1: Definování rozhraní služby WCF</span><span class="sxs-lookup"><span data-stu-id="5a49c-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="5a49c-122">Definování veřejného rozhraní pro službu WCF a označte ji pomocí [<xref:System.ServiceModel.ServiceContractAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="5a49c-123">Označení metody, kterou chcete zpřístupnit klientům s [<xref:System.ServiceModel.OperationContractAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="5a49c-124">Následující příklad ukazuje použití těchto atributů k určení rozhraní na straně serveru a klienta můžete volat metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5a49c-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="5a49c-125">Metoda použitá v tomto scénáři se zobrazí tučným písmem.</span><span class="sxs-lookup"><span data-stu-id="5a49c-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="5a49c-126">Krok 2: Definování kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="5a49c-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="5a49c-127">Dále byste měli vytvořit kontraktu dat pro službu, která popisuje výměna dat mezi službou a klienty.</span><span class="sxs-lookup"><span data-stu-id="5a49c-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="5a49c-128">Třídy je popsáno v kontraktu dat by měl být označeny atributem [<xref:System.Runtime.Serialization.DataContractAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="5a49c-129">Jednotlivé vlastnosti nebo pole má viditelná pro klientské a serverové by měly být označené [<xref:System.Runtime.Serialization.DataMemberAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="5a49c-130">Pokud chcete typy odvozené od třídy v kontraktu dat. Chcete-li být povoleny, je potřeba určit pomocí [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="5a49c-131">WCF se pouze serializaci nebo deserializaci typy v rozhraní služby a typy, které jsou identifikovány jako známé typy.</span><span class="sxs-lookup"><span data-stu-id="5a49c-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="5a49c-132">Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5a49c-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="5a49c-133">Další informace o kontraktech dat najdete v tématu [kontraktů dat](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="5a49c-133">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="5a49c-134">Krok 3: Implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="5a49c-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="5a49c-135">V dalším kroku měli byste implementovat třídu služby WCF, která implementuje rozhraní, které jste definovali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="5a49c-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="5a49c-136">Krok 4: Nakonfigurujte službu a klienta</span><span class="sxs-lookup"><span data-stu-id="5a49c-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="5a49c-137">Pokud chcete spustit službu WCF, musíte deklarovat koncový bod, který zpřístupňuje rozhraní služby na konkrétní adrese URL použití konkrétní vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="5a49c-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="5a49c-138">Vazbu určuje přenos, kódování a protokolu podrobnosti pro klienty a serverem komunikovat.</span><span class="sxs-lookup"><span data-stu-id="5a49c-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="5a49c-139">Obvykle přidáte vazby do konfiguračního souboru projektu služby (web.config).</span><span class="sxs-lookup"><span data-stu-id="5a49c-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="5a49c-140">Následuje ukázka zadání vazby služby příklad:</span><span class="sxs-lookup"><span data-stu-id="5a49c-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="5a49c-141">Dále je třeba nakonfigurovat klienta tak, aby odpovídaly informace o vazbě určeného službou.</span><span class="sxs-lookup"><span data-stu-id="5a49c-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="5a49c-142">Uděláte to tak, přidejte následující k souboru konfigurace (app.config) klienta aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a49c-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="5a49c-143">Krok 5: Spuštění služby</span><span class="sxs-lookup"><span data-stu-id="5a49c-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="5a49c-144">Nakonec můžete svým hostovat ho v konzolové aplikaci, přidáním následující řádky do service app a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a49c-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="5a49c-145">Další informace o dalších způsobech k hostování aplikace služby WCF [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="5a49c-145">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="5a49c-146">Krok 6: Volání služby z klienta</span><span class="sxs-lookup"><span data-stu-id="5a49c-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="5a49c-147">Volání služby z klienta, budete muset vytvořit objekt pro vytváření kanálů pro službu a požádat o kanálu, která vám umožní volat přímo `GetCustomer` metoda přímo z klienta.</span><span class="sxs-lookup"><span data-stu-id="5a49c-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="5a49c-148">Kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku za vás.</span><span class="sxs-lookup"><span data-stu-id="5a49c-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="5a49c-149">Návratová hodnota z volání této metody je deserializovat kopie odezvy služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="5a49c-150">Klient odešle objekt podle hodnoty do serveru</span><span class="sxs-lookup"><span data-stu-id="5a49c-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="5a49c-151">V tomto scénáři klient zasílá objektu na server, podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a49c-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="5a49c-152">To znamená, že server dostanou kopii deserializovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="5a49c-153">Server může volat metody na tuto kopii a zaručit, že není žádná zpětné volání do kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="5a49c-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="5a49c-154">Jak už bylo zmíněno dříve, jsou normální WCF výměny dat podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a49c-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="5a49c-155">Zaručí se tak, že volání metody v jednom z těchto objektů místně spustí, pouze – nebude volat kód na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="5a49c-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="5a49c-156">Tento scénář představuje následující volání metody COM:</span><span class="sxs-lookup"><span data-stu-id="5a49c-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="5a49c-157">Tento scénář používá stejný kontrakt rozhraní a dat služby, jak je znázorněno v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="5a49c-158">Kromě toho klient a služba se nakonfigurují stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5a49c-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="5a49c-159">V tomto příkladu se vytvoří kanál pro odesílání objektu a spustit stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5a49c-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="5a49c-160">Ale v tomto příkladu vytvoříte klienta, který volá služby předávání objektu podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a49c-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="5a49c-161">Metoda služby, které bude klient volat v kontraktu služby se zobrazí tučně:</span><span class="sxs-lookup"><span data-stu-id="5a49c-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="5a49c-162">Přidání kódu do klienta, který odešle objekt podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="5a49c-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="5a49c-163">Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka podle hodnoty, vytvoří kanál, ke komunikaci s `ICustomerManager` služby a odešle objekt zákazníka.</span><span class="sxs-lookup"><span data-stu-id="5a49c-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="5a49c-164">Objekt zákazníka se serializovat a odešle do služby, kde je deserializovat službou do novou kopii tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="5a49c-165">Všechny metody volá služby na tento objekt se spustí jenom místně na serveru.</span><span class="sxs-lookup"><span data-stu-id="5a49c-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="5a49c-166">Je důležité si uvědomit, že tento kód ukazuje odesílání odvozeného typu (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="5a49c-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="5a49c-167">Očekává, že kontrakt služby `Customer` objektu, ale data služby smlouvy používá [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atribut označuje, že `PremiumCustomer` je také povolena.</span><span class="sxs-lookup"><span data-stu-id="5a49c-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="5a49c-168">WCF se nezdaří pokusy o serializaci nebo deserializaci jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="5a49c-169">Služba vrátí objekt odkazem.</span><span class="sxs-lookup"><span data-stu-id="5a49c-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="5a49c-170">V tomto scénáři klientské aplikace volá vzdálenou službu a metoda vrátí objekt, který se předá odkazem ze služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="5a49c-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="5a49c-171">Jak už bylo zmíněno dříve, služby WCF se kdykoli vrátit objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a49c-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="5a49c-172">Však můžete podobného výsledku dosáhnout pomocí <xref:System.ServiceModel.EndpointAddress10> třídy.</span><span class="sxs-lookup"><span data-stu-id="5a49c-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="5a49c-173"><xref:System.ServiceModel.EndpointAddress10> Je objekt serializovatelný podle hodnoty, který je možné k získání objektu s relacemi odkazem na serveru klientem.</span><span class="sxs-lookup"><span data-stu-id="5a49c-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="5a49c-174">Chování pomocí odkazu na objekt ve službě WCF je znázorněno v tomto scénáři se liší od modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="5a49c-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="5a49c-175">V modelu DCOM server vrátit objekt podle odkazu do klienta přímo a klient může volat metody tohoto objektu, které se spustí na serveru.</span><span class="sxs-lookup"><span data-stu-id="5a49c-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="5a49c-176">Ve službě WCF ale objekt vrácený je vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a49c-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="5a49c-177">Klient musí přijmout tento objekt podle hodnoty, reprezentovaný <xref:System.ServiceModel.EndpointAddress10> a použijte ji k vytvoření vlastní objekt s relacemi podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="5a49c-178">Volání metody klienta s relacemi objektu spustit na serveru. Jinými slovy tento objekt podle odkazu ve službě WCF je běžné služby WCF, který je nakonfigurován s relacemi.</span><span class="sxs-lookup"><span data-stu-id="5a49c-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="5a49c-179">Relace ve službě WCF, je způsob, jak korelace více posílané mezi dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="5a49c-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="5a49c-180">To znamená, že Jakmile klient získá připojení pro tuto službu, relace navázat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="5a49c-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="5a49c-181">Klient použije jeden jedinečný instance objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace.</span><span class="sxs-lookup"><span data-stu-id="5a49c-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="5a49c-182">Kontrakty relací WCF jsou podobné vzory požadavku nebo odpovědi síťové připojení objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="5a49c-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="5a49c-183">Tento scénář je reprezentován metodu modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="5a49c-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="5a49c-184">Krok 1: Definování rozhraní služby WCF který neobsahuje relace a implementaci</span><span class="sxs-lookup"><span data-stu-id="5a49c-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="5a49c-185">Nejprve definujte rozhraní služby WCF, které obsahuje objekt s relacemi.</span><span class="sxs-lookup"><span data-stu-id="5a49c-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="5a49c-186">V tomto kódu je označeno objekt s relacemi `ServiceContract` atribut, který ji identifikuje jako regulární rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5a49c-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="5a49c-187">Kromě toho <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> je nastavena na označení bude s relacemi service.</span><span class="sxs-lookup"><span data-stu-id="5a49c-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="5a49c-188">Následující kód ukazuje implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="5a49c-189">Služba je označená pomocí atributu [ServiceBehavior] a jeho vlastností InstanceContextMode nastavenou na InstanceContextMode.PerSessions udávající, že jedinečné instance tohoto typu by měl být vytvářeny pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="5a49c-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="5a49c-190">Krok 2: Definovat objekt pro vytváření služby WCF u objektu s relacemi</span><span class="sxs-lookup"><span data-stu-id="5a49c-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="5a49c-191">Služba, která vytvoří objekt s relacemi musí být definován a implementovat.</span><span class="sxs-lookup"><span data-stu-id="5a49c-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="5a49c-192">Následující kód ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="5a49c-192">The following code shows how to do this.</span></span> <span data-ttu-id="5a49c-193">Tento kód vytvoří jiné služby WCF, který vrátí <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="5a49c-194">Toto je serializovatelného tvaru koncového bodu může použít k vytvoření objektu relace režim.</span><span class="sxs-lookup"><span data-stu-id="5a49c-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="5a49c-195">Tady je implementace této služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-195">Following is the implementation of this service.</span></span> <span data-ttu-id="5a49c-196">Tato implementace udržuje typu singleton objektu pro vytváření kanálů vytváření relací objektů.</span><span class="sxs-lookup"><span data-stu-id="5a49c-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="5a49c-197">Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> , která odkazuje na vzdálenou adresu přidružené k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <xref:System.ServiceModel.EndpointAddress10> <span data-ttu-id="5a49c-198">je datový typ, který může být vrácen do klienta podle hodnota.</span><span class="sxs-lookup"><span data-stu-id="5a49c-198">is a data type that can be returned to the client by-value.</span></span>  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="5a49c-199">Krok 3: Konfigurace a spuštění služeb WCF</span><span class="sxs-lookup"><span data-stu-id="5a49c-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="5a49c-200">K hostování těchto služeb, je potřeba provést následující položky na server konfigurační soubor (web.config).</span><span class="sxs-lookup"><span data-stu-id="5a49c-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="5a49c-201">Přidat `<client>` část popisující koncový bod pro objekt s relacemi.</span><span class="sxs-lookup"><span data-stu-id="5a49c-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="5a49c-202">V tomto scénáři server také funguje jako klient a musí být nakonfigurované tak, aby to.</span><span class="sxs-lookup"><span data-stu-id="5a49c-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="5a49c-203">V `<services>` části, deklarujte koncových bodů služby pro objekt factory a který neobsahuje relace.</span><span class="sxs-lookup"><span data-stu-id="5a49c-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="5a49c-204">To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvořte kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="5a49c-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="5a49c-205">Tady je příklad souboru konfigurace s tímto nastavením:</span><span class="sxs-lookup"><span data-stu-id="5a49c-205">Following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="5a49c-206">Přidejte následující řádky do konzolové aplikace, k hostování na vlastním serveru služby a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5a49c-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="5a49c-207">Krok 4: Konfigurace klienta a volání služby</span><span class="sxs-lookup"><span data-stu-id="5a49c-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="5a49c-208">Konfigurace klienta ke komunikaci se službami WCF tím, že následující položky projektu konfiguračního souboru aplikace (app.config).</span><span class="sxs-lookup"><span data-stu-id="5a49c-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="5a49c-209">K vyvolání služby, přidejte kód do klienta provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="5a49c-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="5a49c-210">Vytvoření kanálu pro `ISessionBoundFactory` služby.</span><span class="sxs-lookup"><span data-stu-id="5a49c-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="5a49c-211">Používaná k volání kanálu `ISessionBoundFactory` služby získání <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="5a49c-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="5a49c-212">Použití <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu s relacemi.</span><span class="sxs-lookup"><span data-stu-id="5a49c-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="5a49c-213">Volání `SetCurrentValue` a `GetCurrentValue` metody k předvedení zůstává stejná instance objektu se používá napříč více volání.</span><span class="sxs-lookup"><span data-stu-id="5a49c-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a49c-214">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a49c-214">See also</span></span>

- [<span data-ttu-id="5a49c-215">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="5a49c-215">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="5a49c-216">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="5a49c-216">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="5a49c-217">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="5a49c-217">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="5a49c-218">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="5a49c-218">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
