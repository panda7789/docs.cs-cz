---
title: 'Postupy: Zabezpečené koncové body metadat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
author: BrucePerlerMS
ms.openlocfilehash: f1dae4b9d2976ddbc941e49843324a29ec8885a4
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836349"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="12e18-102">Postupy: Zabezpečené koncové body metadat</span><span class="sxs-lookup"><span data-stu-id="12e18-102">How to: Secure Metadata Endpoints</span></span>
<span data-ttu-id="12e18-103">Metadata služby mohou obsahovat citlivé údaje o aplikaci, která uživatel se zlými úmysly využívat.</span><span class="sxs-lookup"><span data-stu-id="12e18-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="12e18-104">Příjemci služby budete možná muset zabezpečené mechanismus pro získání metadat o vaší služby.</span><span class="sxs-lookup"><span data-stu-id="12e18-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="12e18-105">Proto je někdy nezbytné pro publikování metadata pomocí zabezpečeného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="12e18-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>  
  
 <span data-ttu-id="12e18-106">Koncové body metadat jsou obecně zabezpečené pomocí mechanismů standard zabezpečení definovaná ve Windows Communication Foundation (WCF) pro zabezpečení koncových bodů aplikace.</span><span class="sxs-lookup"><span data-stu-id="12e18-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="12e18-107">(Další informace najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="12e18-107">(For more information, see [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span></span>  
  
 <span data-ttu-id="12e18-108">Toto téma vás provede kroky k vytvoření koncového bodu zabezpečené pomocí certifikátu vrstvy SSL (Secure Sockets) nebo jinými slovy, koncový bod HTTPS.</span><span class="sxs-lookup"><span data-stu-id="12e18-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="12e18-109">Chcete-li vytvořit zabezpečené HTTPS GET koncových bodů metadat v kódu</span><span class="sxs-lookup"><span data-stu-id="12e18-109">To create a secure HTTPS GET metadata endpoint in code</span></span>  
  
1.  <span data-ttu-id="12e18-110">Konfigurace portu s příslušný certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="12e18-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="12e18-111">Certifikát musí pocházet od důvěryhodné autority a musí mít zamýšlené použití "Ověřování služby."</span><span class="sxs-lookup"><span data-stu-id="12e18-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="12e18-112">Musíte použít nástroj HttpCfg.exe připojit certifikát na port.</span><span class="sxs-lookup"><span data-stu-id="12e18-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="12e18-113">Zobrazit [postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="12e18-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="12e18-114">Předmět certifikátu nebo jeho systému DNS (Domain Name) musí odpovídat názvu počítače.</span><span class="sxs-lookup"><span data-stu-id="12e18-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="12e18-115">To je nezbytné, protože jeden z prvních kroků, které provádí mechanismus HTTPS je ke kontrole, jestli se certifikát vydal do stejný identifikátor URI (Uniform Resource) jako adresu, na kterém je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="12e18-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>  
  
2.  <span data-ttu-id="12e18-116">Vytvořit novou instanci třídy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.</span><span class="sxs-lookup"><span data-stu-id="12e18-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>  
  
3.  <span data-ttu-id="12e18-117">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídu `true`.</span><span class="sxs-lookup"><span data-stu-id="12e18-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>  
  
4.  <span data-ttu-id="12e18-118">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti na příslušné adrese URL.</span><span class="sxs-lookup"><span data-stu-id="12e18-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="12e18-119">Všimněte si, že pokud zadáte absolutní adresa, adresa URL musí začínat schématem "https://".</span><span class="sxs-lookup"><span data-stu-id="12e18-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="12e18-120">Pokud zadáte relativní adresu, musíte zadat základní adresu HTTPS pro hostitele vaší služby.</span><span class="sxs-lookup"><span data-stu-id="12e18-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="12e18-121">Pokud není tato vlastnost nastavena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.</span><span class="sxs-lookup"><span data-stu-id="12e18-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
5.  <span data-ttu-id="12e18-122">Přidání instance kolekce chování, která <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost <xref:System.ServiceModel.Description.ServiceDescription> třídy vrací, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="12e18-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="12e18-123">Chcete-li vytvořit zabezpečené HTTPS GET koncových bodů metadat v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="12e18-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>  
  
1.  <span data-ttu-id="12e18-124">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element konfiguračního souboru pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="12e18-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>  
  
2.  <span data-ttu-id="12e18-125">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elementu [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="12e18-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="12e18-126">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="12e18-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>  
  
4.  <span data-ttu-id="12e18-127">Nastavte `name` atribut `<behavior>` element na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12e18-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="12e18-128">`name` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="12e18-128">The `name` attribute is required.</span></span> <span data-ttu-id="12e18-129">Následující příklad používá hodnotu `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="12e18-129">The example below uses the value `mySvcBehavior`.</span></span>  
  
5.  <span data-ttu-id="12e18-130">Přidat [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) k `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="12e18-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>  
  
6.  <span data-ttu-id="12e18-131">Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="12e18-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>  
  
7.  <span data-ttu-id="12e18-132">Nastavte `httpsGetUrl` atribut `<serviceMetadata>` element na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12e18-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="12e18-133">Všimněte si, že pokud zadáte absolutní adresa, adresa URL musí začínat schématem "https://".</span><span class="sxs-lookup"><span data-stu-id="12e18-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="12e18-134">Pokud zadáte relativní adresu, musíte zadat základní adresu HTTPS pro hostitele vaší služby.</span><span class="sxs-lookup"><span data-stu-id="12e18-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="12e18-135">Pokud není tato vlastnost nastavena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.</span><span class="sxs-lookup"><span data-stu-id="12e18-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
8.  <span data-ttu-id="12e18-136">Chcete-li používat chování se službou, nastavte `behaviorConfiguration` atribut [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) prvku na hodnotu atribut name elementu chování.</span><span class="sxs-lookup"><span data-stu-id="12e18-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="12e18-137">Následující kód konfigurace ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="12e18-137">The following configuration code shows a complete example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="12e18-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="12e18-138">Example</span></span>  
 <span data-ttu-id="12e18-139">Následující příklad vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="12e18-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="12e18-140">Kód poté vytvoří instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy a nastaví vlastnosti pro vytvoření bod zabezpečené metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="12e18-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12e18-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="12e18-141">Compiling the Code</span></span>  
 <span data-ttu-id="12e18-142">Příklad kódu používá následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="12e18-142">The code example uses the following namespaces:</span></span>  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="12e18-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="12e18-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [<span data-ttu-id="12e18-144">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="12e18-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="12e18-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="12e18-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="12e18-146">Informace o zabezpečení metadat</span><span class="sxs-lookup"><span data-stu-id="12e18-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [<span data-ttu-id="12e18-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="12e18-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
