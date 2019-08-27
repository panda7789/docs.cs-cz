---
title: Migrace z .NET Remoting do WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c42255a14a23cb50f3fe8be434efab4af7361daa
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045859"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="6e5d2-102">Migrace z .NET Remoting do WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="6e5d2-103">Tento článek popisuje, jak migrovat aplikaci, která používá vzdálenou komunikaci rozhraní .NET pro použití Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6e5d2-104">Porovnává podobné koncepce mezi těmito produkty a potom popisuje, jak provést několik běžných scénářů vzdálené komunikace ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="6e5d2-105">Vzdálená komunikace .NET je starší verze produktu, která je podporována pouze pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="6e5d2-106">Není zabezpečený napříč prostředími se smíšeným vztahem důvěryhodnosti, protože nemůže udržovat samostatné úrovně důvěryhodnosti mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="6e5d2-107">Například nikdy byste neměli zveřejnit koncový bod vzdálené komunikace rozhraní .NET pro Internet nebo nedůvěryhodné klienty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="6e5d2-108">Doporučujeme migrovat existující aplikace vzdálené komunikace na novější a bezpečnější technologie.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="6e5d2-109">Pokud návrh aplikace používá pouze HTTP a je RESTful, doporučujeme webové rozhraní API pro ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="6e5d2-110">Další informace najdete v tématu webové rozhraní API pro ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="6e5d2-111">Pokud je aplikace založená na protokolu SOAP nebo vyžaduje jiné protokoly než HTTP jako TCP, doporučujeme WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="6e5d2-112">Porovnání vzdálené komunikace .NET s WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="6e5d2-113">Tato část porovnává základní stavební kameny vzdálené komunikace .NET se svými ekvivalenty WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="6e5d2-114">Tyto stavební bloky budeme později používat k vytvoření některých běžných scénářů klient-server ve službě WCF. Následující tabulka shrnuje hlavní podobnosti a rozdíly mezi službami vzdálené komunikace a WCF v technologii .NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="6e5d2-115">Vzdálené komunikace pomocí rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="6e5d2-115">.NET Remoting</span></span>|<span data-ttu-id="6e5d2-116">WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="6e5d2-117">Typ serveru</span><span class="sxs-lookup"><span data-stu-id="6e5d2-117">Server type</span></span>|<span data-ttu-id="6e5d2-118">Třída MarshalByRefObject třídy</span><span class="sxs-lookup"><span data-stu-id="6e5d2-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="6e5d2-119">Označit atributem [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="6e5d2-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="6e5d2-120">Operace služby</span><span class="sxs-lookup"><span data-stu-id="6e5d2-120">Service operations</span></span>|<span data-ttu-id="6e5d2-121">Veřejné metody typu serveru</span><span class="sxs-lookup"><span data-stu-id="6e5d2-121">Public methods on server type</span></span>|<span data-ttu-id="6e5d2-122">Označit atributem [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="6e5d2-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="6e5d2-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="6e5d2-123">Serialization</span></span>|<span data-ttu-id="6e5d2-124">ISerializable nebo [serializovatelný]</span><span class="sxs-lookup"><span data-stu-id="6e5d2-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="6e5d2-125">DataContractSerializer nebo XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="6e5d2-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="6e5d2-126">Předané objekty</span><span class="sxs-lookup"><span data-stu-id="6e5d2-126">Objects passed</span></span>|<span data-ttu-id="6e5d2-127">Podle hodnoty nebo podle odkazu</span><span class="sxs-lookup"><span data-stu-id="6e5d2-127">By-value or by-reference</span></span>|<span data-ttu-id="6e5d2-128">Pouze podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="6e5d2-128">By-value only</span></span>|  
|<span data-ttu-id="6e5d2-129">Chyby a výjimky</span><span class="sxs-lookup"><span data-stu-id="6e5d2-129">Errors/exceptions</span></span>|<span data-ttu-id="6e5d2-130">Jakákoli serializovatelný výjimka</span><span class="sxs-lookup"><span data-stu-id="6e5d2-130">Any serializable exception</span></span>|<span data-ttu-id="6e5d2-131">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="6e5d2-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="6e5d2-132">Klientské proxy objekty</span><span class="sxs-lookup"><span data-stu-id="6e5d2-132">Client proxy objects</span></span>|<span data-ttu-id="6e5d2-133">Silné typy transparentní proxy servery se vytvářejí automaticky z MarshalByRefObjects.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="6e5d2-134">Proxy silného typu se generují na vyžádání pomocí třídy ChannelFactory\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="6e5d2-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="6e5d2-135">Požadovaná platforma</span><span class="sxs-lookup"><span data-stu-id="6e5d2-135">Platform required</span></span>|<span data-ttu-id="6e5d2-136">Klient i server musí používat Microsoft OS a .NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="6e5d2-137">Pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="6e5d2-137">Cross-platform</span></span>|  
|<span data-ttu-id="6e5d2-138">Formát zprávy</span><span class="sxs-lookup"><span data-stu-id="6e5d2-138">Message format</span></span>|<span data-ttu-id="6e5d2-139">Soukromé</span><span class="sxs-lookup"><span data-stu-id="6e5d2-139">Private</span></span>|<span data-ttu-id="6e5d2-140">Oborové standardy (SOAP, WS-\* atd.)</span><span class="sxs-lookup"><span data-stu-id="6e5d2-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="6e5d2-141">Porovnání implementace serveru</span><span class="sxs-lookup"><span data-stu-id="6e5d2-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="6e5d2-142">Vytvoření serveru v technologii vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="6e5d2-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="6e5d2-143">Typy serverů vzdálené komunikace .NET musí být odvozeny od metody MarshalByRefObject a definovat metody, které může klient volat, například následující:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="6e5d2-144">Veřejné metody tohoto typu serveru se stanou veřejnými kontrakty dostupnými klientům.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="6e5d2-145">Neexistuje žádné oddělení mezi veřejným rozhraním serveru a jeho implementací – jeden typ zpracovává oba.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="6e5d2-146">Po definování typ serveru ho můžete zpřístupnit klientům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="6e5d2-147">Existuje mnoho způsobů, jak nastavit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="6e5d2-148">Toto je pouze jeden příklad.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="6e5d2-149">Vytvoření serveru ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="6e5d2-150">Ekvivalentní krok v rámci WCF zahrnuje vytvoření dvou typů – veřejné "kontrakt služby" a konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="6e5d2-151">První je deklarován jako rozhraní s označením [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="6e5d2-152">Metody, které jsou k dispozici pro klienty, jsou označeny [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="6e5d2-153">Implementace serveru je definována v samostatné konkrétní třídě, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="6e5d2-154">Po definování těchto typů lze Server WCF zpřístupnit klientům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
> <span data-ttu-id="6e5d2-155">Protokol TCP se v obou příkladech používá k tomu, aby byl podobný jako možný.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="6e5d2-156">Příklady použití HTTP najdete v tématu věnovaném scénářům, které jsou dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="6e5d2-157">Existuje mnoho způsobů, jak nakonfigurovat a hostovat služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="6e5d2-158">Toto je pouze jeden příklad, označovaný jako "místní hostování".</span><span class="sxs-lookup"><span data-stu-id="6e5d2-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="6e5d2-159">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-159">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="6e5d2-160">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="6e5d2-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="6e5d2-161">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="6e5d2-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="6e5d2-162">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="6e5d2-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="6e5d2-163">Porovnání implementace klienta</span><span class="sxs-lookup"><span data-stu-id="6e5d2-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="6e5d2-164">Vytvoření klienta v technologii vzdálené komunikace .NET</span><span class="sxs-lookup"><span data-stu-id="6e5d2-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="6e5d2-165">Jakmile je objekt serveru vzdálené komunikace .NET k dispozici, může je klient spotřebovat, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="6e5d2-166">Instance RemotingServer vrácená z Activator. GetObject () se označuje jako "transparentní proxy server".</span><span class="sxs-lookup"><span data-stu-id="6e5d2-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="6e5d2-167">Implementuje veřejné rozhraní API pro typ RemotingServer na klientovi, ale všechny metody volají objekt serveru běžící v jiném procesu nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="6e5d2-168">Vytvoření klienta ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="6e5d2-169">Stejný krok služby WCF zahrnuje použití továrny kanálu k vytvoření proxy serveru explicitně.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="6e5d2-170">Podobně jako u vzdálené komunikace lze objekt proxy použít k vyvolání operací na serveru, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="6e5d2-171">Tento příklad ukazuje programování na úrovni kanálu, protože je nejvíce podobný příkladu vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="6e5d2-172">K dispozici je také **Přidat odkaz na službu** přístup v aplikaci Visual Studio, který generuje kód pro zjednodušení programování klienta.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="6e5d2-173">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-173">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="6e5d2-174">Programování klienta na úrovni kanálu</span><span class="sxs-lookup"><span data-stu-id="6e5d2-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="6e5d2-175">Postupy: Přidání, aktualizace nebo odebrání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="6e5d2-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="6e5d2-176">Využití serializace</span><span class="sxs-lookup"><span data-stu-id="6e5d2-176">Serialization Usage</span></span>  
 <span data-ttu-id="6e5d2-177">Vzdálená komunikace rozhraní .NET i služba WCF používají serializace k posílání objektů mezi klientem a serverem, ale liší se v těchto důležitých způsobech:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="6e5d2-178">Používají různé serializace a konvence k označení toho, co se má serializovat.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="6e5d2-179">Vzdálená komunikace .NET podporuje serializaci "podle odkazu", která umožňuje přístup k metodě nebo vlastnostem na jedné úrovni ke spouštění kódu na jiné úrovni, který je napříč hranicemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="6e5d2-180">Tato funkce zveřejňuje chyby zabezpečení a je jedním z hlavních důvodů, proč by koncové body vzdálené komunikace neměly být nikdy vystaveny nedůvěryhodným klientům.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="6e5d2-181">Serializace, kterou používá Vzdálená komunikace, je odhlášená (explicitně vyloučit, co se neserializace) a serializace WCF je výslovný souhlas (explicitně označit členy k serializaci).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="6e5d2-182">Serializace ve vzdálené komunikaci .NET</span><span class="sxs-lookup"><span data-stu-id="6e5d2-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="6e5d2-183">Vzdálená komunikace .NET podporuje dva způsoby serializace a deserializace objektů mezi klientem a serverem:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="6e5d2-184">*Podle hodnoty* – hodnoty objektu jsou serializovány napříč hranicemi vrstev a nová instance tohoto objektu je vytvořena na druhé úrovni.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="6e5d2-185">Všechna volání metod nebo vlastností této nové instance se spouštějí pouze místně a neovlivňují původní objekt nebo vrstvu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="6e5d2-186">Odkazem – speciální "odkaz na objekt" je serializován napříč hranicemi vrstev.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="6e5d2-187">Když jedna vrstva komunikuje s metodami nebo vlastnostmi tohoto objektu, komunikuje zpátky původnímu objektu na původní úrovni.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="6e5d2-188">Objekty podle odkazu můžou v obou směrech směrovat – server na klienta nebo klienta na server.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="6e5d2-189">Typy podle hodnot ve vzdálené komunikaci jsou označeny atributem [serializovatelný] nebo implementací ISerializable, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="6e5d2-190">Odkazem typy jsou odvozeny ze třídy MarshalByRefObject, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="6e5d2-191">Je mimořádně důležité pochopit důsledky objektů odkazujících na vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="6e5d2-192">Pokud kterákoli z vrstev (klienta nebo serveru) odesílá objekt odkazem na druhou úroveň, všechny volání metody se vrátí zpět na úrovni, která je vlastníkem objektu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="6e5d2-193">Například metoda volání metody na objektu podle odkazu, kterou vrátil server, bude spouštět kód na serveru.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="6e5d2-194">Podobně server volající metody v objektu podle odkazu poskytovaný klientem spustí kód zpět v klientovi.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="6e5d2-195">Z tohoto důvodu se použití vzdálené komunikace .NET doporučuje jenom v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="6e5d2-196">Zveřejnění veřejného koncového bodu vzdálené komunikace .NET pro nedůvěryhodné klienty způsobí, že se server vzdálené komunikace bude zranitelný vůči útokům.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="6e5d2-197">Serializace ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-197">Serialization in WCF</span></span>  
 <span data-ttu-id="6e5d2-198">WCF podporuje pouze serializaci podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="6e5d2-199">Nejběžnější způsob, jak definovat typ pro výměnu mezi klientem a serverem, je jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="6e5d2-200">Atribut [DataContract] identifikuje tento typ jako ten, který lze serializovat a deserializovat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="6e5d2-201">Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole k serializaci.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="6e5d2-202">Když WCF odesílá objekt napříč vrstvami, serializovat pouze hodnoty a vytvoří novou instanci objektu na druhé úrovni.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="6e5d2-203">Jakékoli interakce s hodnotami objektu se projeví pouze lokálně – nekomunikují s druhou vrstvou, jak fungují objekty vzdálené komunikace .NET podle referencí.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="6e5d2-204">Další informace naleznete v tématu [serializace a](./feature-details/serialization-and-deserialization.md)deserializace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-204">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="6e5d2-205">Možnosti zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="6e5d2-205">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="6e5d2-206">Výjimky při vzdálené komunikaci .NET</span><span class="sxs-lookup"><span data-stu-id="6e5d2-206">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="6e5d2-207">Výjimky vyvolané vzdáleným serverem jsou serializovány, odesílány klientovi a vyvolány místně na klientovi jako jakákoli jiná výjimka.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-207">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="6e5d2-208">Vlastní výjimky lze vytvořit pomocí dílčí třídy typu výjimky a označením pomocí [serializovatelný].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-208">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="6e5d2-209">Většina výjimek rozhraní je již tímto způsobem označena, což umožňuje vyvolání serveru, jeho serializace a opětovného vyvolání v klientovi.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-209">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="6e5d2-210">I když je tento návrh vhodný během vývoje, můžou být informace na straně serveru neúmyslně zveřejněné klientovi.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-210">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="6e5d2-211">Toto je jeden z mnoha důvodů, proč by se Vzdálená komunikace mohla používat jenom v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-211">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="6e5d2-212">Výjimky a chyby ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-212">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="6e5d2-213">Služba WCF nepovoluje vrácení libovolných typů výjimek ze serveru klientovi, protože by mohlo dojít k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-213">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="6e5d2-214">Pokud operace služby vyvolá neočekávanou výjimku, způsobí to, že na klientovi bude vyvolána FaultExceptiona pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-214">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="6e5d2-215">Tato výjimka neposkytuje žádné informace, proč došlo k problému, a pro některé aplikace to postačuje.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-215">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="6e5d2-216">Aplikace, které potřebují sdělit rozsáhlejší informace o chybách klientovi, najdete tak, že nadefinujete kontrakt selhání.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-216">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="6e5d2-217">Chcete-li to provést, vytvořte nejprve typ [DataContract], který bude obsahovat informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-217">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="6e5d2-218">Zadejte kontrakt selhání, který se má použít pro každou operaci služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-218">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="6e5d2-219">Server hlásí chybové stavy vyvoláním FaultException.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-219">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="6e5d2-220">A vždy, když klient odešle požadavek na server, může zachytit chyby jako normální výjimky.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-220">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="6e5d2-221">Další informace o smlouvách o selhání najdete v <xref:System.ServiceModel.FaultException>tématu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-221">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="6e5d2-222">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6e5d2-222">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="6e5d2-223">Zabezpečení při vzdálené komunikaci .NET</span><span class="sxs-lookup"><span data-stu-id="6e5d2-223">Security in .NET Remoting</span></span>  
 <span data-ttu-id="6e5d2-224">Některé kanály vzdálené komunikace .NET podporují funkce zabezpečení, jako je ověřování a šifrování ve vrstvě kanálu (IPC a TCP).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-224">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="6e5d2-225">Kanál HTTP spoléhá na Internetová informační služba (IIS) pro ověřování i šifrování.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-225">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="6e5d2-226">I přes tuto podporu byste měli vzít v úvahu nezabezpečený komunikační protokol technologie .NET a použít ho jenom v plně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-226">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="6e5d2-227">Nikdy nezveřejňujte veřejný koncový bod vzdálené komunikace pro Internet nebo nedůvěryhodné klienty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-227">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="6e5d2-228">Zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-228">Security in WCF</span></span>  
 <span data-ttu-id="6e5d2-229">Služba WCF byla navržena s ohledem na zabezpečení, v rámci řešení druhů ohrožení zabezpečení zjištěných při vzdálené komunikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-229">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="6e5d2-230">WCF nabízí zabezpečení na úrovni přenosu i zprávy a nabízí mnoho možností pro ověřování, autorizaci, šifrování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-230">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="6e5d2-231">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-231">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="6e5d2-232">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6e5d2-232">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="6e5d2-233">Pokyny pro zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-233">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="6e5d2-234">Migrace na WCF</span><span class="sxs-lookup"><span data-stu-id="6e5d2-234">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="6e5d2-235">Proč migrovat ze vzdálené komunikace na WCF?</span><span class="sxs-lookup"><span data-stu-id="6e5d2-235">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="6e5d2-236">**Vzdálená komunikace .NET je starší verze produktu.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-236">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="6e5d2-237">Jak je popsáno v tématu [Vzdálená komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), se považuje za starší verzi produktu a nedoporučuje se pro vývoj nových verzí.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-237">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="6e5d2-238">Pro nové i existující aplikace se doporučuje webové rozhraní API WCF nebo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-238">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="6e5d2-239">**WCF používá standardy pro různé platformy.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-239">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="6e5d2-240">Služba WCF byla navržena s ohledem na interoperabilitu různých platforem a podporuje řadu průmyslových standardů (SOAP, WS-Security, WS-Trust atd.).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-240">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="6e5d2-241">Služba WCF může spolupracovat s klienty, kteří běží na jiných operačních systémech než Windows.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-241">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="6e5d2-242">Vzdálená komunikace byla navržena primárně pro prostředí, kde jsou spouštěny servery i klientské aplikace pomocí rozhraní .NET Framework v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-242">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
- <span data-ttu-id="6e5d2-243">**WCF má integrované zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-243">**WCF has built-in security.**</span></span> <span data-ttu-id="6e5d2-244">Služba WCF byla navržena s ohledem na zabezpečení a nabízí mnoho možností ověřování, zabezpečení na úrovni přenosu, zabezpečení na úrovni zpráv atd. Vzdálená komunikace byla navržena tak, aby aplikacím usnadnila spolupráci, ale nebyla navržena tak, aby byla zabezpečena v nedůvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-244">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="6e5d2-245">Služba WCF byla navržena tak, aby fungovala v důvěryhodných i nedůvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-245">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="6e5d2-246">Doporučení pro migraci</span><span class="sxs-lookup"><span data-stu-id="6e5d2-246">Migration Recommendations</span></span>  
 <span data-ttu-id="6e5d2-247">Níže jsou uvedené doporučené kroky pro migraci ze vzdálené komunikace rozhraní .NET do WCF:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-247">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="6e5d2-248">**Vytvořte kontrakt služby.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-248">**Create the service contract.**</span></span> <span data-ttu-id="6e5d2-249">Definujte typy rozhraní služby a označte je atributem [ServiceContract]. Označte všechny metody, které budou klienti moci volat s [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-249">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="6e5d2-250">**Vytvoření kontraktu dat.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-250">**Create the data contract.**</span></span> <span data-ttu-id="6e5d2-251">Definujte typy dat, které se budou vyměňovat mezi serverem a klientem, a označte je atributem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-251">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="6e5d2-252">Označte všechna pole a vlastnosti, které bude klient moci používat s [DataMember].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-252">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="6e5d2-253">**Vytvořte kontrakt selhání (volitelné).**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-253">**Create the fault contract (optional).**</span></span> <span data-ttu-id="6e5d2-254">Vytvořte typy, které budou vyměňovány mezi serverem a klientem, pokud dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-254">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="6e5d2-255">Označte tyto typy pomocí [DataContract] a [DataMember], aby je bylo možné serializovat.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-255">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="6e5d2-256">U všech operací služby, které jste označili pomocí [OperationContract], je také označte pomocí [FaultContract], aby označovaly chyby, které mohou vracet.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-256">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="6e5d2-257">**Nakonfigurujte a hostovat službu.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-257">**Configure and host the service.**</span></span> <span data-ttu-id="6e5d2-258">Po vytvoření kontraktu služby je dalším krokem konfigurace vazby k vystavení služby na koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-258">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="6e5d2-259">Další informace najdete v tématu [koncové body: Adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-259">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="6e5d2-260">Jakmile se aplikace vzdálené komunikace migruje na WCF, je stále důležité odebrat závislosti na vzdálené komunikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-260">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="6e5d2-261">Tím se zajistí, že se z aplikace odeberou všechny chyby zabezpečení vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-261">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="6e5d2-262">Tyto kroky zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-262">These steps include the following:</span></span>  
  
- <span data-ttu-id="6e5d2-263">**Přerušit použití objektu MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-263">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="6e5d2-264">Typ MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán službou WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-264">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="6e5d2-265">Všechny typy aplikací, které má třída MarshalByRefObject třídy MarshalByRefObject odebrat nebo změnit.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-265">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="6e5d2-266">**Zrušit použití [serializovatelných vlastností] a ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="6e5d2-266">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="6e5d2-267">Atribut [serializovatelný] a rozhraní ISerializable byly původně určeny k serializaci typů v rámci důvěryhodných prostředí a jsou používány pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-267">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="6e5d2-268">Serializace WCF spoléhá na typy označené [DataContract] a [DataMember].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-268">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="6e5d2-269">Datové typy používané aplikací by měly být upraveny tak, aby používaly [DataContract] a nepoužívaly ISerializable nebo [serializovatelný].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-269">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="6e5d2-270">Scénáře migrace</span><span class="sxs-lookup"><span data-stu-id="6e5d2-270">Migration Scenarios</span></span>  
 <span data-ttu-id="6e5d2-271">Teď se podívejme, jak provádět následující běžné scénáře vzdálené komunikace ve službě WCF:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-271">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="6e5d2-272">Server vrátí klientovi objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-272">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="6e5d2-273">Server vrátí objekt podle odkazu na klienta.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-273">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="6e5d2-274">Klient pošle objekt po hodnotě na server.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-274">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e5d2-275">Odeslání objektu podle odkazu z klienta na server není v rámci WCF povoleno.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-275">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="6e5d2-276">Při čtení těchto scénářů Předpokládejme, že naše základní rozhraní pro vzdálenou komunikaci rozhraní .NET vypadají jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-276">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="6e5d2-277">Implementace vzdálené komunikace .NET není tady důležité, protože chceme ilustrovat jenom použití WCF k implementaci ekvivalentních funkcí.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-277">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="6e5d2-278">Scénář 1: Služba vrátí objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-278">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="6e5d2-279">Tento scénář ukazuje server, který vrací objekt klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-279">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="6e5d2-280">WCF vždycky vrátí objekty ze serveru podle hodnoty, takže následující kroky jednoduše popisují, jak sestavit normální službu WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-280">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="6e5d2-281">Začněte tím, že definujete veřejné rozhraní pro službu WCF a označíte ho atributem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-281">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="6e5d2-282">K identifikaci metod na straně serveru, které bude náš klient volat, používáme [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-282">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="6e5d2-283">Dalším krokem je vytvoření kontraktu dat pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-283">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="6e5d2-284">Provedeme to vytvořením tříd (ne rozhraní) označených atributem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-284">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="6e5d2-285">Jednotlivé vlastnosti nebo pole, které chceme zobrazit pro klienta i server, jsou označeny [DataMember].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-285">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="6e5d2-286">Pokud chceme, aby byly odvozené typy povoleny, je k jejich identifikaci nutné použít atribut [třída KnownType].</span><span class="sxs-lookup"><span data-stu-id="6e5d2-286">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="6e5d2-287">Pouze typy WCF umožní serializaci nebo deserializaci této služby jsou ty, které jsou v rozhraní služby a tyto "známé typy".</span><span class="sxs-lookup"><span data-stu-id="6e5d2-287">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="6e5d2-288">Pokus o výměnu jakéhokoli jiného typu, který není v tomto seznamu, bude odmítnut.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-288">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="6e5d2-289">Dále poskytujeme implementaci rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-289">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="6e5d2-290">Abychom mohli spustit službu WCF, musíme deklarovat koncový bod, který zveřejňuje toto rozhraní služby na konkrétní adrese URL pomocí konkrétní vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-290">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="6e5d2-291">To se obvykle provádí přidáním následujících sekcí do souboru Web. config v projektu serveru.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-291">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="6e5d2-292">Službu WCF lze následně spustit pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-292">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="6e5d2-293">Po spuštění této třídy ServiceHost použije soubor Web. config ke zřízení správného kontraktu, vazby a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-293">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="6e5d2-294">Další informace o konfiguračních souborech najdete v tématu [Konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-294">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="6e5d2-295">Tento styl spuštění serveru se označuje jako samoobslužné hostování.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-295">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="6e5d2-296">Další informace o dalších možnostech hostování služeb WCF najdete v tématu [hostingové služby](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-296">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="6e5d2-297">Soubor App. config klientského projektu musí deklarovat párové informace o vazbě koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-297">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="6e5d2-298">Nejjednodušší způsob, jak to provést v aplikaci Visual Studio, je použít **Přidat odkaz na službu**, který bude automaticky aktualizovat soubor App. config.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-298">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="6e5d2-299">Tyto změny lze také přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-299">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="6e5d2-300">Další informace o použití **Přidat odkaz na službu**naleznete v tématu [How to: Přidejte, aktualizujte nebo odeberte odkaz](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)na službu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-300">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="6e5d2-301">Nyní můžeme volat službu WCF z klienta.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-301">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="6e5d2-302">Provedeme to vytvořením továrny kanálů pro tuto službu, vyžádáním pro kanál a přímo voláním metody, kterou chceme na tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-302">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="6e5d2-303">Můžeme to udělat, protože kanál implementuje rozhraní služby a zpracovává základní logiku požadavků a odpovědí pro nás.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-303">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="6e5d2-304">Návratovou hodnotou z tohoto volání metody je deserializovaná kopie odpovědi serveru.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-304">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="6e5d2-305">Objekty vrácené službou WCF ze serveru do klienta jsou vždy podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-305">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="6e5d2-306">Objekty jsou deserializované kopie dat odesílaných serverem.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-306">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="6e5d2-307">Klient může volat metody pro tyto místní kopie bez jakéhokoli nebezpečí vyvolání kódu serveru prostřednictvím zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-307">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="6e5d2-308">Scénář 2: Server vrátí objekt podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-308">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="6e5d2-309">Tento scénář ukazuje, jak server, který klientovi poskytuje objekt, odkazem.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-309">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="6e5d2-310">V případě vzdálené komunikace rozhraní .NET je tato služba zpracována automaticky pro jakýkoli typ odvozený od třídy MarshalByRefObject, který je serializován podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-310">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="6e5d2-311">Příkladem tohoto scénáře je umožněno, aby více klientů mělo nezávislé relace objektů na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-311">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="6e5d2-312">Jak už jsme uvedli, objekty vrácené službou WCF jsou vždycky podle hodnoty, takže neexistuje přímý ekvivalent objektu podle odkazu, ale je možné dosáhnout podobné sémantiky odkazování pomocí <xref:System.ServiceModel.EndpointAddress10> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-312">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="6e5d2-313">Toto je serializovatelný objekt podle hodnoty, který může klient použít k získání relace pomocí objektu odkazem na server.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-313">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="6e5d2-314">To umožňuje situaci, kdy je více klientů s nezávislou relací objektů na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-314">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="6e5d2-315">Nejdřív musíme definovat kontrakt služby WCF, který odpovídá samotnému objektu relace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-315">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    > <span data-ttu-id="6e5d2-316">Všimněte si, že objekt sessioning je označený jako [ServiceContract] a vytvoří normální rozhraní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-316">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="6e5d2-317">Nastavení vlastnosti SessionMode označuje, že se jedná o službu, která se jedná o relaci.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-317">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="6e5d2-318">V rámci WCF je relace způsob, jak korelovat více zpráv posílaných mezi dvěma koncovými body.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-318">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="6e5d2-319">To znamená, že jakmile klient získá připojení k této službě, bude vytvořena relace mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-319">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="6e5d2-320">Klient bude používat jednu jedinečnou instanci objektu na straně serveru pro všechny interakce v rámci této jediné relace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-320">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="6e5d2-321">Dál je potřeba poskytnout implementaci tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-321">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="6e5d2-322">Informování o tom, že se jedná o [ServiceBehavior] a nastavení InstanceContextMode, sdělujeme, že WCF chceme pro každou relaci použít jedinečnou instanci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-322">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="6e5d2-323">Teď potřebujeme způsob, jak získat instanci tohoto objektu relace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-323">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="6e5d2-324">Provedeme to vytvořením dalšího rozhraní služby WCF, které vrátí objekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-324">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="6e5d2-325">Jedná se o serializovatelný tvar koncového bodu, který může klient použít k vytvoření objektu relace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-325">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="6e5d2-326">A implementujeme tuto službu WCF:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-326">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="6e5d2-327">Tato implementace udržuje objekt pro vytváření relací s jedním prvkem.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-327">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="6e5d2-328">Když se zavolá GetInstanceAddress (), vytvoří kanál a vytvoří objekt EndpointAddress10, který efektivně odkazuje na vzdálenou adresu přidruženou k tomuto kanálu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-328">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="6e5d2-329">EndpointAddress10 je jednoduše datový typ, který může být vrácen klientovi podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-329">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="6e5d2-330">Musíme upravit konfigurační soubor serveru tak, že provedete následující dvě věci, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-330">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="6e5d2-331">Deklarujte > oddíl klienta, který popisuje koncový bod objektu sessioning. \<</span><span class="sxs-lookup"><span data-stu-id="6e5d2-331">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="6e5d2-332">To je nezbytné, protože server v této situaci také funguje jako klient.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-332">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="6e5d2-333">Deklarujte koncové body objektu pro vytváření a relaci.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-333">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="6e5d2-334">To je nezbytné, aby klient mohl komunikovat s koncovými body služby, aby získal EndpointAddress10 a vytvořil kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-334">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="6e5d2-335">A pak můžeme spustit tyto služby:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-335">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="6e5d2-336">Nakonfigurujte klienta deklarováním stejných koncových bodů v souboru App. config projektu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-336">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="6e5d2-337">Aby bylo možné vytvořit a použít tento objekt relace, klient musí provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6e5d2-337">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="6e5d2-338">Vytvořte kanál ke službě ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-338">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="6e5d2-339">Použijte tento kanál k vyvolání této služby k získání EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-339">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="6e5d2-340">Pomocí EndpointAddress10 vytvořte kanál pro získání objektu relace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-340">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="6e5d2-341">Interakce s objektem relace, aby se ukázalo, že zůstává stejná instance napříč více voláními.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-341">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="6e5d2-342">WCF vždycky vrací objekty podle hodnoty, ale je možné podporovat ekvivalent sémantiky odkazování prostřednictvím použití EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-342">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="6e5d2-343">To umožňuje klientovi, aby si vyžádal relaci instance služby WCF, po které s ní bude moct pracovat stejně jako s ostatními službami WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-343">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="6e5d2-344">Scénář 3: Klient odesílá instanci Server a podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-344">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="6e5d2-345">Tento scénář ukazuje klientovi, který neprimitivní instanci objektu odesílá do serveru podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-345">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="6e5d2-346">Protože WCF odesílá pouze objekty podle hodnoty, tento scénář ukazuje normální využití služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-346">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="6e5d2-347">Použijte stejnou službu WCF ze scénáře 1.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-347">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="6e5d2-348">Použijte klienta k vytvoření nového objektu podle hodnoty (zákazník), vytvořte kanál ke komunikaci se službou ICustomerService a odešlete do něj objekt.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-348">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="6e5d2-349">Objekt zákazníka bude serializován a odeslán na server, kde je deserializován do nové kopie tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-349">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6e5d2-350">Tento kód také znázorňuje odeslání odvozeného typu (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-350">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="6e5d2-351">Rozhraní služby očekává objekt zákazníka, ale atribut [třída KnownType] u třídy Customer, který je označen PremiumCustomer, byl také povolen.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-351">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="6e5d2-352">Služba WCF selže při pokusu o serializaci nebo deserializaci jakéhokoli jiného typu prostřednictvím tohoto rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-352">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="6e5d2-353">Normální výměny dat WCF jsou podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-353">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="6e5d2-354">To zaručuje, že vyvolání metod v jednom z těchto datových objektů se spustí pouze lokálně – nevyvolává kód na druhé úrovni.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-354">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="6e5d2-355">I když je možné dosáhnout nějakého typu, například objektů odkazujících na server, není možné, aby klient předal objektu odkazem *na* Server.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-355">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="6e5d2-356">Scénář, který vyžaduje, aby se konverzace mezi klientem a serverem mohla docílit přes službu WCF pomocí duplexní služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-356">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="6e5d2-357">Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-357">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6e5d2-358">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6e5d2-358">Summary</span></span>  
 <span data-ttu-id="6e5d2-359">Vzdálená komunikace .NET je komunikační rozhraní určené k použití pouze v rámci plně důvěryhodných prostředí.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-359">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="6e5d2-360">Je to starší verze produktu a je podporovaná jenom pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-360">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="6e5d2-361">Neměl by se používat k vytváření nových aplikací.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-361">It should not be used to build new applications.</span></span> <span data-ttu-id="6e5d2-362">Naopak služba WCF byla navržena s ohledem na zabezpečení a doporučuje se pro nové a stávající aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-362">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="6e5d2-363">Microsoft doporučuje, aby se stávající aplikace vzdálené komunikace migrovali na místo toho použití WCF nebo ASP.NET webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-363">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
