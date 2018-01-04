---
title: "Postupy: Zabezpečené koncové body metadat"
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
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6923703230d6792d8938de149f64c41a3bf95699
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="ecc2e-102">Postupy: Zabezpečené koncové body metadat</span><span class="sxs-lookup"><span data-stu-id="ecc2e-102">How to: Secure Metadata Endpoints</span></span>
<span data-ttu-id="ecc2e-103">Metadata pro služby mohou obsahovat citlivé údaje o vaší aplikaci, které můžete využít uživatel se zlými úmysly.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="ecc2e-104">Příjemci vaší služby také může vyžadovat zabezpečené mechanismus pro získání metadat o služby.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="ecc2e-105">Někdy je proto potřeba publikovat metadata pomocí zabezpečený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>  
  
 <span data-ttu-id="ecc2e-106">Koncové body metadat jsou obecně zabezpečené pomocí mechanismů standardní zabezpečení, které jsou definované v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro zabezpečení koncových bodů aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-106">Metadata endpoints are generally secured using the standard security mechanisms defined in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] for securing application endpoints.</span></span> <span data-ttu-id="ecc2e-107">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="ecc2e-107">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span></span>  
  
 <span data-ttu-id="ecc2e-108">Toto téma vás provede kroky k vytvoření koncového bodu zabezpečeny certifikát Secure Sockets Layer (SSL) nebo jinými slovy, koncový bod HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="ecc2e-109">Chcete-li vytvořit zabezpečený protokol HTTPS získat metadata koncový bod v kódu</span><span class="sxs-lookup"><span data-stu-id="ecc2e-109">To create a secure HTTPS GET metadata endpoint in code</span></span>  
  
1.  <span data-ttu-id="ecc2e-110">Nakonfigurujte port se příslušný certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="ecc2e-111">Certifikát musí pocházet ze důvěryhodnou autoritou a musí mít zamýšlené použití souboru "Autorizace služby."</span><span class="sxs-lookup"><span data-stu-id="ecc2e-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="ecc2e-112">Musíte použít nástroj HttpCfg.exe připojit certifikát na port.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="ecc2e-113">V tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ecc2e-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ecc2e-114">Předmět certifikátu nebo jeho systému DNS (Domain Name) musí odpovídat názvu počítače.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="ecc2e-115">Toto je nezbytné, protože jeden z první kroky, které provádí mechanismus HTTPS je zkontrolovat, že je certifikát vystavený k stejný identifikátor URI (Uniform Resource) jako adresu, na kterém je volána.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>  
  
2.  <span data-ttu-id="ecc2e-116">Vytvořit novou instanci třídy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>  
  
3.  <span data-ttu-id="ecc2e-117">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy k `true`.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>  
  
4.  <span data-ttu-id="ecc2e-118">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnost příslušnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="ecc2e-119">Všimněte si, že pokud zadáte adresu absolutní, adresa URL musí začínat řetězcem schématu "https://".</span><span class="sxs-lookup"><span data-stu-id="ecc2e-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="ecc2e-120">Pokud zadáte adresu relativní, je třeba zadat základní adresu HTTPS pro svého hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="ecc2e-121">Pokud není tato vlastnost určena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
5.  <span data-ttu-id="ecc2e-122">Přidat do kolekce chování instanci, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost <xref:System.ServiceModel.Description.ServiceDescription> třídy vrátí, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="ecc2e-123">Chcete-li vytvořit zabezpečený protokol HTTPS získat metadata koncový bod v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="ecc2e-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>  
  
1.  <span data-ttu-id="ecc2e-124">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu, který chcete [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element konfiguračního souboru pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>  
  
2.  <span data-ttu-id="ecc2e-125">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elementu, který chcete [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="ecc2e-126">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu, který chcete `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>  
  
4.  <span data-ttu-id="ecc2e-127">Nastavte `name` atribut `<behavior>` element na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="ecc2e-128">`name` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-128">The `name` attribute is required.</span></span> <span data-ttu-id="ecc2e-129">Následující příklad používá hodnotu `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-129">The example below uses the value `mySvcBehavior`.</span></span>  
  
5.  <span data-ttu-id="ecc2e-130">Přidat [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) k `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>  
  
6.  <span data-ttu-id="ecc2e-131">Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` element `true`.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>  
  
7.  <span data-ttu-id="ecc2e-132">Nastavte `httpsGetUrl` atribut `<serviceMetadata>` element na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="ecc2e-133">Všimněte si, že pokud zadáte adresu absolutní, adresa URL musí začínat řetězcem schématu "https://".</span><span class="sxs-lookup"><span data-stu-id="ecc2e-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="ecc2e-134">Pokud zadáte adresu relativní, je třeba zadat základní adresu HTTPS pro svého hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="ecc2e-135">Pokud není tato vlastnost určena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
8.  <span data-ttu-id="ecc2e-136">Chcete-li použít chování službou, nastavte `behaviorConfiguration` atribut [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) prvku na hodnotu atribut názvu prvku chování.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="ecc2e-137">Následující kód konfigurace ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-137">The following configuration code shows a complete example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ecc2e-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecc2e-138">Example</span></span>  
 <span data-ttu-id="ecc2e-139">Následující příklad vytvoří instanci <xref:System.ServiceModel.ServiceHost> a přidává koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="ecc2e-140">Kód vytvoří instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy a nastaví vlastnosti, které chcete vytvořit bod zabezpečené metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="ecc2e-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ecc2e-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ecc2e-141">Compiling the Code</span></span>  
 <span data-ttu-id="ecc2e-142">Příklad kódu používá následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="ecc2e-142">The code example uses the following namespaces:</span></span>  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="ecc2e-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecc2e-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [<span data-ttu-id="ecc2e-144">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="ecc2e-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="ecc2e-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="ecc2e-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ecc2e-146">Informace o zabezpečení metadat</span><span class="sxs-lookup"><span data-stu-id="ecc2e-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [<span data-ttu-id="ecc2e-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ecc2e-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
