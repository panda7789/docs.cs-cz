---
title: Vnitroprocesové souběžné provádění
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a33d3c4216ed8c5d79aef4017c6b9256fc1ad7c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052106"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="1b2b3-102">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="1b2b3-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="1b2b3-103">Počínaje .NET Framework 4 můžete použít Souběžné hostování v rámci procesu ke spouštění více verzí modulu CLR (Common Language Runtime) v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="1b2b3-104">Ve výchozím nastavení se spravované komponenty modelu COM spouštějí s verzí .NET Framework, se kterou byly vytvořeny, bez ohledu na .NET Framework verzi, která je pro tento proces načtena.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="1b2b3-105">Pozadí</span><span class="sxs-lookup"><span data-stu-id="1b2b3-105">Background</span></span>  
 <span data-ttu-id="1b2b3-106">.NET Framework vždy poskytoval Souběžné hostování pro aplikace spravovaného kódu, ale před .NET Framework 4 neposkytovali tuto funkci pro spravované komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="1b2b3-107">V minulosti spravované komponenty modelu COM, které byly načteny do procesu, byly spuštěny buď s verzí modulu runtime, který již byl načten, nebo s nejnovější nainstalovanou verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="1b2b3-108">Pokud tato verze není kompatibilní s komponentou modelu COM, komponenta by se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="1b2b3-109">.NET Framework 4 poskytuje nový přístup k souběžnému hostování, který zajišťuje následující:</span><span class="sxs-lookup"><span data-stu-id="1b2b3-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="1b2b3-110">Instalace nové verze .NET Framework nemá žádný vliv na existující aplikace.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="1b2b3-111">Aplikace běží na verzi .NET Framework, se kterou byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="1b2b3-112">Nepoužívají novou verzi .NET Framework, pokud to není výslovně přesměrováno.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="1b2b3-113">Pro aplikace je však snazší přejít na použití nové verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="1b2b3-114">Účinky na uživatele a vývojáře</span><span class="sxs-lookup"><span data-stu-id="1b2b3-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="1b2b3-115">**Koncoví uživatelé a správci systému**.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-115">**End users and system administrators**.</span></span> <span data-ttu-id="1b2b3-116">Tito uživatelé teď můžou mít větší jistotu, že když si nainstalují novou verzi modulu runtime, ať už nezávisle nebo s aplikací, nebude mít žádný vliv na jejich počítače.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="1b2b3-117">Stávající aplikace budou i nadále běžet stejně jako dříve.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="1b2b3-118">**Vývojáři aplikací**</span><span class="sxs-lookup"><span data-stu-id="1b2b3-118">**Application developers**.</span></span> <span data-ttu-id="1b2b3-119">Souběžné hostování nemá téměř žádný vliv na vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="1b2b3-120">Ve výchozím nastavení se aplikace vždycky spouštějí proti verzi .NET Framework, na které byly vytvořeny. Tato změna se nezměnila.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="1b2b3-121">Vývojáři ale můžou toto chování potlačit a nasměrovat aplikaci tak, aby běžela v novější verzi .NET Framework (viz [scénář 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="1b2b3-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="1b2b3-122">**Vývojáři a příjemci knihovny**.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-122">**Library developers and consumers**.</span></span> <span data-ttu-id="1b2b3-123">Souběžné hostování neřeší problémy s kompatibilitou, které vývojáři knihovny čelí.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="1b2b3-124">Knihovna, která je přímo načtena aplikací – buď prostřednictvím přímého odkazu, nebo prostřednictvím <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> volání – nadále používá modul runtime <xref:System.AppDomain> , který je načten do.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="1b2b3-125">Své knihovny byste měli testovat ve všech verzích .NET Framework, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="1b2b3-126">Pokud je aplikace kompilována pomocí modulu runtime .NET Framework 4, ale obsahuje knihovnu, která byla sestavena pomocí dřívějšího modulu runtime, tato knihovna bude také používat modul runtime .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="1b2b3-127">Pokud však máte aplikaci vytvořenou pomocí dřívějšího modulu runtime a knihovny, která byla sestavena pomocí .NET Framework 4, musíte aplikaci vynutit, aby používala .NET Framework 4 (viz [scénář 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="1b2b3-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="1b2b3-128">**Vývojáři komponent spravovaného modelu COM**.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-128">**Managed COM component developers**.</span></span> <span data-ttu-id="1b2b3-129">V minulosti se spravované komponenty COM automaticky spouštěly pomocí nejnovější verze modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="1b2b3-130">Nyní můžete spouštět komponenty modelu COM v rámci verze modulu runtime, pomocí něhož byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="1b2b3-131">Jak je znázorněno v následující tabulce, součásti, které byly vytvořeny pomocí .NET Framework verze 1,1, mohou být spouštěny souběžně s komponentami verze 4, ale nelze je spustit s komponentami verze 2,0, 3,0 nebo 3,5, protože Souběžné hostování není k dispozici pro tyto zachovávaných.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="1b2b3-132">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1b2b3-132">.NET Framework version</span></span>|<span data-ttu-id="1b2b3-133">1.1</span><span class="sxs-lookup"><span data-stu-id="1b2b3-133">1.1</span></span>|<span data-ttu-id="1b2b3-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="1b2b3-134">2.0 - 3.5</span></span>|<span data-ttu-id="1b2b3-135">4</span><span class="sxs-lookup"><span data-stu-id="1b2b3-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="1b2b3-136">1.1</span><span class="sxs-lookup"><span data-stu-id="1b2b3-136">1.1</span></span>|<span data-ttu-id="1b2b3-137">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="1b2b3-137">Not applicable</span></span>|<span data-ttu-id="1b2b3-138">Ne</span><span class="sxs-lookup"><span data-stu-id="1b2b3-138">No</span></span>|<span data-ttu-id="1b2b3-139">Ano</span><span class="sxs-lookup"><span data-stu-id="1b2b3-139">Yes</span></span>|  
    |<span data-ttu-id="1b2b3-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="1b2b3-140">2.0 - 3.5</span></span>|<span data-ttu-id="1b2b3-141">Ne</span><span class="sxs-lookup"><span data-stu-id="1b2b3-141">No</span></span>|<span data-ttu-id="1b2b3-142">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="1b2b3-142">Not applicable</span></span>|<span data-ttu-id="1b2b3-143">Ano</span><span class="sxs-lookup"><span data-stu-id="1b2b3-143">Yes</span></span>|  
    |<span data-ttu-id="1b2b3-144">4</span><span class="sxs-lookup"><span data-stu-id="1b2b3-144">4</span></span>|<span data-ttu-id="1b2b3-145">Ano</span><span class="sxs-lookup"><span data-stu-id="1b2b3-145">Yes</span></span>|<span data-ttu-id="1b2b3-146">Ano</span><span class="sxs-lookup"><span data-stu-id="1b2b3-146">Yes</span></span>|<span data-ttu-id="1b2b3-147">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="1b2b3-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="1b2b3-148">Verze .NET Framework 3,0 a 3,5 jsou postupně postaveny na verzi 2,0 a nemusejí běžet souběžně.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="1b2b3-149">Tato verze je v podstatě stejnou verzí.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="1b2b3-150">Společné scénáře souběžného hostování</span><span class="sxs-lookup"><span data-stu-id="1b2b3-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="1b2b3-151">**Scénář 1:** Nativní aplikace, která používá komponenty modelu COM sestavené v předchozích verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="1b2b3-152">Nainstalované verze .NET Framework: .NET Framework 4 a všechny ostatní verze .NET Framework používané komponentami COM.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="1b2b3-153">Co dělat: V tomto scénáři neprovádějte žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="1b2b3-154">Komponenty modelu COM budou spouštěny s verzí .NET Framework, se kterými byly zaregistrovány.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="1b2b3-155">**Scénář 2**: Spravovaná aplikace vytvořená pomocí .NET Framework 2,0 SP1, kterou byste chtěli použít s .NET Framework 2,0, ale mají ochotny běžet na .NET Framework 4, pokud verze 2,0 není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="1b2b3-156">Nainstalované verze .NET Framework: Starší verze .NET Framework a .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="1b2b3-157">Co dělat: V [konfiguračním souboru aplikace](../configure-apps/index.md) v adresáři aplikace použijte [ \<element](../configure-apps/file-schema/startup/startup-element.md) [ \<](../configure-apps/file-schema/startup/supportedruntime-element.md) startup > a sadu > elementu supportedRuntime následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1b2b3-157">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="1b2b3-158">**Scénář 3:** Nativní aplikace, která používá komponenty modelu COM sestavené s dřívějšími verzemi .NET Framework, které chcete spustit s .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="1b2b3-159">Nainstalované verze .NET Framework: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="1b2b3-160">Co dělat: V konfiguračním souboru aplikace v adresáři aplikace, `<startup>` použijte element `useLegacyV2RuntimeActivationPolicy` s `<supportedRuntime>` atributem nastaveným na `true` a jako následující prvek sady:</span><span class="sxs-lookup"><span data-stu-id="1b2b3-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="1b2b3-161">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b2b3-161">Example</span></span>  
 <span data-ttu-id="1b2b3-162">Následující příklad ukazuje nespravovaného hostitele modelu COM, na kterém je spuštěna komponenta spravovaného modelu COM, pomocí verze .NET Framework, která byla komponenta zkompilována pro použití.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="1b2b3-163">Chcete-li spustit následující příklad, zkompilujte a zaregistrujte následující spravovanou komponentu COM pomocí .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="1b2b3-164">Chcete-li zaregistrovat součást, klikněte v nabídce **projekt** na příkaz **vlastnosti**, klikněte na kartu **sestavení** a potom zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .</span><span class="sxs-lookup"><span data-stu-id="1b2b3-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="1b2b3-165">Zkompilujte následující nespravovanou C++ aplikaci, která aktivuje objekt com, který je vytvořen předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="1b2b3-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b2b3-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b2b3-166">See also</span></span>

- [<span data-ttu-id="1b2b3-167">\<spouštěcí > – element</span><span class="sxs-lookup"><span data-stu-id="1b2b3-167">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="1b2b3-168">\<supportedRuntime – element ></span><span class="sxs-lookup"><span data-stu-id="1b2b3-168">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
