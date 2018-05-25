---
title: 'Postup: Migrace spravovaného kódu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 187bff7c75ba2a0887e3c5728a484a9231936511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="72c4b-102">Postup: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="72c4b-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="72c4b-103">Windows Communication Foundation (WCF) je volba doporučené a zabezpečení přes distribuované modelu DCOM (Component Object) pro spravovaný kód volání mezi servery a klienty v distribuovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="72c4b-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="72c4b-104">Tento článek ukazuje, jak je možné migrovat kód z modelu DCOM do WCF pro následující scénáře.</span><span class="sxs-lookup"><span data-stu-id="72c4b-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="72c4b-105">Vzdálená služba vrátí klientovi pomocí hodnota objektu</span><span class="sxs-lookup"><span data-stu-id="72c4b-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="72c4b-106">Klient odešle službě Vzdálené podle hodnota objektu</span><span class="sxs-lookup"><span data-stu-id="72c4b-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="72c4b-107">Vzdálená služba vrátí odkaz na objekt podle-klientovi</span><span class="sxs-lookup"><span data-stu-id="72c4b-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="72c4b-108">Z bezpečnostních důvodů odeslání odkaz na objekt podle-klienta ke službě není povolena v WCF.</span><span class="sxs-lookup"><span data-stu-id="72c4b-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="72c4b-109">Ve službě WCF pomocí duplexní služby se dá dosáhnout scénáře, který vyžaduje konverzace přepínat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="72c4b-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="72c4b-110">Další informace o duplexní služby najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="72c4b-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="72c4b-111">Další informace o vytvoření služby WCF a klienty pro tyto služby najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md), [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [sestavování klientů](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="72c4b-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="72c4b-112">Příklad kódu DCOM</span><span class="sxs-lookup"><span data-stu-id="72c4b-112">DCOM example code</span></span>  
 <span data-ttu-id="72c4b-113">Pro tyto scénáře rozhraní DCOM, které jsou zobrazené pomocí WCF mít následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="72c4b-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="72c4b-114">Služba vrátí podle hodnota objektu</span><span class="sxs-lookup"><span data-stu-id="72c4b-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="72c4b-115">V tomto scénáři provedete volání služby a metoda vrátí objekt, který je předán-hodnota ze serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="72c4b-116">Tento scénář představuje následující volání COM:</span><span class="sxs-lookup"><span data-stu-id="72c4b-116">This scenario represents the following COM call:</span></span>  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="72c4b-117">V tomto scénáři klient obdrží kopii deserializovat objekt ze vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="72c4b-118">Klient mohou komunikovat s této místní kopie bez zpětné volání do služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="72c4b-119">Jinými slovy klient je zaručeno, že služba nebude zahrnuta žádným způsobem, pokud jsou volány metody na místní kopii.</span><span class="sxs-lookup"><span data-stu-id="72c4b-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="72c4b-120">WCF vždy vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření regulární služby WCF.</span><span class="sxs-lookup"><span data-stu-id="72c4b-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="72c4b-121">Krok 1: Definování rozhraní služby WCF</span><span class="sxs-lookup"><span data-stu-id="72c4b-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="72c4b-122">Definujte veřejné rozhraní pro službu WCF a označte ji pomocí [<xref:System.ServiceModel.ServiceContractAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="72c4b-123">Označit metody, kterou chcete vystavit klientů [<xref:System.ServiceModel.OperationContractAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="72c4b-124">Následující příklad ukazuje, pomocí těchto atributů k identifikaci rozhraní na straně serveru a metody rozhraní, které můžete volat klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="72c4b-125">Metoda použitá pro tento scénář je zobrazeny tučně.</span><span class="sxs-lookup"><span data-stu-id="72c4b-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="72c4b-126">Krok 2: Definování kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="72c4b-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="72c4b-127">Dále byste měli vytvořit kontraktu dat pro služby, která popisují, jak se budou vyměňovat data mezi službou a jeho klienty.</span><span class="sxs-lookup"><span data-stu-id="72c4b-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="72c4b-128">Třídy, které jsou popsané v kontrakt dat by měl být označen s [<xref:System.Runtime.Serialization.DataContractAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="72c4b-129">Jednotlivé vlastnosti nebo pole, které chcete viditelná pro klientské a serverové by měl být označen s [<xref:System.Runtime.Serialization.DataMemberAttribute>] atributu. Pokud chcete typy odvozené od třídy, v kontraktu dat mají být povolena, je potřeba určit pomocí [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atributu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="72c4b-130">WCF bude pouze serializaci nebo deserializaci typy identifikovat jako známé typy a typy v rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-130">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="72c4b-131">Pokud se pokusíte použít typ, který není typu známé, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="72c4b-131">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="72c4b-132">Další informace o kontraktech dat najdete v tématu [kontrakty dat](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="72c4b-132">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="72c4b-133">Krok 3: Implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="72c4b-133">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="72c4b-134">Další měli byste implementovat třídu služby WCF, který implementuje rozhraní, které jste definovali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="72c4b-134">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="72c4b-135">Krok 4: Konfigurace služby a klienta</span><span class="sxs-lookup"><span data-stu-id="72c4b-135">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="72c4b-136">Pokud chcete spustit službu WCF, musíte deklarovat koncový bod, který zpřístupňuje rozhraní této služby na konkrétní adrese URL, pomocí konkrétní vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="72c4b-136">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="72c4b-137">Vazba Určuje podrobnosti přenosu, kódování a protokol pro klienty a server, ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="72c4b-137">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="72c4b-138">Obvykle přidat vazby do konfiguračního souboru služby projektu (web.config).</span><span class="sxs-lookup"><span data-stu-id="72c4b-138">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="72c4b-139">Na obrázku je položka vazby pro službu příkladu:</span><span class="sxs-lookup"><span data-stu-id="72c4b-139">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="72c4b-140">Dále musíte nakonfigurovat klienta tak, aby odpovídaly informace o vazbě zadaná služba.</span><span class="sxs-lookup"><span data-stu-id="72c4b-140">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="72c4b-141">Uděláte to tak, přidejte následující k souboru konfigurace (app.config) aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-141">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="72c4b-142">Krok 5: Spouštění služby</span><span class="sxs-lookup"><span data-stu-id="72c4b-142">Step 5: Run the service</span></span>  
 <span data-ttu-id="72c4b-143">Nakonec můžete svým hostovat ho v konzolové aplikaci přidáním následující řádky do aplikace služby a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="72c4b-143">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="72c4b-144">Další informace o jiných způsobech hostovat aplikaci služby WCF [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="72c4b-144">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="72c4b-145">Krok 6: Zavolejte službu z klienta</span><span class="sxs-lookup"><span data-stu-id="72c4b-145">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="72c4b-146">Pro volání služby z klienta, budete muset vytvoření postupu kanálu pro službu a požádat o kanál, který vám umožní volat přímo `GetCustomer` metoda přímo z klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-146">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="72c4b-147">Kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku pro vás.</span><span class="sxs-lookup"><span data-stu-id="72c4b-147">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="72c4b-148">Vrácená hodnota z volání této metody se deserializovat kopii odpověď služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-148">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="72c4b-149">Klient odešle objekt podle hodnoty k serveru</span><span class="sxs-lookup"><span data-stu-id="72c4b-149">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="72c4b-150">V tomto scénáři klient odešle příslušný objekt na server, pomocí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="72c4b-150">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="72c4b-151">To znamená, že server dostanou kopii deserializovat objekt.</span><span class="sxs-lookup"><span data-stu-id="72c4b-151">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="72c4b-152">Server můžete volat metody pro tuto kopii a zaručit, že neexistuje žádná zpětného volání do kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-152">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="72c4b-153">Jak je uvedeno nahoře, normální WCF výměny dat jsou-hodnota.</span><span class="sxs-lookup"><span data-stu-id="72c4b-153">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="72c4b-154">To zaručuje, že volání metod v jednom z těchto objektů místně spustí, pouze – ho nebude vyvolání kódu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-154">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="72c4b-155">Tento scénář představuje následující volání metody COM:</span><span class="sxs-lookup"><span data-stu-id="72c4b-155">This scenario represents the following COM method call:</span></span>  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="72c4b-156">Tento scénář používá stejný kontrakt rozhraní a data služby, jak je znázorněno v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-156">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="72c4b-157">Kromě toho se klient a služba nakonfigurovat stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="72c4b-157">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="72c4b-158">V tomto příkladu se vytvoří kanál pro odeslání objektu a spusťte stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="72c4b-158">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="72c4b-159">V tomto příkladu klienta, který volá službě předávání pomocí hodnota objektu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="72c4b-159">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="72c4b-160">Metoda služby klienta bude volat v kontrakt služby se zobrazí tučným písmem:</span><span class="sxs-lookup"><span data-stu-id="72c4b-160">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="72c4b-161">Přidejte kód klientovi, který odešle objekt podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="72c4b-161">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="72c4b-162">Následující kód ukazuje, jak klient vytvoří nový objekt-hodnota zákazníka, vytvoří kanál ke komunikaci s `ICustomerManager` služby a odešle objekt zákazníka k němu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-162">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="72c4b-163">Objekt zákazníka bude serializován a odešle do služby, kde je deserializovat službou do novou kopii tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-163">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="72c4b-164">Žádné metody službu volání na tento objekt, budou spuštěny pouze místně na serveru. Je důležité si uvědomit, že tento kód ukazuje odesílání odvozený typ (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="72c4b-164">Any methods the service calls on this object will execute only locally on the server.It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="72c4b-165">Kontrakt služby očekává `Customer` objektu, ale data služby smlouvy používá [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atributu, která označuje, že `PremiumCustomer` je také povoleno.</span><span class="sxs-lookup"><span data-stu-id="72c4b-165">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="72c4b-166">WCF se nezdaří pokusy o serializaci nebo deserializaci žádným jiným typem prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-166">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="72c4b-167">Služba vrátí objekt odkazem</span><span class="sxs-lookup"><span data-stu-id="72c4b-167">The service returns an object by reference</span></span>  
 <span data-ttu-id="72c4b-168">Pro tento scénář klientská aplikace zavolá vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="72c4b-168">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="72c4b-169">Jak je uvedeno nahoře, služby WCF vždy vrátí objekt hodnotou.</span><span class="sxs-lookup"><span data-stu-id="72c4b-169">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="72c4b-170">Podobně jako výsledek však můžete dosáhnout pomocí <xref:System.ServiceModel.EndpointAddress10> třídy.</span><span class="sxs-lookup"><span data-stu-id="72c4b-170">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="72c4b-171"><xref:System.ServiceModel.EndpointAddress10> Je objekt serializovatelný podle hodnoty, které je možné klientem pro získání objektu relacemi odkazem na serveru.</span><span class="sxs-lookup"><span data-stu-id="72c4b-171">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="72c4b-172">Chování objektu odkazem ve WCF uvedené v tomto scénáři se liší od DCOM.</span><span class="sxs-lookup"><span data-stu-id="72c4b-172">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="72c4b-173">V modelu DCOM server může objekt odkazem vracet klientovi přímo a klient může volat metody tento objekt, které spustit na serveru.</span><span class="sxs-lookup"><span data-stu-id="72c4b-173">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="72c4b-174">Ve službě WCF ale objekt vrácený je vždy podle hodnota.</span><span class="sxs-lookup"><span data-stu-id="72c4b-174">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="72c4b-175">Klient musí mít tento objekt-hodnota reprezentována <xref:System.ServiceModel.EndpointAddress10> a použít ho k vytvoření vlastního objektu relacemi odkazem.</span><span class="sxs-lookup"><span data-stu-id="72c4b-175">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="72c4b-176">Volání metod klienta na objekt relacemi spustit na serveru. Jinými slovy tento objekt odkazem ve WCF je normální služby WCF, který je nakonfigurovaný jako relacemi.</span><span class="sxs-lookup"><span data-stu-id="72c4b-176">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="72c4b-177">Ve službě WCF relace je způsob korelace více zprávy odeslané mezi dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="72c4b-177">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="72c4b-178">To znamená, že Jakmile klient obdrží připojení k této službě, relace navázat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="72c4b-178">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="72c4b-179">Klient použije jeden jedinečný výskyt serverový objekt pro všechny jeho interakce v rámci této jedné relace.</span><span class="sxs-lookup"><span data-stu-id="72c4b-179">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="72c4b-180">Kontrakty relacemi WCF se podobá vzory požadavků a odpovědí orientovaná na připojení sítě.</span><span class="sxs-lookup"><span data-stu-id="72c4b-180">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="72c4b-181">Tento scénář je reprezentována metodu DCOM.</span><span class="sxs-lookup"><span data-stu-id="72c4b-181">This scenario is represented by the following DCOM method.</span></span>  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="72c4b-182">Krok 1: Definování rozhraní služby Sessionful WCF a implementace</span><span class="sxs-lookup"><span data-stu-id="72c4b-182">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="72c4b-183">Nejprve definujte rozhraní služby WCF, který obsahuje objekt relacemi.</span><span class="sxs-lookup"><span data-stu-id="72c4b-183">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="72c4b-184">V tomto kódu je označené relacemi objektu `ServiceContract` atribut, který ji identifikuje jako regulární rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="72c4b-184">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="72c4b-185">Kromě toho <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> je nastavena k označení, bude relacemi služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-185">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="72c4b-186">Následující kód ukazuje implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-186">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="72c4b-187">Služba je označena atributem [ServiceBehavior], a jeho vlastnost režim InstanceContextMode nastavením InstanceContextMode.PerSessions označíte, že jedinečné instance tohoto typu by měl být vytvořen pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="72c4b-187">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="72c4b-188">Krok 2: Definování factory služby WCF pro objekt relací</span><span class="sxs-lookup"><span data-stu-id="72c4b-188">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="72c4b-189">Služba, která vytvoří relacemi objekt musí být definovaný a implementovat.</span><span class="sxs-lookup"><span data-stu-id="72c4b-189">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="72c4b-190">Následující kód ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="72c4b-190">The following code shows how to do this.</span></span> <span data-ttu-id="72c4b-191">Tento kód vytvoří jiné služby WCF, který vrací <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-191">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="72c4b-192">Toto je serializovatelný formu koncový bod může použít k vytvoření objektu relace úplné.</span><span class="sxs-lookup"><span data-stu-id="72c4b-192">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="72c4b-193">Toto je implementací této služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-193">Following is the implementation of this service.</span></span> <span data-ttu-id="72c4b-194">Tato implementace udržuje singleton postup kanálu k vytváření relací objektů.</span><span class="sxs-lookup"><span data-stu-id="72c4b-194">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="72c4b-195">Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> objekt, který odkazuje na vzdálené adresy přidružené k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="72c4b-195">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="72c4b-196"><xref:System.ServiceModel.EndpointAddress10> je datový typ, který může být vrácen do klienta pomocí hodnota.</span><span class="sxs-lookup"><span data-stu-id="72c4b-196"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="72c4b-197">Krok 3: Konfigurace a spuštění služby WCF</span><span class="sxs-lookup"><span data-stu-id="72c4b-197">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="72c4b-198">K hostování těchto služeb, bude třeba, aby těmito přídavky do konfiguračního souboru serveru (web.config).</span><span class="sxs-lookup"><span data-stu-id="72c4b-198">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="72c4b-199">Přidat `<client>` oddíl, který popisuje koncový bod pro objekt relacemi.</span><span class="sxs-lookup"><span data-stu-id="72c4b-199">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="72c4b-200">V tomto scénáři serveru taky funguje jako klient a musí být nakonfigurován pro povolení této.</span><span class="sxs-lookup"><span data-stu-id="72c4b-200">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="72c4b-201">V `<services>` část, deklarovat koncové body služby objektu factory a sessionful.</span><span class="sxs-lookup"><span data-stu-id="72c4b-201">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="72c4b-202">To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvoření kanálu relací.</span><span class="sxs-lookup"><span data-stu-id="72c4b-202">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="72c4b-203">Následující příklad je konfigurační soubor s tímto nastavením:</span><span class="sxs-lookup"><span data-stu-id="72c4b-203">Following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="72c4b-204">Přidejte následující řádky do konzoly aplikace, k hostování samoobslužné služby a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72c4b-204">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="72c4b-205">Krok 4: Konfigurace klienta a volání služby</span><span class="sxs-lookup"><span data-stu-id="72c4b-205">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="72c4b-206">Konfigurace klienta ke komunikaci se službami WCF tím, že provedete následující položky v konfiguračním souboru projektu aplikace (app.config).</span><span class="sxs-lookup"><span data-stu-id="72c4b-206">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="72c4b-207">Pro volání služby, přidejte do klienta, proveďte následující kód:</span><span class="sxs-lookup"><span data-stu-id="72c4b-207">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="72c4b-208">Vytvoření kanálu pro `ISessionBoundFactory` služby.</span><span class="sxs-lookup"><span data-stu-id="72c4b-208">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="72c4b-209">Kanál používaná k volání `ISessionBoundFactory` služby získat <xref:System.ServiceModel.EndpointAddress10> bbject.</span><span class="sxs-lookup"><span data-stu-id="72c4b-209">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> bbject.</span></span>  
  
3.  <span data-ttu-id="72c4b-210">Použití <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu relacemi.</span><span class="sxs-lookup"><span data-stu-id="72c4b-210">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="72c4b-211">Volání `SetCurrentValue` a `GetCurrentValue` metody k předvedení zůstane stejné instance objektu se používá napříč více volání.</span><span class="sxs-lookup"><span data-stu-id="72c4b-211">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72c4b-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="72c4b-212">See Also</span></span>  
 [<span data-ttu-id="72c4b-213">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="72c4b-213">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="72c4b-214">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="72c4b-214">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="72c4b-215">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="72c4b-215">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="72c4b-216">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="72c4b-216">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
