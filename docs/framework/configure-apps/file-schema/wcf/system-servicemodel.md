---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16a3b9b361048344993fdc338544b6b0ceb95387
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="1fafe-102">&lt;system.serviceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="1fafe-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="1fafe-103">Tento konfigurační oddíl obsahuje všechny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel konfigurace – elementy.</span><span class="sxs-lookup"><span data-stu-id="1fafe-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fafe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fafe-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
  </behaviors>  
  <bindings>  
  </bindings>  
  <client>  
  </client>  
  <comContracts>  
  </comContracts>  
  <commonBehaviors>  
  </commonBehaviors>  
  <diagnostics>  
  </diagnostics>  
  <extensions>  
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>  
  <serviceHostingEnvironment>  
  </serviceHostingEnvironment>  
  <services>  
  </services>
  <standardEndpoints>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fafe-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1fafe-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1fafe-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1fafe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fafe-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fafe-107">Attributes</span></span>  
 <span data-ttu-id="1fafe-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="1fafe-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1fafe-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1fafe-109">Child Elements</span></span>  
  
|<span data-ttu-id="1fafe-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fafe-110">Element</span></span>|<span data-ttu-id="1fafe-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1fafe-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fafe-112">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1fafe-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="1fafe-113">Tento oddíl definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="1fafe-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1fafe-114">Každá kolekce definuje chování elementy spotřebovávají koncové body a služby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="1fafe-115">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="1fafe-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="1fafe-116">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1fafe-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="1fafe-117">Tato část obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="1fafe-118">Každá položka je identifikována jeho jedinečné `name`.</span><span class="sxs-lookup"><span data-stu-id="1fafe-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="1fafe-119">Služby používají vazby jejich propojováním pomocí `name`.</span><span class="sxs-lookup"><span data-stu-id="1fafe-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="1fafe-120">\<klient ></span><span class="sxs-lookup"><span data-stu-id="1fafe-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="1fafe-121">Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="1fafe-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="1fafe-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="1fafe-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="1fafe-123">Tento oddíl definuje kontrakty COM povolen pro WCF a rozhraní COM zprostředkovatel komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="1fafe-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="1fafe-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1fafe-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="1fafe-125">V této části můžete definovat pouze v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="1fafe-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="1fafe-126">Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="1fafe-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1fafe-127">Každá kolekce definuje chování prvky používané ve všech [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] koncových bodů a služeb na počítači v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1fafe-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="1fafe-128">Pokud chování je definovaný jak v `<commonBehaviors>` a `<behaviors>` jejich chování v oddílech \<chování > části je přednost.</span><span class="sxs-lookup"><span data-stu-id="1fafe-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="1fafe-129">\<Rozšíření ></span><span class="sxs-lookup"><span data-stu-id="1fafe-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="1fafe-130">Tato část obsahuje kolekci rozšíření, která uživateli umožňuje vytvořit uživatelem definované vazby, chování a dalších aspektů rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1fafe-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="1fafe-131">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="1fafe-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="1fafe-132">Tato část obsahuje nastavení pro diagnostiku funkcím WCF.</span><span class="sxs-lookup"><span data-stu-id="1fafe-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="1fafe-133">Uživatel může povolit či zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a můžete přidat vlastní zprávu filtry.</span><span class="sxs-lookup"><span data-stu-id="1fafe-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="1fafe-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1fafe-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="1fafe-135">Tento oddíl definuje sadu výchozí protokol mapování mezi přenosu protokolu schémata (např. http, net.tcp, net.pipe atd.) a vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="1fafe-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="1fafe-136">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="1fafe-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1fafe-137">Tento oddíl definuje sadu směrování filtry, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="1fafe-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="1fafe-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="1fafe-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="1fafe-139">Tento oddíl definuje, co zadejte službu, kterou vytvoří hostitelské prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="1fafe-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="1fafe-140">Pokud tato část je prázdná, použije se výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="1fafe-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="1fafe-141">\<služby ></span><span class="sxs-lookup"><span data-stu-id="1fafe-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="1fafe-142">Oddíl obsahuje kolekci služeb.</span><span class="sxs-lookup"><span data-stu-id="1fafe-142">The section contains a collection of services.</span></span> <span data-ttu-id="1fafe-143">U každé služby definované v sestavení, obsahuje tento prvek `service` element zadání nastavení pro službu.</span><span class="sxs-lookup"><span data-stu-id="1fafe-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="1fafe-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1fafe-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1fafe-145">Tento oddíl definuje kolekce standardních koncových bodů, které jsou opakovaně použitelné předem nakonfigurované koncové body.</span><span class="sxs-lookup"><span data-stu-id="1fafe-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="1fafe-146">Koncový bod standardní bude mít jeden nebo více adresy, vazby a atributy kontrakt nastavte na pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1fafe-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="1fafe-147">Například v koncový bod zjišťování vyřešen kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1fafe-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="1fafe-148">Standardní koncové body můžete taky rozšířit koncový bod služby s nové vlastnosti podobná definování vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fafe-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1fafe-149">Parent Elements</span></span>  
  
