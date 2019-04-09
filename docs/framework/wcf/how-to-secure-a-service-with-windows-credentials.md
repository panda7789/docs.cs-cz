---
title: 'Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 70b8e2f28559d5fc54736db1319d2309aa5b86a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111329"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="ca32e-102">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="ca32e-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="ca32e-103">Toto téma ukazuje, jak povolit zabezpečení přenosu pro službu Windows Communication Foundation (WCF), která se nachází v doméně Windows a je volán klienty ve stejné doméně.</span><span class="sxs-lookup"><span data-stu-id="ca32e-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="ca32e-104">Další informace o tomto scénáři najdete v tématu [zabezpečení přenosu pomocí ověřování Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="ca32e-105">Ukázková aplikace, najdete v článku [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="ca32e-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="ca32e-106">Toto téma předpokládá máte existující rozhraní kontrakt a implementaci již definována a přidává ke, který.</span><span class="sxs-lookup"><span data-stu-id="ca32e-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="ca32e-107">Můžete také upravit existující služby a služby klienta.</span><span class="sxs-lookup"><span data-stu-id="ca32e-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="ca32e-108">Můžete zabezpečení služby pomocí pověření Windows zcela v kódu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="ca32e-109">Alternativně můžete vynechat kód pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ca32e-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="ca32e-110">Toto téma ukazuje oba způsoby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-110">This topic shows both ways.</span></span> <span data-ttu-id="ca32e-111">Ujistěte se, že budete používat pouze jedním ze způsobů, ne obojí.</span><span class="sxs-lookup"><span data-stu-id="ca32e-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="ca32e-112">První tři postupy ukazují, jak zabezpečit pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="ca32e-113">Čtvrtý a pátý postup ukazuje, jak provést v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ca32e-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="ca32e-114">Pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="ca32e-114">Using Code</span></span>  
 <span data-ttu-id="ca32e-115">V části příklad na konci tohoto tématu je kompletní kód pro službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="ca32e-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="ca32e-116">První postup vás provede vytvořením a konfigurací <xref:System.ServiceModel.WSHttpBinding> třídu v kódu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="ca32e-117">Vazba používá přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ca32e-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="ca32e-118">Stejnou vazbu se používá na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="ca32e-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="ca32e-119">Chcete-li vytvořit WSHttpBinding, používající Windows přihlašovacích údajů a zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="ca32e-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="ca32e-120">Tento postup kód je vložen na začátek `Run` metodu `Test` třídy v kódu služby v oddíle Příklad.</span><span class="sxs-lookup"><span data-stu-id="ca32e-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="ca32e-121">Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="ca32e-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="ca32e-122">Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSHttpSecurity> třídu <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="ca32e-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="ca32e-123">Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp> třídu <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="ca32e-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="ca32e-124">Kód pro tento postup je následující:</span><span class="sxs-lookup"><span data-stu-id="ca32e-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="ca32e-125">Pomocí vazby ve službě</span><span class="sxs-lookup"><span data-stu-id="ca32e-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="ca32e-126">Toto je druhý postup ukazuje, jak tuto vazbu využíval v místním prostředí služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="ca32e-127">Další informace o hostování služeb najdete v části [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="ca32e-128">Chcete-li použít vazbu ve službě</span><span class="sxs-lookup"><span data-stu-id="ca32e-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="ca32e-129">Vložte tento postup kód za kód z předchozího postupu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="ca32e-130">Vytvoření <xref:System.Type> proměnnou s názvem `contractType` a přiřaďte ho typu rozhraní (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="ca32e-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="ca32e-131">Při použití jazyka Visual Basic, použijte `GetType` operátor; při použití jazyka C#, použijte `typeof` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ca32e-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="ca32e-132">Vytvořte druhý <xref:System.Type> proměnnou s názvem `serviceType` a přiřaďte ho typu implementovaného kontraktu (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="ca32e-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="ca32e-133">Vytvoření instance <xref:System.Uri> třídu s názvem `baseAddress` základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="ca32e-134">Základní adresa musí mít schéma, které odpovídá přenos.</span><span class="sxs-lookup"><span data-stu-id="ca32e-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="ca32e-135">V takovém případě je schéma přenosu HTTP a adresa obsahuje speciální identifikátor URI (Uniform Resource) "localhost" a port číslo (8036) a také adresu základního koncového bodu ("serviceModelSamples /): `http://localhost:8036/serviceModelSamples/`.</span><span class="sxs-lookup"><span data-stu-id="ca32e-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>  
  
