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
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="250b9-102">Postup: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="250b9-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="250b9-103">Windows Communication Foundation (WCF) je doporučená a bezpečná volba pro volání spravovaného kódu mezi servery a klienty v distribuovaném prostředí pomocí modelu DCOM (Distributed Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="250b9-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="250b9-104">V tomto článku se dozvíte, jak migrovat kód z modelu DCOM do WCF v následujících scénářích.</span><span class="sxs-lookup"><span data-stu-id="250b9-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="250b9-105">Vzdálená služba vrátí klientovi objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="250b9-106">Klient pošle objekt po jeho hodnotě do vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="250b9-107">Vzdálená služba vrátí objekt podle odkazu na klienta.</span><span class="sxs-lookup"><span data-stu-id="250b9-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="250b9-108">Z bezpečnostních důvodů není v WCF povolený odeslání objektu podle odkazu z klienta na službu.</span><span class="sxs-lookup"><span data-stu-id="250b9-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="250b9-109">Scénář, který vyžaduje, aby se konverzace mezi klientem a serverem mohla docílit přes službu WCF pomocí duplexní služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="250b9-110">Další informace o duplexních službách najdete v tématu [duplexní služby](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="250b9-110">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="250b9-111">Další informace o vytváření služeb a klientů WCF pro tyto služby najdete v tématu [Základní programování WCF](../wcf/basic-wcf-programming.md), [navrhování a implementace služeb](../wcf/designing-and-implementing-services.md)a [vytváření klientů](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="250b9-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="250b9-112">Příklad kódu DCOM</span><span class="sxs-lookup"><span data-stu-id="250b9-112">DCOM example code</span></span>  
 <span data-ttu-id="250b9-113">V těchto scénářích mají rozhraní DCOM, která jsou znázorněná pomocí WCF, následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="250b9-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="250b9-114">Služba vrátí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="250b9-115">V tomto scénáři provedete volání služby a metoda IT vrátí objekt, který je předán podle hodnoty ze serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="250b9-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="250b9-116">Tento scénář představuje následující volání modelu COM:</span><span class="sxs-lookup"><span data-stu-id="250b9-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="250b9-117">V tomto scénáři klient obdrží deserializovanou kopii objektu ze vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="250b9-118">Klient může s touto místní kopií pracovat bez zpětného volání ke službě.</span><span class="sxs-lookup"><span data-stu-id="250b9-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="250b9-119">Jinými slovy, klient garantuje, že služba nebude nijak zapojena v případě, že budou volány metody místní kopie.</span><span class="sxs-lookup"><span data-stu-id="250b9-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="250b9-120">WCF vždycky vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření běžné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="250b9-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="250b9-121">Krok 1: definování rozhraní služby WCF</span><span class="sxs-lookup"><span data-stu-id="250b9-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="250b9-122">Definujte veřejné rozhraní pro službu WCF a označte ji atributem [<xref:System.ServiceModel.ServiceContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="250b9-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="250b9-123">Označte metody, které chcete zpřístupnit klientům s atributem [<xref:System.ServiceModel.OperationContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="250b9-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="250b9-124">Následující příklad ukazuje použití těchto atributů k identifikaci rozhraní na straně serveru a metod rozhraní, které může klient volat.</span><span class="sxs-lookup"><span data-stu-id="250b9-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="250b9-125">Metoda použitá pro tento scénář je zobrazena tučně.</span><span class="sxs-lookup"><span data-stu-id="250b9-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="250b9-126">Krok 2: Definování kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="250b9-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="250b9-127">Dále byste měli vytvořit kontrakt dat pro službu, který popíše, jak budou data vyměněna mezi službou a jejími klienty.</span><span class="sxs-lookup"><span data-stu-id="250b9-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="250b9-128">Třídy popsané v kontraktu dat by měly být označeny atributem<xref:System.Runtime.Serialization.DataContractAttribute>[].</span><span class="sxs-lookup"><span data-stu-id="250b9-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="250b9-129">Jednotlivé vlastnosti nebo pole, které chcete zobrazit pro klienta i server, by měly být označeny atributem<xref:System.Runtime.Serialization.DataMemberAttribute>[].</span><span class="sxs-lookup"><span data-stu-id="250b9-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="250b9-130">Chcete-li, aby byly typy odvozené od třídy v kontraktu dat povoleny, je nutné je identifikovat pomocí atributu [<xref:System.Runtime.Serialization.KnownTypeAttribute>].</span><span class="sxs-lookup"><span data-stu-id="250b9-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="250b9-131">Služba WCF provede pouze serializaci nebo deserializaci typů v rozhraní služby a typech identifikovaných jako známé typy.</span><span class="sxs-lookup"><span data-stu-id="250b9-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="250b9-132">Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="250b9-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="250b9-133">Další informace o kontraktech dat najdete v tématu [kontrakty dat](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="250b9-133">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="250b9-134">Krok 3: implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="250b9-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="250b9-135">Dále byste měli implementovat třídu služby WCF, která implementuje rozhraní, které jste definovali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="250b9-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="250b9-136">Krok 4: Konfigurace služby a klienta</span><span class="sxs-lookup"><span data-stu-id="250b9-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="250b9-137">Chcete-li spustit službu WCF, je nutné deklarovat koncový bod, který zpřístupňuje toto rozhraní služby na konkrétní adrese URL pomocí konkrétní vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="250b9-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="250b9-138">Vazba určuje podrobnosti přenosu, kódování a protokolu pro klienty a server, které mají být sdělovány.</span><span class="sxs-lookup"><span data-stu-id="250b9-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="250b9-139">Obvykle přidáte vazby do konfiguračního souboru projektu služby (Web. config).</span><span class="sxs-lookup"><span data-stu-id="250b9-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="250b9-140">Následující příklad ukazuje položku vazby pro ukázkovou službu:</span><span class="sxs-lookup"><span data-stu-id="250b9-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="250b9-141">Dál je potřeba nakonfigurovat klienta tak, aby odpovídal informacím o vazbě zadaným službou.</span><span class="sxs-lookup"><span data-stu-id="250b9-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="250b9-142">Chcete-li to provést, přidejte následující do konfiguračního souboru aplikace klienta (App. config).</span><span class="sxs-lookup"><span data-stu-id="250b9-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="250b9-143">Krok 5: spuštění služby</span><span class="sxs-lookup"><span data-stu-id="250b9-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="250b9-144">Nakonec ho můžete sami hostovat v konzolové aplikaci přidáním následujících řádků do aplikace služby a spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="250b9-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="250b9-145">Další informace o jiných způsobech hostování aplikace služby WCF, [hostování služeb](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="250b9-145">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="250b9-146">Krok 6: volání služby z klienta</span><span class="sxs-lookup"><span data-stu-id="250b9-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="250b9-147">Chcete-li volat službu z klienta, je nutné vytvořit továrnu kanálu pro službu a požádat o kanál, který vám umožní přímo volat `GetCustomer` metodu přímo z klienta.</span><span class="sxs-lookup"><span data-stu-id="250b9-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="250b9-148">Kanál implementuje rozhraní služby a zpracovává základní logiku požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="250b9-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="250b9-149">Návratovou hodnotou z tohoto volání metody je deserializovaná kopie odpovědi služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="250b9-150">Klient pošle objektu podle hodnoty na server.</span><span class="sxs-lookup"><span data-stu-id="250b9-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="250b9-151">V tomto scénáři klient pošle objekt na server podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="250b9-152">To znamená, že server dostane deserializovanou kopii objektu.</span><span class="sxs-lookup"><span data-stu-id="250b9-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="250b9-153">Server může volat metody v této kopii a zaručit, že se nejedná o zpětné volání do klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="250b9-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="250b9-154">Jak už bylo zmíněno dříve, běžné výměny dat WCF jsou podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="250b9-155">To zaručuje, že volající metody na jednom z těchto objektů se spouští pouze místně – nevyvolává kód na klientovi.</span><span class="sxs-lookup"><span data-stu-id="250b9-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="250b9-156">Tento scénář představuje následující volání metody COM:</span><span class="sxs-lookup"><span data-stu-id="250b9-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="250b9-157">V tomto scénáři se používá stejné rozhraní služby a kontrakt dat, jak je znázorněno v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="250b9-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="250b9-158">Kromě toho se klient a služba nakonfigurují stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="250b9-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="250b9-159">V tomto příkladu je vytvořen kanál pro odeslání objektu a spuštění stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="250b9-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="250b9-160">V tomto příkladu však vytvoříte klienta, který bude volat službu, a předáte objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="250b9-161">Metoda služby, kterou klient bude volat v kontraktu služby, je zobrazená tučně:</span><span class="sxs-lookup"><span data-stu-id="250b9-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="250b9-162">Přidání kódu do klienta odesílajícího objekt podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="250b9-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="250b9-163">Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka podle hodnoty, vytvoří kanál ke komunikaci se `ICustomerManager` službou a odešle do něj objekt zákazníka.</span><span class="sxs-lookup"><span data-stu-id="250b9-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="250b9-164">Objekt zákazníka bude serializován a odeslán službě, kde je deserializována službou do nové kopie tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="250b9-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="250b9-165">Jakékoli metody, které služba volá s tímto objektem, se spustí jenom místně na serveru.</span><span class="sxs-lookup"><span data-stu-id="250b9-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="250b9-166">Je důležité si uvědomit, že tento kód znázorňuje odeslání odvozeného typu (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="250b9-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="250b9-167">Kontrakt služby očekává `Customer` objekt, ale kontrakt dat služby používá atribut [<xref:System.Runtime.Serialization.KnownTypeAttribute>] k označení toho, že `PremiumCustomer` je povolen také.</span><span class="sxs-lookup"><span data-stu-id="250b9-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="250b9-168">Služba WCF selže při pokusu o serializaci nebo deserializaci jiného typu prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="250b9-169">Služba vrátí objekt podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="250b9-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="250b9-170">V tomto scénáři klientská aplikace provede volání vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby na klienta.</span><span class="sxs-lookup"><span data-stu-id="250b9-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="250b9-171">Jak bylo zmíněno dříve, služby WCF vždy vracejí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="250b9-172">Podobný výsledek však můžete dosáhnout použitím <xref:System.ServiceModel.EndpointAddress10> třídy.</span><span class="sxs-lookup"><span data-stu-id="250b9-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="250b9-173"><xref:System.ServiceModel.EndpointAddress10> Je serializovatelný objekt podle hodnoty, který může klient použít k získání relace odkazem objektu na serveru.</span><span class="sxs-lookup"><span data-stu-id="250b9-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="250b9-174">Chování objektu podle odkazu ve službě WCF zobrazené v tomto scénáři se liší od modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="250b9-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="250b9-175">V modelu DCOM může server vrátit objekt podle odkazu přímo klientovi a klient může volat metody tohoto objektu, které jsou spuštěny na serveru.</span><span class="sxs-lookup"><span data-stu-id="250b9-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="250b9-176">Ve službě WCF je však vrácen objekt vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="250b9-177">Klient musí přijmout objekt podle hodnoty reprezentovaný <xref:System.ServiceModel.EndpointAddress10> a použít ho k vytvoření vlastního relace pomocí objektu s odkazem.</span><span class="sxs-lookup"><span data-stu-id="250b9-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="250b9-178">Metoda klienta volá objekt relace spuštěný na serveru. Jinými slovy je tento objekt odkazem na WCF normální službu WCF, která je nakonfigurovaná tak, aby byla relace.</span><span class="sxs-lookup"><span data-stu-id="250b9-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="250b9-179">V rámci WCF je relace způsob, jak korelovat více zpráv posílaných mezi dvěma koncovými body.</span><span class="sxs-lookup"><span data-stu-id="250b9-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="250b9-180">To znamená, že jakmile klient získá připojení k této službě, bude vytvořena relace mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="250b9-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="250b9-181">Klient bude používat jednu jedinečnou instanci objektu na straně serveru pro všechny interakce v rámci této jediné relace.</span><span class="sxs-lookup"><span data-stu-id="250b9-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="250b9-182">Relace WCF jsou podobné vzorům pro požadavky na síťový požadavek a odpověď orientovaný na připojení.</span><span class="sxs-lookup"><span data-stu-id="250b9-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="250b9-183">Tento scénář je reprezentován následující metodou DCOM.</span><span class="sxs-lookup"><span data-stu-id="250b9-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="250b9-184">Krok 1: definování relace rozhraní WCF a implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="250b9-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="250b9-185">Nejdřív definujte rozhraní služby WCF, které obsahuje objekt sessioning.</span><span class="sxs-lookup"><span data-stu-id="250b9-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="250b9-186">V tomto kódu je objekt relace označen `ServiceContract` atributem, který ho identifikuje jako regulární rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="250b9-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="250b9-187"><xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> Vlastnost je navíc nastavená tak, aby označovala, že se jedná o relaci služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="250b9-188">Následující kód ukazuje implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="250b9-189">Služba je označena atributem [ServiceBehavior] a jeho vlastnost InstanceContextMode je nastavena na hodnotu InstanceContextMode. PerSessions, aby označovala, že pro každou relaci by měla být vytvořena jedinečná instance tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="250b9-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="250b9-190">Krok 2: definování služby WCF Factory pro objekt sessioning</span><span class="sxs-lookup"><span data-stu-id="250b9-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="250b9-191">Služba, která vytváří objekt relace, musí být definovaná a implementovaná.</span><span class="sxs-lookup"><span data-stu-id="250b9-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="250b9-192">Následující kód ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="250b9-192">The following code shows how to do this.</span></span> <span data-ttu-id="250b9-193">Tento kód vytvoří jinou službu WCF, která vrací <xref:System.ServiceModel.EndpointAddress10> objekt.</span><span class="sxs-lookup"><span data-stu-id="250b9-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="250b9-194">Jedná se o serializovatelný tvar koncového bodu, pomocí kterého lze vytvořit objekt s úplnými relacemi.</span><span class="sxs-lookup"><span data-stu-id="250b9-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="250b9-195">Níže je tato implementace této služby.</span><span class="sxs-lookup"><span data-stu-id="250b9-195">The following is the implementation of this service.</span></span> <span data-ttu-id="250b9-196">Tato implementace udržuje objekt pro vytváření relací s jedním prvkem.</span><span class="sxs-lookup"><span data-stu-id="250b9-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="250b9-197">Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> objekt, který odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="250b9-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="250b9-198"><xref:System.ServiceModel.EndpointAddress10>je datový typ, který může být vrácen klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="250b9-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="250b9-199">Krok 3: konfigurace a spuštění služeb WCF</span><span class="sxs-lookup"><span data-stu-id="250b9-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="250b9-200">Chcete-li hostovat tyto služby, budete muset provést následující přidání do konfiguračního souboru serveru (Web. config).</span><span class="sxs-lookup"><span data-stu-id="250b9-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="250b9-201">Přidejte `<client>` část, která popisuje koncový bod objektu Session.</span><span class="sxs-lookup"><span data-stu-id="250b9-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="250b9-202">V tomto scénáři server funguje taky jako klient a musí se nakonfigurovat, aby se povolil.</span><span class="sxs-lookup"><span data-stu-id="250b9-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="250b9-203">V `<services>` části deklarujete koncové body služby objektu pro vytváření a relaci.</span><span class="sxs-lookup"><span data-stu-id="250b9-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="250b9-204">To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvořit kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="250b9-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="250b9-205">Následuje příklad konfiguračního souboru s těmito nastaveními:</span><span class="sxs-lookup"><span data-stu-id="250b9-205">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="250b9-206">Přidejte následující řádky do konzolové aplikace, pro samoobslužnou hostování služby a aplikaci spusťte.</span><span class="sxs-lookup"><span data-stu-id="250b9-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="250b9-207">Krok 4: Konfigurace klienta a volání služby</span><span class="sxs-lookup"><span data-stu-id="250b9-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="250b9-208">Nakonfigurujte klienta ke komunikaci se službami WCF tím, že v konfiguračním souboru aplikace projektu (App. config) provedete následující záznamy.</span><span class="sxs-lookup"><span data-stu-id="250b9-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="250b9-209">Chcete-li zavolat službu, přidejte do klienta kód, abyste mohli provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="250b9-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="250b9-210">Vytvořte kanál ke `ISessionBoundFactory` službě.</span><span class="sxs-lookup"><span data-stu-id="250b9-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="250b9-211">Použití kanálu k vyvolání `ISessionBoundFactory` služby a získání <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="250b9-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="250b9-212">Použijte <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu relace.</span><span class="sxs-lookup"><span data-stu-id="250b9-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="250b9-213">Zavolejte metody `SetCurrentValue` a `GetCurrentValue` , abyste ukázali, že zůstane stejná instance objektu použita v rámci více volání.</span><span class="sxs-lookup"><span data-stu-id="250b9-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="250b9-214">Viz také</span><span class="sxs-lookup"><span data-stu-id="250b9-214">See also</span></span>

- [<span data-ttu-id="250b9-215">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="250b9-215">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="250b9-216">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="250b9-216">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="250b9-217">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="250b9-217">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="250b9-218">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="250b9-218">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
