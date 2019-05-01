---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967892"
---
# <a name="simplified-configuration"></a><span data-ttu-id="a9779-102">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="a9779-102">Simplified Configuration</span></span>
<span data-ttu-id="a9779-103">Konfigurace služby Windows Communication Foundation (WCF) může být složitý úkol.</span><span class="sxs-lookup"><span data-stu-id="a9779-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="a9779-104">Spousta různých možností, a to není vždy jednoduché určit nastavení, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="a9779-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="a9779-105">Konfigurační soubory zvýšit flexibilitu služeb WCF, ale také jsou zdroje pro mnoho obtížné najít problémy.</span><span class="sxs-lookup"><span data-stu-id="a9779-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a9779-106">řeší tyto problémy a poskytuje způsob, jak zmenšit velikost a složitost konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="a9779-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="a9779-107">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="a9779-107">Simplified Configuration</span></span>  
 <span data-ttu-id="a9779-108">V souborech konfigurace služby WCF <`system.serviceModel`> obsahuje oddíl <`service`> – element pro každé služby hostované.</span><span class="sxs-lookup"><span data-stu-id="a9779-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="a9779-109"><`service`> Kolekce obsahuje element <`endpoint`> elementy, které určují koncových bodů pro každou službu a volitelně také sadu chování služby.</span><span class="sxs-lookup"><span data-stu-id="a9779-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="a9779-110"><`endpoint`> Elementy zadejte adresy, vazby a kontrakt vystavit koncový bod a volitelně konfigurace vazby a chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a9779-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="a9779-111"><`system.serviceModel`> Obsahuje také <`behaviors`> element, který vám umožní určit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a9779-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="a9779-112">Následující příklad ukazuje <`system.serviceModel`> oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a9779-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="a9779-113">Díky konfigurace služby WCF jednodušší odebráním požadavek <`service`> element.</span><span class="sxs-lookup"><span data-stu-id="a9779-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="a9779-114">Pokud nepřidáte <`service`> části nebo přidat žádné koncové body v <`service`> části a vaše služba nedefinuje programově žádné koncové body a pak sadu výchozí koncové body jsou automaticky přidány do vaší služby, jeden pro každou Základní adresa služby a pro každou smlouvu implementované vaší služby.</span><span class="sxs-lookup"><span data-stu-id="a9779-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="a9779-115">V každém z těchto koncových bodů adresu koncového bodu odpovídá základní adresa, vazba se určuje podle schématu základní adresu a kontrakt je implementované vaše služba.</span><span class="sxs-lookup"><span data-stu-id="a9779-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="a9779-116">Pokud není potřeba zadat všechny koncové body nebo chování služby nebo provést změny nastavení vazby, není potřeba zadat konfigurační soubor služby vůbec.</span><span class="sxs-lookup"><span data-stu-id="a9779-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="a9779-117">Pokud služba implementuje dva kontrakty a hostitele umožňuje přenosy HTTP i protokol TCP hostitele služby vytvoří čtyři výchozí koncové body, jeden pro každou smlouvu pomocí jednotlivých přenosu.</span><span class="sxs-lookup"><span data-stu-id="a9779-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="a9779-118">Vytvořit výchozí koncové body hostitele služby musíte vědět, jaké vazby použít.</span><span class="sxs-lookup"><span data-stu-id="a9779-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="a9779-119">Tato nastavení jsou určené v <`protocolMappings`> části v rámci <`system.serviceModel`> oddílu.</span><span class="sxs-lookup"><span data-stu-id="a9779-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="a9779-120"><`protocolMappings`> Oddíl obsahuje seznam z namapované na typů vazeb schématy přenosových protokolů.</span><span class="sxs-lookup"><span data-stu-id="a9779-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="a9779-121">Hostitel služby používá základní adresy do něho předaný k určení použité vazby.</span><span class="sxs-lookup"><span data-stu-id="a9779-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="a9779-122">V následujícím příkladu <`protocolMappings`> element.</span><span class="sxs-lookup"><span data-stu-id="a9779-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a9779-123">Změna výchozí konfigurační prvky, jako je například vazby nebo chování, může mít vliv na služby definované v nižších úrovních hierarchie konfigurace, protože by mohly používat tyto výchozí vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="a9779-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="a9779-124">Tím, kdo mění výchozí vazby a chování musí mějte na paměti, že tyto změny mohou ovlivnit ostatní služby v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="a9779-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9779-125">Služby hostované v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS) použít virtuální adresář jako svoje základní adresa.</span><span class="sxs-lookup"><span data-stu-id="a9779-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="a9779-126">V předchozím příkladu používá koncový bod s základní adresa, která začíná textem "http" schéma <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a9779-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="a9779-127">Koncový bod s základní adresa, která začíná textem "net.tcp" schéma používá <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a9779-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="a9779-128">Můžete přepsat nastavení v místním souboru App.config nebo Web.config.</span><span class="sxs-lookup"><span data-stu-id="a9779-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="a9779-129">Každý prvek v rámci <`protocolMappings`> části musíte zadat schéma a vazbu.</span><span class="sxs-lookup"><span data-stu-id="a9779-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="a9779-130">Volitelně můžete zadat `bindingConfiguration` atribut, který určuje konfiguraci vazby v rámci <`bindings`> oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a9779-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="a9779-131">Pokud ne `bindingConfiguration` není zadána, bude použita konfigurace anonymní vytváření vazby typu odpovídající vazby.</span><span class="sxs-lookup"><span data-stu-id="a9779-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="a9779-132">Chování služby se konfigurují pro výchozí koncové body pomocí anonymní <`behavior`> v rámci oddílu <`serviceBehaviors`> oddíly.</span><span class="sxs-lookup"><span data-stu-id="a9779-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="a9779-133">Žádné nepojmenované <`behavior`> elementů v rámci <`serviceBehaviors`> se používají ke konfiguraci chování služby.</span><span class="sxs-lookup"><span data-stu-id="a9779-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="a9779-134">Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9779-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="a9779-135">Chování koncového bodu se konfigurují přes anonymní <`behavior`> v rámci oddílu <`serviceBehaviors`> oddíly.</span><span class="sxs-lookup"><span data-stu-id="a9779-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="a9779-136">Následující příklad je ekvivalentní je na začátku tohoto tématu, který používá zjednodušené konfigurační model konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a9779-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9779-137">Tato funkce se týká pouze konfigurace služby WCF, není konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="a9779-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="a9779-138">Většinu času konfigurace klienta WCF se vygeneruje pomocí nástroje, jako je svcutil.exe nebo přidáním odkazu na službu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9779-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="a9779-139">Při ruční konfiguraci klienta WCF je potřeba přidat \<klienta > element konfigurace a určete žádné koncové body, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="a9779-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9779-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9779-140">See also</span></span>

- [<span data-ttu-id="a9779-141">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="a9779-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="a9779-142">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="a9779-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="a9779-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a9779-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a9779-144">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="a9779-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="a9779-145">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="a9779-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="a9779-146">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="a9779-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
