---
title: Vnitroprocesové souběžné provádění
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37c2ad92af938c1816c275ce217e48652b0628d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141255"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="9f34c-102">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="9f34c-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="9f34c-103">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít v procesu – souběžně hostování v jediném procesu spuštění více verzí modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9f34c-103">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="9f34c-104">Ve výchozím nastavení spravované komponenty modelu COM s verzí rozhraní .NET Framework, kterými byly vytvořeny, bez ohledu na verzi rozhraní .NET Framework, který je načten pro proces spuštění.</span><span class="sxs-lookup"><span data-stu-id="9f34c-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="9f34c-105">Pozadí</span><span class="sxs-lookup"><span data-stu-id="9f34c-105">Background</span></span>  
 <span data-ttu-id="9f34c-106">Rozhraní .NET Framework má vždy zadaná vedle sebe hostování pro spravovaný kód aplikace, ale předtím, než [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], neposkytl, které tuto funkci pro spravované komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9f34c-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="9f34c-107">V minulosti spravované komponenty modelu COM, která byla načtena do procesu běžel s verzí modulu runtime, který byl již načten nebo s nainstalovanou verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f34c-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="9f34c-108">Pokud tato verze není kompatibilní s komponenty modelu COM, součást selže.</span><span class="sxs-lookup"><span data-stu-id="9f34c-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="9f34c-109">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Nabízí nový přístup k hostování vedle sebe, která zajišťuje následující:</span><span class="sxs-lookup"><span data-stu-id="9f34c-109">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
-   <span data-ttu-id="9f34c-110">Instalace nové verze rozhraní .NET Framework nemá žádný vliv na stávající aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f34c-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
-   <span data-ttu-id="9f34c-111">Aplikace běží na verzi rozhraní .NET Framework, se kterými byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="9f34c-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="9f34c-112">Nepoužívají novou verzi rozhraní .NET Framework pokud výslovně směrované. Uděláte to tak.</span><span class="sxs-lookup"><span data-stu-id="9f34c-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="9f34c-113">Je však snazší pro aplikace pro přechod na novou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f34c-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="9f34c-114">Vliv na uživatele a vývojáře</span><span class="sxs-lookup"><span data-stu-id="9f34c-114">Effects on Users and Developers</span></span>  
  
-   <span data-ttu-id="9f34c-115">**Koncoví uživatelé a správci systému**.</span><span class="sxs-lookup"><span data-stu-id="9f34c-115">**End users and system administrators**.</span></span> <span data-ttu-id="9f34c-116">Tito uživatelé teď můžou mít větší jistotu, že při instalaci nové verze modulu runtime, buď samostatně, nebo s aplikací, bude mít žádný vliv na svých počítačích.</span><span class="sxs-lookup"><span data-stu-id="9f34c-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="9f34c-117">Stávající aplikace bude dál běžet podle před nástupem prostředí.</span><span class="sxs-lookup"><span data-stu-id="9f34c-117">Existing applications will continue to run as they did before.</span></span>  
  
