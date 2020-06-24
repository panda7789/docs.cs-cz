---
title: 'Koncové body: adresy, vazby a kontrakty'
description: Zjistěte, jak veškerá komunikace se službou WCF probíhá prostřednictvím koncových bodů služby, které klientům poskytují přístup k funkcím, které služba nabízí.
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: ce0874bfed716716b6fd1801b35a4266095cd752
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247309"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="30a8b-103">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="30a8b-103">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="30a8b-104">Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím *koncových bodů* služby.</span><span class="sxs-lookup"><span data-stu-id="30a8b-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="30a8b-105">Koncové body poskytují klientům přístup k funkcím, které nabízí služba WCF.</span><span class="sxs-lookup"><span data-stu-id="30a8b-105">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="30a8b-106">Každý koncový bod se skládá ze čtyř vlastností:</span><span class="sxs-lookup"><span data-stu-id="30a8b-106">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="30a8b-107">Adresa, která indikuje, kde lze koncový bod najít.</span><span class="sxs-lookup"><span data-stu-id="30a8b-107">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="30a8b-108">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="30a8b-108">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="30a8b-109">Kontrakt, který identifikuje dostupné operace.</span><span class="sxs-lookup"><span data-stu-id="30a8b-109">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="30a8b-110">Sada chování, která určuje podrobnosti o místní implementaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="30a8b-110">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="30a8b-111">Toto téma popisuje tuto strukturu koncových bodů a vysvětluje, jak je znázorněno v objektovém modelu WCF.</span><span class="sxs-lookup"><span data-stu-id="30a8b-111">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="30a8b-112">Struktura koncového bodu</span><span class="sxs-lookup"><span data-stu-id="30a8b-112">The Structure of an Endpoint</span></span>