5.  <span data-ttu-id="ca32e-136">Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy s `serviceType` a `baseAddress` proměnné.</span><span class="sxs-lookup"><span data-stu-id="ca32e-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="ca32e-137">Přidání koncového bodu služby pomocí `contractType`, vazby a název koncového bodu (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="ca32e-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="ca32e-138">Klient musí při zahájení volání služby zřetězit základní adresu a název koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="ca32e-139">Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="ca32e-140">Kód pro tento postup je znázorněna zde:</span><span class="sxs-lookup"><span data-stu-id="ca32e-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="ca32e-141">Pomocí vazby v klientovi</span><span class="sxs-lookup"><span data-stu-id="ca32e-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="ca32e-142">Tento postup ukazuje, jak generovat proxy server, který komunikuje se službou.</span><span class="sxs-lookup"><span data-stu-id="ca32e-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="ca32e-143">Generuje proxy server s použitím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření proxy serveru používá metadata služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="ca32e-144">Tento postup také vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy ke komunikaci se službou a pak zavolá služba.</span><span class="sxs-lookup"><span data-stu-id="ca32e-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="ca32e-145">Tento příklad používá pouze kód pro vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="ca32e-145">This example uses only code to create the client.</span></span> <span data-ttu-id="ca32e-146">Jako alternativu můžete použít konfigurační soubor, který se zobrazí v části tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="ca32e-147">Pro použití vazby v klientovi s kódem</span><span class="sxs-lookup"><span data-stu-id="ca32e-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="ca32e-148">Pomocí nástroje SvcUtil.exe generovat proxy kód z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="ca32e-149">Další informace najdete v tématu [jak: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="ca32e-150">Vygenerovaný proxy kód dědí z <xref:System.ServiceModel.ClientBase%601> třídu, která zajistí, že má každý klient nezbytné konstruktory, metody a vlastnosti komunikovat se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="ca32e-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="ca32e-151">V tomto příkladu obsahuje generovaného kódu `CalculatorClient` třídy, která implementuje `ICalculator` rozhraní, povolení kompatibility se kódu služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="ca32e-152">Tento postup kód je vložen na začátek `Main` metoda klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ca32e-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="ca32e-153">Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte jeho režim zabezpečení na `Message` a typ do přihlašovacích údajů klienta `Windows`.</span><span class="sxs-lookup"><span data-stu-id="ca32e-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="ca32e-154">Příklad názvy proměnné `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="ca32e-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="ca32e-155">Vytvoření instance <xref:System.ServiceModel.EndpointAddress> třídu s názvem `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="ca32e-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="ca32e-156">Inicializuje instanci se základní adresou zřetězená s název koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="ca32e-157">Vytvoření instance třídy generovaného klienta s `serviceAddress` a `clientBinding` proměnné.</span><span class="sxs-lookup"><span data-stu-id="ca32e-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="ca32e-158">Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> způsob, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="ca32e-159">Volání služby a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="ca32e-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="ca32e-160">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ca32e-160">Using the Configuration File</span></span>  
 <span data-ttu-id="ca32e-161">Místo vytváření vazby z kódu procedury, můžete použít následující kód pro části vazeb konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ca32e-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="ca32e-162">Pokud již nemáte službě definované, najdete v článku [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="ca32e-163">**Poznámka:** tento kód konfigurace se používá v konfiguračních souborech na služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="ca32e-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="ca32e-164">Povolit přenos zabezpečení ve službě service v doméně Windows pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="ca32e-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="ca32e-165">Přidat [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ca32e-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="ca32e-166">Přidat <`binding`> element <`WSHttpBinding`> elementu a nastavte `configurationName` atribut na hodnotu vhodné pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ca32e-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="ca32e-167">Přidat <`security`> element a nastavte `mode` atribut na zprávu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="ca32e-168">Přidat <`message`> element a nastavte `clientCredentialType` atribut pro Windows.</span><span class="sxs-lookup"><span data-stu-id="ca32e-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="ca32e-169">V konfiguračním souboru služby, nahraďte `<bindings>` oddíl s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="ca32e-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="ca32e-170">Pokud již nemáte konfigurační soubor služby, přečtěte si téma [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
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
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="ca32e-171">Pomocí vazby v klientovi</span><span class="sxs-lookup"><span data-stu-id="ca32e-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="ca32e-172">Tento postup ukazuje, jak vytvořit dva soubory: proxy server, který komunikuje s služby a konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="ca32e-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="ca32e-173">Také popisuje změny klientský program, který je třetí souboru použít na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="ca32e-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="ca32e-174">Pro použití vazby v klientovi s konfigurací</span><span class="sxs-lookup"><span data-stu-id="ca32e-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="ca32e-175">Pomocí nástroje SvcUtil.exe pro generování souboru kódu a konfigurace proxy serveru z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="ca32e-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="ca32e-176">Další informace najdete v tématu [jak: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="ca32e-177">Nahradit [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) část vygenerovaný konfigurační soubor s kódem konfigurace z předchozí části.</span><span class="sxs-lookup"><span data-stu-id="ca32e-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="ca32e-178">Vložení kódu procedury na začátku `Main` metoda klientský program.</span><span class="sxs-lookup"><span data-stu-id="ca32e-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="ca32e-179">Vytvoření instance třídy generovaného klienta předejte název vazby v konfiguračním souboru jako vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="ca32e-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="ca32e-180">Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> způsob, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ca32e-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="ca32e-181">Volání služby a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="ca32e-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="ca32e-182">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca32e-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="ca32e-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca32e-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="ca32e-184">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ca32e-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="ca32e-185">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="ca32e-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="ca32e-186">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="ca32e-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="ca32e-187">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ca32e-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
