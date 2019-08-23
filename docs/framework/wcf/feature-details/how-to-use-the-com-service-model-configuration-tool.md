---
title: 'Postupy: Použití nástroje pro konfiguraci modelu služby COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 9677e516ef6c91ef344e10bc8f608a397a4ed157
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966140"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="90bfb-102">Postupy: Použití nástroje pro konfiguraci modelu služby COM+</span><span class="sxs-lookup"><span data-stu-id="90bfb-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="90bfb-103">Po výběru vhodného hostitelského režimu použijte nástroj příkazového řádku konfigurace modelu COM+ (ComSvcConfig. exe) ke konfiguraci rozhraní aplikace, která budou vystavena jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="90bfb-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90bfb-104">Abyste mohli provádět některé z následujících úkolů, musíte být správcem počítače.</span><span class="sxs-lookup"><span data-stu-id="90bfb-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="90bfb-105">Při použití nástroje ComSvcConfig. exe na počítači se systémem Windows 7 ke konfiguraci webové služby pro použití nejnovější verze modelu služby (aktuálně v 4.5) proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="90bfb-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1. <span data-ttu-id="90bfb-106">Nastavte klíč `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` registru na hodnotu DWORD 0x00000001.</span><span class="sxs-lookup"><span data-stu-id="90bfb-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2. <span data-ttu-id="90bfb-107">Spusťte ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="90bfb-107">Run comsvcconfig.exe</span></span>  
  
