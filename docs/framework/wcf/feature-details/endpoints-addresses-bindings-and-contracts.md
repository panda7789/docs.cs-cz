---
title: "Koncové body: adresy, vazby a kontrakty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af82cb934570b371d332c0e08ebc9b2338d0c0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="6a2a4-102">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="6a2a4-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="6a2a4-103">Veškerá komunikace s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="6a2a4-104">Koncové body poskytují klientům přístup k funkce nabízené sítěmi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="6a2a4-105">Každý koncový bod se skládá ze čtyř vlastností:</span><span class="sxs-lookup"><span data-stu-id="6a2a4-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="6a2a4-106">Adresa, která určuje, kde můžete najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="6a2a4-107">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="6a2a4-108">Kontrakt, který identifikuje operace, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="6a2a4-109">Sada chování, které určují místní implementace podrobnosti koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="6a2a4-110">Toto téma popisuje tuto strukturu koncový bod a vysvětluje, jak je reprezentována v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="6a2a4-111">Struktura koncový bod</span><span class="sxs-lookup"><span data-stu-id="6a2a4-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="6a2a4-112">Každý koncový bod se skládá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="6a2a4-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="6a2a4-113">Adresa: Adresa jednoznačně identifikuje koncový bod a říká potenciální příjemcům služby, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="6a2a4-114">Je zobrazena v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model pomocí <xref:System.ServiceModel.EndpointAddress> třídy.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="6a2a4-115"><xref:System.ServiceModel.EndpointAddress> Třída obsahuje:</span><span class="sxs-lookup"><span data-stu-id="6a2a4-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="6a2a4-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnosti, která představuje adresu služby.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="6a2a4-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnosti, která představuje identitu zabezpečení služby a kolekci hlaviček volitelné zprávy.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="6a2a4-118">Záhlaví volitelné zpráv slouží k poskytnutí dalších a podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6a2a4-119">[Zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="6a2a4-120">Vazba: Vazba Určuje, jak ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="6a2a4-121">Sem patří:</span><span class="sxs-lookup"><span data-stu-id="6a2a4-121">This includes:</span></span>  
  
    -   <span data-ttu-id="6a2a4-122">Přenosový protokol použít (například protokol TCP nebo HTTP).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="6a2a4-123">Kódování pro zprávy (například textu nebo binárních).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="6a2a4-124">Požadavky na nezbytné zabezpečení (například protokol SSL nebo SOAP zabezpečení zpráv).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6a2a4-125">[Vazby WCF – přehled](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="6a2a4-126">Vazba je znázorněná [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model abstraktní základní třída <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="6a2a4-127">Pro většinu scénářů uživatelé mohou používat jednu z vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="6a2a4-128">Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="6a2a4-129">Kontrakty: Kontrakt popisuje, jaké funkce koncový bod vystavuje klienta.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="6a2a4-130">Kontrakt určuje:</span><span class="sxs-lookup"><span data-stu-id="6a2a4-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="6a2a4-131">Jaké operace lze volat klientem.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="6a2a4-132">Formulář zprávy.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="6a2a4-133">Typ vstupní parametry nebo data potřebná k operaci volat.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="6a2a4-134">Jaký typ zpracování nebo odpovědi zprávy klienta můžete očekávat.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="6a2a4-135">Další informace o definování kontraktu najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="6a2a4-136">Chování: Koncový bod chování můžete použít k přizpůsobení chování místní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="6a2a4-137">Koncový bod chování dosáhnout účastí procesu vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="6a2a4-138">Je například chování koncového bodu <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnosti, která umožňuje zadat adresu odlišnou naslouchání adresu protokolu SOAP nebo webové služby popis Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6a2a4-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="6a2a4-140">Definování koncové body</span><span class="sxs-lookup"><span data-stu-id="6a2a4-140">Defining Endpoints</span></span>  
 <span data-ttu-id="6a2a4-141">Zadaný koncový bod služby buď imperativní pomocí kódu nebo deklarativně pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6a2a4-142">[Postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) a [postupy: vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a2a4-143">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6a2a4-143">In This Section</span></span>  
 <span data-ttu-id="6a2a4-144">Tato část popisuje účel vazby, koncových bodů a adresy; ukazuje, jak nakonfigurovat vazbu a koncový bod; a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="6a2a4-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="6a2a4-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="6a2a4-146">Popisuje, jak jsou řešeny koncové body v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a2a4-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="6a2a4-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="6a2a4-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="6a2a4-148">Popisuje, jak vazby slouží k zadání přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="6a2a4-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="6a2a4-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="6a2a4-150">Popisuje, jak definovat kontrakty metody služby.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="6a2a4-151">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="6a2a4-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="6a2a4-152">Popisuje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="6a2a4-153">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="6a2a4-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="6a2a4-154">Popisuje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="6a2a4-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="6a2a4-155">Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="6a2a4-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="6a2a4-156">Popisuje, jak detekovat chyby v implementace služby a konfigurace bez hostování služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6a2a4-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2a4-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a2a4-157">See Also</span></span>  
 [<span data-ttu-id="6a2a4-158">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="6a2a4-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="6a2a4-159">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="6a2a4-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
