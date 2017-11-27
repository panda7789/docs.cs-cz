---
title: "Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f812beea611633fe1fa47ced5db46c462443f28
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="c27aa-102">Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="c27aa-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="c27aa-103">Nástroj příkazového řádku modelu COM + Service Model Configuration (ComSvcConfig.exe) umožňuje nakonfigurovat rozhraní modelu COM + mají být exponovány jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="c27aa-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c27aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c27aa-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c27aa-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c27aa-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c27aa-106">Musíte být správce v místním počítači používat ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c27aa-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="c27aa-107">Tento nástroj naleznete v následujícím umístění</span><span class="sxs-lookup"><span data-stu-id="c27aa-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="c27aa-108">Foundation\ %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace</span><span class="sxs-lookup"><span data-stu-id="c27aa-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="c27aa-109">Další informace o ComSvcConfig.exe najdete v tématu [postupy: použití modelu COM + Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c27aa-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="c27aa-110">Následující tabulka popisuje režimy, které lze použít s ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c27aa-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="c27aa-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="c27aa-111">Option</span></span>|<span data-ttu-id="c27aa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c27aa-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="c27aa-113">Nainstaluje konfigurační rozhraní modelu COM + modelu služby integrace.</span><span class="sxs-lookup"><span data-stu-id="c27aa-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="c27aa-114">Krátký tvar `/i`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="c27aa-115">Konfigurace pro rozhraní modelu COM + odinstaluje z modelu služby integrace.</span><span class="sxs-lookup"><span data-stu-id="c27aa-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="c27aa-116">Krátký tvar `/u`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="c27aa-117">Zobrazí informace o modelu COM + aplikací a součástí, které mají rozhraní, které jsou nakonfigurované pro integraci Model služby.</span><span class="sxs-lookup"><span data-stu-id="c27aa-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="c27aa-118">Krátký tvar `/l`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="c27aa-119">Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c27aa-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="c27aa-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="c27aa-120">Option</span></span>|<span data-ttu-id="c27aa-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c27aa-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c27aa-122">`/application:`\< *ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="c27aa-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="c27aa-123">Určuje aplikace modelu COM + ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c27aa-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="c27aa-124">Krátký tvar `/a`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="c27aa-125">`/contract:`\< *Atribut ClassID* &#124; *ProgID* &#124; \*,*ID rozhraní* &#124; *InterfaceName* &#124;\*\></span><span class="sxs-lookup"><span data-stu-id="c27aa-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="c27aa-126">Určuje komponenty modelu COM + a rozhraní, které budou nakonfigurované jako kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="c27aa-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="c27aa-127">Krátký tvar `/c`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="c27aa-128">Při zástupného znaku (\*) lze použít při zadávání názvů součásti a rozhraní, doporučujeme, abyste že nepoužijete, protože mohou být vystaveny rozhraní, které jste nechtěli.</span><span class="sxs-lookup"><span data-stu-id="c27aa-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="c27aa-129">`/hosting:`\< *complus* &#124; *byl*\></span><span class="sxs-lookup"><span data-stu-id="c27aa-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="c27aa-130">Určuje, jestli se má používat hostování režim nebo režim hostování webových modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c27aa-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="c27aa-131">Krátký tvar `/h`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="c27aa-132">Použití modelu COM + hostování režim vyžaduje explicitní aktivace aplikace modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c27aa-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="c27aa-133">Použití webového hostingu režim umožňuje aplikace modelu COM + chcete automaticky aktivovat jako vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c27aa-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="c27aa-134">Pokud aplikace modelu COM + je knihovna aplikace, spustí se v procesu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="c27aa-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="c27aa-135">Pokud aplikace modelu COM + je serverová aplikace, spustí se proces Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="c27aa-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="c27aa-136">`/webSite:`\< *Název webu*\></span><span class="sxs-lookup"><span data-stu-id="c27aa-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="c27aa-137">Určuje, se používá na webu při hostování webových hostitelských režimu (v tématu `/hosting` příznak).</span><span class="sxs-lookup"><span data-stu-id="c27aa-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="c27aa-138">Krátký tvar `/w`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="c27aa-139">Pokud není zadán žádný web, se používá výchozí webový server.</span><span class="sxs-lookup"><span data-stu-id="c27aa-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="c27aa-140">`/webDirectory:`\< *WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="c27aa-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="c27aa-141">Určuje virtuální adresář, který pro hostování při publikování na webu se používá (viz `/hosting` příznak).</span><span class="sxs-lookup"><span data-stu-id="c27aa-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="c27aa-142">Krátký tvar `/d`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="c27aa-143">Přidá do výchozí konfiguraci služby pro podporu klientů, které chcete získat definici kontraktu ze služby Exchange Metadata (MEX) koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="c27aa-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="c27aa-144">Krátký tvar `/x`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="c27aa-145">Zobrazí aplikace, součásti a informace o rozhraní jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="c27aa-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="c27aa-146">Krátký tvar `/k`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="c27aa-147">Zabrání zobrazení jeho logo ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c27aa-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="c27aa-148">Krátký tvar `/n`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="c27aa-149">Výstupy všechna upozornění nebo informační text kromě chybám došlo.</span><span class="sxs-lookup"><span data-stu-id="c27aa-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="c27aa-150">Krátký tvar `/v`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="c27aa-151">Zobrazí zprávu využití.</span><span class="sxs-lookup"><span data-stu-id="c27aa-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="c27aa-152">Krátký tvar `/?`.</span><span class="sxs-lookup"><span data-stu-id="c27aa-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="c27aa-153">Konfigurace služby generuje, pokud zadaný rozhraní obsahuje jeden nebo více metoda podpisy, které mohou být zveřejněny.</span><span class="sxs-lookup"><span data-stu-id="c27aa-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="c27aa-154">Během inicializace služby kompatibilní metody zobrazují jako operací na kontrakt služby, a nekompatibilní metody jsou ignorovány a chybí z kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="c27aa-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="c27aa-155">Pokud chybí tento příznak, nevygeneruje nástroj Konfigurace služby při zadané rozhraní obsahuje jednu nebo více metod nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="c27aa-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="c27aa-156">Příklady</span><span class="sxs-lookup"><span data-stu-id="c27aa-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="c27aa-157">Popis</span><span class="sxs-lookup"><span data-stu-id="c27aa-157">Description</span></span>  
 <span data-ttu-id="c27aa-158">Následující příklad přidá `IFinances` rozhraní `ItemOrders.IFinancial` součást (z OnlineStore aplikace COM +) do sady rozhraní, které jsou zveřejněné jako webové služby, pomocí režimu hostování modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="c27aa-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="c27aa-159">Všechna upozornění bude výstup kromě chybám došlo.</span><span class="sxs-lookup"><span data-stu-id="c27aa-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c27aa-160">Kód</span><span class="sxs-lookup"><span data-stu-id="c27aa-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="c27aa-161">Popis</span><span class="sxs-lookup"><span data-stu-id="c27aa-161">Description</span></span>  
 <span data-ttu-id="c27aa-162">Následující příklad přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` součást (z OnlineWarehouse aplikace COM +) do sady rozhraní, které jsou zveřejněné jako webové služby pomocí webového hostingu režimu.</span><span class="sxs-lookup"><span data-stu-id="c27aa-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="c27aa-163">Webová služba je že web hostovaný ve virtuálním adresáři OnlineWarehouse služby IIS.</span><span class="sxs-lookup"><span data-stu-id="c27aa-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c27aa-164">Kód</span><span class="sxs-lookup"><span data-stu-id="c27aa-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="c27aa-165">Popis</span><span class="sxs-lookup"><span data-stu-id="c27aa-165">Description</span></span>  
 <span data-ttu-id="c27aa-166">Následující příklad odebere `IFinances` rozhraní `ItemOrders.Financial` součást (z OnlineStore aplikace COM +) ze sady rozhraní, které jsou zveřejněné jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="c27aa-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c27aa-167">Kód</span><span class="sxs-lookup"><span data-stu-id="c27aa-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="c27aa-168">Popis</span><span class="sxs-lookup"><span data-stu-id="c27aa-168">Description</span></span>  
 <span data-ttu-id="c27aa-169">Následující příklad zobrazí aktuálně zveřejňují rozhraní modelu COM + hostované, spolu s odpovídající adresu a podrobnosti o vazby pro aplikaci OnlineStore modelu COM + v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="c27aa-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c27aa-170">Kód</span><span class="sxs-lookup"><span data-stu-id="c27aa-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="c27aa-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="c27aa-171">See Also</span></span>  
 [<span data-ttu-id="c27aa-172">Postupy: použití modelu COM + Service Model Configuration Tool</span><span class="sxs-lookup"><span data-stu-id="c27aa-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
