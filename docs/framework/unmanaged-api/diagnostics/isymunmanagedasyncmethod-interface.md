---
title: ISymUnmanagedAsyncMethod – rozhraní
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504449"
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod – rozhraní
Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetAsyncStepInfo – metoda](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetAsyncStepInfoCount – metoda](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetCatchHandlerILOffset – metoda](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|Viz [Metoda definecatchhandleriloffset –](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[GetKickoffMethod – metoda](isymunmanagedasyncmethod-getkickoffmethod-method.md)|Viz [Metoda definekickoffmethod –](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).|  
|[HasCatchHandlerILOffset – metoda](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|Viz [Metoda definecatchhandleriloffset –](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[IsAsyncMethod – metoda](isymunmanagedasyncmethod-isasyncmethod-method.md)|Kontroluje, zda metoda obsahuje asynchronní informace nebo nikoli.<br /><br /> Pokud se tato metoda vrátí `FALSE` , je neplatná pro volání jakékoli jiné metody v tomto rozhraní. Budou `E_UNEXPECTED` v tomto případě vráceny.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
