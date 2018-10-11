---
title: Přehled vytváření koncových bodů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: b72c3959b2a42c6a5abc8ef31975d5bdb9ce220e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086840"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="7c4bc-102">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="7c4bc-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="7c4bc-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) nastane prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="7c4bc-104">Koncové body poskytují klientům přístup k funkci, která nabízí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="7c4bc-105">Tato část popisuje strukturu koncový bod a ukazuje, jak definovat koncový bod v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="7c4bc-106">Struktura koncový bod</span><span class="sxs-lookup"><span data-stu-id="7c4bc-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="7c4bc-107">Každý koncový bod obsahuje adresu, která označuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem a kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="7c4bc-108">**Adresa**.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-108">**Address**.</span></span> <span data-ttu-id="7c4bc-109">Adresa jednoznačně identifikuje koncový bod a říká potenciálním zákazníkům, kde se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="7c4bc-110">Je zastoupena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> adresu, která obsahuje identifikátor URI (Uniform Resource) a vlastnosti adresy, které zahrnují identitu, některé prvky webové služby WSDL (Description Language) a kolekce volitelné záhlaví.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="7c4bc-111">Volitelná záhlaví poskytují další podrobné informace o adresování k identifikaci a k interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="7c4bc-112">Další informace najdete v tématu [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="7c4bc-113">**Vytvoření vazby**.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-113">**Binding**.</span></span> <span data-ttu-id="7c4bc-114">Vazba Určuje, jak se ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="7c4bc-115">Určuje vazbu, jak koncový bod komunikuje s ostatními, včetně protokolu přenosu (například TCP nebo HTTP), kódování, které pro zprávy (například text nebo binary) a jaké požadavky na zabezpečení, které jsou nezbytné (pro například Secure Sockets Layer [SSL] nebo zabezpečení zprávy protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="7c4bc-116">Další informace najdete v tématu [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="7c4bc-117">**Kontrakt služby**.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-117">**Service contract**.</span></span> <span data-ttu-id="7c4bc-118">Kontrakt služby popisuje, jaké funkce zpřístupňuje koncový bod do klienta.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="7c4bc-119">Kontrakt určuje operace, které můžete volat klienta, formulář zprávy a typ vstupních parametrů nebo data potřebná pro volání operace a druh zpracování nebo zprávy s odpovědí, kterou můžete očekávat, že klient.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="7c4bc-120">Tři základní typy kontraktů odpovídají základní zprávy exchange vzory (MEPs): datagram (jednocestné), požadavek/odpověď a přenos (obousměrné).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="7c4bc-121">Kontrakt služby můžete použít taky data a zprávy smlouvy tak, aby vyžadovala konkrétní datové typy a formáty zpráv při, ke kterému přistupujete.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="7c4bc-122">Další informace o tom, jak definování kontraktu služby najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="7c4bc-123">Všimněte si, že klient může rovněž vyžaduje, aby implementace kontraktu služby definované, volá se, kontrakt zpětného volání pro příjem zpráv ze služby v duplexním MEP.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="7c4bc-124">Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="7c4bc-125">Koncový bod služby lze toho pomocí kódu nebo deklarativně prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="7c4bc-126">Pokud nejsou zadány žádné koncové body modul runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každou smlouvu službou implementována.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="7c4bc-127">Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="7c4bc-128">Obecně je praktičtější k definování koncových bodů služby pomocí konfigurace namísto kódu.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="7c4bc-129">Udržování vazby a adresování informace mimo kód umožňující změnit bez nutnosti znovu kompilovat a opětovné nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c4bc-130">Při přidávání koncového bodu služby, který provádí zosobnění, je nutné použít jeden z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody nebo <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metoda správně načíst smlouvy do nové <xref:System.ServiceModel.Description.ServiceDescription> objektu.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="7c4bc-131">Definování koncových bodů v kódu</span><span class="sxs-lookup"><span data-stu-id="7c4bc-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="7c4bc-132">Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícími možnostmi:</span><span class="sxs-lookup"><span data-stu-id="7c4bc-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="7c4bc-133">Definují kontrakt `IEcho` typ služby, který přijímá název jiného uživatele a zpětné vazby pomocí odpověď "Hello \<jméno >!".</span><span class="sxs-lookup"><span data-stu-id="7c4bc-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="7c4bc-134">Implementace `Echo` služby typu definované `IEcho` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="7c4bc-135">Zadejte adresu koncového bodu z `http://localhost:8000/Echo` pro službu.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>  
  
-   <span data-ttu-id="7c4bc-136">Konfigurace `Echo` služby pomocí <xref:System.ServiceModel.WSHttpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  <span data-ttu-id="7c4bc-137">Hostitel služby je vytvořen pomocí základní adresu a pak je zbytek adresy, relativní k základní adresa, zadaný jako součást koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="7c4bc-138">Toto rozdělení do oddílů adresy umožňuje více koncových bodů, snadněji pro služby na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c4bc-139">Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> ve službě application nesmí upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodu na <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="7c4bc-140">Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost a `AddServiceEndpoint` metody <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, vyvolat výjimku, pokud byl změněn za tímto bodem.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="7c4bc-141">Ostatní umožňují upravovat, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="7c4bc-142">Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> hodnoty nesmí být změněny po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="7c4bc-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud byl změněn za tímto bodem.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="7c4bc-144">Ostatní hodnoty Popis klienta můžete změnit bez chyb, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="7c4bc-145">Ať už pro službu nebo klienta, se doporučuje, že upravíte popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="7c4bc-146">Definování koncových bodů v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7c4bc-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="7c4bc-147">Při vytváření aplikace, často chcete odložit rozhodnutí správce, který je nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="7c4bc-148">Například je často bude vědět předem, jaké služby Adresa (URI).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="7c4bc-149">Místo pevného kódování adresu, je vhodnější umožňují správcům udělat po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="7c4bc-150">Díky této flexibilitě se provádí prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="7c4bc-151">Podrobnosti najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c4bc-152">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config:` *filename*`[,`*filename* `]` přepnout na rychle vytvořte konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="7c4bc-153">Pomocí výchozí koncové body</span><span class="sxs-lookup"><span data-stu-id="7c4bc-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="7c4bc-154">Pokud nejsou zadány žádné koncové body, v kódu nebo v konfiguraci modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každou smlouvu službou implementována.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="7c4bc-155">Základní adresa se dá nastavit v kódu nebo v konfiguraci a jsou přidány výchozí koncové body, kdy <xref:System.ServiceModel.ICommunicationObject.Open> je volán na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7c4bc-156">Tento příklad je stejný příklad z předchozí části, ale protože nejsou zadány žádné koncové body, jsou přidány výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 <span data-ttu-id="7c4bc-157">Pokud koncové body jsou explicitně zadán, výchozí koncové body může být přidána voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c4bc-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="7c4bc-158">Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c4bc-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4bc-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c4bc-159">See Also</span></span>  
 [<span data-ttu-id="7c4bc-160">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="7c4bc-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
