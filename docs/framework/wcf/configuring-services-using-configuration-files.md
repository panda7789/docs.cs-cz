---
title: "Konfigurace služeb pomocí konfiguračních souborů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 480cdb83248dc1cf9dd90c0f654aa4f269318c4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="f0e6a-102">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="f0e6a-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="f0e6a-103">Konfigurace [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby s konfiguračním souborem vám umožní poskytovat chování data koncový bod a služby v okamžiku nasazení místo v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-103">Configuring a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="f0e6a-104">Toto téma popisuje primární techniky, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="f0e6a-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služba je konfigurovatelná pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="f0e6a-106">Nejčastěji, jsou přidány elementy XML v souboru Web.config pro stránku Internetové informační služby (IIS), který je hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="f0e6a-107">Prvky umožňují změnit podrobnosti, například adresy koncových bodů (skutečná adresami používaný ke komunikaci se službou) na základě počítače podle počítače.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="f0e6a-108">Kromě toho [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obsahuje několik poskytované systémem prvky, které vám umožní rychle vybrat nejzákladnější funkce pro služby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-108">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="f0e6a-109">Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] se dodává s nový model výchozí konfigurace, který zjednodušuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] požadavky na konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="f0e6a-110">Pokud nezadáte žádné [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfigurace pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s některými standardní koncové body a výchozí chování nebo vazby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="f0e6a-111">V praxi, zápis konfigurace je hlavní část programování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-111">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="f0e6a-112">[Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0e6a-112"> [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> [!INCLUDE[crlist](../../../includes/crlist-md.md)]<span data-ttu-id="f0e6a-113">nejčastěji používané elementů, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="f0e6a-113"> of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f0e6a-114">výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0e6a-114"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0e6a-115">Při nasazení scénářů vedle sebe, kde se nasadí dvě různé verze služby, je nutné zadat částečné názvy sestavení odkazovaných v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="f0e6a-116">Je to proto, že konfigurační soubor je sdílena mezi všemi verzemi služby a může být spuštěno různé verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="f0e6a-117">System.Configuration: Soubor Web.config a App.config</span><span class="sxs-lookup"><span data-stu-id="f0e6a-117">System.Configuration: Web.config and App.config</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f0e6a-118">používá System.Configuration konfigurace systému [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0e6a-118"> uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="f0e6a-119">Při konfiguraci služby v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], použijte soubor Web.config nebo soubor App.config a zadejte nastavení.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-119">When configuring a service in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="f0e6a-120">Volba název konfiguračního souboru je určen podle hostitelského prostředí, které zvolíte pro službu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="f0e6a-121">Pokud používáte k hostování služby IIS, použijte soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="f0e6a-122">Pokud používáte jiné hostitelské prostředí, můžete používejte soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="f0e6a-123">V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], soubor s názvem souboru App.config se používá k vytvoření konečné konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-123">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="f0e6a-124">Název poslední ve skutečnosti použili při konfiguraci závisí na název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="f0e6a-125">Například sestavení s názvem "Cohowinery.exe" má název souboru finální konfiguraci "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="f0e6a-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="f0e6a-126">Ale stačí pro změnu souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="f0e6a-127">Změny provedené v souboru jsou automaticky vytvářeny do konfiguračního souboru konečné aplikace v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="f0e6a-128">Pomocí App.config, soubor konfigurační systém při spuštění aplikace a používá konfiguraci sloučí soubor App.config s obsahem souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="f0e6a-129">Tento mechanismus umožňuje celého systému a jak jsou definovány v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="f0e6a-130">Použít soubor App.config pro přepsání nastavení souboru Machine.config; tak, aby získat používají, můžete uzamknout nastavení v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="f0e6a-131">V případě Web.config sloučí konfigurační systém souborů Web.config ve všech adresářích vedoucí k adresáři aplikace do konfigurace, který se použije.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f0e6a-132">Konfigurace a nastavení priority, najdete v tématech v <xref:System.Configuration> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-132"> configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="f0e6a-133">Hlavní části konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f0e6a-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="f0e6a-134">Hlavní části v konfiguračním souboru zahrnují následující prvky.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
>  <span data-ttu-id="f0e6a-135">Vazby a chování částech jsou volitelné a jsou zahrnuty pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="f0e6a-136">\<Services > – Element</span><span class="sxs-lookup"><span data-stu-id="f0e6a-136">The \<services> Element</span></span>  
 <span data-ttu-id="f0e6a-137">`services` Element obsahuje specifikace pro všechny služby hostitelů aplikací.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="f0e6a-138">Počínaje zjednodušené konfigurační model v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], v této části je volitelný.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="f0e6a-139">\<služby ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="f0e6a-140">\<Služby > elementu</span><span class="sxs-lookup"><span data-stu-id="f0e6a-140">The \<service> Element</span></span>  
 <span data-ttu-id="f0e6a-141">Každá služba má tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="f0e6a-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-142">`name`.</span></span> <span data-ttu-id="f0e6a-143">Určuje typ, který poskytuje implementaci kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="f0e6a-144">Toto je plně kvalifikovaný název, který se skládá z oboru názvů, dobou a název typu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="f0e6a-145">Například `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="f0e6a-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="f0e6a-147">Určuje název jednoho z `behavior` elementy v nalezen `behaviors` element.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="f0e6a-148">Zadané chování řídí akce, například zda služba umožňuje zosobnění.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="f0e6a-149">Pokud je jeho hodnota prázdná název nebo Ne `behaviorConfiguration` je k dispozici potom sadu výchozí chování služby je přidán ke službě.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="f0e6a-150">\<služby ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="f0e6a-151">\<Endpoint > – Element</span><span class="sxs-lookup"><span data-stu-id="f0e6a-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="f0e6a-152">Každý koncový bod vyžaduje adresy, vazby a kontraktu, které jsou reprezentované pomocí následující atributy:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="f0e6a-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-153">`address`.</span></span> <span data-ttu-id="f0e6a-154">Určuje služby identifikátor URI (Uniform Resource), které mohou být absolutní adresu nebo ten, který je uveden relativně k základní adresa služby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="f0e6a-155">Pokud nastavit na prázdný řetězec, se označuje, že koncový bod je k dispozici na základní adrese, která je zadána při vytváření <xref:System.ServiceModel.ServiceHost> pro službu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="f0e6a-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-156">`binding`.</span></span> <span data-ttu-id="f0e6a-157">Obvykle určuje vazby poskytované systémem jako <xref:System.ServiceModel.WSHttpBinding>, ale můžete také určit, uživatelem definované vazby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="f0e6a-158">Zadaná vazba Určuje typ přenosu, zabezpečení a kódování použité a toho, jestli spolehlivé relace, transakce nebo vysílání datového proudu podporován nebo povoleno.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="f0e6a-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-159">`bindingConfiguration`.</span></span> <span data-ttu-id="f0e6a-160">Pokud je třeba upravit výchozí hodnoty vazby, to lze provést tak, že nakonfigurujete odpovídající `binding` element v `bindings` elementu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="f0e6a-161">Tento atribut by měly mít stejnou hodnotu jako `name` atribut `binding` element, který se používá, chcete-li změnit výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="f0e6a-162">Pokud není zadán název, nebo žádný `bindingConfiguration` je zadán vazba, vazba výchozí typ vazby se používá v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="f0e6a-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-163">`contract`.</span></span> <span data-ttu-id="f0e6a-164">Určuje rozhraní, které definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="f0e6a-165">Toto je rozhraní implementované v běžné typ language runtime (CLR) určeného `name` atribut `service` elementu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="f0e6a-166">\<koncový bod > odkaz na element</span><span class="sxs-lookup"><span data-stu-id="f0e6a-166">\<endpoint> element reference</span></span>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="f0e6a-167">\<Vazby > elementu</span><span class="sxs-lookup"><span data-stu-id="f0e6a-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="f0e6a-168">`bindings` Element obsahuje specifikace pro všechny vazby, které můžete používat libovolný koncový bod definované v jakékoli služby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="f0e6a-169">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="f0e6a-170">\<Vazby > elementu</span><span class="sxs-lookup"><span data-stu-id="f0e6a-170">The \<binding> Element</span></span>  
 <span data-ttu-id="f0e6a-171">`binding` Elementů obsažených v `bindings` prvek může být buď jedné vazby poskytované systémem (najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md)) nebo vlastní vazby (najdete v části [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="f0e6a-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="f0e6a-172">`binding` Element má `name` atribut, který korelaci vazba s zadaného v koncového bodu `bindingConfiguration` atribut `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="f0e6a-173">Pokud není zadán žádný název, potom vazbou odpovídá na výchozí hodnoty tohoto typu vazby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f0e6a-174">Konfigurace služeb a klientů, najdete v části [konfigurace Windows Communication Foundation aplikací](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="f0e6a-174"> configuring services and clients, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="f0e6a-175">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="f0e6a-176">\<Chování > elementu</span><span class="sxs-lookup"><span data-stu-id="f0e6a-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="f0e6a-177">Toto je kontejnerový element pro `behavior` prvky, které definují chování pro službu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="f0e6a-178">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="f0e6a-179">\<Chování > elementu</span><span class="sxs-lookup"><span data-stu-id="f0e6a-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="f0e6a-180">Každý `behavior` element je identifikována `name` atribut a poskytuje buď poskytované systémem chování, například <`throttling`>, nebo vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="f0e6a-181">Pokud není zadán název tohoto chování prvku odpovídá výchozí chování služba nebo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="f0e6a-182">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="f0e6a-183">Jak používat vazby a konfigurace chování</span><span class="sxs-lookup"><span data-stu-id="f0e6a-183">How to Use Binding and Behavior Configurations</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f0e6a-184">umožňuje snadno sdílet konfigurace mezi koncovými body pomocí referenčního systému v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-184"> makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="f0e6a-185">Namísto přímo přiřazení hodnoty konfigurace pro koncový bod, konfigurace související se vazby hodnoty jsou seskupené v `bindingConfiguration` elementů v `<binding>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="f0e6a-186">Konfigurace vazeb je pojmenovanou skupinu nastavení u vazby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="f0e6a-187">Koncové body pak můžete odkazovat `bindingConfiguration` podle názvu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="f0e6a-188">`name` z `bindingConfiguration` je nastavena v `<binding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="f0e6a-189">`name` Musí být jedinečné řetězce v rámci oboru typ vazby – v takovém případě [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), nebo prázdná hodnota k odkazování na výchozí vazby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="f0e6a-190">Koncový bod odkazy na konfiguraci nastavením `bindingConfiguration` atribut tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="f0e6a-191">A `behaviorConfiguration` je implementována stejným způsobem, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="f0e6a-192">Všimněte si, že sada výchozí chování služby jsou přidány do služby.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="f0e6a-193">Tento systém umožňuje koncové body k sdílejí společné konfigurace bez opětovná definice nastavení.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="f0e6a-194">Pokud celého systému obor je požadován, vytvořte vazbu nebo chování konfiguraci v souboru Machine.config. Nastavení konfigurace jsou k dispozici ve všech souborů v souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="f0e6a-195">[Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytvoření konfigurací.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="f0e6a-196">Chování sloučení</span><span class="sxs-lookup"><span data-stu-id="f0e6a-196">Behavior Merge</span></span>  
 <span data-ttu-id="f0e6a-197">Funkci sloučení chování usnadňuje správu chování, pokud chcete sadu společné chování, který se má použít konzistentně.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="f0e6a-198">Tato funkce umožňuje zadat chování na různých úrovních v konfigurační hierarchii a máte služby dědit chování z několika úrovní v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="f0e6a-199">Pro ilustraci jak toto funguje předpokládá, že máte následující rozložení virtuální adresář ve službě IIS:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="f0e6a-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="f0e6a-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="f0e6a-201">A souboru ~\Web.config má následující obsah:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-201">And your ~\Web.config file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="f0e6a-202">A máte podřízený, které se nachází soubor Web.config v ~\Child\Web.config s tímto obsahem:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="f0e6a-203">Služby umístěné v ~\Child\Service.svc se bude chovat, jako kdyby bylo serviceDebug i serviceMetadata chování.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="f0e6a-204">Služba nachází v ~\Service.svc budou mít pouze serviceDebug chování.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="f0e6a-205">Co se stane, je, že jsou sloučit dva chování kolekce se stejným názvem (v tomto případě prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="f0e6a-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="f0e6a-206">Můžete také vymazat chování kolekce pomocí \<vymazat > značky a odebrat jednotlivé chování z kolekce pomocí \<odebrat > značky.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="f0e6a-207">Například následující dvě konfigurace výsledky v podřízeném služby s pouze serviceMetadata chování:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="f0e6a-208">Chování sloučení se provádí pro kolekce nameless chování jako v příkladu nahoře a s názvem také kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="f0e6a-209">Chování sloučení funguje ve službě IIS hostování prostředí, ve které sloučení souborů Web.config hierarchicky s souboru machine.config a kořenovém souboru Web.config. Ale spolupracuje také v prostředí aplikace, kde můžete sloučit machine.config pomocí souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="f0e6a-210">Chování sloučení se vztahuje na koncový bod chování a chování služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="f0e6a-211">Pokud podřízené chování kolekce obsahuje chování, které se již nachází v kolekci chování nadřazené, přepíše chování podřízené nadřazený.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="f0e6a-212">Ano, pokud kolekce chování nadřazené měli `<serviceMetadata httpGetEnabled="False" />` a podřízené chování kolekce musí `<serviceMetadata httpGetEnabled="True" />`, podřízené chování by se mělo přepsat chování nadřazené v kolekci chování a httpGetEnabled by "true".</span><span class="sxs-lookup"><span data-stu-id="f0e6a-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e6a-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0e6a-213">See Also</span></span>  
 [<span data-ttu-id="f0e6a-214">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="f0e6a-214">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="f0e6a-215">Konfigurace aplikací pro Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f0e6a-215">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="f0e6a-216">\<služby ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="f0e6a-217">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f0e6a-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
