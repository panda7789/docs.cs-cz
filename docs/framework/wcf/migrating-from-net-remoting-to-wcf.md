---
title: Migrace z .NET Remoting do WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c6bc16e97a87461be7b2c4877777329a0005a497
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296196"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="781bf-102">Migrace z .NET Remoting do WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="781bf-103">Tento článek popisuje, jak migrovat aplikace, která používá vzdálené komunikace .NET na použití služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="781bf-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="781bf-104">Porovná podobné koncepty mezi tyto produkty a pak popisuje, jak provádět několik běžných scénářů vzdálené komunikace v WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="781bf-105">Vzdálené komunikace .NET je starší verze produktu, který je podporován pouze z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="781bf-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="781bf-106">Není zabezpečení napříč prostředími ve smíšeném vztahu důvěryhodnosti, protože ho nejde Udržovat úrovně důvěryhodnosti samostatných mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="781bf-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="781bf-107">Například byste nikdy neměli zveřejňovat koncový bod vzdálené komunikace .NET na Internetu nebo nedůvěryhodné klienty.</span><span class="sxs-lookup"><span data-stu-id="781bf-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="781bf-108">Doporučujeme, abyste existující vzdálenou komunikaci aplikace migrovat na novější a bezpečnější technologií.</span><span class="sxs-lookup"><span data-stu-id="781bf-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="781bf-109">Pokud návrh aplikace používá pouze protokol HTTP a je RESTful, doporučujeme rozhraní ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="781bf-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="781bf-110">Další informace najdete v tématu rozhraní ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="781bf-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="781bf-111">Pokud aplikace je založená na protokolu SOAP nebo vyžaduje jiným protokolem než Http protokoly, například TCP, doporučujeme vám WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="781bf-112">Porovnání služeb vzdálené komunikace .NET na WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="781bf-113">Tato část se porovná se základními stavebními bloky vzdálené komunikace .NET s jejich ekvivalenty WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="781bf-114">Použijeme tyto stavební bloky později vytvořit některé obvyklé scénáře, klient server ve službě WCF. Následující diagram obsahuje souhrn hlavní podobnosti a rozdíly mezi vzdálené komunikace .NET a WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="781bf-115">Vzdálené komunikace pomocí rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="781bf-115">.NET Remoting</span></span>|<span data-ttu-id="781bf-116">WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="781bf-117">Typ serveru</span><span class="sxs-lookup"><span data-stu-id="781bf-117">Server type</span></span>|<span data-ttu-id="781bf-118">Podtřídy třídy MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="781bf-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="781bf-119">Označit pomocí atributu [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="781bf-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="781bf-120">Operace služby</span><span class="sxs-lookup"><span data-stu-id="781bf-120">Service operations</span></span>|<span data-ttu-id="781bf-121">Veřejné metody pro typ serveru</span><span class="sxs-lookup"><span data-stu-id="781bf-121">Public methods on server type</span></span>|<span data-ttu-id="781bf-122">Označit pomocí atributu [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="781bf-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="781bf-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="781bf-123">Serialization</span></span>|<span data-ttu-id="781bf-124">ISerializable nebo [Serializable]</span><span class="sxs-lookup"><span data-stu-id="781bf-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="781bf-125">DataContractSerializer nebo XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="781bf-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="781bf-126">Objekty předané</span><span class="sxs-lookup"><span data-stu-id="781bf-126">Objects passed</span></span>|<span data-ttu-id="781bf-127">Podle hodnoty nebo podle odkazu</span><span class="sxs-lookup"><span data-stu-id="781bf-127">By-value or by-reference</span></span>|<span data-ttu-id="781bf-128">Podle hodnoty pouze</span><span class="sxs-lookup"><span data-stu-id="781bf-128">By-value only</span></span>|  
|<span data-ttu-id="781bf-129">Chyby a výjimky</span><span class="sxs-lookup"><span data-stu-id="781bf-129">Errors/exceptions</span></span>|<span data-ttu-id="781bf-130">Jakoukoli serializovatelný výjimku</span><span class="sxs-lookup"><span data-stu-id="781bf-130">Any serializable exception</span></span>|<span data-ttu-id="781bf-131">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="781bf-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="781bf-132">Objekty proxy serveru klienta</span><span class="sxs-lookup"><span data-stu-id="781bf-132">Client proxy objects</span></span>|<span data-ttu-id="781bf-133">Silného typu transparentních proxy se automaticky vytvořen z kolekci MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="781bf-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="781bf-134">Silného typu proxy servery jsou generovány, vyžádaná použití třídy ChannelFactory\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="781bf-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="781bf-135">Požadované platformy</span><span class="sxs-lookup"><span data-stu-id="781bf-135">Platform required</span></span>|<span data-ttu-id="781bf-136">Klient i server musí používat Microsoft OS a .NET</span><span class="sxs-lookup"><span data-stu-id="781bf-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="781bf-137">Různé platformy</span><span class="sxs-lookup"><span data-stu-id="781bf-137">Cross-platform</span></span>|  
|<span data-ttu-id="781bf-138">Formát zprávy</span><span class="sxs-lookup"><span data-stu-id="781bf-138">Message format</span></span>|<span data-ttu-id="781bf-139">Soukromé</span><span class="sxs-lookup"><span data-stu-id="781bf-139">Private</span></span>|<span data-ttu-id="781bf-140">Oborové standardy (SOAP, WS-\*, atd.)</span><span class="sxs-lookup"><span data-stu-id="781bf-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="781bf-141">Porovnání implementace serveru</span><span class="sxs-lookup"><span data-stu-id="781bf-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="781bf-142">Vytvoření serveru ve vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="781bf-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="781bf-143">Vzdálené komunikace .NET serveru typy musí odvodit z třídy MarshalByRefObject a definovat metody, které klient volat, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="781bf-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="781bf-144">Veřejné metody tohoto typu serveru budou dostupné klientům veřejný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="781bf-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="781bf-145">Není bez jakéhokoli oddělení veřejného rozhraní serveru a jeho implementaci – jeden typ zpracovává obojí.</span><span class="sxs-lookup"><span data-stu-id="781bf-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="781bf-146">Po definování typu serveru to můžete provést k dispozici pro klienty, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="781bf-147">Existuje mnoho způsobů, jak zpřístupnit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="781bf-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="781bf-148">Toto je pouze jeden z příkladů.</span><span class="sxs-lookup"><span data-stu-id="781bf-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="781bf-149">Vytvoření serveru ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="781bf-150">Ekvivalentní krok ve službě WCF zahrnuje vytvoření dva typy – public "servisní smlouva" a konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="781bf-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="781bf-151">První je deklarován jako rozhraní označené [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="781bf-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="781bf-152">Metody dostupné pro klienty jsou označené [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="781bf-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="781bf-153">Implementace serveru je definován v samostatných konkrétní třída, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="781bf-154">Po definování těchto typů WCF serveru můžete provést k dispozici pro klienty, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
>  <span data-ttu-id="781bf-155">TCP se používá v obou příkladech Novoroční co.</span><span class="sxs-lookup"><span data-stu-id="781bf-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="781bf-156">Naleznete v následujících názorných postupech scénář dále v tomto tématu příklady použití protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="781bf-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="781bf-157">Existuje mnoho způsobů, jak nakonfigurovat a hostování služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="781bf-158">Toto je pouze jeden z příkladů, známé jako "v místním prostředí".</span><span class="sxs-lookup"><span data-stu-id="781bf-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="781bf-159">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="781bf-159">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="781bf-160">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="781bf-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
-   [<span data-ttu-id="781bf-161">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="781bf-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
-   [<span data-ttu-id="781bf-162">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="781bf-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="781bf-163">Porovnání implementace klienta</span><span class="sxs-lookup"><span data-stu-id="781bf-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="781bf-164">Vytvoření klienta ve vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="781bf-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="781bf-165">Jakmile je objekt serveru vzdálené komunikace .NET byla k dispozici, může být upotřebena klienty, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="781bf-166">Vrácená z Activator.GetObject() RemotingServer instance se označuje jako "transparentní proxy server."</span><span class="sxs-lookup"><span data-stu-id="781bf-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="781bf-167">Implementuje veřejné rozhraní API pro typ RemotingServer na straně klienta, ale všechny metody volání objektu server běží na jiný proces nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="781bf-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="781bf-168">Vytvoření klienta ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="781bf-169">Ekvivalentní krok ve službě WCF spočívá v použití objektu pro vytváření kanálů explicitně vytvořit proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="781bf-170">Podobně jako vzdálené komunikace objekt proxy serveru slouží k vyvolání operací na serveru, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="781bf-171">Tento příklad ukazuje programování na úrovni kanálu, protože je nejvíce podobně jako v příkladu vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="781bf-172">K dispozici je také **přidat odkaz na službu** přístup v sadě Visual Studio, který generuje kód pro zjednodušení programování klienta.</span><span class="sxs-lookup"><span data-stu-id="781bf-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="781bf-173">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="781bf-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="781bf-174">Programování klienta na úrovni kanálu</span><span class="sxs-lookup"><span data-stu-id="781bf-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="781bf-175">Postupy: Přidání, aktualizace nebo odebrání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="781bf-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="781bf-176">Použití serializace</span><span class="sxs-lookup"><span data-stu-id="781bf-176">Serialization Usage</span></span>  
 <span data-ttu-id="781bf-177">Vzdálené komunikace .NET a WCF používat k odesílání objektů mezi klientem a serverem serializace, ale liší se v těchto důležitých směrech –:</span><span class="sxs-lookup"><span data-stu-id="781bf-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="781bf-178">Používají různé serializátory a konvence lze označit, jaký k serializaci.</span><span class="sxs-lookup"><span data-stu-id="781bf-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="781bf-179">Vzdálené komunikace .NET podporuje "podle odkazu" serializace, která umožňuje přístup metody nebo vlastnosti na jednu vrstvu k provádění kódu na jiné úrovni, což je hranice zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="781bf-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="781bf-180">Tato funkce zpřístupňuje ohrožení zabezpečení a je jedním z hlavních důvodů, proč koncové body vzdálené komunikace by měly být vystaveny nikdy k nedůvěryhodné klienty.</span><span class="sxs-lookup"><span data-stu-id="781bf-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="781bf-181">Vzdálená komunikace používá serializace je odhlásit (explicitně vyloučit jaké není určená k serializaci) a WCF serializace je vyjádřit výslovný souhlas (explicitně označit členy k serializaci).</span><span class="sxs-lookup"><span data-stu-id="781bf-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="781bf-182">Serializace v .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="781bf-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="781bf-183">Vzdálené komunikace .NET podporuje dva způsoby, jak k serializaci a deserializaci objektů mezi klientem a serverem:</span><span class="sxs-lookup"><span data-stu-id="781bf-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="781bf-184">*Podle hodnoty* – hodnoty objektu serializují hranicemi důvěryhodnosti úroveň a je vytvořena nová instance tohoto objektu na jiné úrovni.</span><span class="sxs-lookup"><span data-stu-id="781bf-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="781bf-185">Všechna volání do metody nebo vlastnosti této nové instance pouze místně spouštějí a nemají vliv na původní objekt nebo úroveň.</span><span class="sxs-lookup"><span data-stu-id="781bf-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="781bf-186">*Pomocí odkazu* – speciální "odkaz na objekt" serializován hranicemi důvěryhodnosti úroveň.</span><span class="sxs-lookup"><span data-stu-id="781bf-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="781bf-187">Při jedné vrstvy interakci s metodami nebo vlastnostmi tohoto objektu, komunikuje zpět na původní objekt na původní úroveň.</span><span class="sxs-lookup"><span data-stu-id="781bf-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="781bf-188">Objekty podle odkazu můžete tok v obou směrech – serveru ke klientovi nebo klienta na server.</span><span class="sxs-lookup"><span data-stu-id="781bf-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="781bf-189">Typy podle hodnot ve vzdálené komunikace onačené atributem [Serializable] nebo implementujte rozhraní ISerializable, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="781bf-190">Typy podle odkazu odvozen od třídy MarshalByRefObject, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="781bf-191">Je velmi důležité si uvědomit důsledky objekty podle odkazu na vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="781bf-192">Pokud buď úroveň (klienta nebo serveru) odešle pomocí referenční objekt na úrovni, všechna volání metody spuštění zpět na úrovni vlastnící objekt.</span><span class="sxs-lookup"><span data-stu-id="781bf-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="781bf-193">Klienta volání metod na objekt odkazem vrácená serverem bude třeba spustit kód na serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="781bf-194">Na serveru, volání metod na objekt podle odkazu, který klient poskytl podobně, spustí kód zpět na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="781bf-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="781bf-195">Z tohoto důvodu se doporučuje použití vzdálené komunikace .NET pouze v rámci plně důvěryhodného prostředí.</span><span class="sxs-lookup"><span data-stu-id="781bf-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="781bf-196">Vystavení veřejný koncový bod vzdálené komunikace .NET na nedůvěryhodní klienti způsobí, že vzdálený server snadno napadnutelný.</span><span class="sxs-lookup"><span data-stu-id="781bf-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="781bf-197">Serializace ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-197">Serialization in WCF</span></span>  
 <span data-ttu-id="781bf-198">WCF podporuje pouze podle hodnoty serializace.</span><span class="sxs-lookup"><span data-stu-id="781bf-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="781bf-199">Nejběžnější způsob, jak definovat typ vyměňovat mezi klientem a serverem je stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="781bf-200">Atribut [kontraktu dat DataContract] identifikuje tento typ jako jednu, která může serializovat a deserializovat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="781bf-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="781bf-201">Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole k serializaci.</span><span class="sxs-lookup"><span data-stu-id="781bf-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="781bf-202">Když WCF odešle objekt napříč úrovněmi, serializuje pouze hodnoty a vytvoří novou instanci objektu na jiné úrovni.</span><span class="sxs-lookup"><span data-stu-id="781bf-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="781bf-203">Všechny interakce s hodnotami objektu dojít pouze místně – nekomunikují s úrovní, které objekty podle odkazu způsob, jak vzdálené komunikace .NET.</span><span class="sxs-lookup"><span data-stu-id="781bf-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="781bf-204">Další informace najdete v tématu [serializace a deserializace](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="781bf-204">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="781bf-205">Možnosti zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="781bf-205">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="781bf-206">Výjimky ve vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="781bf-206">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="781bf-207">Výjimky vyvolané v serveru vzdálené komunikace se serializovat, může odeslat klientovi a vyvolána místně na straně klienta, stejně jako jakoukoli jinou výjimku.</span><span class="sxs-lookup"><span data-stu-id="781bf-207">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="781bf-208">Dílčí classing typ výjimky a označením [Serializable] je možné vytvořit vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="781bf-208">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="781bf-209">Většina výjimek framework jsou již označen tímto způsobem umožňuje většina vyvolání serverem serializovat a znovu vyvolána na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="781bf-209">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="781bf-210">I když tento návrh je vhodné při vývoji, neúmyslně být odhalena klientovi informace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-210">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="781bf-211">Toto je jeden z mnoha důvodů, které vzdálené komunikace by měla sloužit pouze v plně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="781bf-211">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="781bf-212">Výjimky a chyby ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-212">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="781bf-213">WCF nepovoluje typy libovolného výjimek, který se má vrátit ze serveru klientovi vzhledem k tomu by mohlo vést k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="781bf-213">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="781bf-214">Pokud operace služby dojde k neočekávané výjimce, dojde k obecné výjimce FaultException, která je vyvolána na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="781bf-214">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="781bf-215">Tato výjimka neobsahuje žádné informace, proč nebo kde k problému došlo, a u některých aplikací to stačí.</span><span class="sxs-lookup"><span data-stu-id="781bf-215">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="781bf-216">Aplikace, které potřebují komunikovat bohatší informace o chybě klienta to definováním kontrakt chyby.</span><span class="sxs-lookup"><span data-stu-id="781bf-216">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="781bf-217">K tomuto účelu nejprve vytvořte typ [kontraktu dat DataContract] k přenosu informací o selhání.</span><span class="sxs-lookup"><span data-stu-id="781bf-217">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="781bf-218">Určete kontrakt chyby pro každou operaci služby.</span><span class="sxs-lookup"><span data-stu-id="781bf-218">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="781bf-219">Server sestav vyvoláním FaultException chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="781bf-219">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="781bf-220">A pokaždé, když klient odešle požadavek na server, můžete zachytit chyby jako normální výjimky.</span><span class="sxs-lookup"><span data-stu-id="781bf-220">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="781bf-221">Další informace o selhání kontrakty, naleznete v tématu <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="781bf-221">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="781bf-222">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="781bf-222">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="781bf-223">Zabezpečení vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="781bf-223">Security in .NET Remoting</span></span>  
 <span data-ttu-id="781bf-224">Některé kanálů řízení vzdálené komunikace .NET podporují funkce zabezpečení, jako je například ověřování a šifrování ve vrstvě kanálu (IPC a TCP).</span><span class="sxs-lookup"><span data-stu-id="781bf-224">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="781bf-225">Kanál protokolu HTTP spoléhá v Internetové informační služby (IIS) pro ověřování a šifrování.</span><span class="sxs-lookup"><span data-stu-id="781bf-225">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="781bf-226">Bez ohledu na tato podpora by měl vezměte v úvahu vzdálené komunikace .NET nezabezpečené komunikační protokol a použít pouze v rámci plně důvěryhodného prostředí.</span><span class="sxs-lookup"><span data-stu-id="781bf-226">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="781bf-227">Nikdy vystavit veřejný koncový bod vzdálené komunikace na Internetu nebo nedůvěryhodné klienty.</span><span class="sxs-lookup"><span data-stu-id="781bf-227">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="781bf-228">Zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-228">Security in WCF</span></span>  
 <span data-ttu-id="781bf-229">WCF byla navržena s na bezpečnost, v části řešení typy v .NET Remoting zjištěná ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="781bf-229">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="781bf-230">WCF nabízí zabezpečení na úrovni přenosu i zprávu a nabízí celou řadu možností pro ověřování, autorizace, šifrování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="781bf-230">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="781bf-231">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="781bf-231">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="781bf-232">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="781bf-232">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="781bf-233">Doprovodné materiály zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-233">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="781bf-234">Migrace na WCF</span><span class="sxs-lookup"><span data-stu-id="781bf-234">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="781bf-235">Proč migrovat Remoting do WCF?</span><span class="sxs-lookup"><span data-stu-id="781bf-235">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="781bf-236">**Vzdálené komunikace .NET je starší verze produktu.**</span><span class="sxs-lookup"><span data-stu-id="781bf-236">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="781bf-237">Jak je popsáno v [vzdálené komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), se považuje za starší verzi produktu a nedoporučuje se používat pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="781bf-237">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="781bf-238">WCF a ASP.NET Web API se doporučuje pro nová a existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-238">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="781bf-239">**WCF využívá multiplatformní standardy.**</span><span class="sxs-lookup"><span data-stu-id="781bf-239">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="781bf-240">WCF byla navržena s vzájemná funkční spolupráce napříč platformami v úvahu a podporuje mnoho oborových standardů (SOAP, WS-Security, WS-Trust, atd.).</span><span class="sxs-lookup"><span data-stu-id="781bf-240">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="781bf-241">Služby WCF můžete spolupráci s klienty běžící na jiných operačních systémech než Windows.</span><span class="sxs-lookup"><span data-stu-id="781bf-241">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="781bf-242">Vzdálená komunikace je navržená především pro prostředí, kde server i klient aplikace běží, pomocí rozhraní .NET framework v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="781bf-242">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="781bf-243">**WCF má integrované zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="781bf-243">**WCF has built-in security.**</span></span> <span data-ttu-id="781bf-244">WCF byla navržena s ohledem na bezpečnost a nabízí celou řadu možností pro ověřování, zabezpečení na úrovni přenosu, zabezpečení na úrovni zpráv atd. Vzdálené komunikace byl navržen k tomu, aby pro aplikace pro spolupráci, ale nebyl navržen, aby bylo zabezpečené v nedůvěryhodné prostředí.</span><span class="sxs-lookup"><span data-stu-id="781bf-244">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="781bf-245">WCF byla navržena pro práci v obou důvěryhodné a nedůvěryhodné prostředích.</span><span class="sxs-lookup"><span data-stu-id="781bf-245">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="781bf-246">Doporučení pro migraci</span><span class="sxs-lookup"><span data-stu-id="781bf-246">Migration Recommendations</span></span>  
 <span data-ttu-id="781bf-247">Tady jsou doporučené kroky migrace z .NET Remoting do WCF:</span><span class="sxs-lookup"><span data-stu-id="781bf-247">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="781bf-248">**Vytvoření kontraktu služby.**</span><span class="sxs-lookup"><span data-stu-id="781bf-248">**Create the service contract.**</span></span> <span data-ttu-id="781bf-249">Definování typů rozhraní služby a označit pomocí atributu [ServiceContract]. Označte všechny metody, klienti budou moct volat [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="781bf-249">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="781bf-250">**Vytvoření kontraktu dat.**</span><span class="sxs-lookup"><span data-stu-id="781bf-250">**Create the data contract.**</span></span> <span data-ttu-id="781bf-251">Definování typů dat, které se vyměňují mezi serverem a klientem a označit pomocí atributu [kontraktu dat DataContract].</span><span class="sxs-lookup"><span data-stu-id="781bf-251">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="781bf-252">Označte všechna pole a vlastnosti, které klienta se bude moct používat s [DataMember].</span><span class="sxs-lookup"><span data-stu-id="781bf-252">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="781bf-253">**Vytvoření kontraktu selhání (nepovinné).**</span><span class="sxs-lookup"><span data-stu-id="781bf-253">**Create the fault contract (optional).**</span></span> <span data-ttu-id="781bf-254">Vytvoření typů, které se vyměňují mezi serverem a klientem, pokud nedojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="781bf-254">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="781bf-255">Označte tyto typy s [kontraktu dat DataContract] a [DataMember], aby se daly serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="781bf-255">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="781bf-256">Pro všechny operace služby, které jste označili [OperationContract] také označte je pomocí [FaultContract] pro označení chyb, které můžou vrátit.</span><span class="sxs-lookup"><span data-stu-id="781bf-256">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="781bf-257">**Konfigurace a hostitelem služby.**</span><span class="sxs-lookup"><span data-stu-id="781bf-257">**Configure and host the service.**</span></span> <span data-ttu-id="781bf-258">Po vytvoření kontraktu služby, dalším krokem je ke konfiguraci vazby pro vystavení služby na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="781bf-258">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="781bf-259">Další informace najdete v tématu [koncové body: Adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="781bf-259">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="781bf-260">Po použití vzdálené komunikace se migroval na WCF, je stále potřeba odebrat závislosti na vzdálené komunikace .NET.</span><span class="sxs-lookup"><span data-stu-id="781bf-260">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="781bf-261">Tím se zajistí, že z aplikace odeberou se všechny chyby zabezpečení vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-261">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="781bf-262">Tyto kroky zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="781bf-262">These steps include the following:</span></span>  
  
-   <span data-ttu-id="781bf-263">**Přestat používat MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="781bf-263">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="781bf-264">Typ třídy MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-264">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="781bf-265">Všechny typy aplikací, které dílčí třídy MarshalByRefObject by měla odebrat nebo změnit.</span><span class="sxs-lookup"><span data-stu-id="781bf-265">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="781bf-266">**Ukončení použití [Serializable] a rozhraní ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="781bf-266">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="781bf-267">Atribut [Serializable] a rozhraní ISerializable byly původně navržen k serializaci typů v rámci důvěryhodného prostředí a jejich používání vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-267">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="781bf-268">Serializace WCF spoléhá na typy, které jsou označené [kontraktu dat DataContract] a [DataMember].</span><span class="sxs-lookup"><span data-stu-id="781bf-268">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="781bf-269">Datové typy používané aplikací by měl být upraven použití [kontraktu dat DataContract] a nepoužívat ISerializable nebo [Serializable].</span><span class="sxs-lookup"><span data-stu-id="781bf-269">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="781bf-270">Scénáře migrace</span><span class="sxs-lookup"><span data-stu-id="781bf-270">Migration Scenarios</span></span>  
 <span data-ttu-id="781bf-271">Nyní Pojďme zjistit, jak provést následující běžné scénáře vzdálené komunikace v WCF:</span><span class="sxs-lookup"><span data-stu-id="781bf-271">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="781bf-272">Server vrátí klientovi objektu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="781bf-272">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="781bf-273">Server vrátí klientovi pomocí – odkaz na objekt</span><span class="sxs-lookup"><span data-stu-id="781bf-273">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="781bf-274">Klient odešle na server objektu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="781bf-274">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="781bf-275">Odesílání pomocí – odkaz na objekt z klienta na server není povolena ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-275">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="781bf-276">Při čtení prostřednictvím těchto scénářů, se předpokládá, že naše základní rozhraní pro .NET Remoting vypadat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="781bf-276">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="781bf-277">Implementace .NET Remoting důležité zde není vzhledem k tomu, že chceme, aby si ukážeme, jak pouze pomocí WCF implementovat ekvivalentní funkce.</span><span class="sxs-lookup"><span data-stu-id="781bf-277">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="781bf-278">Scénář 1: Služba vrátí objekt podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="781bf-278">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="781bf-279">Tento scénář předvádí server objektu podle hodnoty vrácením klientovi.</span><span class="sxs-lookup"><span data-stu-id="781bf-279">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="781bf-280">WCF vždy vrátí objekty ze serveru podle hodnoty, takže takto jednoduše popisují, jak vytvářet běžné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-280">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="781bf-281">Začněte tím, že definování veřejného rozhraní pro službu WCF a označte ji pomocí atributu [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="781bf-281">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="781bf-282">K identifikaci metody na straně serveru, který bude volat naše klientské používáme [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="781bf-282">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="781bf-283">Dalším krokem je vytvoření kontraktu dat pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="781bf-283">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="781bf-284">To provedeme vytvořením tříd (nikoli rozhraní) označená pomocí atributu [kontraktu dat DataContract].</span><span class="sxs-lookup"><span data-stu-id="781bf-284">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="781bf-285">Jednotlivé vlastnosti nebo pole, která chceme, aby viditelné pro klienta a serveru jsou označené [DataMember].</span><span class="sxs-lookup"><span data-stu-id="781bf-285">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="781bf-286">Pokud se mají povolit odvozené typy, musíme použít atribut [Třída KnownType] jejich identifikaci.</span><span class="sxs-lookup"><span data-stu-id="781bf-286">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="781bf-287">Pouze typy WCF umožní serializován nebo deserializován pro tuto službu jsou v rozhraní služby a tyto "známé typy".</span><span class="sxs-lookup"><span data-stu-id="781bf-287">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="781bf-288">Pokus o výměně jakýkoli jiný typ není v tomto seznamu budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="781bf-288">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="781bf-289">Dále poskytujeme implementace rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="781bf-289">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="781bf-290">Ke spuštění služby WCF, musíme deklarovat koncový bod, který zpřístupňuje rozhraní služby na konkrétní adrese URL použití konkrétní vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-290">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="781bf-291">To se obvykle provádí přidáním následující části souboru web.config a server project.</span><span class="sxs-lookup"><span data-stu-id="781bf-291">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="781bf-292">Služby WCF může být spuštěn s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="781bf-292">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="781bf-293">Při spuštění tohoto hostitele ServiceHost pomocí souboru web.config zřizuje správné kontrakt, vazbu a koncový bod.</span><span class="sxs-lookup"><span data-stu-id="781bf-293">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="781bf-294">Další informace o konfiguračních souborech najdete v tématu [konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="781bf-294">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="781bf-295">Tento styl spouštění na serveru se označuje jako s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="781bf-295">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="781bf-296">Další informace o další možnosti hostování služby WCF, naleznete v tématu [hostování služeb](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="781bf-296">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="781bf-297">Klientský projekt app.config musí deklarovat odpovídající informace o vazbě pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="781bf-297">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="781bf-298">Nejjednodušší způsob, jak to provést v sadě Visual Studio je určený **přidat odkaz na službu**, která bude automaticky aktualizovat soubor app.config.</span><span class="sxs-lookup"><span data-stu-id="781bf-298">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="781bf-299">Můžete také tyto stejné změny je možné přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="781bf-299">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="781bf-300">Další informace o používání **přidat odkaz na službu**, naleznete v tématu [jak: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="781bf-300">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="781bf-301">Nyní jsme volat službu WCF z klienta.</span><span class="sxs-lookup"><span data-stu-id="781bf-301">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="781bf-302">Můžeme to udělat tak vytvoření objektu pro vytváření kanálů pro tuto službu požadujícího kanál a přímo volat metodu, kterou chceme, aby na tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="781bf-302">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="781bf-303">Můžeme to udělat, protože kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku pro nás.</span><span class="sxs-lookup"><span data-stu-id="781bf-303">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="781bf-304">Návratová hodnota z volání této metody je deserializovat kopie odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-304">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="781bf-305">Objektů vrácených službou WCF ze serveru do klienta jsou vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="781bf-305">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="781bf-306">Jsou objekty deserializovat kopie dat odeslaných serverem.</span><span class="sxs-lookup"><span data-stu-id="781bf-306">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="781bf-307">Klient může volat metody na tyto místní kopie bez jakékoli nebezpečí vyvolání kódu serveru pomocí zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="781bf-307">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="781bf-308">Scénář 2: Server vrací objekt odkazem.</span><span class="sxs-lookup"><span data-stu-id="781bf-308">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="781bf-309">Tento scénář předvádí serveru, který poskytuje objekt pro klienta podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="781bf-309">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="781bf-310">Ve vzdálené komunikace .NET, to je automaticky zpracována pro libovolného typu odvozeného od třídy MarshalByRefObject, což je serializován podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="781bf-310">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="781bf-311">Příkladem tohoto scénáře je povolení více klientům mají nezávislé objekty s relacemi na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-311">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="781bf-312">Jak už jsme zmínili, objektů vrácených službou WCF neustále podle hodnoty, takže není žádný přímý ekvivalent objektu podle odkazu, ale je možné dosáhnout něco podobného pomocí sémantiky odkazem <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="781bf-312">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="781bf-313">Toto je objekt serializovatelný podle hodnoty, který je možné k získání objektu s relacemi odkazem na serveru klientem.</span><span class="sxs-lookup"><span data-stu-id="781bf-313">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="781bf-314">To umožňuje scénáře s více klienty s nezávislé objekty s relacemi na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-314">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="781bf-315">Nejdřív potřebujeme definování kontraktu služby WCF, která odpovídá na samotný objekt s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-315">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    >  <span data-ttu-id="781bf-316">Všimněte si, že objekt s relacemi je označená pomocí [ServiceContract], což normální rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-316">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="781bf-317">Nastavení režim SessionMode vlastnost určuje, že bude služba s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-317">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="781bf-318">Relace ve službě WCF, je způsob, jak korelace více posílané mezi dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="781bf-318">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="781bf-319">To znamená, že Jakmile klient získá připojení pro tuto službu, relace navázat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="781bf-319">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="781bf-320">Klient použije jeden jedinečný instance objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace.</span><span class="sxs-lookup"><span data-stu-id="781bf-320">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="781bf-321">V dalším kroku potřebujeme pro poskytování implementací rozhraní této služby.</span><span class="sxs-lookup"><span data-stu-id="781bf-321">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="781bf-322">Označující s [ServiceBehavior] a nastavením režim InstanceContextMode, můžeme říct WCF, které že chceme pro každou relaci pomocí jedinečných instance tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="781bf-322">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="781bf-323">Nyní potřebujeme způsob, jak získat instanci tohoto objektu s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-323">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="781bf-324">Uděláme to tak, že vytvoříte jiného rozhraní služby WCF, která vrací objekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="781bf-324">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="781bf-325">Toto je serializovatelného tvaru koncového bodu, který může klient použít k vytvoření objektu s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-325">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="781bf-326">A jsme implementaci této služby WCF:</span><span class="sxs-lookup"><span data-stu-id="781bf-326">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="781bf-327">Tato implementace udržuje typu singleton objektu pro vytváření kanálů vytváření relací objektů.</span><span class="sxs-lookup"><span data-stu-id="781bf-327">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="781bf-328">Při volání GetInstanceAddress() vytvoří kanál a vytvoří EndpointAddress10 objekt, který efektivně odkazuje na vzdálenou adresu spojený s tímto kanálem.</span><span class="sxs-lookup"><span data-stu-id="781bf-328">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="781bf-329">EndpointAddress10 je jednoduše datový typ, který může být vrácen do klienta podle hodnota.</span><span class="sxs-lookup"><span data-stu-id="781bf-329">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="781bf-330">Potřebujeme upravit konfigurační soubor serveru tímto způsobem následující dvě věci, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="781bf-330">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="781bf-331">Deklarace \<klienta > část popisující koncový bod pro objekt s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-331">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="781bf-332">To je nezbytné, protože server také funguje jako klient v této situaci.</span><span class="sxs-lookup"><span data-stu-id="781bf-332">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="781bf-333">Deklarujte koncové body pro objekt factory a který neobsahuje relace.</span><span class="sxs-lookup"><span data-stu-id="781bf-333">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="781bf-334">To je potřeba povolit klienta ke komunikaci s koncovými body služby a získat EndpointAddress10 vytvořte kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-334">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="781bf-335">A pak můžeme začít tyto služby:</span><span class="sxs-lookup"><span data-stu-id="781bf-335">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="781bf-336">Nakonfigurujeme deklarováním tyto stejné koncové body v souboru app.config jeho projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="781bf-336">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="781bf-337">Pokud chcete vytvořit a použít tento objekt s relacemi, musí klient proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="781bf-337">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="781bf-338">Vytvořte kanál ke službě ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="781bf-338">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="781bf-339">Tento kanál používaná k volání této služby k získání EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="781bf-339">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="781bf-340">Použijte EndpointAddress10 k vytvoření kanálu pro získání objektu s relacemi.</span><span class="sxs-lookup"><span data-stu-id="781bf-340">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="781bf-341">Pracovat s relacemi objekt prokázat, že zůstane stejné instance napříč více volání.</span><span class="sxs-lookup"><span data-stu-id="781bf-341">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="781bf-342">WCF vždy vrátí objekty podle hodnoty, ale je možné pro podporu ekvivalent pomocí odkazové sémantiky prostřednictvím EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="781bf-342">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="781bf-343">To umožňuje klientům žádosti s relacemi instance služby WCF, po jejímž uplynutí ho s ním mohli pracovat stejně jako jakoukoli jinou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-343">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="781bf-344">Scénář 3: Klient odešle serveru Instance podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="781bf-344">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="781bf-345">Tento scénář předvádí klientů v odesílání instance objektu jiného než primitivního typu serveru podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="781bf-345">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="781bf-346">Protože WCF odesílá pouze objekty podle hodnoty, tento scénář předvádí normálního využití WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-346">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="781bf-347">Používaly stejnou službu WCF z scénář 1.</span><span class="sxs-lookup"><span data-stu-id="781bf-347">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="781bf-348">Klienta můžete použijte k vytvoření nového objektu podle hodnoty (zákazníka), vytvořit kanál ke komunikaci se službou ICustomerService a posílat objektu.</span><span class="sxs-lookup"><span data-stu-id="781bf-348">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="781bf-349">Objekt zákazníka se serializovat a odeslat na server, kde je deserializovat do novou kopii tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="781bf-349">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="781bf-350">Tento kód také ukazuje odesílání odvozeného typu (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="781bf-350">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="781bf-351">Rozhraní služby očekává, že objekt zákazníků, ale zákazníka pomocí atributu [Třída KnownType] označil že premiumcustomer také byla povolena.</span><span class="sxs-lookup"><span data-stu-id="781bf-351">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="781bf-352">WCF se nezdaří jakýkoliv pokus o serializaci nebo deserializaci jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="781bf-352">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="781bf-353">Normální WCF výměny dat jsou podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="781bf-353">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="781bf-354">Zaručí se tak, že volání metod na jednom z těchto datových objektů provádí pouze místně – nebude volat kód na jiné úrovni.</span><span class="sxs-lookup"><span data-stu-id="781bf-354">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="781bf-355">I když je možné dosáhnout něco jako vrácených objektů podle odkazu *z* server, není možné pro klienta k předání objektu podle odkazu *k* serveru.</span><span class="sxs-lookup"><span data-stu-id="781bf-355">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="781bf-356">Tento scénář vyžaduje konverzace vpřed a zpět mezi klientem a serverem lze dosáhnout pomocí duplexní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="781bf-356">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="781bf-357">Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="781bf-357">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="781bf-358">Souhrn</span><span class="sxs-lookup"><span data-stu-id="781bf-358">Summary</span></span>  
 <span data-ttu-id="781bf-359">Vzdálené komunikace .NET je určena pro použití pouze v rámci plně důvěryhodného prostředí rozhraní komunikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-359">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="781bf-360">Je starší verze produktu a pouze kvůli zpětné kompatibilitě podporované.</span><span class="sxs-lookup"><span data-stu-id="781bf-360">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="781bf-361">Není vhodné používat k vytváření nových aplikací.</span><span class="sxs-lookup"><span data-stu-id="781bf-361">It should not be used to build new applications.</span></span> <span data-ttu-id="781bf-362">WCF a naopak, byla navržena s ohledem na bezpečnost a se doporučuje pro nová a existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-362">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="781bf-363">Společnost Microsoft doporučuje tento existující aplikací vzdálené komunikace migrovat místo toho použít WCF a ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="781bf-363">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
