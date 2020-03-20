---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174820"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="54efc-102">Konfigurace vazeb pro služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="54efc-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="54efc-103">Při vytváření aplikace, často chcete odložit rozhodnutí správce po nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="54efc-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="54efc-104">Například často neexistuje žádný způsob, jak předem zjistit, jaká bude adresa služby nebo identifikátor URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="54efc-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="54efc-105">Místo pevného kódování adresy je vhodnější povolit správci, aby tak učinil po vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="54efc-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="54efc-106">Tato flexibilita se provádí prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="54efc-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54efc-107">Pomocí [nástroje ServiceModel Metadata Utility Tool Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) s přepínačem `/config` můžete rychle vytvářet konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="54efc-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="54efc-108">Hlavní sekce</span><span class="sxs-lookup"><span data-stu-id="54efc-108">Major Sections</span></span>  
 <span data-ttu-id="54efc-109">Schéma konfigurace Windows Communication Foundation (WCF) zahrnuje`serviceModel`následující `bindings`tři `services`hlavní oddíly ( , , a ):</span><span class="sxs-lookup"><span data-stu-id="54efc-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="54efc-110">Prvky modelu service</span><span class="sxs-lookup"><span data-stu-id="54efc-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="54efc-111">Oddíl ohraničený elementem `system.ServiceModel` můžete použít ke konfiguraci typu služby s jedním nebo více koncovými body a také nastavením služby.</span><span class="sxs-lookup"><span data-stu-id="54efc-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="54efc-112">Každý koncový bod pak lze nakonfigurovat s adresou, smlouvy a vazby.</span><span class="sxs-lookup"><span data-stu-id="54efc-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="54efc-113">Další informace o koncových bodech naleznete v [tématu Přehled vytváření koncových bodů](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="54efc-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="54efc-114">Pokud nejsou zadány žádné koncové body, runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="54efc-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="54efc-115">Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="54efc-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="54efc-116">Vazba určuje přenosy (HTTP, TCP, kanály, řízení front zpráv) a protokoly (zabezpečení, spolehlivost, toky transakcí) a skládá se z elementů vazby, z nichž každý určuje aspekt způsobu komunikace koncového bodu se světem.</span><span class="sxs-lookup"><span data-stu-id="54efc-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="54efc-117">Například zadání [ \<elementu basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) označuje použití protokolu HTTP jako přenosu pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="54efc-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="54efc-118">Používá se k drátu koncového bodu v době běhu při otevření služby pomocí tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="54efc-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="54efc-119">Existují dva druhy vazeb: předdefinované a vlastní.</span><span class="sxs-lookup"><span data-stu-id="54efc-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="54efc-120">Předdefinované vazby obsahují užitečné kombinace prvků, které se používají v běžných scénářích.</span><span class="sxs-lookup"><span data-stu-id="54efc-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="54efc-121">Seznam předdefinovaných typů vazeb, které poskytuje WCF, naleznete v [tématu Vazby poskytované systémem](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="54efc-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="54efc-122">Pokud žádná předdefinovaná kolekce vazeb má správnou kombinaci funkcí, které aplikace služby potřebuje, můžete vytvořit vlastní vazby tak, aby splňovaly požadavky aplikace.</span><span class="sxs-lookup"><span data-stu-id="54efc-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="54efc-123">Další informace o vlastní vazby naleznete [ \<v tématu customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="54efc-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="54efc-124">Následující čtyři příklady ilustrují nejběžnější konfigurace vazby používané pro nastavení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="54efc-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="54efc-125">Určení koncového bodu pro použití typu vazby</span><span class="sxs-lookup"><span data-stu-id="54efc-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="54efc-126">První příklad ukazuje, jak určit koncový bod nakonfigurovaný s adresou, smlouvou a vazbou.</span><span class="sxs-lookup"><span data-stu-id="54efc-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="54efc-127">V tomto příkladu `name` atribut označuje, pro který typ služby je konfigurace.</span><span class="sxs-lookup"><span data-stu-id="54efc-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="54efc-128">Když vytvoříte službu v `HelloWorld` kódu se smlouvou, je inicializována se všemi koncovými body definovanými v konfiguraci příkladu.</span><span class="sxs-lookup"><span data-stu-id="54efc-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="54efc-129">Pokud sestavení implementuje pouze jednu servisní smlouvu, `name` atribut lze vynechat, protože služba používá pouze dostupný typ.</span><span class="sxs-lookup"><span data-stu-id="54efc-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="54efc-130">Atribut přebírá řetězec, který musí být ve formátu`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="54efc-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="54efc-131">Atribut `address` určuje identifikátor URI, který ostatní koncové body používají ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="54efc-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="54efc-132">Identifikátor URI může být absolutní nebo relativní cesta.</span><span class="sxs-lookup"><span data-stu-id="54efc-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="54efc-133">Pokud je k dispozici relativní adresa, očekává se, že hostitel poskytne základní adresu, která je vhodná pro schéma přenosu použité ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="54efc-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="54efc-134">Pokud adresa není nakonfigurována, předpokládá se, že základní adresa je adresa pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="54efc-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="54efc-135">Atribut `contract` určuje kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="54efc-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="54efc-136">Typ implementace služby musí implementovat typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="54efc-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="54efc-137">Pokud implementace služby implementuje jeden typ smlouvy, pak tuto vlastnost lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="54efc-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="54efc-138">Atribut `binding` vybere předdefinovanou nebo vlastní vazbu, která se použije pro tento konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="54efc-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="54efc-139">Koncový bod, který explicitně nevybere vazbu, používá `BasicHttpBinding`výchozí výběr vazby, což je .</span><span class="sxs-lookup"><span data-stu-id="54efc-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="54efc-140">Úprava předdefinované vazby</span><span class="sxs-lookup"><span data-stu-id="54efc-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="54efc-141">V následujícím příkladu je změněna předdefinovaná vazba.</span><span class="sxs-lookup"><span data-stu-id="54efc-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="54efc-142">Potom lze nakonfigurovat libovolný koncový bod ve službě.</span><span class="sxs-lookup"><span data-stu-id="54efc-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="54efc-143">Vazba je změněna <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> nastavením hodnoty na 1 sekundu.</span><span class="sxs-lookup"><span data-stu-id="54efc-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="54efc-144">Všimněte si, <xref:System.TimeSpan> že vlastnost vrátí objekt.</span><span class="sxs-lookup"><span data-stu-id="54efc-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="54efc-145">Tato změněná vazba se nachází v části vazby.</span><span class="sxs-lookup"><span data-stu-id="54efc-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="54efc-146">Tuto změněnou vazbu lze nyní použít při `binding` vytváření libovolného koncového bodu nastavením atributu `endpoint` v prvku.</span><span class="sxs-lookup"><span data-stu-id="54efc-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54efc-147">Pokud zadáváte určitý název vazby, `bindingConfiguration` zadaný v koncovém bodu služby musí odpovídat s ním.</span><span class="sxs-lookup"><span data-stu-id="54efc-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="54efc-148">Konfigurace chování, které se má použít u služby</span><span class="sxs-lookup"><span data-stu-id="54efc-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="54efc-149">V následujícím příkladu je pro typ služby nakonfigurováno určité chování.</span><span class="sxs-lookup"><span data-stu-id="54efc-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="54efc-150">Prvek `ServiceMetadataBehavior` se používá k povolení [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) k dotazování služby a generování webových služeb Description Language (WSDL) dokumenty z metadat.</span><span class="sxs-lookup"><span data-stu-id="54efc-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54efc-151">Pokud přidáváte určitý název chování, `behaviorConfiguration` zadaný v části služby nebo koncového bodu musí odpovídat.</span><span class="sxs-lookup"><span data-stu-id="54efc-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="54efc-152">Předchozí konfigurace umožňuje klientovi volat a získat metadata služby "HelloWorld" zadali.</span><span class="sxs-lookup"><span data-stu-id="54efc-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="54efc-153">Určení služby se dvěma koncovými body pomocí různých hodnot vazby</span><span class="sxs-lookup"><span data-stu-id="54efc-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="54efc-154">V tomto posledním příkladu jsou pro `HelloWorld` typ služby nakonfigurovány dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="54efc-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="54efc-155">Každý koncový bod používá `bindingConfiguration` jiný přizpůsobený atribut stejného typu vazby (každý upravuje `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="54efc-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="54efc-156">Stejné chování pomocí výchozí konfigurace můžete získat `protocolMapping` přidáním oddílu a konfigurací vazeb, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="54efc-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54efc-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="54efc-157">See also</span></span>

- [<span data-ttu-id="54efc-158">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="54efc-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="54efc-159">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="54efc-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="54efc-160">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="54efc-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="54efc-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="54efc-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
