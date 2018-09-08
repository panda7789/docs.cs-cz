---
title: Konfigurace služeb pomocí konfiguračních souborů
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 904abff4f3cae5873fe3cc9705dee84f73e2a523
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195568"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="fc44e-102">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="fc44e-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="fc44e-103">Konfigurace služby Windows Communication Foundation (WCF) s konfiguračním souborem dává možnost poskytovat koncový bod a data o chování služby Přejme během nasazení místo v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="fc44e-104">Toto téma popisuje primární techniky, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fc44e-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="fc44e-105">Služba WCF se dají konfigurovat pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace.</span><span class="sxs-lookup"><span data-stu-id="fc44e-105">A WCF service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="fc44e-106">Nejčastěji jsou přidány elementy XML v souboru Web.config pro web Internetové informační služby (IIS), který je hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fc44e-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="fc44e-107">Prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používaný ke komunikaci se službou service) pro počítače podle počítače.</span><span class="sxs-lookup"><span data-stu-id="fc44e-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="fc44e-108">Kromě toho WCF obsahuje několik elementů poskytované systémem, které umožňují rychle vybrat většina základních funkcí pro službu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="fc44e-109">Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF se dodává s novou výchozí konfiguraci modelu, která zjednodušuje požadavky na konfiguraci WCF.</span><span class="sxs-lookup"><span data-stu-id="fc44e-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="fc44e-110">Pokud nezadáte žádnou konfiguraci WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaše služba se některé standardní koncové body a výchozí vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="fc44e-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="fc44e-111">V praxi, zápis konfigurace je velkou část programování WCF aplikací.</span><span class="sxs-lookup"><span data-stu-id="fc44e-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="fc44e-112">Další informace najdete v tématu [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc44e-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="fc44e-113">Seznam nejčastějších běžně používají elementy, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="fc44e-113">For a list of of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="fc44e-114">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc44e-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc44e-115">Při nasazení vedle sebe scénáře, ve které jsou nasazené dvě různé verze služby, je nutné zadat částečné názvy sestavení odkazovaná v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="fc44e-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="fc44e-116">Je to proto, že konfigurační soubor se sdílí mezi všemi verzemi služby a mohl být spuštěn v různých verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc44e-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="fc44e-117">System.Configuration: Soubor Web.config a App.config</span><span class="sxs-lookup"><span data-stu-id="fc44e-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="fc44e-118">WCF používá systém konfigurace System.Configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc44e-118">WCF uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="fc44e-119">Při konfiguraci služby v sadě Visual Studio, použijte k určení nastavení souboru Web.config nebo App.config soubor.</span><span class="sxs-lookup"><span data-stu-id="fc44e-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="fc44e-120">Volba název konfiguračního souboru určuje hostitelské prostředí, které jste vybrali pro službu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="fc44e-121">Pokud používáte k hostování vaší služby IIS, použijte soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="fc44e-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="fc44e-122">Pokud používáte jiné hostitelské prostředí, pomocí souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="fc44e-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="fc44e-123">V sadě Visual Studio soubor s názvem souboru App.config slouží k vytvoření konečného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fc44e-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="fc44e-124">Poslední název ve skutečnosti využívá ke konfiguraci závisí na názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="fc44e-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="fc44e-125">Například sestavení s názvem "Cohowinery.exe" má název souboru, konečnou konfiguraci "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="fc44e-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="fc44e-126">Však stačí změnit soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="fc44e-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="fc44e-127">Změny provedené v tomto souboru jsou automaticky provedeny do konfiguračního souboru konečné aplikace v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="fc44e-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="fc44e-128">Pomocí App.config, sloučí soubor konfigurační systém souboru App.config s obsahem souboru Machine.config při spuštění aplikace a tato konfigurace používá.</span><span class="sxs-lookup"><span data-stu-id="fc44e-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="fc44e-129">Tento mechanismus umožňuje nastavení platná pro celý počítač byly definovány v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="fc44e-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="fc44e-130">Souboru App.config můžete použít k přepsání nastavení souboru Machine.config. Můžete také uzamknout v nastavení v souboru Machine.config tak, aby získat použít.</span><span class="sxs-lookup"><span data-stu-id="fc44e-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="fc44e-131">V případě souboru Web.config sloučí konfigurační systém souborů Web.config ve všech adresářích vedoucí do adresáře aplikace do konfigurace, který se použije.</span><span class="sxs-lookup"><span data-stu-id="fc44e-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="fc44e-132">Další informace o konfiguraci a nastavení priorit, najdete v tématech v <xref:System.Configuration> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc44e-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="fc44e-133">Hlavní části konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fc44e-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="fc44e-134">Hlavní části v konfiguračním souboru obsahují následující prvky.</span><span class="sxs-lookup"><span data-stu-id="fc44e-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="fc44e-135">Vazby a chování oddíly jsou volitelné a jsou zahrnuty pouze v případě vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="fc44e-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="fc44e-136">\<Services > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-136">The \<services> Element</span></span>  
 <span data-ttu-id="fc44e-137">`services` Prvek obsahuje specifikace pro všechny služby hostitelů aplikací.</span><span class="sxs-lookup"><span data-stu-id="fc44e-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="fc44e-138">Počínaje zjednodušené konfigurační model v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tato část je nepovinná.</span><span class="sxs-lookup"><span data-stu-id="fc44e-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="fc44e-139">\<služby ></span><span class="sxs-lookup"><span data-stu-id="fc44e-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="fc44e-140">\<Služby > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-140">The \<service> Element</span></span>  
 <span data-ttu-id="fc44e-141">Každá služba má tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="fc44e-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="fc44e-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-142">`name`.</span></span> <span data-ttu-id="fc44e-143">Určuje typ, který poskytuje implementaci kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="fc44e-144">Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečku a název typu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="fc44e-145">Například `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="fc44e-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="fc44e-147">Určuje název jedné z `behavior` součástí prvky `behaviors` elementu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="fc44e-148">Zadané chování se řídí akce, například zda služba umožňuje zosobnění.</span><span class="sxs-lookup"><span data-stu-id="fc44e-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="fc44e-149">Pokud je jeho hodnota prázdný název nebo žádnou instanci `behaviorConfiguration` je k dispozici potom výchozí sadu chování služby je přidán do služby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="fc44e-150">\<service></span><span class="sxs-lookup"><span data-stu-id="fc44e-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="fc44e-151">\<Endpoint > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="fc44e-152">Každý koncový bod požaduje adresu vazba a kontrakt, které jsou znázorněny následující atributy:</span><span class="sxs-lookup"><span data-stu-id="fc44e-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="fc44e-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-153">`address`.</span></span> <span data-ttu-id="fc44e-154">Určuje služby identifikátor URI (Uniform Resource), což může být absolutní adresa nebo ten, který je zadána relativní k základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="fc44e-155">Pokud nastavit na prázdný řetězec znamená, že koncový bod je k dispozici na základní adrese, který je určen při vytváření <xref:System.ServiceModel.ServiceHost> pro službu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="fc44e-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-156">`binding`.</span></span> <span data-ttu-id="fc44e-157">Obvykle určuje vazeb poskytovaných systémem jako <xref:System.ServiceModel.WSHttpBinding>, ale můžete také určit uživatelem definované vazby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="fc44e-158">Zadaná vazba Určuje typ přenosu, zabezpečení a kódování použité a určuje, zda je podporována nebo povolené spolehlivé relace, transakcí nebo datové proudy.</span><span class="sxs-lookup"><span data-stu-id="fc44e-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="fc44e-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-159">`bindingConfiguration`.</span></span> <span data-ttu-id="fc44e-160">Pokud výchozí hodnoty vazby musí být změněny, to můžete udělat pomocí konfigurace odpovídající `binding` prvek `bindings` element.</span><span class="sxs-lookup"><span data-stu-id="fc44e-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="fc44e-161">Tento atribut by měly mít stejnou hodnotu jako `name` atribut `binding` element, který umožňuje změnit výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="fc44e-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="fc44e-162">Pokud není zadán název, nebo žádný `bindingConfiguration` je zadaná ve vazbě, koncový bod je použita výchozí vazbu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="fc44e-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="fc44e-163">`contract`.</span></span> <span data-ttu-id="fc44e-164">Určuje rozhraní definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fc44e-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="fc44e-165">Toto je rozhraní implementované v společný typ language runtime (CLR) určené `name` atribut `service` elementu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="fc44e-166">\<koncový bod > referenční dokumentace elementu</span><span class="sxs-lookup"><span data-stu-id="fc44e-166">\<endpoint> element reference</span></span>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="fc44e-167">\<Vazby > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="fc44e-168">`bindings` Prvek obsahuje specifikace pro všechny vazby, které může používat libovolný koncový bod definovaný v libovolnou službu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="fc44e-169">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="fc44e-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="fc44e-170">\<Vazby > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-170">The \<binding> Element</span></span>  
 <span data-ttu-id="fc44e-171">`binding` Elementů obsažených v `bindings` element může být buď jeden vazeb poskytovaných systémem (naleznete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md)) nebo vlastní vazby (naleznete v tématu [vlastních vazeb](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="fc44e-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="fc44e-172">`binding` Element má `name` atributů, které souvisí s koncového bodu určeného v vazbu `bindingConfiguration` atribut `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="fc44e-173">Pokud není zadán žádný název, pak je, že vazba odpovídá na výchozí hodnotu tohoto typu vazby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 <span data-ttu-id="fc44e-174">Další informace o konfiguraci služeb a klientů najdete v tématu [konfigurace Windows Communication Foundation aplikací](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="fc44e-174">For more information about configuring services and clients, see [Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="fc44e-175">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="fc44e-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="fc44e-176">\<Chování > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="fc44e-177">Toto je prvek kontejneru pro `behavior` prvky, které definují chování pro službu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="fc44e-178">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fc44e-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="fc44e-179">\<Chování > – Element</span><span class="sxs-lookup"><span data-stu-id="fc44e-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="fc44e-180">Každý `behavior` element je identifikován `name` atribut a poskytuje buď poskytnuté systémem chování, například <`throttling`>, nebo vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="fc44e-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="fc44e-181">Pokud není zadán název prvku chování odpovídá výchozí chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="fc44e-182">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fc44e-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="fc44e-183">Jak používat vazby a chování konfigurace</span><span class="sxs-lookup"><span data-stu-id="fc44e-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="fc44e-184">WCF umožňuje snadno sdílet konfigurace mezi koncovými body pomocí referenčního systému v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fc44e-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="fc44e-185">Místo toho přímo konfigurační hodnoty pro koncový bod, související vazby konfigurační hodnoty jsou seskupené ve `bindingConfiguration` prvky `<binding>` části.</span><span class="sxs-lookup"><span data-stu-id="fc44e-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="fc44e-186">Konfigurace vazby je pojmenovaná skupina nastavení na vazbu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="fc44e-187">Koncové body můžete odkázat `bindingConfiguration` podle názvu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fc44e-188">`name` z `bindingConfiguration` je nastavena v `<binding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="fc44e-189">`name` Musí být jedinečný řetězec v rámci oboru typ vazby – v tomto případě [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), nebo prázdná hodnota pro odkazování na výchozí vazby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="fc44e-190">Koncový bod odkazy na konfiguraci tak, že nastavíte `bindingConfiguration` atributu na řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc44e-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="fc44e-191">A `behaviorConfiguration` je implementováno stejným způsobem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fc44e-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fc44e-192">Všimněte si, že výchozí sadu chování služby jsou přidány do služby.</span><span class="sxs-lookup"><span data-stu-id="fc44e-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="fc44e-193">Tento systém umožňuje koncové body sdílení obvyklé konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="fc44e-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="fc44e-194">Pokud celý počítač obor je požadován, vytvoření vazby nebo chování konfigurace v souboru Machine.config. Nastavení konfigurace jsou k dispozici ve všech souborech App.config.</span><span class="sxs-lookup"><span data-stu-id="fc44e-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="fc44e-195">[Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytvoření konfigurací.</span><span class="sxs-lookup"><span data-stu-id="fc44e-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="fc44e-196">Chování sloučení</span><span class="sxs-lookup"><span data-stu-id="fc44e-196">Behavior Merge</span></span>  
 <span data-ttu-id="fc44e-197">Slučovací funkce chování usnadňuje správu chování, pokud chcete sadu společné chování, který se má použít konzistentně.</span><span class="sxs-lookup"><span data-stu-id="fc44e-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="fc44e-198">Tato funkce umožňuje určit chování na různých úrovních hierarchie configuration a služby dědit z více úrovní hierarchie konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="fc44e-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="fc44e-199">Pro ilustraci jak tohle funguje Předpokládejme, že máte následující virtuální adresář rozložení ve službě IIS:</span><span class="sxs-lookup"><span data-stu-id="fc44e-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="fc44e-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="fc44e-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="fc44e-201">A ~\Web.config soubor má následující obsah:</span><span class="sxs-lookup"><span data-stu-id="fc44e-201">And your ~\Web.config file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fc44e-202">A jste dítě tohoto souboru Web.config umístěný v ~\Child\Web.config s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="fc44e-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fc44e-203">Služby umístěné v ~\Child\Service.svc se bude chovat, jako by byl serviceDebug i serviceMetadata chování.</span><span class="sxs-lookup"><span data-stu-id="fc44e-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="fc44e-204">Chování serviceDebug bude mít jenom služby umístěné v ~\Service.svc.</span><span class="sxs-lookup"><span data-stu-id="fc44e-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="fc44e-205">Co se stane, je, že se sloučí dvě chování kolekce se stejným názvem (v tomto případě prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="fc44e-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="fc44e-206">Chování kolekce můžete také zrušit pomocí \<vymazat > Označit a odebrat jednotlivé chování z kolekce pomocí \<odebrat > značky.</span><span class="sxs-lookup"><span data-stu-id="fc44e-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="fc44e-207">Například následující dvě konfigurace výsledky v podřízeném služeb s pouze serviceMetadata chování:</span><span class="sxs-lookup"><span data-stu-id="fc44e-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fc44e-208">Chování sloučení je Hotovo nameless chování kolekcí, jak je znázorněno výše a s názvem také kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="fc44e-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="fc44e-209">Sloučení chování funguje ve službě IIS hostitelské prostředí, ve které sloučit soubory Web.config hierarchicky s kořenový soubor Web.config a souboru machine.config. Funguje to ovšem i v prostředí aplikace, kde můžete machine.config sloučit s soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="fc44e-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="fc44e-210">Sloučení chování platí pro chování koncového bodu a chování služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fc44e-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="fc44e-211">Pokud podřízená kolekce chování obsahuje chování, které je již v kolekci chování nadřazeného, podřízené chování potlačuje nadřazené.</span><span class="sxs-lookup"><span data-stu-id="fc44e-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="fc44e-212">Ano, pokud kolekce chování nadřazených `<serviceMetadata httpGetEnabled="False" />` a podřízené kolekce chování měli `<serviceMetadata httpGetEnabled="True" />`podřízené chování by se mělo přepsat chování nadřazené v kolekci chování a httpGetEnabled by být "true".</span><span class="sxs-lookup"><span data-stu-id="fc44e-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc44e-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc44e-213">See Also</span></span>  
 [<span data-ttu-id="fc44e-214">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="fc44e-214">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="fc44e-215">Konfigurace aplikací Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fc44e-215">Configuring Windows Communication Foundation Applications</span></span>](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="fc44e-216">\<service></span><span class="sxs-lookup"><span data-stu-id="fc44e-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="fc44e-217">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="fc44e-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
