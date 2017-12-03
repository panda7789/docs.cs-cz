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
ms.openlocfilehash: 6c0b13ee48ed729d89f4b4b506e3608abe7e82b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="554d7-102">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="554d7-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="554d7-103">Veškerá komunikace s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="554d7-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="554d7-104">Koncové body poskytují klientům přístup k funkce nabízené sítěmi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="554d7-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="554d7-105">Každý koncový bod se skládá ze čtyř vlastností:</span><span class="sxs-lookup"><span data-stu-id="554d7-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="554d7-106">Adresa, která určuje, kde můžete najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="554d7-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="554d7-107">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="554d7-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="554d7-108">Kontrakt, který identifikuje operace, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="554d7-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="554d7-109">Sada chování, které určují místní implementace podrobnosti koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="554d7-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="554d7-110">Toto téma popisuje tuto strukturu koncový bod a vysvětluje, jak je reprezentována v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="554d7-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="554d7-111">Struktura koncový bod</span><span class="sxs-lookup"><span data-stu-id="554d7-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="554d7-112">Každý koncový bod se skládá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="554d7-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="554d7-113">Adresa: Adresa jednoznačně identifikuje koncový bod a říká potenciální příjemcům služby, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="554d7-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="554d7-114">Je zobrazena v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model pomocí <xref:System.ServiceModel.EndpointAddress> třídy.</span><span class="sxs-lookup"><span data-stu-id="554d7-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="554d7-115"><xref:System.ServiceModel.EndpointAddress> Třída obsahuje:</span><span class="sxs-lookup"><span data-stu-id="554d7-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="554d7-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnosti, která představuje adresu služby.</span><span class="sxs-lookup"><span data-stu-id="554d7-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="554d7-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnosti, která představuje identitu zabezpečení služby a kolekci hlaviček volitelné zprávy.</span><span class="sxs-lookup"><span data-stu-id="554d7-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="554d7-118">Záhlaví volitelné zpráv slouží k poskytnutí dalších a podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="554d7-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="554d7-119">[Zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="554d7-120">Vazba: Vazba Určuje, jak ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="554d7-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="554d7-121">Sem patří:</span><span class="sxs-lookup"><span data-stu-id="554d7-121">This includes:</span></span>  
  
    -   <span data-ttu-id="554d7-122">Přenosový protokol použít (například protokol TCP nebo HTTP).</span><span class="sxs-lookup"><span data-stu-id="554d7-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="554d7-123">Kódování pro zprávy (například textu nebo binárních).</span><span class="sxs-lookup"><span data-stu-id="554d7-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="554d7-124">Požadavky na nezbytné zabezpečení (například protokol SSL nebo SOAP zabezpečení zpráv).</span><span class="sxs-lookup"><span data-stu-id="554d7-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="554d7-125">[Vazby WCF – přehled](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="554d7-126">Vazba je znázorněná [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model abstraktní základní třída <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="554d7-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="554d7-127">Pro většinu scénářů uživatelé mohou používat jednu z vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="554d7-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="554d7-128">Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="554d7-129">Kontrakty: Kontrakt popisuje, jaké funkce koncový bod vystavuje klienta.</span><span class="sxs-lookup"><span data-stu-id="554d7-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="554d7-130">Kontrakt určuje:</span><span class="sxs-lookup"><span data-stu-id="554d7-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="554d7-131">Jaké operace lze volat klientem.</span><span class="sxs-lookup"><span data-stu-id="554d7-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="554d7-132">Formulář zprávy.</span><span class="sxs-lookup"><span data-stu-id="554d7-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="554d7-133">Typ vstupní parametry nebo data potřebná k operaci volat.</span><span class="sxs-lookup"><span data-stu-id="554d7-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="554d7-134">Jaký typ zpracování nebo odpovědi zprávy klienta můžete očekávat.</span><span class="sxs-lookup"><span data-stu-id="554d7-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="554d7-135">Další informace o definování kontraktu najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="554d7-136">Chování: Koncový bod chování můžete použít k přizpůsobení chování místní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="554d7-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="554d7-137">Koncový bod chování dosáhnout účastí procesu vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="554d7-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="554d7-138">Je například chování koncového bodu <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnosti, která umožňuje zadat adresu odlišnou naslouchání adresu protokolu SOAP nebo webové služby popis Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="554d7-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="554d7-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="554d7-140">Definování koncové body</span><span class="sxs-lookup"><span data-stu-id="554d7-140">Defining Endpoints</span></span>  
 <span data-ttu-id="554d7-141">Zadaný koncový bod služby buď imperativní pomocí kódu nebo deklarativně pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="554d7-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="554d7-142">[Postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) a [postupy: vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="554d7-143">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="554d7-143">In This Section</span></span>  
 <span data-ttu-id="554d7-144">Tato část popisuje účel vazby, koncových bodů a adresy; ukazuje, jak nakonfigurovat vazbu a koncový bod; a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="554d7-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="554d7-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="554d7-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="554d7-146">Popisuje, jak jsou řešeny koncové body v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="554d7-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="554d7-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="554d7-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="554d7-148">Popisuje, jak vazby slouží k zadání přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="554d7-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="554d7-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="554d7-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="554d7-150">Popisuje, jak definovat kontrakty metody služby.</span><span class="sxs-lookup"><span data-stu-id="554d7-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="554d7-151">Postupy: vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="554d7-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="554d7-152">Popisuje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="554d7-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="554d7-153">Postupy: vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="554d7-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="554d7-154">Popisuje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="554d7-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="554d7-155">Postupy: použití Svcutil.exe pro ověření kompilovaného kódu služby</span><span class="sxs-lookup"><span data-stu-id="554d7-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="554d7-156">Popisuje, jak detekovat chyby v implementace služby a konfigurace bez hostování služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="554d7-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554d7-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="554d7-157">See Also</span></span>  
 [<span data-ttu-id="554d7-158">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="554d7-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="554d7-159">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="554d7-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
