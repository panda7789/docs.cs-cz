---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 52f93acacec434ce6f7ba93678615c104aa94b24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704040"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="19e8a-102">Konfigurace vazeb pro služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="19e8a-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="19e8a-103">Při vytváření aplikace, často chcete odložit rozhodnutí, která správci po nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="19e8a-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="19e8a-104">Například není často předem vědět, co adresu služby, nebo identifikátor URI (Uniform Resource), budou.</span><span class="sxs-lookup"><span data-stu-id="19e8a-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="19e8a-105">Místo pevného kódování adresu, je vhodnější umožňují správcům udělat po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="19e8a-106">Díky této flexibilitě se provádí prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="19e8a-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e8a-107">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config` přepínač tak, aby rychle vytvořit konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="19e8a-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="19e8a-108">Major Sections</span><span class="sxs-lookup"><span data-stu-id="19e8a-108">Major Sections</span></span>  
 <span data-ttu-id="19e8a-109">Schéma konfigurace Windows Communication Foundation (WCF) zahrnuje následující tři hlavní části (`serviceModel`, `bindings`, a `services`):</span><span class="sxs-lookup"><span data-stu-id="19e8a-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="19e8a-110">Prvky ServiceModel</span><span class="sxs-lookup"><span data-stu-id="19e8a-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="19e8a-111">Můžete použít části ohraničené `system.ServiceModel` element konfigurace typu služby pomocí jednoho nebo víc koncových bodů, nastavení služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="19e8a-112">Každý koncový bod může být nakonfigurována s adresou, kontrakt a vazby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="19e8a-113">Další informace o koncových bodech najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="19e8a-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="19e8a-114">Pokud nejsou zadány žádné koncové body, modulu runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="19e8a-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="19e8a-115">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="19e8a-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="19e8a-116">Vazbu určuje přenosy (HTTP, TCP, kanály, služby Řízení front zpráv) a protokoly (zabezpečení, spolehlivost, transakce toky) a skládá se z elementů, z nichž každý Určuje určitý aspekt jak koncový bod komunikuje s ostatními vazby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="19e8a-117">Například zadání [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) určuje element na používání protokolu HTTP jako přenosu pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="19e8a-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="19e8a-118">To se používá k přenosu do koncového bodu v době běhu, když se otevře pomocí tohoto koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="19e8a-119">Existují dva typy vazeb: předdefinované a vlastní.</span><span class="sxs-lookup"><span data-stu-id="19e8a-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="19e8a-120">Předdefinovaných vazeb obsahují užitečné kombinaci prvků, které se používají v běžné scénáře.</span><span class="sxs-lookup"><span data-stu-id="19e8a-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="19e8a-121">Seznam typů předdefinovaných vazeb, které poskytuje WCF najdete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="19e8a-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="19e8a-122">Pokud žádná vazba předdefinované kolekce nemá správnou kombinaci funkcí, které musí aplikace služby, můžete vytvořit vlastní vazby pro splnění požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="19e8a-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="19e8a-123">Další informace o vlastních vazeb naleznete v tématu [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="19e8a-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="19e8a-124">Následující čtyři příklady ilustrují nejběžnější konfigurace vazby používá pro nastavení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="19e8a-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="19e8a-125">Zadání koncového bodu používat typ vazby</span><span class="sxs-lookup"><span data-stu-id="19e8a-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="19e8a-126">První příklad ukazuje, jak zadat koncový bod nakonfigurovaný s adresou, kontrakt a vazby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="19e8a-127">V tomto příkladu `name` atribut označuje, jaký typ služby, je konfigurace pro.</span><span class="sxs-lookup"><span data-stu-id="19e8a-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="19e8a-128">Při vytváření služby v kódu s `HelloWorld` smlouvy, je inicializována s všechny koncové body definované v konfiguraci příklad.</span><span class="sxs-lookup"><span data-stu-id="19e8a-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="19e8a-129">Pokud sestavení implementuje pouze jeden kontrakt služby `name` atribut lze vynechat, protože služba využívá typ pouze k dispozici.</span><span class="sxs-lookup"><span data-stu-id="19e8a-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="19e8a-130">Atribut přijímá řetězec, který musí být ve formátu `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="19e8a-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="19e8a-131">`address` Atribut určuje identifikátor URI, který ostatní koncové body používat pro komunikaci ve službě.</span><span class="sxs-lookup"><span data-stu-id="19e8a-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="19e8a-132">Identifikátor URI může být absolutní nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="19e8a-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="19e8a-133">Pokud je zadána relativní adresa, hostitel se očekává poskytování základní adresa, která je vhodná pro schéma přepravy používá ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="19e8a-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="19e8a-134">Pokud není konfigurována adresa, základní adresa je považován za adresu pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="19e8a-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="19e8a-135">`contract` Atribut určuje kontrakt tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="19e8a-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="19e8a-136">Typ implementace služby musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="19e8a-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="19e8a-137">Pokud implementace služby implementuje typ jeden kontrakt, lze tuto vlastnost vynechat.</span><span class="sxs-lookup"><span data-stu-id="19e8a-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="19e8a-138">`binding` Atribut vybere předdefinovaných nebo vlastních vazbu pro tento konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="19e8a-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="19e8a-139">Koncový bod, který není explicitně zvolená vazby používá vazbu výchozí výběr, který je `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="19e8a-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="19e8a-140">Úprava předdefinovaných vazeb</span><span class="sxs-lookup"><span data-stu-id="19e8a-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="19e8a-141">V následujícím příkladu je upraven předdefinované vazby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="19e8a-142">Ji pak slouží ke konfiguraci libovolný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="19e8a-143">Vazba je upravit tak, že nastavíte <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> hodnotu na 1 sekundu.</span><span class="sxs-lookup"><span data-stu-id="19e8a-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="19e8a-144">Všimněte si, že vlastnost vrací <xref:System.TimeSpan> objektu.</span><span class="sxs-lookup"><span data-stu-id="19e8a-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="19e8a-145">Který změnit vazby najdete v části vazeb.</span><span class="sxs-lookup"><span data-stu-id="19e8a-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="19e8a-146">To změnit vazby se teď dá při vytváření libovolný koncový bod tak, že nastavíte `binding` atribut `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="19e8a-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e8a-147">Pokud dáte konkrétní název vazby, `bindingConfiguration` zadaný ve službě koncový bod se musí shodovat s ním.</span><span class="sxs-lookup"><span data-stu-id="19e8a-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="19e8a-148">Konfigurace chování má použít pro služby</span><span class="sxs-lookup"><span data-stu-id="19e8a-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="19e8a-149">V následujícím příkladu je nakonfigurované konkrétní chování pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="19e8a-150">`ServiceMetadataBehavior` Element slouží k povolení [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k dotazování na službu a generovat webové služby WSDL (Description Language) dokumenty z metadat.</span><span class="sxs-lookup"><span data-stu-id="19e8a-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e8a-151">Pokud musíte pojmenovat konkrétní chování, `behaviorConfiguration` podle služba nebo koncový bod oddílu odpovídat.</span><span class="sxs-lookup"><span data-stu-id="19e8a-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="19e8a-152">Předchozí konfigurace umožňuje klient volat a získat metadata "HelloWorld" typu služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="19e8a-153">Určení služby pomocí dva koncové body pomocí hodnoty jinou vazbou</span><span class="sxs-lookup"><span data-stu-id="19e8a-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="19e8a-154">V tomto příkladu poslední dva koncové body se konfigurují pro `HelloWorld` typ služby.</span><span class="sxs-lookup"><span data-stu-id="19e8a-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="19e8a-155">Každý koncový bod používá jiný přizpůsobit `bindingConfiguration` atribut stejný typ vazby (každý upraví `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="19e8a-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="19e8a-156">Můžete získat stejné chování pomocí výchozí konfigurace tak, že přidáte `protocolMapping` oddílu a konfigurace vazby, jak je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="19e8a-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19e8a-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19e8a-157">See also</span></span>
- [<span data-ttu-id="19e8a-158">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="19e8a-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="19e8a-159">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="19e8a-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="19e8a-160">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="19e8a-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="19e8a-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="19e8a-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
