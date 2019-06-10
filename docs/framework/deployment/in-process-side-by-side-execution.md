---
title: Vnitroprocesové souběžné provádění
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89dfe697f49e8144d15586cc9c1075f69d1f3a07
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816052"
---
# <a name="in-process-side-by-side-execution"></a>Vnitroprocesové souběžné provádění
Od verze rozhraní .NET Framework 4, můžete použít v procesu – souběžně hostování v jediném procesu spuštění více verzí modulu common language runtime (CLR). Ve výchozím nastavení spravované komponenty modelu COM s verzí rozhraní .NET Framework, kterými byly vytvořeny, bez ohledu na verzi rozhraní .NET Framework, který je načten pro proces spuštění.  
  
## <a name="background"></a>Pozadí  
 Rozhraní .NET Framework má vždy zadaná vedle sebe hostování pro aplikace spravovaného kódu, ale před rozhraní .NET Framework 4 se neposkytl, které tuto funkci pro spravované komponenty modelu COM. V minulosti spravované komponenty modelu COM, která byla načtena do procesu běžel s verzí modulu runtime, který byl již načten nebo s nainstalovanou verzí rozhraní .NET Framework. Pokud tato verze není kompatibilní s komponenty modelu COM, součást selže.  
  
 Rozhraní .NET Framework 4 nabízí nový přístup k hostování vedle sebe, která zajišťuje následující:  
  
- Instalace nové verze rozhraní .NET Framework nemá žádný vliv na stávající aplikace.  
  
- Aplikace běží na verzi rozhraní .NET Framework, se kterými byly vytvořeny. Nepoužívají novou verzi rozhraní .NET Framework pokud výslovně směrované. Uděláte to tak. Je však snazší pro aplikace pro přechod na novou verzi rozhraní .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Vliv na uživatele a vývojáře  
  
- **Koncoví uživatelé a správci systému**. Tito uživatelé teď můžou mít větší jistotu, že při instalaci nové verze modulu runtime, buď samostatně, nebo s aplikací, bude mít žádný vliv na svých počítačích. Stávající aplikace bude dál běžet podle před nástupem prostředí.  
  
- **Vývojáři aplikací**. Hostování vedle sebe nemá téměř žádný vliv na vývojáře aplikací. Ve výchozím nastavení aplikace vždy spustit proti verzi rozhraní .NET Framework, které byly vytvořeny. To se nezměnil. Však mohou vývojáři toto chování přepsat a nasměrovat aplikace na spouštění v novější verzi rozhraní .NET Framework (viz [scénář 2](#scenarios)).  
  
- **Vývojáři knihoven a spotřebitelé**. Hostování vedle sebe nevyřeší problémy s kompatibilitou vývojáři této knihovny pro rozpoznávání tváře. Knihovnu, která je přímo načíst aplikací – buď prostřednictvím přímého odkazu nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> volání – pořád používá modul runtime <xref:System.AppDomain> je načten do. Měli byste otestovat knihovny pro všechny verze rozhraní .NET Framework, které chcete podporovat. Pokud aplikace je kompilována použitím modul runtime rozhraní .NET Framework 4, ale obsahuje knihovnu, která byla vytvořena pomocí starší modul runtime, knihovny použije i modul runtime rozhraní .NET Framework 4. Nicméně, pokud máte aplikaci, která byla vytvořena pomocí starší modul runtime a knihovnu, která byla vytvořena pomocí rozhraní .NET Framework 4, je nutné donutit aplikace také pomocí rozhraní .NET Framework 4 (viz [scénář 3](#scenarios)).  
  
- **Vývojáři komponent COM pro spravované**. V minulosti spravované komponenty modelu COM automaticky spustili pomocí nejnovější verze modulu runtime nainstalovaného v počítači. Teď můžete spustit komponenty modelu COM s verzí modulu runtime, které byly vytvořeny.  
  
     Jak je znázorněno v následující tabulce, komponenty, které byly vytvořeny s použitím rozhraní .NET Framework verze 1.1 lze spustit souběžně s verzí 4 komponenty, ale nelze je spustit s verzí 2.0, 3.0 nebo 3.5 komponenty, protože není k dispozici pro ty hostování vedle sebe verze.  
  
    |Verze rozhraní .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nelze použít|Ne|Ano|  
    |2.0 - 3.5|Ne|Nelze použít|Ano|  
    |4|Ano|Ano|Nelze použít|  
  
> [!NOTE]
>  Verze rozhraní .NET framework 3.0 a 3.5 jsou postupně sestavena na verzi 2.0 a není potřeba pracovat souběžně. Toto jsou ze své podstaty stejnou verzi.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Běžné scénáře hostování vedle sebe  
  
- **Scénář 1:** Nativní aplikace, který používá COM komponenty sestavené v předchozích verzích rozhraní .NET Framework.  
  
     Nainstalovaná verze rozhraní .NET framework: Rozhraní .NET Framework 4 a všechny ostatní verze rozhraní .NET Framework používá komponenty modelu COM.  
  
     Co dělat: V tomto scénáři neprovádějte žádnou akci. Komponenty modelu COM se spustí s verzí rozhraní .NET Framework byla zaregistrována.  
  
- **Scénář 2**: Spravované aplikace vytvořené pomocí rozhraní .NET Framework 2.0 SP1, který chcete spustit s [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ale mají snahu si spustit v rozhraní .NET Framework 4, pokud není k dispozici verze 2.0.  
  
     Nainstalovaná verze rozhraní .NET framework: Starší verze rozhraní .NET Framework a .NET Framework 4.  
  
     Co dělat: V [konfiguračního souboru aplikace](../../../docs/framework/configure-apps/index.md) v adresáři aplikace, použijte [ \<spuštění > element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) a [ \<supportedRuntime >–element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) nastavte následujícím způsobem:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Scénář 3:** Nativní aplikace, který používá COM komponenty sestavené v předchozích verzích rozhraní .NET Framework, kterou chcete spustit pomocí rozhraní .NET Framework 4.  
  
     Nainstalovaná verze rozhraní .NET framework: Rozhraní .NET Framework 4.  
  
     Co dělat: V konfiguračním souboru aplikace v adresáři aplikace, použijte `<startup>` element s `useLegacyV2RuntimeActivationPolicy` atribut nastaven na `true` a `<supportedRuntime>` element nastavte následujícím způsobem:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje nespravovaný hostitel modelu COM, na kterém běží spravované komponenty modelu COM pomocí verze rozhraní .NET Framework, která komponenta byla sestavena pro použití.  
  
 Pokud chcete spustit příklad, kompilaci a zaregistrovat následující spravované komponenty modelu COM pomocí rozhraní .NET Framework 3.5. K registraci komponenty, na **projektu** nabídky, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **sestavení** kartu a potom vyberte **zaregistrovat pro interoperabilitu COM**zaškrtávací políčko.  
  
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
  
 Zkompilujte následující nespravovaná aplikace C++, která se aktivuje objekt modelu COM, který je vytvořen z předchozího příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [\<Po spuštění > – Element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [\<supportedRuntime > – Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
