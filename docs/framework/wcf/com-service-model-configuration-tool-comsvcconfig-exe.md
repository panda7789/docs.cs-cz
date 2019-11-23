---
title: Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 13368dfa7ca9d7981ac146b87e83f77077eaf537
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320727"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="6cff3-102">Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="6cff3-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="6cff3-103">Nástroj příkazového řádku konfigurace modelu COM+ (ComSvcConfig. exe) umožňuje konfigurovat rozhraní modelu COM+, která se zveřejňují jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cff3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cff3-104">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6cff3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cff3-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cff3-106">Abyste mohli používat ComSvcConfig. exe, musíte být správce na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="6cff3-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="6cff3-107">Tento nástroj najdete v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="6cff3-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="6cff3-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="6cff3-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="6cff3-109">Další informace o nástroji ComSvcConfig. exe najdete v tématu [How to: use com+ service model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6cff3-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="6cff3-110">Následující tabulka popisuje režimy, které lze použít s ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="6cff3-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="6cff3-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="6cff3-111">Option</span></span>|<span data-ttu-id="6cff3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6cff3-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="6cff3-113">Nainstaluje konfiguraci pro rozhraní COM+ pro integraci modelu služby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="6cff3-114">`/i`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="6cff3-115">Odinstaluje konfiguraci rozhraní modelu COM+ z integrace modelu služby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="6cff3-116">`/u`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="6cff3-117">Obsahuje seznam informací o aplikacích a součástech modelu COM+, které mají rozhraní konfigurovaná pro integraci Service Model.</span><span class="sxs-lookup"><span data-stu-id="6cff3-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="6cff3-118">`/l`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="6cff3-119">Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="6cff3-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="6cff3-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="6cff3-120">Option</span></span>|<span data-ttu-id="6cff3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6cff3-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6cff3-122">`/application:` \<*ApplicationId* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="6cff3-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="6cff3-123">Určuje aplikaci COM+, která se má nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="6cff3-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="6cff3-124">`/a`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="6cff3-125">`/contract:` \< &#124; *identifikátoru* &#124; ClassID \*,*InterfaceID* &#124; *Název_rozhraní* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="6cff3-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="6cff3-126">Určuje komponentu a rozhraní COM+, které budou nakonfigurovány jako kontrakt pro službu.</span><span class="sxs-lookup"><span data-stu-id="6cff3-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="6cff3-127">`/c`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="6cff3-128">I když se zástupný znak (\*) dá použít při zadání názvu komponenty a rozhraní, doporučujeme, abyste ho nepoužívali, protože možná vystavíte rozhraní, na která jste se nechtěli.</span><span class="sxs-lookup"><span data-stu-id="6cff3-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="6cff3-129">*byl*\> `/hosting:` \<*ComPlus* &#124; .</span><span class="sxs-lookup"><span data-stu-id="6cff3-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="6cff3-130">Určuje, zda se má použít režim hostování modelu COM+ nebo webový hostující režim.</span><span class="sxs-lookup"><span data-stu-id="6cff3-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="6cff3-131">`/h`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="6cff3-132">Použití hostitelského režimu modelu COM+ vyžaduje explicitní aktivaci aplikace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="6cff3-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="6cff3-133">Použití režimu hostování webu umožňuje, aby se aplikace COM+ automaticky aktivovala podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="6cff3-134">Pokud je aplikace modelu COM+ knihovnou aplikace, běží v procesu Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="6cff3-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="6cff3-135">Pokud je aplikace modelu COM+ aplikace serveru, běží v procesu Dllhost. exe.</span><span class="sxs-lookup"><span data-stu-id="6cff3-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="6cff3-136">`/webSite:` \<*webu*\></span><span class="sxs-lookup"><span data-stu-id="6cff3-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="6cff3-137">Určuje web pro hostování při použití režimu hostování webu (viz příznak `/hosting`).</span><span class="sxs-lookup"><span data-stu-id="6cff3-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="6cff3-138">`/w`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="6cff3-139">Pokud není zadán žádný web, použije se výchozí web.</span><span class="sxs-lookup"><span data-stu-id="6cff3-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="6cff3-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="6cff3-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="6cff3-141">Určuje virtuální adresář pro hostování při použití hostování webu (viz příznak `/hosting`).</span><span class="sxs-lookup"><span data-stu-id="6cff3-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="6cff3-142">`/d`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="6cff3-143">Přidá koncový bod služby Metadata Exchange (MEX) do výchozí konfigurace služby pro podporu klientů, kteří chtějí načíst definici smlouvy ze služby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="6cff3-144">`/x`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="6cff3-145">Zobrazí informace o aplikaci, součásti a rozhraní jako ID.</span><span class="sxs-lookup"><span data-stu-id="6cff3-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="6cff3-146">`/k`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="6cff3-147">Zabraňuje souboru ComSvcConfig. exe zobrazovat jeho logo.</span><span class="sxs-lookup"><span data-stu-id="6cff3-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="6cff3-148">`/n`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="6cff3-149">Vypíše všechna upozornění nebo informativní text kromě všech zjištěných chyb.</span><span class="sxs-lookup"><span data-stu-id="6cff3-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="6cff3-150">`/v`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="6cff3-151">Zobrazí zprávu o využití.</span><span class="sxs-lookup"><span data-stu-id="6cff3-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="6cff3-152">`/?`krátký tvar.</span><span class="sxs-lookup"><span data-stu-id="6cff3-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="6cff3-153">Vygeneruje konfiguraci služby, když zadané rozhraní obsahuje jeden nebo více podpisů metody, které mohou být vystaveny.</span><span class="sxs-lookup"><span data-stu-id="6cff3-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="6cff3-154">V okamžiku inicializace služby se kompatibilní metody zobrazí jako operace v kontraktu služby a nekompatibilní metody jsou ignorovány a chybí od kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="6cff3-155">Pokud tento příznak chybí, nástroj nebude generovat konfiguraci služby, když zadané rozhraní obsahuje jednu nebo více nekompatibilních metod.</span><span class="sxs-lookup"><span data-stu-id="6cff3-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="6cff3-156">Příklady</span><span class="sxs-lookup"><span data-stu-id="6cff3-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="6cff3-157">Popis</span><span class="sxs-lookup"><span data-stu-id="6cff3-157">Description</span></span>  
 <span data-ttu-id="6cff3-158">Následující příklad přidá rozhraní `IFinances` komponenty `ItemOrders.IFinancial` (z aplikace OnlineStore COM+) do sady rozhraní, které jsou vystaveny jako webové služby, pomocí hostitelského režimu COM+.</span><span class="sxs-lookup"><span data-stu-id="6cff3-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="6cff3-159">Všechna upozornění budou kromě všech zjištěných chyb i výstupy.</span><span class="sxs-lookup"><span data-stu-id="6cff3-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6cff3-160">Kód</span><span class="sxs-lookup"><span data-stu-id="6cff3-160">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="6cff3-161">Popis</span><span class="sxs-lookup"><span data-stu-id="6cff3-161">Description</span></span>  
 <span data-ttu-id="6cff3-162">Následující příklad přidá rozhraní `IStockLevels` komponenty `ItemInventory.Warehouse` (z aplikace OnlineWarehouse COM+) do sady rozhraní, které jsou zveřejněny jako webové služby, a to pomocí režimu hostování na webu.</span><span class="sxs-lookup"><span data-stu-id="6cff3-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="6cff3-163">Webová služba je hostitelem webu ve virtuálním adresáři OnlineWarehouse služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6cff3-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6cff3-164">Kód</span><span class="sxs-lookup"><span data-stu-id="6cff3-164">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="6cff3-165">Popis</span><span class="sxs-lookup"><span data-stu-id="6cff3-165">Description</span></span>  
 <span data-ttu-id="6cff3-166">Následující příklad odebere rozhraní `IFinances` komponenty `ItemOrders.Financial` (z aplikace OnlineStore COM+) ze sady rozhraní, které jsou přístupné jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="6cff3-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6cff3-167">Kód</span><span class="sxs-lookup"><span data-stu-id="6cff3-167">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="6cff3-168">Popis</span><span class="sxs-lookup"><span data-stu-id="6cff3-168">Description</span></span>  
 <span data-ttu-id="6cff3-169">Následující příklad uvádí seznam aktuálně vydaných hostovaných rozhraní COM+ spolu s odpovídajícími podrobnostmi adres a vazeb pro aplikaci OnlineStore COM+ na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="6cff3-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6cff3-170">Kód</span><span class="sxs-lookup"><span data-stu-id="6cff3-170">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cff3-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cff3-171">See also</span></span>

- [<span data-ttu-id="6cff3-172">Postupy: Použití nástroje pro konfiguraci služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="6cff3-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
