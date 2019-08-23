---
title: Přehled vytváření koncových bodů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 561839138baf448db881e3bd72777bda7b7c65bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941257"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="94f75-102">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="94f75-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="94f75-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím koncových *bodů* služby.</span><span class="sxs-lookup"><span data-stu-id="94f75-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="94f75-104">Koncové body poskytují klientům přístup k funkcím, které služba WCF nabízí.</span><span class="sxs-lookup"><span data-stu-id="94f75-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="94f75-105">Tato část popisuje strukturu koncového bodu a popisuje, jak definovat koncový bod v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="94f75-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="94f75-106">Struktura koncového bodu</span><span class="sxs-lookup"><span data-stu-id="94f75-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="94f75-107">Každý koncový bod obsahuje adresu, která indikuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem, a kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="94f75-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
- <span data-ttu-id="94f75-108">**Adresa**.</span><span class="sxs-lookup"><span data-stu-id="94f75-108">**Address**.</span></span> <span data-ttu-id="94f75-109">Adresa jednoznačně identifikuje koncový bod a oznamuje potenciálním příjemcům, kde se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="94f75-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="94f75-110">Je reprezentovaná v objektovém modelu <xref:System.ServiceModel.EndpointAddress> WCF adresou, která obsahuje identifikátor URI (Uniform Resource Identifier) a vlastnosti adresy, které obsahují identitu, některé prvky WSDL (Web Services Description Language) a kolekci volitelných záhlaví.</span><span class="sxs-lookup"><span data-stu-id="94f75-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="94f75-111">Volitelná záhlaví poskytují dodatečné podrobné informace o adresách, které umožňují identifikovat nebo komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="94f75-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="94f75-112">Další informace najdete v tématu [určení adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="94f75-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
- <span data-ttu-id="94f75-113">**Vazba**.</span><span class="sxs-lookup"><span data-stu-id="94f75-113">**Binding**.</span></span> <span data-ttu-id="94f75-114">Vazba určuje, jak komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="94f75-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="94f75-115">Tato vazba určuje, jak koncový bod komunikuje s celým světem, včetně přenosového protokolu, který se má použít (například TCP nebo HTTP), který kódování má být použito pro zprávy (například text nebo binární), a které požadavky na zabezpečení jsou nezbytné (pro Příklad: SSL (Secure Sockets Layer) [SSL] nebo zabezpečení zpráv SOAP).</span><span class="sxs-lookup"><span data-stu-id="94f75-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="94f75-116">Další informace najdete v tématu [použití vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="94f75-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
- <span data-ttu-id="94f75-117">**Kontrakt služby**.</span><span class="sxs-lookup"><span data-stu-id="94f75-117">**Service contract**.</span></span> <span data-ttu-id="94f75-118">Kontrakt služby popisuje, jaké funkce koncový bod zpřístupňuje klientovi.</span><span class="sxs-lookup"><span data-stu-id="94f75-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="94f75-119">Kontrakt Určuje operace, které může klient volat, formu zprávy a typ vstupních parametrů nebo data potřebná k volání operace a druh zprávy o zpracování nebo odpovědi, kterou může klient očekávat.</span><span class="sxs-lookup"><span data-stu-id="94f75-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="94f75-120">Tři základní typy smluv odpovídají základním vzorům výměny zpráv (MEPs): datagram (jednosměrný), Request/Reply a duplexní přenos (obousměrný).</span><span class="sxs-lookup"><span data-stu-id="94f75-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="94f75-121">Kontrakt služby může také využívat data a kontrakty zpráv, aby při přistupování vyžadoval konkrétní datové typy a formáty zpráv.</span><span class="sxs-lookup"><span data-stu-id="94f75-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="94f75-122">Další informace o tom, jak definovat kontrakt služby, najdete v tématu [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="94f75-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="94f75-123">Upozorňujeme, že klient může být taky nutný k implementaci kontraktu definovaného službou, kterému se říká kontrakt zpětného volání, aby přijímal zprávy ze služby v duplexní MEP.</span><span class="sxs-lookup"><span data-stu-id="94f75-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="94f75-124">Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="94f75-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="94f75-125">Koncový bod pro službu lze zadat buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="94f75-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="94f75-126">Pokud nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu pro každou základní adresu pro každý kontrakt služby implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="94f75-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="94f75-127">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="94f75-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="94f75-128">Obecně je praktické definovat koncové body služby pomocí konfigurace namísto kódu.</span><span class="sxs-lookup"><span data-stu-id="94f75-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="94f75-129">Zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace a opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="94f75-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94f75-130">Při přidávání koncového bodu služby, který provádí zosobnění, je nutné buď použít jednu z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod, <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> nebo metodu pro správné načtení kontraktu do nového <xref:System.ServiceModel.Description.ServiceDescription> objektu.</span><span class="sxs-lookup"><span data-stu-id="94f75-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="94f75-131">Definování koncových bodů v kódu</span><span class="sxs-lookup"><span data-stu-id="94f75-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="94f75-132">Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícím:</span><span class="sxs-lookup"><span data-stu-id="94f75-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
- <span data-ttu-id="94f75-133">Definujte kontrakt pro `IEcho` typ služby, který přijímá jméno a odezvu osoby s odpovědí "Hello \<>!".</span><span class="sxs-lookup"><span data-stu-id="94f75-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
- <span data-ttu-id="94f75-134">`IEcho` Implementujte `Echo` službu typu definovaného smlouvou.</span><span class="sxs-lookup"><span data-stu-id="94f75-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
- <span data-ttu-id="94f75-135">Zadejte adresu `http://localhost:8000/Echo` koncového bodu pro službu.</span><span class="sxs-lookup"><span data-stu-id="94f75-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>  
  
- <span data-ttu-id="94f75-136">`Echo` Nakonfigurujte službu<xref:System.ServiceModel.WSHttpBinding> pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="94f75-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
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
> <span data-ttu-id="94f75-137">Hostitel služby se vytvoří se základní adresou a potom zbytek adresy, která je relativní vzhledem k základní adrese, je zadána jako součást koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="94f75-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="94f75-138">Tento oddíl adresy umožňuje lépe definovat více koncových bodů pro služby na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="94f75-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94f75-139">Vlastnosti v aplikaci služby se nesmí upravovat <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> po metodě na <xref:System.ServiceModel.ServiceHostBase>. <xref:System.ServiceModel.Description.ServiceDescription></span><span class="sxs-lookup"><span data-stu-id="94f75-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="94f75-140">Někteří členové <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> , jako je například vlastnost `AddServiceEndpoint` a metody <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost>, vyvolají výjimku, pokud byla změněna za daný bod.</span><span class="sxs-lookup"><span data-stu-id="94f75-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="94f75-141">Jiné vám umožní je upravovat, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="94f75-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="94f75-142">Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> hodnoty nesmí být upraveny po volání metody do. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ChannelFactory></span><span class="sxs-lookup"><span data-stu-id="94f75-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="94f75-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud byla změněna za tento bod.</span><span class="sxs-lookup"><span data-stu-id="94f75-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="94f75-144">Ostatní hodnoty popisů klienta lze upravovat bez chyb, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="94f75-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="94f75-145">Bez ohledu na to, jestli pro službu nebo klienta, se doporučuje změnit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="94f75-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="94f75-146">Definování koncových bodů v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="94f75-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="94f75-147">Při vytváření aplikace často chcete odložit rozhodnutí správci, který aplikaci nasazuje.</span><span class="sxs-lookup"><span data-stu-id="94f75-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="94f75-148">Například neexistuje žádný způsob, jak si předem zjistit, co bude adresa služby (identifikátor URI).</span><span class="sxs-lookup"><span data-stu-id="94f75-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="94f75-149">Místo hardwarového zakódování adresy je vhodnější dát správcům po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="94f75-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="94f75-150">Tato flexibilita je zajištěna prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="94f75-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="94f75-151">Podrobnosti najdete v tématu [Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="94f75-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94f75-152">K rychlému vytvoření konfiguračních souborů použijte nástroj pro tvorbu [metadat (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config:`parametrem *filename*`[,`*filename* `]` .</span><span class="sxs-lookup"><span data-stu-id="94f75-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="94f75-153">Používání výchozích koncových bodů</span><span class="sxs-lookup"><span data-stu-id="94f75-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="94f75-154">Pokud v kódu nebo v konfiguraci nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu pro každou základní adresu pro každý kontrakt služby implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="94f75-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="94f75-155">Základní adresu lze zadat v kódu nebo v konfiguraci a výchozí koncové body jsou přidány při <xref:System.ServiceModel.ICommunicationObject.Open> volání <xref:System.ServiceModel.ServiceHost>na.</span><span class="sxs-lookup"><span data-stu-id="94f75-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="94f75-156">Tento příklad je stejný jako v předchozí části, ale vzhledem k tomu, že nejsou zadány žádné koncové body, jsou přidány výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="94f75-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
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
  
 <span data-ttu-id="94f75-157">Pokud jsou koncové body explicitně poskytnuty, lze výchozí koncové body přidat voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="94f75-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="94f75-158">Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="94f75-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f75-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94f75-159">See also</span></span>

- [<span data-ttu-id="94f75-160">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="94f75-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
