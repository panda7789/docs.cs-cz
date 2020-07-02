---
title: Vnitroprocesové souběžné provádění
description: Použijte souběžné hostování v procesu k provedení mnoha verzí modulu CLR (Common Language Runtime) v jednom procesu .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 078f2eaada8fac57138bef22d46218ef2ccda835
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622598"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="765d7-103">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="765d7-103">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="765d7-104">Počínaje .NET Framework 4 můžete použít Souběžné hostování v rámci procesu ke spouštění více verzí modulu CLR (Common Language Runtime) v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="765d7-104">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="765d7-105">Ve výchozím nastavení se spravované komponenty modelu COM spouštějí s verzí .NET Framework, se kterou byly vytvořeny, bez ohledu na .NET Framework verzi, která je pro tento proces načtena.</span><span class="sxs-lookup"><span data-stu-id="765d7-105">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="765d7-106">Pozadí</span><span class="sxs-lookup"><span data-stu-id="765d7-106">Background</span></span>  
 <span data-ttu-id="765d7-107">.NET Framework vždy poskytoval Souběžné hostování pro aplikace spravovaného kódu, ale před .NET Framework 4 neposkytovali tuto funkci pro spravované komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="765d7-107">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="765d7-108">V minulosti spravované komponenty modelu COM, které byly načteny do procesu, byly spuštěny buď s verzí modulu runtime, který již byl načten, nebo s nejnovější nainstalovanou verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="765d7-108">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="765d7-109">Pokud tato verze není kompatibilní s komponentou modelu COM, komponenta by se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="765d7-109">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="765d7-110">.NET Framework 4 poskytuje nový přístup k souběžnému hostování, který zajišťuje následující:</span><span class="sxs-lookup"><span data-stu-id="765d7-110">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="765d7-111">Instalace nové verze .NET Framework nemá žádný vliv na existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="765d7-111">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="765d7-112">Aplikace běží na verzi .NET Framework, se kterou byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="765d7-112">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="765d7-113">Nepoužívají novou verzi .NET Framework, pokud to není výslovně přesměrováno.</span><span class="sxs-lookup"><span data-stu-id="765d7-113">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="765d7-114">Pro aplikace je však snazší přejít na použití nové verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="765d7-114">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="765d7-115">Účinky na uživatele a vývojáře</span><span class="sxs-lookup"><span data-stu-id="765d7-115">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="765d7-116">**Koncoví uživatelé a správci systému**.</span><span class="sxs-lookup"><span data-stu-id="765d7-116">**End users and system administrators**.</span></span> <span data-ttu-id="765d7-117">Tito uživatelé teď můžou mít větší jistotu, že když si nainstalují novou verzi modulu runtime, ať už nezávisle nebo s aplikací, nebude mít žádný vliv na jejich počítače.</span><span class="sxs-lookup"><span data-stu-id="765d7-117">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="765d7-118">Stávající aplikace budou i nadále běžet stejně jako dříve.</span><span class="sxs-lookup"><span data-stu-id="765d7-118">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="765d7-119">**Vývojáři aplikací**</span><span class="sxs-lookup"><span data-stu-id="765d7-119">**Application developers**.</span></span> <span data-ttu-id="765d7-120">Souběžné hostování nemá téměř žádný vliv na vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="765d7-120">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="765d7-121">Ve výchozím nastavení se aplikace vždycky spouštějí proti verzi .NET Framework, na které byly vytvořeny. Tato změna se nezměnila.</span><span class="sxs-lookup"><span data-stu-id="765d7-121">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="765d7-122">Vývojáři ale můžou toto chování potlačit a nasměrovat aplikaci tak, aby běžela v novější verzi .NET Framework (viz [scénář 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="765d7-122">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="765d7-123">**Vývojáři a příjemci knihovny**.</span><span class="sxs-lookup"><span data-stu-id="765d7-123">**Library developers and consumers**.</span></span> <span data-ttu-id="765d7-124">Souběžné hostování neřeší problémy s kompatibilitou, které vývojáři knihovny čelí.</span><span class="sxs-lookup"><span data-stu-id="765d7-124">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="765d7-125">Knihovna, která je přímo načtena aplikací – buď prostřednictvím přímého odkazu, nebo prostřednictvím <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> volání – nadále používá modul runtime, který <xref:System.AppDomain> je načten do.</span><span class="sxs-lookup"><span data-stu-id="765d7-125">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="765d7-126">Své knihovny byste měli testovat ve všech verzích .NET Framework, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="765d7-126">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="765d7-127">Pokud je aplikace kompilována pomocí modulu runtime .NET Framework 4, ale obsahuje knihovnu, která byla sestavena pomocí dřívějšího modulu runtime, tato knihovna bude také používat modul runtime .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="765d7-127">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="765d7-128">Pokud však máte aplikaci vytvořenou pomocí dřívějšího modulu runtime a knihovny, která byla sestavena pomocí .NET Framework 4, musíte aplikaci vynutit, aby používala .NET Framework 4 (viz [scénář 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="765d7-128">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="765d7-129">**Vývojáři komponent spravovaného modelu COM**.</span><span class="sxs-lookup"><span data-stu-id="765d7-129">**Managed COM component developers**.</span></span> <span data-ttu-id="765d7-130">V minulosti se spravované komponenty COM automaticky spouštěly pomocí nejnovější verze modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="765d7-130">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="765d7-131">Nyní můžete spouštět komponenty modelu COM v rámci verze modulu runtime, pomocí něhož byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="765d7-131">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="765d7-132">Jak je znázorněno v následující tabulce, součásti, které byly vytvořeny pomocí .NET Framework verze 1,1, mohou být spouštěny souběžně s komponentami verze 4, ale nelze je spustit s komponentami verze 2,0, 3,0 nebo 3,5, protože Souběžné hostování není pro tyto verze k dispozici.</span><span class="sxs-lookup"><span data-stu-id="765d7-132">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="765d7-133">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="765d7-133">.NET Framework version</span></span>|<span data-ttu-id="765d7-134">1.1</span><span class="sxs-lookup"><span data-stu-id="765d7-134">1.1</span></span>|<span data-ttu-id="765d7-135">2,0 – 3,5</span><span class="sxs-lookup"><span data-stu-id="765d7-135">2.0 - 3.5</span></span>|<span data-ttu-id="765d7-136">4</span><span class="sxs-lookup"><span data-stu-id="765d7-136">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="765d7-137">1.1</span><span class="sxs-lookup"><span data-stu-id="765d7-137">1.1</span></span>|<span data-ttu-id="765d7-138">Neuvedeno</span><span class="sxs-lookup"><span data-stu-id="765d7-138">Not applicable</span></span>|<span data-ttu-id="765d7-139">No</span><span class="sxs-lookup"><span data-stu-id="765d7-139">No</span></span>|<span data-ttu-id="765d7-140">Ano</span><span class="sxs-lookup"><span data-stu-id="765d7-140">Yes</span></span>|  
    |<span data-ttu-id="765d7-141">2,0 – 3,5</span><span class="sxs-lookup"><span data-stu-id="765d7-141">2.0 - 3.5</span></span>|<span data-ttu-id="765d7-142">Ne</span><span class="sxs-lookup"><span data-stu-id="765d7-142">No</span></span>|<span data-ttu-id="765d7-143">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="765d7-143">Not applicable</span></span>|<span data-ttu-id="765d7-144">Ano</span><span class="sxs-lookup"><span data-stu-id="765d7-144">Yes</span></span>|  
    |<span data-ttu-id="765d7-145">4</span><span class="sxs-lookup"><span data-stu-id="765d7-145">4</span></span>|<span data-ttu-id="765d7-146">Ano</span><span class="sxs-lookup"><span data-stu-id="765d7-146">Yes</span></span>|<span data-ttu-id="765d7-147">Ano</span><span class="sxs-lookup"><span data-stu-id="765d7-147">Yes</span></span>|<span data-ttu-id="765d7-148">Neuvedeno</span><span class="sxs-lookup"><span data-stu-id="765d7-148">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="765d7-149">Verze .NET Framework 3,0 a 3,5 jsou postupně postaveny na verzi 2,0 a nemusejí běžet souběžně.</span><span class="sxs-lookup"><span data-stu-id="765d7-149">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="765d7-150">Tato verze je v podstatě stejnou verzí.</span><span class="sxs-lookup"><span data-stu-id="765d7-150">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="765d7-151">Společné scénáře souběžného hostování</span><span class="sxs-lookup"><span data-stu-id="765d7-151">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="765d7-152">**Scénář 1:** Nativní aplikace, která používá komponenty modelu COM sestavené v předchozích verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="765d7-152">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="765d7-153">Nainstalované verze .NET Framework: .NET Framework 4 a všechny ostatní verze .NET Framework používané komponentami modelu COM.</span><span class="sxs-lookup"><span data-stu-id="765d7-153">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="765d7-154">Co dělat: v tomto scénáři neprovádějte žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="765d7-154">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="765d7-155">Komponenty modelu COM budou spouštěny s verzí .NET Framework, se kterými byly zaregistrovány.</span><span class="sxs-lookup"><span data-stu-id="765d7-155">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="765d7-156">**Scénář 2**: spravovaná aplikace vytvořená pomocí nástroje .NET Framework 2,0 SP1, kterou byste chtěli použít s .NET Framework 2,0, ale mají ochotny běžet na .NET Framework 4, pokud verze 2,0 není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="765d7-156">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="765d7-157">Nainstalované verze .NET Framework: starší verze .NET Framework a .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="765d7-157">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="765d7-158">Co dělat: v [konfiguračním souboru aplikace](../configure-apps/index.md) v adresáři aplikace použijte [ \<startup> element](../configure-apps/file-schema/startup/startup-element.md) a sadu [ \<supportedRuntime> elementů](../configure-apps/file-schema/startup/supportedruntime-element.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="765d7-158">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="765d7-159">**Scénář 3:** Nativní aplikace, která používá komponenty modelu COM sestavené s dřívějšími verzemi .NET Framework, které chcete spustit s .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="765d7-159">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="765d7-160">Nainstalované verze .NET Framework: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="765d7-160">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="765d7-161">Co dělat: v konfiguračním souboru aplikace v adresáři aplikace, použijte `<startup>` element s `useLegacyV2RuntimeActivationPolicy` atributem nastaveným na `true` a a `<supportedRuntime>` nastavte element takto:</span><span class="sxs-lookup"><span data-stu-id="765d7-161">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="765d7-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="765d7-162">Example</span></span>  
 <span data-ttu-id="765d7-163">Následující příklad ukazuje nespravovaného hostitele modelu COM, na kterém je spuštěna komponenta spravovaného modelu COM, pomocí verze .NET Framework, která byla komponenta zkompilována pro použití.</span><span class="sxs-lookup"><span data-stu-id="765d7-163">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="765d7-164">Chcete-li spustit následující příklad, zkompilujte a zaregistrujte následující spravovanou komponentu COM pomocí .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="765d7-164">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="765d7-165">Chcete-li zaregistrovat součást, klikněte v nabídce **projekt** na příkaz **vlastnosti**, klikněte na kartu **sestavení** a potom zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .</span><span class="sxs-lookup"><span data-stu-id="765d7-165">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="765d7-166">Zkompilujte následující nespravované aplikace v jazyce C++, která aktivuje objekt COM, který je vytvořen předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="765d7-166">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="765d7-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="765d7-167">See also</span></span>

- [<span data-ttu-id="765d7-168">\<startup>Objekt</span><span class="sxs-lookup"><span data-stu-id="765d7-168">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="765d7-169">\<supportedRuntime>Objekt</span><span class="sxs-lookup"><span data-stu-id="765d7-169">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
