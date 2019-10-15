---
title: Konfigurace služeb pomocí konfiguračních souborů
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 9a8db0670fff604cc9db8279ab1566e6e3fd3c8d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320678"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="a6c07-102">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="a6c07-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="a6c07-103">Konfigurace služby Windows Communication Foundation (WCF) pomocí konfiguračního souboru vám poskytne flexibilitu při poskytování dat o chování koncových bodů a služeb v bodě nasazení místo v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="a6c07-104">Toto téma popisuje primární techniky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a6c07-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="a6c07-105">Služba WCF se dá konfigurovat pomocí technologie konfigurace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6c07-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="a6c07-106">Nejčastěji se prvky XML přidávají do souboru Web. config pro web Internetová informační služba (IIS), který je hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a6c07-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="a6c07-107">Tyto prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používané ke komunikaci se službou) na počítačích jednotlivých počítačů.</span><span class="sxs-lookup"><span data-stu-id="a6c07-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="a6c07-108">Kromě toho WCF zahrnuje několik prvků poskytovaných systémem, které umožňují rychle vybrat základní funkce pro službu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="a6c07-109">Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] se WCF dodává s novým výchozím modelem konfigurace, který zjednodušuje požadavky na konfiguraci WCF.</span><span class="sxs-lookup"><span data-stu-id="a6c07-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="a6c07-110">Pokud neposkytnete konfiguraci služby WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s některými standardními koncovými body a výchozí vazbou/chování.</span><span class="sxs-lookup"><span data-stu-id="a6c07-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="a6c07-111">V praxi je psaní konfigurace hlavní součástí programování aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="a6c07-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="a6c07-112">Další informace najdete v tématu [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6c07-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="a6c07-113">Seznam nejčastěji používaných prvků najdete v tématu [vazby poskytované systémem](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a6c07-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="a6c07-114">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6c07-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a6c07-115">Při nasazování souběžných scénářů, kde jsou nasazeny dvě různé verze služby, je nutné zadat částečné názvy sestavení, na které se odkazuje v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="a6c07-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="a6c07-116">Je to proto, že konfigurační soubor je sdílen napříč všemi verzemi služby a mohl by být spuštěn v různých verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6c07-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="a6c07-117">System. Configuration: Web. config a App. config</span><span class="sxs-lookup"><span data-stu-id="a6c07-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="a6c07-118">WCF používá systém konfigurace System. Configuration .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6c07-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a6c07-119">Při konfiguraci služby v aplikaci Visual Studio použijte soubor Web. config nebo App. config k zadání nastavení.</span><span class="sxs-lookup"><span data-stu-id="a6c07-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="a6c07-120">Volba názvu konfiguračního souboru je určena hostujícím prostředím, které jste si zvolili pro službu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="a6c07-121">Pokud používáte službu IIS k hostování vaší služby, použijte soubor Web. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="a6c07-122">Pokud používáte jiné hostitelské prostředí, použijte soubor App. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="a6c07-123">V aplikaci Visual Studio se k vytvoření finálního konfiguračního souboru používá soubor s názvem App. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="a6c07-124">Konečný název, který je ve skutečnosti použitý pro konfiguraci, závisí na názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="a6c07-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="a6c07-125">Například sestavení s názvem "cohowinery. exe" má konečný název konfiguračního souboru "cohowinery. exe. config".</span><span class="sxs-lookup"><span data-stu-id="a6c07-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="a6c07-126">Je však třeba upravit pouze soubor App. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="a6c07-127">Změny provedené v tomto souboru jsou automaticky provedeny v konečném konfiguračním souboru aplikace v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a6c07-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="a6c07-128">V části použití souboru App. config sloučí konfigurační systém soubor App. config s obsahem souboru Machine. config při spuštění aplikace a použije se konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a6c07-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="a6c07-129">Tento mechanismus povoluje definování nastavení v rámci počítače v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="a6c07-130">Soubor App. config lze použít k přepsání nastavení souboru Machine. config; Můžete také uzamknout nastavení v souboru Machine. config tak, aby se používaly.</span><span class="sxs-lookup"><span data-stu-id="a6c07-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="a6c07-131">V případě souboru Web. config sloučí konfigurační systém soubory Web. config ve všech adresářích až do adresáře aplikace do konfigurace, která se použije.</span><span class="sxs-lookup"><span data-stu-id="a6c07-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="a6c07-132">Další informace o konfiguraci a prioritách nastavení najdete v tématech v oboru názvů <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="a6c07-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="a6c07-133">Hlavní části konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a6c07-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="a6c07-134">Hlavní části konfiguračního souboru obsahují následující prvky.</span><span class="sxs-lookup"><span data-stu-id="a6c07-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="a6c07-135">Části vazby a chování jsou volitelné a jsou zahrnuty pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="a6c07-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="a6c07-136">Element \<services ></span><span class="sxs-lookup"><span data-stu-id="a6c07-136">The \<services> Element</span></span>  
 <span data-ttu-id="a6c07-137">Element `services` obsahuje specifikace pro všechny služby, které jsou hostiteli aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6c07-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="a6c07-138">Počínaje zjednodušeným modelem konfigurace v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] je tato část volitelná.</span><span class="sxs-lookup"><span data-stu-id="a6c07-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="a6c07-139">@no__t – 1services ></span><span class="sxs-lookup"><span data-stu-id="a6c07-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="a6c07-140">Element \<service ></span><span class="sxs-lookup"><span data-stu-id="a6c07-140">The \<service> Element</span></span>  
 <span data-ttu-id="a6c07-141">Každá služba má tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="a6c07-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="a6c07-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-142">`name`.</span></span> <span data-ttu-id="a6c07-143">Určuje typ, který poskytuje implementaci kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="a6c07-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="a6c07-144">Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečky a názvu typu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="a6c07-145">Například `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="a6c07-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="a6c07-147">Určuje název jednoho z prvků `behavior` nalezených v prvku `behaviors`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="a6c07-148">Zadané chování řídí akce, například zda služba umožňuje zosobnění.</span><span class="sxs-lookup"><span data-stu-id="a6c07-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="a6c07-149">Pokud je jeho hodnota prázdný název nebo není k dispozici `behaviorConfiguration`, bude do služby přidána výchozí sada chování služby.</span><span class="sxs-lookup"><span data-stu-id="a6c07-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="a6c07-150">@no__t – 1service ></span><span class="sxs-lookup"><span data-stu-id="a6c07-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="a6c07-151">Element \<endpoint ></span><span class="sxs-lookup"><span data-stu-id="a6c07-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="a6c07-152">Každý koncový bod vyžaduje adresu, vazbu a kontrakt, které jsou reprezentované následujícími atributy:</span><span class="sxs-lookup"><span data-stu-id="a6c07-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="a6c07-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-153">`address`.</span></span> <span data-ttu-id="a6c07-154">Určuje identifikátor URI (Uniform Resource Identifier) služby, který může být absolutní adresa nebo jedna z nich relativní vzhledem k základní adrese služby.</span><span class="sxs-lookup"><span data-stu-id="a6c07-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="a6c07-155">Pokud je hodnota nastavena na prázdný řetězec, indikuje to, že koncový bod je k dispozici na základní adrese, která je určena při vytváření <xref:System.ServiceModel.ServiceHost> pro službu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="a6c07-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-156">`binding`.</span></span> <span data-ttu-id="a6c07-157">Obvykle určuje systémovou vazbu, například <xref:System.ServiceModel.WSHttpBinding>, ale může také určit uživatelem definovanou vazbu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="a6c07-158">Zadaná vazba určuje typ přenosu, zabezpečení a používaného kódování a to, jestli jsou podporované nebo povolené spolehlivé relace, transakce nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="a6c07-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="a6c07-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-159">`bindingConfiguration`.</span></span> <span data-ttu-id="a6c07-160">Pokud je nutné upravit výchozí hodnoty vazby, lze to provést konfigurací příslušného prvku `binding` v prvku `bindings`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="a6c07-161">Tento atribut by měl mít stejnou hodnotu jako atribut `name` elementu `binding`, který se používá ke změně výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="a6c07-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="a6c07-162">Není-li zadán žádný název nebo není-li zadán žádný `bindingConfiguration` ve vazbě, je použita výchozí vazba typu vazby v koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="a6c07-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-163">`contract`.</span></span> <span data-ttu-id="a6c07-164">Určuje rozhraní, které definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a6c07-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="a6c07-165">Toto je rozhraní implementované v typu modulu CLR (Common Language Runtime) určeném atributem `name` elementu `service`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="a6c07-166">@no__t – 1endpoint ></span><span class="sxs-lookup"><span data-stu-id="a6c07-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="a6c07-167">Element \<bindings ></span><span class="sxs-lookup"><span data-stu-id="a6c07-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="a6c07-168">Element `bindings` obsahuje specifikace pro všechny vazby, které mohou být použity jakýmkoli koncovým bodem definovaným v jakékoli službě.</span><span class="sxs-lookup"><span data-stu-id="a6c07-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="a6c07-169">@no__t – 1bindings ></span><span class="sxs-lookup"><span data-stu-id="a6c07-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="a6c07-170">Element \<binding ></span><span class="sxs-lookup"><span data-stu-id="a6c07-170">The \<binding> Element</span></span>  
 <span data-ttu-id="a6c07-171">Prvky `binding` obsažené v prvku `bindings` mohou být buď jedna z těchto vazeb poskytovaných systémem (viz téma [vazby poskytnuté systémem](system-provided-bindings.md)), nebo vlastní vazba (viz [vlastní vazby](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="a6c07-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="a6c07-172">Element `binding` má atribut `name`, který koreluje vazbu s koncovým bodem zadaným v atributu `bindingConfiguration` elementu `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="a6c07-173">Pokud název není zadán, bude tato vazba odpovídat výchozímu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="a6c07-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="a6c07-174">Další informace o konfiguraci služeb a klientů najdete v tématu [Konfigurace služeb WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6c07-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="a6c07-175">@no__t – 1binding ></span><span class="sxs-lookup"><span data-stu-id="a6c07-175">\<binding></span></span>](../misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="a6c07-176">Element \<behaviors ></span><span class="sxs-lookup"><span data-stu-id="a6c07-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="a6c07-177">Toto je prvek kontejneru pro prvky `behavior`, které definují chování pro službu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="a6c07-178">@no__t – 1behaviors ></span><span class="sxs-lookup"><span data-stu-id="a6c07-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="a6c07-179">Element \<behavior ></span><span class="sxs-lookup"><span data-stu-id="a6c07-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="a6c07-180">Každý prvek `behavior` je identifikován atributem `name` a poskytuje buď chování poskytované systémem, například < `throttling` > nebo vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="a6c07-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="a6c07-181">Pokud název není zadán, bude tento prvek chování odpovídat výchozímu chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="a6c07-182">@no__t – 1behavior ></span><span class="sxs-lookup"><span data-stu-id="a6c07-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="a6c07-183">Jak používat konfigurace vazeb a chování</span><span class="sxs-lookup"><span data-stu-id="a6c07-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="a6c07-184">Technologie WCF usnadňuje sdílení konfigurací mezi koncovými body pomocí referenčního systému v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a6c07-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="a6c07-185">Místo přímého přiřazování hodnot konfigurace koncovému bodu jsou konfigurační hodnoty související s vazbami seskupeny do `bindingConfiguration` prvků v části `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="a6c07-186">Konfigurace vazby je pojmenovaná skupina nastavení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="a6c07-187">Koncové body pak můžou odkazovat na `bindingConfiguration` podle názvu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="a6c07-188">@No__t-0 `bindingConfiguration` je nastavena v prvku `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="a6c07-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="a6c07-189">@No__t-0 musí být jedinečný řetězec v rámci oboru typu vazby – v tomto případě [< BasicHttpBinding @ no__t-2](../configure-apps/file-schema/wcf/basichttpbinding.md)nebo prázdná hodnota, která odkazuje na výchozí vazbu.</span><span class="sxs-lookup"><span data-stu-id="a6c07-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="a6c07-190">Koncový bod odkazuje na konfiguraci nastavením atributu `bindingConfiguration` na tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="a6c07-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="a6c07-191">@No__t-0 je implementován stejným způsobem, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="a6c07-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="a6c07-192">Všimněte si, že se do služby přidala výchozí sada chování služby.</span><span class="sxs-lookup"><span data-stu-id="a6c07-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="a6c07-193">Tento systém umožňuje koncovým bodům sdílet společné konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="a6c07-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="a6c07-194">Je-li požadován obor v rámci rozsahu počítače, vytvořte konfiguraci vazby nebo chování v souboru Machine. config. Konfigurační nastavení jsou k dispozici ve všech souborech App. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="a6c07-195">[Nástroj Configuration Editor (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytváření konfigurací.</span><span class="sxs-lookup"><span data-stu-id="a6c07-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="a6c07-196">Sloučení chování</span><span class="sxs-lookup"><span data-stu-id="a6c07-196">Behavior Merge</span></span>  
 <span data-ttu-id="a6c07-197">Funkce sloučení chování usnadňuje správu chování, když chcete, aby se sada běžných chování používala konzistentně.</span><span class="sxs-lookup"><span data-stu-id="a6c07-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="a6c07-198">Tato funkce umožňuje zadat chování na různých úrovních konfigurační hierarchie a mít služby dědění chování z více úrovní konfigurační hierarchie.</span><span class="sxs-lookup"><span data-stu-id="a6c07-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="a6c07-199">K tomu, abyste se vypředpokládali, jak to funguje, máte ve službě IIS následující rozložení virtuálních adresářů:</span><span class="sxs-lookup"><span data-stu-id="a6c07-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="a6c07-200">A váš soubor `~\Web.config` má následující obsah:</span><span class="sxs-lookup"><span data-stu-id="a6c07-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="a6c07-201">A máte podřízený soubor Web. config umístěný na adrese ~ \Child\Web.config s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="a6c07-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="a6c07-202">Služba, která se nachází na ~ \Child\Service.svc, se bude chovat, jako by se jednalo o chování serviceDebug a oddílu serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="a6c07-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="a6c07-203">Služba nacházející se na ~ \Service.svc bude mít pouze chování serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="a6c07-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="a6c07-204">K tomu dochází, když se sloučí dvě kolekce chování se stejným názvem (v tomto případě je to prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="a6c07-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="a6c07-205">Můžete také vymazat kolekce chování pomocí značky > \<clear a odebrat jednotlivá chování z kolekce pomocí značky > \<remove.</span><span class="sxs-lookup"><span data-stu-id="a6c07-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="a6c07-206">Například následující dvě výsledky konfigurace v podřízené službě mají pouze chování oddílu serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="a6c07-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="a6c07-207">Sloučení chování je provedeno pro kolekce chování Nameless, jak je uvedeno výše, a pojmenované kolekce chování také.</span><span class="sxs-lookup"><span data-stu-id="a6c07-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="a6c07-208">Sloučení chování funguje v prostředí hostování služby IIS, ve kterém se soubory Web. config sloučí hierarchicky s kořenovým souborem Web. config a Machine. config. Ale funguje i v prostředí aplikace, kde Machine. config dokáže sloučit se souborem App. config.</span><span class="sxs-lookup"><span data-stu-id="a6c07-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="a6c07-209">Sloučení chování se aplikuje na chování koncového bodu i na chování služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a6c07-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="a6c07-210">Pokud kolekce podřízených chování obsahuje chování, které již je přítomno v nadřazené kolekci chování, podřízené chování přepíše nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="a6c07-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="a6c07-211">Takže pokud kolekce nadřazených chování `<serviceMetadata httpGetEnabled="False" />` a podřízená kolekce chování měla `<serviceMetadata httpGetEnabled="True" />`, podřízené chování by přepsalo nadřazené chování v kolekci chování a httpGetEnabled by bylo "true".</span><span class="sxs-lookup"><span data-stu-id="a6c07-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c07-212">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6c07-212">See also</span></span>

- [<span data-ttu-id="a6c07-213">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="a6c07-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="a6c07-214">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="a6c07-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="a6c07-215">@no__t – 1service ></span><span class="sxs-lookup"><span data-stu-id="a6c07-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="a6c07-216">@no__t – 1binding ></span><span class="sxs-lookup"><span data-stu-id="a6c07-216">\<binding></span></span>](../misc/binding.md)