-   <span data-ttu-id="9f34c-118">**Vývojáři aplikací**.</span><span class="sxs-lookup"><span data-stu-id="9f34c-118">**Application developers**.</span></span> <span data-ttu-id="9f34c-119">Hostování vedle sebe nemá téměř žádný vliv na vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="9f34c-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="9f34c-120">Ve výchozím nastavení aplikace vždy spustit proti verzi rozhraní .NET Framework, které byly vytvořeny. To se nezměnil.</span><span class="sxs-lookup"><span data-stu-id="9f34c-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="9f34c-121">Však mohou vývojáři toto chování přepsat a nasměrovat aplikace na spouštění v novější verzi rozhraní .NET Framework (viz [scénář 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="9f34c-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
-   <span data-ttu-id="9f34c-122">**Vývojáři knihoven a spotřebitelé**.</span><span class="sxs-lookup"><span data-stu-id="9f34c-122">**Library developers and consumers**.</span></span> <span data-ttu-id="9f34c-123">Hostování vedle sebe nevyřeší problémy s kompatibilitou vývojáři této knihovny pro rozpoznávání tváře.</span><span class="sxs-lookup"><span data-stu-id="9f34c-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="9f34c-124">Knihovnu, která je přímo načíst aplikací – buď prostřednictvím přímého odkazu nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> volání – pořád používá modul runtime <xref:System.AppDomain> je načten do.</span><span class="sxs-lookup"><span data-stu-id="9f34c-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="9f34c-125">Měli byste otestovat knihovny pro všechny verze rozhraní .NET Framework, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="9f34c-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="9f34c-126">Pokud aplikace je kompilována použitím [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime ale obsahuje knihovnu, která byla vytvořena pomocí starší modul runtime, knihovny použije [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="9f34c-126">If an application is compiled using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime but includes a library that was built using an earlier runtime, that library will use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime as well.</span></span> <span data-ttu-id="9f34c-127">Nicméně pokud máte aplikaci, která byla vytvořena pomocí starší modul runtime a knihovnu, která byla vytvořena pomocí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], musí přinutit aplikaci použít také [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (naleznete v tématu [scénář 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="9f34c-127">However, if you have an application that was built using an earlier runtime and a library that was built using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], you must force your application to also use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (see [scenario 3](#scenarios)).</span></span>  
  
-   <span data-ttu-id="9f34c-128">**Vývojáři komponent COM pro spravované**.</span><span class="sxs-lookup"><span data-stu-id="9f34c-128">**Managed COM component developers**.</span></span> <span data-ttu-id="9f34c-129">V minulosti spravované komponenty modelu COM automaticky spustili pomocí nejnovější verze modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="9f34c-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="9f34c-130">Teď můžete spustit komponenty modelu COM s verzí modulu runtime, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="9f34c-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="9f34c-131">Jak je znázorněno v následující tabulce, komponenty, které byly vytvořeny s použitím rozhraní .NET Framework verze 1.1 lze spustit souběžně s verzí 4 komponenty, ale nelze je spustit s verzí 2.0, 3.0 nebo 3.5 komponenty, protože není k dispozici pro ty hostování vedle sebe verze.</span><span class="sxs-lookup"><span data-stu-id="9f34c-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="9f34c-132">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f34c-132">.NET Framework version</span></span>|<span data-ttu-id="9f34c-133">1.1</span><span class="sxs-lookup"><span data-stu-id="9f34c-133">1.1</span></span>|<span data-ttu-id="9f34c-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="9f34c-134">2.0 - 3.5</span></span>|<span data-ttu-id="9f34c-135">4</span><span class="sxs-lookup"><span data-stu-id="9f34c-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="9f34c-136">1.1</span><span class="sxs-lookup"><span data-stu-id="9f34c-136">1.1</span></span>|<span data-ttu-id="9f34c-137">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="9f34c-137">Not applicable</span></span>|<span data-ttu-id="9f34c-138">Ne</span><span class="sxs-lookup"><span data-stu-id="9f34c-138">No</span></span>|<span data-ttu-id="9f34c-139">Ano</span><span class="sxs-lookup"><span data-stu-id="9f34c-139">Yes</span></span>|  
    |<span data-ttu-id="9f34c-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="9f34c-140">2.0 - 3.5</span></span>|<span data-ttu-id="9f34c-141">Ne</span><span class="sxs-lookup"><span data-stu-id="9f34c-141">No</span></span>|<span data-ttu-id="9f34c-142">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="9f34c-142">Not applicable</span></span>|<span data-ttu-id="9f34c-143">Ano</span><span class="sxs-lookup"><span data-stu-id="9f34c-143">Yes</span></span>|  
    |<span data-ttu-id="9f34c-144">4</span><span class="sxs-lookup"><span data-stu-id="9f34c-144">4</span></span>|<span data-ttu-id="9f34c-145">Ano</span><span class="sxs-lookup"><span data-stu-id="9f34c-145">Yes</span></span>|<span data-ttu-id="9f34c-146">Ano</span><span class="sxs-lookup"><span data-stu-id="9f34c-146">Yes</span></span>|<span data-ttu-id="9f34c-147">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="9f34c-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9f34c-148">Verze rozhraní .NET framework 3.0 a 3.5 jsou postupně sestavena na verzi 2.0 a není potřeba pracovat souběžně.</span><span class="sxs-lookup"><span data-stu-id="9f34c-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="9f34c-149">Toto jsou ze své podstaty stejnou verzi.</span><span class="sxs-lookup"><span data-stu-id="9f34c-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="9f34c-150">Běžné scénáře hostování vedle sebe</span><span class="sxs-lookup"><span data-stu-id="9f34c-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
-   <span data-ttu-id="9f34c-151">**Scénář 1:** Nativní aplikace, který používá COM komponenty sestavené v předchozích verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f34c-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="9f34c-152">Nainstalovaná verze rozhraní .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a všechny ostatní verze rozhraní .NET Framework používá komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9f34c-152">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="9f34c-153">Co dělat: V tomto scénáři neprovádějte žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="9f34c-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="9f34c-154">Komponenty modelu COM se spustí s verzí rozhraní .NET Framework byla zaregistrována.</span><span class="sxs-lookup"><span data-stu-id="9f34c-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
-   <span data-ttu-id="9f34c-155">**Scénář 2**: Spravované aplikace vytvořené pomocí [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] , který chcete spustit s [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale mají snahu si spouštět [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Pokud není k dispozici verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="9f34c-155">**Scenario 2**: Managed application built with the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="9f34c-156">Nainstalovaná verze rozhraní .NET framework: Starší verzi rozhraní .NET Framework a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f34c-156">.NET Framework versions installed: An earlier version of the .NET Framework and the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="9f34c-157">Co dělat: V [konfiguračního souboru aplikace](../../../docs/framework/configure-apps/index.md) v adresáři aplikace, použijte [ \<spuštění > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) a [ \<supportedRuntime >–element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) nastavte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9f34c-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="9f34c-158">**Scénář 3:** Nativní aplikace, který používá COM komponenty sestavené v předchozích verzích rozhraní .NET Framework, kterou chcete spustit s [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f34c-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="9f34c-159">Nainstalovaná verze rozhraní .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f34c-159">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="9f34c-160">Co dělat: V konfiguračním souboru aplikace v adresáři aplikace, použijte `<startup>` element s `useLegacyV2RuntimeActivationPolicy` atribut nastaven na `true` a `<supportedRuntime>` element nastavte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9f34c-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="9f34c-161">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f34c-161">Example</span></span>  
 <span data-ttu-id="9f34c-162">Následující příklad ukazuje nespravovaný hostitel modelu COM, na kterém běží spravované komponenty modelu COM pomocí verze rozhraní .NET Framework, která komponenta byla sestavena pro použití.</span><span class="sxs-lookup"><span data-stu-id="9f34c-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="9f34c-163">Spustit v následujícím příkladu, kompilaci a registraci následující spravované pomocí komponenty modelu COM [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f34c-163">To run the following example, compile and register the following managed COM component using the [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span></span> <span data-ttu-id="9f34c-164">K registraci komponenty, na **projektu** nabídky, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **sestavení** kartu a potom vyberte **zaregistrovat pro interoperabilitu COM**zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="9f34c-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9f34c-165">Zkompilujte následující nespravovaná aplikace C++, která se aktivuje objekt modelu COM, který je vytvořen z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f34c-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f34c-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f34c-166">See also</span></span>

- [<span data-ttu-id="9f34c-167">\<Po spuštění > – Element</span><span class="sxs-lookup"><span data-stu-id="9f34c-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="9f34c-168">\<supportedRuntime > – Element</span><span class="sxs-lookup"><span data-stu-id="9f34c-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
