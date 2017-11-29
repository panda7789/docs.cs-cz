---
title: "Konfigurace vazeb pro služby Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ccb7dbb7beb99cbad9a0ecf9ad14dd74e37fda6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="32a46-102">Konfigurace vazeb pro služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="32a46-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="32a46-103">Při vytváření aplikace, budete chtít často odložení rozhodnutí, která správci po nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="32a46-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="32a46-104">Například je často žádný způsob, jak předem zjistit, co služba adresu nebo identifikátor URI (Uniform Resource), bude.</span><span class="sxs-lookup"><span data-stu-id="32a46-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="32a46-105">Místo pevně kódováno adresu, je vhodnější umožňují správcům udělat po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="32a46-106">Tato možnost se provádí prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="32a46-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32a46-107">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config` přepínač tak, aby rychle vytvořit konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="32a46-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="32a46-108">Hlavní části</span><span class="sxs-lookup"><span data-stu-id="32a46-108">Major Sections</span></span>  
 <span data-ttu-id="32a46-109">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Schéma konfigurace zahrnuje následující tři hlavní oddíly (`serviceModel`, `bindings`, a `services`):</span><span class="sxs-lookup"><span data-stu-id="32a46-109">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="32a46-110">Elementy ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32a46-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="32a46-111">Můžete použít v části ohraničené `system.ServiceModel` elementu, který chcete nakonfigurovat jeden nebo více koncových bodů, jakož i nastavení služby typu služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="32a46-112">Každý koncový body, můžete pak nakonfigurovat s adresu, kontrakt a vazbu.</span><span class="sxs-lookup"><span data-stu-id="32a46-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="32a46-113">Koncové body, najdete v části [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="32a46-113"> endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="32a46-114">Pokud nejsou zadány žádné koncové body, modul runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="32a46-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="32a46-115">výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="32a46-115"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="32a46-116">Vazba určuje přenosy (HTTP, TCP, kanály, služby Řízení front zpráv) a protokoly (zabezpečení, spolehlivost, transakce toky) a se skládá z elementů, z nichž každý určuje aspekt jak koncový bod komunikuje s ostatními vazby.</span><span class="sxs-lookup"><span data-stu-id="32a46-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="32a46-117">Například zadání [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element označuje na používání protokolu HTTP jako přenosu pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="32a46-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="32a46-118">To se používá k přenosu do koncového bodu v době běhu, když je otevřen služby pomocí tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="32a46-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="32a46-119">Existují dva typy vazeb: předdefinované a vlastní.</span><span class="sxs-lookup"><span data-stu-id="32a46-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="32a46-120">Předdefinované vazby obsahovat užitečné kombinace elementů, které se používají v běžné scénáře.</span><span class="sxs-lookup"><span data-stu-id="32a46-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="32a46-121">Pro seznam předdefinovaných vazby typy, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] poskytuje, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="32a46-121">For a list of predefined binding types that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="32a46-122">Pokud žádná vazba předdefinované kolekce má správnou kombinaci funkcí, které potřebuje aplikace služby, můžete vytvořit vlastní vazby splnění aplikace.</span><span class="sxs-lookup"><span data-stu-id="32a46-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="32a46-123">vlastní vazby, najdete v části [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="32a46-123"> custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="32a46-124">Následující čtyři příklady ilustrují nejběžnější konfigurace vazby používá pro nastavení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-124">The following four examples illustrate the most common binding configurations used for setting up a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="32a46-125">Určení použít typ vazby koncového bodu</span><span class="sxs-lookup"><span data-stu-id="32a46-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="32a46-126">V prvním příkladu znázorňuje, jak zadat koncovým bodem nakonfigurovaným s adresu, kontrakt a vazbu.</span><span class="sxs-lookup"><span data-stu-id="32a46-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
```  
  
 <span data-ttu-id="32a46-127">V tomto příkladu `name` atribut určuje, jaký typ služby, konfigurace je pro.</span><span class="sxs-lookup"><span data-stu-id="32a46-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="32a46-128">Při vytváření služby v kódu pomocí `HelloWorld` kontrakt, je inicializován s koncové body definované v příklad konfigurace.</span><span class="sxs-lookup"><span data-stu-id="32a46-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="32a46-129">Pokud sestavení implementuje pouze jeden kontrakt služby, `name` atribut můžete tento parametr vynechán, protože služba používá k dispozici pouze typu.</span><span class="sxs-lookup"><span data-stu-id="32a46-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="32a46-130">Atribut přebírá řetězec, který musí být ve formátu`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="32a46-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="32a46-131">`address` Atribut určuje identifikátor URI, který ostatní koncové body, používat pro komunikaci ve službě.</span><span class="sxs-lookup"><span data-stu-id="32a46-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="32a46-132">Identifikátor URI může být absolutní nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="32a46-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="32a46-133">Pokud je zadaný relativní adresa, hostitel se očekává poskytování základní adresu, která je vhodná pro používané vazba schéma přenosu.</span><span class="sxs-lookup"><span data-stu-id="32a46-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="32a46-134">Pokud adresa není nakonfigurována, základní adresu se považuje za adresu pro tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="32a46-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="32a46-135">`contract` Atribut určuje kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="32a46-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="32a46-136">Typ implementace služby musí implementovat typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="32a46-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="32a46-137">Pokud implementace služby implementuje typu jeden kontrakt, můžete tuto vlastnost vynechat.</span><span class="sxs-lookup"><span data-stu-id="32a46-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="32a46-138">`binding` Atribut vybere předdefinované nebo vlastní vazby má použít pro tento konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="32a46-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="32a46-139">Koncový bod, který není explicitně vyberte vazbu používá výchozí výběr vazby, což je `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="32a46-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="32a46-140">Úprava předdefinované vazby</span><span class="sxs-lookup"><span data-stu-id="32a46-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="32a46-141">V následujícím příkladu je upravit vazbu předdefinované.</span><span class="sxs-lookup"><span data-stu-id="32a46-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="32a46-142">Ji pak slouží ke konfiguraci žádný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="32a46-143">Vazba je upravena podle nastavení <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> hodnotu na 1 sekundu.</span><span class="sxs-lookup"><span data-stu-id="32a46-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="32a46-144">Všimněte si, že vlastnost vrací <xref:System.TimeSpan> objektu.</span><span class="sxs-lookup"><span data-stu-id="32a46-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="32a46-145">Který změnit vazby naleznete v části vazby.</span><span class="sxs-lookup"><span data-stu-id="32a46-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="32a46-146">Změnit vazby lze nyní použít při vytváření žádný koncový bod, a to nastavením `binding` atribut `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="32a46-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32a46-147">Pokud přiřadíte konkrétní název pro vazba, `bindingConfiguration` zadané v rámci služby koncový bod se musí shodovat s ním.</span><span class="sxs-lookup"><span data-stu-id="32a46-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="32a46-148">Konfigurace chování chcete použít pro služby</span><span class="sxs-lookup"><span data-stu-id="32a46-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="32a46-149">V následujícím příkladu je konkrétní chování nakonfigurován pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="32a46-150">`ServiceMetadataBehavior` Element slouží k povolení [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zadat dotaz na službu a generovat webové služby popis Language (WSDL) dokumenty z metadat.</span><span class="sxs-lookup"><span data-stu-id="32a46-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32a46-151">Pokud přiřadíte konkrétní název v chování `behaviorConfiguration` zadaný v služba nebo koncový bod oddíl se musí shodovat se.</span><span class="sxs-lookup"><span data-stu-id="32a46-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />  
       </endpoint>  
    </service>  
</services>  
```  
  
 <span data-ttu-id="32a46-152">Předchozí konfigurace umožňuje klient volání a získat metadata "HelloWorld" zadali služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="32a46-153">Určení služby s dva koncové body pomocí hodnot jinou vazbou</span><span class="sxs-lookup"><span data-stu-id="32a46-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="32a46-154">V tomto příkladu poslední dva koncové body pro nakonfigurovaných `HelloWorld` typ služby.</span><span class="sxs-lookup"><span data-stu-id="32a46-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="32a46-155">Každý koncový bod používá jiné přizpůsobit `bindingConfiguration` atribut stejný typ vazby (každý upraví `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="32a46-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout"  
    </endpoint>  
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure"  
     </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
 <span data-ttu-id="32a46-156">Můžete získat pomocí výchozí konfigurace přidáním stejné chování `protocolMapping` části a konfiguraci vazby, jak je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32a46-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32a46-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="32a46-157">See Also</span></span>  
 [<span data-ttu-id="32a46-158">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="32a46-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="32a46-159">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="32a46-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="32a46-160">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="32a46-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="32a46-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="32a46-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
