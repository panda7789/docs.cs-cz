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
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399445"
---
# <a name="systemservicemodel"></a><span data-ttu-id="1c649-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1c649-102">\<system.serviceModel></span></span>
<span data-ttu-id="1c649-103">Tento oddíl konfigurace obsahuje všechny prvky konfigurace ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1c649-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

<span data-ttu-id="1c649-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1c649-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1c649-105">&nbsp;&nbsp; **\<System. serviceModel >**</span><span class="sxs-lookup"><span data-stu-id="1c649-105">&nbsp;&nbsp;**\<system.serviceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c649-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c649-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c649-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c649-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1c649-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c649-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c649-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c649-109">Attributes</span></span>  
 <span data-ttu-id="1c649-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="1c649-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c649-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c649-111">Child Elements</span></span>  
  
|<span data-ttu-id="1c649-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c649-112">Element</span></span>|<span data-ttu-id="1c649-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1c649-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c649-114">\<> chování</span><span class="sxs-lookup"><span data-stu-id="1c649-114">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="1c649-115">V této části jsou definovány dvě podřízené `endpointBehaviors` kolekce `serviceBehaviors`s názvem a.</span><span class="sxs-lookup"><span data-stu-id="1c649-115">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1c649-116">Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1c649-116">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="1c649-117">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="1c649-117">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="1c649-118">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="1c649-118">\<bindings></span></span>](bindings.md)|<span data-ttu-id="1c649-119">Tato část obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="1c649-119">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="1c649-120">Každá položka je identifikována jejím jedinečným `name`.</span><span class="sxs-lookup"><span data-stu-id="1c649-120">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="1c649-121">Služby používají vazby propojením s použitím `name`.</span><span class="sxs-lookup"><span data-stu-id="1c649-121">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="1c649-122">\<client></span><span class="sxs-lookup"><span data-stu-id="1c649-122">\<client></span></span>](client.md)|<span data-ttu-id="1c649-123">Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="1c649-123">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="1c649-124">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="1c649-124">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="1c649-125">Tato část definuje kontrakty COM aktivované pro WCF a zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="1c649-125">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="1c649-126">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="1c649-126">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="1c649-127">Tento oddíl lze definovat pouze v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="1c649-127">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="1c649-128">Definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="1c649-128">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1c649-129">Každá kolekce definuje prvky chování spotřebované všemi koncovými body a službami WCF v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="1c649-129">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="1c649-130">Pokud je chování definováno v obou `<commonBehaviors>` částech a `<behaviors>` \<, chování v části chování > má přednost.</span><span class="sxs-lookup"><span data-stu-id="1c649-130">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="1c649-131">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="1c649-131">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="1c649-132">Tato část obsahuje nastavení pro diagnostické funkce služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1c649-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="1c649-133">Uživatel může povolit nebo zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a může přidat vlastní filtry zpráv.</span><span class="sxs-lookup"><span data-stu-id="1c649-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="1c649-134">\<> rozšíření</span><span class="sxs-lookup"><span data-stu-id="1c649-134">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="1c649-135">Tato část obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1c649-135">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="1c649-136">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="1c649-136">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="1c649-137">Tato část definuje sadu výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a WCF vazbami.</span><span class="sxs-lookup"><span data-stu-id="1c649-137">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="1c649-138">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="1c649-138">\<routing></span></span>](routing.md)|<span data-ttu-id="1c649-139">Tato část definuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovacích tabulek, které definují cílové koncové body, do kterých se odesílají zprávy. filtrovat shody</span><span class="sxs-lookup"><span data-stu-id="1c649-139">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="1c649-140">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="1c649-140">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="1c649-141">V této části je definován typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="1c649-141">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="1c649-142">Pokud je tato část prázdná, použije se výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="1c649-142">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="1c649-143">\<services></span><span class="sxs-lookup"><span data-stu-id="1c649-143">\<services></span></span>](services.md)|<span data-ttu-id="1c649-144">Oddíl obsahuje kolekci služeb.</span><span class="sxs-lookup"><span data-stu-id="1c649-144">The section contains a collection of services.</span></span> <span data-ttu-id="1c649-145">Pro každou službu definovanou v sestavení tento element obsahuje element, který `service` určuje nastavení pro službu.</span><span class="sxs-lookup"><span data-stu-id="1c649-145">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="1c649-146">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1c649-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="1c649-147">Tato část definuje kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body.</span><span class="sxs-lookup"><span data-stu-id="1c649-147">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="1c649-148">Standardní koncový bod bude mít jednu nebo víc atributů adresa, vazba a kontraktu nastavenou na pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c649-148">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="1c649-149">Například ve koncovém bodě zjišťování je smlouva opravena.</span><span class="sxs-lookup"><span data-stu-id="1c649-149">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="1c649-150">Pomocí standardních koncových bodů můžete také rozšířenit koncový bod služby s novými vlastnostmi podobnými definování vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="1c649-150">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="1c649-151">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1c649-151">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="1c649-152">Tato část definuje nastavení sledování pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1c649-152">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c649-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c649-153">Parent Elements</span></span>  
  
