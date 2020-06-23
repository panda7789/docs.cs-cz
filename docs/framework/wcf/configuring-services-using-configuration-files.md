---
title: Konfigurace služeb pomocí konfiguračních souborů
description: Přečtěte si, jak konfigurační soubor pro službu WCF poskytuje flexibilitu při poskytování dat o chování koncových bodů a služeb během nasazení.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 1a3266ad8890436c9be9d0f2b231aeaca0f9236e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245424"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="601e3-103">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="601e3-103">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="601e3-104">Konfigurace služby Windows Communication Foundation (WCF) pomocí konfiguračního souboru vám poskytne flexibilitu při poskytování dat o chování koncových bodů a služeb v bodě nasazení místo v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="601e3-104">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="601e3-105">Toto téma popisuje primární techniky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="601e3-105">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="601e3-106">Služba WCF se dá konfigurovat pomocí technologie konfigurace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="601e3-106">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="601e3-107">Nejčastěji se prvky XML přidávají do souboru Web.config pro web Internetová informační služba (IIS), který je hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="601e3-107">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="601e3-108">Tyto prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používané ke komunikaci se službou) na počítačích jednotlivých počítačů.</span><span class="sxs-lookup"><span data-stu-id="601e3-108">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="601e3-109">Kromě toho WCF zahrnuje několik prvků poskytovaných systémem, které umožňují rychle vybrat základní funkce pro službu.</span><span class="sxs-lookup"><span data-stu-id="601e3-109">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="601e3-110">Počínaje .NET Framework 4 přichází WCF k dispozici nový výchozí konfigurační model, který zjednodušuje požadavky na konfiguraci WCF.</span><span class="sxs-lookup"><span data-stu-id="601e3-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="601e3-111">Pokud neposkytnete konfiguraci služby WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s některými standardními koncovými body a výchozí vazbou/chování.</span><span class="sxs-lookup"><span data-stu-id="601e3-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="601e3-112">V praxi je psaní konfigurace hlavní součástí programování aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="601e3-112">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="601e3-113">Další informace najdete v tématu [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="601e3-113">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="601e3-114">Seznam nejčastěji používaných prvků najdete v tématu [vazby poskytované systémem](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="601e3-114">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="601e3-115">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="601e3-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="601e3-116">Při nasazování souběžných scénářů, kde jsou nasazeny dvě různé verze služby, je nutné zadat částečné názvy sestavení, na které se odkazuje v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="601e3-116">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="601e3-117">Je to proto, že konfigurační soubor je sdílen napříč všemi verzemi služby a mohl by být spuštěn v různých verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="601e3-117">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="601e3-118">System.Configuration: Web.config a App.config</span><span class="sxs-lookup"><span data-stu-id="601e3-118">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="601e3-119">WCF používá konfigurační systém System.Configuration .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="601e3-119">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="601e3-120">Při konfiguraci služby v aplikaci Visual Studio použijte k zadání nastavení buď soubor Web.config, nebo App.config soubor.</span><span class="sxs-lookup"><span data-stu-id="601e3-120">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="601e3-121">Volba názvu konfiguračního souboru je určena hostujícím prostředím, které jste si zvolili pro službu.</span><span class="sxs-lookup"><span data-stu-id="601e3-121">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="601e3-122">Pokud používáte službu IIS k hostování vaší služby, použijte soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="601e3-122">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="601e3-123">Pokud používáte jiné hostitelské prostředí, použijte soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="601e3-123">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="601e3-124">V aplikaci Visual Studio se k vytvoření finálního konfiguračního souboru používá soubor s názvem App.config.</span><span class="sxs-lookup"><span data-stu-id="601e3-124">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="601e3-125">Konečný název, který je ve skutečnosti použitý pro konfiguraci, závisí na názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="601e3-125">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="601e3-126">Například sestavení s názvem "Cohowinery.exe" má konečný název konfiguračního souboru "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="601e3-126">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="601e3-127">Je však třeba upravit soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="601e3-127">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="601e3-128">Změny provedené v tomto souboru jsou automaticky provedeny v konečném konfiguračním souboru aplikace v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="601e3-128">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="601e3-129">V části použití App.config se zaznamená, že konfigurační systém sloučí App.config soubor s obsahem Machine.config souboru při spuštění aplikace a použije se konfigurace.</span><span class="sxs-lookup"><span data-stu-id="601e3-129">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="601e3-130">Tento mechanismus umožňuje definovat nastavení pro všechny počítače v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="601e3-130">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="601e3-131">Soubor App.config lze použít k přepsání nastavení Machine.config souboru; Můžete také uzamknout nastavení v souboru Machine.config tak, aby se používala.</span><span class="sxs-lookup"><span data-stu-id="601e3-131">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="601e3-132">V případě Web.config konfigurační systém sloučí Web.config soubory ve všech adresářích až do adresáře aplikace do konfigurace, která se použije.</span><span class="sxs-lookup"><span data-stu-id="601e3-132">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="601e3-133">Další informace o konfiguraci a prioritách nastavení naleznete v tématech v <xref:System.Configuration> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="601e3-133">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="601e3-134">Hlavní části konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="601e3-134">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="601e3-135">Hlavní části konfiguračního souboru obsahují následující prvky.</span><span class="sxs-lookup"><span data-stu-id="601e3-135">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="601e3-136">Části vazby a chování jsou volitelné a jsou zahrnuty pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="601e3-136">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="601e3-137">\<services>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-137">The \<services> Element</span></span>  
 <span data-ttu-id="601e3-138">`services`Element obsahuje specifikace pro všechny služby, které jsou hostiteli aplikace.</span><span class="sxs-lookup"><span data-stu-id="601e3-138">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="601e3-139">Počínaje zjednodušeným modelem konfigurace v .NET Framework 4 je tato část volitelná.</span><span class="sxs-lookup"><span data-stu-id="601e3-139">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="601e3-140">\<service>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-140">The \<service> Element</span></span>  
 <span data-ttu-id="601e3-141">Každá služba má tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="601e3-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="601e3-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="601e3-142">`name`.</span></span> <span data-ttu-id="601e3-143">Určuje typ, který poskytuje implementaci kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="601e3-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="601e3-144">Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečky a názvu typu.</span><span class="sxs-lookup"><span data-stu-id="601e3-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="601e3-145">Například `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="601e3-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="601e3-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="601e3-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="601e3-147">Určuje název jednoho z `behavior` prvků nalezených v `behaviors` elementu.</span><span class="sxs-lookup"><span data-stu-id="601e3-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="601e3-148">Zadané chování řídí akce, například zda služba umožňuje zosobnění.</span><span class="sxs-lookup"><span data-stu-id="601e3-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="601e3-149">Pokud je jeho hodnota prázdný název, nebo není zadána žádná, bude `behaviorConfiguration` do služby přidána výchozí sada chování služby.</span><span class="sxs-lookup"><span data-stu-id="601e3-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="601e3-150">\<endpoint>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-150">The \<endpoint> Element</span></span>  
 <span data-ttu-id="601e3-151">Každý koncový bod vyžaduje adresu, vazbu a kontrakt, které jsou reprezentované následujícími atributy:</span><span class="sxs-lookup"><span data-stu-id="601e3-151">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="601e3-152">`address`.</span><span class="sxs-lookup"><span data-stu-id="601e3-152">`address`.</span></span> <span data-ttu-id="601e3-153">Určuje identifikátor URI (Uniform Resource Identifier) služby, který může být absolutní adresa nebo jedna z nich relativní vzhledem k základní adrese služby.</span><span class="sxs-lookup"><span data-stu-id="601e3-153">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="601e3-154">Pokud je parametr nastaven na prázdný řetězec, znamená to, že koncový bod je k dispozici na základní adrese, která je určena při vytváření <xref:System.ServiceModel.ServiceHost> služby pro službu.</span><span class="sxs-lookup"><span data-stu-id="601e3-154">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="601e3-155">`binding`.</span><span class="sxs-lookup"><span data-stu-id="601e3-155">`binding`.</span></span> <span data-ttu-id="601e3-156">Obvykle určuje systémovou vazbu <xref:System.ServiceModel.WSHttpBinding> , jako je, ale může také specifikovat uživatelsky definované vazby.</span><span class="sxs-lookup"><span data-stu-id="601e3-156">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="601e3-157">Zadaná vazba určuje typ přenosu, zabezpečení a používaného kódování a to, jestli jsou podporované nebo povolené spolehlivé relace, transakce nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="601e3-157">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="601e3-158">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="601e3-158">`bindingConfiguration`.</span></span> <span data-ttu-id="601e3-159">Pokud je nutné upravit výchozí hodnoty vazby, lze to provést nakonfigurováním příslušného `binding` prvku v `bindings` elementu.</span><span class="sxs-lookup"><span data-stu-id="601e3-159">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="601e3-160">Tento atribut by měl mít stejnou hodnotu jako `name` atribut `binding` prvku, který se používá ke změně výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="601e3-160">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="601e3-161">Pokud není zadán žádný název nebo pokud není `bindingConfiguration` zadána žádná vazba, je v tomto koncovém bodu použita výchozí vazba typu vazby.</span><span class="sxs-lookup"><span data-stu-id="601e3-161">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="601e3-162">`contract`.</span><span class="sxs-lookup"><span data-stu-id="601e3-162">`contract`.</span></span> <span data-ttu-id="601e3-163">Určuje rozhraní, které definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="601e3-163">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="601e3-164">Toto je rozhraní implementované v typu modulu CLR (Common Language Runtime) určeném `name` atributem `service` elementu.</span><span class="sxs-lookup"><span data-stu-id="601e3-164">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="601e3-165">\<bindings>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-165">The \<bindings> Element</span></span>  
 <span data-ttu-id="601e3-166">`bindings`Element obsahuje specifikace pro všechny vazby, které mohou být použity jakýmkoli koncovým bodem definovaným v jakékoli službě.</span><span class="sxs-lookup"><span data-stu-id="601e3-166">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="601e3-167">\<binding>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-167">The \<binding> Element</span></span>  
 <span data-ttu-id="601e3-168">`binding`Prvky obsažené v `bindings` elementu mohou být buď jedna z těchto vazeb poskytovaných systémem (viz téma [vazby poskytnuté systémem](system-provided-bindings.md)) nebo vlastní vazba (viz [vlastní vazby](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="601e3-168">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="601e3-169">`binding`Element má `name` atribut, který koreluje vazbu s koncovým bodem zadaným v `bindingConfiguration` atributu `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="601e3-169">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="601e3-170">Pokud název není zadán, bude tato vazba odpovídat výchozímu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="601e3-170">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="601e3-171">Další informace o konfiguraci služeb a klientů najdete v tématu [Konfigurace služeb WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="601e3-171">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="601e3-172">\<behaviors>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-172">The \<behaviors> Element</span></span>  
 <span data-ttu-id="601e3-173">Toto je prvek kontejneru pro `behavior` prvky, které definují chování pro službu.</span><span class="sxs-lookup"><span data-stu-id="601e3-173">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="601e3-174">\<behavior>Element</span><span class="sxs-lookup"><span data-stu-id="601e3-174">The \<behavior> Element</span></span>  
 <span data-ttu-id="601e3-175">Každý `behavior` element je identifikován `name` atributem a poskytuje buď chování poskytované systémem, například <`throttling`> nebo vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="601e3-175">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="601e3-176">Pokud název není zadán, bude tento prvek chování odpovídat výchozímu chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="601e3-176">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="601e3-177">Jak používat konfigurace vazeb a chování</span><span class="sxs-lookup"><span data-stu-id="601e3-177">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="601e3-178">Technologie WCF usnadňuje sdílení konfigurací mezi koncovými body pomocí referenčního systému v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="601e3-178">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="601e3-179">Místo přímého přiřazování hodnot konfigurace koncovému bodu jsou konfigurační hodnoty související s vazbami seskupeny do `bindingConfiguration` prvků v `<binding>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="601e3-179">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="601e3-180">Konfigurace vazby je pojmenovaná skupina nastavení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="601e3-180">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="601e3-181">Koncové body pak mohou odkazovat `bindingConfiguration` podle názvu.</span><span class="sxs-lookup"><span data-stu-id="601e3-181">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="601e3-182">`name` `bindingConfiguration` Je nastaven v `<binding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="601e3-182">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="601e3-183">`name`Musí být jedinečný řetězec v rámci oboru typu vazby – v tomto případě [<\> BasicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md)nebo prázdná hodnota pro odkazování na výchozí vazbu.</span><span class="sxs-lookup"><span data-stu-id="601e3-183">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="601e3-184">Koncový bod odkazuje na konfiguraci nastavením `bindingConfiguration` atributu na tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="601e3-184">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="601e3-185">A `behaviorConfiguration` je implementován stejným způsobem, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="601e3-185">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="601e3-186">Všimněte si, že se do služby přidala výchozí sada chování služby.</span><span class="sxs-lookup"><span data-stu-id="601e3-186">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="601e3-187">Tento systém umožňuje koncovým bodům sdílet společné konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="601e3-187">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="601e3-188">Je-li požadován obor v rámci rozsahu počítače, vytvořte v Machine.config konfiguraci vazby nebo chování. Konfigurační nastavení jsou k dispozici ve všech App.config souborech.</span><span class="sxs-lookup"><span data-stu-id="601e3-188">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="601e3-189">[Nástroj Editor konfigurací (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytváření konfigurací.</span><span class="sxs-lookup"><span data-stu-id="601e3-189">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="601e3-190">Sloučení chování</span><span class="sxs-lookup"><span data-stu-id="601e3-190">Behavior Merge</span></span>  
 <span data-ttu-id="601e3-191">Funkce sloučení chování usnadňuje správu chování, když chcete, aby se sada běžných chování používala konzistentně.</span><span class="sxs-lookup"><span data-stu-id="601e3-191">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="601e3-192">Tato funkce umožňuje zadat chování na různých úrovních konfigurační hierarchie a mít služby dědění chování z více úrovní konfigurační hierarchie.</span><span class="sxs-lookup"><span data-stu-id="601e3-192">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="601e3-193">K tomu, abyste se vypředpokládali, jak to funguje, máte ve službě IIS následující rozložení virtuálních adresářů:</span><span class="sxs-lookup"><span data-stu-id="601e3-193">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="601e3-194">A `~\Web.config` soubor má následující obsah:</span><span class="sxs-lookup"><span data-stu-id="601e3-194">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="601e3-195">A máte podřízený Web.config nacházející se v umístění ~\Child\Web.config s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="601e3-195">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="601e3-196">Služba, která se nachází na ~ \Child\Service.svc, se bude chovat, jako by se jednalo o chování serviceDebug a oddílu serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="601e3-196">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="601e3-197">Služba nacházející se na ~ \Service.svc bude mít pouze chování serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="601e3-197">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="601e3-198">K tomu dochází, když se sloučí dvě kolekce chování se stejným názvem (v tomto případě je to prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="601e3-198">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="601e3-199">Můžete také vymazat kolekce chování pomocí \<clear> značky a odebrat jednotlivá chování z kolekce pomocí \<remove> značky.</span><span class="sxs-lookup"><span data-stu-id="601e3-199">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="601e3-200">Například následující dvě výsledky konfigurace v podřízené službě mají pouze chování oddílu serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="601e3-200">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="601e3-201">Sloučení chování je provedeno pro kolekce chování Nameless, jak je uvedeno výše, a pojmenované kolekce chování také.</span><span class="sxs-lookup"><span data-stu-id="601e3-201">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="601e3-202">Sloučení chování funguje v hostitelském prostředí služby IIS, ve kterém se Web.config soubory sloučí hierarchicky s kořenovým Web.config souborem a machine.config. Ale funguje i v prostředí aplikace, kde se machine.config můžou sloučit se souborem App.config.</span><span class="sxs-lookup"><span data-stu-id="601e3-202">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="601e3-203">Sloučení chování se aplikuje na chování koncového bodu i na chování služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="601e3-203">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="601e3-204">Pokud kolekce podřízených chování obsahuje chování, které již je přítomno v nadřazené kolekci chování, podřízené chování přepíše nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="601e3-204">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="601e3-205">Takže pokud kolekce nadřazených chování měla `<serviceMetadata httpGetEnabled="False" />` a podřízená kolekce chování měla `<serviceMetadata httpGetEnabled="True" />` , může podřízené chování přepsat nadřazené chování v kolekci chování a HttpGetEnabled by byla "true".</span><span class="sxs-lookup"><span data-stu-id="601e3-205">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601e3-206">Viz také</span><span class="sxs-lookup"><span data-stu-id="601e3-206">See also</span></span>

- [<span data-ttu-id="601e3-207">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="601e3-207">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="601e3-208">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="601e3-208">Configuring WCF services</span></span>](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
