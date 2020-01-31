---
title: CreateCordbObject – funkce
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793861"
---
# <a name="createcordbobject-function"></a>CreateCordbObject – funkce
Vytvoří rozhraní ladicího programu ([ICorDebug](icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 pro Verze ladicího programu cílového procesu. Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.  
  
 `ppCordb`  
 mimo Ukazatel na ukazatel na objekt, který bude převeden na rozhraní [ICorDebug](icordebug-interface.md) a vráceno.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.  
  
 E_INVALIDARG  
 `ppCordb` je null nebo `iDebuggerVersion` není CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppCordb`  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Další chyby.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní [ICorDebug](icordebug-interface.md) , které je vráceno v `ppCordb`, je rozhraní ladění nejvyšší úrovně pro všechny spravované služby ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Verze .NET Framework:** 3,5 SP1
