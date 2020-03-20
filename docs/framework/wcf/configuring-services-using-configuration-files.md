---
title: Konfigurace služeb pomocí konfiguračních souborů
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174794"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="a84ca-102">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="a84ca-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="a84ca-103">Konfigurace služby WCF (Windows Communication Foundation) s konfiguračním souborem poskytuje data o chování koncového bodu a služby v okamžiku nasazení namísto v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="a84ca-104">Toto téma popisuje primární techniky, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a84ca-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="a84ca-105">Služba WCF je konfigurovatelná pomocí konfigurační technologie rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a84ca-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="a84ca-106">Nejčastěji jsou prvky XML přidány do souboru Web.config pro web Internetové informační služby (IIS), který je hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a84ca-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="a84ca-107">Prvky umožňují změnit podrobnosti, jako jsou adresy koncového bodu (skutečné adresy používané ke komunikaci se službou) na základě strojpo počítači.</span><span class="sxs-lookup"><span data-stu-id="a84ca-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="a84ca-108">WCF navíc obsahuje několik prvků poskytovaných systémem, které umožňují rychle vybrat nejzákladnější funkce pro službu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="a84ca-109">Počínaje rozhraním .NET Framework 4 je wcf dodáván s novým výchozím konfiguračním modelem, který zjednodušuje požadavky na konfiguraci WCF.</span><span class="sxs-lookup"><span data-stu-id="a84ca-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="a84ca-110">Pokud nezadáte žádnou konfiguraci WCF pro konkrétní službu, runtime automaticky nakonfiguruje službu s některými standardními koncovými body a výchozí vazbou/chováním.</span><span class="sxs-lookup"><span data-stu-id="a84ca-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="a84ca-111">V praxi je konfigurace zápisu hlavní součástí programování aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="a84ca-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="a84ca-112">Další informace naleznete [v tématu Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a84ca-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="a84ca-113">Seznam nejčastěji používaných prvků naleznete v tématu [Vazby poskytované systémem](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a84ca-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="a84ca-114">Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a84ca-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a84ca-115">Při nasazování souběžných scénářů, kde jsou nasazeny dvě různé verze služby, je nutné zadat částečné názvy sestavení odkazovaných v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="a84ca-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="a84ca-116">Důvodem je, že konfigurační soubor je sdílen ve všech verzích služby a mohou být spuštěny v různých verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a84ca-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="a84ca-117">System.Configuration: Web.config a App.config</span><span class="sxs-lookup"><span data-stu-id="a84ca-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="a84ca-118">WCF používá konfigurační systém System.Configuration rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a84ca-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a84ca-119">Při konfiguraci služby v sadě Visual Studio určete nastavení pomocí souboru Web.config nebo souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="a84ca-120">Volba názvu konfiguračního souboru je určena hostitelským prostředím, které zvolíte pro službu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="a84ca-121">Pokud používáte službu IIS k hostování služby, použijte soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="a84ca-122">Pokud používáte jiné hostitelské prostředí, použijte soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="a84ca-123">V sadě Visual Studio se soubor s názvem App.config používá k vytvoření konečného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a84ca-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="a84ca-124">Konečný název skutečně použitý pro konfiguraci závisí na názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="a84ca-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="a84ca-125">Například sestavení s názvem "Cohowinery.exe" má konečný název konfiguračního souboru "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="a84ca-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="a84ca-126">Je však třeba upravit pouze soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="a84ca-127">Změny provedené v tomto souboru jsou automaticky provedeny do konečného konfiguračního souboru aplikace v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a84ca-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="a84ca-128">Při použití souboru App.config sloučí soubor Konfigurace souboru App.config s obsahem souboru Machine.config při spuštění aplikace a použití konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a84ca-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="a84ca-129">Tento mechanismus umožňuje nastavení celého počítače, které mají být definovány v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="a84ca-130">Soubor App.config lze použít k přepsání nastavení souboru Machine.config; můžete také zamknout v nastavení v souboru Machine.config tak, aby si zvykli.</span><span class="sxs-lookup"><span data-stu-id="a84ca-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="a84ca-131">V případě Web.config sloučí konfigurační systém soubory Web.config ve všech adresářích, které vedou k adresáři aplikace, do konfigurace, která bude použita.</span><span class="sxs-lookup"><span data-stu-id="a84ca-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="a84ca-132">Další informace o konfiguraci a prioritách <xref:System.Configuration> nastavení naleznete v tématech v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a84ca-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="a84ca-133">Hlavní části konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a84ca-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="a84ca-134">Hlavní části konfiguračního souboru obsahují následující prvky.</span><span class="sxs-lookup"><span data-stu-id="a84ca-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
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
> <span data-ttu-id="a84ca-135">Vazby a chování oddíly jsou volitelné a jsou zahrnuty pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="a84ca-136">Služby \<> Element</span><span class="sxs-lookup"><span data-stu-id="a84ca-136">The \<services> Element</span></span>  
 <span data-ttu-id="a84ca-137">Prvek `services` obsahuje specifikace pro všechny služby, které aplikace hostuje.</span><span class="sxs-lookup"><span data-stu-id="a84ca-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="a84ca-138">Počínaje zjednodušeným konfiguračním modelem v rozhraní .NET Framework 4 je tato část volitelná.</span><span class="sxs-lookup"><span data-stu-id="a84ca-138">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [<span data-ttu-id="a84ca-139">\<služby></span><span class="sxs-lookup"><span data-stu-id="a84ca-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="a84ca-140">Služba \<> Element</span><span class="sxs-lookup"><span data-stu-id="a84ca-140">The \<service> Element</span></span>  
 <span data-ttu-id="a84ca-141">Každá služba má tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="a84ca-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="a84ca-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-142">`name`.</span></span> <span data-ttu-id="a84ca-143">Určuje typ, který poskytuje implementaci servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="a84ca-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="a84ca-144">Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečky a potom názvu typu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="a84ca-145">Například `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="a84ca-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="a84ca-147">Určuje název jednoho z `behavior` prvků nalezených `behaviors` v prvku.</span><span class="sxs-lookup"><span data-stu-id="a84ca-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="a84ca-148">Zadané chování řídí akce, jako je například zda služba umožňuje zosobnění.</span><span class="sxs-lookup"><span data-stu-id="a84ca-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="a84ca-149">Pokud je jeho hodnota prázdný `behaviorConfiguration` název nebo ne je k dispozici, pak je do služby přidána výchozí sada chování služby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="a84ca-150">\<servisní></span><span class="sxs-lookup"><span data-stu-id="a84ca-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="a84ca-151">Koncový \<bod> element</span><span class="sxs-lookup"><span data-stu-id="a84ca-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="a84ca-152">Každý koncový bod vyžaduje adresu, vazbu a smlouvu, které jsou reprezentovány následujícími atributy:</span><span class="sxs-lookup"><span data-stu-id="a84ca-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="a84ca-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-153">`address`.</span></span> <span data-ttu-id="a84ca-154">Určuje identifikátor URI (Uniform Resource Identifier) služby, což může být absolutní adresa nebo adresa, která je dána vzhledem k základní adrese služby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="a84ca-155">Pokud je nastavena na prázdný řetězec, znamená to, že koncový bod <xref:System.ServiceModel.ServiceHost> je k dispozici na základní adrese, která je určena při vytváření pro službu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="a84ca-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-156">`binding`.</span></span> <span data-ttu-id="a84ca-157">Obvykle určuje systémem poskytované <xref:System.ServiceModel.WSHttpBinding>vazby jako , ale můžete také určit uživatelem definované vazby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="a84ca-158">Zadaná vazba určuje typ přenosu, zabezpečení a kódování a zda jsou podporovány nebo povoleny spolehlivé relace, transakce nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="a84ca-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="a84ca-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-159">`bindingConfiguration`.</span></span> <span data-ttu-id="a84ca-160">Pokud musí být změněny výchozí hodnoty vazby, lze to `binding` provést `bindings` konfigurací příslušného prvku v elementu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="a84ca-161">Tento atribut by měl mít `name` stejnou hodnotu jako atribut `binding` prvku, který se používá ke změně výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="a84ca-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="a84ca-162">Pokud není zadán žádný `bindingConfiguration` název nebo není zadán žádný ve vazbě, použije se v koncovém bodě výchozí vazba typu vazby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="a84ca-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="a84ca-163">`contract`.</span></span> <span data-ttu-id="a84ca-164">Určuje rozhraní, které definuje smlouvu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="a84ca-165">Toto je rozhraní implementované v typu CLR (CLR) jazyka určeného `name` atributem `service` prvku.</span><span class="sxs-lookup"><span data-stu-id="a84ca-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="a84ca-166">\<>koncového bodu</span><span class="sxs-lookup"><span data-stu-id="a84ca-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="a84ca-167">Vazby \<> Element</span><span class="sxs-lookup"><span data-stu-id="a84ca-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="a84ca-168">Prvek `bindings` obsahuje specifikace pro všechny vazby, které lze použít libovolný koncový bod definovaný v libovolné službě.</span><span class="sxs-lookup"><span data-stu-id="a84ca-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="a84ca-169">\<vázání></span><span class="sxs-lookup"><span data-stu-id="a84ca-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="a84ca-170">Vazba \<> Element</span><span class="sxs-lookup"><span data-stu-id="a84ca-170">The \<binding> Element</span></span>  
 <span data-ttu-id="a84ca-171">Prvky `binding` obsažené v `bindings` prvku může být buď jeden ze systémem poskytované vazby (viz [System-Provided Vazby)](system-provided-bindings.md)nebo vlastní vazby (viz [vlastní vazby).](./extending/custom-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a84ca-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="a84ca-172">Prvek `binding` má `name` atribut, který koreluje vazbu s `bindingConfiguration` koncovým `endpoint` bodem zadaným v atributu prvku.</span><span class="sxs-lookup"><span data-stu-id="a84ca-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="a84ca-173">Pokud není zadán žádný název, pak tato vazba odpovídá výchozí mu typ vazby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="a84ca-174">Další informace o konfiguraci služeb a klientů naleznete v [tématu Konfigurace služeb WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="a84ca-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="a84ca-175">\<závazné></span><span class="sxs-lookup"><span data-stu-id="a84ca-175">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="a84ca-176">Chování \<> Element</span><span class="sxs-lookup"><span data-stu-id="a84ca-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="a84ca-177">Toto je prvek `behavior` kontejneru pro prvky, které definují chování pro službu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="a84ca-178">\<chování></span><span class="sxs-lookup"><span data-stu-id="a84ca-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="a84ca-179">Chování \<> Element</span><span class="sxs-lookup"><span data-stu-id="a84ca-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="a84ca-180">Každý `behavior` prvek je `name` identifikován atributem a poskytuje buď systémové `throttling` chování, například <> nebo vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="a84ca-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="a84ca-181">Pokud není uveden žádný název, pak tento prvek chování odpovídá výchozí službě nebo chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="a84ca-182">\<chování></span><span class="sxs-lookup"><span data-stu-id="a84ca-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="a84ca-183">Použití konfigurace vazby a chování</span><span class="sxs-lookup"><span data-stu-id="a84ca-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="a84ca-184">WCF usnadňuje sdílení konfigurací mezi koncovými body pomocí referenčního systému v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a84ca-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="a84ca-185">Spíše než přímo přiřazení konfiguračních hodnot ke koncovému `bindingConfiguration` bodu, `<binding>` hodnoty konfigurace související s vazbou jsou seskupeny do prvků v části.</span><span class="sxs-lookup"><span data-stu-id="a84ca-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="a84ca-186">Konfigurace vazby je pojmenovaná skupina nastavení na vazbě.</span><span class="sxs-lookup"><span data-stu-id="a84ca-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="a84ca-187">Koncové body pak `bindingConfiguration` mohou odkazovat na název podle.</span><span class="sxs-lookup"><span data-stu-id="a84ca-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
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
  
 <span data-ttu-id="a84ca-188">`bindingConfiguration` `<binding>` Je `name` nastavena v prvku.</span><span class="sxs-lookup"><span data-stu-id="a84ca-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="a84ca-189">Musí `name` být jedinečný řetězec v rámci oboru typu vazby – v tomto případě [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md)nebo prázdnou hodnotu odkazovat na výchozí vazbu.</span><span class="sxs-lookup"><span data-stu-id="a84ca-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="a84ca-190">Koncový bod odkazuje na konfiguraci `bindingConfiguration` nastavením atributu na tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="a84ca-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="a84ca-191">A `behaviorConfiguration` je implementována stejným způsobem, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="a84ca-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="a84ca-192">Všimněte si, že výchozí sada chování služby jsou přidány do služby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="a84ca-193">Tento systém umožňuje koncovým bodům sdílet běžné konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="a84ca-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="a84ca-194">Pokud je vyžadován obor celého počítače, vytvořte konfiguraci vazby nebo chování v souboru Machine.config. Nastavení konfigurace jsou k dispozici ve všech souborech App.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="a84ca-195">[Nástroj Editor konfigurace (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytváření konfigurací.</span><span class="sxs-lookup"><span data-stu-id="a84ca-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="a84ca-196">Sloučení chování</span><span class="sxs-lookup"><span data-stu-id="a84ca-196">Behavior Merge</span></span>  
 <span data-ttu-id="a84ca-197">Funkce sloučení chování usnadňuje správu chování, pokud chcete, aby sada běžných chování byla použita konzistentně.</span><span class="sxs-lookup"><span data-stu-id="a84ca-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="a84ca-198">Tato funkce umožňuje určit chování na různých úrovních hierarchie konfigurace a nechat služby dědit chování z více úrovní hierarchie konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a84ca-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="a84ca-199">Pro ilustraci, jak to funguje, předpokládáte, že máte ve službě IIS následující rozložení virtuálního adresáře:</span><span class="sxs-lookup"><span data-stu-id="a84ca-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="a84ca-200">A `~\Web.config` váš soubor má následující obsah:</span><span class="sxs-lookup"><span data-stu-id="a84ca-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="a84ca-201">A máte podřízený web.config umístěný na adrese ~\Child\Web.config s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="a84ca-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="a84ca-202">Služba umístěná na adrese ~\Child\Service.svc se bude chovat, jako by měla chování ladění a metadat služby.</span><span class="sxs-lookup"><span data-stu-id="a84ca-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="a84ca-203">Služba umístěná na adrese ~\Service.svc bude mít pouze chování serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="a84ca-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="a84ca-204">Co se stane, je, že dvě kolekce chování se stejným názvem (v tomto případě prázdný řetězec) jsou sloučeny.</span><span class="sxs-lookup"><span data-stu-id="a84ca-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="a84ca-205">Kolekce chování můžete také vymazat \<pomocí značky clear> a odebráním \<jednotlivých chování z kolekce pomocí značky remove>.</span><span class="sxs-lookup"><span data-stu-id="a84ca-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="a84ca-206">Například následující dvě konfigurace výsledky v podřízené služby s pouze serviceMetadata chování:</span><span class="sxs-lookup"><span data-stu-id="a84ca-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="a84ca-207">Sloučení chování se provádí pro bezejmenné kolekce chování, jak je uvedeno výše a pojmenované kolekce chování také.</span><span class="sxs-lookup"><span data-stu-id="a84ca-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="a84ca-208">Sloučení chování funguje v hostitelském prostředí služby IIS, ve kterém se soubory Web.config hierarchicky slučují s kořenovým souborem Web.config a machine.config. Ale funguje také v aplikačním prostředí, kde machine.config může sloučit se souborem App.config.</span><span class="sxs-lookup"><span data-stu-id="a84ca-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="a84ca-209">Sloučení chování platí pro chování koncového bodu a chování služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a84ca-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="a84ca-210">Pokud kolekce podřízené chování obsahuje chování, které je již k dispozici v nadřazené kolekci chování, podřízené chování přepíše nadřazené.</span><span class="sxs-lookup"><span data-stu-id="a84ca-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="a84ca-211">Takže pokud nadřazené kolekce chování měl `<serviceMetadata httpGetEnabled="False" />` a podřízené chování kolekce měla `<serviceMetadata httpGetEnabled="True" />`, podřízené chování by přepsat nadřazené chování v kolekci chování a httpGetEnabled by být "true".</span><span class="sxs-lookup"><span data-stu-id="a84ca-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84ca-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="a84ca-212">See also</span></span>

- [<span data-ttu-id="a84ca-213">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="a84ca-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="a84ca-214">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="a84ca-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="a84ca-215">\<servisní></span><span class="sxs-lookup"><span data-stu-id="a84ca-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="a84ca-216">\<závazné></span><span class="sxs-lookup"><span data-stu-id="a84ca-216">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)
