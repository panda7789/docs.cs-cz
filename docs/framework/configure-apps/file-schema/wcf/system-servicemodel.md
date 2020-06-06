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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399445"
---
# \<system.serviceModel>
<span data-ttu-id="ecb3c-102">Tento oddíl konfigurace obsahuje všechny prvky konfigurace ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ecb3c-102">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="ecb3c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecb3c-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecb3c-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ecb3c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ecb3c-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecb3c-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="ecb3c-106">Attributes</span></span>  
 <span data-ttu-id="ecb3c-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="ecb3c-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ecb3c-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ecb3c-108">Child Elements</span></span>  
  
|<span data-ttu-id="ecb3c-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="ecb3c-109">Element</span></span>|<span data-ttu-id="ecb3c-110">Description</span><span class="sxs-lookup"><span data-stu-id="ecb3c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="ecb3c-111">V této části jsou definovány dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="ecb3c-111">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ecb3c-112">Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-112">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="ecb3c-113">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-113">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="ecb3c-114">Tato část obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-114">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="ecb3c-115">Každá položka je identifikována jejím jedinečným `name` .</span><span class="sxs-lookup"><span data-stu-id="ecb3c-115">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="ecb3c-116">Služby používají vazby propojením s použitím `name` .</span><span class="sxs-lookup"><span data-stu-id="ecb3c-116">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="ecb3c-117">Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-117">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="ecb3c-118">Tato část definuje kontrakty COM aktivované pro WCF a zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-118">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="ecb3c-119">Tento oddíl lze definovat pouze v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-119">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="ecb3c-120">Definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="ecb3c-120">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ecb3c-121">Každá kolekce definuje prvky chování spotřebované všemi koncovými body a službami WCF v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-121">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="ecb3c-122">Pokud je chování definováno v obou `<commonBehaviors>` částech a `<behaviors>` , chování v \<behaviors> oddílu má přednost.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-122">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="ecb3c-123">Tato část obsahuje nastavení pro diagnostické funkce služby WCF.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-123">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="ecb3c-124">Uživatel může povolit nebo zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a může přidat vlastní filtry zpráv.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-124">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="ecb3c-125">Tato část obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-125">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="ecb3c-126">Tato část definuje sadu výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a WCF vazbami.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-126">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="ecb3c-127">Tato část definuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který <xref:System.ServiceModel.Dispatcher.MessageFilter> se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se budou posílat zprávy, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-127">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="ecb3c-128">V této části je definován typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-128">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="ecb3c-129">Pokud je tato část prázdná, použije se výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-129">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="ecb3c-130">Oddíl obsahuje kolekci služeb.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-130">The section contains a collection of services.</span></span> <span data-ttu-id="ecb3c-131">Pro každou službu definovanou v sestavení tento element obsahuje element, který `service` Určuje nastavení pro službu.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-131">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ecb3c-132">Tato část definuje kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-132">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="ecb3c-133">Standardní koncový bod bude mít jednu nebo víc atributů adresa, vazba a kontraktu nastavenou na pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-133">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="ecb3c-134">Například ve koncovém bodě zjišťování je smlouva opravena.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-134">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="ecb3c-135">Pomocí standardních koncových bodů můžete také rozšířenit koncový bod služby s novými vlastnostmi podobnými definování vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-135">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="ecb3c-136">Tato část definuje nastavení sledování pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-136">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ecb3c-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ecb3c-137">Parent Elements</span></span>  
  
|<span data-ttu-id="ecb3c-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="ecb3c-138">Element</span></span>|<span data-ttu-id="ecb3c-139">Description</span><span class="sxs-lookup"><span data-stu-id="ecb3c-139">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="ecb3c-140">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-140">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb3c-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecb3c-141">Remarks</span></span>  
 <span data-ttu-id="ecb3c-142">Technologie WCF nepřidává prvky do konfiguračních oddílů jiných produktů.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-142">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="ecb3c-143">Služby WCF jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-143">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="ecb3c-144">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-144">An assembly can contain any number of services.</span></span> <span data-ttu-id="ecb3c-145">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-145">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="ecb3c-146">Oddíl a jeho obsah definují kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-146">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="ecb3c-147">`name`Je vyžadován pouze atribut služby.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-147">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="ecb3c-148">Ve výchozím nastavení popisuje název služby základní typ CLR používaný k implementaci služby. Můžete však změnit vlastnost ConfigurationName pro na, aby bylo možné <xref:System.ServiceModel.ServiceContractAttribute> přepsat požadavek typu CLR.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-148">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="ecb3c-149">`behaviorConfiguration`Atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-149">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="ecb3c-150">Identifikuje chování služby používané službou.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-150">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="ecb3c-151">Chování zadané pomocí tohoto atributu musí odkazovat na chování služby definované v oboru stejného konfiguračního souboru (tj. stejný soubor nebo nadřazený soubor).</span><span class="sxs-lookup"><span data-stu-id="ecb3c-151">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="ecb3c-152">Každá služba zveřejňuje jeden nebo více koncových bodů definovaných v `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-152">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="ecb3c-153">Každý koncový bod má svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-153">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="ecb3c-154">Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-154">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="ecb3c-155">Vazby jsou propojeny s koncovými body pomocí kombinace atributů `name` a `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ecb3c-155">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="ecb3c-156">`binding`Atribut definuje, v jakém oddílu je vazba definována.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-156">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="ecb3c-157">`bindingConfiguration`Atribut určuje, která konfigurovaná vazba v rámci oddílu Binding je použita.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-157">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="ecb3c-158">Oddíl Binding může definovat několik nakonfigurovaných vazeb.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-158">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecb3c-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecb3c-159">Example</span></span>  
 <span data-ttu-id="ecb3c-160">Toto je příklad konfiguračního souboru WCF.</span><span class="sxs-lookup"><span data-stu-id="ecb3c-160">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecb3c-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecb3c-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
