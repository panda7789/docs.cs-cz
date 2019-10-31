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
ms.openlocfilehash: d21e0d3d0370ec7c1b223be29099f6b99822463b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132108"
---
# <a name="createcordbobject-function"></a>CreateCordbObject – funkce
Vytvoří rozhraní ladicího programu ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.  
  
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
 mimo Ukazatel na ukazatel na objekt, který bude převeden na rozhraní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) a vráceno.  
  
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
 Rozhraní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , které je vráceno v `ppCordb`, je rozhraní ladění nejvyšší úrovně pro všechny spravované služby ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1
