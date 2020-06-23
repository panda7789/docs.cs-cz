---
title: 'Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows'
description: Naučte se, jak povolit zabezpečení přenosu ve službě WCF, která se nachází v doméně systému Windows a která je volána klienty ve stejné doméně.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244630"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="a5f2e-103">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="a5f2e-103">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="a5f2e-104">V tomto tématu se dozvíte, jak povolit zabezpečení přenosu ve službě Windows Communication Foundation (WCF), která se nachází v doméně systému Windows a která je volána klienty ve stejné doméně.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-104">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="a5f2e-105">Další informace o tomto scénáři najdete v tématu [zabezpečení přenosu s ověřováním systému Windows](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-105">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="a5f2e-106">Ukázkovou aplikaci najdete v ukázce [WSHttpBinding](./samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-106">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="a5f2e-107">Toto téma předpokládá, že máte již definované existující rozhraní kontraktu a implementaci, a přidá k tomu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-107">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="a5f2e-108">Můžete také upravit existující službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-108">You can also modify an existing service and client.</span></span>

<span data-ttu-id="a5f2e-109">Službu s přihlašovacími údaji systému Windows můžete zabezpečit kompletně v kódu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-109">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="a5f2e-110">Alternativně můžete vynechat část kódu pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-110">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="a5f2e-111">Toto téma ukazuje oba způsoby.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-111">This topic shows both ways.</span></span> <span data-ttu-id="a5f2e-112">Ujistěte se, že používáte pouze jeden ze způsobů, nikoli obojí.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-112">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="a5f2e-113">První tři postupy ukazují, jak službu zabezpečit pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-113">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="a5f2e-114">Čtvrtý a pátý postup ukazuje, jak to provést s konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-114">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="a5f2e-115">Použití kódu</span><span class="sxs-lookup"><span data-stu-id="a5f2e-115">Using Code</span></span>

<span data-ttu-id="a5f2e-116">Úplný kód pro službu a klienta se nachází v části příklad na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-116">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="a5f2e-117">První postup vás provede vytvořením a konfigurací <xref:System.ServiceModel.WSHttpBinding> třídy v kódu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-117">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="a5f2e-118">Vazba používá přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-118">The binding uses the HTTP transport.</span></span> <span data-ttu-id="a5f2e-119">Na straně klienta se používá stejná vazba.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-119">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="a5f2e-120">Vytvoření WSHttpBinding využívajícího přihlašovací údaje systému Windows a zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="a5f2e-120">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="a5f2e-121">Kód této procedury je vložen na začátek `Run` metody `Test` třídy v kódu služby v části příklad.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-121">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="a5f2e-122">Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-122">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="a5f2e-123">Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSHttpSecurity> třídy na <xref:System.ServiceModel.SecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-123">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="a5f2e-124">Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp> třídy na <xref:System.ServiceModel.MessageCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-124">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="a5f2e-125">Kód pro tento postup je následující:</span><span class="sxs-lookup"><span data-stu-id="a5f2e-125">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="a5f2e-126">Použití vazby ve službě</span><span class="sxs-lookup"><span data-stu-id="a5f2e-126">Using the Binding in a Service</span></span>

<span data-ttu-id="a5f2e-127">Toto je druhý postup, který ukazuje, jak použít vazbu v rámci samoobslužné služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-127">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="a5f2e-128">Další informace o hostitelských službách najdete v tématu [hostingové služby](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-128">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="a5f2e-129">Použití vazby ve službě</span><span class="sxs-lookup"><span data-stu-id="a5f2e-129">To use a binding in a service</span></span>

1. <span data-ttu-id="a5f2e-130">Vložte kód této procedury za kód z předchozího postupu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-130">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="a5f2e-131">Vytvořte <xref:System.Type> proměnnou s názvem `contractType` a přiřaďte ji typu rozhraní ( `ICalculator` ).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-131">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="a5f2e-132">Při použití Visual Basic použijte `GetType` operátor; při použití jazyka C# použijte `typeof` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-132">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="a5f2e-133">Vytvořte druhou <xref:System.Type> proměnnou s názvem `serviceType` a přiřaďte ji typu implementovaného kontraktu ( `Calculator` ).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-133">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="a5f2e-134">Vytvořte instanci <xref:System.Uri> třídy s názvem `baseAddress` se základní adresou služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-134">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="a5f2e-135">Základní adresa musí mít schéma, které odpovídá přenosu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-135">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="a5f2e-136">V tomto případě je přenosové schéma HTTP a adresa zahrnuje speciální identifikátor URI (Uniform Resource Identifier) "localhost" a číslo portu (8036) a také adresu základního koncového bodu (serviceModelSamples/): `http://localhost:8036/serviceModelSamples/` .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-136">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="a5f2e-137">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy s `serviceType` `baseAddress` proměnnými a.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-137">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="a5f2e-138">Přidejte koncový bod ke službě pomocí `contractType` , vazby a názvu koncového bodu (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-138">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="a5f2e-139">Klient musí při inicializaci volání služby zřetězit základní adresu a název koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-139">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="a5f2e-140">Zavolejte <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodu pro spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-140">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="a5f2e-141">Kód pro tento postup je zobrazen zde:</span><span class="sxs-lookup"><span data-stu-id="a5f2e-141">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="a5f2e-142">Použití vazby v klientovi</span><span class="sxs-lookup"><span data-stu-id="a5f2e-142">Using the Binding in a Client</span></span>

<span data-ttu-id="a5f2e-143">Tento postup ukazuje, jak vygenerovat proxy server, který komunikuje se službou.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-143">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="a5f2e-144">Proxy se generuje pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který používá metadata služby k vytvoření proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-144">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="a5f2e-145">Tento postup také vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy ke komunikaci se službou a poté zavolá službu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-145">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="a5f2e-146">Tento příklad používá pouze kód k vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-146">This example uses only code to create the client.</span></span> <span data-ttu-id="a5f2e-147">Alternativně můžete použít konfigurační soubor, který je uveden v části následující postup.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-147">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="a5f2e-148">Použití vazby v klientovi s kódem</span><span class="sxs-lookup"><span data-stu-id="a5f2e-148">To use a binding in a client with code</span></span>

1. <span data-ttu-id="a5f2e-149">K vygenerování kódu proxy z metadat služby použijte nástroj SvcUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-149">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="a5f2e-150">Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-150">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="a5f2e-151">Generovaný proxy kód dědí z <xref:System.ServiceModel.ClientBase%601> třídy, která zajišťuje, že každý klient má potřebné konstruktory, metody a vlastnosti ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-151">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="a5f2e-152">V tomto příkladu vygenerovaný kód obsahuje `CalculatorClient` třídu, která implementuje `ICalculator` rozhraní a povoluje kompatibilitu s kódem služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-152">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="a5f2e-153">Kód této procedury je vložen na začátek `Main` metody klientského programu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-153">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="a5f2e-154">Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na hodnotu `Message` a typ přihlašovacích údajů klienta na `Windows` .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-154">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="a5f2e-155">Příklad pojmenuje proměnnou `clientBinding` .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-155">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="a5f2e-156">Vytvořte instanci <xref:System.ServiceModel.EndpointAddress> třídy s názvem `serviceAddress` .</span><span class="sxs-lookup"><span data-stu-id="a5f2e-156">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="a5f2e-157">Inicializujte instanci se základní adresou zřetězenou s názvem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-157">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="a5f2e-158">Vytvořte instanci generované třídy klienta s `serviceAddress` `clientBinding` proměnnými a.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-158">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="a5f2e-159">Zavolejte <xref:System.ServiceModel.ClientBase%601.Open%2A> metodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-159">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="a5f2e-160">Zavolejte službu a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-160">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="a5f2e-161">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a5f2e-161">Using the Configuration File</span></span>

<span data-ttu-id="a5f2e-162">Místo vytvoření vazby pomocí procedurálního kódu můžete použít následující kód, který je zobrazen pro oddíl Bindings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-162">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="a5f2e-163">Pokud ještě nemáte definovanou službu, přečtěte si téma [navrhování a implementace služeb](designing-and-implementing-services.md)a [Konfigurace služeb](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-163">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a5f2e-164">Tento konfigurační kód se používá v konfiguračních souborech služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-164">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="a5f2e-165">Postup povolení přenosu zabezpečení ve službě v doméně systému Windows pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="a5f2e-165">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="a5f2e-166">Přidejte [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element do [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) oddílu element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-166">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="a5f2e-167">`binding`Do prvku <> přidejte prvek <> `WSHttpBinding` a nastavte `configurationName` atribut na hodnotu odpovídající vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-167">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="a5f2e-168">Přidejte prvek <`security`> a nastavte `mode` atribut na Message.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-168">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="a5f2e-169">Přidejte prvek <`message`> a nastavte `clientCredentialType` atribut na hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-169">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="a5f2e-170">V konfiguračním souboru služby nahraďte `<bindings>` oddíl následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-170">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="a5f2e-171">Pokud ještě nemáte konfigurační soubor služby, přečtěte si téma [použití vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-171">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

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

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="a5f2e-172">Použití vazby v klientovi</span><span class="sxs-lookup"><span data-stu-id="a5f2e-172">Using the Binding in a Client</span></span>

<span data-ttu-id="a5f2e-173">Tento postup ukazuje, jak vygenerovat dva soubory: proxy server, který komunikuje se službou a konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-173">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="a5f2e-174">Popisuje také změny v klientském programu, což je třetí soubor, který se používá na klientovi.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-174">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="a5f2e-175">Použití vazby v klientovi s konfigurací</span><span class="sxs-lookup"><span data-stu-id="a5f2e-175">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="a5f2e-176">Použijte nástroj SvcUtil.exe k vygenerování kódu a konfiguračního souboru proxy serveru z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-176">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="a5f2e-177">Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2e-177">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="a5f2e-178">Nahraďte [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) oddíl generovaného konfiguračního souboru konfiguračním kódem z předchozí části.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-178">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="a5f2e-179">Kód procedurální je vložen na začátek `Main` metody klientského programu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-179">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="a5f2e-180">Vytvořte instanci generované třídy klienta předáním názvu vazby v konfiguračním souboru jako vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-180">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="a5f2e-181">Zavolejte <xref:System.ServiceModel.ClientBase%601.Open%2A> metodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-181">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="a5f2e-182">Zavolejte službu a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="a5f2e-182">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="a5f2e-183">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5f2e-183">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="a5f2e-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5f2e-184">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="a5f2e-185">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="a5f2e-185">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="a5f2e-186">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="a5f2e-186">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="a5f2e-187">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="a5f2e-187">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="a5f2e-188">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a5f2e-188">Security Overview</span></span>](./feature-details/security-overview.md)
