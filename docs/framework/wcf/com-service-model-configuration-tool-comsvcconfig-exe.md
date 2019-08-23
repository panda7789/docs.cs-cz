---
title: Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 89462d05b9da7fc63bda58955517bfa9f0c50ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964192"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="6353f-102">Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="6353f-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="6353f-103">Nástroj příkazového řádku konfigurace modelu COM+ (ComSvcConfig. exe) umožňuje konfigurovat rozhraní modelu COM+, která se zveřejňují jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="6353f-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6353f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6353f-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6353f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6353f-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6353f-106">Abyste mohli používat ComSvcConfig. exe, musíte být správce na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="6353f-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="6353f-107">Tento nástroj najdete v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="6353f-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="6353f-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="6353f-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="6353f-109">Další informace o ComSvcConfig. exe naleznete v tématu [How to: Použijte nástroj](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)pro konfiguraci modelu služby com+.</span><span class="sxs-lookup"><span data-stu-id="6353f-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="6353f-110">Následující tabulka popisuje režimy, které lze použít s ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="6353f-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="6353f-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="6353f-111">Option</span></span>|<span data-ttu-id="6353f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6353f-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="6353f-113">Nainstaluje konfiguraci pro rozhraní COM+ pro integraci modelu služby.</span><span class="sxs-lookup"><span data-stu-id="6353f-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="6353f-114">Krátká forma `/i`.</span><span class="sxs-lookup"><span data-stu-id="6353f-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="6353f-115">Odinstaluje konfiguraci rozhraní modelu COM+ z integrace modelu služby.</span><span class="sxs-lookup"><span data-stu-id="6353f-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="6353f-116">Krátká forma `/u`.</span><span class="sxs-lookup"><span data-stu-id="6353f-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="6353f-117">Obsahuje seznam informací o aplikacích a součástech modelu COM+, které mají rozhraní konfigurovaná pro integraci Service Model.</span><span class="sxs-lookup"><span data-stu-id="6353f-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="6353f-118">Krátká forma `/l`.</span><span class="sxs-lookup"><span data-stu-id="6353f-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="6353f-119">Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="6353f-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="6353f-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="6353f-120">Option</span></span>|<span data-ttu-id="6353f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6353f-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6353f-122">`/application:`&#124; ApplicationId \<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="6353f-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="6353f-123">Určuje aplikaci COM+, která se má nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="6353f-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="6353f-124">Krátká forma `/a`.</span><span class="sxs-lookup"><span data-stu-id="6353f-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="6353f-125">`/contract:`&#124; &#124; &#124; ClassID ProgID&#124; , InterfaceID Název_rozhraní\* \<    \*\></span><span class="sxs-lookup"><span data-stu-id="6353f-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="6353f-126">Určuje komponentu a rozhraní COM+, které budou nakonfigurovány jako kontrakt pro službu.</span><span class="sxs-lookup"><span data-stu-id="6353f-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="6353f-127">Krátká forma `/c`.</span><span class="sxs-lookup"><span data-stu-id="6353f-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="6353f-128">I když se zástupný znak\*() dá použít při zadání názvu komponenty a rozhraní, doporučujeme, abyste ho nepoužívali, protože můžete vystavovat rozhraní, které jste nechtěli mít.</span><span class="sxs-lookup"><span data-stu-id="6353f-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="6353f-129">`/hosting:`&#124; ComPlus \<byl  \></span><span class="sxs-lookup"><span data-stu-id="6353f-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="6353f-130">Určuje, zda se má použít režim hostování modelu COM+ nebo webový hostující režim.</span><span class="sxs-lookup"><span data-stu-id="6353f-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="6353f-131">Krátká forma `/h`.</span><span class="sxs-lookup"><span data-stu-id="6353f-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="6353f-132">Použití hostitelského režimu modelu COM+ vyžaduje explicitní aktivaci aplikace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="6353f-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="6353f-133">Použití režimu hostování webu umožňuje, aby se aplikace COM+ automaticky aktivovala podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6353f-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="6353f-134">Pokud je aplikace modelu COM+ knihovnou aplikace, běží v procesu Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="6353f-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="6353f-135">Pokud je aplikace modelu COM+ aplikace serveru, běží v procesu Dllhost. exe.</span><span class="sxs-lookup"><span data-stu-id="6353f-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="6353f-136">`/webSite:`\< *Webový server*\></span><span class="sxs-lookup"><span data-stu-id="6353f-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="6353f-137">Určuje web pro hostování při použití režimu hostování webu (viz `/hosting` příznak).</span><span class="sxs-lookup"><span data-stu-id="6353f-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="6353f-138">Krátká forma `/w`.</span><span class="sxs-lookup"><span data-stu-id="6353f-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="6353f-139">Pokud není zadán žádný web, použije se výchozí web.</span><span class="sxs-lookup"><span data-stu-id="6353f-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="6353f-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="6353f-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="6353f-141">Určuje virtuální adresář pro hostování při použití webového hostování (viz `/hosting` příznak).</span><span class="sxs-lookup"><span data-stu-id="6353f-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="6353f-142">Krátká forma `/d`.</span><span class="sxs-lookup"><span data-stu-id="6353f-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="6353f-143">Přidá koncový bod služby Metadata Exchange (MEX) do výchozí konfigurace služby pro podporu klientů, kteří chtějí načíst definici smlouvy ze služby.</span><span class="sxs-lookup"><span data-stu-id="6353f-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="6353f-144">Krátká forma `/x`.</span><span class="sxs-lookup"><span data-stu-id="6353f-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="6353f-145">Zobrazí informace o aplikaci, součásti a rozhraní jako ID.</span><span class="sxs-lookup"><span data-stu-id="6353f-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="6353f-146">Krátká forma `/k`.</span><span class="sxs-lookup"><span data-stu-id="6353f-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="6353f-147">Zabraňuje souboru ComSvcConfig. exe zobrazovat jeho logo.</span><span class="sxs-lookup"><span data-stu-id="6353f-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="6353f-148">Krátká forma `/n`.</span><span class="sxs-lookup"><span data-stu-id="6353f-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="6353f-149">Vypíše všechna upozornění nebo informativní text kromě všech zjištěných chyb.</span><span class="sxs-lookup"><span data-stu-id="6353f-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="6353f-150">Krátká forma `/v`.</span><span class="sxs-lookup"><span data-stu-id="6353f-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="6353f-151">Zobrazí zprávu o využití.</span><span class="sxs-lookup"><span data-stu-id="6353f-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="6353f-152">Krátká forma `/?`.</span><span class="sxs-lookup"><span data-stu-id="6353f-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="6353f-153">Vygeneruje konfiguraci služby, když zadané rozhraní obsahuje jeden nebo více podpisů metody, které mohou být vystaveny.</span><span class="sxs-lookup"><span data-stu-id="6353f-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="6353f-154">V okamžiku inicializace služby se kompatibilní metody zobrazí jako operace v kontraktu služby a nekompatibilní metody jsou ignorovány a chybí od kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6353f-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="6353f-155">Pokud tento příznak chybí, nástroj nebude generovat konfiguraci služby, když zadané rozhraní obsahuje jednu nebo více nekompatibilních metod.</span><span class="sxs-lookup"><span data-stu-id="6353f-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="6353f-156">Příklady</span><span class="sxs-lookup"><span data-stu-id="6353f-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="6353f-157">Popis</span><span class="sxs-lookup"><span data-stu-id="6353f-157">Description</span></span>  
 <span data-ttu-id="6353f-158">Následující příklad přidá `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z aplikace OnlineStore com+) do sady rozhraní, které jsou zpřístupněny jako webové služby, pomocí hostitelského režimu com+.</span><span class="sxs-lookup"><span data-stu-id="6353f-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="6353f-159">Všechna upozornění budou kromě všech zjištěných chyb i výstupy.</span><span class="sxs-lookup"><span data-stu-id="6353f-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6353f-160">Kód</span><span class="sxs-lookup"><span data-stu-id="6353f-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="6353f-161">Popis</span><span class="sxs-lookup"><span data-stu-id="6353f-161">Description</span></span>  
 <span data-ttu-id="6353f-162">Následující příklad přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` komponenty (z aplikace OnlineWarehouse com+) do sady rozhraní, které jsou zpřístupněny jako webové služby, pomocí režimu hostování webu.</span><span class="sxs-lookup"><span data-stu-id="6353f-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="6353f-163">Webová služba je hostitelem webu ve virtuálním adresáři OnlineWarehouse služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6353f-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6353f-164">Kód</span><span class="sxs-lookup"><span data-stu-id="6353f-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="6353f-165">Popis</span><span class="sxs-lookup"><span data-stu-id="6353f-165">Description</span></span>  
 <span data-ttu-id="6353f-166">Následující příklad odebere `IFinances` rozhraní `ItemOrders.Financial` součásti (z aplikace OnlineStore com+) ze sady rozhraní, které jsou zpřístupněny jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="6353f-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6353f-167">Kód</span><span class="sxs-lookup"><span data-stu-id="6353f-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="6353f-168">Popis</span><span class="sxs-lookup"><span data-stu-id="6353f-168">Description</span></span>  
 <span data-ttu-id="6353f-169">Následující příklad uvádí seznam aktuálně vydaných hostovaných rozhraní COM+ spolu s odpovídajícími podrobnostmi adres a vazeb pro aplikaci OnlineStore COM+ na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="6353f-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6353f-170">Kód</span><span class="sxs-lookup"><span data-stu-id="6353f-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="6353f-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6353f-171">See also</span></span>

- [<span data-ttu-id="6353f-172">Postupy: Použití nástroje pro konfiguraci modelu služby COM+</span><span class="sxs-lookup"><span data-stu-id="6353f-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
