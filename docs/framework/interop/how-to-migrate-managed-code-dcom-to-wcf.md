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
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="c977f-103">Postupy: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="c977f-103">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="c977f-104">Windows Communication Foundation (WCF) je doporučená a bezpečná volba pro volání spravovaného kódu mezi servery a klienty v distribuovaném prostředí pomocí modelu DCOM (Distributed Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="c977f-104">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="c977f-105">V tomto článku se dozvíte, jak migrovat kód z modelu DCOM do WCF v následujících scénářích.</span><span class="sxs-lookup"><span data-stu-id="c977f-105">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="c977f-106">Vzdálená služba vrátí klientovi objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-106">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="c977f-107">Klient pošle objekt po jeho hodnotě do vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-107">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="c977f-108">Vzdálená služba vrátí objekt podle odkazu na klienta.</span><span class="sxs-lookup"><span data-stu-id="c977f-108">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="c977f-109">Z bezpečnostních důvodů není v WCF povolený odeslání objektu podle odkazu z klienta na službu.</span><span class="sxs-lookup"><span data-stu-id="c977f-109">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="c977f-110">Scénář, který vyžaduje, aby se konverzace mezi klientem a serverem mohla docílit přes službu WCF pomocí duplexní služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-110">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="c977f-111">Další informace o duplexních službách najdete v tématu [duplexní služby](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="c977f-111">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="c977f-112">Další informace o vytváření služeb a klientů WCF pro tyto služby najdete v tématu [Základní programování WCF](../wcf/basic-wcf-programming.md), [navrhování a implementace služeb](../wcf/designing-and-implementing-services.md)a [vytváření klientů](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c977f-112">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="c977f-113">Příklad kódu DCOM</span><span class="sxs-lookup"><span data-stu-id="c977f-113">DCOM example code</span></span>  
 <span data-ttu-id="c977f-114">V těchto scénářích mají rozhraní DCOM, která jsou znázorněná pomocí WCF, následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="c977f-114">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="c977f-115">Služba vrátí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-115">The service returns an object by-value</span></span>  
 <span data-ttu-id="c977f-116">V tomto scénáři provedete volání služby a metoda IT vrátí objekt, který je předán podle hodnoty ze serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="c977f-116">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="c977f-117">Tento scénář představuje následující volání modelu COM:</span><span class="sxs-lookup"><span data-stu-id="c977f-117">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="c977f-118">V tomto scénáři klient obdrží deserializovanou kopii objektu ze vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-118">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="c977f-119">Klient může s touto místní kopií pracovat bez zpětného volání ke službě.</span><span class="sxs-lookup"><span data-stu-id="c977f-119">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="c977f-120">Jinými slovy, klient garantuje, že služba nebude nijak zapojena v případě, že budou volány metody místní kopie.</span><span class="sxs-lookup"><span data-stu-id="c977f-120">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="c977f-121">WCF vždycky vrátí objekty ze služby podle hodnoty, takže následující kroky popisují vytvoření běžné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c977f-121">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="c977f-122">Krok 1: definování rozhraní služby WCF</span><span class="sxs-lookup"><span data-stu-id="c977f-122">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="c977f-123">Definujte veřejné rozhraní pro službu WCF a označte ji <xref:System.ServiceModel.ServiceContractAttribute> atributem [].</span><span class="sxs-lookup"><span data-stu-id="c977f-123">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="c977f-124">Označte metody, které chcete zpřístupnit klientům s <xref:System.ServiceModel.OperationContractAttribute> atributem [].</span><span class="sxs-lookup"><span data-stu-id="c977f-124">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="c977f-125">Následující příklad ukazuje použití těchto atributů k identifikaci rozhraní na straně serveru a metod rozhraní, které může klient volat.</span><span class="sxs-lookup"><span data-stu-id="c977f-125">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="c977f-126">Metoda použitá pro tento scénář je zobrazena tučně.</span><span class="sxs-lookup"><span data-stu-id="c977f-126">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="c977f-127">Krok 2: Definování kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="c977f-127">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="c977f-128">Dále byste měli vytvořit kontrakt dat pro službu, který popíše, jak budou data vyměněna mezi službou a jejími klienty.</span><span class="sxs-lookup"><span data-stu-id="c977f-128">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="c977f-129">Třídy popsané v kontraktu dat by měly být označeny <xref:System.Runtime.Serialization.DataContractAttribute> atributem [].</span><span class="sxs-lookup"><span data-stu-id="c977f-129">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="c977f-130">Jednotlivé vlastnosti nebo pole, které chcete zobrazit pro klienta i server, by měly být označeny <xref:System.Runtime.Serialization.DataMemberAttribute> atributem [].</span><span class="sxs-lookup"><span data-stu-id="c977f-130">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="c977f-131">Chcete-li, aby byly typy odvozené od třídy v kontraktu dat povoleny, je nutné je identifikovat pomocí atributu [ <xref:System.Runtime.Serialization.KnownTypeAttribute> ].</span><span class="sxs-lookup"><span data-stu-id="c977f-131">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="c977f-132">Služba WCF provede pouze serializaci nebo deserializaci typů v rozhraní služby a typech identifikovaných jako známé typy.</span><span class="sxs-lookup"><span data-stu-id="c977f-132">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="c977f-133">Pokud se pokusíte použít typ, který není známý typ, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c977f-133">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="c977f-134">Další informace o kontraktech dat najdete v tématu [kontrakty dat](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c977f-134">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="c977f-135">Krok 3: implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="c977f-135">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="c977f-136">Dále byste měli implementovat třídu služby WCF, která implementuje rozhraní, které jste definovali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="c977f-136">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="c977f-137">Krok 4: Konfigurace služby a klienta</span><span class="sxs-lookup"><span data-stu-id="c977f-137">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="c977f-138">Chcete-li spustit službu WCF, je nutné deklarovat koncový bod, který zpřístupňuje toto rozhraní služby na konkrétní adrese URL pomocí konkrétní vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="c977f-138">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="c977f-139">Vazba určuje podrobnosti přenosu, kódování a protokolu pro klienty a server, které mají být sdělovány.</span><span class="sxs-lookup"><span data-stu-id="c977f-139">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="c977f-140">Do konfiguračního souboru projektu služby se obvykle přidávají vazby (web.config).</span><span class="sxs-lookup"><span data-stu-id="c977f-140">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="c977f-141">Následující příklad ukazuje položku vazby pro ukázkovou službu:</span><span class="sxs-lookup"><span data-stu-id="c977f-141">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="c977f-142">Dál je potřeba nakonfigurovat klienta tak, aby odpovídal informacím o vazbě zadaným službou.</span><span class="sxs-lookup"><span data-stu-id="c977f-142">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="c977f-143">Uděláte to tak, že do souboru konfigurace aplikace klienta (app.config) přidáte následující.</span><span class="sxs-lookup"><span data-stu-id="c977f-143">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="c977f-144">Krok 5: spuštění služby</span><span class="sxs-lookup"><span data-stu-id="c977f-144">Step 5: Run the service</span></span>  
 <span data-ttu-id="c977f-145">Nakonec ho můžete sami hostovat v konzolové aplikaci přidáním následujících řádků do aplikace služby a spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="c977f-145">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="c977f-146">Další informace o jiných způsobech hostování aplikace služby WCF, [hostování služeb](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="c977f-146">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="c977f-147">Krok 6: volání služby z klienta</span><span class="sxs-lookup"><span data-stu-id="c977f-147">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="c977f-148">Chcete-li volat službu z klienta, je nutné vytvořit továrnu kanálu pro službu a požádat o kanál, který vám umožní přímo volat `GetCustomer` metodu přímo z klienta.</span><span class="sxs-lookup"><span data-stu-id="c977f-148">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="c977f-149">Kanál implementuje rozhraní služby a zpracovává základní logiku požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="c977f-149">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="c977f-150">Návratovou hodnotou z tohoto volání metody je deserializovaná kopie odpovědi služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-150">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="c977f-151">Klient pošle objektu podle hodnoty na server.</span><span class="sxs-lookup"><span data-stu-id="c977f-151">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="c977f-152">V tomto scénáři klient pošle objekt na server podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-152">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="c977f-153">To znamená, že server dostane deserializovanou kopii objektu.</span><span class="sxs-lookup"><span data-stu-id="c977f-153">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="c977f-154">Server může volat metody v této kopii a zaručit, že se nejedná o zpětné volání do klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="c977f-154">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="c977f-155">Jak už bylo zmíněno dříve, běžné výměny dat WCF jsou podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-155">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="c977f-156">To zaručuje, že volající metody na jednom z těchto objektů se spouští pouze místně – nevyvolává kód na klientovi.</span><span class="sxs-lookup"><span data-stu-id="c977f-156">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="c977f-157">Tento scénář představuje následující volání metody COM:</span><span class="sxs-lookup"><span data-stu-id="c977f-157">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="c977f-158">V tomto scénáři se používá stejné rozhraní služby a kontrakt dat, jak je znázorněno v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="c977f-158">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="c977f-159">Kromě toho se klient a služba nakonfigurují stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c977f-159">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="c977f-160">V tomto příkladu je vytvořen kanál pro odeslání objektu a spuštění stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c977f-160">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="c977f-161">V tomto příkladu však vytvoříte klienta, který bude volat službu, a předáte objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-161">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="c977f-162">Metoda služby, kterou klient bude volat v kontraktu služby, je zobrazená tučně:</span><span class="sxs-lookup"><span data-stu-id="c977f-162">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="c977f-163">Přidání kódu do klienta odesílajícího objekt podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="c977f-163">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="c977f-164">Následující kód ukazuje, jak klient vytvoří nový objekt zákazníka podle hodnoty, vytvoří kanál ke komunikaci se `ICustomerManager` službou a odešle do něj objekt zákazníka.</span><span class="sxs-lookup"><span data-stu-id="c977f-164">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="c977f-165">Objekt zákazníka bude serializován a odeslán službě, kde je deserializována službou do nové kopie tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="c977f-165">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="c977f-166">Jakékoli metody, které služba volá s tímto objektem, se spustí jenom místně na serveru.</span><span class="sxs-lookup"><span data-stu-id="c977f-166">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="c977f-167">Je důležité si uvědomit, že tento kód znázorňuje odeslání odvozeného typu ( `PremiumCustomer` ).</span><span class="sxs-lookup"><span data-stu-id="c977f-167">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="c977f-168">Kontrakt služby očekává `Customer` objekt, ale kontrakt dat služby používá <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut [] k označení toho, že `PremiumCustomer` je povolen také.</span><span class="sxs-lookup"><span data-stu-id="c977f-168">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="c977f-169">Služba WCF selže při pokusu o serializaci nebo deserializaci jiného typu prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-169">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="c977f-170">Služba vrátí objekt podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="c977f-170">The service returns an object by reference</span></span>  
 <span data-ttu-id="c977f-171">V tomto scénáři klientská aplikace provede volání vzdálené služby a metoda vrátí objekt, který je předán odkazem ze služby na klienta.</span><span class="sxs-lookup"><span data-stu-id="c977f-171">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="c977f-172">Jak bylo zmíněno dříve, služby WCF vždy vracejí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-172">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="c977f-173">Podobný výsledek však můžete dosáhnout použitím <xref:System.ServiceModel.EndpointAddress10> třídy.</span><span class="sxs-lookup"><span data-stu-id="c977f-173">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="c977f-174"><xref:System.ServiceModel.EndpointAddress10>Je serializovatelný objekt podle hodnoty, který může klient použít k získání relace odkazem objektu na serveru.</span><span class="sxs-lookup"><span data-stu-id="c977f-174">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="c977f-175">Chování objektu podle odkazu ve službě WCF zobrazené v tomto scénáři se liší od modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="c977f-175">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="c977f-176">V modelu DCOM může server vrátit objekt podle odkazu přímo klientovi a klient může volat metody tohoto objektu, které jsou spuštěny na serveru.</span><span class="sxs-lookup"><span data-stu-id="c977f-176">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="c977f-177">Ve službě WCF je však vrácen objekt vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-177">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="c977f-178">Klient musí přijmout objekt podle hodnoty reprezentovaný <xref:System.ServiceModel.EndpointAddress10> a použít ho k vytvoření vlastního relace pomocí objektu s odkazem.</span><span class="sxs-lookup"><span data-stu-id="c977f-178">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="c977f-179">Metoda klienta volá objekt relace spuštěný na serveru. Jinými slovy je tento objekt odkazem na WCF normální službu WCF, která je nakonfigurovaná tak, aby byla relace.</span><span class="sxs-lookup"><span data-stu-id="c977f-179">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="c977f-180">V rámci WCF je relace způsob, jak korelovat více zpráv posílaných mezi dvěma koncovými body.</span><span class="sxs-lookup"><span data-stu-id="c977f-180">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="c977f-181">To znamená, že jakmile klient získá připojení k této službě, bude vytvořena relace mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="c977f-181">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="c977f-182">Klient bude používat jednu jedinečnou instanci objektu na straně serveru pro všechny interakce v rámci této jediné relace.</span><span class="sxs-lookup"><span data-stu-id="c977f-182">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="c977f-183">Relace WCF jsou podobné vzorům pro požadavky na síťový požadavek a odpověď orientovaný na připojení.</span><span class="sxs-lookup"><span data-stu-id="c977f-183">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="c977f-184">Tento scénář je reprezentován následující metodou DCOM.</span><span class="sxs-lookup"><span data-stu-id="c977f-184">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="c977f-185">Krok 1: definování relace rozhraní WCF a implementace služby WCF</span><span class="sxs-lookup"><span data-stu-id="c977f-185">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="c977f-186">Nejdřív definujte rozhraní služby WCF, které obsahuje objekt sessioning.</span><span class="sxs-lookup"><span data-stu-id="c977f-186">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="c977f-187">V tomto kódu je objekt relace označen `ServiceContract` atributem, který ho identifikuje jako regulární rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c977f-187">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="c977f-188"><xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>Vlastnost je navíc nastavená tak, aby označovala, že se jedná o relaci služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-188">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="c977f-189">Následující kód ukazuje implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-189">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="c977f-190">Služba je označena atributem [ServiceBehavior] a jeho vlastnost InstanceContextMode je nastavena na hodnotu InstanceContextMode. PerSessions, aby označovala, že pro každou relaci by měla být vytvořena jedinečná instance tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="c977f-190">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="c977f-191">Krok 2: definování služby WCF Factory pro objekt sessioning</span><span class="sxs-lookup"><span data-stu-id="c977f-191">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="c977f-192">Služba, která vytváří objekt relace, musí být definovaná a implementovaná.</span><span class="sxs-lookup"><span data-stu-id="c977f-192">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="c977f-193">Následující kód ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="c977f-193">The following code shows how to do this.</span></span> <span data-ttu-id="c977f-194">Tento kód vytvoří jinou službu WCF, která vrací <xref:System.ServiceModel.EndpointAddress10> objekt.</span><span class="sxs-lookup"><span data-stu-id="c977f-194">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="c977f-195">Jedná se o serializovatelný tvar koncového bodu, pomocí kterého lze vytvořit objekt s úplnými relacemi.</span><span class="sxs-lookup"><span data-stu-id="c977f-195">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="c977f-196">Níže je tato implementace této služby.</span><span class="sxs-lookup"><span data-stu-id="c977f-196">The following is the implementation of this service.</span></span> <span data-ttu-id="c977f-197">Tato implementace udržuje objekt pro vytváření relací s jedním prvkem.</span><span class="sxs-lookup"><span data-stu-id="c977f-197">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="c977f-198">Když `GetInstanceAddress` je volána, vytvoří kanál a vytvoří <xref:System.ServiceModel.EndpointAddress10> objekt, který odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="c977f-198">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="c977f-199"><xref:System.ServiceModel.EndpointAddress10>je datový typ, který může být vrácen klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c977f-199"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="c977f-200">Krok 3: konfigurace a spuštění služeb WCF</span><span class="sxs-lookup"><span data-stu-id="c977f-200">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="c977f-201">Chcete-li hostovat tyto služby, budete muset provést následující přidání do konfiguračního souboru serveru (web.config).</span><span class="sxs-lookup"><span data-stu-id="c977f-201">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="c977f-202">Přidejte `<client>` část, která popisuje koncový bod objektu Session.</span><span class="sxs-lookup"><span data-stu-id="c977f-202">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="c977f-203">V tomto scénáři server funguje taky jako klient a musí se nakonfigurovat, aby se povolil.</span><span class="sxs-lookup"><span data-stu-id="c977f-203">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="c977f-204">V `<services>` části deklarujete koncové body služby objektu pro vytváření a relaci.</span><span class="sxs-lookup"><span data-stu-id="c977f-204">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="c977f-205">To umožňuje klientovi komunikovat s koncovými body služby, získat <xref:System.ServiceModel.EndpointAddress10> a vytvořit kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="c977f-205">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="c977f-206">Následuje příklad konfiguračního souboru s těmito nastaveními:</span><span class="sxs-lookup"><span data-stu-id="c977f-206">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="c977f-207">Přidejte následující řádky do konzolové aplikace, pro samoobslužnou hostování služby a aplikaci spusťte.</span><span class="sxs-lookup"><span data-stu-id="c977f-207">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="c977f-208">Krok 4: Konfigurace klienta a volání služby</span><span class="sxs-lookup"><span data-stu-id="c977f-208">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="c977f-209">Nakonfigurujte klienta tak, aby komunikoval se službami WCF, a to tak, že v konfiguračním souboru aplikace projektu (app.config) provedete následující položky.</span><span class="sxs-lookup"><span data-stu-id="c977f-209">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="c977f-210">Chcete-li zavolat službu, přidejte do klienta kód, abyste mohli provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="c977f-210">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="c977f-211">Vytvořte kanál ke `ISessionBoundFactory` službě.</span><span class="sxs-lookup"><span data-stu-id="c977f-211">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="c977f-212">Použití kanálu k vyvolání služby a `ISessionBoundFactory` získání <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="c977f-212">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="c977f-213">Použijte <xref:System.ServiceModel.EndpointAddress10> k vytvoření kanálu pro získání objektu relace.</span><span class="sxs-lookup"><span data-stu-id="c977f-213">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="c977f-214">Zavolejte `SetCurrentValue` metody a `GetCurrentValue` , abyste ukázali, že zůstane stejná instance objektu použita v rámci více volání.</span><span class="sxs-lookup"><span data-stu-id="c977f-214">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c977f-215">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c977f-215">See also</span></span>

- [<span data-ttu-id="c977f-216">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="c977f-216">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="c977f-217">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="c977f-217">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="c977f-218">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="c977f-218">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="c977f-219">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="c977f-219">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
