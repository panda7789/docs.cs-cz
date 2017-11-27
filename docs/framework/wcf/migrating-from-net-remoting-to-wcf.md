---
title: Migrace z .NET Remoting do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 228a6faca43ed121de59ed35c5a186294b41d147
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="9b6c5-102">Migrace z .NET Remoting do WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="9b6c5-103">Tento článek popisuje, jak k migraci aplikace, která používá .NET Remoting používat Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9b6c5-104">Porovnává podobné koncepty mezi tyto produkty a pak popisuje, jak provést několik běžných scénářů vzdálené komunikace v WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="9b6c5-105">.NET remoting je starší verze produktu, který je podporován pouze z důvodů zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="9b6c5-106">Není zabezpečené přes důvěryhodnosti ve smíšeném prostředí, protože jej nelze udržovat úrovně samostatné vztah důvěryhodnosti mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="9b6c5-107">Například byste nikdy neměli zveřejňovat koncový bod .NET Remoting k Internetu nebo nedůvěryhodné klientům.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="9b6c5-108">Doporučujeme, abyste existující vzdálenou komunikaci aplikace migrovat do technologie novější a bezpečnější.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="9b6c5-109">Pokud aplikace návrhu používá jen protokol HTTP a je dosáhl standardu RESTful, doporučujeme rozhraní ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="9b6c5-110">Další informace najdete v tématu rozhraní ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="9b6c5-111">Pokud aplikace je založena na protokolu SOAP nebo vyžaduje jiných protokolů než Http například TCP, doporučujeme WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="9b6c5-112">Porovnání .NET Remoting do WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="9b6c5-113">Tato část porovná základní stavební bloky .NET Remoting s jejich ekvivalenty u WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="9b6c5-114">Použijeme tyto stavební bloky později vytvořit některé běžné scénáře klient server ve WCF. Následující graf shrnuje hlavní podobnosti a rozdíly mezi .NET Remoting a WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="9b6c5-115">Vzdálené komunikace pomocí rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="9b6c5-115">.NET Remoting</span></span>|<span data-ttu-id="9b6c5-116">WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="9b6c5-117">Typ serveru</span><span class="sxs-lookup"><span data-stu-id="9b6c5-117">Server type</span></span>|<span data-ttu-id="9b6c5-118">Podtřída MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="9b6c5-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="9b6c5-119">Označit atributem [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="9b6c5-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="9b6c5-120">Operace služby</span><span class="sxs-lookup"><span data-stu-id="9b6c5-120">Service operations</span></span>|<span data-ttu-id="9b6c5-121">Veřejné metody na typ serveru</span><span class="sxs-lookup"><span data-stu-id="9b6c5-121">Public methods on server type</span></span>|<span data-ttu-id="9b6c5-122">Označit pomocí atributu [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="9b6c5-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="9b6c5-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="9b6c5-123">Serialization</span></span>|<span data-ttu-id="9b6c5-124">ISerializable nebo [Serializable]</span><span class="sxs-lookup"><span data-stu-id="9b6c5-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="9b6c5-125">DataContractSerializer nebo třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="9b6c5-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="9b6c5-126">Objekty předané</span><span class="sxs-lookup"><span data-stu-id="9b6c5-126">Objects passed</span></span>|<span data-ttu-id="9b6c5-127">Hodnotou nebo odkazem</span><span class="sxs-lookup"><span data-stu-id="9b6c5-127">By-value or by-reference</span></span>|<span data-ttu-id="9b6c5-128">Podle hodnoty jenom</span><span class="sxs-lookup"><span data-stu-id="9b6c5-128">By-value only</span></span>|  
|<span data-ttu-id="9b6c5-129">Chyby nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="9b6c5-129">Errors/exceptions</span></span>|<span data-ttu-id="9b6c5-130">Všechny serializovatelný výjimky</span><span class="sxs-lookup"><span data-stu-id="9b6c5-130">Any serializable exception</span></span>|<span data-ttu-id="9b6c5-131">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="9b6c5-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="9b6c5-132">Objekty proxy serveru klienta</span><span class="sxs-lookup"><span data-stu-id="9b6c5-132">Client proxy objects</span></span>|<span data-ttu-id="9b6c5-133">Silného typu transparentní proxy jsou automaticky vytvořen z MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="9b6c5-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="9b6c5-134">Silného typu proxy se generují pomocí ChannelFactory na vyžádání\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="9b6c5-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="9b6c5-135">Platforma požadované</span><span class="sxs-lookup"><span data-stu-id="9b6c5-135">Platform required</span></span>|<span data-ttu-id="9b6c5-136">Klient i server musí používat Microsoft OS a rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="9b6c5-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="9b6c5-137">Více platforem</span><span class="sxs-lookup"><span data-stu-id="9b6c5-137">Cross-platform</span></span>|  
|<span data-ttu-id="9b6c5-138">Formát zprávy</span><span class="sxs-lookup"><span data-stu-id="9b6c5-138">Message format</span></span>|<span data-ttu-id="9b6c5-139">Soukromé</span><span class="sxs-lookup"><span data-stu-id="9b6c5-139">Private</span></span>|<span data-ttu-id="9b6c5-140">Oborové standardy (SOAP, WS-* atd.)</span><span class="sxs-lookup"><span data-stu-id="9b6c5-140">Industry standards (SOAP, WS-*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="9b6c5-141">Porovnání implementace serveru</span><span class="sxs-lookup"><span data-stu-id="9b6c5-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="9b6c5-142">Vytvoření serveru ve vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="9b6c5-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="9b6c5-143">Typy .NET remoting server musí odvozena od třídy MarshalByRefObject a definovat metody, které klient může volat, podobně jako tento:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="9b6c5-144">Veřejné metody tohoto typu serveru stanou veřejného kontraktu, která je k dispozici pro klienty.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="9b6c5-145">Neexistuje žádné oddělení mezi veřejné rozhraní serveru a jeho implementace – jeden typ zpracuje obě.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="9b6c5-146">Po definování typ serveru, se může být dostupné pro klienty, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="9b6c5-147">Existuje mnoho způsobů, jak zpřístupnit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="9b6c5-148">Toto je pouze jeden z příkladů.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="9b6c5-149">Vytvoření serveru ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="9b6c5-150">Ekvivalentní krok ve WCF zahrnuje vytvoření dva typy – veřejných "kontrakt služby" a konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="9b6c5-151">První je deklarován jako rozhraní označené jako [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="9b6c5-152">[OperationContract] jsou označené metody, které jsou dostupné klientům:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="9b6c5-153">Implementace serveru je definována v samostatné konkrétní třídy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="9b6c5-154">Po definování těchto typů WCF serveru může být dostupné pro klienty, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="9b6c5-155">TCP se používá v obou příkladech jejich udržování v co.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="9b6c5-156">Naleznete návodů scénář dále v tomto tématu příklady pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="9b6c5-157">Existuje mnoho způsobů, jak nakonfigurovat a hostování služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="9b6c5-158">Toto je pouze jeden z příkladů, označuje jako "samoobslužně hostovaná".</span><span class="sxs-lookup"><span data-stu-id="9b6c5-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="9b6c5-159">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-159">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9b6c5-160">Postupy: definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="9b6c5-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
-   [<span data-ttu-id="9b6c5-161">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="9b6c5-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
-   [<span data-ttu-id="9b6c5-162">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="9b6c5-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="9b6c5-163">Porovnání implementace klienta</span><span class="sxs-lookup"><span data-stu-id="9b6c5-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="9b6c5-164">Vytvoření klienta v rozhraní .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="9b6c5-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="9b6c5-165">Jakmile objekt .NET Remoting serveru dojde k dispozici, se mohou být spotřebovávána klientů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="9b6c5-166">Instance RemotingServer vrácená z Activator.GetObject() se označuje jako "transparentní proxy."</span><span class="sxs-lookup"><span data-stu-id="9b6c5-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="9b6c5-167">Implementuje veřejné rozhraní API pro typ RemotingServer na straně klienta, ale všechny metody volat objekt serveru s jiným procesem nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="9b6c5-168">Vytvoření klienta ve WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="9b6c5-169">Ekvivalentní krok ve WCF, která využívá kanálu explicitně vytvořit proxy server.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="9b6c5-170">Jako Vzdálená komunikace objekt proxy serveru slouží k vyvolání operace na serveru, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="9b6c5-171">Tento příklad ukazuje, programování na úrovni kanálu, protože je nejvíce podobně jako v příkladu vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="9b6c5-172">Je také k dispozici **přidat odkaz na službu** přístup v sadě Visual Studio, který generuje kód pro zjednodušení programování klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="9b6c5-173">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9b6c5-174">Programování na úrovni kanálu klienta</span><span class="sxs-lookup"><span data-stu-id="9b6c5-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="9b6c5-175">Postupy: Přidání, aktualizace nebo odebrání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="9b6c5-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="9b6c5-176">Serializace využití</span><span class="sxs-lookup"><span data-stu-id="9b6c5-176">Serialization Usage</span></span>  
 <span data-ttu-id="9b6c5-177">.NET Remoting a WCF používat serializace k odesílání objektů mezi klientem a serverem, ale liší se tyto důležité způsoby:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1.  <span data-ttu-id="9b6c5-178">Používají různé serializátorů a konvence lze označit, jaký k serializaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2.  <span data-ttu-id="9b6c5-179">.NET remoting podporuje "odkazem" serializace, které umožňuje metody nebo vlastnosti přístup na jednu úroveň ke spouštění kódu na další úroveň, která je v rámci hranice zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="9b6c5-180">Tato funkce zpřístupňuje ohrožení zabezpečení a je jedním z hlavních důvodů, proč koncové body vzdálené komunikace by měly být vystaveny nikdy nedůvěryhodné klientům.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3.  <span data-ttu-id="9b6c5-181">Serializace používá vzdálené komunikace je výslovný nesouhlas s (výslovně vyloučili jaké není určená k serializaci) a serializace WCF je výslovný souhlas (explicitně označit které členy k serializaci).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="9b6c5-182">Serializace v .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="9b6c5-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="9b6c5-183">.NET remoting podporuje dva způsoby, jak serializaci a deserializaci objektů mezi klientem a serverem:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="9b6c5-184">*Podle hodnoty* – hodnoty objektu se serializují napříč hranicemi vrstvy a vytvořit novou instanci tohoto objektu, na jiné vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="9b6c5-185">Volání metody nebo vlastnosti této nové instance provést pouze místně a neovlivní původní objekt nebo vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="9b6c5-186">*Odkazem* – speciální "odkaz na objekt" je serializováno napříč hranicemi vrstvy.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="9b6c5-187">Když jedné vrstvy pracuje s metody nebo vlastnosti daného objektu, komunikuje se zpět na původní objekt na původní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="9b6c5-188">Objekty podle odkazu můžete procházet v obou směrech – serveru ke klientovi nebo klienta k serveru.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="9b6c5-189">Typy podle hodnot v vzdálené komunikace jsou označené atributem [Serializable] nebo implementovat ISerializable, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="9b6c5-190">Typy odkazem odvozena od třídy MarshalByRefObject, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="9b6c5-191">Je velmi důležité pochopit důsledky objekty odkazem na vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="9b6c5-192">Pokud buď vrstvy (klienta nebo serveru) odešle objekt odkazem k jiné vrstvě, všechna volání metody spouštění zpět na úroveň, který vlastní objekt.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="9b6c5-193">Klienta voláním metody na objekt odkazem vrácená serverem bude třeba spustit kód na serveru.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="9b6c5-194">Podobně serveru, volání metod na objekt odkazem klient poskytl spustí kód zpět na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="9b6c5-195">Z tohoto důvodu se doporučuje použití .NET Remoting pouze ve plně důvěryhodná prostředích.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="9b6c5-196">Vystavení veřejný koncový bod .NET Remoting do nedůvěryhodní klienti budou vzdálenou komunikaci server bude zranitelný vůči útoku.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="9b6c5-197">Serializace ve WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-197">Serialization in WCF</span></span>  
 <span data-ttu-id="9b6c5-198">WCF podporuje pouze serializace-hodnota.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="9b6c5-199">Nejběžnější způsob, jak definovat typů Exchange mezi klientem a serverem je jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="9b6c5-200">Atribut [kontraktu] Určuje tento typ jako jednu, která může serializovat a deserializovat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="9b6c5-201">Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole určená k serializaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="9b6c5-202">Pokud WCF odešle objekt mezi vrstvami, serializuje jenom hodnoty a vytvoří novou instanci objektu na jiné vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="9b6c5-203">Všechny interakce s hodnotami objektu dojít pouze místně – tito klienti nekomunikují s další vrstvou, které objekty způsob .NET Remoting odkazem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="9b6c5-204">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-204">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9b6c5-205">Serializace a deserializace</span><span class="sxs-lookup"><span data-stu-id="9b6c5-205">Serialization and Deserialization</span></span>](./feature-details/serialization-and-deserialization.md)  
  
-   [<span data-ttu-id="9b6c5-206">Serializace ve službě Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9b6c5-206">Serialization in Windows Communication Foundation</span></span>](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="9b6c5-207">Možnosti zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="9b6c5-207">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="9b6c5-208">Výjimky v .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="9b6c5-208">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="9b6c5-209">Výjimky vyvolané vzdálenou komunikaci serveru jsou serializovat, může odeslat klientovi a vyvolána místně na straně klienta jako všechny ostatní výjimky.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-209">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="9b6c5-210">Dílčí classing typ výjimky a označení [Serializable] možné vytvářet vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-210">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="9b6c5-211">Většina framework výjimky jsou již označené tímto způsobem, povolení většina vyvolání serverem serializovat a znovu vyvolány na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-211">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="9b6c5-212">I když tento návrh je vhodné při vývoji, můžete informace serverové nechtěně zveřejněna do klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-212">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="9b6c5-213">Toto je jedním z mnoha důvodů, vzdálené komunikace by měla být používána pouze ve plně důvěryhodná prostředích.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-213">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="9b6c5-214">Výjimek a chyb ve WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-214">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="9b6c5-215">WCF nepovoluje typy libovolný výjimek má být vrácen ze serveru klientovi protože by mohlo vést k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-215">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="9b6c5-216">Pokud je operace služby neočekávanou výjimku, způsobí obecné účely FaultException vyvolání na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-216">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="9b6c5-217">Tato výjimka neobsahuje žádné informace, proč nebo kde k problému došlo, a pro některé aplikace jde dostatečná.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-217">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="9b6c5-218">Aplikace, které je třeba komunikovat bohatší informace o chybě úkol klienta to tak, že definujete kontraktu selhání.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-218">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="9b6c5-219">Uděláte to tak, nejdřív vytvořte typ [kontraktu] k přenosu informací o selhání.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-219">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="9b6c5-220">Zadejte kontrakt odolnost pro každou operaci služby.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-220">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="9b6c5-221">Server sestav po vyvolání výjimky FaultException chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-221">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="9b6c5-222">A vždy, když klient odešle požadavek na server, můžete ho catch chyb jako normální výjimky.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-222">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 <span data-ttu-id="9b6c5-223">Další informace o selhání kontrakty najdete v tématu <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-223">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="9b6c5-224">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b6c5-224">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="9b6c5-225">Zabezpečení v rozhraní .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="9b6c5-225">Security in .NET Remoting</span></span>  
 <span data-ttu-id="9b6c5-226">Některé .NET Remoting kanály podpory funkce zabezpečení, jako je například ověřování a šifrování ve vrstvě kanálu (IPC a TCP).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-226">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="9b6c5-227">Kanál protokolu HTTP spoléhá na Internetové informační služby (IIS) pro ověřování a šifrování.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-227">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="9b6c5-228">I přes tato podpora měli vzít v úvahu .NET Remoting protokol nezabezpečená komunikace a použít ho pouze ve plně důvěryhodná prostředích.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-228">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="9b6c5-229">Nikdy neměli zveřejňovat veřejný koncový bod Vzdálená komunikace na Internetu nebo nedůvěryhodné klientů.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-229">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="9b6c5-230">Zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-230">Security in WCF</span></span>  
 <span data-ttu-id="9b6c5-231">WCF byla navržena s důrazem na bezpečnost, v části vyřešit druhy ohrožení zabezpečení v rozhraní .NET Remoting nalezen.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-231">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="9b6c5-232">WCF nabízí zabezpečení na úrovni přenosu i zprávu a nabízí mnoho možností pro ověřování, autorizace, šifrování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-232">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="9b6c5-233">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-233">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9b6c5-234">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b6c5-234">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="9b6c5-235">Doprovodné materiály zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-235">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="9b6c5-236">Migrace na službu WCF</span><span class="sxs-lookup"><span data-stu-id="9b6c5-236">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="9b6c5-237">Proč migrace Remoting do WCF?</span><span class="sxs-lookup"><span data-stu-id="9b6c5-237">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="9b6c5-238">**.NET remoting je starší verze produktu.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-238">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="9b6c5-239">Jak je popsáno v [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), se považuje za starší verze produktu a nedoporučuje se používat pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-239">As described in [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="9b6c5-240">WCF nebo rozhraní ASP.NET Web API se doporučují pro nových nebo stávajících aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-240">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="9b6c5-241">**WCF používá standardy napříč platformami.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-241">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="9b6c5-242">WCF byl navržen s interoperabilitu napříč platformami v paměti a podporuje mnoho oborových standardů (SOAP, WS-zabezpečení, WS-Trust, atd.).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-242">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="9b6c5-243">Služby WCF můžete zajistit vzájemnou funkční spolupráci s klienty běžící na operačních systémech než Windows.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-243">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="9b6c5-244">Vzdálená komunikace byla určena především pro prostředí, kde spustit serverových a klientských aplikací pomocí rozhraní .NET framework v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-244">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="9b6c5-245">**WCF je integrované zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-245">**WCF has built-in security.**</span></span> <span data-ttu-id="9b6c5-246">WCF byla navržena s důrazem na bezpečnost a nabízí mnoho možností pro ověřování, zabezpečení na úrovni přenosu, úroveň zabezpečení zpráv atd. Vzdálená komunikace byla navržená tak, aby mohl snadno aplikace pro spolupráci, ale nebyl navržen, aby bylo zabezpečené v nedůvěryhodné prostředích.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-246">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="9b6c5-247">WCF byla navržená tak, aby fungovaly v prostředí důvěryhodné i nedůvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-247">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="9b6c5-248">Migrace doporučení</span><span class="sxs-lookup"><span data-stu-id="9b6c5-248">Migration Recommendations</span></span>  
 <span data-ttu-id="9b6c5-249">Následující části jsou doporučené kroky migrace z .NET Remoting do WCF:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-249">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="9b6c5-250">**Vytvoření kontraktu služby.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-250">**Create the service contract.**</span></span> <span data-ttu-id="9b6c5-251">Definování typů rozhraní vaší služby a označit je pomocí atributu [ServiceContract]. Označte všechny metody, klienti nebudou mít dovoleno volání s [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-251">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="9b6c5-252">**Vytvoření kontraktu dat.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-252">**Create the data contract.**</span></span> <span data-ttu-id="9b6c5-253">Definování typů dat, které se vyměňují mezi serverem a klientem a označit je pomocí atributu [kontraktu].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-253">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="9b6c5-254">Označte všechny polí a vlastností, které se bude moct klient pomocí [DataMember].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-254">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="9b6c5-255">**Vytvoření kontraktu selhání (nepovinné).**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-255">**Create the fault contract (optional).**</span></span> <span data-ttu-id="9b6c5-256">Vytvoření typů, které se vyměňují mezi serverem a klientem, když dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-256">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="9b6c5-257">Označte tyto typy s [kontraktu] a [DataMember] tak, aby byly serializable.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-257">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="9b6c5-258">Pro všechny operace služby, které jste označili [OperationContract] také označte je pomocí [FaultContract] k označení chyb, které se můžou vrátit.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-258">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="9b6c5-259">**Nakonfigurujte a hostitelem služby.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-259">**Configure and host the service.**</span></span> <span data-ttu-id="9b6c5-260">Po vytvoření kontraktu služby, dalším krokem je konfigurace vazbu ke zveřejnění službu na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-260">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="9b6c5-261">Další informace najdete v tématu [koncové body: adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-261">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="9b6c5-262">Jakmile aplikaci Vzdálená komunikace byla migrována do WCF, je stále důležité odebrání závislostí na .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-262">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="9b6c5-263">Tím se zajistí, že žádné ohrožení zabezpečení vzdálené komunikace se odeberou z aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-263">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="9b6c5-264">Tyto kroky zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-264">These steps include the following:</span></span>  
  
-   <span data-ttu-id="9b6c5-265">**Přestat používat MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-265">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="9b6c5-266">Typ MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-266">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="9b6c5-267">Všechny typy aplikací, které dílčí třídy MarshalByRefObject by měla být odebrán nebo změněn.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-267">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span> <span data-ttu-id="9b6c5-268">Typ MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-268">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="9b6c5-269">Všechny typy aplikací, které dílčí třídy MarshalByRefObject by měla být odebrán nebo změněn.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-269">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="9b6c5-270">**Ukončí použití [Serializable] a ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="9b6c5-270">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="9b6c5-271">Atribut [Serializable] a ISerializable rozhraní byly původně navrženy k serializaci typů v rámci důvěryhodné prostředí a jsou používány vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-271">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="9b6c5-272">Serializace WCF spoléhá na typy, které je označené jako [kontraktu] a [DataMember].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-272">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="9b6c5-273">Datové typy používané aplikace by měl být upraven, abyste mohli používat [kontraktu] a nepoužívat ISerializable nebo [Serializable].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-273">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span> <span data-ttu-id="9b6c5-274">Atribut [Serializable] a ISerializable rozhraní byly původně navrženy k serializaci typů v rámci důvěryhodné prostředí a jsou používány vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-274">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="9b6c5-275">Serializace WCF spoléhá na typy, které je označené jako [kontraktu] a [DataMember].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-275">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="9b6c5-276">Datové typy používané aplikace by měl být upraven, abyste mohli používat [kontraktu] a nepoužívat ISerializable nebo [Serializable].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-276">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="9b6c5-277">Scénáře migrace</span><span class="sxs-lookup"><span data-stu-id="9b6c5-277">Migration Scenarios</span></span>  
 <span data-ttu-id="9b6c5-278">Nyní Podíváme se, jak provést následující běžné scénáře vzdálené komunikace ve WCF:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-278">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1.  <span data-ttu-id="9b6c5-279">Server vrátí klientovi pomocí hodnota objektu</span><span class="sxs-lookup"><span data-stu-id="9b6c5-279">Server returns an object by-value to the client</span></span>  
  
2.  <span data-ttu-id="9b6c5-280">Server vrátí odkaz na objekt podle – pro klienta</span><span class="sxs-lookup"><span data-stu-id="9b6c5-280">Server returns an object by-reference to the client</span></span>  
  
3.  <span data-ttu-id="9b6c5-281">Klient odešle na server pomocí hodnota objektu</span><span class="sxs-lookup"><span data-stu-id="9b6c5-281">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b6c5-282">Odesílání odkaz na objekt podle-od klienta k serveru není povolen ve WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-282">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="9b6c5-283">Při čtení prostřednictvím těchto scénářů, předpokládá, že naše základní rozhraní pro .NET Remoting vypadat podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-283">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="9b6c5-284">Implementace .NET Remoting důležité zde není vzhledem k tomu, že chceme ilustrují pouze způsob implementace ekvivalentní funkce pomocí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-284">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="9b6c5-285">Scénář 1: Služba vrátí objekt podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="9b6c5-285">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="9b6c5-286">Tento scénář předvádí, server vrátí objekt, do klienta podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-286">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="9b6c5-287">WCF vždy vrátí objekty ze serveru podle hodnoty, takže následující kroky popisují jednoduše jak sestavit normální služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-287">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1.  <span data-ttu-id="9b6c5-288">Začněte definováním veřejné rozhraní pro službu WCF a označte ji s atributem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-288">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="9b6c5-289">[OperationContract] používáme k identifikaci metody na straně serveru, který bude volat naše klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-289">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2.  <span data-ttu-id="9b6c5-290">Dalším krokem je vytvoření kontraktu dat pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-290">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="9b6c5-291">Provedeme to vytvořením třídy (ne rozhraní) s atributem [kontraktu].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-291">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="9b6c5-292">Jednotlivé vlastnosti nebo pole, která má být viditelná pro klientské a serverové jsou označené [DataMember].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-292">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="9b6c5-293">Pokud odvozené typy smí chceme, jsme musí identifikovat pomocí atributu [Třída KnownType].</span><span class="sxs-lookup"><span data-stu-id="9b6c5-293">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="9b6c5-294">Pouze typy WCF umožní serializován nebo deserializován pro tuto službu, jsou rozhraní služby a tyto "známé typy".</span><span class="sxs-lookup"><span data-stu-id="9b6c5-294">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="9b6c5-295">Probíhá pokus o exchange libovolného typu nejsou v tomto seznamu budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-295">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3.  <span data-ttu-id="9b6c5-296">V dalším kroku poskytujeme implementaci pro rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-296">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4.  <span data-ttu-id="9b6c5-297">Pokud chcete spustit službu WCF, je potřeba deklarovat koncový bod, který zpřístupňuje rozhraní této služby na konkrétní adrese URL, pomocí konkrétní vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-297">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="9b6c5-298">To se obvykle provádí přidáním následující části souboru web.config serverový projekt.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-298">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5.  <span data-ttu-id="9b6c5-299">Pak se spuštění služby WCF s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-299">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="9b6c5-300">Při spuštění této ServiceHost pomocí souboru web.config zřizuje správné kontrakt, vazbu a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-300">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="9b6c5-301">Další informace o konfiguračních souborech najdete v tématu [konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-301">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="9b6c5-302">Tento styl spouštění serveru se označuje jako vlastní hostování.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-302">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="9b6c5-303">Další informace o další možnosti pro hostování služby WCF najdete v tématu [hostování služeb](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-303">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6.  <span data-ttu-id="9b6c5-304">App.config projektu klienta je třeba deklarovat odpovídající informace o vazbě pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-304">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="9b6c5-305">Nejjednodušší způsob, jak to udělat v sadě Visual Studio je použití **přidat odkaz na službu**, který se automaticky aktualizuje soubor app.config.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-305">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="9b6c5-306">Tyto změny budou stejně Alternativně lze přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-306">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="9b6c5-307">Další informace o používání **přidat odkaz na službu**, najdete v části [postupy: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-307">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7.  <span data-ttu-id="9b6c5-308">Služby WCF jsme teď můžete volat z klienta.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-308">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="9b6c5-309">Jsme to udělat vytvoření postupu kanálu pro tuto službu požadující kanál a přímo volání metody, které má být v tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-309">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="9b6c5-310">Jsme lze provést, protože kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku pro nás.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-310">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="9b6c5-311">Vrácená hodnota z volání této metody se deserializovat kopii odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-311">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 <span data-ttu-id="9b6c5-312">Objektů vrácený WCF ze serveru do klienta se vždycky hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-312">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="9b6c5-313">Objekty jsou deserializovat kopie data odeslaná na server.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-313">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="9b6c5-314">Klienta můžete volat metody pro tyto místní kopie bez jakékoli nebezpečí vyvolání kódu serveru prostřednictvím zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-314">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="9b6c5-315">Scénář 2: Server vrátí objekt odkazem</span><span class="sxs-lookup"><span data-stu-id="9b6c5-315">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="9b6c5-316">Tento scénář předvádí serveru, který poskytuje objekt klientovi odkazem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-316">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="9b6c5-317">V .NET Remoting, to je automaticky zpracována pro jakéhokoli typu odvozeného z MarshalByRefObject, což je serializovat odkazem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-317">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="9b6c5-318">Příkladem tento scénář umožňuje více klientů mít nezávislé relacemi server na straně objektů.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-318">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="9b6c5-319">Jak už jsme zmínili, objektů vrácený služby WCF jsou vždy podle hodnoty, takže není ekvivalent objektu odkazem, ale je možné dosáhnout podobný pomocí sémantiky odkazem <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-319">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="9b6c5-320">Toto je objekt serializovatelný podle hodnoty, které je možné klientem pro získání objektu relacemi odkazem na serveru.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-320">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="9b6c5-321">To umožňuje scénáře s více klientů s nezávislé objekty relací na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-321">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1.  <span data-ttu-id="9b6c5-322">Nejprve musíme definování kontraktu služby WCF, která odpovídá relacemi odkaz sám na sebe.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-322">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    >  <span data-ttu-id="9b6c5-323">Všimněte si, že objekt relacemi označeno [ServiceContract], což normální rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-323">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="9b6c5-324">Nastavení SessionMode vlastnost značí, že bude relacemi služby.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-324">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="9b6c5-325">Ve službě WCF relace je způsob korelace více zprávy odeslané mezi dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-325">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="9b6c5-326">To znamená, že Jakmile klient obdrží připojení k této službě, relace navázat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-326">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="9b6c5-327">Klient použije jeden jedinečný výskyt serverový objekt pro všechny jeho interakce v rámci této jedné relace.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-327">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2.  <span data-ttu-id="9b6c5-328">V dalším kroku potřebujeme k zajištění implementace tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-328">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="9b6c5-329">Představující s [ServiceBehavior] a nastavením InstanceContextMode, jsme zjistit WCF, že nám chcete použít pro každou relaci jedinečné instance tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-329">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3.  <span data-ttu-id="9b6c5-330">Nyní potřebujeme způsob, jak získat instanci tohoto objektu relacemi.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-330">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="9b6c5-331">Provedeme to tak, že vytvoříte jiné rozhraní služby WCF, která vrací objekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-331">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="9b6c5-332">Toto je serializovatelný formu koncový bod, který může klient použít k vytvoření relací objektu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-332">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="9b6c5-333">A implementaci této služby WCF:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-333">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="9b6c5-334">Tato implementace udržuje singleton postup kanálu k vytváření relací objektů.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-334">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="9b6c5-335">Při volání GetInstanceAddress() vytvoří kanál a vytvoří objekt EndpointAddress10 efektivně odkazující na vzdálené adresy přidružené k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-335">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="9b6c5-336">EndpointAddress10 je jednoduše datový typ, který může být vrácen do klienta pomocí hodnota.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-336">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4.  <span data-ttu-id="9b6c5-337">Je potřeba upravit konfigurační soubor serveru pomocí tohoto postupu následující dva postupy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-337">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="9b6c5-338">Deklarace \<klienta > oddíl, který popisuje koncový bod pro objekt relacemi.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-338">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="9b6c5-339">To je nezbytné, protože server taky funguje jako klient v této situaci.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-339">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="9b6c5-340">Koncové body pro objekt factory a sessionful deklarujte.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-340">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="9b6c5-341">To je potřeba povolit klientům komunikovat pomocí koncových bodů služby získat EndpointAddress10 a k vytvoření kanálu relací.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-341">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="9b6c5-342">A potom můžeme začít tyto služby:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-342">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  <span data-ttu-id="9b6c5-343">Nakonfigurujeme klienta deklarováním tyto stejné koncové body v souboru app.config jeho projektu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-343">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6.  <span data-ttu-id="9b6c5-344">Chcete-li vytvořit a použít tento objekt relacemi, musíte klienta udělat následující kroky:</span><span class="sxs-lookup"><span data-stu-id="9b6c5-344">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="9b6c5-345">Vytvoření kanálu pro službu ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-345">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="9b6c5-346">Tento kanál používaná k volání této služby k získání EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-346">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="9b6c5-347">Pomocí EndpointAddress10 k vytvoření kanálu pro získání objektu relacemi.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-347">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="9b6c5-348">Komunikovat s relacemi objekt, který má ukazují, že zůstane na stejnou instanci napříč více volání.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-348">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="9b6c5-349">Objekty WCF vždy vrátí hodnotu, ale je možné podporovat ekvivalent odkazem sémantiku prostřednictvím EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-349">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="9b6c5-350">To umožňuje klientovi požadavku relacemi instance služby WCF, po který může komunikovat s ním stejně jako ostatní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-350">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="9b6c5-351">Scénář 3: Klient odešle serveru Instance-hodnota</span><span class="sxs-lookup"><span data-stu-id="9b6c5-351">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="9b6c5-352">Tento scénář předvádí, klient pro odeslání na server instance objektu není primitivní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-352">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="9b6c5-353">Protože WCF odesílá pouze objekty podle hodnoty, tento scénář předvádí normálního využití WCF.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-353">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1.  <span data-ttu-id="9b6c5-354">Použijte stejnou službu WCF z scénář 1.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-354">Use the same WCF Service from Scenario 1.</span></span>  
  
2.  <span data-ttu-id="9b6c5-355">Pomocí klienta můžete vytvořit nový objekt-hodnota (zákazníka), vytvořit kanál ke komunikaci se službou ICustomerService a poslat objektu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-355">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     <span data-ttu-id="9b6c5-356">Objekt zákazníka bude serializován a odesílá na server, kde je deserializovat do novou kopii tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-356">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b6c5-357">Tento kód také ukazuje odesílání odvozený typ (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-357">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="9b6c5-358">Rozhraní služby očekává objekt zákazníků, ale atribut [Třída KnownType] k třídě zákazníka označil že premiumcustomer také povolený.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-358">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="9b6c5-359">WCF se nezdaří pokusy o serializaci nebo deserializaci žádným jiným typem prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-359">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="9b6c5-360">Normální WCF výměny dat jsou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-360">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="9b6c5-361">To zaručuje, že volání metod v jednom z těchto objektů dat provádí pouze místně – ho nebude vyvolání kódu v jiné vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-361">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="9b6c5-362">Když je možné dosáhnout něco podobného jako vrácených objektů odkazem *z* serveru, není možné pro klienta předat objekt odkazem *k* serveru.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-362">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="9b6c5-363">Ve službě WCF pomocí duplexní služby se dá dosáhnout scénáře, který vyžaduje konverzace přepínat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-363">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="9b6c5-364">Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="9b6c5-364">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="9b6c5-365">Souhrn</span><span class="sxs-lookup"><span data-stu-id="9b6c5-365">Summary</span></span>  
 <span data-ttu-id="9b6c5-366">.NET remoting je určena pro použití pouze v rámci prostředí plně důvěryhodná komunikace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-366">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="9b6c5-367">Je starší verze produktu a podporované pouze z důvodů zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-367">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="9b6c5-368">Není vhodné používat k vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-368">It should not be used to build new applications.</span></span> <span data-ttu-id="9b6c5-369">Naopak WCF byl navržen s důrazem na bezpečnost a doporučuje se pro nových nebo stávajících aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-369">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="9b6c5-370">Společnost Microsoft doporučuje, že existující aplikací vzdálené komunikace migrovat místo toho použít WCF nebo webové rozhraní API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9b6c5-370">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>