---
title: "Postupy: zabezpečení služby pomocí pověření systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: "26"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 09e15fcb1f18a91961ee77a57dd8eed80f3faf6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="acd9d-102">Postupy: zabezpečení služby pomocí pověření systému Windows</span><span class="sxs-lookup"><span data-stu-id="acd9d-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="acd9d-103">Toto téma ukazuje, jak povolit zabezpečení přenosu na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služba, která se nachází v doméně systému Windows a je volána klienty ve stejné doméně.</span><span class="sxs-lookup"><span data-stu-id="acd9d-103">This topic shows how to enable transport security on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service that resides in a Windows domain and is called by clients in the same domain.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="acd9d-104">v tomto scénáři najdete v části [zabezpečení přenosu pomocí ověřování systému Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="acd9d-104"> this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="acd9d-105">Ukázkovou aplikaci, najdete v článku [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="acd9d-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="acd9d-106">Toto téma předpokládá máte existující rozhraní kontrakt a implementaci již definována a přidá na který.</span><span class="sxs-lookup"><span data-stu-id="acd9d-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="acd9d-107">Můžete také upravit existující službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="acd9d-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="acd9d-108">Můžete zabezpečit služba pomocí přihlašovacích údajů Windows zcela v kódu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="acd9d-109">Alternativně můžete vynechat některé kódu pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="acd9d-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="acd9d-110">Toto téma ukazuje obou směrech.</span><span class="sxs-lookup"><span data-stu-id="acd9d-110">This topic shows both ways.</span></span> <span data-ttu-id="acd9d-111">Ujistěte se, že byste používat jenom jedním ze způsobů, nikoli oba dva.</span><span class="sxs-lookup"><span data-stu-id="acd9d-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="acd9d-112">První tři postupy ukazují, jak zabezpečit pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="acd9d-113">Čtvrtý a pátý postup ukazuje, jak to udělat pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="acd9d-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="acd9d-114">Pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="acd9d-114">Using Code</span></span>  
 <span data-ttu-id="acd9d-115">Kompletní kód pro tuto službu a klienta je v části příkladu na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="acd9d-116">První postup provede procesem vytvoření a konfiguraci <xref:System.ServiceModel.WSHttpBinding> – třída v kódu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="acd9d-117">Vazba používá přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="acd9d-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="acd9d-118">Stejnou vazbu se používá na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="acd9d-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="acd9d-119">Chcete-li vytvořit WSHttpBinding, která používá přihlašovací údaje systému Windows a zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="acd9d-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="acd9d-120">Tento postup kód je vložen na začátku `Run` metodu `Test` – třída v kódu služby v části příklad.</span><span class="sxs-lookup"><span data-stu-id="acd9d-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="acd9d-121">Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="acd9d-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="acd9d-122">Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSHttpSecurity> třídy k <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="acd9d-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="acd9d-123">Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp> třídy k <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="acd9d-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="acd9d-124">Kód pro tento postup je následující:</span><span class="sxs-lookup"><span data-stu-id="acd9d-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="acd9d-125">Pomocí vazby ve službě</span><span class="sxs-lookup"><span data-stu-id="acd9d-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="acd9d-126">Toto je druhý postup, který ukazuje způsob použití vazby v služba s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="acd9d-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="acd9d-127">hostování služeb najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="acd9d-127"> hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="acd9d-128">Chcete-li použít vazbu ve službě</span><span class="sxs-lookup"><span data-stu-id="acd9d-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="acd9d-129">Vložení kódu tento postup po kód v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="acd9d-130">Vytvoření <xref:System.Type> proměnné s názvem `contractType` a přiřaďte ho typ rozhraní (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="acd9d-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="acd9d-131">Při použití [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], použijte `GetType` operátor; při použití jazyka C#, použijte `typeof` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="acd9d-131">When using [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="acd9d-132">Vytvořte druhý `Type` proměnné s názvem `serviceType` a přiřaďte ho typ implementovaná smlouvy (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="acd9d-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="acd9d-133">Vytvoření instance <xref:System.Uri> třídu s názvem `baseAddress` s základní adresa služby.</span><span class="sxs-lookup"><span data-stu-id="acd9d-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="acd9d-134">Základní adresa musí mít schématu, která odpovídá přenosu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="acd9d-135">V takovém případě je schéma přenosu HTTP a adresu obsahuje speciální identifikátor URI (Uniform Resource) "localhost" a port number (8036) a také adresu základní koncový bod ("serviceModelSamples /): http://localhost:8036/serviceModelSamples /.</span><span class="sxs-lookup"><span data-stu-id="acd9d-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): http://localhost:8036/serviceModelSamples/.</span></span>  
  
5.  <span data-ttu-id="acd9d-136">Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy s `serviceType` a `baseAddress` proměnné.</span><span class="sxs-lookup"><span data-stu-id="acd9d-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="acd9d-137">Přidání koncového bodu služby pomocí `contractType`, vazbu a název koncového bodu (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="acd9d-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="acd9d-138">Při inicializaci volání služby musí klient řetězení základní adresu a název koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="acd9d-139">Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="acd9d-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="acd9d-140">Kód pro tento postup je uveden zde:</span><span class="sxs-lookup"><span data-stu-id="acd9d-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="acd9d-141">Pomocí vazby v klientovi</span><span class="sxs-lookup"><span data-stu-id="acd9d-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="acd9d-142">Tento postup ukazuje, jak vygenerovat proxy server, který komunikuje se službou.</span><span class="sxs-lookup"><span data-stu-id="acd9d-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="acd9d-143">Proxy server je generována [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , který používá metadata služby pro vytvoření proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="acd9d-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="acd9d-144">Tento postup také vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy ke komunikaci se službou a potom zavolá službu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="acd9d-145">Tento příklad používá jenom kód pro vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="acd9d-145">This example uses only code to create the client.</span></span> <span data-ttu-id="acd9d-146">Jako alternativu můžete konfigurační soubor, který se zobrazí v části tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="acd9d-147">Chcete-li použít vazby v klientovi s kódem</span><span class="sxs-lookup"><span data-stu-id="acd9d-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="acd9d-148">Použití nástroje SvcUtil.exe pro generování kódu proxy z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="acd9d-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="acd9d-149">[Postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="acd9d-149"> [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="acd9d-150">Vygenerovaný proxy server kód dědí z <xref:System.ServiceModel.ClientBase%601> třídy, která zajistí, že má každý klient nezbytné konstruktory, metod a vlastností ke komunikaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="acd9d-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="acd9d-151">V tomto příkladu obsahuje generovaný kód `CalculatorClient` třídy, které implementuje `ICalculator` rozhraní, povolení kompatibilitu s kódu služby.</span><span class="sxs-lookup"><span data-stu-id="acd9d-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="acd9d-152">Tento postup kód je vložen na začátku `Main` metoda programu klienta.</span><span class="sxs-lookup"><span data-stu-id="acd9d-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="acd9d-153">Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte režim zabezpečení na `Message` a svého klienta na typ přihlašovacích údajů `Windows`.</span><span class="sxs-lookup"><span data-stu-id="acd9d-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="acd9d-154">V příkladu názvy proměnnou `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="acd9d-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="acd9d-155">Vytvoření instance <xref:System.ServiceModel.EndpointAddress> třídu s názvem `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="acd9d-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="acd9d-156">Inicializaci instance s základní adresu zřetězen s název koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="acd9d-157">Vytvoření instance třídy generovaného klienta s `serviceAddress` a `clientBinding` proměnné.</span><span class="sxs-lookup"><span data-stu-id="acd9d-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="acd9d-158">Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> metoda, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="acd9d-159">Zavolá službu a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="acd9d-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="acd9d-160">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="acd9d-160">Using the Configuration File</span></span>  
 <span data-ttu-id="acd9d-161">Místo vytvoření vazby s procedurální kódu, můžete použít následující kód ukazuje pro vazby oddíl konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="acd9d-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="acd9d-162">Pokud již službu definované nemáte, přečtěte si téma [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="acd9d-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="acd9d-163">**Poznámka:** tento kód konfigurace se používá v konfiguračních souborech na služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="acd9d-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="acd9d-164">Povolení služby v doméně systému Windows pomocí konfigurace zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="acd9d-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="acd9d-165">Přidat [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu, který chcete [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) části element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="acd9d-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="acd9d-166">Přidat <`binding`> elementu, který chcete <`WSHttpBinding`> elementu a sadu `configurationName` vhodné pro vaše aplikace hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="acd9d-167">Přidat <`security`> elementu a sadu `mode` atribut zprávy.</span><span class="sxs-lookup"><span data-stu-id="acd9d-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="acd9d-168">Přidat <`message`> elementu a sadu `clientCredentialType` atribut systému Windows.</span><span class="sxs-lookup"><span data-stu-id="acd9d-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="acd9d-169">V konfiguračním souboru služby, nahraďte `<bindings>` oddíl následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="acd9d-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="acd9d-170">Pokud již nemáte konfigurační soubor služby, přečtěte si téma [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="acd9d-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="acd9d-171">Pomocí vazby v klientovi</span><span class="sxs-lookup"><span data-stu-id="acd9d-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="acd9d-172">Tento postup ukazuje, jak vygenerovat dva soubory: proxy server, který komunikuje s službu a konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="acd9d-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="acd9d-173">Také popisuje změny v programu klienta, což je třetí soubor používá na klientovi.</span><span class="sxs-lookup"><span data-stu-id="acd9d-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="acd9d-174">Chcete-li použít vazby v klientovi s konfigurací</span><span class="sxs-lookup"><span data-stu-id="acd9d-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="acd9d-175">Pomocí nástroje SvcUtil.exe vygenerujte soubor kódu a konfigurace proxy serveru z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="acd9d-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="acd9d-176">[Postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="acd9d-176"> [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="acd9d-177">Nahraďte [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) části generovaného konfiguračního souboru s kódem konfigurace z předchozí části.</span><span class="sxs-lookup"><span data-stu-id="acd9d-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="acd9d-178">Na začátku je vložen procedurální kód `Main` metoda programu klienta.</span><span class="sxs-lookup"><span data-stu-id="acd9d-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="acd9d-179">Vytvoření instance třídy generovaného klienta předání názvu vazby v konfiguračním souboru jako vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="acd9d-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="acd9d-180">Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> metoda, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="acd9d-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="acd9d-181">Zavolá službu a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="acd9d-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="acd9d-182">Příklad</span><span class="sxs-lookup"><span data-stu-id="acd9d-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="acd9d-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="acd9d-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="acd9d-184">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="acd9d-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="acd9d-185">Postupy: vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="acd9d-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="acd9d-186">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="acd9d-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="acd9d-187">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="acd9d-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
