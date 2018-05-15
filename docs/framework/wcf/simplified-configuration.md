---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 9f35a5f4fa4ae6be63bd75a24f58b56dd236ee9c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="simplified-configuration"></a><span data-ttu-id="5f785-102">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="5f785-102">Simplified Configuration</span></span>
<span data-ttu-id="5f785-103">Konfigurace služby Windows Communication Foundation (WCF) může být složité úlohy.</span><span class="sxs-lookup"><span data-stu-id="5f785-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="5f785-104">Existuje mnoho různých možností a není vždy snadno určit nastavení, které jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="5f785-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="5f785-105">Při konfiguraci souborů zvýšíte flexibilitu služby WCF, jsou také zdroj pro mnoho vyhledání problémů.</span><span class="sxs-lookup"><span data-stu-id="5f785-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="5f785-106"> řeší tyto problémy a poskytuje způsob, jak snížit velikost a složitost konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="5f785-106"> addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="5f785-107">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="5f785-107">Simplified Configuration</span></span>  
 <span data-ttu-id="5f785-108">V modulu snap-in soubory konfigurace služby WCF <`system.serviceModel`> obsahuje <`service`> element u každé služby hostované.</span><span class="sxs-lookup"><span data-stu-id="5f785-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="5f785-109"><`service`> Kolekce obsahuje element <`endpoint`> elementy, které určují koncové body vystavený pro každou službu a volitelně sadu chování služby.</span><span class="sxs-lookup"><span data-stu-id="5f785-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="5f785-110"><`endpoint`> Elementy zadejte adresy, vazby a kontraktu viditelné v koncovém bodě a volitelně Konfigurace vazeb a chování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5f785-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="5f785-111"><`system.serviceModel`> Obsahuje také <`behaviors`> elementu, který umožňuje zadat chování služba nebo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5f785-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="5f785-112">Následující příklad ukazuje <`system.serviceModel`> oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5f785-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="5f785-113"> Umožňuje konfiguraci služby WCF jednodušší odebráním požadavek <`service`> elementu.</span><span class="sxs-lookup"><span data-stu-id="5f785-113"> makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="5f785-114">Pokud nepřidáte <`service`> části nebo přidat žádné koncové body v <`service`> části a služby nedefinuje prostřednictvím kódu programu žádné koncové body a pak sadu výchozí koncové body se automaticky přidají do vaší služby, jeden pro každou Základní adresa služby a pro každou smlouvu implementované služby.</span><span class="sxs-lookup"><span data-stu-id="5f785-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="5f785-115">V každé z těchto koncových bodů adresa koncového bodu odpovídá bázové adresy, vazby je dáno schéma základní adresa a kontrakt je implementované vaše služba.</span><span class="sxs-lookup"><span data-stu-id="5f785-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="5f785-116">Pokud není potřeba žádné koncové body nebo chování služby a provedli změny nastavení vazby, není potřeba zadat konfigurační soubor služby vůbec.</span><span class="sxs-lookup"><span data-stu-id="5f785-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="5f785-117">Pokud služba implementuje dva kontrakty a hostitele povolí přenosy HTTP a TCP hostitele služby vytvoří čtyři výchozí koncové body, jeden pro každou smlouvu použití každé přenosu.</span><span class="sxs-lookup"><span data-stu-id="5f785-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="5f785-118">Chcete-li vytvořit výchozí koncové body hostitele služby musí znát které vazby použít.</span><span class="sxs-lookup"><span data-stu-id="5f785-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="5f785-119">Tato nastavení jsou určené v <`protocolMappings`> části v rámci <`system.serviceModel`> části.</span><span class="sxs-lookup"><span data-stu-id="5f785-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="5f785-120"><`protocolMappings`> Část obsahuje seznam přenosu protokolu schémata namapované na vazby typy.</span><span class="sxs-lookup"><span data-stu-id="5f785-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="5f785-121">Hostitel služby používá základní adresy do ní předán k určení které vazby použít.</span><span class="sxs-lookup"><span data-stu-id="5f785-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="5f785-122">Následující příklad používá <`protocolMappings`> elementu.</span><span class="sxs-lookup"><span data-stu-id="5f785-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5f785-123">Změna výchozí konfigurační prvky, jako je například vazby nebo chování, může ovlivnit služby definované v nižších úrovních hierarchie konfigurace, protože by mohly používat tyto výchozí vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="5f785-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="5f785-124">Proto, kdo změní výchozí vazby a chování je potřeba vědět, že tyto změny mohou ovlivnit jiných služeb v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="5f785-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f785-125">Služby hostované v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS) jako jejich základní adresa se použije virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5f785-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="5f785-126">V předchozím příkladu používá koncový bod s základní adresa, který začíná na "http" schématu <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5f785-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="5f785-127">Koncový bod s základní adresa, který začíná na "net.tcp" schématu používá <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5f785-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="5f785-128">Můžete přepsat nastavení v místním souboru App.config nebo Web.config.</span><span class="sxs-lookup"><span data-stu-id="5f785-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="5f785-129">Každý prvek v rámci <`protocolMappings`> části zadejte schéma a vazbu.</span><span class="sxs-lookup"><span data-stu-id="5f785-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="5f785-130">Volitelně můžete zadat `bindingConfiguration` atribut, který určuje vazby konfigurace v rámci <`bindings`> oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5f785-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="5f785-131">Pokud žádné `bindingConfiguration` je zadána, bude použita konfigurace anonymní vazba typu odpovídající vazby.</span><span class="sxs-lookup"><span data-stu-id="5f785-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="5f785-132">Chování služby jsou nakonfigurovány pro jsou výchozí koncové body pomocí anonymní <`behavior`> částech v rámci <`serviceBehaviors`> oddíly.</span><span class="sxs-lookup"><span data-stu-id="5f785-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="5f785-133">Všechny nepojmenované <`behavior`> elementů v rámci <`serviceBehaviors`> se používají ke konfiguraci chování služby.</span><span class="sxs-lookup"><span data-stu-id="5f785-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="5f785-134">Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.</span><span class="sxs-lookup"><span data-stu-id="5f785-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="5f785-135">Koncový bod chování se konfigurují pomocí anonymní <`behavior`> částech v rámci <`serviceBehaviors`> oddíly.</span><span class="sxs-lookup"><span data-stu-id="5f785-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="5f785-136">Následující příklad je ekvivalentní jeden na začátku tohoto tématu, která používá zjednodušené konfigurační model konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5f785-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f785-137">Tato funkce se týká pouze konfigurace služby WCF, není konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="5f785-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="5f785-138">Většina dobu konfigurace klienta WCF se budou generovat pomocí nástroje, jako je svcutil.exe nebo přidání odkazu na službu ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f785-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="5f785-139">Pokud ručně nakonfigurujete klienta WCF budete muset přidat \<klienta > element ke konfiguraci a zadejte žádné koncové body, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="5f785-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f785-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f785-140">See Also</span></span>  
 [<span data-ttu-id="5f785-141">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="5f785-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="5f785-142">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="5f785-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="5f785-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5f785-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5f785-144">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="5f785-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="5f785-145">Konfigurace aplikací pro Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5f785-145">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="5f785-146">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="5f785-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
