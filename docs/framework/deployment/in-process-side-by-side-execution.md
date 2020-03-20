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
# <a name="in-process-side-by-side-execution"></a>Vnitroprocesové souběžné provádění
Počínaje rozhraním .NET Framework 4 můžete použít hostování v procesu vedle sebe ke spuštění více verzí běžného jazykového běhu (CLR) v jednom procesu. Ve výchozím nastavení jsou spravované součásti modelu COM spuštěny s verzí rozhraní .NET Framework, se kterou byly vytvořeny, bez ohledu na verzi rozhraní .NET Framework načtenou pro tento proces.  
  
## <a name="background"></a>Pozadí  
 Rozhraní .NET Framework vždy poskytovalo hostování vedle sebe pro aplikace spravovaného kódu, ale před rozhraním .NET Framework 4 neposkytovalo tuto funkci pro spravované součásti modelu COM. V minulosti byly spravované součásti modelu COM načtené do procesu spuštěny buď s verzí runtime, která již byla načtena, nebo s nejnovější nainstalovanou verzí rozhraní .NET Framework. Pokud tato verze nebyla kompatibilní s komponentou modelu COM, součást by se nezdaří.  
  
 Rozhraní .NET Framework 4 poskytuje nový přístup k hostování vedle sebe, který zajišťuje následující:  
  
- Instalace nové verze rozhraní .NET Framework nemá žádný vliv na existující aplikace.  
  
- Aplikace spustit proti verzi rozhraní .NET Framework, které byly vytvořeny s. Nepoužívají novou verzi rozhraní .NET Framework, pokud k tomu není výslovně nařízeno. Pro aplikace je však snazší přejít na novou verzi rozhraní .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Účinky na uživatele a vývojáře  
  
- **Koncoví uživatelé a správci systému**. Tito uživatelé mohou mít nyní větší jistotu, že při instalaci nové verze runtime, samostatně nebo s aplikací, nebude mít žádný vliv na jejich počítače. Existující aplikace budou nadále fungovat stejně jako dříve.  
  
- **Vývojáři aplikací**. Side-by-side hosting nemá téměř žádný vliv na vývojáře aplikací. Ve výchozím nastavení aplikace vždy spustit proti verzi rozhraní .NET Framework byly postaveny na; to se nezměnilo. Vývojáři však můžete přepsat toto chování a nasměrovat aplikaci ke spuštění v novější verzi rozhraní .NET Framework (viz [scénář 2](#scenarios)).  
  
- **Vývojáři knihoven a spotřebitelé**. Hostování vedle sebe neřeší problémy s kompatibilitou, kterým vývojáři knihovny čelí. Knihovna, která je přímo načtena aplikací – buď <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> prostřednictvím přímého odkazu nebo <xref:System.AppDomain> prostřednictvím volání – nadále používá dobu runtime, do které je načtena. Knihovny byste měli otestovat proti všem verzím rozhraní .NET Framework, které chcete podporovat. Pokud je aplikace kompilována pomocí runtime rozhraní .NET Framework 4, ale obsahuje knihovnu, která byla vytvořena pomocí dřívějšího běhu runtime, bude tato knihovna také používat runtime rozhraní .NET Framework 4. Pokud však máte aplikaci, která byla vytvořena pomocí dřívějšího běhu runtime a knihovny, která byla vytvořena pomocí rozhraní .NET Framework 4, musíte vynutit, aby aplikace také používala rozhraní .NET Framework 4 (viz [scénář 3](#scenarios)).  
  
- **Spravovaní vývojáři komponent modelu COM**. V minulosti byly spravované součásti modelu COM automaticky spuštěny pomocí nejnovější verze runtime nainstalovaného v počítači. Nyní můžete spustit komponenty modelu COM proti verzi runtime, se kterou byly vytvořeny.  
  
     Jak ukazuje následující tabulka, součásti, které byly vytvořeny s rozhraním .NET Framework verze 1.1, mohou být spuštěny vedle sebe s komponentami verze 4, ale nelze je spustit s komponentami verze 2.0, 3.0 nebo 3.5, protože hostování vedle sebe není pro tyto součásti k dispozici Verze.  
  
    |Verze rozhraní .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Neuvedeno|Ne|Ano|  
    |2.0 - 3.5|Ne|Neuvedeno|Ano|  
    |4|Ano|Ano|Neuvedeno|  
  
> [!NOTE]
> Rozhraní .NET Framework verze 3.0 a 3.5 jsou postupně sestaveny ve verzi 2.0 a není nutné spouštět vedle sebe. Jedná se ze své podstaty stejnou verzi.  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a>Běžné scénáře hostování vedle sebe  
  
- **Scénář 1:** Nativní aplikace, která používá komponenty MODELU COM vytvořené staršími verzemi rozhraní .NET Framework.  
  
     Nainstalované verze rozhraní .NET Framework: Rozhraní .NET Framework 4 a všechny ostatní verze rozhraní .NET Framework používané komponentami modelu COM.  
  
     Co dělat: V tomto scénáři nedělat nic. Součásti modelu COM budou spuštěny s verzí rozhraní .NET Framework, ve které byly zaregistrovány.  
  
- **Scénář 2**: Spravovaná aplikace vytvořená pomocí rozhraní .NET Framework 2.0 SP1, kterou byste raději spouštěli s rozhraním .NET Framework 2.0, ale jste ochotni spustit v rozhraní .NET Framework 4, pokud není k dispozici verze 2.0.  
  
     Nainstalované verze rozhraní .NET Framework: Starší verze rozhraní .NET Framework a rozhraní .NET Framework 4.  
  
     Co dělat: V [konfiguračním souboru aplikace](../configure-apps/index.md) v adresáři aplikace použijte [ \<spouštěcí> element](../configure-apps/file-schema/startup/startup-element.md) a [ \<sadu prvků supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) následujícím způsobem:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Scénář 3:** Nativní aplikace, která používá komponenty MODELU COM vytvořené staršími verzemi rozhraní .NET Framework, které chcete spustit s rozhraním .NET Framework 4.  
  
     Nainstalované verze rozhraní .NET Framework: Rozhraní .NET Framework 4.  
  
     Co dělat: V konfiguračním souboru `<startup>` aplikace v `useLegacyV2RuntimeActivationPolicy` adresáři `true` aplikace `<supportedRuntime>` použijte prvek s atributem nastaveným na a sadu prvků následujícím způsobem:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje nespravovaného hostitele modelu COM, který používá spravovanou komponentu MODELU COM pomocí verze rozhraní .NET Framework, ke které byla komponenta zkompilována.  
  
 Chcete-li spustit následující příklad, zkompilujte a zaregistrujte následující spravovanou komponentu MODELU COM pomocí rozhraní .NET Framework 3.5. Pokud chcete komponentu zaregistrovat, klikněte v nabídce **Projekt** na **Příkaz Vlastnosti**, klikněte na kartu **Sestavení** a zaškrtněte políčko **Registrovat pro com interop.**  
  
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
  
 Zkompilujte následující nespravovanou aplikaci jazyka C++, která aktivuje objekt COM vytvořený v předchozím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také

- [\<spouštěcí> Element](../configure-apps/file-schema/startup/startup-element.md)
- [\<podporovaný modul> Modul runtime](../configure-apps/file-schema/startup/supportedruntime-element.md)