<span data-ttu-id="30a8b-113">Každý koncový bod se skládá z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="30a8b-113">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="30a8b-114">Adresa: Adresa jednoznačně identifikuje koncový bod a oznamuje potenciálním příjemcům služby, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="30a8b-114">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="30a8b-115">Je reprezentovaná v objektovém modelu WCF <xref:System.ServiceModel.EndpointAddress> třídou.</span><span class="sxs-lookup"><span data-stu-id="30a8b-115">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="30a8b-116"><xref:System.ServiceModel.EndpointAddress>Třída obsahuje:</span><span class="sxs-lookup"><span data-stu-id="30a8b-116">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="30a8b-117"><xref:System.ServiceModel.EndpointAddress.Uri%2A>Vlastnost, která představuje adresu služby.</span><span class="sxs-lookup"><span data-stu-id="30a8b-117">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="30a8b-118"><xref:System.ServiceModel.EndpointAddress.Identity%2A>Vlastnost, která představuje identitu zabezpečení služby a kolekci volitelných záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="30a8b-118">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="30a8b-119">Volitelná záhlaví zpráv slouží k poskytnutí dalších a podrobnějších informací o adresách k identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="30a8b-119">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="30a8b-120">Další informace najdete v tématu [určení adresy koncového bodu](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-120">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="30a8b-121">Binding: Vazba určuje, jak komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="30a8b-121">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="30a8b-122">To zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="30a8b-122">This includes:</span></span>

  - <span data-ttu-id="30a8b-123">Transportní protokol, který se má použít (například TCP nebo HTTP).</span><span class="sxs-lookup"><span data-stu-id="30a8b-123">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="30a8b-124">Kódování, které má být použito pro zprávy (například text nebo Binary).</span><span class="sxs-lookup"><span data-stu-id="30a8b-124">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="30a8b-125">Nezbytné požadavky na zabezpečení (například zabezpečení SSL nebo SOAP zprávy).</span><span class="sxs-lookup"><span data-stu-id="30a8b-125">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="30a8b-126">Další informace najdete v tématu [Přehled vazeb WCF](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-126">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="30a8b-127">Vazba je reprezentovaná v objektovém modelu WCF abstraktní základní třídou <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="30a8b-127">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="30a8b-128">Ve většině scénářů můžou uživatelé použít jednu z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="30a8b-128">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="30a8b-129">Další informace najdete v tématu o [vazbách poskytovaných systémem](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-129">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="30a8b-130">Smlouvy: kontrakt obsahuje popis funkcí, které koncový bod zpřístupňuje klientovi.</span><span class="sxs-lookup"><span data-stu-id="30a8b-130">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="30a8b-131">Kontrakt Určuje:</span><span class="sxs-lookup"><span data-stu-id="30a8b-131">A contract specifies:</span></span>

  - <span data-ttu-id="30a8b-132">Které operace může klient volat.</span><span class="sxs-lookup"><span data-stu-id="30a8b-132">What operations can be called by a client.</span></span>

  - <span data-ttu-id="30a8b-133">Forma zprávy</span><span class="sxs-lookup"><span data-stu-id="30a8b-133">The form of the message.</span></span>

  - <span data-ttu-id="30a8b-134">Typ vstupních parametrů nebo dat vyžadovaných pro volání operace.</span><span class="sxs-lookup"><span data-stu-id="30a8b-134">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="30a8b-135">Jaký typ zprávy pro zpracování nebo odpověď může klient očekávat.</span><span class="sxs-lookup"><span data-stu-id="30a8b-135">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="30a8b-136">Další informace o definování kontraktu najdete v tématu [Navrhování kontraktů služby](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-136">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="30a8b-137">Chování: k přizpůsobení místního chování koncového bodu služby můžete použít chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="30a8b-137">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="30a8b-138">Chování koncového bodu dosahuje tím, že se účastní procesu vytváření modulu runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="30a8b-138">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="30a8b-139">Příkladem chování koncového bodu je <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnost, která umožňuje zadat jinou naslouchající adresu než adresa SOAP nebo Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="30a8b-139">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="30a8b-140">Další informace najdete v tématu [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-140">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="30a8b-141">Definování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="30a8b-141">Defining Endpoints</span></span>

<span data-ttu-id="30a8b-142">Můžete určit koncový bod pro službu buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="30a8b-142">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="30a8b-143">Další informace najdete v tématech [Postupy: Vytvoření koncového bodu služby v konfiguraci](how-to-create-a-service-endpoint-in-configuration.md) a [Postupy: Vytvoření koncového bodu služby v kódu](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-143">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="30a8b-144">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="30a8b-144">In This Section</span></span>

<span data-ttu-id="30a8b-145">Tato část vysvětluje účel vazeb, koncových bodů a adres; ukazuje, jak nakonfigurovat vazbu a koncový bod. a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="30a8b-145">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="30a8b-146">[Adresa](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="30a8b-146">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="30a8b-147">Popisuje způsob adresování koncových bodů ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="30a8b-147">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="30a8b-148">[Vazeb](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="30a8b-148">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="30a8b-149">Popisuje způsob, jakým se používají vazby k určení přenosu, kódování a podrobností protokolu požadovaných pro komunikaci mezi klienty a službami.</span><span class="sxs-lookup"><span data-stu-id="30a8b-149">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="30a8b-150">[Financovan](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="30a8b-150">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="30a8b-151">Popisuje, jak kontrakty definují metody služby.</span><span class="sxs-lookup"><span data-stu-id="30a8b-151">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="30a8b-152">[Postupy: Vytvoření koncového bodu služby v konfiguraci](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="30a8b-152">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="30a8b-153">Popisuje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="30a8b-153">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="30a8b-154">[Postupy: Vytvoření koncového bodu služby v kódu](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="30a8b-154">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="30a8b-155">Popisuje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="30a8b-155">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="30a8b-156">[Postupy: použití Svcutil.exe k ověření zkompilovaného kódu služby](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="30a8b-156">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="30a8b-157">V této části najdete popis postupu při detekci chyb v implementacích a konfiguracích služby bez hostování služby pomocí [Nástroje pro nástroj pro metadata ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="30a8b-157">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30a8b-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="30a8b-158">See also</span></span>

- [<span data-ttu-id="30a8b-159">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="30a8b-159">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="30a8b-160">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="30a8b-160">Extending Bindings</span></span>](../extending/extending-bindings.md)
