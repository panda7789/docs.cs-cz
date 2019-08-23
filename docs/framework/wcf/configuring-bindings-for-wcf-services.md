---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: bfcdcd172d96660c3351926a9c42d298ac3fa654
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928564"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="175ea-102">Konfigurace vazeb pro služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="175ea-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="175ea-103">Při vytváření aplikace často chcete po nasazení aplikace odložit rozhodnutí správci.</span><span class="sxs-lookup"><span data-stu-id="175ea-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="175ea-104">Například neexistuje žádný způsob, jak si předem zjistit, jakou adresu služby nebo identifikátor URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="175ea-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="175ea-105">Místo hardwarového zakódování adresy je vhodnější dát správcům po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="175ea-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="175ea-106">Tato flexibilita je zajištěna prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="175ea-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="175ea-107">K rychlému vytvoření konfiguračních souborů použijte nástroj pro dodané [metadata (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config` přepínačem.</span><span class="sxs-lookup"><span data-stu-id="175ea-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="175ea-108">Hlavní oddíly</span><span class="sxs-lookup"><span data-stu-id="175ea-108">Major Sections</span></span>  
 <span data-ttu-id="175ea-109">Schéma konfigurace Windows Communication Foundation (WCF) obsahuje následující tři hlavní oddíly (`serviceModel`, `bindings` `services`a):</span><span class="sxs-lookup"><span data-stu-id="175ea-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="175ea-110">ServiceModel – prvky</span><span class="sxs-lookup"><span data-stu-id="175ea-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="175ea-111">Můžete použít oddíl ohraničený `system.ServiceModel` prvkem ke konfiguraci typu služby s jedním nebo více koncovými body a také s nastavením pro službu.</span><span class="sxs-lookup"><span data-stu-id="175ea-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="175ea-112">U každého koncového bodu se pak dá nakonfigurovat adresa, kontrakt a vazba.</span><span class="sxs-lookup"><span data-stu-id="175ea-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="175ea-113">Další informace o koncových bodech najdete v tématu [Přehled vytváření koncových](../../../docs/framework/wcf/endpoint-creation-overview.md)bodů.</span><span class="sxs-lookup"><span data-stu-id="175ea-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="175ea-114">Pokud nejsou zadány žádné koncové body, modul runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="175ea-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="175ea-115">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="175ea-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="175ea-116">Vazba určuje přenosy (HTTP, TCP, kanály, řízení front zpráv) a protokoly (zabezpečení, spolehlivost, toky transakcí) a skládá se z elementů vazby, z nichž každý určuje aspekt způsobu komunikace koncového bodu s celým světem.</span><span class="sxs-lookup"><span data-stu-id="175ea-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="175ea-117">Například určení prvku [ \<BasicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) označuje, že se má jako přenos pro koncový bod používat protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="175ea-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="175ea-118">Tento postup se používá k navýšení koncového bodu v době běhu, kdy je otevřená služba používající tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="175ea-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="175ea-119">Existují dva druhy vazeb: předdefinované a vlastní.</span><span class="sxs-lookup"><span data-stu-id="175ea-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="175ea-120">Předdefinované vazby obsahují užitečné kombinace prvků, které se používají v běžných scénářích.</span><span class="sxs-lookup"><span data-stu-id="175ea-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="175ea-121">Seznam předdefinovaných typů vazeb, které poskytuje WCF, najdete v tématu [vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="175ea-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="175ea-122">Pokud žádná předdefinovaná kolekce vazeb nemá správnou kombinaci funkcí, které potřebuje aplikace služby, můžete vytvořit vlastní vazby, které splňují požadavky aplikace.</span><span class="sxs-lookup"><span data-stu-id="175ea-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="175ea-123">Další informace o vlastních vazbách naleznete v tématu [ \<CustomBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="175ea-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="175ea-124">Následující čtyři příklady ilustrují nejběžnější konfigurace vazeb používané pro nastavení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="175ea-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="175ea-125">Zadání koncového bodu pro použití typu vazby</span><span class="sxs-lookup"><span data-stu-id="175ea-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="175ea-126">První příklad ukazuje, jak zadat koncový bod nakonfigurovaný s adresou, kontraktem a vazbou.</span><span class="sxs-lookup"><span data-stu-id="175ea-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="175ea-127">V tomto příkladu `name` atribut označuje, pro který typ služby se konfigurace používá.</span><span class="sxs-lookup"><span data-stu-id="175ea-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="175ea-128">Když ve svém kódu vytvoříte službu s `HelloWorld` kontraktem, inicializuje se se všemi koncovými body definovanými v ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="175ea-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="175ea-129">Pokud sestavení implementuje pouze jeden kontrakt služby, může být `name` atribut vynechán, protože služba používá pouze dostupný typ.</span><span class="sxs-lookup"><span data-stu-id="175ea-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="175ea-130">Atribut přebírá řetězec, který musí být ve formátu`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="175ea-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="175ea-131">`address` Atribut určuje identifikátor URI, který používají jiné koncové body ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="175ea-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="175ea-132">Identifikátor URI může být buď absolutní, nebo relativní cesta.</span><span class="sxs-lookup"><span data-stu-id="175ea-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="175ea-133">Pokud je zadána relativní adresa, očekává se, že hostitel poskytne základní adresu, která je vhodná pro přenosové schéma používané ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="175ea-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="175ea-134">Pokud není adresa nakonfigurovaná, předpokládá se, že základní adresa je adresa pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="175ea-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="175ea-135">`contract` Atribut určuje kontrakt, který tento koncový bod zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="175ea-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="175ea-136">Typ implementace služby musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="175ea-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="175ea-137">Pokud implementace služby implementuje jeden typ kontraktu, může být tato vlastnost vynechána.</span><span class="sxs-lookup"><span data-stu-id="175ea-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="175ea-138">`binding` Atribut vybere předdefinovanou nebo vlastní vazbu, která se má použít pro tento konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="175ea-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="175ea-139">Koncový bod, který explicitně nevybere vazbu, používá výchozí výběr vazby, který je `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="175ea-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="175ea-140">Úprava předdefinované vazby</span><span class="sxs-lookup"><span data-stu-id="175ea-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="175ea-141">V následujícím příkladu je upravena předdefinovaná vazba.</span><span class="sxs-lookup"><span data-stu-id="175ea-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="175ea-142">Pak ji můžete použít ke konfiguraci libovolného koncového bodu ve službě.</span><span class="sxs-lookup"><span data-stu-id="175ea-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="175ea-143">Vazba je upravena nastavením <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> hodnoty na 1 sekundu.</span><span class="sxs-lookup"><span data-stu-id="175ea-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="175ea-144">Všimněte si, že vlastnost vrací <xref:System.TimeSpan> objekt.</span><span class="sxs-lookup"><span data-stu-id="175ea-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="175ea-145">Změněné vazby najdete v části Bindings.</span><span class="sxs-lookup"><span data-stu-id="175ea-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="175ea-146">Tato změněná vazba se teď dá použít při vytváření libovolného koncového bodu `binding` nastavením atributu `endpoint` v elementu.</span><span class="sxs-lookup"><span data-stu-id="175ea-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="175ea-147">Pokud k vazbě přiřadíte konkrétní název, `bindingConfiguration` musí být zadaná v koncovém bodu služby shodná s ní.</span><span class="sxs-lookup"><span data-stu-id="175ea-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="175ea-148">Konfigurace chování, které se má použít u služby</span><span class="sxs-lookup"><span data-stu-id="175ea-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="175ea-149">V následujícím příkladu je pro typ služby nakonfigurováno konkrétní chování.</span><span class="sxs-lookup"><span data-stu-id="175ea-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="175ea-150">Element slouží k povolení nástroje pro doSvcutilení [metadat (ServiceModel. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k dotazování služby a generování dokumentů jazyka WSDL (Web Services Description Language) z metadat. `ServiceMetadataBehavior`</span><span class="sxs-lookup"><span data-stu-id="175ea-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="175ea-151">Pokud tomuto chování udělíte konkrétní název, `behaviorConfiguration` musí být zadaný v oddílu služba nebo koncový bod odpovídat.</span><span class="sxs-lookup"><span data-stu-id="175ea-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="175ea-152">Předchozí konfigurace umožňuje klientovi volat a získat metadata služby typovaného typu HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="175ea-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="175ea-153">Určení služby se dvěma koncovými body pomocí různých hodnot vazeb</span><span class="sxs-lookup"><span data-stu-id="175ea-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="175ea-154">V tomto posledním příkladu jsou pro `HelloWorld` typ služby nakonfigurovány dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="175ea-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="175ea-155">Každý koncový bod používá jiný přizpůsobený `bindingConfiguration` atribut stejného typu vazby (každý z `basicHttpBinding`nich upravuje).</span><span class="sxs-lookup"><span data-stu-id="175ea-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="175ea-156">Stejné chování můžete získat pomocí výchozí konfigurace přidáním `protocolMapping` oddílu a konfigurací vazeb, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="175ea-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="175ea-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="175ea-157">See also</span></span>

- [<span data-ttu-id="175ea-158">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="175ea-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="175ea-159">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="175ea-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="175ea-160">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="175ea-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="175ea-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="175ea-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
