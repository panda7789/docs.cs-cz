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
ms.openlocfilehash: 4fa6916437bb569029efe270ba8296703d89c539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938907"
---
# <a name="systemservicemodel"></a><span data-ttu-id="e3d9d-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e3d9d-102">\<system.serviceModel></span></span>
<span data-ttu-id="e3d9d-103">Tento oddíl konfigurace obsahuje všechny prvky konfigurace ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e3d9d-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3d9d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3d9d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3d9d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e3d9d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3d9d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3d9d-107">Attributes</span></span>  
 <span data-ttu-id="e3d9d-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="e3d9d-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3d9d-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e3d9d-109">Child Elements</span></span>  
  
|<span data-ttu-id="e3d9d-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3d9d-110">Element</span></span>|<span data-ttu-id="e3d9d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e3d9d-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3d9d-112">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e3d9d-112">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="e3d9d-113">V této části jsou definovány dvě podřízené `endpointBehaviors` kolekce `serviceBehaviors`s názvem a.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e3d9d-114">Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="e3d9d-115">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="e3d9d-116">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="e3d9d-116">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e3d9d-117">Tato část obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="e3d9d-118">Každá položka je identifikována jejím jedinečným `name`.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="e3d9d-119">Služby používají vazby propojením s použitím `name`.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="e3d9d-120">\<client></span><span class="sxs-lookup"><span data-stu-id="e3d9d-120">\<client></span></span>](client.md)|<span data-ttu-id="e3d9d-121">Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="e3d9d-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e3d9d-122">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="e3d9d-123">Tato část definuje kontrakty COM aktivované pro WCF a zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="e3d9d-124">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="e3d9d-124">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="e3d9d-125">Tento oddíl lze definovat pouze v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="e3d9d-126">Definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e3d9d-127">Každá kolekce definuje prvky chování spotřebované všemi koncovými body a službami WCF v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="e3d9d-128">Pokud je chování definováno v obou `<commonBehaviors>` částech a `<behaviors>` \<, chování v části chování > má přednost.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="e3d9d-129">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="e3d9d-129">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="e3d9d-130">Tato část obsahuje nastavení pro diagnostické funkce služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="e3d9d-131">Uživatel může povolit nebo zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a může přidat vlastní filtry zpráv.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="e3d9d-132">\<> rozšíření</span><span class="sxs-lookup"><span data-stu-id="e3d9d-132">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="e3d9d-133">Tato část obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="e3d9d-134">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="e3d9d-134">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="e3d9d-135">Tato část definuje sadu výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a WCF vazbami.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="e3d9d-136">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="e3d9d-136">\<routing></span></span>](routing.md)|<span data-ttu-id="e3d9d-137">Tato část definuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovacích tabulek, které definují cílové koncové body, do kterých se odesílají zprávy. filtrovat shody</span><span class="sxs-lookup"><span data-stu-id="e3d9d-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="e3d9d-138">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e3d9d-138">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="e3d9d-139">V této části je definován typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="e3d9d-140">Pokud je tato část prázdná, použije se výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="e3d9d-141">\<services></span><span class="sxs-lookup"><span data-stu-id="e3d9d-141">\<services></span></span>](services.md)|<span data-ttu-id="e3d9d-142">Oddíl obsahuje kolekci služeb.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-142">The section contains a collection of services.</span></span> <span data-ttu-id="e3d9d-143">Pro každou službu definovanou v sestavení tento element obsahuje element, který `service` určuje nastavení pro službu.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="e3d9d-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e3d9d-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e3d9d-145">Tato část definuje kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="e3d9d-146">Standardní koncový bod bude mít jednu nebo víc atributů adresa, vazba a kontraktu nastavenou na pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="e3d9d-147">Například ve koncovém bodě zjišťování je smlouva opravena.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="e3d9d-148">Pomocí standardních koncových bodů můžete také rozšířenit koncový bod služby s novými vlastnostmi podobnými definování vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="e3d9d-149">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e3d9d-149">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="e3d9d-150">Tato část definuje nastavení sledování pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3d9d-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e3d9d-151">Parent Elements</span></span>  
  
|<span data-ttu-id="e3d9d-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3d9d-152">Element</span></span>|<span data-ttu-id="e3d9d-153">Popis</span><span class="sxs-lookup"><span data-stu-id="e3d9d-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3d9d-154">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e3d9d-154">\<configuration></span></span>|<span data-ttu-id="e3d9d-155">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3d9d-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3d9d-156">Remarks</span></span>  
 <span data-ttu-id="e3d9d-157">Technologie WCF nepřidává prvky do konfiguračních oddílů jiných produktů.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="e3d9d-158">Služby WCF jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e3d9d-159">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="e3d9d-160">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="e3d9d-161">Oddíl a jeho obsah definují kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="e3d9d-162">Je vyžadován pouze `name` atribut služby.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="e3d9d-163">Ve výchozím nastavení popisuje název služby základní typ CLR používaný k implementaci služby. Můžete však změnit vlastnost <xref:System.ServiceModel.ServiceContractAttribute> ConfigurationName pro na, aby bylo možné přepsat požadavek typu CLR.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="e3d9d-164">`behaviorConfiguration` Atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="e3d9d-165">Identifikuje chování služby používané službou.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="e3d9d-166">Chování zadané pomocí tohoto atributu musí odkazovat na chování služby definované v oboru stejného konfiguračního souboru (tj. stejný soubor nebo nadřazený soubor).</span><span class="sxs-lookup"><span data-stu-id="e3d9d-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="e3d9d-167">Každá služba zveřejňuje jeden nebo více koncových bodů `endpoint` definovaných v elementu.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="e3d9d-168">Každý koncový bod má svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="e3d9d-169">Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="e3d9d-170">Vazby jsou propojeny s koncovými body pomocí kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="e3d9d-171">`binding` Atribut definuje, v jakém oddílu je vazba definována.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="e3d9d-172">`bindingConfiguration` Atribut určuje, která konfigurovaná vazba v rámci oddílu Binding je použita.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="e3d9d-173">Oddíl Binding může definovat několik nakonfigurovaných vazeb.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3d9d-174">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3d9d-174">Example</span></span>  
 <span data-ttu-id="e3d9d-175">Toto je příklad konfiguračního souboru WCF.</span><span class="sxs-lookup"><span data-stu-id="e3d9d-175">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3d9d-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3d9d-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
