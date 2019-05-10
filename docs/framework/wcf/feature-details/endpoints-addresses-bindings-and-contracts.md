---
title: 'Koncové body: adresy, vazby a kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3d345cfa3169e22e7c5e85cd1c7d11c2feef4f5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665964"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="3a3fc-102">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="3a3fc-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="3a3fc-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) nastane prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="3a3fc-104">Koncové body poskytují klientům přístup k funkcím, které nabízí služba WCF.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="3a3fc-105">Každý koncový bod se skládá ze čtyř vlastností:</span><span class="sxs-lookup"><span data-stu-id="3a3fc-105">Each endpoint consists of four properties:</span></span>  
  
- <span data-ttu-id="3a3fc-106">Adresa, která určuje, kde můžete najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-106">An address that indicates where the endpoint can be found.</span></span>  
  
- <span data-ttu-id="3a3fc-107">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="3a3fc-108">Smlouvy, které jsou uvedeny operace, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-108">A contract that identifies the operations available.</span></span>  
  
- <span data-ttu-id="3a3fc-109">Sada chování, které určují místní implementace podrobnosti koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="3a3fc-110">Toto téma popisuje strukturu tohoto koncového bodu a vysvětluje, jak je reprezentován v objektovém modelu WCF.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="3a3fc-111">Struktura koncový bod</span><span class="sxs-lookup"><span data-stu-id="3a3fc-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="3a3fc-112">Každý koncový bod se skládá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3a3fc-112">Each endpoint consists of the following:</span></span>  
  
- <span data-ttu-id="3a3fc-113">Adresa: Adresa jednoznačně identifikuje koncový bod a říká potenciál příjemce služby, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="3a3fc-114">Je zastoupena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> třídy.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="3a3fc-115"><xref:System.ServiceModel.EndpointAddress> Třída obsahuje:</span><span class="sxs-lookup"><span data-stu-id="3a3fc-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    - <span data-ttu-id="3a3fc-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnost, která představuje adresu služby.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    - <span data-ttu-id="3a3fc-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnost, která představuje zabezpečení identity služby a kolekce hlaviček volitelnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="3a3fc-118">Záhlaví volitelnou zprávu se používají k zajištění další a další podrobné informace o adresách k identifikaci a k interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="3a3fc-119">Další informace najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
- <span data-ttu-id="3a3fc-120">Vazby: Vazba Určuje, jak se ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="3a3fc-121">Sem patří:</span><span class="sxs-lookup"><span data-stu-id="3a3fc-121">This includes:</span></span>  
  
    - <span data-ttu-id="3a3fc-122">Protokol přenos, který se má použít (například protokol TCP nebo HTTP).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    - <span data-ttu-id="3a3fc-123">Kódování pro zprávy (například text nebo binární).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    - <span data-ttu-id="3a3fc-124">Nezbytné požadavky na zabezpečení (například protokol SSL nebo SOAP zabezpečení zpráv).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="3a3fc-125">Další informace najdete v tématu [vazby WCF – přehled](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="3a3fc-126">Vazbu v objektovém modelu WCF reprezentována abstraktní základní třída <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="3a3fc-127">Pro většinu scénářů uživatelé mohou používat jednu z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="3a3fc-128">Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
- <span data-ttu-id="3a3fc-129">Kontrakty: Kontrakt popisuje, jaké funkce zpřístupňuje koncový bod do klienta.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="3a3fc-130">Určuje kontrakt:</span><span class="sxs-lookup"><span data-stu-id="3a3fc-130">A contract specifies:</span></span>  
  
    - <span data-ttu-id="3a3fc-131">Jaké operace lze volat pro klienta.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-131">What operations can be called by a client.</span></span>  
  
    - <span data-ttu-id="3a3fc-132">Formulář zprávy.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-132">The form of the message.</span></span>  
  
    - <span data-ttu-id="3a3fc-133">Typ vstupních parametrů nebo data potřebná pro volání operace.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-133">The type of input parameters or data required to call the operation.</span></span>  
  
    - <span data-ttu-id="3a3fc-134">Jaký typ odpověď nebo zpracování zpráv klienta můžete očekávat.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="3a3fc-135">Další informace o definování kontraktu, naleznete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
- <span data-ttu-id="3a3fc-136">Chování: Chování koncového bodu můžete použít k úpravě místní chování koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="3a3fc-137">Chování koncového bodu dosáhnout účastí průběhu sestavování WCFruntime.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="3a3fc-138">Příklad chování koncového bodu je <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnost, která vám umožní určit jinou adresu naslouchání, než adresu SOAP nebo webové služby WSDL (Description Language).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="3a3fc-139">Další informace najdete v tématu [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="3a3fc-140">Definování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="3a3fc-140">Defining Endpoints</span></span>  
 <span data-ttu-id="3a3fc-141">Můžete zadat koncový bod služby buď imperativně promocí kódu nebo deklarativně prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="3a3fc-142">Další informace najdete v tématu [jak: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) a [jak: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a3fc-143">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3a3fc-143">In This Section</span></span>  
 <span data-ttu-id="3a3fc-144">Tato část vysvětluje účel, adresy, vazby a koncové body ukazuje postup při konfiguraci vazby a koncový bod; a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="3a3fc-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="3a3fc-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="3a3fc-146">Popisuje, jak se řeší koncových bodů WCF.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="3a3fc-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="3a3fc-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="3a3fc-148">Popisuje, jak vazby se používají k určení přenosu, kódování a podrobnosti protokolu pro klienty a služby musí komunikovat mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="3a3fc-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="3a3fc-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="3a3fc-150">Popisuje, jak definovat metody služby smluv.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="3a3fc-151">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="3a3fc-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="3a3fc-152">Popisuje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="3a3fc-153">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="3a3fc-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="3a3fc-154">Popisuje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="3a3fc-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="3a3fc-155">Postupy: Pomocí Svcutil.exe k ověření zkompilovaného kódu služby</span><span class="sxs-lookup"><span data-stu-id="3a3fc-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="3a3fc-156">Popisuje, jak detekovat chyby v implementacemi služeb a konfigurace bez hostování pomocí služby [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3a3fc-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3fc-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a3fc-157">See also</span></span>

- [<span data-ttu-id="3a3fc-158">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="3a3fc-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="3a3fc-159">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3a3fc-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