3. <span data-ttu-id="90bfb-108">Vrátí klíč registru přidaný v kroku 1 zpátky do původní hodnoty nebo ho odstraňte, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="90bfb-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="90bfb-109">Vrácení tohoto klíče registru je důležité.</span><span class="sxs-lookup"><span data-stu-id="90bfb-109">Reverting this registry key is important.</span></span> <span data-ttu-id="90bfb-110">Toto je klíč kompatibility.</span><span class="sxs-lookup"><span data-stu-id="90bfb-110">This is a compatibility key.</span></span> <span data-ttu-id="90bfb-111">Nevrácení této změny může způsobit problémy s jinými aplikacemi .NET běžícími v počítači.</span><span class="sxs-lookup"><span data-stu-id="90bfb-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="90bfb-112">Při použití ComSvcConfig. exe/install v počítači s Windows 8 se zobrazí dialogové okno s informacemi o tom, že aplikace na vašem počítači potřebuje tuto funkci Windows: .NET Framework 3,5 (zahrnuje .NET 2,0 a .NET 3,0, pokud není nainstalovaná .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="90bfb-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="90bfb-113">Toto dialogové okno může být ignorováno.</span><span class="sxs-lookup"><span data-stu-id="90bfb-113">This dialog may be ignored.</span></span> <span data-ttu-id="90bfb-114">Alternativně můžete klíč registru OnlyUseLatestCLR SED na hodnotu DWORD 0x00000001.</span><span class="sxs-lookup"><span data-stu-id="90bfb-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="90bfb-115">Přidání rozhraní do sady rozhraní, které mají být zveřejněny jako webové služby, pomocí hostitelského režimu COM+</span><span class="sxs-lookup"><span data-stu-id="90bfb-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
- <span data-ttu-id="90bfb-116">Spusťte ComSvcConfig pomocí `/install` možností a `/hosting:complus` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="90bfb-117">Příkaz přidá `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z aplikace OnlineStore com+) do sady rozhraní, které budou zveřejněny jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="90bfb-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="90bfb-118">Služba používá hostitelský režim modelu COM+, takže vyžaduje explicitní aktivaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="90bfb-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="90bfb-119">I když se znak hvězdičky (\*) dá použít pro komponentu a rozhraní, nepoužívejte ho, protože možná budete chtít vystavit jenom vybrané funkce jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="90bfb-120">Pokud se spustí s budoucí verzí této součásti, může použití zástupného znaku neúmyslně vystavit rozhraní, které nemusí být k dispozici při určení syntaxe konfigurace.</span><span class="sxs-lookup"><span data-stu-id="90bfb-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="90bfb-121">Možnost/verbose dá nástroji pokyn, aby zobrazoval upozornění spolu s případnými chybami.</span><span class="sxs-lookup"><span data-stu-id="90bfb-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="90bfb-122">Kontrakt pro vydanou službu bude obsahovat všechny metody z `IFinances` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90bfb-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="90bfb-123">Chcete-li přidat pouze konkrétní metody z rozhraní do sady rozhraní, které mají být zveřejněny jako webové služby, pomocí hostitelského režimu COM+</span><span class="sxs-lookup"><span data-stu-id="90bfb-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
- <span data-ttu-id="90bfb-124">Spusťte ComSvcConfig pomocí `/install` možností a `/hosting:complus` s explicitním pojmenování požadovaných metod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="90bfb-125">Příkaz přidá pouze `Credit` metody a `Debit` z `IFinances` rozhraní jako operace do vystavené kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="90bfb-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="90bfb-126">Všechny ostatní metody rozhraní budou z kontraktu vynechány a nebude možné je volat od klientů webové služby.</span><span class="sxs-lookup"><span data-stu-id="90bfb-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="90bfb-127">Přidání rozhraní do sady rozhraní, které mají být zveřejněny jako webové služby, pomocí režimu hostování webu</span><span class="sxs-lookup"><span data-stu-id="90bfb-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
- <span data-ttu-id="90bfb-128">Spusťte ComSvcConfig pomocí `/install` možnosti `/hosting:was` a možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="90bfb-129">Příkaz přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` součásti (z aplikace OnlineWarehouse com+) do sady rozhraní, které budou zveřejněny jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="90bfb-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="90bfb-130">Služba je web hostovaný ve virtuálním adresáři OnlineWarehouse služby IIS, nikoli v modelu COM+, a proto je aplikace automaticky aktivována podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="90bfb-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="90bfb-131">Chcete-li použít konfiguraci v rámci procesu hostovaného v rámci webu, musí být aplikace modelu COM+ nakonfigurována tak, aby běžela jako aplikace knihovny, nikoli serverová aplikace pomocí konzoly pro správu služby Component Services.</span><span class="sxs-lookup"><span data-stu-id="90bfb-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="90bfb-132">Aplikace nakonfigurované jako serverové aplikace používají standardní režim v rámci webu a při zpracování jednotlivých požadavků naúčtují směrování procesu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="90bfb-133">Tato `/mex` možnost přidá koncový bod služby pro výměnu metadat (MEX), který používá stejný přenos jako koncový bod služby aplikace, aby podporoval klienty, kteří chtějí z této služby načíst definici smlouvy.</span><span class="sxs-lookup"><span data-stu-id="90bfb-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="90bfb-134">Odebrání webové služby pro zadané rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bfb-134">To remove a Web service for a specified interface</span></span>  
  
- <span data-ttu-id="90bfb-135">Spusťte ComSvcConfig pomocí `/uninstall` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="90bfb-136">Příkaz odebere `IFinances` rozhraní `ItemOrders.Financial` součásti (z aplikace modelu COM+ OnlineStore).</span><span class="sxs-lookup"><span data-stu-id="90bfb-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="90bfb-137">Výpis aktuálně vystavených rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bfb-137">To list currently exposed interfaces</span></span>  
  
- <span data-ttu-id="90bfb-138">Spusťte ComSvcConfig pomocí `/list` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="90bfb-139">Příkaz vypíše aktuálně vystavená rozhraní spolu s odpovídajícími podrobnostmi adres a vazeb v oboru pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="90bfb-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="90bfb-140">Seznam konkrétních aktuálně vystavených rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bfb-140">To list specific currently exposed interfaces</span></span>  
  
- <span data-ttu-id="90bfb-141">Spusťte ComSvcConfig pomocí `/list` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="90bfb-142">Příkaz vypíše aktuálně vystavená rozhraní založená na modelu COM+ spolu s odpovídajícími podrobnostmi adres a vazeb pro aplikaci OnlineStore COM+ na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="90bfb-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="90bfb-143">Zobrazení pomocníka s možnostmi, které lze použít s nástrojem</span><span class="sxs-lookup"><span data-stu-id="90bfb-143">To display help on the options that can be used with the utility</span></span>  
  
- <span data-ttu-id="90bfb-144">Spustit ComSvcConfig pomocí/?</span><span class="sxs-lookup"><span data-stu-id="90bfb-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="90bfb-145">, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90bfb-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="90bfb-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90bfb-146">See also</span></span>

- [<span data-ttu-id="90bfb-147">Přehled integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="90bfb-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
