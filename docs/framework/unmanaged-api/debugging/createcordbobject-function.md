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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f546d7707c40f7f26a46177ae972a988e54e1e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965825"
---
# <a name="createcordbobject-function"></a>CreateCordbObject – funkce
Vytvoří rozhraní ladicího programu ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), která poskytuje funkce pro vytvoření instance spravované ladicí relace na vzdálený proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [in] Ladicí verze cílového procesu. Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.  
  
 `ppCordb`  
 [out] Ukazatel na ukazatel na objekt, který bude převeden [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní a vrátí.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.  
  
 E_INVALIDARG  
 `ppCordb` má hodnotu null, nebo `iDebuggerVersion` není CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nepovedlo se přidělit dostatek paměti pro `ppCordb`  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Jiné chyby.  
  
## <a name="remarks"></a>Poznámky  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní, které se vrátí v `ppCordb` pro všechny spravované ladění služby je rozhraní pro ladění nejvyšší úrovně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
