---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201788"
---
# \<serviceMetadata>
<span data-ttu-id="e1522-101">Určuje publikování metadat služby a přidružených informací.</span><span class="sxs-lookup"><span data-stu-id="e1522-101">Specifies the publication of service metadata and associated information.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="e1522-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1522-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1522-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e1522-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e1522-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e1522-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1522-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="e1522-105">Attributes</span></span>  
  
|<span data-ttu-id="e1522-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="e1522-106">Attribute</span></span>|<span data-ttu-id="e1522-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e1522-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1522-108">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="e1522-108">externalMetadataLocation</span></span>|<span data-ttu-id="e1522-109">Identifikátor URI, který obsahuje umístění souboru WSDL, který je vrácen uživateli v odpovědi na požadavky WSDL a MEX namísto automaticky generovaného WSDL.</span><span class="sxs-lookup"><span data-stu-id="e1522-109">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="e1522-110">Pokud tento atribut není nastaven, je vrácen výchozí prvek WSDL.</span><span class="sxs-lookup"><span data-stu-id="e1522-110">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="e1522-111">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e1522-111">The default is an empty string.</span></span>|  
|<span data-ttu-id="e1522-112">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="e1522-112">httpGetBinding</span></span>|<span data-ttu-id="e1522-113">Řetězec, který určuje typ vazby, který bude použit pro načtení metadat prostřednictvím HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="e1522-113">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="e1522-114">Toto nastavení je volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1522-114">This setting is optional.</span></span> <span data-ttu-id="e1522-115">Pokud není zadaný, použijí se výchozí vazby.</span><span class="sxs-lookup"><span data-stu-id="e1522-115">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="e1522-116">Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> .</span><span class="sxs-lookup"><span data-stu-id="e1522-116">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="e1522-117">Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1522-117">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="e1522-118">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e1522-118">httpGetBindingConfiguration</span></span>|<span data-ttu-id="e1522-119">Řetězec, který nastaví název vazby, která je zadána v `httpGetBinding` atributu, který odkazuje na Další informace o konfiguraci této vazby.</span><span class="sxs-lookup"><span data-stu-id="e1522-119">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="e1522-120">V části se musí definovat stejný název `<bindings>` .</span><span class="sxs-lookup"><span data-stu-id="e1522-120">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="e1522-121">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="e1522-121">httpGetEnabled</span></span>|<span data-ttu-id="e1522-122">Logická hodnota, která určuje, zda se mají publikovat metadata služby pro načtení pomocí požadavku HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="e1522-122">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="e1522-123">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="e1522-123">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e1522-124">Pokud není zadán atribut httpGetUrl, adresa, na které jsou metadata publikována, je adresa služby plus a "? WSDL".</span><span class="sxs-lookup"><span data-stu-id="e1522-124">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="e1522-125">Například pokud je adresa služby `http://localhost:8080/CalculatorService` , adresa HTTP/GET metadat je `http://localhost:8080/CalculatorService?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="e1522-125">For example, if the service address is `http://localhost:8080/CalculatorService`, the HTTP/Get metadata address is `http://localhost:8080/CalculatorService?wsdl`.</span></span><br /><br /> <span data-ttu-id="e1522-126">Pokud je tato vlastnost `false` nebo adresa služby není založena na http nebo https, "? WSDL" se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e1522-126">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="e1522-127">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="e1522-127">httpGetUrl</span></span>|<span data-ttu-id="e1522-128">Identifikátor URI, který určuje adresu, na které jsou metadata publikována pro načtení pomocí požadavku HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="e1522-128">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="e1522-129">Je-li zadán relativní identifikátor URI, bude považován za relativní k základní adrese služby.</span><span class="sxs-lookup"><span data-stu-id="e1522-129">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="e1522-130">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="e1522-130">httpsGetBinding</span></span>|<span data-ttu-id="e1522-131">Řetězec, který určuje typ vazby, který bude použit pro načtení metadat prostřednictvím protokolu HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="e1522-131">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="e1522-132">Toto nastavení je volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1522-132">This setting is optional.</span></span> <span data-ttu-id="e1522-133">Pokud není zadaný, použijí se výchozí vazby.</span><span class="sxs-lookup"><span data-stu-id="e1522-133">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="e1522-134">Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> .</span><span class="sxs-lookup"><span data-stu-id="e1522-134">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="e1522-135">Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1522-135">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="e1522-136">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e1522-136">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="e1522-137">Řetězec, který nastaví název vazby, která je zadána v `httpsGetBinding` atributu, který odkazuje na Další informace o konfiguraci této vazby.</span><span class="sxs-lookup"><span data-stu-id="e1522-137">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="e1522-138">V části se musí definovat stejný název `<bindings>` .</span><span class="sxs-lookup"><span data-stu-id="e1522-138">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="e1522-139">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="e1522-139">httpsGetEnabled</span></span>|<span data-ttu-id="e1522-140">Logická hodnota, která určuje, zda se mají publikovat metadata služby pro načtení pomocí požadavku HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="e1522-140">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="e1522-141">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="e1522-141">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e1522-142">Pokud není zadán atribut httpsGetUrl, adresa, na které jsou metadata publikována, je adresa služby plus a "? WSDL".</span><span class="sxs-lookup"><span data-stu-id="e1522-142">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="e1522-143">Například pokud je adresa služby " https://localhost:8080/CalculatorService ", adresa HTTP/GET metadat je " https://localhost:8080/CalculatorService?wsdl ".</span><span class="sxs-lookup"><span data-stu-id="e1522-143">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="e1522-144">Pokud je tato vlastnost `false` nebo adresa služby není založena na http nebo https, "? WSDL" se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e1522-144">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="e1522-145">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="e1522-145">httpsGetUrl</span></span>|<span data-ttu-id="e1522-146">Identifikátor URI, který určuje adresu, na které jsou metadata publikována pro načtení pomocí požadavku HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="e1522-146">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="e1522-147">policyVersion</span><span class="sxs-lookup"><span data-stu-id="e1522-147">policyVersion</span></span>|<span data-ttu-id="e1522-148">Řetězec, který určuje verzi používané specifikace WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="e1522-148">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="e1522-149">Tento atribut je typu <xref:System.ServiceModel.Description.PolicyVersion> .</span><span class="sxs-lookup"><span data-stu-id="e1522-149">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1522-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e1522-150">Child Elements</span></span>  
 <span data-ttu-id="e1522-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1522-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1522-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e1522-152">Parent Elements</span></span>  
  
