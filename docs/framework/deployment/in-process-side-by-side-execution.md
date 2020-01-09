---
title: Vnitroprocesové souběžné provádění
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 0c699f90143a87b7e7bee24c892efe2936a9399e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716484"
---
# <a name="in-process-side-by-side-execution"></a>Vnitroprocesové souběžné provádění
Počínaje .NET Framework 4 můžete použít Souběžné hostování v rámci procesu ke spouštění více verzí modulu CLR (Common Language Runtime) v jednom procesu. Ve výchozím nastavení se spravované komponenty modelu COM spouštějí s verzí .NET Framework, se kterou byly vytvořeny, bez ohledu na .NET Framework verzi, která je pro tento proces načtena.  
  
## <a name="background"></a>Podrobnosti  
 .NET Framework vždy poskytoval Souběžné hostování pro aplikace spravovaného kódu, ale před .NET Framework 4 neposkytovali tuto funkci pro spravované komponenty modelu COM. V minulosti spravované komponenty modelu COM, které byly načteny do procesu, byly spuštěny buď s verzí modulu runtime, který již byl načten, nebo s nejnovější nainstalovanou verzí .NET Framework. Pokud tato verze není kompatibilní s komponentou modelu COM, komponenta by se nezdařila.  
  
 .NET Framework 4 poskytuje nový přístup k souběžnému hostování, který zajišťuje následující:  
  
- Instalace nové verze .NET Framework nemá žádný vliv na existující aplikace.  
  
- Aplikace běží na verzi .NET Framework, se kterou byly vytvořeny. Nepoužívají novou verzi .NET Framework, pokud to není výslovně přesměrováno. Pro aplikace je však snazší přejít na použití nové verze .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Účinky na uživatele a vývojáře  
  
- **Koncoví uživatelé a správci systému**. Tito uživatelé teď můžou mít větší jistotu, že když si nainstalují novou verzi modulu runtime, ať už nezávisle nebo s aplikací, nebude mít žádný vliv na jejich počítače. Stávající aplikace budou i nadále běžet stejně jako dříve.  
  
- **Vývojáři aplikací** Souběžné hostování nemá téměř žádný vliv na vývojáře aplikací. Ve výchozím nastavení se aplikace vždycky spouštějí proti verzi .NET Framework, na které byly vytvořeny. Tato změna se nezměnila. Vývojáři ale můžou toto chování potlačit a nasměrovat aplikaci tak, aby běžela v novější verzi .NET Framework (viz [scénář 2](#scenarios)).  
  
- **Vývojáři a příjemci knihovny**. Souběžné hostování neřeší problémy s kompatibilitou, které vývojáři knihovny čelí. Knihovna, která je přímo načtena aplikací – buď přímým odkazem, nebo prostřednictvím <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> volání – nadále používá modul runtime <xref:System.AppDomain>, do kterého je načten. Své knihovny byste měli testovat ve všech verzích .NET Framework, které chcete podporovat. Pokud je aplikace kompilována pomocí modulu runtime .NET Framework 4, ale obsahuje knihovnu, která byla sestavena pomocí dřívějšího modulu runtime, tato knihovna bude také používat modul runtime .NET Framework 4. Pokud však máte aplikaci vytvořenou pomocí dřívějšího modulu runtime a knihovny, která byla sestavena pomocí .NET Framework 4, musíte aplikaci vynutit, aby používala .NET Framework 4 (viz [scénář 3](#scenarios)).  
  
- **Vývojáři komponent spravovaného modelu COM**. V minulosti se spravované komponenty COM automaticky spouštěly pomocí nejnovější verze modulu runtime nainstalovaného v počítači. Nyní můžete spouštět komponenty modelu COM v rámci verze modulu runtime, pomocí něhož byly vytvořeny.  
  
     Jak je znázorněno v následující tabulce, součásti, které byly vytvořeny pomocí .NET Framework verze 1,1, mohou být spouštěny souběžně s komponentami verze 4, ale nelze je spustit s komponentami verze 2,0, 3,0 nebo 3,5, protože Souběžné hostování není k dispozici pro tyto zachovávaných.  
  
    |Verze rozhraní .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nelze použít|Ne|Ano|  
    |2.0 - 3.5|Ne|Nelze použít|Ano|  
    |4|Ano|Ano|Nelze použít|  
  
> [!NOTE]
> Verze .NET Framework 3,0 a 3,5 jsou postupně postaveny na verzi 2,0 a nemusejí běžet souběžně. Tato verze je v podstatě stejnou verzí.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Společné scénáře souběžného hostování  
  
- **Scénář 1:** Nativní aplikace, která používá komponenty modelu COM sestavené v předchozích verzích .NET Framework.  
  
     Nainstalované verze .NET Framework: .NET Framework 4 a všechny ostatní verze .NET Framework používané komponentami modelu COM.  
  
     Co dělat: v tomto scénáři neprovádějte žádnou akci. Komponenty modelu COM budou spouštěny s verzí .NET Framework, se kterými byly zaregistrovány.  
  
- **Scénář 2**: spravovaná aplikace vytvořená pomocí nástroje .NET Framework 2,0 SP1, kterou byste chtěli použít s .NET Framework 2,0, ale mají ochotny běžet na .NET Framework 4, pokud verze 2,0 není k dispozici.  
  
     Nainstalované verze .NET Framework: starší verze .NET Framework a .NET Framework 4.  
  
     Co dělat: v [konfiguračním souboru aplikace](../configure-apps/index.md) v adresáři aplikace použijte [\<](../configure-apps/file-schema/startup/startup-element.md) a [> prvku\<supportedRuntime](../configure-apps/file-schema/startup/supportedruntime-element.md) , který je uvedený níže:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Scénář 3:** Nativní aplikace, která používá komponenty modelu COM sestavené s dřívějšími verzemi .NET Framework, které chcete spustit s .NET Framework 4.  
  
     Nainstalované verze .NET Framework: .NET Framework 4.  
  
     Co dělat: v konfiguračním souboru aplikace v adresáři aplikace, použijte element `<startup>` s atributem `useLegacyV2RuntimeActivationPolicy` nastaveným na `true` a `<supportedRuntime>` sadu elementů následujícím způsobem:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje nespravovaného hostitele modelu COM, na kterém je spuštěna komponenta spravovaného modelu COM, pomocí verze .NET Framework, která byla komponenta zkompilována pro použití.  
  
 Chcete-li spustit následující příklad, zkompilujte a zaregistrujte následující spravovanou komponentu COM pomocí .NET Framework 3,5. Chcete-li zaregistrovat součást, klikněte v nabídce **projekt** na příkaz **vlastnosti**, klikněte na kartu **sestavení** a potom zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .  
  
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
  
 Zkompilujte následující nespravovanou C++ aplikaci, která aktivuje objekt com, který je vytvořen předchozím příkladem.  
  
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

- [\<> element Startup](../configure-apps/file-schema/startup/startup-element.md)
- [\<element > supportedRuntime](../configure-apps/file-schema/startup/supportedruntime-element.md)
