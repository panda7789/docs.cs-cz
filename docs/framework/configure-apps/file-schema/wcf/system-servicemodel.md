---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 7b0c91bafc14dee0d298a5cd31dc674f5002466a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274193"
---
# <a name="systemservicemodel"></a><span data-ttu-id="20022-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20022-102">\<system.serviceModel></span></span>
<span data-ttu-id="20022-103">Tento oddíl konfigurace obsahuje všechny elementy konfigurace ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="20022-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20022-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20022-104">Syntax</span></span>  
  
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
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20022-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="20022-105">Attributes and Elements</span></span>  
 <span data-ttu-id="20022-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20022-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20022-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="20022-107">Attributes</span></span>  
 <span data-ttu-id="20022-108">Žádná</span><span class="sxs-lookup"><span data-stu-id="20022-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20022-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="20022-109">Child Elements</span></span>  
  
|<span data-ttu-id="20022-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="20022-110">Element</span></span>|<span data-ttu-id="20022-111">Popis</span><span class="sxs-lookup"><span data-stu-id="20022-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20022-112">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="20022-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="20022-113">Tento oddíl definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="20022-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="20022-114">Každou kolekci definuje chování elementů používané koncové body a služby.</span><span class="sxs-lookup"><span data-stu-id="20022-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="20022-115">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="20022-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="20022-116">\<bindings></span><span class="sxs-lookup"><span data-stu-id="20022-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="20022-117">Tato část obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="20022-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="20022-118">Každá položka je identifikován jeho jedinečné `name`.</span><span class="sxs-lookup"><span data-stu-id="20022-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="20022-119">Služby používají vazby jejich propojením pomocí `name`.</span><span class="sxs-lookup"><span data-stu-id="20022-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="20022-120">\<client></span><span class="sxs-lookup"><span data-stu-id="20022-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="20022-121">Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="20022-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="20022-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="20022-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="20022-123">Tento oddíl definuje kontrakty COM pro WCF a modelu COM interop povolené.</span><span class="sxs-lookup"><span data-stu-id="20022-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="20022-124">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="20022-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="20022-125">Tato část lze definovat pouze v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="20022-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="20022-126">Definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="20022-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="20022-127">Každou kolekci definuje chování elementů používané všech koncových bodů WCF a služeb na počítači.</span><span class="sxs-lookup"><span data-stu-id="20022-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="20022-128">Pokud chování je definován v `<commonBehaviors>` a `<behaviors>` části, chování \<chování > části je přednost.</span><span class="sxs-lookup"><span data-stu-id="20022-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="20022-129">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="20022-129">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="20022-130">Tato část obsahuje nastavení pro funkce Diagnostika služby WCF.</span><span class="sxs-lookup"><span data-stu-id="20022-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="20022-131">Uživatel můžete povolit nebo zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a můžete přidat vlastní zprávu filtry.</span><span class="sxs-lookup"><span data-stu-id="20022-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="20022-132">\<extensions></span><span class="sxs-lookup"><span data-stu-id="20022-132">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="20022-133">Tento oddíl obsahuje kolekci rozšíření, které umožňují uživateli vytvořit uživatelem definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="20022-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="20022-134">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="20022-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="20022-135">Tento oddíl definuje sadu výchozích mapování protokolů mezi schématy přenosových protokolů (např. http, net.tcp, net.pipe atd.) a vazbami WCF.</span><span class="sxs-lookup"><span data-stu-id="20022-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="20022-136">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="20022-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="20022-137">Tento oddíl definuje sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body pro odesílání zpráv do kdy filtr hledá shodu.</span><span class="sxs-lookup"><span data-stu-id="20022-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="20022-138">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="20022-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="20022-139">Tento oddíl definuje, jaký typ služby, který vytvoří instanci hostitelské prostředí pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="20022-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="20022-140">Pokud v této části je prázdný, je použit výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="20022-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="20022-141">\<services></span><span class="sxs-lookup"><span data-stu-id="20022-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="20022-142">Oddíl obsahuje kolekci služeb.</span><span class="sxs-lookup"><span data-stu-id="20022-142">The section contains a collection of services.</span></span> <span data-ttu-id="20022-143">U každé služby definované v sestavení, obsahuje tento element `service` prvek nastavení pro službu.</span><span class="sxs-lookup"><span data-stu-id="20022-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="20022-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="20022-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="20022-145">Tento oddíl definuje kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body.</span><span class="sxs-lookup"><span data-stu-id="20022-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="20022-146">Standardní koncový bod bude mít jednu nebo více adresa, vazba a kontrakt atributy nastavit na pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20022-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="20022-147">Například v koncový bod zjišťování vyřešen kontrakt.</span><span class="sxs-lookup"><span data-stu-id="20022-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="20022-148">Standardní koncové body můžete použít také k rozšíření koncového bodu služby s novou vlastností k definování vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="20022-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="20022-149">\<tracking></span><span class="sxs-lookup"><span data-stu-id="20022-149">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|<span data-ttu-id="20022-150">Tento oddíl definuje nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20022-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20022-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="20022-151">Parent Elements</span></span>  
  