|<span data-ttu-id="1fafe-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fafe-150">Element</span></span>|<span data-ttu-id="1fafe-151">Popis</span><span class="sxs-lookup"><span data-stu-id="1fafe-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1fafe-152">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="1fafe-152">\<configuration></span></span>|<span data-ttu-id="1fafe-153">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="1fafe-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fafe-154">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fafe-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="1fafe-155">nepřidává žádné další prvky konfigurace části Další produkty.</span><span class="sxs-lookup"><span data-stu-id="1fafe-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="1fafe-156">služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1fafe-156"> services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="1fafe-157">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="1fafe-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="1fafe-158">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="1fafe-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="1fafe-159">Části a jejího obsahu definovat kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="1fafe-160">Pouze služby `name` atribut je požadován.</span><span class="sxs-lookup"><span data-stu-id="1fafe-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="1fafe-161">Ve výchozím nastavení název služby popisuje základní typ CLR použít k implementaci služby; Můžete však změnit vlastnost ConfigurationName na <xref:System.ServiceModel.ServiceContractAttribute> potlačit požadavek na typ CLR.</span><span class="sxs-lookup"><span data-stu-id="1fafe-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="1fafe-162">`behaviorConfiguration` Atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="1fafe-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="1fafe-163">Určuje chování služby používané služby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="1fafe-164">Nastavení chování tímto atributem propojit chování služby definovaný v oboru stejné konfigurační soubor (tj. stejný soubor nebo soubor nadřazené).</span><span class="sxs-lookup"><span data-stu-id="1fafe-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="1fafe-165">Každá služba vystavuje jeden nebo více koncové body definované v `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="1fafe-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="1fafe-166">Každý koncový bod má svou vlastní adresu a vazby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="1fafe-167">Všechny vazby používaných v rámci konfiguračního souboru musí být definován v oboru souboru.</span><span class="sxs-lookup"><span data-stu-id="1fafe-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="1fafe-168">Vazby jsou propojeny s koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="1fafe-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="1fafe-169">`binding` Atribut definuje, ve které části je definovaný vazby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="1fafe-170">`bindingConfiguration` Atribut definuje, které nakonfigurovanou vazbu v rámci části vazby se používá.</span><span class="sxs-lookup"><span data-stu-id="1fafe-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="1fafe-171">Vazba části můžete definovat několik nakonfigurované vazby.</span><span class="sxs-lookup"><span data-stu-id="1fafe-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fafe-172">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fafe-172">Example</span></span>  
 <span data-ttu-id="1fafe-173">Jedná se o příklad konfiguračního souboru WCF.</span><span class="sxs-lookup"><span data-stu-id="1fafe-173">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fafe-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fafe-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
