---
title: '&lt;serviceMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a771b3b89c9031a011185a579e70767081d20597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicemetadatagt"></a><span data-ttu-id="0a5f6-102">&lt;serviceMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="0a5f6-102">&lt;serviceMetadata&gt;</span></span>
<span data-ttu-id="0a5f6-103">Určuje publikování metadat služby a související informace.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-103">Specifies the publication of service metadata and associated information.</span></span>  
  
<span data-ttu-id="0a5f6-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0a5f6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0a5f6-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0a5f6-105">\<behaviors></span></span>  
<span data-ttu-id="0a5f6-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0a5f6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0a5f6-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0a5f6-107">\<behavior></span></span>  
<span data-ttu-id="0a5f6-108">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="0a5f6-108">\<serviceMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a5f6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a5f6-109">Syntax</span></span>  
  
```xml
<serviceMetadata externalMetadataLocation="String"  
                 httpGetBinding="String" 
                 httpGetBindingConfiguration="String"  
                 httpGetEnabled="Boolean" 
                 httpGetUrl="String" 
                 httpsGetBinding="String" 
                 httpsGetBindingConfiguration="String"  
                 httpsGetEnabled="Boolean"   
                 httpsGetUrl="String"  
                 policyVersion="Policy12/Policy15" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a5f6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a5f6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a5f6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a5f6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a5f6-112">Attributes</span></span>  
  
|<span data-ttu-id="0a5f6-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a5f6-113">Attribute</span></span>|<span data-ttu-id="0a5f6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0a5f6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a5f6-115">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="0a5f6-115">externalMetadataLocation</span></span>|<span data-ttu-id="0a5f6-116">Identifikátor Uri, která obsahuje umístění souboru WSDL, která je vrátil uživateli v reakci na požadavky WSDL a MEX místo automaticky generovaný WSDL.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-116">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="0a5f6-117">Pokud není tento atribut nastavený, je výchozí WSDL vrátila.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-117">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="0a5f6-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="0a5f6-119">elementy httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="0a5f6-119">httpGetBinding</span></span>|<span data-ttu-id="0a5f6-120">Řetězec, který určuje typ vazby, který se použije pro načtení metadat pomocí metody GET protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-120">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="0a5f6-121">Toto nastavení je volitelné.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-121">This setting is optional.</span></span> <span data-ttu-id="0a5f6-122">Pokud není zadaný, použije se výchozí vazby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-122">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="0a5f6-123">Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-123">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="0a5f6-124">Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-124">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="0a5f6-125">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a5f6-125">httpGetBindingConfiguration</span></span>|<span data-ttu-id="0a5f6-126">Řetězec, který nastaví název vazby, který je uveden v `httpGetBinding` atribut, který odkazuje na další konfigurační informace této vazby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-126">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="0a5f6-127">Se stejným názvem, musí být definován v `<bindings>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-127">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="0a5f6-128">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="0a5f6-128">httpGetEnabled</span></span>|<span data-ttu-id="0a5f6-129">Logická hodnota, která určuje, zda publikování metadat služby k získání pomocí požadavek HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-129">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="0a5f6-130">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-130">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0a5f6-131">Pokud není zadán atribut httpGetUrl, adresu, kde je zveřejněna metadat je adresa služby plus "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="0a5f6-131">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="0a5f6-132">Například pokud je adresa služby "adrese http://localhost: 8080/CalculatorService", adresa protokolu HTTP nebo získat metadata je "adrese http://localhost: 8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="0a5f6-132">For example, if the service address is "http://localhost:8080/CalculatorService", the HTTP/Get metadata address is "http://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="0a5f6-133">Pokud je tato vlastnost `false`, nebo adresu služby není založen na protokolu HTTP nebo HTTPS, "? wsdl" je ignorována.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-133">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="0a5f6-134">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="0a5f6-134">httpGetUrl</span></span>|<span data-ttu-id="0a5f6-135">Identifikátor Uri, který určuje, kdy je zveřejněna metadata k získání pomocí požadavek HTTP nebo získat adresu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-135">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="0a5f6-136">Pokud je zadán relativní identifikátor Uri nakládáno jako relativně k základní adresa služby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-136">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="0a5f6-137">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="0a5f6-137">httpsGetBinding</span></span>|<span data-ttu-id="0a5f6-138">Řetězec, který určuje typ vazby, který se použije pro načtení metadat prostřednictvím protokolu HTTPS získat.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-138">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="0a5f6-139">Toto nastavení je volitelné.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-139">This setting is optional.</span></span> <span data-ttu-id="0a5f6-140">Pokud není zadaný, použije se výchozí vazby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-140">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="0a5f6-141">Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-141">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="0a5f6-142">Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-142">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="0a5f6-143">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a5f6-143">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="0a5f6-144">Řetězec, který nastaví název vazby, který je uveden v `httpsGetBinding` atribut, který odkazuje na další konfigurační informace této vazby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-144">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="0a5f6-145">Se stejným názvem, musí být definován v `<bindings>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-145">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="0a5f6-146">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="0a5f6-146">httpsGetEnabled</span></span>|<span data-ttu-id="0a5f6-147">Logická hodnota, která určuje, zda publikování metadat služby k získání pomocí požadavek HTTPS nebo získat.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-147">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="0a5f6-148">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0a5f6-149">Pokud není zadán atribut httpsGetUrl, adresu, kde je zveřejněna metadat je adresa služby plus "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="0a5f6-149">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="0a5f6-150">Například pokud je adresa služby "https://localhost:8080/CalculatorService", adresa protokolu HTTP nebo získat metadata je "https://localhost:8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="0a5f6-150">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="0a5f6-151">Pokud je tato vlastnost `false`, nebo adresu služby není založen na protokolu HTTP nebo HTTPS, "? wsdl" je ignorována.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-151">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="0a5f6-152">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="0a5f6-152">httpsGetUrl</span></span>|<span data-ttu-id="0a5f6-153">Identifikátor Uri, který určuje, kdy je zveřejněna metadata k získání pomocí požadavek HTTPS nebo získat adresu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-153">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="0a5f6-154">PolicyVersion</span><span class="sxs-lookup"><span data-stu-id="0a5f6-154">policyVersion</span></span>|<span data-ttu-id="0a5f6-155">Řetězec, který určuje verzi specifikace WS-Policy, který je používán.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-155">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="0a5f6-156">Tento atribut je typu <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-156">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a5f6-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a5f6-157">Child Elements</span></span>  
 <span data-ttu-id="0a5f6-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="0a5f6-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a5f6-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a5f6-159">Parent Elements</span></span>  
  
