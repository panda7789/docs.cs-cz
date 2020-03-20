---
title: Vnitroprocesové souběžné provádění
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 5ca2f03576946a23b3133bbe7532d46c4ad758ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181664"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="e552c-102">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="e552c-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="e552c-103">Počínaje rozhraním .NET Framework 4 můžete použít hostování v procesu vedle sebe ke spuštění více verzí běžného jazykového běhu (CLR) v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="e552c-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="e552c-104">Ve výchozím nastavení jsou spravované součásti modelu COM spuštěny s verzí rozhraní .NET Framework, se kterou byly vytvořeny, bez ohledu na verzi rozhraní .NET Framework načtenou pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="e552c-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="e552c-105">Pozadí</span><span class="sxs-lookup"><span data-stu-id="e552c-105">Background</span></span>  
 <span data-ttu-id="e552c-106">Rozhraní .NET Framework vždy poskytovalo hostování vedle sebe pro aplikace spravovaného kódu, ale před rozhraním .NET Framework 4 neposkytovalo tuto funkci pro spravované součásti modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e552c-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="e552c-107">V minulosti byly spravované součásti modelu COM načtené do procesu spuštěny buď s verzí runtime, která již byla načtena, nebo s nejnovější nainstalovanou verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e552c-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="e552c-108">Pokud tato verze nebyla kompatibilní s komponentou modelu COM, součást by se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e552c-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="e552c-109">Rozhraní .NET Framework 4 poskytuje nový přístup k hostování vedle sebe, který zajišťuje následující:</span><span class="sxs-lookup"><span data-stu-id="e552c-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="e552c-110">Instalace nové verze rozhraní .NET Framework nemá žádný vliv na existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="e552c-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="e552c-111">Aplikace spustit proti verzi rozhraní .NET Framework, které byly vytvořeny s.</span><span class="sxs-lookup"><span data-stu-id="e552c-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="e552c-112">Nepoužívají novou verzi rozhraní .NET Framework, pokud k tomu není výslovně nařízeno.</span><span class="sxs-lookup"><span data-stu-id="e552c-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="e552c-113">Pro aplikace je však snazší přejít na novou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e552c-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="e552c-114">Účinky na uživatele a vývojáře</span><span class="sxs-lookup"><span data-stu-id="e552c-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="e552c-115">**Koncoví uživatelé a správci systému**.</span><span class="sxs-lookup"><span data-stu-id="e552c-115">**End users and system administrators**.</span></span> <span data-ttu-id="e552c-116">Tito uživatelé mohou mít nyní větší jistotu, že při instalaci nové verze runtime, samostatně nebo s aplikací, nebude mít žádný vliv na jejich počítače.</span><span class="sxs-lookup"><span data-stu-id="e552c-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="e552c-117">Existující aplikace budou nadále fungovat stejně jako dříve.</span><span class="sxs-lookup"><span data-stu-id="e552c-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="e552c-118">**Vývojáři aplikací**.</span><span class="sxs-lookup"><span data-stu-id="e552c-118">**Application developers**.</span></span> <span data-ttu-id="e552c-119">Side-by-side hosting nemá téměř žádný vliv na vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="e552c-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="e552c-120">Ve výchozím nastavení aplikace vždy spustit proti verzi rozhraní .NET Framework byly postaveny na; to se nezměnilo.</span><span class="sxs-lookup"><span data-stu-id="e552c-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="e552c-121">Vývojáři však můžete přepsat toto chování a nasměrovat aplikaci ke spuštění v novější verzi rozhraní .NET Framework (viz [scénář 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="e552c-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="e552c-122">**Vývojáři knihoven a spotřebitelé**.</span><span class="sxs-lookup"><span data-stu-id="e552c-122">**Library developers and consumers**.</span></span> <span data-ttu-id="e552c-123">Hostování vedle sebe neřeší problémy s kompatibilitou, kterým vývojáři knihovny čelí.</span><span class="sxs-lookup"><span data-stu-id="e552c-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="e552c-124">Knihovna, která je přímo načtena aplikací – buď <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> prostřednictvím přímého odkazu nebo <xref:System.AppDomain> prostřednictvím volání – nadále používá dobu runtime, do které je načtena.</span><span class="sxs-lookup"><span data-stu-id="e552c-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="e552c-125">Knihovny byste měli otestovat proti všem verzím rozhraní .NET Framework, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="e552c-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="e552c-126">Pokud je aplikace kompilována pomocí runtime rozhraní .NET Framework 4, ale obsahuje knihovnu, která byla vytvořena pomocí dřívějšího běhu runtime, bude tato knihovna také používat runtime rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e552c-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="e552c-127">Pokud však máte aplikaci, která byla vytvořena pomocí dřívějšího běhu runtime a knihovny, která byla vytvořena pomocí rozhraní .NET Framework 4, musíte vynutit, aby aplikace také používala rozhraní .NET Framework 4 (viz [scénář 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="e552c-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="e552c-128">**Spravovaní vývojáři komponent modelu COM**.</span><span class="sxs-lookup"><span data-stu-id="e552c-128">**Managed COM component developers**.</span></span> <span data-ttu-id="e552c-129">V minulosti byly spravované součásti modelu COM automaticky spuštěny pomocí nejnovější verze runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="e552c-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="e552c-130">Nyní můžete spustit komponenty modelu COM proti verzi runtime, se kterou byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="e552c-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="e552c-131">Jak ukazuje následující tabulka, součásti, které byly vytvořeny s rozhraním .NET Framework verze 1.1, mohou být spuštěny vedle sebe s komponentami verze 4, ale nelze je spustit s komponentami verze 2.0, 3.0 nebo 3.5, protože hostování vedle sebe není pro tyto součásti k dispozici Verze.</span><span class="sxs-lookup"><span data-stu-id="e552c-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="e552c-132">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e552c-132">.NET Framework version</span></span>|<span data-ttu-id="e552c-133">1.1</span><span class="sxs-lookup"><span data-stu-id="e552c-133">1.1</span></span>|<span data-ttu-id="e552c-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="e552c-134">2.0 - 3.5</span></span>|<span data-ttu-id="e552c-135">4</span><span class="sxs-lookup"><span data-stu-id="e552c-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="e552c-136">1.1</span><span class="sxs-lookup"><span data-stu-id="e552c-136">1.1</span></span>|<span data-ttu-id="e552c-137">Neuvedeno</span><span class="sxs-lookup"><span data-stu-id="e552c-137">Not applicable</span></span>|<span data-ttu-id="e552c-138">Ne</span><span class="sxs-lookup"><span data-stu-id="e552c-138">No</span></span>|<span data-ttu-id="e552c-139">Ano</span><span class="sxs-lookup"><span data-stu-id="e552c-139">Yes</span></span>|  
    |<span data-ttu-id="e552c-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="e552c-140">2.0 - 3.5</span></span>|<span data-ttu-id="e552c-141">Ne</span><span class="sxs-lookup"><span data-stu-id="e552c-141">No</span></span>|<span data-ttu-id="e552c-142">Neuvedeno</span><span class="sxs-lookup"><span data-stu-id="e552c-142">Not applicable</span></span>|<span data-ttu-id="e552c-143">Ano</span><span class="sxs-lookup"><span data-stu-id="e552c-143">Yes</span></span>|  
    |<span data-ttu-id="e552c-144">4</span><span class="sxs-lookup"><span data-stu-id="e552c-144">4</span></span>|<span data-ttu-id="e552c-145">Ano</span><span class="sxs-lookup"><span data-stu-id="e552c-145">Yes</span></span>|<span data-ttu-id="e552c-146">Ano</span><span class="sxs-lookup"><span data-stu-id="e552c-146">Yes</span></span>|<span data-ttu-id="e552c-147">Neuvedeno</span><span class="sxs-lookup"><span data-stu-id="e552c-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e552c-148">Rozhraní .NET Framework verze 3.0 a 3.5 jsou postupně sestaveny ve verzi 2.0 a není nutné spouštět vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="e552c-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="e552c-149">Jedná se ze své podstaty stejnou verzi.</span><span class="sxs-lookup"><span data-stu-id="e552c-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="e552c-150">Běžné scénáře hostování vedle sebe</span><span class="sxs-lookup"><span data-stu-id="e552c-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="e552c-151">**Scénář 1:** Nativní aplikace, která používá komponenty MODELU COM vytvořené staršími verzemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e552c-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="e552c-152">Nainstalované verze rozhraní .NET Framework: Rozhraní .NET Framework 4 a všechny ostatní verze rozhraní .NET Framework používané komponentami modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e552c-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="e552c-153">Co dělat: V tomto scénáři nedělat nic.</span><span class="sxs-lookup"><span data-stu-id="e552c-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="e552c-154">Součásti modelu COM budou spuštěny s verzí rozhraní .NET Framework, ve které byly zaregistrovány.</span><span class="sxs-lookup"><span data-stu-id="e552c-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="e552c-155">**Scénář 2**: Spravovaná aplikace vytvořená pomocí rozhraní .NET Framework 2.0 SP1, kterou byste raději spouštěli s rozhraním .NET Framework 2.0, ale jste ochotni spustit v rozhraní .NET Framework 4, pokud není k dispozici verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e552c-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="e552c-156">Nainstalované verze rozhraní .NET Framework: Starší verze rozhraní .NET Framework a rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e552c-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="e552c-157">Co dělat: V [konfiguračním souboru aplikace](../configure-apps/index.md) v adresáři aplikace použijte [ \<spouštěcí> element](../configure-apps/file-schema/startup/startup-element.md) a [ \<sadu prvků supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e552c-157">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="e552c-158">**Scénář 3:** Nativní aplikace, která používá komponenty MODELU COM vytvořené staršími verzemi rozhraní .NET Framework, které chcete spustit s rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e552c-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="e552c-159">Nainstalované verze rozhraní .NET Framework: Rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e552c-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="e552c-160">Co dělat: V konfiguračním souboru `<startup>` aplikace v `useLegacyV2RuntimeActivationPolicy` adresáři `true` aplikace `<supportedRuntime>` použijte prvek s atributem nastaveným na a sadu prvků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e552c-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="e552c-161">Příklad</span><span class="sxs-lookup"><span data-stu-id="e552c-161">Example</span></span>  
 <span data-ttu-id="e552c-162">Následující příklad ukazuje nespravovaného hostitele modelu COM, který používá spravovanou komponentu MODELU COM pomocí verze rozhraní .NET Framework, ke které byla komponenta zkompilována.</span><span class="sxs-lookup"><span data-stu-id="e552c-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="e552c-163">Chcete-li spustit následující příklad, zkompilujte a zaregistrujte následující spravovanou komponentu MODELU COM pomocí rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="e552c-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="e552c-164">Pokud chcete komponentu zaregistrovat, klikněte v nabídce **Projekt** na **Příkaz Vlastnosti**, klikněte na kartu **Sestavení** a zaškrtněte políčko **Registrovat pro com interop.**</span><span class="sxs-lookup"><span data-stu-id="e552c-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="e552c-165">Zkompilujte následující nespravovanou aplikaci jazyka C++, která aktivuje objekt COM vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e552c-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e552c-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="e552c-166">See also</span></span>

- [<span data-ttu-id="e552c-167">\<spouštěcí> Element</span><span class="sxs-lookup"><span data-stu-id="e552c-167">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="e552c-168">\<podporovaný modul> Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e552c-168">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
