---
title: "Postupy: Použití nástroje pro konfiguraci modelu služby COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd89a3333ab68b7d580c813a4b7741686b46c5b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="eb00b-102">Postupy: Použití nástroje pro konfiguraci modelu služby COM+</span><span class="sxs-lookup"><span data-stu-id="eb00b-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="eb00b-103">Jakmile vyberete příslušné hostující režim pomocí nástroje příkazového řádku modelu COM + Service Model Configuration (ComSvcConfig.exe) ke konfiguraci rozhraní aplikace, které se zveřejní jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb00b-104">Musíte být správce na počítači lze provádět následující úlohy.</span><span class="sxs-lookup"><span data-stu-id="eb00b-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="eb00b-105">Při použití ComSvcConfig.exe na počítače s Windows 7 konfigurovat webovou službu, která používá nejnovější verze modelu (aktuálně v4.5), proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="eb00b-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1.  <span data-ttu-id="eb00b-106">Nastavte klíč registru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` na hodnotu DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="eb00b-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2.  <span data-ttu-id="eb00b-107">Spustit comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="eb00b-107">Run comsvcconfig.exe</span></span>  
  
3.  <span data-ttu-id="eb00b-108">Vrátit přidali v kroku 1 zpět na původní hodnotu klíče registru nebo ho odstranit, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="eb00b-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb00b-109">Při vrácení tohoto klíče registru je důležité.</span><span class="sxs-lookup"><span data-stu-id="eb00b-109">Reverting this registry key is important.</span></span> <span data-ttu-id="eb00b-110">Jedná se o klíč kompatibility.</span><span class="sxs-lookup"><span data-stu-id="eb00b-110">This is a compatibility key.</span></span> <span data-ttu-id="eb00b-111">Tato změna není vrácení může způsobit problémy s jinými aplikacemi .NET spuštěná na tomto počítači).</span><span class="sxs-lookup"><span data-stu-id="eb00b-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="eb00b-112">Při použití ComSvcConfig.exe/install na počítače s Windows 8, zobrazí se dialogové okno se zobrazí s oznámením "aplikace ve vašem počítači potřebuje následující funkce systému Windows: rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a .NET 3.0" Pokud není nainstalované rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="eb00b-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="eb00b-113">Tento dialog můžete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="eb00b-113">This dialog may be ignored.</span></span> <span data-ttu-id="eb00b-114">Případně můžete menšit OnlyUseLatestCLR klíče registru na hodnotu DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="eb00b-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="eb00b-115">Chcete-li přidat rozhraní do sady rozhraní, která se mají být exponovány jako webové služby, který je hostitelem režimu modelu COM +</span><span class="sxs-lookup"><span data-stu-id="eb00b-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="eb00b-116">Spustí ComSvcConfig / pomocí `/install` a `/hosting:complus` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="eb00b-117">Příkaz přidá `IFinances` rozhraní `ItemOrders.IFinancial` součást (z OnlineStore aplikace COM +) do sady rozhraní, které jsou k dispozici jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="eb00b-118">Služba používá hostování režimu modelu COM + a proto vyžaduje aktivaci explicitní aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb00b-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="eb00b-119">Pokud pro komponentu a rozhraní můžete použít zástupný znak hvězdičky (\*), nepoužívejte ji vzhledem k tomu, že chcete vystavit pouze vybrané funkce jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="eb00b-120">Po spuštění s budoucí verze této součásti, pomocí zástupného může neúmyslně vystavit rozhraní, která nemusí být při syntaxe konfigurace byla určena.</span><span class="sxs-lookup"><span data-stu-id="eb00b-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="eb00b-121">/ Verbose – možnost instruuje nástroj, který zobrazí upozornění kromě případné chyby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="eb00b-122">Kontrakt služby zveřejněné bude obsahovat všechny metody z `IFinances` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb00b-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="eb00b-123">Chcete-li přidat pouze konkrétní metody z rozhraní sadu rozhraní, která se mají být exponovány jako webové služby, který je hostitelem režimu modelu COM +</span><span class="sxs-lookup"><span data-stu-id="eb00b-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="eb00b-124">Spustí ComSvcConfig / pomocí `/install` a `/hosting:complus` možnosti explicitní názvy požadované metody, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="eb00b-125">Příkaz přidá jenom `Credit` a `Debit` metody z `IFinances` rozhraní jako operace zveřejněné servisní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="eb00b-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="eb00b-126">Všechny ostatní metody na rozhraní bude vynechán ze smlouvy a nebude možné volat z klienty webové služby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="eb00b-127">Přidat sadu rozhraní, která se mají být exponovány jako webové služby, pomocí režimu hostování webových rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb00b-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="eb00b-128">Spustí ComSvcConfig / pomocí `/install` možnost a `/hosting:was` možnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="eb00b-129">Příkaz přidá `IStockLevels` rozhraní na `ItemInventory.Warehouse` součást (z OnlineWarehouse aplikace COM +) do sady rozhraní, které jsou k dispozici jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="eb00b-130">Služba je hostovaná v OnlineWarehouse virtuálního adresáře služby IIS, ne v modelu COM + na webu, a proto bude aplikace automaticky aktivována podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="eb00b-131">K použití v rámci procesu konfigurace hostované webové aplikace modelu COM + musí být nakonfigurována pro spuštění jako knihovny aplikace a nikoli serverová aplikace pomocí konzoly pro správu služby komponent.</span><span class="sxs-lookup"><span data-stu-id="eb00b-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="eb00b-132">Aplikace, nakonfigurované jako Server aplikace použijte standardní režim hostované webové a způsobit procesu směrování pro každou žádost zpracovat.</span><span class="sxs-lookup"><span data-stu-id="eb00b-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="eb00b-133">`/mex` Možnost přidá další koncový bod služby Exchange Metadata (MEX), který používá stejné přenosu jako koncový bod služby aplikace pro podporu klientů, které chcete získat definici kontraktu ze služby.</span><span class="sxs-lookup"><span data-stu-id="eb00b-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="eb00b-134">Chcete-li odebrat webové služby pro dané rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb00b-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="eb00b-135">Spustí ComSvcConfig / pomocí `/uninstall` možnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="eb00b-136">Příkaz odebere `IFinances` rozhraní na `ItemOrders.Financial` součásti (z OnlineStore aplikace COM +).</span><span class="sxs-lookup"><span data-stu-id="eb00b-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="eb00b-137">Seznam aktuálně vystavovaných rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb00b-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="eb00b-138">Spustí ComSvcConfig / pomocí `/list` možnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="eb00b-139">Příkaz seznam aktuálně zveřejněné rozhraní, spolu s odpovídající adresu a podrobnosti vazby obor v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="eb00b-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="eb00b-140">Seznam aktuálně konkrétní zveřejněné rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb00b-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="eb00b-141">Spustí ComSvcConfig / pomocí `/list` možnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="eb00b-142">Příkaz seznamy aktuálně zveřejněné modelu COM +-hostované rozhraní, spolu s odpovídající adresu a podrobnosti o vazby pro aplikaci OnlineStore modelu COM + v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="eb00b-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="eb00b-143">Chcete-li zobrazit nápovědu pro možnosti, které lze použít s nástroj</span><span class="sxs-lookup"><span data-stu-id="eb00b-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="eb00b-144">Spustí ComSvcConfig / pomocí /?</span><span class="sxs-lookup"><span data-stu-id="eb00b-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="eb00b-145">možnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb00b-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="eb00b-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb00b-146">See Also</span></span>  
 [<span data-ttu-id="eb00b-147">Přehled integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="eb00b-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
