---
title: Migrace z .NET Remoting do WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183967"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="93af2-102">Migrace z .NET Remoting do WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="93af2-103">Tento článek popisuje, jak migrovat aplikaci, která používá vzdálené komunikace .NET k použití Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="93af2-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="93af2-104">Porovnává podobné koncepty mezi těmito produkty a pak popisuje, jak provést několik běžných scénářů vzdálené komunikace v WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="93af2-105">Vzdálené komunikace rozhraní .NET je starší produkt, který je podporován pouze pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="93af2-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="93af2-106">Není zabezpečená v prostředích se smíšenými důvěryhodnostmi, protože nemůže udržovat samostatné úrovně důvěryhodnosti mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="93af2-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="93af2-107">Například byste nikdy neměli vystavit koncový bod vzdálené komunikace .NET do Internetu nebo nedůvěryhodným klientům.</span><span class="sxs-lookup"><span data-stu-id="93af2-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="93af2-108">Doporučujeme, aby stávající aplikace vzdálené komunikace byly migrovány na novější a bezpečnější technologie.</span><span class="sxs-lookup"><span data-stu-id="93af2-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="93af2-109">Pokud návrh aplikace používá pouze protokol HTTP a je restful, doporučujeme ASP.NET webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="93af2-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="93af2-110">Další informace naleznete v tématu ASP.NET web API.</span><span class="sxs-lookup"><span data-stu-id="93af2-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="93af2-111">Pokud je aplikace založena na SOAP nebo vyžaduje protokoly bez http, jako je například TCP, doporučujeme WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="93af2-112">Porovnání vzdálené komunikace rozhraní .NET s wcf</span><span class="sxs-lookup"><span data-stu-id="93af2-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="93af2-113">Tato část porovnává základní stavební bloky .NET Vzdálené komunikace s jejich wcf ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="93af2-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="93af2-114">Tyto stavební bloky použijeme později k vytvoření některých běžných scénářů klient-server v WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-114">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="93af2-115">Následující graf shrnuje hlavní podobnosti a rozdíly mezi .NET Vzdálené komunikace a WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-115">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="93af2-116">Vzdálené komunikace pomocí rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="93af2-116">.NET Remoting</span></span>|<span data-ttu-id="93af2-117">WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-117">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="93af2-118">Typ serveru</span><span class="sxs-lookup"><span data-stu-id="93af2-118">Server type</span></span>|<span data-ttu-id="93af2-119">Třída MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="93af2-119">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="93af2-120">Označit atributem [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="93af2-120">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="93af2-121">Servisní operace</span><span class="sxs-lookup"><span data-stu-id="93af2-121">Service operations</span></span>|<span data-ttu-id="93af2-122">Veřejné metody na typu serveru</span><span class="sxs-lookup"><span data-stu-id="93af2-122">Public methods on server type</span></span>|<span data-ttu-id="93af2-123">Označit atributem [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="93af2-123">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="93af2-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="93af2-124">Serialization</span></span>|<span data-ttu-id="93af2-125">ISerializable nebo [Serializovatelné]</span><span class="sxs-lookup"><span data-stu-id="93af2-125">ISerializable or [Serializable]</span></span>|<span data-ttu-id="93af2-126">Serializátor datakontraktu nebo xmlserializátor</span><span class="sxs-lookup"><span data-stu-id="93af2-126">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="93af2-127">Předané objekty</span><span class="sxs-lookup"><span data-stu-id="93af2-127">Objects passed</span></span>|<span data-ttu-id="93af2-128">Podle hodnoty nebo odkaz</span><span class="sxs-lookup"><span data-stu-id="93af2-128">By-value or by-reference</span></span>|<span data-ttu-id="93af2-129">Pouze podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="93af2-129">By-value only</span></span>|  
|<span data-ttu-id="93af2-130">Chyby/výjimky</span><span class="sxs-lookup"><span data-stu-id="93af2-130">Errors/exceptions</span></span>|<span data-ttu-id="93af2-131">Jakákoli serializovatelná výjimka</span><span class="sxs-lookup"><span data-stu-id="93af2-131">Any serializable exception</span></span>|<span data-ttu-id="93af2-132">ChybaContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="93af2-132">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="93af2-133">Objekty proxy klienta</span><span class="sxs-lookup"><span data-stu-id="93af2-133">Client proxy objects</span></span>|<span data-ttu-id="93af2-134">Silně zadané průhledné proxy servery jsou vytvořeny automaticky z MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="93af2-134">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="93af2-135">Servery proxy silného typu jsou generovány na\<vyžádání pomocí ChannelFactory TChannel></span><span class="sxs-lookup"><span data-stu-id="93af2-135">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="93af2-136">Požadovaná platforma</span><span class="sxs-lookup"><span data-stu-id="93af2-136">Platform required</span></span>|<span data-ttu-id="93af2-137">Klient i server musí používat operační systém Microsoft OS a rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="93af2-137">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="93af2-138">Různé platformy</span><span class="sxs-lookup"><span data-stu-id="93af2-138">Cross-platform</span></span>|  
|<span data-ttu-id="93af2-139">Formát zprávy</span><span class="sxs-lookup"><span data-stu-id="93af2-139">Message format</span></span>|<span data-ttu-id="93af2-140">Private</span><span class="sxs-lookup"><span data-stu-id="93af2-140">Private</span></span>|<span data-ttu-id="93af2-141">Průmyslové standardy (SOAP, WS-\*atd.)</span><span class="sxs-lookup"><span data-stu-id="93af2-141">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="93af2-142">Porovnání implementace serveru</span><span class="sxs-lookup"><span data-stu-id="93af2-142">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="93af2-143">Vytvoření serveru ve vzdálené remotingu rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="93af2-143">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="93af2-144">Typy serveru vzdálené komunikace sítě .NET musí být odvozeny z MarshalByRefObject a definovat metody, které může klient volat, například následující:</span><span class="sxs-lookup"><span data-stu-id="93af2-144">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="93af2-145">Veřejné metody tohoto typu serveru se stanou veřejnou smlouvou dostupnou klientům.</span><span class="sxs-lookup"><span data-stu-id="93af2-145">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="93af2-146">Neexistuje žádné oddělení mezi veřejným rozhraním serveru a jeho implementací – jeden typ zpracovává oba.</span><span class="sxs-lookup"><span data-stu-id="93af2-146">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="93af2-147">Jakmile je definován typ serveru, může být k dispozici klientům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-147">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="93af2-148">Existuje mnoho způsobů, jak zpřístupnit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="93af2-148">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="93af2-149">To je jen jeden příklad.</span><span class="sxs-lookup"><span data-stu-id="93af2-149">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="93af2-150">Vytvoření serveru v wcf</span><span class="sxs-lookup"><span data-stu-id="93af2-150">Creating a Server in WCF</span></span>  
 <span data-ttu-id="93af2-151">Ekvivalentní krok v WCF zahrnuje vytvoření dvou typů – veřejné "smlouvy o poskytování služeb" a konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="93af2-151">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="93af2-152">První je deklarována jako rozhraní označené [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="93af2-152">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="93af2-153">Metody, které jsou klientům k dispozici, jsou označeny [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="93af2-153">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="93af2-154">Implementace serveru je definována v samostatné konkrétní třídy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-154">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="93af2-155">Jakmile jsou tyto typy definovány, wcf server může být k dispozici klientům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-155">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
> <span data-ttu-id="93af2-156">TCP se používá v obou příkladech, aby byly co nejpodobnější.</span><span class="sxs-lookup"><span data-stu-id="93af2-156">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="93af2-157">Naleznete scénář návody dále v tomto tématu příklady pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="93af2-157">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="93af2-158">Existuje mnoho způsobů konfigurace a hostování služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-158">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="93af2-159">Toto je jen jeden příklad, známý jako "self-hosted".</span><span class="sxs-lookup"><span data-stu-id="93af2-159">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="93af2-160">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="93af2-160">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="93af2-161">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="93af2-161">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="93af2-162">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="93af2-162">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="93af2-163">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="93af2-163">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="93af2-164">Porovnání implementace klienta</span><span class="sxs-lookup"><span data-stu-id="93af2-164">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="93af2-165">Vytvoření klienta ve vzdálené remotingu rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="93af2-165">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="93af2-166">Jakmile je objekt serveru vzdálené komunikace .NET zpřístupněn, mohou jej spotřebovávat klienti, například v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-166">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="93af2-167">Instance RemotingServer vrácená z Activator.GetObject() se označuje jako "transparentní proxy server".</span><span class="sxs-lookup"><span data-stu-id="93af2-167">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="93af2-168">Implementuje veřejné rozhraní API pro typ RemotingServer na straně klienta, ale všechny metody volají objekt serveru spuštěný v jiném procesu nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="93af2-168">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="93af2-169">Vytvoření klienta v WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-169">Creating a Client in WCF</span></span>  
 <span data-ttu-id="93af2-170">Ekvivalentní krok v WCF zahrnuje použití kanálu factory k vytvoření proxy explicitně.</span><span class="sxs-lookup"><span data-stu-id="93af2-170">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="93af2-171">Stejně jako vzdálené komunikace, proxy objekt lze vyvolat operace na serveru, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-171">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="93af2-172">Tento příklad ukazuje programování na úrovni kanálu, protože je nejvíce podobný příkladu vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="93af2-172">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="93af2-173">K dispozici je také přístup **Přidat odkaz na službu** v sadě Visual Studio, který generuje kód pro zjednodušení programování klienta.</span><span class="sxs-lookup"><span data-stu-id="93af2-173">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="93af2-174">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="93af2-174">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="93af2-175">Programování na úrovni kanálu klienta</span><span class="sxs-lookup"><span data-stu-id="93af2-175">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="93af2-176">Postup: Přidání, aktualizace nebo odebrání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="93af2-176">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="93af2-177">Použití serializace</span><span class="sxs-lookup"><span data-stu-id="93af2-177">Serialization Usage</span></span>  
 <span data-ttu-id="93af2-178">Vzdálené komunikace rozhraní .NET i WCF používají serializaci k odesílání objektů mezi klientem a serverem, ale liší se těmito důležitými způsoby:</span><span class="sxs-lookup"><span data-stu-id="93af2-178">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="93af2-179">Používají různé serializátory a konvence k označení, co serializovat.</span><span class="sxs-lookup"><span data-stu-id="93af2-179">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="93af2-180">Vzdálené volání podporuje serializaci "odkazem", která umožňuje přístup metody nebo vlastnosti na jedné vrstvě ke spuštění kódu na druhé vrstvě, která je přes hranice zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="93af2-180">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="93af2-181">Tato funkce zveřejňuje chyby zabezpečení a je jedním z hlavních důvodů, proč vzdálené komunikace koncové body by nikdy být vystaveny nedůvěryhodným klientům.</span><span class="sxs-lookup"><span data-stu-id="93af2-181">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="93af2-182">Serializace používá vzdálené volání je opt-out (explicitně vyloučit, co není serializovat) a WCF serializace je opt-in (explicitně označit členy serializovat).</span><span class="sxs-lookup"><span data-stu-id="93af2-182">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="93af2-183">Serializace ve vzdálené remotingu .NET</span><span class="sxs-lookup"><span data-stu-id="93af2-183">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="93af2-184">Vzdálené komunikace rozhraní .NET podporují dva způsoby serializace a deserializace objektů mezi klientem a serverem:</span><span class="sxs-lookup"><span data-stu-id="93af2-184">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="93af2-185">*Podle hodnoty* – hodnoty objektu jsou serializovány přes hranice vrstvy a nová instance tohoto objektu je vytvořena na druhé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="93af2-185">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="93af2-186">Všechna volání metod nebo vlastností této nové instance spustit pouze místně a nemají vliv na původní objekt nebo vrstvu.</span><span class="sxs-lookup"><span data-stu-id="93af2-186">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="93af2-187">*Odkaz* – speciální "odkaz na objekt" je serializován přes hranice vrstvy.</span><span class="sxs-lookup"><span data-stu-id="93af2-187">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="93af2-188">Když jedna vrstva interaguje s metodami nebo vlastnostmi tohoto objektu, komunikuje zpět k původnímu objektu na původní úrovni.</span><span class="sxs-lookup"><span data-stu-id="93af2-188">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="93af2-189">Odkaz na objekty mohou tok v obou směrech – server ke klientovi nebo klientka na server.</span><span class="sxs-lookup"><span data-stu-id="93af2-189">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="93af2-190">Typy podle hodnot ve vzdálené remotingu jsou označeny atributem [Serializable] nebo implementují ISerializable, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-190">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="93af2-191">Typy odkazů odvozené z Třídy MarshalByRefObject, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-191">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="93af2-192">Je nesmírně důležité pochopit důsledky remoting je by-referenční objekty.</span><span class="sxs-lookup"><span data-stu-id="93af2-192">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="93af2-193">Pokud buď vrstva (klient nebo server) odešle objekt podle odkazu na druhou vrstvu, všechna volání metody spustit zpět na vrstvě vlastnící objekt.</span><span class="sxs-lookup"><span data-stu-id="93af2-193">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="93af2-194">Například metody volání klienta na objekt u odkazu vrácené serverem spustí kód na serveru.</span><span class="sxs-lookup"><span data-stu-id="93af2-194">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="93af2-195">Podobně server volající metody na odkaz na objekt poskytnutý klientem spustí kód zpět na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="93af2-195">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="93af2-196">Z tohoto důvodu se doporučuje použití vzdálené komunikace .NET pouze v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="93af2-196">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="93af2-197">Vystavení veřejného koncového bodu vzdálené komunikace .NET nedůvěryhodným klientům způsobí, že server vzdálené komunikace bude zranitelný vůči útoku.</span><span class="sxs-lookup"><span data-stu-id="93af2-197">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="93af2-198">Serializace v WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-198">Serialization in WCF</span></span>  
 <span data-ttu-id="93af2-199">WCF podporuje pouze serializace podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-199">WCF supports only by-value serialization.</span></span> <span data-ttu-id="93af2-200">Nejběžnější způsob, jak definovat typ pro výměnu mezi klientem a serverem je jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-200">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="93af2-201">Atribut [DataContract] identifikuje tento typ jako typ, který lze serializovat a rekonstruovat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="93af2-201">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="93af2-202">Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole serializovat.</span><span class="sxs-lookup"><span data-stu-id="93af2-202">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="93af2-203">Když WCF odešle objekt napříč vrstvami, serializuje pouze hodnoty a vytvoří novou instanci objektu na druhé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="93af2-203">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="93af2-204">Všechny interakce s hodnotami objektu dojít pouze místně – nekomunikují s druhou vrstvou způsobem .NET Vzdálené komunikace podle referenční objekty.</span><span class="sxs-lookup"><span data-stu-id="93af2-204">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="93af2-205">Další informace naleznete [v tématu Serializace a deserializace](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="93af2-205">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="93af2-206">Možnosti zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="93af2-206">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="93af2-207">Výjimky ve vzdálené remotingu .NET</span><span class="sxs-lookup"><span data-stu-id="93af2-207">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="93af2-208">Výjimky vyvolané serverem vzdálené komunikace jsou serializovány, odeslány klientovi a vyvolány místně na straně klienta jako jakákoli jiná výjimka.</span><span class="sxs-lookup"><span data-stu-id="93af2-208">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="93af2-209">Vlastní výjimky lze vytvořit pomocí sub-classing exception typu a označení s [Serializovat].</span><span class="sxs-lookup"><span data-stu-id="93af2-209">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="93af2-210">Většina výjimky rozhraní jsou již označeny tímto způsobem, což umožňuje většinu být vyvolána serverem, serializované a znovu vyvolána na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="93af2-210">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="93af2-211">Ačkoli tento návrh je vhodný během vývoje, informace na straně serveru mohou být neúmyslně zpřístupněny klientovi.</span><span class="sxs-lookup"><span data-stu-id="93af2-211">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="93af2-212">To je jeden z mnoha důvodů, proč by vzdálené komunikace měla být používána pouze v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="93af2-212">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="93af2-213">Výjimky a chyby v WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-213">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="93af2-214">WCF neumožňuje libovolné typy výjimek, které mají být vráceny ze serveru klientovi, protože by mohlo vést k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="93af2-214">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="93af2-215">Pokud operace služby vyvolá neočekávanou výjimku, způsobí, že na straně klienta bude vyvolána výjimka pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="93af2-215">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="93af2-216">Tato výjimka neobsahuje žádné informace, proč nebo kde došlo k problému a pro některé aplikace je to dostačující.</span><span class="sxs-lookup"><span data-stu-id="93af2-216">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="93af2-217">Aplikace, které je třeba komunikovat bohatší informace o chybě klientovi to definováním chybové smlouvy.</span><span class="sxs-lookup"><span data-stu-id="93af2-217">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="93af2-218">Chcete-li to provést, nejprve vytvořte typ [DataContract] pro přenos informací o chybě.</span><span class="sxs-lookup"><span data-stu-id="93af2-218">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="93af2-219">Zadejte kontrakt poruchy, který se má použít pro každou operaci služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-219">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="93af2-220">Server hlásí chybové stavy vyvoláním výjimky FaultException.</span><span class="sxs-lookup"><span data-stu-id="93af2-220">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 <span data-ttu-id="93af2-221">A vždy, když klient provede požadavek na server, může zachytit chyby jako normální výjimky.</span><span class="sxs-lookup"><span data-stu-id="93af2-221">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="93af2-222">Další informace o kontraktech <xref:System.ServiceModel.FaultException>poruch naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="93af2-222">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="93af2-223">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="93af2-223">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="93af2-224">Zabezpečení ve vzdálené remotingu .NET</span><span class="sxs-lookup"><span data-stu-id="93af2-224">Security in .NET Remoting</span></span>  
 <span data-ttu-id="93af2-225">Některé kanály vzdálené komunikace .NET podporují funkce zabezpečení, jako je ověřování a šifrování ve vrstvě kanálu (IPC a TCP).</span><span class="sxs-lookup"><span data-stu-id="93af2-225">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="93af2-226">Kanál HTTP závisí na internetové informační službě (IIS) pro ověřování i šifrování.</span><span class="sxs-lookup"><span data-stu-id="93af2-226">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="93af2-227">Navzdory této podpoře byste měli zvážit přenos dat .NET vzdálené komunikace jako nezabezpečeného komunikačního protokolu a používat jej pouze v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="93af2-227">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="93af2-228">Nikdy nezveřejňujte veřejný koncový bod vzdálené komunikace pro internet nebo nedůvěryhodné klienty.</span><span class="sxs-lookup"><span data-stu-id="93af2-228">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="93af2-229">Zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-229">Security in WCF</span></span>  
 <span data-ttu-id="93af2-230">WCF byl navržen s ohledem na zabezpečení, částečně k řešení druhů chyb zabezpečení nalezených v .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="93af2-230">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="93af2-231">WCF nabízí zabezpečení na úrovni přenosu i zprávy a nabízí mnoho možností pro ověřování, autorizace, šifrování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="93af2-231">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="93af2-232">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="93af2-232">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="93af2-233">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="93af2-233">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="93af2-234">Pokyny wcf zabezpečení</span><span class="sxs-lookup"><span data-stu-id="93af2-234">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="93af2-235">Migrace na WCF</span><span class="sxs-lookup"><span data-stu-id="93af2-235">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="93af2-236">Proč migrovat z vzdálené komunikace na WCF?</span><span class="sxs-lookup"><span data-stu-id="93af2-236">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="93af2-237">**Vzdálené komunikace .NET je starší produkt.**</span><span class="sxs-lookup"><span data-stu-id="93af2-237">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="93af2-238">Jak je popsáno v [.NET Vzdálené komunikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), je považován za starší produkt a není doporučeno pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="93af2-238">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="93af2-239">WCF nebo ASP.NET webové rozhraní API se doporučuje pro nové i existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="93af2-239">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="93af2-240">**WCF používá standardy pro různé platformy.**</span><span class="sxs-lookup"><span data-stu-id="93af2-240">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="93af2-241">WCF byl navržen s ohledem na interoperabilitu napříč platformami a podporuje mnoho oborových standardů (SOAP, WS-Security, WS-Trust atd.).</span><span class="sxs-lookup"><span data-stu-id="93af2-241">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="93af2-242">Služba WCF může spolupracovat s klienty spuštěnými v jiných operačních systémech než v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="93af2-242">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="93af2-243">Vzdálené volání do vzdálené komunikace bylo navrženo především pro prostředí, kde serverové i klientské aplikace běží pomocí rozhraní .NET Framework v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="93af2-243">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="93af2-244">**WCF má integrované zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="93af2-244">**WCF has built-in security.**</span></span> <span data-ttu-id="93af2-245">WCF byl navržen s ohledem na zabezpečení a nabízí mnoho možností pro ověřování, zabezpečení na úrovni přenosu, zabezpečení na úrovni zpráv atd. Vzdálené komunikace byla navržena tak, aby usnadnila vzájemné působení aplikací, ale nebyla navržena tak, aby byla zabezpečena v nedůvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="93af2-245">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="93af2-246">WCF byl navržen tak, aby fungoval v důvěryhodných i nedůvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="93af2-246">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="93af2-247">Doporučení pro migraci</span><span class="sxs-lookup"><span data-stu-id="93af2-247">Migration Recommendations</span></span>  
 <span data-ttu-id="93af2-248">Následující kroky jsou doporučené pro migraci z vzdálené komunikace rozhraní .NET do wcf:</span><span class="sxs-lookup"><span data-stu-id="93af2-248">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="93af2-249">**Vytvořte servisní smlouvu.**</span><span class="sxs-lookup"><span data-stu-id="93af2-249">**Create the service contract.**</span></span> <span data-ttu-id="93af2-250">Definujte typy rozhraní služby a označte je atributem [ServiceContract]. Označte všechny metody, které budou moci klienti volat pomocí [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="93af2-250">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="93af2-251">**Vytvořte kontrakt dat.**</span><span class="sxs-lookup"><span data-stu-id="93af2-251">**Create the data contract.**</span></span> <span data-ttu-id="93af2-252">Definujte datové typy, které budou vyměňovány mezi serverem a klientem, a označte je atributem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="93af2-252">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="93af2-253">Označte všechna pole a vlastnosti, které bude klient moci používat s uživatelem [DataMember].</span><span class="sxs-lookup"><span data-stu-id="93af2-253">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="93af2-254">**Vytvořte kontrakt poruchy (volitelné).**</span><span class="sxs-lookup"><span data-stu-id="93af2-254">**Create the fault contract (optional).**</span></span> <span data-ttu-id="93af2-255">Vytvořte typy, které budou vyměňovány mezi serverem a klientem, pokud dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="93af2-255">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="93af2-256">Označte tyto typy [DataContract] a [DataMember], aby byly serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="93af2-256">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="93af2-257">Pro všechny servisní operace, které jste označili [OperationContract], také označte je [FaultContract] k označení, které chyby mohou vrátit.</span><span class="sxs-lookup"><span data-stu-id="93af2-257">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="93af2-258">**Konfigurace a hostování služby.**</span><span class="sxs-lookup"><span data-stu-id="93af2-258">**Configure and host the service.**</span></span> <span data-ttu-id="93af2-259">Po vytvoření smlouvy o poskytování služeb je dalším krokem konfigurace vazby pro vystavení služby v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="93af2-259">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="93af2-260">Další informace naleznete [v tématu Koncové body: Adresy, vazby a smlouvy](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="93af2-260">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="93af2-261">Po migraci vzdálené aplikace do WCF, je stále důležité odebrat závislosti na .NET Vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="93af2-261">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="93af2-262">Tím zajistíte, že všechny chyby zabezpečení vzdálené komunikace budou odebrány z aplikace.</span><span class="sxs-lookup"><span data-stu-id="93af2-262">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="93af2-263">Mezi tyto kroky patří následující:</span><span class="sxs-lookup"><span data-stu-id="93af2-263">These steps include the following:</span></span>  
  
- <span data-ttu-id="93af2-264">**Přestaňte používat MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="93af2-264">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="93af2-265">Typ MarshalByRefObject existuje pouze pro vzdálené komunikace a wcf nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="93af2-265">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="93af2-266">Všechny typy aplikací, které podtřídy MarshalByRefObject by měly být odebrány nebo změněny.</span><span class="sxs-lookup"><span data-stu-id="93af2-266">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="93af2-267">**Přestaňte používat [Serializable] a ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="93af2-267">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="93af2-268">Atribut [Serializable] a rozhraní ISerializable byly původně navrženy tak, aby serializovaly typy v důvěryhodných prostředích a jsou používány vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="93af2-268">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="93af2-269">Serializace WCF závisí na typech označených [DataContract] a [DataMember].</span><span class="sxs-lookup"><span data-stu-id="93af2-269">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="93af2-270">Datové typy používané aplikací by měly být upraveny tak, aby používaly [DataContract] a nepoužívaly iSerializable nebo [Serializable].</span><span class="sxs-lookup"><span data-stu-id="93af2-270">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="93af2-271">Scénáře migrace</span><span class="sxs-lookup"><span data-stu-id="93af2-271">Migration Scenarios</span></span>  
 <span data-ttu-id="93af2-272">Nyní se podívejme, jak dosáhnout následujících běžných scénářů vzdálené komunikace v WCF:</span><span class="sxs-lookup"><span data-stu-id="93af2-272">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="93af2-273">Server vrátí klientovi hodnotu podle objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-273">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="93af2-274">Server vrátí objekt odkaz na klienta</span><span class="sxs-lookup"><span data-stu-id="93af2-274">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="93af2-275">Klient odešle na server hodnotu podle hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-275">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93af2-276">Odeslání odkazu na objekt z klienta na server není v wcf povoleno.</span><span class="sxs-lookup"><span data-stu-id="93af2-276">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="93af2-277">Při čtení těchto scénářů předpokládejme, že naše základní rozhraní pro vzdálené čtení .NET vypadají jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="93af2-277">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="93af2-278">Implementace vzdálené komunikace .NET není důležité, protože chceme ilustrovat pouze jak použít WCF implementovat ekvivalentní funkce.</span><span class="sxs-lookup"><span data-stu-id="93af2-278">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="93af2-279">Scénář 1: Služba vrátí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-279">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="93af2-280">Tento scénář ukazuje server vrací objekt klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-280">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="93af2-281">WCF vždy vrací objekty ze serveru podle hodnoty, takže následující kroky jednoduše popisují, jak vytvořit normální službu WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-281">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="93af2-282">Začněte definováním veřejného rozhraní pro službu WCF a označte ji atributem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="93af2-282">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="93af2-283">Používáme [OperationContract] k identifikaci metod na straně serveru, které bude náš klient volat.</span><span class="sxs-lookup"><span data-stu-id="93af2-283">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="93af2-284">Dalším krokem je vytvoření kontraktu dat pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="93af2-284">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="93af2-285">Děláme to vytvořením třídy (ne rozhraní) označené atributem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="93af2-285">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="93af2-286">Jednotlivé vlastnosti nebo pole, které chceme zobrazit jak pro klienta, tak pro server, jsou označeny [DataMember].</span><span class="sxs-lookup"><span data-stu-id="93af2-286">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="93af2-287">Pokud chceme, aby byly odvozené typy povoleny, musíme k jejich identifikaci použít atribut [KnownType].</span><span class="sxs-lookup"><span data-stu-id="93af2-287">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="93af2-288">Pouze typy WCF umožní serializovat nebo rekonstruovat pro tuto službu jsou ty v rozhraní služby a tyto "známé typy".</span><span class="sxs-lookup"><span data-stu-id="93af2-288">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="93af2-289">Pokus o výměnu jiného typu, který není v tomto seznamu, bude odmítnut.</span><span class="sxs-lookup"><span data-stu-id="93af2-289">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="93af2-290">Dále poskytujeme implementaci pro rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-290">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="93af2-291">Chcete-li spustit službu WCF, musíme deklarovat koncový bod, který zveřejňuje toto rozhraní služby na konkrétní adresu URL pomocí konkrétní wcf vazby.</span><span class="sxs-lookup"><span data-stu-id="93af2-291">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="93af2-292">To se obvykle provádí přidáním následujících částí do souboru web.config projektu serveru.</span><span class="sxs-lookup"><span data-stu-id="93af2-292">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="93af2-293">Službu WCF lze spustit pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="93af2-293">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="93af2-294">Při spuštění tohoto ServiceHost, používá soubor web.config k vytvoření správné smlouvy, vazby a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="93af2-294">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="93af2-295">Další informace o konfiguračních souborech naleznete [v tématu Konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="93af2-295">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="93af2-296">Tento styl spuštění serveru je známý jako self-hosting.</span><span class="sxs-lookup"><span data-stu-id="93af2-296">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="93af2-297">Další informace o dalších možnostech hostování služeb WCF najdete v [tématu Hostingové služby](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="93af2-297">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="93af2-298">Soubor app.config klientského projektu musí deklarovat odpovídající informace o vazbě pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-298">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="93af2-299">Nejjednodušší způsob, jak to udělat v sadě Visual Studio, je použít **add service reference**, který automaticky aktualizuje soubor app.config.</span><span class="sxs-lookup"><span data-stu-id="93af2-299">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="93af2-300">Alternativně tyto stejné změny lze přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="93af2-300">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="93af2-301">Další informace o použití **funkce Přidat odkaz na službu**naleznete v [tématu How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="93af2-301">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="93af2-302">Nyní můžeme volat službu WCF z klienta.</span><span class="sxs-lookup"><span data-stu-id="93af2-302">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="93af2-303">Děláme to vytvořením továrny kanálu pro tuto službu, žádostí o kanál a přímým voláním metody, kterou chceme na tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="93af2-303">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="93af2-304">Můžeme to udělat, protože kanál implementuje rozhraní služby a zpracovává základní logiku požadavku/odpovědi pro nás.</span><span class="sxs-lookup"><span data-stu-id="93af2-304">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="93af2-305">Vrácená hodnota z tohoto volání metody je rekonstruovaná kopie odpovědi serveru.</span><span class="sxs-lookup"><span data-stu-id="93af2-305">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="93af2-306">Objekty vrácené WCF ze serveru do klienta jsou vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-306">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="93af2-307">Objekty jsou rekonstruovány kopie dat odeslaných serverem.</span><span class="sxs-lookup"><span data-stu-id="93af2-307">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="93af2-308">Klient může volat metody na těchto místních kopiíbez nebezpečí vyvolání kódu serveru prostřednictvím zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="93af2-308">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="93af2-309">Scénář 2: Server vrátí odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="93af2-309">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="93af2-310">Tento scénář ukazuje server poskytující objekt klientovi odkazem.</span><span class="sxs-lookup"><span data-stu-id="93af2-310">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="93af2-311">Ve vzdálené remotingu rozhraní .NET je tato funkce zpracována automaticky pro libovolný typ odvozený z marshalByRefObject, který je serializován podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="93af2-311">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="93af2-312">Příkladem tohoto scénáře je povolení více klientů mít nezávislé sessionful objekty na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="93af2-312">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="93af2-313">Jak již bylo zmíněno, objekty vrácené službou WCF jsou vždy podle hodnoty, takže neexistuje žádný přímý ekvivalent objektu podle odkazu, <xref:System.ServiceModel.EndpointAddress10> ale je možné dosáhnout něco podobného sémantiku odkaz pomocí objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-313">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="93af2-314">Jedná se o serializovatelný objekt podle hodnoty, který může klient použít k získání objektu relace odkazem na serveru.</span><span class="sxs-lookup"><span data-stu-id="93af2-314">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="93af2-315">To umožňuje scénář mít více klientů s nezávislými sessionful objekty na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="93af2-315">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="93af2-316">Nejprve musíme definovat wcf servisní smlouvy, která odpovídá sessionful objektu sám.</span><span class="sxs-lookup"><span data-stu-id="93af2-316">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    > <span data-ttu-id="93af2-317">Všimněte si, že objekt relace je označen [ServiceContract], což je normální wcf rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-317">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="93af2-318">Nastavení SessionMode vlastnost označuje, že bude relace služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-318">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="93af2-319">V WCF relace je způsob korelace více zpráv odeslaných mezi dvěma koncovými body.</span><span class="sxs-lookup"><span data-stu-id="93af2-319">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="93af2-320">To znamená, že jakmile klient získá připojení k této službě, bude mezi klientem a serverem vytvořena relace.</span><span class="sxs-lookup"><span data-stu-id="93af2-320">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="93af2-321">Klient použije jednu jedinečnou instanci objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace.</span><span class="sxs-lookup"><span data-stu-id="93af2-321">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="93af2-322">Dále musíme zajistit implementaci tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-322">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="93af2-323">Tím, že jej opatříte [ServiceBehavior] a nastavíme InstanceContextMode, řekneme WCF, že chceme použít jedinečnou instanci tohoto typu pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="93af2-323">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="93af2-324">Nyní potřebujeme způsob, jak získat instanci tohoto sessionful objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-324">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="93af2-325">Děláme to vytvořením jiného rozhraní služby WCF, který vrací endpointaddress10 objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-325">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="93af2-326">Toto je serializovatelná forma koncového bodu, který může klient použít k vytvoření objektu relačného.</span><span class="sxs-lookup"><span data-stu-id="93af2-326">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="93af2-327">A implementujeme tuto službu WCF:</span><span class="sxs-lookup"><span data-stu-id="93af2-327">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="93af2-328">Tato implementace udržuje totokanálovou továrnu pro vytváření objektů relací.</span><span class="sxs-lookup"><span data-stu-id="93af2-328">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="93af2-329">Při getInstanceAddress() je volána, vytvoří kanál a vytvoří EndpointAddress10 objekt, který účinně odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="93af2-329">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="93af2-330">EndpointAddress10 je jednoduše datový typ, který lze vrátit klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-330">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="93af2-331">Potřebujeme upravit konfigurační soubor serveru provedením následujících dvou věcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="93af2-331">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="93af2-332">Deklarovat klienta \<> části, která popisuje koncový bod pro sessionful objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-332">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="93af2-333">To je nezbytné, protože server také funguje jako klient v této situaci.</span><span class="sxs-lookup"><span data-stu-id="93af2-333">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="93af2-334">Deklarovat koncové body pro objekt výroby a sessionful.</span><span class="sxs-lookup"><span data-stu-id="93af2-334">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="93af2-335">To je nezbytné, aby klient komunikovat s koncovými body služby získat EndpointAddress10 a vytvořit sessionful kanálu.</span><span class="sxs-lookup"><span data-stu-id="93af2-335">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="93af2-336">A pak můžeme začít tyto služby:</span><span class="sxs-lookup"><span data-stu-id="93af2-336">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="93af2-337">Klienta nakonfigurujeme deklarováním stejných koncových bodů v souboru app.config svého projektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-337">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="93af2-338">Chcete-li vytvořit a použít tento objekt relace, musí klient provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="93af2-338">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="93af2-339">Vytvořte kanál ke službě ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="93af2-339">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="93af2-340">Pomocí tohoto kanálu vyvolat tuto službu získat EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="93af2-340">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="93af2-341">Pomocí endpointaddress10 vytvořit kanál pro získání sessionful objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-341">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="93af2-342">Interakci s sessionful objektu prokázat, že zůstane stejná instance přes více volání.</span><span class="sxs-lookup"><span data-stu-id="93af2-342">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="93af2-343">WCF vždy vrátí objekty podle hodnoty, ale je možné podporovat ekvivalent sémantiku odkaz pomocí EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="93af2-343">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="93af2-344">To umožňuje klientovi požadovat sessionful WCF instance služby, po kterém může komunikovat s ním jako všechny ostatní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="93af2-344">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="93af2-345">Scénář 3: Klient odešle serveru instanci by-Value</span><span class="sxs-lookup"><span data-stu-id="93af2-345">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="93af2-346">Tento scénář ukazuje klienta odesílání neprimitivní objekt instance na server podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-346">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="93af2-347">Vzhledem k tomu, že WCF odesílá pouze objekty podle hodnoty, tento scénář demonstruje normální wcf použití.</span><span class="sxs-lookup"><span data-stu-id="93af2-347">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="93af2-348">Použijte stejnou službu WCF ze scénáře 1.</span><span class="sxs-lookup"><span data-stu-id="93af2-348">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="93af2-349">Pomocí klienta vytvořte nový objekt podle hodnoty (Zákazník), vytvořte kanál pro komunikaci se službou ICustomerService a odešlete do něj objekt.</span><span class="sxs-lookup"><span data-stu-id="93af2-349">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="93af2-350">Objekt zákazníka bude serializován a odeslán na server, kde je deserializován do nové kopie tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="93af2-350">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="93af2-351">Tento kód také ilustruje odeslání odvozeného typu (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="93af2-351">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="93af2-352">Rozhraní služby očekává objekt Customer, ale atribut [KnownType] ve třídě Customer uvedl, že byl povolen také premiumcustomer.</span><span class="sxs-lookup"><span data-stu-id="93af2-352">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="93af2-353">WCF se nezdaří jakýkoli pokus o serializovat nebo rekonstruovat jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-353">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="93af2-354">Normální WCF výměny dat jsou podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93af2-354">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="93af2-355">To zaručuje, že vyvolání metody na jednom z těchto datových objektů provede pouze místně – nebude vyvolat kód na druhé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="93af2-355">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="93af2-356">I když je možné dosáhnout něco jako odkaz na objekty vrácené *ze* serveru, není možné pro klienta předat objekt odkazu *na* server.</span><span class="sxs-lookup"><span data-stu-id="93af2-356">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="93af2-357">Scénář, který vyžaduje konverzaci tam a zpět mezi klientem a serverem lze dosáhnout v WCF pomocí duplexní služby.</span><span class="sxs-lookup"><span data-stu-id="93af2-357">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="93af2-358">Další informace naleznete v tématu [Duplex Services](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="93af2-358">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="93af2-359">Souhrn</span><span class="sxs-lookup"><span data-stu-id="93af2-359">Summary</span></span>  
 <span data-ttu-id="93af2-360">Vzdálené volání .NET je komunikační rámec určený k použití pouze v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="93af2-360">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="93af2-361">Jedná se o starší produkt a je podporován pouze pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="93af2-361">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="93af2-362">Neměl by být používán k vytváření nových aplikací.</span><span class="sxs-lookup"><span data-stu-id="93af2-362">It should not be used to build new applications.</span></span> <span data-ttu-id="93af2-363">Naopak WCF byl navržen s ohledem na zabezpečení a je doporučeno pro nové i stávající aplikace.</span><span class="sxs-lookup"><span data-stu-id="93af2-363">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="93af2-364">Společnost Microsoft doporučuje, aby existující vzdálené komunikace aplikace migrovat použít WCF nebo ASP.NET webové rozhraní API místo.</span><span class="sxs-lookup"><span data-stu-id="93af2-364">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
