---
title: Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158655"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="c8194-102">Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="c8194-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="c8194-103">Nástroj příkazového řádku modelu COM + Service Model Configuration (ComSvcConfig.exe) můžete nakonfigurovat rozhraní COM +. Chcete-li být vystavena jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="c8194-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8194-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8194-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8194-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8194-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8194-106">Musíte být správce na místním počítači použít ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c8194-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="c8194-107">Nástroj najdete v následujícím umístění</span><span class="sxs-lookup"><span data-stu-id="c8194-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="c8194-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="c8194-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="c8194-109">Další informace o ComSvcConfig.exe najdete v tématu [jak: Použijte nástroj pro konfiguraci modelu služby COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c8194-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="c8194-110">Následující tabulka popisuje režimy, které lze použít s ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c8194-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="c8194-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="c8194-111">Option</span></span>|<span data-ttu-id="c8194-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c8194-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="c8194-113">Nainstaluje konfigurační rozhraní modelu COM + pro integraci Service Model.</span><span class="sxs-lookup"><span data-stu-id="c8194-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="c8194-114">Krátký tvar `/i`.</span><span class="sxs-lookup"><span data-stu-id="c8194-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="c8194-115">Odinstaluje z integrace Service Model configuration pro rozhraní modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c8194-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="c8194-116">Krátký tvar `/u`.</span><span class="sxs-lookup"><span data-stu-id="c8194-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="c8194-117">Obsahuje informace o modelu COM + aplikace a komponenty, které mají rozhraní, které jsou nakonfigurované pro integraci Service Model.</span><span class="sxs-lookup"><span data-stu-id="c8194-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="c8194-118">Krátký tvar `/l`.</span><span class="sxs-lookup"><span data-stu-id="c8194-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="c8194-119">Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c8194-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="c8194-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="c8194-120">Option</span></span>|<span data-ttu-id="c8194-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c8194-121">Description</span></span>|  
|------------|-----------------|  
|`/application:` <span data-ttu-id="c8194-122">\<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="c8194-122">\<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="c8194-123">Určuje aplikaci COM +. ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c8194-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="c8194-124">Krátký tvar `/a`.</span><span class="sxs-lookup"><span data-stu-id="c8194-124">Short form `/a`.</span></span>|  
|`/contract:` <span data-ttu-id="c8194-125">\<*ID třídy* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName*    &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="c8194-125">\<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="c8194-126">Určuje komponenty modelu COM + a rozhraní, které budou nakonfigurované jako kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="c8194-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="c8194-127">Krátký tvar `/c`.</span><span class="sxs-lookup"><span data-stu-id="c8194-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="c8194-128">Zatímco zástupný znak (\*) lze použít při zadávání názvů součásti a rozhraní, doporučujeme vám, že je velmi riskantní používat, protože může vystavit rozhraní, které jste neměli v úmyslu.</span><span class="sxs-lookup"><span data-stu-id="c8194-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|`/hosting:` <span data-ttu-id="c8194-129">\<*ComPlus* &#124; *byl* \></span><span class="sxs-lookup"><span data-stu-id="c8194-129">\<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="c8194-130">Určuje, zda určený hostující režim nebo režim hostování webu modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c8194-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="c8194-131">Krátký tvar `/h`.</span><span class="sxs-lookup"><span data-stu-id="c8194-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="c8194-132">Používání modelu COM + hostující režim vyžaduje explicitní aktivace aplikace modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c8194-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="c8194-133">Použití webového hostingu režim umožňuje aplikace modelu COM + automaticky aktivaci jako povinné.</span><span class="sxs-lookup"><span data-stu-id="c8194-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="c8194-134">Pokud je aplikace modelu COM + aplikace knihovny, běží v procesu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="c8194-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="c8194-135">Pokud aplikace modelu COM + je serverová aplikace, spustí se v procesu Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="c8194-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|`/webSite:` <span data-ttu-id="c8194-136">\<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="c8194-136">\<*WebsiteName*\></span></span>|<span data-ttu-id="c8194-137">Určuje, se používá na webu pro hostování při hostování režimu webu (najdete v článku `/hosting` příznak).</span><span class="sxs-lookup"><span data-stu-id="c8194-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="c8194-138">Krátký tvar `/w`.</span><span class="sxs-lookup"><span data-stu-id="c8194-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="c8194-139">Pokud není zadán žádný web, použije se výchozí webový server.</span><span class="sxs-lookup"><span data-stu-id="c8194-139">If no Web site is specified, the default Web site is used.</span></span>|  
|`/webDirectory:` <span data-ttu-id="c8194-140">\<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="c8194-140">\<*WebDirectoryName*\></span></span>|<span data-ttu-id="c8194-141">Určuje virtuální adresář pro hostování při hostování webu se používá (viz `/hosting` příznak).</span><span class="sxs-lookup"><span data-stu-id="c8194-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="c8194-142">Krátký tvar `/d`.</span><span class="sxs-lookup"><span data-stu-id="c8194-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="c8194-143">Přidá do výchozí konfigurace služby pro podporu klientů, které chcete načíst definici kontraktu služby koncového bodu služby Metadata Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="c8194-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="c8194-144">Krátký tvar `/x`.</span><span class="sxs-lookup"><span data-stu-id="c8194-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="c8194-145">Zobrazí aplikace, komponenty a informace o rozhraní jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="c8194-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="c8194-146">Krátký tvar `/k`.</span><span class="sxs-lookup"><span data-stu-id="c8194-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="c8194-147">Zabrání zobrazení loga. jeho ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c8194-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="c8194-148">Krátký tvar `/n`.</span><span class="sxs-lookup"><span data-stu-id="c8194-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="c8194-149">Vypíše všechna upozornění nebo informační text kromě jakékoli došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="c8194-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="c8194-150">Krátký tvar `/v`.</span><span class="sxs-lookup"><span data-stu-id="c8194-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="c8194-151">Zobrazí zprávu o použití.</span><span class="sxs-lookup"><span data-stu-id="c8194-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="c8194-152">Krátký tvar `/?`.</span><span class="sxs-lookup"><span data-stu-id="c8194-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="c8194-153">Konfigurace služby generuje, pokud zadané rozhraní obsahuje jeden nebo více podpisy metod, které mohou být zveřejněny.</span><span class="sxs-lookup"><span data-stu-id="c8194-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="c8194-154">Během inicializace služby kompatibilní metody se zobrazí jako operace v kontraktu služby, a metody není kompatibilní se ignorují a chybí kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="c8194-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="c8194-155">Pokud tento příznak chybí, nástroj se nevygeneruje konfigurace služby při zadané rozhraní obsahuje jednu nebo více nekompatibilních metod.</span><span class="sxs-lookup"><span data-stu-id="c8194-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="c8194-156">Příklady</span><span class="sxs-lookup"><span data-stu-id="c8194-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="c8194-157">Popis</span><span class="sxs-lookup"><span data-stu-id="c8194-157">Description</span></span>  
 <span data-ttu-id="c8194-158">Následující příklad přidá `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z OnlineStore aplikace COM +) do sady rozhraní, které jsou vystaveny jako webové služby pomocí hostující režim modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c8194-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="c8194-159">Všechna upozornění vydá kromě jakékoli došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="c8194-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c8194-160">Kód</span><span class="sxs-lookup"><span data-stu-id="c8194-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="c8194-161">Popis</span><span class="sxs-lookup"><span data-stu-id="c8194-161">Description</span></span>  
 <span data-ttu-id="c8194-162">Následující příklad přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` komponenty (z OnlineWarehouse aplikace COM +) do sady rozhraní, které jsou vystaveny jako webové služby pomocí webového hostující režim.</span><span class="sxs-lookup"><span data-stu-id="c8194-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="c8194-163">Webová služba je že web hostovaný ve virtuálním adresáři OnlineWarehouse služby IIS.</span><span class="sxs-lookup"><span data-stu-id="c8194-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c8194-164">Kód</span><span class="sxs-lookup"><span data-stu-id="c8194-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="c8194-165">Popis</span><span class="sxs-lookup"><span data-stu-id="c8194-165">Description</span></span>  
 <span data-ttu-id="c8194-166">Následující příklad odebere `IFinances` rozhraní `ItemOrders.Financial` součásti (z OnlineStore aplikace COM +) ze sady rozhraní, které jsou vystaveny jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="c8194-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c8194-167">Kód</span><span class="sxs-lookup"><span data-stu-id="c8194-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="c8194-168">Popis</span><span class="sxs-lookup"><span data-stu-id="c8194-168">Description</span></span>  
 <span data-ttu-id="c8194-169">Následující příklad zobrazí aktuálně vystavit rozhraní modelu COM + hostované, spolu s příslušnou adresou a podrobnosti o vazbu pro aplikaci OnlineStore modelu COM + v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="c8194-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c8194-170">Kód</span><span class="sxs-lookup"><span data-stu-id="c8194-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8194-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8194-171">See also</span></span>

- [<span data-ttu-id="c8194-172">Postupy: Použití nástroje pro konfiguraci modelu služby COM+</span><span class="sxs-lookup"><span data-stu-id="c8194-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
