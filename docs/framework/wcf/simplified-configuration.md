---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 567f03e8f35ed72ba7e2a602bf47257158741fb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321160"
---
# <a name="simplified-configuration"></a><span data-ttu-id="543ba-102">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="543ba-102">Simplified Configuration</span></span>
<span data-ttu-id="543ba-103">Konfigurace služeb Windows Communication Foundation (WCF) může být složitý úkol.</span><span class="sxs-lookup"><span data-stu-id="543ba-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="543ba-104">Existuje mnoho různých možností a není vždy snadné určit, která nastavení se vyžadují.</span><span class="sxs-lookup"><span data-stu-id="543ba-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="543ba-105">Přestože konfigurační soubory zvyšují flexibilitu služeb WCF, jsou také zdrojem mnoha obtíží při hledání problémů.</span><span class="sxs-lookup"><span data-stu-id="543ba-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="543ba-106">řeší tyto problémy a poskytuje způsob, jak omezit velikost a složitost konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="543ba-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="543ba-107">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="543ba-107">Simplified Configuration</span></span>  
 <span data-ttu-id="543ba-108">V konfiguračních souborech služby WCF < oddíl `system.serviceModel` > obsahuje @no__t prvek < >-1 pro každou hostovanou službu.</span><span class="sxs-lookup"><span data-stu-id="543ba-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="543ba-109">< Prvek `service` > obsahuje kolekci < `endpoint` > prvků, které určují koncové body vystavené pro každou službu a volitelně také chování sady.</span><span class="sxs-lookup"><span data-stu-id="543ba-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="543ba-110">< Prvky `endpoint` > určují adresu, vazbu a kontrakt vystavený koncovým bodem a volitelně vazby chování konfigurace a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="543ba-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="543ba-111">< Oddíl `system.serviceModel` > obsahuje také @no__t prvek < >-1, který umožňuje určit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="543ba-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="543ba-112">Následující příklad ukazuje < oddíl `system.serviceModel` > konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="543ba-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="543ba-113">zjednodušuje konfiguraci služby WCF tím, že odebere požadavek na > prvek `service` <.</span><span class="sxs-lookup"><span data-stu-id="543ba-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="543ba-114">Pokud nepřidáte < oddíl `service` > nebo přidáte žádné koncové body do < `service` > a vaše služba nedefinuje žádné koncové body, pak se do vaší služby automaticky přidají sada výchozích koncových bodů, jednu pro každou základní adresu služby. a pro každou smlouvu, kterou služba implementuje.</span><span class="sxs-lookup"><span data-stu-id="543ba-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="543ba-115">V každém z těchto koncových bodů adresa koncového bodu odpovídá základní adrese. vazba je určena základním adresním schématem a smlouva je ta, kterou implementuje vaše služba.</span><span class="sxs-lookup"><span data-stu-id="543ba-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="543ba-116">Pokud nepotřebujete zadat žádné koncové body nebo chování služby nebo provést žádné změny nastavení vazby, nemusíte vůbec zadávat konfigurační soubor služby.</span><span class="sxs-lookup"><span data-stu-id="543ba-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="543ba-117">Pokud služba implementuje dvě smlouvy a hostitel povolí přenos přes protokol HTTP i TCP, vytvoří hostitel služby čtyři výchozí koncové body, jednu pro každou kontrakt pomocí každého přenosu.</span><span class="sxs-lookup"><span data-stu-id="543ba-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="543ba-118">Chcete-li vytvořit výchozí koncové body, musí hostitel služby zjistit, jaké vazby se mají použít.</span><span class="sxs-lookup"><span data-stu-id="543ba-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="543ba-119">Tato nastavení jsou uvedená v < `protocolMappings` > v části < `system.serviceModel` >.</span><span class="sxs-lookup"><span data-stu-id="543ba-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="543ba-120">Část < `protocolMappings` > obsahuje seznam schémat přenosových protokolů mapovaných na typy vazeb.</span><span class="sxs-lookup"><span data-stu-id="543ba-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="543ba-121">Hostitel služby používá předaných základních adres k určení, která vazba se má použít.</span><span class="sxs-lookup"><span data-stu-id="543ba-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="543ba-122">Následující příklad používá < prvek `protocolMappings` >.</span><span class="sxs-lookup"><span data-stu-id="543ba-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="543ba-123">Změna výchozích prvků konfigurace, jako jsou vazby nebo chování, může ovlivnit služby definované v nižších úrovních konfigurační hierarchie, protože by mohly používat tyto výchozí vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="543ba-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="543ba-124">I když se jim budou měnit výchozí vazby a chování, je třeba si uvědomit, že tyto změny mohou ovlivnit jiné služby v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="543ba-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="543ba-125">Služby hostované v rámci služby Internetová informační služba (IIS) nebo aktivační služba procesů systému Windows (WAS) používají jako základní adresu virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="543ba-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="543ba-126">V předchozím příkladu koncový bod se základní adresou začínající schématem HTTP používá <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="543ba-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="543ba-127">Koncový bod se základní adresou, který začíná schématem NET. TCP, používá <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="543ba-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="543ba-128">Nastavení můžete přepsat v souboru Local App. config nebo Web. config.</span><span class="sxs-lookup"><span data-stu-id="543ba-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="543ba-129">Každý prvek v části < `protocolMappings` > musí určovat schéma a vazbu.</span><span class="sxs-lookup"><span data-stu-id="543ba-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="543ba-130">Volitelně můžete zadat atribut `bindingConfiguration`, který určuje konfiguraci vazby v části < `bindings` > konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="543ba-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="543ba-131">Pokud není zadaný žádný `bindingConfiguration`, použije se konfigurace anonymní vazby příslušného typu vazby.</span><span class="sxs-lookup"><span data-stu-id="543ba-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="543ba-132">Chování služby se konfiguruje pro výchozí koncové body pomocí anonymních < `behavior` > oddíly v < `serviceBehaviors` > oddíly.</span><span class="sxs-lookup"><span data-stu-id="543ba-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="543ba-133">Ke konfiguraci chování služby se používají všechny nepojmenované < prvky `behavior` > v rámci < `serviceBehaviors` >.</span><span class="sxs-lookup"><span data-stu-id="543ba-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="543ba-134">Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.</span><span class="sxs-lookup"><span data-stu-id="543ba-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="543ba-135">Chování koncového bodu se konfiguruje pomocí anonymních < `behavior` > oddíly v @no__t oddílech < >-1.</span><span class="sxs-lookup"><span data-stu-id="543ba-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="543ba-136">Následující příklad je konfigurační soubor, který je ekvivalentní k tomu na začátku tohoto tématu, které používá zjednodušený konfigurační model.</span><span class="sxs-lookup"><span data-stu-id="543ba-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
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
> <span data-ttu-id="543ba-137">Tato funkce se týká pouze konfigurace služby WCF, nikoli konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="543ba-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="543ba-138">Ve většině případů bude konfigurace klienta WCF vygenerována nástrojem, jako je Svcutil. exe, nebo přidáním odkazu na službu ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="543ba-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="543ba-139">Pokud ručně konfigurujete klienta WCF, bude nutné do konfigurace přidat prvek \<client > a zadat koncové body, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="543ba-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543ba-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="543ba-140">See also</span></span>

- [<span data-ttu-id="543ba-141">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="543ba-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="543ba-142">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="543ba-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="543ba-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="543ba-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="543ba-144">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="543ba-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="543ba-145">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="543ba-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="543ba-146">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="543ba-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