|<span data-ttu-id="1c649-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c649-154">Element</span></span>|<span data-ttu-id="1c649-155">Popis</span><span class="sxs-lookup"><span data-stu-id="1c649-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c649-156">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1c649-156">\<configuration></span></span>|<span data-ttu-id="1c649-157">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="1c649-157">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c649-158">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c649-158">Remarks</span></span>  
 <span data-ttu-id="1c649-159">Technologie WCF nepřidává prvky do konfiguračních oddílů jiných produktů.</span><span class="sxs-lookup"><span data-stu-id="1c649-159">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="1c649-160">Služby WCF jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1c649-160">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="1c649-161">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="1c649-161">An assembly can contain any number of services.</span></span> <span data-ttu-id="1c649-162">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="1c649-162">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="1c649-163">Oddíl a jeho obsah definují kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="1c649-163">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="1c649-164">Je vyžadován pouze `name` atribut služby.</span><span class="sxs-lookup"><span data-stu-id="1c649-164">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="1c649-165">Ve výchozím nastavení popisuje název služby základní typ CLR používaný k implementaci služby. Můžete však změnit vlastnost <xref:System.ServiceModel.ServiceContractAttribute> ConfigurationName pro na, aby bylo možné přepsat požadavek typu CLR.</span><span class="sxs-lookup"><span data-stu-id="1c649-165">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="1c649-166">`behaviorConfiguration` Atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="1c649-166">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="1c649-167">Identifikuje chování služby používané službou.</span><span class="sxs-lookup"><span data-stu-id="1c649-167">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="1c649-168">Chování zadané pomocí tohoto atributu musí odkazovat na chování služby definované v oboru stejného konfiguračního souboru (tj. stejný soubor nebo nadřazený soubor).</span><span class="sxs-lookup"><span data-stu-id="1c649-168">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="1c649-169">Každá služba zveřejňuje jeden nebo více koncových bodů `endpoint` definovaných v elementu.</span><span class="sxs-lookup"><span data-stu-id="1c649-169">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="1c649-170">Každý koncový bod má svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="1c649-170">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="1c649-171">Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="1c649-171">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="1c649-172">Vazby jsou propojeny s koncovými body pomocí kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="1c649-172">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="1c649-173">`binding` Atribut definuje, v jakém oddílu je vazba definována.</span><span class="sxs-lookup"><span data-stu-id="1c649-173">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="1c649-174">`bindingConfiguration` Atribut určuje, která konfigurovaná vazba v rámci oddílu Binding je použita.</span><span class="sxs-lookup"><span data-stu-id="1c649-174">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="1c649-175">Oddíl Binding může definovat několik nakonfigurovaných vazeb.</span><span class="sxs-lookup"><span data-stu-id="1c649-175">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c649-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c649-176">Example</span></span>  
 <span data-ttu-id="1c649-177">Toto je příklad konfiguračního souboru WCF.</span><span class="sxs-lookup"><span data-stu-id="1c649-177">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c649-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c649-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
