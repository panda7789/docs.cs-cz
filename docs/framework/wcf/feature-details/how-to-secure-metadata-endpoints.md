---
title: 'Postupy: Zabezpečené koncové body metadat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 2746c608fb47b94446c5d7e10748ba185d555e7f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202333"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="7962d-102">Postupy: Zabezpečené koncové body metadat</span><span class="sxs-lookup"><span data-stu-id="7962d-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="7962d-103">Metadata služby můžou obsahovat citlivé informace o vaší aplikaci, které může využívat uživatel se zlými úmysly.</span><span class="sxs-lookup"><span data-stu-id="7962d-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="7962d-104">Uživatelé vaší služby můžou také vyžadovat zabezpečený mechanismus pro získání metadat služby.</span><span class="sxs-lookup"><span data-stu-id="7962d-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="7962d-105">Z tohoto důvodu je někdy nutné publikovat metadata pomocí zabezpečeného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7962d-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="7962d-106">Koncové body metadat jsou obecně zabezpečeny pomocí standardních mechanismů zabezpečení definovaných v Windows Communication Foundation (WCF) pro zabezpečení koncových bodů aplikace.</span><span class="sxs-lookup"><span data-stu-id="7962d-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="7962d-107">Další informace najdete v tématu [Přehled zabezpečení](security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7962d-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="7962d-108">Toto téma vás provede kroky pro vytvoření koncového bodu zabezpečeného certifikátem SSL (Secure Sockets Layer) (SSL) nebo jinými slovy koncového bodu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7962d-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="7962d-109">Vytvoření koncového bodu metadat GET pro zabezpečený protokol HTTPS v kódu</span><span class="sxs-lookup"><span data-stu-id="7962d-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="7962d-110">Nakonfigurujte port s příslušným certifikátem X. 509.</span><span class="sxs-lookup"><span data-stu-id="7962d-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="7962d-111">Certifikát musí pocházet z důvěryhodné autority a musí mít zamýšlené použití autorizace služby.</span><span class="sxs-lookup"><span data-stu-id="7962d-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="7962d-112">K připojení certifikátu k portu je nutné použít nástroj HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="7962d-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="7962d-113">Informace najdete v tématu [How to: Configure a port with a Certificate SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="7962d-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7962d-114">Předmět certifikátu nebo jeho DNS (Domain Name System) se musí shodovat s názvem počítače.</span><span class="sxs-lookup"><span data-stu-id="7962d-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="7962d-115">To je nezbytné, protože jeden z prvních kroků mechanismu protokolu HTTPS provede ověření, že certifikát je vydán pro stejný identifikátor URI (Uniform Resource Identifier) jako adresa, na které je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="7962d-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="7962d-116">Vytvořte novou instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.</span><span class="sxs-lookup"><span data-stu-id="7962d-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="7962d-117">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy na `true` .</span><span class="sxs-lookup"><span data-stu-id="7962d-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="7962d-118">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnost na příslušnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7962d-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="7962d-119">Všimněte si, že pokud zadáte absolutní adresu, adresa URL musí začínat schématem `https://` .</span><span class="sxs-lookup"><span data-stu-id="7962d-119">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="7962d-120">Pokud zadáte relativní adresu, musíte pro hostitele služby zadat základní adresu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7962d-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="7962d-121">Není-li tato vlastnost nastavena, je použita výchozí adresa "" nebo přímo na základní adrese HTTPS pro službu.</span><span class="sxs-lookup"><span data-stu-id="7962d-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="7962d-122">Přidejte instanci do kolekce chování, kterou <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> vrátí vlastnost třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7962d-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="7962d-123">Vytvoření koncového bodu metadat získat zabezpečený protokol HTTPS v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7962d-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="7962d-124">Přidejte [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element do [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) prvku konfiguračního souboru pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="7962d-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="7962d-125">Přidejte [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element do [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7962d-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="7962d-126">Přidejte [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element do `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7962d-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="7962d-127">Nastavte `name` atribut `<behavior>` prvku na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7962d-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="7962d-128">`name` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="7962d-128">The `name` attribute is required.</span></span> <span data-ttu-id="7962d-129">Následující příklad používá hodnotu `mySvcBehavior` .</span><span class="sxs-lookup"><span data-stu-id="7962d-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="7962d-130">Přidejte [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) k `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7962d-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="7962d-131">Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="7962d-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="7962d-132">Nastavte `httpsGetUrl` atribut `<serviceMetadata>` prvku na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7962d-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="7962d-133">Všimněte si, že pokud zadáte absolutní adresu, adresa URL musí začínat schématem `https://` .</span><span class="sxs-lookup"><span data-stu-id="7962d-133">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="7962d-134">Pokud zadáte relativní adresu, musíte pro hostitele služby zadat základní adresu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7962d-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="7962d-135">Není-li tato vlastnost nastavena, je použita výchozí adresa "" nebo přímo na základní adrese HTTPS pro službu.</span><span class="sxs-lookup"><span data-stu-id="7962d-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="7962d-136">Chcete-li použít chování se službou, nastavte `behaviorConfiguration` atribut [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu na hodnotu atributu name elementu behavior.</span><span class="sxs-lookup"><span data-stu-id="7962d-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="7962d-137">Následující konfigurační kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="7962d-137">The following configuration code shows a complete example.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a><span data-ttu-id="7962d-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="7962d-138">Example</span></span>

<span data-ttu-id="7962d-139">Následující příklad vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7962d-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="7962d-140">Kód pak vytvoří instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy a nastaví vlastnosti pro vytvoření zabezpečeného bodu výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="7962d-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="7962d-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7962d-141">Compiling the Code</span></span>

<span data-ttu-id="7962d-142">Příklad kódu používá následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="7962d-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="7962d-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="7962d-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="7962d-144">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="7962d-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="7962d-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="7962d-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7962d-146">Informace o zabezpečení metadat</span><span class="sxs-lookup"><span data-stu-id="7962d-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="7962d-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7962d-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
