---
title: Přehled vytváření koncových bodů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 46ca6294d68537e86a319b55d8c11e3ae0084738
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="cc728-102">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="cc728-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="cc728-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="cc728-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="cc728-104">Koncové body poskytují klientům přístup k funkce, které nabízí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="cc728-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="cc728-105">Tato část popisuje strukturu koncový bod a popisuje, jak definovat koncový bod v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="cc728-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="cc728-106">Struktura koncový bod</span><span class="sxs-lookup"><span data-stu-id="cc728-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="cc728-107">Každý koncový bod obsahuje adresu, která určuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem a kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="cc728-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="cc728-108">**Adresa**.</span><span class="sxs-lookup"><span data-stu-id="cc728-108">**Address**.</span></span> <span data-ttu-id="cc728-109">Adresa jednoznačně identifikuje koncový bod a potenciální spotřebitelé informuje, kde se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="cc728-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="cc728-110">Je zobrazena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> adresu, která obsahuje identifikátor URI (Uniform Resource) a vlastnosti adresy, které zahrnují identity, některé prvky webové služby popis Language (WSDL) a kolekce volitelné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="cc728-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="cc728-111">Volitelné hlavičky poskytují další podrobné adresování informace k identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="cc728-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="cc728-112">Další informace najdete v tématu [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="cc728-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="cc728-113">**Vazba**.</span><span class="sxs-lookup"><span data-stu-id="cc728-113">**Binding**.</span></span> <span data-ttu-id="cc728-114">Vazba Určuje, jak ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="cc728-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="cc728-115">Vazba Určuje, jak koncový bod komunikuje s na světě, včetně které přenosový protokol použít (například TCP nebo HTTP), které kódování určené k použití pro zprávy (například textu nebo binárních) a jsou nezbytné (pro které požadavky na zabezpečení například Secure Sockets Layer [SSL] nebo zabezpečení protokolu SOAP zprávy).</span><span class="sxs-lookup"><span data-stu-id="cc728-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="cc728-116">Další informace najdete v tématu [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cc728-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="cc728-117">**Kontrakt služby**.</span><span class="sxs-lookup"><span data-stu-id="cc728-117">**Service contract**.</span></span> <span data-ttu-id="cc728-118">Kontrakt služby popisuje, jaké funkce koncový bod vystavuje klienta.</span><span class="sxs-lookup"><span data-stu-id="cc728-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="cc728-119">Kontrakt určuje operace, které můžete volat klienta, formulář zprávy a typ vstupní parametry nebo data potřebná k volání operace a typ zpracování nebo zprávu odpovědi, které můžete očekávat klienta.</span><span class="sxs-lookup"><span data-stu-id="cc728-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="cc728-120">Tři základní typy kontraktů odpovídají základní zpráva exchange vzory (MEPs): datagram (jednocestné), požadavek nebo odpověď a duplexní režim (obousměrné).</span><span class="sxs-lookup"><span data-stu-id="cc728-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="cc728-121">Kontrakt služby můžete také použít kontraktů dat a zpráv tak, aby vyžadovala konkrétní datové typy a formáty zpráv, pokud přistupuje.</span><span class="sxs-lookup"><span data-stu-id="cc728-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="cc728-122">Další informace o tom, jak definování kontraktu služby najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cc728-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="cc728-123">Všimněte si, že klient může rovněž vyžaduje, aby implementace kontraktu služby definované, názvem kontraktu zpětného volání pro příjem zpráv z služby v rámci duplexní MEP.</span><span class="sxs-lookup"><span data-stu-id="cc728-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="cc728-124">Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="cc728-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="cc728-125">Koncový bod pro službu lze imperativní pomocí kódu nebo deklarativně pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cc728-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="cc728-126">Pokud nejsou zadány žádné koncové body modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každý kontrakt služby implementované službu.</span><span class="sxs-lookup"><span data-stu-id="cc728-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="cc728-127">Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě.</span><span class="sxs-lookup"><span data-stu-id="cc728-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="cc728-128">Obecně je praktičtější definovat koncové body služby pomocí konfigurace, nikoli kódu.</span><span class="sxs-lookup"><span data-stu-id="cc728-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="cc728-129">Zachování vazby a adresování informace mimo kód vám umožní se změnit bez nutnosti znovu zkompiluje a znovu nasaďte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cc728-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc728-130">Při přidávání koncový bod služby, který provádí zosobnění, je nutné použít jeden z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody nebo <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metoda správně načíst smlouvy do nové <xref:System.ServiceModel.Description.ServiceDescription> objektu.</span><span class="sxs-lookup"><span data-stu-id="cc728-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="cc728-131">Definování koncové body v kódu</span><span class="sxs-lookup"><span data-stu-id="cc728-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="cc728-132">Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícími službami:</span><span class="sxs-lookup"><span data-stu-id="cc728-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="cc728-133">Definování kontraktu pro `IEcho` typ služby, který přijímá název jiného uživatele a zpětné vazby pomocí odpověď "Hello \<name >!".</span><span class="sxs-lookup"><span data-stu-id="cc728-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="cc728-134">Implementace `Echo` služby typu definované `IEcho` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="cc728-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="cc728-135">Zadejte adresu koncového bodu z http://localhost:8000/Echo pro službu.</span><span class="sxs-lookup"><span data-stu-id="cc728-135">Specify an endpoint address of http://localhost:8000/Echo for the service.</span></span>  
  
-   <span data-ttu-id="cc728-136">Konfigurace `Echo` služby pomocí <xref:System.ServiceModel.WSHttpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="cc728-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
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
>  <span data-ttu-id="cc728-137">Hostitel služby se vytvoří základní adresu a potom je zbytek adresy, relativně k základní adresu, zadaný jako součást koncový bod.</span><span class="sxs-lookup"><span data-stu-id="cc728-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="cc728-138">Toto rozdělení do oddílů adresy umožňuje víc koncových bodů být snadněji definované pro služby na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="cc728-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc728-139">Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> ve službě aplikace nesmí být upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodu <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="cc728-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="cc728-140">Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost a `AddServiceEndpoint` metody na <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, způsobí výjimku, pokud se změní za tento bod.</span><span class="sxs-lookup"><span data-stu-id="cc728-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="cc728-141">Ostatní umožňují je upravovat, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="cc728-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="cc728-142">Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> po zavolání nesmí měnit hodnoty <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="cc728-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="cc728-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud se změní za tento bod.</span><span class="sxs-lookup"><span data-stu-id="cc728-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="cc728-144">Ostatní hodnoty klienta popis můžete změnit bez chyby, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="cc728-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="cc728-145">Zda se služba nebo klienta, se doporučuje, když je upravit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc728-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="cc728-146">Definování koncové body v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="cc728-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="cc728-147">Při vytváření aplikace, budete chtít často odložení rozhodnutí týkající se na správce, který je nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc728-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="cc728-148">Například je často bude žádný způsob, jak zjistit předem jaké služby adres (URI).</span><span class="sxs-lookup"><span data-stu-id="cc728-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="cc728-149">Místo pevně kódováno adresu, je vhodnější umožňují správcům udělat po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="cc728-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="cc728-150">Tato možnost se provádí prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cc728-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="cc728-151">Podrobnosti najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="cc728-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc728-152">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config:` *filename*`[,`*filename* `]` přepnout na rychle vytvořte konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="cc728-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="cc728-153">Pomocí výchozí koncové body</span><span class="sxs-lookup"><span data-stu-id="cc728-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="cc728-154">Pokud nejsou zadány žádné koncové body, v kódu nebo v konfiguraci modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každý kontrakt služby implementované službu.</span><span class="sxs-lookup"><span data-stu-id="cc728-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="cc728-155">Základní adresa může být určený v kódu nebo v konfiguraci a jsou výchozí koncové body se přidají při <xref:System.ServiceModel.ICommunicationObject.Open> se volá na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cc728-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="cc728-156">V tomto příkladu je příkladě z předchozí části, ale vzhledem k tomu, že nejsou zadány žádné koncové body, se přidají jsou výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="cc728-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
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
  
 <span data-ttu-id="cc728-157">Pokud jsou k dispozici explicitně koncových bodů, jsou výchozí koncové body může být přidán voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc728-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="cc728-158">Další informace o výchozí koncové body najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cc728-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc728-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc728-159">See Also</span></span>  
 [<span data-ttu-id="cc728-160">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="cc728-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
