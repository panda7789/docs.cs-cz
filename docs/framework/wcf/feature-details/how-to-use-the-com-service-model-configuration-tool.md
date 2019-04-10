---
title: 'Postupy: Použití nástroje pro konfiguraci modelu služby COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 5b330a727c0a4a20de13f43fd2844d0b745e5060
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322586"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="f9e45-102">Postupy: Použití nástroje pro konfiguraci modelu služby COM+</span><span class="sxs-lookup"><span data-stu-id="f9e45-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="f9e45-103">Jakmile vyberete příslušné hostující režim, použijte nástroj příkazového řádku konfiguraci modelu služby COM + (ComSvcConfig.exe) ke konfiguraci rozhraní aplikací, které se zveřejní jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9e45-104">Musíte být správcem na počítači lze provádět následující úlohy.</span><span class="sxs-lookup"><span data-stu-id="f9e45-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="f9e45-105">Při použití ComSvcConfig.exe konfigurovat webovou službu, která používá nejnovější verze modelu služby (aktuálně v4.5) na počítači s Windows 7, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="f9e45-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1. <span data-ttu-id="f9e45-106">Nastavte klíč registru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` na hodnotu DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="f9e45-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2. <span data-ttu-id="f9e45-107">Spustit comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="f9e45-107">Run comsvcconfig.exe</span></span>  
  
