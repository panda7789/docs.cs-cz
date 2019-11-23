---
title: Přehled vytváření koncových bodů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: bf6bfb10123223bf689945ef93ff09219a68092c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319930"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="8c165-102">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="8c165-102">Endpoint Creation Overview</span></span>

<span data-ttu-id="8c165-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím *koncových bodů* služby.</span><span class="sxs-lookup"><span data-stu-id="8c165-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="8c165-104">Koncové body poskytují klientům přístup k funkcím, které služba WCF nabízí.</span><span class="sxs-lookup"><span data-stu-id="8c165-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="8c165-105">Tato část popisuje strukturu koncového bodu a popisuje, jak definovat koncový bod v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="8c165-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="8c165-106">Struktura koncového bodu</span><span class="sxs-lookup"><span data-stu-id="8c165-106">The Structure of an Endpoint</span></span>

<span data-ttu-id="8c165-107">Každý koncový bod obsahuje adresu, která indikuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem, a kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="8c165-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="8c165-108">**Adresa**.</span><span class="sxs-lookup"><span data-stu-id="8c165-108">**Address**.</span></span> <span data-ttu-id="8c165-109">Adresa jednoznačně identifikuje koncový bod a oznamuje potenciálním příjemcům, kde se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="8c165-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="8c165-110">Je reprezentovaná v objektovém modelu WCF pomocí <xref:System.ServiceModel.EndpointAddress> adresy, která obsahuje identifikátor URI (Uniform Resource Identifier) a vlastnosti adresy, které obsahují identitu, některé prvky WSDL (Web Services Description Language) a kolekci volitelných hlaviček.</span><span class="sxs-lookup"><span data-stu-id="8c165-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="8c165-111">Volitelná záhlaví poskytují dodatečné podrobné informace o adresách, které umožňují identifikovat nebo komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="8c165-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="8c165-112">Další informace najdete v tématu [určení adresy koncového bodu](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="8c165-112">For more information, see [Specifying an Endpoint Address](specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="8c165-113">**Vazba**.</span><span class="sxs-lookup"><span data-stu-id="8c165-113">**Binding**.</span></span> <span data-ttu-id="8c165-114">Vazba určuje, jak komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="8c165-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="8c165-115">Tato vazba určuje, jak koncový bod komunikuje s celým světem, včetně přenosového protokolu, který se má použít (například TCP nebo HTTP), který kódování má být použito pro zprávy (například text nebo binární), a které požadavky na zabezpečení jsou nezbytné (pro Příklad: SSL (Secure Sockets Layer) [SSL] nebo zabezpečení zpráv SOAP).</span><span class="sxs-lookup"><span data-stu-id="8c165-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="8c165-116">Další informace najdete v tématu [použití vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8c165-116">For more information, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="8c165-117">**Kontrakt služby**.</span><span class="sxs-lookup"><span data-stu-id="8c165-117">**Service contract**.</span></span> <span data-ttu-id="8c165-118">Kontrakt služby popisuje, jaké funkce koncový bod zpřístupňuje klientovi.</span><span class="sxs-lookup"><span data-stu-id="8c165-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="8c165-119">Kontrakt Určuje operace, které může klient volat, formu zprávy a typ vstupních parametrů nebo data potřebná k volání operace a druh zprávy o zpracování nebo odpovědi, kterou může klient očekávat.</span><span class="sxs-lookup"><span data-stu-id="8c165-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="8c165-120">Tři základní typy smluv odpovídají základním vzorům výměny zpráv (MEPs): datagram (jednosměrný), Request/Reply a duplexní přenos (obousměrný).</span><span class="sxs-lookup"><span data-stu-id="8c165-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="8c165-121">Kontrakt služby může také využívat data a kontrakty zpráv, aby při přistupování vyžadoval konkrétní datové typy a formáty zpráv.</span><span class="sxs-lookup"><span data-stu-id="8c165-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="8c165-122">Další informace o tom, jak definovat kontrakt služby, najdete v tématu [Navrhování kontraktů služby](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8c165-122">For more information about how to define a service contract, see [Designing Service Contracts](designing-service-contracts.md).</span></span> <span data-ttu-id="8c165-123">Upozorňujeme, že klient může být taky nutný k implementaci kontraktu definovaného službou, kterému se říká kontrakt zpětného volání, aby přijímal zprávy ze služby v duplexní MEP.</span><span class="sxs-lookup"><span data-stu-id="8c165-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="8c165-124">Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="8c165-124">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>

<span data-ttu-id="8c165-125">Koncový bod pro službu lze zadat buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8c165-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="8c165-126">Pokud nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu pro každou základní adresu pro každý kontrakt služby implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="8c165-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="8c165-127">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="8c165-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="8c165-128">Obecně je praktické definovat koncové body služby pomocí konfigurace namísto kódu.</span><span class="sxs-lookup"><span data-stu-id="8c165-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="8c165-129">Zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace a opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c165-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8c165-130">Při přidávání koncového bodu služby, který provádí zosobnění, je nutné buď použít jednu z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod, nebo metodu <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> pro správné načtení kontraktu do nového objektu <xref:System.ServiceModel.Description.ServiceDescription>.</span><span class="sxs-lookup"><span data-stu-id="8c165-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="8c165-131">Definování koncových bodů v kódu</span><span class="sxs-lookup"><span data-stu-id="8c165-131">Defining Endpoints in Code</span></span>

<span data-ttu-id="8c165-132">Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícím:</span><span class="sxs-lookup"><span data-stu-id="8c165-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="8c165-133">Definujte kontrakt pro `IEcho` typ služby, který přijímá jméno a odpověď uživatele s odpovědí "Hello \<Name >!".</span><span class="sxs-lookup"><span data-stu-id="8c165-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="8c165-134">Implementujte službu `Echo` typu definovaného smlouvou `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="8c165-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="8c165-135">Zadejte adresu koncového bodu `http://localhost:8000/Echo` služby.</span><span class="sxs-lookup"><span data-stu-id="8c165-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="8c165-136">Nakonfigurujte službu `Echo` pomocí <xref:System.ServiceModel.WSHttpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="8c165-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
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
> <span data-ttu-id="8c165-137">Hostitel služby se vytvoří se základní adresou a potom zbytek adresy, která je relativní vzhledem k základní adrese, je zadána jako součást koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8c165-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="8c165-138">Tento oddíl adresy umožňuje lépe definovat více koncových bodů pro služby na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="8c165-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="8c165-139">Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> v aplikaci služby se nesmí upravovat za metodou <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="8c165-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="8c165-140">Někteří členové, jako je například vlastnost <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> a `AddServiceEndpoint` metody v <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, vyvolávají výjimku, pokud byla změněna za daný bod.</span><span class="sxs-lookup"><span data-stu-id="8c165-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="8c165-141">Jiné vám umožní je upravovat, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="8c165-141">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="8c165-142">Podobně na straně klienta nesmí být hodnoty <xref:System.ServiceModel.Description.ServiceEndpoint> po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>upravovat.</span><span class="sxs-lookup"><span data-stu-id="8c165-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="8c165-143">Vlastnost <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vyvolá výjimku, pokud byla změněna za chvíli.</span><span class="sxs-lookup"><span data-stu-id="8c165-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="8c165-144">Ostatní hodnoty popisů klienta lze upravovat bez chyb, ale výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="8c165-144">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="8c165-145">Bez ohledu na to, jestli pro službu nebo klienta, se doporučuje změnit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c165-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="8c165-146">Definování koncových bodů v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="8c165-146">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="8c165-147">Při vytváření aplikace často chcete odložit rozhodnutí správci, který aplikaci nasazuje.</span><span class="sxs-lookup"><span data-stu-id="8c165-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="8c165-148">Například neexistuje žádný způsob, jak si předem zjistit, co bude adresa služby (identifikátor URI).</span><span class="sxs-lookup"><span data-stu-id="8c165-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="8c165-149">Místo hardwarového zakódování adresy je vhodnější dát správcům po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="8c165-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="8c165-150">Tato flexibilita je zajištěna prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8c165-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="8c165-151">Podrobnosti najdete v tématu [Konfigurace služeb](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="8c165-151">For details, see [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8c165-152">K rychlému vytvoření konfiguračních souborů použijte nástroj pro tvorbu [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) s *názvem `/config:`filename*`[,`*filename*`]` přepínač.</span><span class="sxs-lookup"><span data-stu-id="8c165-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="8c165-153">Používání výchozích koncových bodů</span><span class="sxs-lookup"><span data-stu-id="8c165-153">Using Default Endpoints</span></span>

<span data-ttu-id="8c165-154">Pokud v kódu nebo v konfiguraci nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu pro každou základní adresu pro každý kontrakt služby implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="8c165-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="8c165-155">Základní adresu lze zadat v kódu nebo v konfiguraci a výchozí koncové body jsou přidány při volání <xref:System.ServiceModel.ICommunicationObject.Open> v <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8c165-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8c165-156">Tento příklad je stejný jako v předchozí části, ale vzhledem k tomu, že nejsou zadány žádné koncové body, jsou přidány výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="8c165-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
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

 <span data-ttu-id="8c165-157">Pokud jsou zadány koncové body explicitně, lze výchozí koncové body přidat voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c165-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="8c165-158">Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8c165-158">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c165-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c165-159">See also</span></span>

- [<span data-ttu-id="8c165-160">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="8c165-160">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
