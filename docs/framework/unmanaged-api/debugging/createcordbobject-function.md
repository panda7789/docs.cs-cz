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
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179234"
---
# <a name="createcordbobject-function"></a>CreateCordbObject – funkce
Vytvoří ladicí rozhraní ([ICorDebug](icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění ve vzdáleném procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [v] Ladicí verze cílového procesu. Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.  
  
 `ppCordb`  
 [out] Ukazatel na ukazatel na objekt, který bude přetypován do rozhraní [ICorDebug](icordebug-interface.md) a vrácen.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byl úspěšně určen a odpovídající popisovač a pole cesty byly správně vyplněny.  
  
 E_invalidarg  
 `ppCordb`je null `iDebuggerVersion` nebo není CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro`ppCordb`  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Další selhání.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní [ICorDebug,](icordebug-interface.md) které `ppCordb` je vráceno v je nejvyšší úrovně ladění rozhraní pro všechny spravované ladicí služby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET Framework:** 3.5 SP1