|<span data-ttu-id="0a5f6-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a5f6-160">Element</span></span>|<span data-ttu-id="0a5f6-161">Popis</span><span class="sxs-lookup"><span data-stu-id="0a5f6-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a5f6-162">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0a5f6-162">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="0a5f6-163">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-163">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a5f6-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a5f6-164">Remarks</span></span>  
 <span data-ttu-id="0a5f6-165">Tento element konfigurace můžete k řízení funkcí publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-165">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="0a5f6-166">Aby se zabránilo neúmyslnému zveřejnění metadata potenciálně citlivých služby, výchozí konfiguraci pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zakáže publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-166">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="0a5f6-167">Toto chování je ve výchozím nastavení zabezpečení, ale také znamená, že nelze použít metadata importovat nástroj (například Svcutil.exe) ke generování kódu klienta pro volání služby, pokud není výslovně povolena chování publikování metadat služby v konfiguraci požadován.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-167">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="0a5f6-168">Pomocí elementu. Tato konfigurace, můžete povolit toto chování při publikování pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-168">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="0a5f6-169">Podrobný příklad konfigurace toto chování najdete v tématu [chování publikování metadat](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f6-169">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="0a5f6-170">Volitelné `httpGetBinding` a `httpsGetBinding` atributů umožňují konfigurovat vazby používá pro načtení metadat prostřednictvím metody GET protokolu HTTP (nebo získat HTTPS).</span><span class="sxs-lookup"><span data-stu-id="0a5f6-170">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="0a5f6-171">Pokud nejsou zadané, výchozí vazby (`HttpTransportBindingElement`, v případě protokolu HTTP a `HttpsTransportBindingElement`, v případě HTTPS) se používají pro načtení metadat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-171">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="0a5f6-172">Všimněte si, že tyto atributy nelze použít s integrovanou vazby WCF.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-172">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="0a5f6-173">Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-173">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="0a5f6-174">Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-174">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="0a5f6-175">Aby se snížila zranitelnost služby uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí protokolu SSL přes protokol HTTP (HTTPS) mechanismus.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-175">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="0a5f6-176">To pokud chcete udělat, je třeba nejprve svázat vhodný certifikát X.509 konkrétní port, na počítači, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-176">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="0a5f6-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Druhý, přidejte tento element konfigurace služby a nastavte `httpsGetEnabled` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="0a5f6-178">Nakonec nastavte `httpsGetUrl` atribut na adresu URL metadat koncového bodu služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-178">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml
<behaviors>  
  <serviceBehaviors>  
    <behavior name="NewBehavior">  
      <serviceMetadata httpsGetEnabled="true"   
                       httpsGetUrl="https://myComputerName/myEndpoint" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="example"></a><span data-ttu-id="0a5f6-179">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a5f6-179">Example</span></span>  
 <span data-ttu-id="0a5f6-180">Následující příklad konfigurace ve službě vystavit metadat pomocí \<serviceMetadata > elementu.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-180">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="0a5f6-181">Nakonfiguruje taky koncový bod ke zveřejnění `IMetadataExchange` kontrakt jako implementaci protokolu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="0a5f6-181">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="0a5f6-182">V příkladu se používá `mexHttpBinding`, což je pro vaše pohodlí standardní vazby, která je ekvivalentní `wsHttpBinding` s režim zabezpečení nastavený na `None`.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-182">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="0a5f6-183">Relativní adresu "mex" se používá v koncovém bodě, který v případě přeložit proti služby základní adresu výsledkem koncový bod adresy http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="0a5f6-183">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService" 
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a5f6-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a5f6-184">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="0a5f6-185">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0a5f6-185">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="0a5f6-186">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="0a5f6-186">Metadata Publishing Behavior</span></span>](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