|<span data-ttu-id="e1522-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1522-153">Element</span></span>|<span data-ttu-id="e1522-154">Description</span><span class="sxs-lookup"><span data-stu-id="e1522-154">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e1522-155">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e1522-155">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1522-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1522-156">Remarks</span></span>  
 <span data-ttu-id="e1522-157">Tento prvek konfigurace umožňuje řídit funkce publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="e1522-157">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="e1522-158">Aby nedocházelo k neúmyslnému zveřejnění potenciálně citlivých metadat služby, služba výchozí konfigurace služby Windows Communication Foundation (WCF) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="e1522-158">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="e1522-159">Toto chování je standardně zabezpečené, ale také znamená, že nemůžete použít nástroj pro import metadat (například Svcutil. exe), aby se vygeneroval kód klienta vyžadovaný pro volání služby, pokud není v konfiguraci explicitně povolený chování publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="e1522-159">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="e1522-160">Pomocí tohoto elementu konfigurace můžete toto chování publikování povolit pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="e1522-160">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="e1522-161">Podrobný příklad konfigurace tohoto chování najdete v tématu chování při [publikování metadat](../../../wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="e1522-161">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="e1522-162">Volitelné `httpGetBinding` atributy a `httpsGetBinding` umožňují konfigurovat vazby používané pro načtení METADAT prostřednictvím HTTP GET (nebo https Get).</span><span class="sxs-lookup"><span data-stu-id="e1522-162">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="e1522-163">Pokud nejsou zadány, použijí se výchozí vazby ( `HttpTransportBindingElement` v případě protokolu HTTP a `HttpsTransportBindingElement` v případě protokolu HTTPS) pro načtení metadat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="e1522-163">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="e1522-164">Všimněte si, že nemůžete použít tyto atributy s předdefinovanými vazbami WCF.</span><span class="sxs-lookup"><span data-stu-id="e1522-164">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="e1522-165">Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> .</span><span class="sxs-lookup"><span data-stu-id="e1522-165">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="e1522-166">Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1522-166">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="e1522-167">Aby se snížila pravděpodobnost, že se služba vystavuje uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí mechanismu SSL přes protokol HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="e1522-167">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="e1522-168">K tomu je nutné nejdřív navazovat vhodný certifikát X. 509 na konkrétní port v počítači, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="e1522-168">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="e1522-169">(Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).) Za druhé přidejte tento prvek do konfigurace služby a nastavte `httpsGetEnabled` atribut na `true` .</span><span class="sxs-lookup"><span data-stu-id="e1522-169">(For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="e1522-170">Nakonec nastavte `httpsGetUrl` atribut na adresu URL koncového bodu metadat služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e1522-170">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e1522-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1522-171">Example</span></span>  
 <span data-ttu-id="e1522-172">Následující příklad nakonfiguruje službu tak, aby zveřejnila metadata pomocí \<serviceMetadata> elementu.</span><span class="sxs-lookup"><span data-stu-id="e1522-172">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="e1522-173">Také nakonfiguruje koncový bod k zveřejnění `IMetadataExchange` kontraktu jako implementace protokolu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="e1522-173">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="e1522-174">V příkladu se používá `mexHttpBinding` , což je pohodlná standardní vazba, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveným na `None` .</span><span class="sxs-lookup"><span data-stu-id="e1522-174">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="e1522-175">V koncovém bodu se používá relativní adresa "MEX", která při překladu na základě základní adresy služeb má za následek adresu koncového bodu `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="e1522-175">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span>  
  
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
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e1522-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1522-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="e1522-177">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e1522-177">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e1522-178">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="e1522-178">Metadata Publishing Behavior</span></span>](../../../wcf/samples/metadata-publishing-behavior.md)
