---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249627"
---
# <a name="simplified-configuration"></a><span data-ttu-id="59610-102">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="59610-102">Simplified Configuration</span></span>
<span data-ttu-id="59610-103">Konfigurace služeb Windows Communication Foundation (WCF) může být složitý úkol.</span><span class="sxs-lookup"><span data-stu-id="59610-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="59610-104">Existuje mnoho různých možností a není vždy snadné určit, jaká nastavení jsou požadována.</span><span class="sxs-lookup"><span data-stu-id="59610-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="59610-105">Zatímco konfigurační soubory zvyšují flexibilitu služeb WCF, jsou také zdrojem pro mnoho problémů, které se těžko nacházejí.</span><span class="sxs-lookup"><span data-stu-id="59610-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="59610-106">řeší tyto problémy a poskytuje způsob, jak snížit velikost a složitost konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="59610-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="59610-107">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="59610-107">Simplified Configuration</span></span>  
 <span data-ttu-id="59610-108">V konfiguračních souborech služby WCF obsahuje část> služby <`system.serviceModel` <prvek> <`service` pro každou hostovanci služby.</span><span class="sxs-lookup"><span data-stu-id="59610-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="59610-109">Prvek `service` <> obsahuje kolekci <`endpoint`> prvků, které určují koncové body vystavené pro každou službu a volitelně sadu chování služby.</span><span class="sxs-lookup"><span data-stu-id="59610-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="59610-110"><`endpoint`> prvky určují adresu, vazbu a kontrakt vystavený koncovým bodem a volitelně vazby konfigurace a chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="59610-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="59610-111">Oddíl `system.serviceModel` <> obsahuje `behaviors` také prvek <>, který umožňuje určit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="59610-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="59610-112">Následující příklad ukazuje `system.serviceModel` <> části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="59610-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="59610-113">usnadňuje konfiguraci služby WCF odebráním požadavku `service` na <> element.</span><span class="sxs-lookup"><span data-stu-id="59610-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="59610-114">Pokud nepřidáte oddíl `service` <> nebo nepřidáte žádné `service` koncové body v <> části a vaše služba programově nedefinuje žádné koncové body, bude do vaší služby automaticky přidána sada výchozích koncových bodů, jeden pro každou adresu základny služeb a pro každou smlouvu implementovanou vaší službou.</span><span class="sxs-lookup"><span data-stu-id="59610-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="59610-115">V každém z těchto koncových bodů adresa koncového bodu odpovídá základní adrese, vazba je určena schématem základní adresy a smlouva je ta implementovaná vaší službou.</span><span class="sxs-lookup"><span data-stu-id="59610-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="59610-116">Pokud není nutné zadat žádné koncové body nebo chování služby nebo provádět změny nastavení vazby, není nutné zadat konfigurační soubor služby vůbec.</span><span class="sxs-lookup"><span data-stu-id="59610-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="59610-117">Pokud služba implementuje dvě smlouvy a hostitel umožňuje přenosy HTTP i TCP, hostitel služby vytvoří čtyři výchozí koncové body, jeden pro každou smlouvu pomocí každého přenosu.</span><span class="sxs-lookup"><span data-stu-id="59610-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="59610-118">Chcete-li vytvořit výchozí koncové body, musí hostitel služby vědět, jaké vazby se mají použít.</span><span class="sxs-lookup"><span data-stu-id="59610-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="59610-119">Tato nastavení jsou určena `protocolMappings` v oddílu `system.serviceModel` <> v části <>.</span><span class="sxs-lookup"><span data-stu-id="59610-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="59610-120"><`protocolMappings`> část obsahuje seznam schémat protokolu přenosu mapovaných na typy vazeb.</span><span class="sxs-lookup"><span data-stu-id="59610-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="59610-121">Hostitel služby používá základní adresy, které mu byly předány, k určení, kterou vazbu použít.</span><span class="sxs-lookup"><span data-stu-id="59610-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="59610-122">Následující příklad používá `protocolMappings` prvek <>.</span><span class="sxs-lookup"><span data-stu-id="59610-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="59610-123">Změna výchozích prvků konfigurace, jako jsou vazby nebo chování, může ovlivnit služby definované v nižších úrovních hierarchie konfigurace, protože mohou používat tyto výchozí vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="59610-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="59610-124">Takže ten, kdo změní výchozí vazby a chování musí být vědomi, že tyto změny mohou mít vliv na jiné služby v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="59610-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59610-125">Služby hostované v rámci Služby internetovou informační služby (IIS) nebo služby aktivace procesů systému Windows (WAS) používají virtuální adresář jako svou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="59610-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="59610-126">V předchozím příkladu koncový bod se základní adresou, která začíná <xref:System.ServiceModel.BasicHttpBinding>schématem http, používá .</span><span class="sxs-lookup"><span data-stu-id="59610-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="59610-127">Koncový bod se základní adresou, která začíná schématem net.tcp, používá rozhraní <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="59610-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="59610-128">Nastavení můžete přepsat v místním souboru App.config nebo Web.config.</span><span class="sxs-lookup"><span data-stu-id="59610-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="59610-129">Každý prvek v `protocolMappings` oddílu <> musí určit schéma a vazbu.</span><span class="sxs-lookup"><span data-stu-id="59610-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="59610-130">Volitelně může určit `bindingConfiguration` atribut, který určuje konfiguraci `bindings` vazby v části <> konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="59610-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="59610-131">Pokud `bindingConfiguration` není zadána žádná, použije se konfigurace anonymní vazby příslušného typu vazby.</span><span class="sxs-lookup"><span data-stu-id="59610-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="59610-132">Chování služby jsou konfigurovány pro výchozí `behavior` koncové body `serviceBehaviors` pomocí anonymních <> oddíly v <> oddíly.</span><span class="sxs-lookup"><span data-stu-id="59610-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="59610-133">Všechny nepojmenované `behavior` prvky `serviceBehaviors`> <v rámci <> se používají ke konfiguraci chování služby.</span><span class="sxs-lookup"><span data-stu-id="59610-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="59610-134">Následující konfigurační soubor například umožňuje publikování metadat služby pro všechny služby v rámci hostitele.</span><span class="sxs-lookup"><span data-stu-id="59610-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="59610-135">Chování koncových bodů se nakonfiguruje pomocí anonymních <`behavior`> oddílů v <`serviceBehaviors` oddílech>.</span><span class="sxs-lookup"><span data-stu-id="59610-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="59610-136">Následující příklad je konfigurační soubor ekvivalentní souboru na začátku tohoto tématu, který používá zjednodušený konfigurační model.</span><span class="sxs-lookup"><span data-stu-id="59610-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
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
> <span data-ttu-id="59610-137">Tato funkce se vztahuje pouze na konfiguraci služby WCF, nikoli konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="59610-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="59610-138">Ve většině případů wcf konfigurace klienta budou generovány nástrojem, jako je například svcutil.exe nebo přidání odkazu na službu z visual studio.</span><span class="sxs-lookup"><span data-stu-id="59610-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="59610-139">Pokud ručně konfigurujete klienta WCF, \<budete muset přidat prvek klienta> do konfigurace a zadat všechny koncové body, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="59610-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59610-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="59610-140">See also</span></span>

- [<span data-ttu-id="59610-141">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="59610-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="59610-142">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="59610-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="59610-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="59610-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59610-144">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="59610-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="59610-145">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="59610-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="59610-146">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="59610-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