3. <span data-ttu-id="f9e45-108">Vrátit přidali v kroku 1 zpět na původní hodnotu klíče registru nebo odstranit, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f9e45-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f9e45-109">Při vrácení tohoto klíče registru je důležité.</span><span class="sxs-lookup"><span data-stu-id="f9e45-109">Reverting this registry key is important.</span></span> <span data-ttu-id="f9e45-110">Toto je kompatibility klíče.</span><span class="sxs-lookup"><span data-stu-id="f9e45-110">This is a compatibility key.</span></span> <span data-ttu-id="f9e45-111">Není při vrácení této změny může způsobit problémy s jinými aplikacemi .NET na počítači spuštěná).</span><span class="sxs-lookup"><span data-stu-id="f9e45-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f9e45-112">Při použití ComSvcConfig.exe/install na počítači s Windows 8 dialogové okno se zobrazí s oznámením "aplikace ve vašem počítači potřebuje následující funkce Windows: rozhraní .NET Framework 3.5 (zahrnuje .NET 2.0 a .NET 3.0" Pokud není nainstalované rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="f9e45-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="f9e45-113">Toto dialogové okno může být ignorován.</span><span class="sxs-lookup"><span data-stu-id="f9e45-113">This dialog may be ignored.</span></span> <span data-ttu-id="f9e45-114">Případně můžete sed OnlyUseLatestCLR klíče registru na hodnotu DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="f9e45-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="f9e45-115">Chcete-li přidat rozhraní do sady rozhraní, které mají být vystavena jako webové služby, pomocí hostující režim modelu COM +</span><span class="sxs-lookup"><span data-stu-id="f9e45-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="f9e45-116">Spuštění pomocí ComSvcConfig / `/install` a `/hosting:complus` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="f9e45-117">Přidá příkaz `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z OnlineStore aplikace COM +) do sady rozhraní, která bude vystavena jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="f9e45-118">Služba používá hostující režim modelu COM + a proto vyžaduje aktivaci explicitní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9e45-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="f9e45-119">Zástupný znak hvězdička (\*) můžete využít pro komponentu a rozhraní, vyhněte se ho používat, protože můžete chtít pouze vybranou funkci jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="f9e45-120">Spuštění v budoucí verzi této součásti, pomocí zástupného znaku může nechtěně vystavit rozhraní, která nemusí být k dispozici, pokud bylo zjištěno syntaxe konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f9e45-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="f9e45-121">/ Verbose – možnost instruuje nástroj, který zobrazí upozornění kromě nějaké chyby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="f9e45-122">Kontrakt služby vystavené bude obsahovat všechny metody z `IFinances` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9e45-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="f9e45-123">Můžete přidat pouze konkrétní metody z rozhraní do sady rozhraní, které mají být vystavena jako webové služby, pomocí hostující režim modelu COM +</span><span class="sxs-lookup"><span data-stu-id="f9e45-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="f9e45-124">Spuštění pomocí ComSvcConfig / `/install` a `/hosting:complus` možnosti s explicitní názvy z požadovaných metod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="f9e45-125">Tento příkaz přidá pouze `Credit` a `Debit` metody ze `IFinances` rozhraní jako operace pro kontrakt vystavené služby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="f9e45-126">Všechny metody v rozhraní budou vypuštěny ze smlouvy a nebudou volány z klienty webové služby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="f9e45-127">Chcete-li přidat rozhraní do sady rozhraní, které mají být vystavena jako webové služby, pomocí hostující režim webu</span><span class="sxs-lookup"><span data-stu-id="f9e45-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="f9e45-128">Spuštění pomocí ComSvcConfig / `/install` možnost a `/hosting:was` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="f9e45-129">Přidá příkaz `IStockLevels` rozhraní na `ItemInventory.Warehouse` komponenty (z OnlineWarehouse aplikace COM +) do sady rozhraní, která bude vystavena jako webové služby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="f9e45-130">Služba je hostovaná v OnlineWarehouse virtuální adresář služby IIS, nikoli v modelu COM + na webu, a proto se automaticky aktivuje aplikace podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="f9e45-131">K použití v procesu konfigurace hostované webové aplikace modelu COM + nastavené ke spuštění jako knihovny aplikace spíše než serverové aplikace pomocí konzoly pro správu služby Component Services.</span><span class="sxs-lookup"><span data-stu-id="f9e45-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="f9e45-132">Aplikace, konfigurované jako Server aplikace použít standardní režim hostované webové a proces směrování pro zpracování každého požadavku se vám účtovat.</span><span class="sxs-lookup"><span data-stu-id="f9e45-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="f9e45-133">`/mex` Možnost přidá další koncový bod služby Metadata Exchange (MEX), který používá stejné přenosové jako koncový bod služby vaší aplikace pro podporu klientů, které chcete načíst definici kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="f9e45-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="f9e45-134">Chcete-li odebrat webovou službu pro zadané rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9e45-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="f9e45-135">Spuštění pomocí ComSvcConfig / `/uninstall` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="f9e45-136">Příkaz odebere `IFinances` rozhraní na `ItemOrders.Financial` (z OnlineStore aplikace COM +).</span><span class="sxs-lookup"><span data-stu-id="f9e45-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="f9e45-137">Na seznamu aktuálně vystavit rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9e45-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="f9e45-138">Spuštění pomocí ComSvcConfig / `/list` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="f9e45-139">Příkaz vypíše aktuálně vystavené rozhraní spolu s příslušnou adresou a podrobnosti o vazbu, omezená na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f9e45-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="f9e45-140">Seznam aktuálně konkrétní vystavit rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9e45-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="f9e45-141">Spuštění pomocí ComSvcConfig / `/list` možnosti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="f9e45-142">Seznamy příkazů aktuálně vystavena COM +.-hostované rozhraní spolu s příslušnou adresou a podrobnosti o vazbu pro aplikaci OnlineStore modelu COM + v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f9e45-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="f9e45-143">Chcete-li zobrazit nápovědu pro možnosti, které je možné pomocí nástroje</span><span class="sxs-lookup"><span data-stu-id="f9e45-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="f9e45-144">Spuštění pomocí ComSvcConfig / /?</span><span class="sxs-lookup"><span data-stu-id="f9e45-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="f9e45-145">možnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e45-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9e45-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9e45-146">See also</span></span>

- [<span data-ttu-id="f9e45-147">Integrace s aplikacemi modelu COM+ – přehled</span><span class="sxs-lookup"><span data-stu-id="f9e45-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
