---
title: Vnitroprocesové souběžné provádění
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee9eb30d6966d8162b29286140c068d854f7911c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397452"
---
# <a name="in-process-side-by-side-execution"></a>Vnitroprocesové souběžné provádění
Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít v procesu souběžného hostování spustit více verzí common language runtime (CLR) v jediném procesu. Ve výchozím nastavení spravované komponenty COM s verzí rozhraní .NET Framework, které byly vytvořené s nástroji, bez ohledu na verzi rozhraní .NET Framework, který je načten pro proces spustit.  
  
## <a name="background"></a>Pozadí  
 Rozhraní .NET Framework má vždy zadaná vedle sebe hostování pro spravovaný kód aplikace, ale předtím, než [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], neposkytl této funkce pro spravované COM – součásti. V minulosti spravované komponenty modelu COM, které byly načteny do procesu spustili verzi modulu runtime, která již byla načtena nebo s nainstalovanou verzí rozhraní .NET Framework. Pokud byla tato verze není kompatibilní s komponenty modelu COM, skončí s chybou komponentu.  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Poskytuje nový přístup k hostování vedle sebe, který zajišťuje následující:  
  
-   Instalace nové verze rozhraní .NET Framework nemá žádný vliv na stávající aplikace.  
  
-   Aplikace spustit pro verzi rozhraní .NET Framework, které byly vytvořené s nástroji. Nepoužívají novou verzi rozhraní .NET Framework pokud výslovně směrované Uděláte to tak. Je však snazší pro aplikace pro přechod na novou verzi rozhraní .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Dopady na uživatelů a vývojářů  
  
-   **Koncovým uživatelům a správcům systému**. Tito uživatelé nyní může mít větší jistotu, že při instalaci nové verze modulu runtime nezávisle nebo s aplikací, bude mít žádný vliv na svých počítačích. Existující aplikace bude nadále spouštět jako před.  
  
-   **Vývojáři aplikací**. Souběžně sdílená hostování nemá téměř žádný vliv na vývojáře aplikace. Ve výchozím nastavení aplikace vždy spouštění verzi rozhraní .NET Framework, které byly vytvořené na; To se nezměnilo. Vývojáři můžou, ale toto chování potlačit a přímé aplikace spuštěna v novější verzi rozhraní .NET Framework (viz [scénář 2](#scenarios)).  
  
-   **Vývojáři knihoven a spotřebitelé**. Souběžně sdílená hostování nevyřeší problémy s kompatibilitou vzhled vývojáři této knihovny. Do knihovny, která je přímo zavedená aplikací – buď prostřednictvím přímý odkaz, nebo prostřednictvím <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> volání – budou nadále používat modul runtime <xref:System.AppDomain> je načten do. Měli byste otestovat knihovnách proti všechny verze rozhraní .NET Framework, která chcete podporovat. Pokud aplikace kompiluje pomocí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime ale obsahuje knihovnu, který byl vytvořený pomocí dřívější modul runtime, budou používat tuto knihovnu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime také. Ale pokud máte aplikaci, která byla vytvořena pomocí dřívější runtime a knihovny, který byl vytvořený pomocí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], musíte vynutit aplikace také pomocí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (najdete v části [scénář 3](#scenarios)).  
  
-   **Spravované vývojáři komponent COM**. V minulosti spravované součásti COM automaticky proběhla za použití nejnovější verzi modulu runtime v počítači nainstalována. COM – součásti proti verzi modulu runtime, které byly vytvořené s můžete nyní spustit.  
  
     Jak je uvedeno v následující tabulce, můžete spustit součásti, které byly vytvořeny s rozhraním .NET Framework verze 1.1 node souběžně s součásti verze 4, ale nebudou moct spustit verze 2.0, 3.0 nebo 3.5 součásti, protože není k dispozici pro ty hostování vedle sebe verze.  
  
    |Verze rozhraní .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nelze použít|Ne|Ano|  
    |2.0 - 3.5|Ne|Nelze použít|Ano|  
    |4|Ano|Ano|Nelze použít|  
  
> [!NOTE]
>  Verze rozhraní .NET framework 3.0 a 3.5 jsou postupně vytvořeny na verze 2.0 a není nutné spustit souběžně. Toto jsou ze své podstaty stejnou verzi.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Běžné scénáře hostování vedle sebe  
  
-   **Scénář 1:** nativní aplikaci, která používá komponenty modelu COM, které jsou vytvořené ve starších verzích rozhraní .NET Framework.  
  
     Nainstalovaná verze rozhraní .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a všech ostatních verzí rozhraní .NET Framework používané komponenty COM.  
  
     Co dělat: V tomto scénáři nic nestane. Komponenty COM se spustí s verzí rozhraní .NET Framework byla zaregistrována.  
  
-   **Scénář 2**: spravované aplikace vytvořené s nástroji [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] , ve kterém by se spouští s [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale chcete spustit na [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Pokud není k dispozici verze 2.0.  
  
     Nainstalovaná verze rozhraní .NET framework: dřívější verzi rozhraní .NET Framework a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Co dělat: V [konfigurační soubor aplikace](../../../docs/framework/configure-apps/index.md) v adresáři aplikace používat [ \<spuštění > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) a [ \<supportedRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) nastavit takto:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   **Scénář 3:** nativní aplikaci, která používá komponenty modelu COM, které jsou vytvořené ve starších verzích rozhraní .NET Framework, který chcete spustit s [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Nainstalovaná verze rozhraní .NET framework: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Co dělat: V konfiguračním souboru aplikace v adresáři aplikace, použijte `<startup>` element s `useLegacyV2RuntimeActivationPolicy` atribut nastaven na `true` a `<supportedRuntime>` element nastavit takto:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje nespravované modelu COM hostitele se systémem spravované komponenty modelu COM pomocí verzi rozhraní .NET Framework, kompilovanou pro komponentu použít.  
  
 Spusťte následující příklad, kompilace a zaregistrovat následující spravovaných pomocí součásti COM [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Zaregistrovat komponentu, na **projektu** nabídky, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **sestavení** a pak vyberte **zaregistrovat zprostředkovatel komunikace s objekty COM**zaškrtávací políčko.  
  
```  
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
  
 Zkompilujte následující nespravovaná aplikace C++, která aktivuje objektu COM, který byl vytvořený v předchozím příkladu.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [\<spuštění > elementu](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
 [\<supportedRuntime > elementu](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
