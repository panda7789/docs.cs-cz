---
title: 'Koncové body: adresy, vazby a kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 0909d1d10ab8932f27f7ca6cba6207d57fa4f4cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493745"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="b4bbf-102">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="b4bbf-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="b4bbf-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="b4bbf-104">Koncové body poskytují klientům přístup k funkce nabízené službou WCF.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="b4bbf-105">Každý koncový bod se skládá ze čtyř vlastností:</span><span class="sxs-lookup"><span data-stu-id="b4bbf-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="b4bbf-106">Adresa, která určuje, kde můžete najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="b4bbf-107">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="b4bbf-108">Kontrakt, který identifikuje operace, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="b4bbf-109">Sada chování, které určují místní implementace podrobnosti koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="b4bbf-110">Toto téma popisuje tuto strukturu koncový bod a vysvětluje, jak je reprezentována v objektový model WCF.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="b4bbf-111">Struktura koncový bod</span><span class="sxs-lookup"><span data-stu-id="b4bbf-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="b4bbf-112">Každý koncový bod se skládá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b4bbf-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="b4bbf-113">Adresa: Adresa jednoznačně identifikuje koncový bod a říká potenciální příjemcům služby, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="b4bbf-114">Je zobrazena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> třídy.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="b4bbf-115"><xref:System.ServiceModel.EndpointAddress> Třída obsahuje:</span><span class="sxs-lookup"><span data-stu-id="b4bbf-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="b4bbf-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnosti, která představuje adresu služby.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="b4bbf-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnosti, která představuje identitu zabezpečení služby a kolekci hlaviček volitelné zprávy.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="b4bbf-118">Záhlaví volitelné zpráv slouží k poskytnutí dalších a podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="b4bbf-119">Další informace najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="b4bbf-120">Vazba: Vazba Určuje, jak ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="b4bbf-121">Sem patří:</span><span class="sxs-lookup"><span data-stu-id="b4bbf-121">This includes:</span></span>  
  
    -   <span data-ttu-id="b4bbf-122">Přenosový protokol použít (například protokol TCP nebo HTTP).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="b4bbf-123">Kódování pro zprávy (například textu nebo binárních).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="b4bbf-124">Požadavky na nezbytné zabezpečení (například protokol SSL nebo SOAP zabezpečení zpráv).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="b4bbf-125">Další informace najdete v tématu [vazby WCF – přehled](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="b4bbf-126">Vazba je reprezentována v objektový model WCF abstraktní základní třída <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b4bbf-127">Pro většinu scénářů uživatelé mohou používat jednu z vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="b4bbf-128">Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="b4bbf-129">Kontrakty: Kontrakt popisuje, jaké funkce koncový bod vystavuje klienta.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="b4bbf-130">Kontrakt určuje:</span><span class="sxs-lookup"><span data-stu-id="b4bbf-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="b4bbf-131">Jaké operace lze volat klientem.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="b4bbf-132">Formulář zprávy.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="b4bbf-133">Typ vstupní parametry nebo data potřebná k operaci volat.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="b4bbf-134">Jaký typ zpracování nebo odpovědi zprávy klienta můžete očekávat.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="b4bbf-135">Další informace o definování kontraktu najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="b4bbf-136">Chování: Koncový bod chování můžete použít k přizpůsobení chování místní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="b4bbf-137">Koncový bod chování dosáhnout účastí procesu vytváření WCFruntime.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="b4bbf-138">Je například chování koncového bodu <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnosti, která umožňuje zadat adresu odlišnou naslouchání adresu protokolu SOAP nebo webové služby popis Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="b4bbf-139">Další informace najdete v tématu [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="b4bbf-140">Definování koncové body</span><span class="sxs-lookup"><span data-stu-id="b4bbf-140">Defining Endpoints</span></span>  
 <span data-ttu-id="b4bbf-141">Zadaný koncový bod služby buď imperativní pomocí kódu nebo deklarativně pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="b4bbf-142">Další informace najdete v tématu [postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) a [postupy: vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4bbf-143">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b4bbf-143">In This Section</span></span>  
 <span data-ttu-id="b4bbf-144">Tato část popisuje účel vazby, koncových bodů a adresy; ukazuje, jak nakonfigurovat vazbu a koncový bod; a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="b4bbf-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="b4bbf-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="b4bbf-146">Popisuje, jak popisuje koncových bodů WCF.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="b4bbf-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="b4bbf-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="b4bbf-148">Popisuje, jak vazby slouží k zadání přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="b4bbf-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="b4bbf-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="b4bbf-150">Popisuje, jak definovat kontrakty metody služby.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="b4bbf-151">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="b4bbf-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="b4bbf-152">Popisuje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="b4bbf-153">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="b4bbf-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="b4bbf-154">Popisuje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="b4bbf-155">Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="b4bbf-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="b4bbf-156">Popisuje, jak detekovat chyby v implementace služby a konfigurace bez hostování služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4bbf-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4bbf-157">See Also</span></span>  
 [<span data-ttu-id="b4bbf-158">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="b4bbf-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="b4bbf-159">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b4bbf-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