|<span data-ttu-id="20022-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="20022-152">Element</span></span>|<span data-ttu-id="20022-153">Popis</span><span class="sxs-lookup"><span data-stu-id="20022-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20022-154">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="20022-154">\<configuration></span></span>|<span data-ttu-id="20022-155">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="20022-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20022-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20022-156">Remarks</span></span>  
 <span data-ttu-id="20022-157">WCF nepřidá prvky do oddílu konfigurace ostatních produktů.</span><span class="sxs-lookup"><span data-stu-id="20022-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="20022-158">Služby WCF, které jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="20022-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="20022-159">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="20022-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="20022-160">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="20022-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="20022-161">Části a její obsah definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="20022-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="20022-162">Pouze služby `name` atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="20022-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="20022-163">Ve výchozím nastavení název služby popisuje základní typ CLR používaný k implementaci služby; Můžete však změnit vlastnost ConfigurationName na <xref:System.ServiceModel.ServiceContractAttribute> přepsat požadovaný typ CLR.</span><span class="sxs-lookup"><span data-stu-id="20022-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="20022-164">`behaviorConfiguration` Atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="20022-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="20022-165">Určuje chování služby používané službou.</span><span class="sxs-lookup"><span data-stu-id="20022-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="20022-166">Chování určené jinou tento atribut musí odkazovat na chování služby definované v oboru stejný konfigurační soubor (tj. na stejný soubor nebo nadřazený soubor).</span><span class="sxs-lookup"><span data-stu-id="20022-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="20022-167">Každá služba zpřístupňuje jeden nebo více koncových bodů podle `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="20022-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="20022-168">Každý koncový bod má svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="20022-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="20022-169">Všechny vazby používá v konfiguračním souboru musí být definován v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="20022-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="20022-170">Vazby jsou propojeny do koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="20022-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="20022-171">`binding` Atribut definuje, ve které části je definována vazby.</span><span class="sxs-lookup"><span data-stu-id="20022-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="20022-172">`bindingConfiguration` Atribut definuje, které nakonfigurovanou vazbu v rámci oddílu vazby se používá.</span><span class="sxs-lookup"><span data-stu-id="20022-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="20022-173">Část vazby můžete definovat několik nakonfigurované vazby.</span><span class="sxs-lookup"><span data-stu-id="20022-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20022-174">Příklad</span><span class="sxs-lookup"><span data-stu-id="20022-174">Example</span></span>  
 <span data-ttu-id="20022-175">Toto je příklad konfiguračního souboru WCF.</span><span class="sxs-lookup"><span data-stu-id="20022-175">This is an example of a WCF configuration file.</span></span>  
  
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
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
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
  
## <a name="see-also"></a><span data-ttu-id="20022-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20022-176">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
